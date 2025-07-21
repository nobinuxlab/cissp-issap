# Domain 3：Secure Network and Communication Infrastructure（20問）

CISSP-ISSAP Domain 3「Secure Network and Communication Infrastructure」に準拠した20問のサンプル問題です。日本語設問、英語原文を併記し、解説ではAzureをはじめMicrosoft製品も具体例として紹介します。

---

### 問3.1  
設問：ステートレスファイアウォールとステートフルファイアウォールの主な違いはどれか？  
英語原文：What is the primary difference between a stateless firewall and a stateful firewall?  

A. すべてのパケットを検査しない  
B. 通信セッションの状態を追跡する  
C. VLANタグを認識できない  
D. アプリケーション層のプロトコルを解釈しない  

解答：B  

解説：  
- ステートフル (stateful) ファイアウォールはTCP/UDPセッションの状態（コネクションテーブル）を維持し、応答パケットのみを許可可能。  
- ステートレス (stateless) は各パケットを個別に評価し、応答関係を認識しない。  
- Azureでは**Azure Firewall**がステートフル、**Network Security Group (NSG)** は基本的にステートレスなルール適用。  

---

### 問3.2  
設問：IPsec トンネルモード（Tunnel Mode）とトランスポートモード（Transport Mode）の違いは何か？  
英語原文：What differentiates IPsec Tunnel Mode from Transport Mode?  

A. トラフィックの暗号化対象がネットワークレイヤーかトランスポートレイヤーか  
B. トンネルモードはSHA-1しか使わない  
C. トランスポートモードはIKEを使用しない  
D. トンネルモードはUDPでしか動作しない  

解答：A  

解説：  
- トンネルモードはIPヘッダーを含む「ネットワーク層全体」を暗号化し、新規IPヘッダーを付与。  
- トランスポートモードは元のIPヘッダーを保持し、ペイロード（L4以降）のみ暗号化。  
- Azure Site-to-Site VPNではトンネルモードが使われる。  

---

### 問3.3  
設問：TLSオフロードを実現するAzureのサービスはどれか？  
英語原文：Which Azure service provides TLS offloading?  

A. Azure Traffic Manager  
B. Azure Application Gateway  
C. Azure Bastion  
D. Azure Virtual WAN  

解答：B  

解説：  
- **Azure Application Gateway（WAF付きも可）** はTLSターミネーションをフロントエンドで行い、バックエンドへの通信はHTTP/HTTPSまたはHTTPのみ可能。  
- Traffic ManagerはDNSベースの負荷分散、BastionはRDP/SSHのプロキシ、Virtual WANはSD-WAN機能。  

---

### 問3.4  
設問：PKIにおけるOCSPとCRLの主な違いは何か？  
英語原文：What is the main difference between OCSP and CRL in PKI?  

A. OCSPはリアルタイムで証明書失効情報を問い合わせる  
B. CRLは常にオンラインで利用可能  
C. OCSPは一括ダウンロード方式  
D. CRLはTLS1.3でのみ使われる  

解答：A  

解説：  
- CRL (Certificate Revocation List) は定期的に配布される失効一覧をダウンロードし、クライアント側で照合。  
- OCSP (Online Certificate Status Protocol) はCAにリアルタイム問い合わせを行い、応答を得る。  
- Azure Key Vaultの**Certificate**機能でもOCSP/CRL情報を扱える。  

---

### 問3.5  
設問：WPA3の「SAE（Simultaneous Authentication of Equals）」が改善する主な点は何か？  
英語原文：What improvement does WPA3’s SAE (Simultaneous Authentication of Equals) bring?  

A. 静的WEPキーのサポート  
B. 辞書攻撃に対する耐性  
C. MACアドレスフィルタリング  
D. TLS1.0互換性  

解答：B  

解説：  
- SAEはパスワードベースの4ウェイハンドシェイクを置き換え、辞書攻撃や中間者攻撃に強い。  
- WPA2ではPSKのハンドシェイクが脆弱だったため、SAEによりセキュアに鍵交換。  

---

### 問3.6  
設問：Zero Trust ネットワークアーキテクチャにおけるマイクロセグメンテーションの目的は何か？  
英語原文：What is the purpose of micro-segmentation in a Zero Trust network architecture?  

A. 帯域幅の動的割り当て  
B. ワークロード間通信を最小限のルールで制御  
C. VPNの代替  
D. CDNとの統合  

解答：B  

