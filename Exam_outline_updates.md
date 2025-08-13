# Comparison of ISSAP Exam Outline Updates (2025 vs. 2020)

---

## Key Structural Changes

- Domains reduced from six to four  
- Domain names refined and weights reallocated  
- Removed standalone Application Security and Security Operations domains; their topics folded into the remaining four  

---

## Domain-by-Domain Differences

### Domain 1: Governance, Risk, and Compliance (GRC)

- Name changed from “Architect for Governance, Compliance, and Risk Management” to “Governance, Risk, and Compliance (GRC)”.  
- Weight increased from 17 % to 21 %.  
- Added emphasis on resilient solutions under legal/regulatory requirements.  
- Expanded “architecting for GRC” tasks to include:
  - Design of continuous monitoring and reporting (e.g., vulnerability management, compliance audits)  
  - Incorporation of formal risk assessment artifacts  
  - Advising on risk treatment strategies (mitigate, transfer, accept, avoid)  

### Domain 2: Security Architecture Modeling

- Name unchanged; weight rose from 15 % to 22 %.  
- Subdomain 2.1 now explicitly calls out:
  - Threat modeling frameworks (STRIDE, CVSS, threat intelligence)  
- Subdomain 2.2 expanded to include:
  - Code review methodologies (dynamic, manual, static analysis, software composition analysis)  
  - Structured peer and third-party validation (e.g., tabletop exercises, modeling/simulation)  

### Domain 3: Infrastructure and System Security Architecture

- Renamed from “Infrastructure Security Architecture”; weight up from 21 % to 32 %.  
- Subdomain 3.1 broadened to cover:
  - Application security requirements (Requirements Traceability Matrix, secure coding)  
  - IT/OT convergence in on-premises, cloud, and hybrid deployments  
- Subdomain 3.2 reorganized as a single, comprehensive “architect” section, adding:
  - Secure shared services (email, VoIP, unified communications)  
  - Third-party integrations (API, federation, SFTP, VPN)  
  - Infrastructure and content monitoring (email, web, data loss prevention)  
  - Out-of-band communications planning (incident response, BC/DR)  
- Subdomain 3.3 extracted as a dedicated cryptographic architecture topic:
  - Lifecycle planning for keys (generation, storage, distribution)  
  - Implementation across in-transit, at-rest, and in-use states  

### Domain 4: Identity and Access Management (IAM) Architecture

- Name unchanged; weight climbed from 16 % to 25 %.  
- Split into four clear lifecycle stages:
  1. Identity lifecycle (establish, verify, provision/de-provision)  
  2. Authentication (single-factor, MFA, risk-based; SAML, Kerberos, RADIUS, OAuth)  
  3. Authorization (SoD, least privilege; SSO, RBAC, ABAC, certificate- and token-based)  
  4. Accounting (forensics requirements, defining audit events, log management, analysis, reporting)  

---

# English Summary of Updates

The 2025 ISSAP outline streamlines six domains into four, redistributing weight to stress infrastructure and IAM architecture. Governance shifts from a risk-management focus to a broader GRC discipline, adding resilient-solution design and continuous monitoring. Security modeling now mandates explicit threat-modeling frameworks and code-review practices. Infrastructure architecture balloons to encompass application security, OT/IT convergence, third-party integrations, content monitoring, cryptography, and out-of-band communications. IAM evolves into a full lifecycle model—identity, authentication, authorization, accounting—emphasizing modern protocols and auditability. Application Security and Security Operations no longer stand alone but integrate into the core domains to reflect today’s interconnected, cloud-centric environments.

---

# 日本語での更新内容まとめ

2025年版では、従来の6ドメインを4ドメインに統合し、インフラストラクチャとIAMアーキテクチャの比重を大幅に引き上げました。GRC（Governance, Risk, and Compliance）ドメインとして、リスク管理だけでなくレジリエント設計と継続的モニタリングを含む広範なガバナンス機能を追加。セキュリティアーキテクチャモデリングでは、STRIDEやCVSSなどの脅威モデリングフレームワークとコードレビュー手法を明示的に要求。インフラアーキテクチャはアプリケーションセキュリティ、IT/OT統合、サードパーティ連携、コンテンツモニタリング、暗号化設計、BC/DRコミュニケーション計画までを包含。IAMはアイデンティティライフサイクル、認証、認可、アカウンティングの4フェーズに拡張し、最新プロトコルと監査機能を強化。アプリケーションセキュリティとセキュリティ運用は独立ドメインとしては廃止され、相互接続したクラウド環境を反映して既存4ドメインに統合されています。
