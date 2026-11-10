# Chương 7: An ninh mạng (Network Security)

> Nguồn: *Computer Networking: A Top-Down Approach, 9th ed.* - Chapter 7 (slide Chapter 8 trong PPTX)

---

## 7.1 Mục tiêu an ninh (Security Goals - CIA+)

| Mục tiêu | Mô tả | Kỹ thuật liên quan |
|----------|-------|-------------------|
| **Confidentiality (Bảo mật)** | Chỉ bên được phép mới đọc được dữ liệu | Encryption (AES, ChaCha20, RSA, ECC) |
| **Integrity (Toàn vẹn)** | Dữ liệu không bị sửa đổi không được phép | Hash (SHA-256), HMAC, Digital Signature, AEAD |
| **Authentication (Xác thực)** | Xác minh danh tính thực thể | Password, Certificate, PKI, MFA, SAE |
| **Non-repudiation (Phủ nhận)** | Không thể chối cối hành động đã thực hiện | Digital Signature, Audit log |
| **Availability (Khả dụng)** | Dịch vụ luôn sẵn sàng khi cần | DDoS mitigation, Redundancy, Failover |

---

## 7.2 Mật mã học (Cryptography) - Cơ sở

### 7.2.1 Mật mã đối xứng (Symmetric Key Cryptography)
- **Cùng một khóa** để encrypt và decrypt
- **Nhanh**, phù hợp bulk data encryption

| Algorithm | Key Size | Block/Stream | Mode phổ biến | Trạng thái |
|-----------|----------|--------------|---------------|------------|
| **AES** | 128/192/256 | Block (128-bit) | GCM, CCM, CTR, CBC | **Standard** |
| **ChaCha20** | 256 | Stream | Poly1305 (AEAD) | **Standard** (TLS 1.3, WireGuard) |
| **3DES** | 168 (112 effective) | Block | CBC | **Deprecated** |
| **RC4** | 40-2048 | Stream | - | **Broken** |

#### Modes of Operation (Block Cipher)
| Mode | IV/Nonce | Parallel | Authentication | Use case |
|------|----------|----------|----------------|----------|
| **ECB** | Không | Có | Không | **KHÔNG dùng** (pattern leak) |
| **CBC** | Random IV | Encrypt: Không, Decrypt: Có | Không | Legacy (TLS 1.2, IPsec) |
| **CTR** | Nonce | Có | Không | Stream-like, disk encryption |
| **GCM** | Nonce (96-bit) | Có | **Có (AEAD)** | **TLS 1.3, IPsec, SSH** |
| **CCM** | Nonce | Không | **Có (AEAD)** | 802.11i (WPA2), Zigbee |
| **OCB** | Nonce | Có | **Có (AEAD)** | High performance (patented) |

> **AEAD (Authenticated Encryption with Associated Data)**: Cung cấp cả confidentiality + integrity trong một operation. Input: Key, Nonce, Plaintext, AAD → Output: Ciphertext, Tag.

### 7.2.2 Mật mã khóa công khai (Asymmetric / Public Key Cryptography)
- **Key pair**: Public Key (công khai) + Private Key (bí mật)
- **Chậm**, dùng cho key exchange, digital signature, key encapsulation

| Algorithm | Key Size (equiv. security) | Dùng cho | Trạng thái |
|-----------|----------------------------|----------|------------|
| **RSA** | 2048 (112-bit), 3072 (128-bit), 4096 (150-bit) | Encrypt, Sign, KEM | **Legacy** (lớn, chậm) |
| **ECDSA** | P-256 (128-bit), P-384 (192-bit), P-521 (256-bit) | Sign | **Common** |
| **EdDSA** (Ed25519/Ed448) | 128/224-bit | Sign | **Modern**, fast, deterministic |
| **ECDH** | X25519 (Curve25519), P-256, P-384 | Key Agreement | **Standard** (TLS 1.3) |
| **ML-KEM** (Kyber) | 512/768/1024 | KEM (PQC) | **NIST PQC Standard 2024** |
| **ML-DSA** (Dilithium) | 2/3/5 | Sign (PQC) | **NIST PQC Standard 2024** |
| **SLH-DSA** (SPHINCS+) | - | Sign (PQC, hash-based) | **NIST PQC Standard 2024** |