解説：  
- マイクロセグメンテーションはワークロードごとにポリシーを細かく定義し、横展開 (Lateral Movement) を防止。  
- Azureでは**Azure Firewall Manager**＋**Azure Virtual Network**でNSG／Application Security Groupを組み合わせる。  

---

### 問3.7  
設問：SASE（Secure Access Service Edge）の主要コンポーネントではないものはどれか？  
英語原文：Which of the following is NOT a core component of SASE?  

A. SD-WAN  
B. CASB (Cloud Access Security Broker)  
C. MPLSバックボーン  
D. SWG (Secure Web Gateway)  

解答：C  

解説：  
- SASEはSD-WANとセキュリティ機能（SWG、CASB、FWaaS、ZTNA）をクラウドサービスとして統合。  
- MPLSは従来型のWAN技術で、SASEのクラウドネイティブとは対極。  

---

### 問3.8  
設問：BGPハイジャック攻撃に対する防御策として最も有効なのはどれか？  
英語原文：What is the most effective mitigation against a BGP hijacking attack?  

A. ルートフィルタリングとRPKI (Resource Public Key Infrastructure) の導入  
B. BGPセッションをMD5で保護  
C. ネットワークACLの強化  
D. IPv6のみを使用  

解答：A  

解説：  
- RPKIを用い、正当なAS番号・プレフィックス組み合わせを暗号的に検証し、ハイジャックを防止。  
- MD5はBGPセッションの保護、ACLはL3制御だがAS間ルーティング乗っ取りには無効。  

---

### 問3.9  
設問：MPLSネットワークにおいてラベルスイッチパス (LSP) を設定する技術はどれか？  
英語原文：Which technology sets up a Label Switched Path (LSP) in an MPLS network?  

A. RSVP-TE  
B. OSPF  
C. RIP  
D. STP  

解答：A  

解説：  
- RSVP-TE (Resource Reservation Protocol–Traffic Engineering) はMPLS LSPを予約・トラフィックエンジニアリングを実現。  
- OSPF/RIPはIPルーティングプロトコル、STPはレイヤ2ループ防止。  

---

### 問3.10  
設問：Azure ExpressRoute回線でVMからオンプレミスへの掘り出しトラフィックを暗号化するには何を用いるべきか？  
英語原文：What should you use to encrypt traffic from your VM to on-premises over an Azure ExpressRoute circuit?  

A. ExpressRouteのみで自動暗号化される  
B. IPsec Site-to-Site VPNを併用  
C. Azure DDoS Protection  
D. Azure Bastion  

解答：B  

解説：  
- ExpressRouteは専用線接続だが暗号化は提供しないため、IPsec Site-to-Site VPNを併用してトラフィックを暗号化する必要がある。  
- DDoS Protectionは防御、BastionはRDP/SSHの安全接続サービス。  

---

### 問3.11  
設問：DNSキャッシュポイズニング攻撃に対する効果的な防御策はどれか？  
英語原文：Which is an effective mitigation against DNS cache poisoning attacks?  

A. DNSSECの導入  
B. TCPのみでDNSを運用  
C. EDNSを無効化  
D. DNSキャッシュを無制限に維持  

解答：A  

解説：  
- DNSSECはゾーン署名により応答の真正性と整合性を検証し、キャッシュポイズニングを防ぐ。  
- TCP運用は応答性改善のための代替手段であり、無効化/無制限キャッシュは対策にならない。  

---

### 問3.12  
設問：TLS1.3で廃止された機能はどれか？  
英語原文：Which feature was removed in TLS 1.3?  

A. 差分RSAキー交換 (RSA key exchange)  
B. ECDHE (Elliptic Curve Diffie-Hellman Ephemeral)  
C. AES-GCM 暗号化  
D. HMAC-SHA256  

解答：A  

解説：  
- TLS1.3ではRSAキー交換を廃止し、Forward Secrecyを保証するE (Ephemeral) DHのみをサポート。  
- AES-GCMやHMACアルゴリズムは継続してサポート。  

---

### 問3.13  
設問：SNMPv3が提供するセキュリティ機能として誤っているものはどれか？  
英語原文：Which of the following is NOT a security feature provided by SNMPv3?  

A. 認証（Authentication）  
B. 暗号化（Encryption）  
C. データ整合性（Integrity）  
D. 侵入検知（Intrusion Detection）  

解答：D  

