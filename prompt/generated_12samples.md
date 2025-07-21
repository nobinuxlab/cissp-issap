以下では、まず試験範囲（Domain 1～6）それぞれから2問ずつ、計12問のサンプル問題と解説を提示します。  
ご要望に応じて、実際のCISSP-ISSAP試験（125問）同等のボリュームで全問題を作成することも可能です。  

---

# サンプル問題（全12問）

## Domain 1：Security Architecture Modeling and Concepts  
### 問題 1.1  
企業がマルチテナント型クラウドで論理的に分離されたセキュリティドメインを構築したい。以下のうち最適な技術はどれか？  

A. VLAN (Virtual LAN)  
B. SDN (Software-Defined Networking)  
C. Azure Virtual Network (仮想ネットワーク)  
D. サブネットマスクによるIP分割  

### 解答・解説  
解答：C  
- Azure Virtual Networkはマルチテナント環境で論理的に分離された仮想ネットワークを構築できる（Entra IDやNetwork Security Groupとも連携可能）。  
- VLANやSDNも分離に寄与するが、Microsoft Azureを利用する前提ではVNetがネイティブで最適。  
- IP分割だけでは通信制御までは担保できない。  

**キーワード**：論理分離, Microsoft Entra ID, NSG  

---

### 問題 1.2  
セキュリティアーキテクチャの設計フェーズで、システム間の信頼関係を「最小権限」「最小信頼」で定義したい。これに最も該当する原則はどれか？  

A. ゼロトラスト (Zero Trust)  
B. 王の道 (King’s Process)  
C. チョークポイント (Choke Point)  
D. 信任モデル (Trust Model)  

### 解答・解説  
解答：A  
- ゼロトラスト (Zero Trust)は「何も信頼せず、すべてを検証する」モデルであり、最小権限・最小信頼を実現する。  
- これはOfficial (ISC)² Guide to the CISSP CBK, 8th Edition, Domain 1「Secure Architecture Concepts」に詳述。  

---

## Domain 2：Secure Virtualization and Cloud Infrastructure  
### 問題 2.1  
企業がAWS上でコンテナワークロードを実行中。Fargate Spotを利用したいが、常にリソースが奪われるリスクを軽減したい。どの設計が最適か？  

A. ECS Fargate標準タスクを複数AZにデプロイ  
B. Fargate Spotと標準Fargateを混在させたAuto Scalingグループを構成  
C. EC2 インスタンス上で自己管理のKubernetesを動作  
D. Lambdaにすべての処理を移行  

### 解答・解説  
解答：B  
- Fargate Spotは低コストだが中断リスクがあるため、標準Fargateタスクと混在させAuto Scalingでフォールバックさせるのがベストプラクティス。  
- マルチAZ構成だけでは中断時の回復が十分ではない。  

---

### 問題 2.2  
ハイパーバイザーを用いたVMベースのIaaSと、コンテナベースのPaaSを比較したとき、コンテナが持つ最大のセキュリティ上の懸念はどれか？  

A. ホストカーネル共有による横展開（Lateral Movement）  
B. DMA攻撃（Direct Memory Access）  
C. BIOSレベルのマルウェア  
D. TPMチップの改ざん  

### 解答・解説  
解答：A  
- コンテナはホストカーネルを共有するため、あるコンテナからホストや他コンテナへの横展開リスクが高い。  
- DMAやBIOSレベル、TPM改ざんは物理／ハードウェア層の懸念で、VM／コンテナ共通ではない。  

---

## Domain 3：Secure Network and Communication Infrastructure  
### 問題 3.1  
企業がオンプレミスのデータセンターとAzureをSite-to-Site VPNで接続。トンネル内でAzureのマネージドVPNゲートウェイを用いているが、IPv6トラフィックを通せない。なぜか？  

A. Azure VPNゲートウェイはIPv6をサポートしない  
B. BGP経由でのみIPv6を伝搬できる  
C. Azure Virtual Network自体がIPv6非対応  
D. エンドポイント間でIPsecを採用していない  

### 解答・解説  
解答：A  
- 2025年現在、Azure VPNゲートウェイはIPv4のみサポート（NAT over IPv6も未対応）。【参考：Azure ドキュメント】  
- IPv6接続が必要ならExpressRouteやテナント間VPNではなく、別途IPv6ネイティブ対応のサービスを検討。  

---

### 問題 3.2  
TLS導入済みのWebサービスにおいて、サーバ側証明書を定期的に自動更新させたい。最も手軽な実装手法はどれか？  