#### Diffie-Hellman Key Exchange
```
Alice                                    Bob
a ← random                          b ← random
A = g^a mod p                      B = g^b mod p
    |------- A -------------------->|
    |<------- B --------------------|
K = B^a mod p = g^(ab) mod p     K = A^b mod p = g^(ab) mod p
```
- **Ephemeral (DHE/ECDHE)**: Key mới mỗi session → **Forward Secrecy (FS)**
- **Static DH**: Key cố định → **No FS**

### 7.2.3 Hàm băm (Hash Functions)
| Algorithm | Output | Block Size | Trạng thái |
|-----------|--------|------------|------------|
| **MD5** | 128-bit | 512-bit | **Broken** (collision) |
| **SHA-1** | 160-bit | 512-bit | **Broken** (collision) |
| **SHA-256** | 256-bit | 512-bit | **Standard** |
| **SHA-384** | 384-bit | 1024-bit | **Standard** |
| **SHA-512** | 512-bit | 1024-bit | **Standard** |
| **SHA-3** (Keccak) | 224/256/384/512 | 1152/1088/832/576 | **Standard** (PQC-friendly) |
| **BLAKE2** | 256/512 | - | **Fast**, modern |
| **BLAKE3** | 256 | - | **Very fast**, parallelizable |

#### HMAC (Keyed-Hash Message Authentication Code) - RFC 2104
```
HMAC(K, m) = H((K' ⊕ opad) || H((K' ⊕ ipad) || m))
```
- **K'**: Key padded/truncated to block size
- **ipad** = 0x36..., **opad** = 0x5c...
- **An toàn** ngay cả khi H có collision weakness

### 7.2.4 Chữ ký số (Digital Signature)
- **Non-repudiation** + **Authentication** + **Integrity**
- **Sign**: `s = Sign(sk, m)` → thường `s = Hash(m)^d mod n` (RSA) hoặc ECDSA/EdDSA
- **Verify**: `Verify(pk, m, s)` → true/false
- **Chuẩn**: PKCS#1 v1.5, PSS (RSA), RFC 6979 (deterministic ECDSA)

### 7.2.5 PKI (Public Key Infrastructure) & X.509 Certificates

#### X.509 Certificate Structure (RFC 5280)
| Field | Mô tả |
|-------|-------|
| **Version** | v3 (0x02) |
| **Serial Number** | Unique per CA |
| **Signature Algorithm** | e.g., sha256WithRSAEncryption |
| **Issuer** | CA Distinguished Name (DN) |
| **Validity** | NotBefore, NotAfter |
| **Subject** | Entity DN (CN, O, OU, C...) |
| **Subject Public Key Info** | Algorithm + Public Key |
| **Extensions** | **Critical/Non-critical**: Key Usage, Extended Key Usage, Subject Alternative Name (SAN), Basic Constraints (CA:TRUE/FALSE), CRL Distribution Points, Authority Info Access (OCSP), Certificate Policies... |

#### Certificate Chain of Trust
```
Root CA (Self-signed, offline, long-lived ~10-25 yrs)
    │
    ├── Intermediate CA 1 (Online, ~5-10 yrs)
    │       └── Leaf Certificate (Server/Client, ~90-398 days)
    │
    └── Intermediate CA 2 (Cross-sign, backup)
            └── Leaf Certificate
```
- **Validation**: Verify signature chain + Validity + Revocation + Name constraints + Policy OIDs

#### Revocation
| Method | Mô tả | Ưu/nhược điểm |
|--------|-------|---------------|
| **CRL** (Certificate Revocation List) | CA ký list serial numbers revoked | Đơn giản, nhưng kích thước lớn, latency cao |
| **OCSP** (Online Certificate Status Protocol - RFC 6960) | Real-time query responder | Nhanh, nhưng privacy (CA biết client truy cập ai), load CA |
| **OCSP Stapling** (RFC 6066) | Server gắn OCSP response trong TLS handshake | Tốt nhất: Fast, privacy, offload CA |
| **CRLite / Certificate Transparency** | Log-based, compressed revocation | Mozilla Firefox, Chrome |