解説：  
- SNMPv3はユーザー認証（USM）とメッセージの暗号化・整合性保証を提供。  
- 侵入検知はマネージド機能ではなく、ネットワークIDS/IPSが担当。  

---

### 問3.14  
設問：802.1Xによるポートベースアクセス制御で必要な要素はどれか？  
英語原文：What is a required component in 802.1X port-based access control?  

A. RADIUSサーバー  
B. DNSサーバー  
C. DHCPサーバー  
D. NTPサーバー  

解答：A  

解説：  
- 802.1Xは認証サーバー (通常RADIUS) と連携し、スイッチの認証ポートを制御。  
- DNS/DHCP/NTPは別の機能で、アクセス制御には直接関与しない。  

---

### 問3.15  
設問：DMVPN（Dynamic Multipoint VPN）の利点として最も適切なのはどれか？  
英語原文：What is a key benefit of DMVPN (Dynamic Multipoint VPN)?  

A. メッシュ型VPNトンネルを動的に確立できる  
B. すべてのトラフィックを一極集中ルーターで経由させる  
C. IPsecを使用しない  
D. BGPを使用しない  

解答：A  

解説：  
- DMVPNはHub-and-Spoke構成から動的にSpoke間のメッシュトンネルを確立し、効率的な分散通信を実現。  
- IPsec/IKE、BGP/マルチキャスト(NHRP)を利用する。  

---

### 問3.16  
設問：DDoS攻撃に対しAzureが提供するマネージドサービスはどれか？  
英語原文：Which managed service does Azure offer for DDoS mitigation?  

A. Azure DDoS Protection  
B. Azure Firewall  
C. Azure Traffic Manager  
D. Azure Load Balancer  

解答：A  

解説：  
- **Azure DDoS Protection Standard** はネットワーク層およびアプリ層への大規模攻撃を自動検知・緩和。  
- Firewall/Load BalancerはFWaaSやLBaaS、Traffic ManagerはDNSベースの負荷分散。  

---

### 問3.17  
設問：NATトランスレーションで「Port Preservation」が意味するものは何か？  
英語原文：What does “port preservation” mean in NAT translation?  

A. 送信元ポートを変更せずに NAT する  
B. すべてのポートをランダム化する  
C. ポート番号を削除する  
D. ポートフォワードを使用しない  

解答：A  

解説：  
- Port Preservation はソースポートをそのまま利用し、既存のポート番号を維持してマッピングする動作。  
- ランダム化や削除はセキュリティ向上のための別手法。  

---

### 問3.18  
設問：ハイブリッドWAN（Software-Defined WAN）実装時のセキュリティ上の懸念はどれか？  
英語原文：What is a security concern when implementing a Software-Defined WAN in a hybrid environment?  

A. 制御プレーンとデータプレーンの適切な分離  
B. 路由プロトコルは静的ルーティングのみ対応  
C. L2プロトコルのサポート不足  
D. スタティックNATのみ利用可能  

解答：A  

解説：  
- SD-WANでは制御プレーン（集中管理サーバ）とデータプレーン（エッジルーター）が分離されるため、認証や暗号化、アクセス制御の強化が必須。  
- 静的ルーティング／L2／NATは機能制限の話。  

---

### 問3.19  
設問：ネットワークフォレンジックで主に取得するデータはどれか？  
英語原文：What data is primarily collected in network forensics?  

A. パケットキャプチャ  
B. システムログ  
C. メモリダンプ  
D. ファイルのハッシュ値  

解答：A  

解説：  
- ネットワークフォレンジックは通信内容（パケット）を収集・解析し、攻撃経路や手口を特定。  
- システムログやメモリダンプは別のフォレンジック分野。  

---

### 問3.20  
設問：TLSセッションの中間者攻撃（MITM）を防ぐための最適策はどれか？  
英語原文：Which is the best mitigation against a TLS session MITM attack?  

A. サーバー証明書の完全検証（ホスト名、ルートCA、失効チェック）  
B. TLS1.0を利用  
C. 公開鍵ピンニングを避ける  
D. 自己署名証明書を使用  

解答：A  

解説：  
- 証明書のホスト名一致、信頼ルートCA確認、OCSP/CRLによる失効チェックを行うことでMITMを防止。  
- 古いTLSバージョンや自己署名、ピンニング回避はリスクを増大させる。  

---

Domain 3の20問を提示しました。  
次はDomain 4「Secure Data Storage and Lifecycle Management」に移ります。準備ができましたらお知らせください。