A. Azure App ServiceのManaged Certificate  
B. Azure Key Vault＋WebJobスクリプト  
C. Let’s Encryptを手動で実行  
D. オンプレミスACMEサーバの構築  

### 解答・解説  
解答：A  
- Azure App ServiceのManaged Certificateは無料・自動更新で、特別なスクリプト不要。  
- Key Vault＋WebJobでも実現可能だが、実装コストが高い。  

---

## Domain 4：Secure Data Storage and Lifecycle Management  
### 問題 4.1  
オンプレミスDBからAzure SQL Databaseに移行を計画。移行中のデータを透過的に暗号化（TDE）したい。どの設定が必要か？  

A. Azure SQLの組み込みTDEを有効化  
B. Always Encryptedを有効化  
C. Transparent Data Encryptionではなく、セルフ管理キーをAzure Key Vaultに置く  
D. TLS 1.0だけを利用  

### 解答・解説  
解答：A  
- Azure SQL Databaseには組み込みのTDE（Transparent Data Encryption）があり、ボタン一つで適用可能。  
- Always Encryptedはクライアント側での暗号化、セルフ管理キーはKey Vaultでの管理方法。  

---

### 問題 4.2  
機密情報を保持するファイルサーバに、Azure Defender for Storageを導入。検出できない攻撃はどれか？  

A. ファイル暗号化マルウェア  
B. 読み取り専用マウント  
C. 大量ダウンロード  
D. ストレージアカウントのアクセスキー窃取  

### 解答・解説  
解答：B  
- Azure Defender for Storageはマルウェア検出／アクセス異常／権限昇格を検知できるが、あくまでAPIログベース。マウント先での読み取り専用設定は検知困難。  

---

## Domain 5：Security Architecture Evaluation and Assessment  
### 問題 5.1  
新規クラウド環境のセキュリティレビューで、「サービス間通信のポリシーをコード化し、バージョン管理したい」と要件が出た。最適な手法はどれか？  

A. Infrastructure as Code（IaC）ツールでNSGルールを管理  
B. 手順書を定期的にレビュー  
C. Azure Policyでのみポリシーを適用  
D. Azure Security Centerの推奨設定  

### 解答・解説  
解答：A  
- IaC（Terraform／ARMテンプレート）でNetwork Security Groupルールをコード管理すれば、バージョン履歴やプルリクエストによる変更承認が可能。  
- Azure PolicyやSecurity Centerは検知・修復が中心で、ポリシー自体をコード化して管理する機能は限定的。  

---

### 問題 5.2  
社内に実装済みのSSO基盤を評価する際、SPF・DKIM・DMARCの設定状況も確認すべき理由はどれか？  

A. メールフッキングを防止するため  
B. SAMLレスポンスの暗号化に必要だから  
C. Webシングルサインオンとは関係ない  
D. JWTの署名検証に影響するから  

### 解答・解説  
解答：A  
- SSOメール通知（パスワードリセットやMFA通知）がメールスプーフィングされないよう、SPF・DKIM・DMARCでドメインなりすましを防止する。  

---

## Domain 6：Identity and Access Management Architecture  
### 問題 6.1  
ハイブリッド環境でオンプレADとAzure AD (Entra ID) を連携。パスワードハッシュ同期（PHS）とパススルー認証（PTA）を比較したとき、Entra ID Conditional Accessで必要な構成はどれか？  

A. PHS：Exchange Hybridにも対応  
B. PTA：オンプレ側で永続的なエージェント接続が必要  
C. PHS：Passwordless認証に非対応  
D. PTA：Azure MFAを使えない  

### 解答・解説  
解答：B  
- PTAはオンプレ側にエージェントを常駐させ、Entra IDへ認証要求を中継するので、常時稼働のエージェントが必須。  
- PHSはハッシュを同期するだけで、エージェント不要。  

---

### 問題 6.2  
OAuth 2.0 の Authorization Code Grant を用いた多要素認証付きSPA（Single Page Application）実装で推奨されるリダイレクトURI の設定はどれか？  

A. ワイルドカード付き URI (e.g. https://app.example.com/*)  
B. 完全一致の HTTPS URI (e.g. https://app.example.com/callback)  
C. http://localhost を含むローカルURI  
D. Fragment 部分にトークンを設定する URI  

### 解答・解説  
解答：B  
- リダイレクトURIは完全一致 (Exact Match) かつHTTPSで指定し、ワイルドカードやHTTPはセキュリティリスクが高いため許可されない。  

---

以上が各Domainから2問ずつのサンプルです。  

もし「実際のCISSP-ISSAP試験（125問）相当の全問題」をご希望でしたら、その旨お知らせください。さらに詳細なボリュームで作成いたします。