---

## 7.3 TLS (Transport Layer Security) - RFC 8446 (TLS 1.3)

### TLS Evolution
| Version | Year | Trạng thái | Key Changes |
|---------|------|------------|-------------|
| SSL 3.0 | 1996 | **Deprecated** | POODLE |
| TLS 1.0 | 1999 | **Deprecated** | BEAST |
| TLS 1.1 | 2006 | **Deprecated** | - |
| **TLS 1.2** | 2008 | **Widely used** | AEAD, SHA-256, ECDHE |
| **TLS 1.3** | 2018 | **Current Standard** | 1-RTT, 0-RTT, AEAD only, PFS mandatory |

### TLS 1.3 Handshake (1-RTT) - Full Handshake
```
Client                                                        Server
────────────────────────────────────────────────────────────────────
ClientHello
  - cipher_suites (AEAD only)
  - key_share (ECDHE groups)
  - supported_groups
  - signature_algorithms
  - psk_key_exchange_modes (optional)
  - server_name (SNI)
  - ...
────────────────────────────────────────────────────────────────────
                                          ServerHello
                                            - cipher_suite
                                            - key_share
                                          EncryptedExtensions
                                          CertificateRequest (optional)
                                          Certificate
                                            - cert chain
                                          CertificateVerify
                                            - signature over transcript
                                          Finished
                                            - HMAC(handshake transcript)
────────────────────────────────────────────────────────────────────
Client (verify cert, verify CertificateVerify, verify Finished)
  Finished
  Application Data
────────────────────────────────────────────────────────────────────
                                          Application Data
```

### TLS 1.3 Key Derivation
```
PSK (optional) + (ECDHE shared secret)
       ↓
Early Secret → Handshake Secret → Master Secret
       ↓              ↓                  ↓
  Early Traffic   Handshake Traffic   Application Traffic
  Secrets         Secrets             Secrets (client/server)
```
- **HKDF-Extract/Expand** với SHA-256/384
- **Traffic Keys**: `client_handshake_traffic_secret`, `server_handshake_traffic_secret`, `client_application_traffic_secret`, `server_application_traffic_secret`

### TLS 1.3 Cipher Suites (Only 5 standardized)
| Cipher Suite | Encryption | Hash | Key Exchange |
|--------------|------------|------|--------------|
| `TLS_AES_128_GCM_SHA256` | AES-128-GCM | SHA-256 | (EC)DHE |
| `TLS_AES_256_GCM_SHA384` | AES-256-GCM | SHA-384 | (EC)DHE |
| `TLS_CHACHA20_POLY1305_SHA256` | ChaCha20-Poly1305 | SHA-256 | (EC)DHE |
| `TLS_AES_128_CCM_SHA256` | AES-128-CCM | SHA-256 | (EC)DHE |
| `TLS_AES_128_CCM_8_SHA256` | AES-128-CCM (8-byte tag) | SHA-256 | (EC)DHE |

### TLS 1.3 0-RTT (Resumption)
- **PSK (Pre-Shared Key)**: Từ session trước (session ticket hoặc external PSK)
- **ClientHello** + **Early Data** (Application Data) cùng lúc
- **Risch**: **Replay Attack** → Server phải implement anti-replay (single-use, idempotent APIs only)

### TLS 1.2 vs 1.3 Key Differences
| Aspect | TLS 1.2 | TLS 1.3 |
|--------|---------|---------|
| **Round trips** | 2-RTT (full), 1-RTT (resume) | **1-RTT (full), 0-RTT (resume)** |
| **Key Exchange** | RSA, DH, ECDHE (negotiated) | **(EC)DHE only** (PFS mandatory) |
| **Cipher Suites** | ~300+ (CBC, RC4, GCM, CCM) | **5 AEAD only** |
| **Handshake Encryption** | Không (trừ Finished) | **Tất cả sau ServerHello** |
| **Renegotiation** | Có (insecure) | **Không** (KeyUpdate thay thế) |
| **Compression** | Có (CRIME) | **Không** |
| **Version Negotiation** | Trong ClientHello | **supported_versions extension** |

---

## 7.4 IPsec (Network Layer Security) - RFC 4301, 4303

### Architecture
- **AH (Authentication Header)** - RFC 4302: Integrity + Auth, **KHÔNG encryption**
- **ESP (Encapsulating Security Payload)** - RFC 4303: **Integrity + Auth + Encryption** (phổ biến)

### Modes
| Mode | IPv4 Header | IPsec Header | Payload | IPv6 |
|------|-------------|--------------|---------|------|
| **Transport** | Giữ nguyên | Insert sau IP header | Encrypt (ESP) / Auth (AH) | Extension header |
| **Tunnel** | New IP header | New IP header + IPsec | Encrypt toàn bộ original packet | Extension header |

### ESP Packet Format (Transport Mode)
```
| IPv4 Header | ESP Header | Payload | ESP Trailer | ESP Auth |
| (Original)  | (SPI, Seq) | (Enc)   | (Pad, Next) | (ICV)    |
```

### Security Association (SA) - Unidirectional
- **SPI (Security Parameter Index)**: 32-bit, identify SA
- **Parameters**: Encryption alg, Integrity alg, Keys, Lifetime, Replay window, Mode
- **SAD (Security Association Database)**: Store SA entries
- **SPD (Security Policy Database)**: Policy (selector → action: PROTECT/BYPASS/DISCARD)

### IKEv2 (Internet Key Exchange v2) - RFC 7296
```
Initiator                              Responder
    |                                     |
    |--- IKE_SA_INIT (SAi, KEi, Ni) ----->|
    |                                     |
    |<-- IKE_SA_INIT (SAr, KEr, Nr, [CERTREQ]) --|
    |                                     |
    |--- IKE_AUTH (IDi, AUTH, SAi2, TSi, TSr, [CERT]) -->|
    |                                     |
    |<-- IKE_AUTH (IDr, AUTH, SAr2, TSi, TSr, [CERT]) ---|
    |                                     |
    |    (IKE SA ESTABLISHED + CHILD SA)  |
    |                                     |
```
- **Phase 1**: IKE SA (ISAKMP) - Auth (PSK/PKI/EAP), DH key exchange
- **Phase 2**: Child SA (IPsec SA) - Quick mode, Traffic Selectors (TSi/TSr)
- **Rekeying**: CREATE_CHILD_SA exchange
- **Mobility**: MOBIKE (RFC 4555) - maintain IPsec SA khi IP thay đổi

---

## 7.5 Email Security

### PGP / GPG (Pretty Good Privacy) - RFC 4880 (OpenPGP)
- **Web of Trust**: User ký key nhau, không CA tập trung
- **Hybrid Encryption**: Session key (AES) + Public key (RSA/ECC) encrypt session key
- **Sign + Encrypt**: Sign trước, encrypt sau (hoặc encrypt then sign)

### S/MIME (Secure/Multipurpose Internet Mail Extensions) - RFC 8551
- **X.509 Certificates** (CA-based PKI)
- **CMS (Cryptographic Message Syntax)** - RFC 5652
- **Sign + Encrypt**: Triple-wrapping (Sign → Encrypt → Sign)
- **Widely supported** in email clients (Outlook, Apple Mail, Thunderbird)

---

## 7.6 Wireless & Mobile Security

### WiFi Security (Chi tiết ở Chương 6)
| Protocol | Auth | Encryption | Key Mgmt |
|----------|------|------------|----------|
| **WPA2-Personal** | PSK | AES-CCMP | 4-way handshake (PTK/GTK) |
| **WPA2-Enterprise** | 802.1X/EAP | AES-CCMP | PMK từ RADIUS → PTK/GTK |
| **WPA3-Personal** | **SAE** (Dragonfly) | AES-GCMP-128 | SAE (Forward Secrecy, Anti-dict) |
| **WPA3-Enterprise** | 802.1X/EAP-TLS | **AES-GCMP-256** (Suite B) | CNSA Suite |

### 5G Security (Chi tiết ở Chương 6)
- **5G-AKA**: Home network control, key separation (K_SEAF, K_AMF, K_gNB, K_UP)
- **SUCI**: Encrypted SUPI (IMSI) → Privacy
- **EAP-AKA'**: Improved EAP-AKA
- **TLS tunnel**: Visited ↔ Home network (N32 interface)

---

## 7.7 Operational Security (An ninh vận hành)

### 7.7.1 Firewall (Tường lửa)

#### Stateless Packet Filter
- Kiểm tra **từng gói** độc lập: Src/Dst IP, Src/Dst Port, Protocol, TCP Flags, Interface
- **Không** theo dõi state kết nối
- Nhanh, ít bộ nhớ, nhưng **không phân biệt** legitimate return traffic vs new connection

#### Stateful Packet Filter (Stateful Inspection)
- **Connection State Table**: Track (Src IP, Dst IP, Src Port, Dst Port, Protocol, State)
- **States**: SYN_SENT, SYN_RCVD, ESTABLISHED, FIN_WAIT, TIME_WAIT, CLOSED
- **Allow** traffic thuộc known connection (ESTABLISHED, RELATED)
- **Default deny** new inbound connections

#### Application Gateway / Proxy Firewall (Layer 7)
- **Hiểu giao thức ứng dụng**: HTTP, FTP, SMTP, DNS, SIP...
- **Deep Packet Inspection (DPI)**: Parse payload, enforce policy (URL filtering, malware scan, data loss prevention)
- **Proxy**: Terminate client connection, tạo connection mới đến server
- **Ưu**: Granular control, content inspection
- **Nhược**: Latency, scalability, protocol support limited

#### Next-Generation Firewall (NGFW)
- **Stateful Inspection + DPI + IPS + Application Awareness + SSL Inspection + Threat Intelligence**
- **User/Group identity integration** (AD/LDAP)
- **Sandboxing** (detonate suspicious files)

#### Firewall Rules (ACL - Access Control List)
```
Action   Protocol   Src IP/Port   Dst IP/Port   Interface   Time/Schedule   Logging
ALLOW    TCP        ANY           192.168.1.10:80   WAN         Always          Yes
DENY     TCP        10.0.0.0/8    ANY               LAN         Business hrs    Yes
ALLOW    UDP        192.168.1.0/24 192.168.1.1:53   LAN         Always          No
```
- **Top-down processing**: First match wins
- **Implicit deny all** at end

#### DMZ (Demilitarized Zone)
```
Internet → Firewall → DMZ (Web, DNS, Mail, VPN Gateway) → Firewall → Internal Network
```
- **Public-facing servers** trong DMZ
- **Chỉ allow necessary ports** từ Internet → DMZ và DMZ → Internal
- **No direct access** Internet → Internal

---

### 7.7.2 IDS/IPS (Intrusion Detection/Prevention Systems)

| Loại | Đặc điểm |
|------|----------|
| **NIDS** (Network IDS) | Monitor network traffic (SPAN port, Tap), out-of-band (IDS) hoặc inline (IPS) |
| **HIDS** (Host IDS) | Agent trên host: log, file integrity, syscall, registry |
| **Signature-based** | Pattern matching known attacks (Snort rules, Suricata) - Low false positive, zero-day miss |
| **Anomaly-based** | Machine learning baseline normal behavior - Detect zero-day, high false positive |
| **Hybrid** | Kết hợp cả hai |

#### Deployment Architecture
```
Internet
    │
    ▼
[Border Router] → [Firewall] → [DMZ: NIDS] → [Internal Firewall] → [Internal Network: NIDS/HIDS]
                                                      │
                                              [SIEM/SOAR]
                                              (Log aggregation,
                                               correlation, alerting)
```

#### Snort/Suricata Rule Example
```
alert tcp $EXTERNAL_NET any -> $HOME_NET 80 (
    msg:"WEB-ATTACK SQL injection attempt";
    flow:to_server,established;
    content:"UNION SELECT";
    nocase;
    http_uri;
    classtype:web-application-attack;
    sid:1000001;
    rev:1;
)
```

---

## 7.8 VPN (Virtual Private Network)

| Loại | Layer | Protocol | Use Case |
|------|-------|----------|----------|
| **IPsec VPN** | L3 | ESP (Tunnel mode) | Site-to-site, Remote access (IKEv2) |
| **SSL/TLS VPN** | L4/L7 | HTTPS (TLS) | Remote access (browser/client), clientless |
| **WireGuard** | L3 | Noise_IK (ChaCha20-Poly1305) | Modern, simple, fast, kernel module |
| **OpenVPN** | L2/L3 | TLS (custom) | Flexible, TCP/UDP, proxy support |
| **L2TP/IPsec** | L2 | L2TP + IPsec | Legacy remote access |
| **PPTP** | L2 | GRE + MPPE | **Deprecated** (insecure) |

---

## 7.9 Zero Trust Architecture (ZTA) - NIST SP 800-207

### Core Principles
1. **Verify explicitly**: Always authenticate & authorize (never trust)
2. **Least privilege access**: Just-in-time, just-enough access
3. **Assume breach**: Minimize blast radius, micro-segmentation, encryption everywhere

### Components
| Component | Chức năng |
|-----------|-----------|
| **Policy Engine (PE)** | Decision: Allow/Deny (Policy + Context) |
| **Policy Administrator (PA)** | Execute: Configure enforcement points |
| **Policy Enforcement Point (PEP)** | Enforce: Gateway, Agent, Sidecar, Service Mesh |
| **Identity Provider (IdP)** | User/Device authentication (OIDC, SAML, FIDO2) |
| **Device Trust** | Posture assessment (MDM, EDR, TPM, hardware root of trust) |
| **Network Segmentation** | Micro-segmentation (SDN, Service Mesh, Host firewall) |
| **Observability** | Continuous monitoring, logging, analytics |

---

## Tóm tắt chương 7

| Chủ đề | Key Points |
|--------|------------|
| **Security Goals** | CIA + Non-repudiation + Availability |
| **Symmetric Crypto** | AES-GCM/CCM, ChaCha20-Poly1305 (AEAD), modes (ECB bad, CBC/CTR/GCM) |
| **Asymmetric Crypto** | RSA (legacy), ECDSA/EdDSA (sign), ECDH/X25519 (KA), PQC (ML-KEM, ML-DSA, SLH-DSA) |
| **Hash & MAC** | SHA-256/384/3, BLAKE2/3, HMAC |
| **Digital Signature** | Non-repudiation, PKCS#1 v1.5/PSS, ECDSA, EdDSA |
| **PKI/X.509** | Chain of trust (Root → Intermediate → Leaf), SAN, Key Usage, Revocation (CRL/OCSP/Stapling/CT) |
| **TLS 1.3** | 1-RTT handshake, AEAD only, (EC)DHE mandatory, 0-RTT resumption, Encrypted handshake |
| **IPsec** | AH (auth only), ESP (enc+auth), Transport/Tunnel mode, IKEv2 (2-phase), MOBIKE |
| **Email Security** | PGP (Web of Trust), S/MIME (X.509/CMS) |
| **Wireless/Mobile** | WPA2/WPA3 (SAE, GCMP), 5G-AKA, SUCI, EAP-AKA' |
| **Firewall** | Stateless, Stateful, Proxy/L7, NGFW, DMZ, ACL top-down |
| **IDS/IPS** | NIDS/HIDS, Signature/Anomaly/Hybrid, Snort/Suricata, SIEM |
| **VPN** | IPsec, SSL/TLS, WireGuard, OpenVPN |
| **Zero Trust** | Never trust, verify explicitly, least privilege, assume breach, micro-segmentation |

---

## Liên kết
- [[MỤC LỤC - Lý thuyết Mạng máy tính]]
- [[Chương 6 - Mạng không dây & Di động]]