# Domain 2：Secure Virtualization and Cloud Infrastructure（20問）

以下はCISSP-ISSAPのDomain 2「Secure Virtualization and Cloud Infrastructure」に準拠した20問のサンプル問題です。各設問では日本語訳と英語原文を併記し、Microsoft Azureなど製品事例を交えて解説しています。

---

### 問2.1
設問：Type 1ハイパーバイザー（英：Native/Bare-metal Hypervisor）の特徴はどれか？  
A. OS上にインストールされる (Runs on host OS)  
B. ハードウェア上で直接動作する (Runs directly on hardware)  
C. コンテナと同様にホストカーネルを共有する (Shares host kernel like containers)  
D. アプリケーションレベルで仮想化を行う (Performs application-level virtualization)  

解答：B  

解説：  
- Type 1ハイパーバイザーは物理サーバ（ベアメタル）上で直接動作し、ゲストOSを管理する。  
- 代表例：Microsoft Hyper-V、VMware ESXi。Azure Stack HCIもHyper-VベースでType 1に該当する。  
- Type 2はホストOS上で動作し、Type 1ほどのパフォーマンスや分離強度を持たない。  

---

### 問2.2
設問：VM Escape（仮想マシンからハイパーバイザーへの脱出）リスクを低減する機能として最も適切なのはどれか？  
A. Secure Boot（UEFIセキュアブート）  
B. VLANによる論理分離 (Logical separation via VLAN)  
C. NVMe over Fabrics  
D. 仮想スイッチ（vSwitch）のACL  

解答：A  

解説：  
- UEFI Secure Bootは未署名または改ざんされたブートローダーの実行を防ぎ、マルウェアによる低レベル侵入やVM Escapeを抑制する。  
- VLANやvSwitch ACLはネットワーク分離に有効だが、ハイパーバイザー層でのコード実行保護にはならない。  

---

### 問2.3
設問：機密計算（英：Confidential Computing）が必要なワークロードに適したAzureサービスはどれか？  
A. Azure Confidential VM  
B. Azure Kubernetes Service (AKS)  
C. Azure Virtual Machine Scale Sets  
D. Azure Container Instances (ACI)  

解答：A  

解説：  
- Azure Confidential VMはIntel SGXやAMD SEVの技術を利用し、メモリ内容を実行時にハードウェアレベルで暗号化する。  
- コンテナ基盤やVMSSは汎用的な仮想化環境であり、機密計算機能は持たない。  

---

### 問2.4
設問：コスト最適化のためAzure Spot VMを利用する際、予期せずリソースが回収された場合の可用性を担保する設計はどれか？  
A. Spot VMを単独で運用  
B. Spot VMと通常VMをスケールセットで混在させる  
C. Spot VMをVNet外に配置  
D. Spot VMをローカルディスクのみで使用  

解答：B  

解説：  
- Azure Spot VMは余剰キャパシティを低価格提供するが、優先度が低いためリソースが回収される可能性がある。  
- 通常VMと混在させ、Auto Scaleで負荷移行/回復できる設計がベストプラクティス。  

---

### 問2.5
設問：Azure PaaSサービス（例：Azure App Service）において顧客が管理すべき責任はどれか？  
A. 基盤となるホストOSのパッチ管理  
B. アプリケーションコードの脆弱性修正  
C. ハイパーバイザー層のセキュリティ  
D. データセンター物理アクセス管理  

解答：B  

解説：  
- PaaSモデルではホストOS／ハイパーバイザー／物理層はクラウド事業者が管理する。  
- 顧客はアプリケーションやデータの設定・脆弱性修正、認証／認可設定などを担う。  

---

### 問2.6
設問：Azure Kubernetes Service (AKS) の「Virtual Nodes」機能の主な目的はどれか？  
A. Azure Container Instances（ACI）によるマルチテナント隔離  
B. VMの自動バックアップ  
C. AKSクラスターのスケールアップ  
D. コンテナイメージのレジストリ管理  

解答：A  

解説：  
- Virtual NodesはACIをAKSノードとしてシームレスに統合し、ハイパーバイザーによるワークロード隔離を提供する。  
- スケーリング自体はKubernetesの機能で、バックアップやレジストリ管理は別サービスで実現。  

---

### 問2.7
設問：仮想環境内でマイクロセグメンテーションを実現するためのAzure技術はどれか？  
A. Azure Virtual Network サブネット  
B. Azure Network Security Group (NSG)  
C. Azure Private Link  
D. Azure ExpressRoute  

解答：B  

解説：  
- NSGはサブネットまたはNIC単位で5層（L4/L5）のトラフィックフィルタリングを行い、ワークロード間通信を細かく制御できる。  
- Private Linkはプライベートエンドポイント、ExpressRouteは専用線接続のサービス。  

---

### 問2.8
設問：専用物理サーバをクラウドで利用し、他テナントからの干渉を排除するサービスはどれか？  
A. Azure Dedicated Host  
B. Azure Shared Host  
C. Azure Spot VM  
D. Azure Container Instances  

解答：A  

解説：  
- Azure Dedicated Hostは物理サーバを顧客専用で占有し、CPU／メモリ／キャッシュなどのリソース隔離を担保する。  
- Shared HostやSpot VM、ACIはマルチテナント基盤上で動作する。  

---

### 問2.9
設問：イベントドリブンの短時間実行ワークロードに最適なのはどれか？  
A. Azure Functions  
B. Azure Kubernetes Service  
C. Azure Virtual Machines  
D. Azure Dedicated Host  

解答：A  

解説：  
- Azure FunctionsはFaaS（Function-as-a-Service）で、イベント駆動・サーバーレス実行モデルを提供する。  
- コンテナOrchestratorや専用VMは持続的なサービス向き。  

---

### 問2.10
設問：IaaS VMの一時ディスク（英：Temporary Disk）を使用する際の注意点はどれか？  
A. データはVM再起動時に保持される  
B. データはインスタンス停止・再作成時に消去される  
C. データはAzure Backupで自動保存される  
D. データは異なるリージョンに複製される  

解答：B  

解説：  
- 一時ディスクはローカルSSDであり、VM停止・再作成・ハードウェア障害時にデータが消失する。  
- 重要データはManaged DiskやAzure Filesなど永続ストレージに保存する必要がある。  

---

### 問2.11
設問：仮想マシンの脆弱性をリアルタイムで検出し、パッチ適用状況を一元管理できるAzureサービスはどれか？  
A. Microsoft Defender for Cloud（旧：Azure Security Center）  
B. Azure Policy  
C. Azure Monitor  
D. Azure Arc  

解答：A  

解説：  
- Defender for CloudはVMの脆弱性スキャン、脆弱性評価、推奨修正アクションを提供し、パッチ管理を支援する。  
- Azure Policyはポリシー適用、Monitorはログ/メトリクス収集、Arcはハイブリッド管理基盤。  

---

### 問2.12
設問：クラウドでハードウェアセキュリティモジュール（HSM）を利用し、FIPS 140-2準拠で鍵管理する場合に最適なサービスはどれか？  
A. Azure Key Vault Managed HSM  
B. Azure Key Vault ソフトウェアキー  
C. Azure Disk Encryption  
D. Azure App Service Managed Certificate  

解答：A  

解説：  
- Managed HSMは専用のクラウドHSMをFIPS 140-2 Level 3で提供し、鍵の生成・保護・操作をハードウェアで隔離する。  
- ソフトウェアキーはソフトウェアによる暗号化バックエンド。  

---

### 問2.13
設問：コンテナイメージの脆弱性スキャンやポリシー評価を自動化できるAzureサービスはどれか？  
A. Defender for Container Registries  
B. Azure Container Instances  
C. Azure Monitor  
D. Azure Policy  

解答：A  

解説：  
- Defender for Container RegistriesはAzure Container Registry (ACR) と連携し、イメージプッシュ時に脆弱性をスキャン／レポートする。  
- ACIはランタイム、Monitor/Policyは監視・ガバナンス用途。  

---

### 問2.14
設問：KubernetesクラスターでRBACをAzure ADと連携させるために利用するコンポーネントはどれか？  
A. Azure AD Pod Identity  
B. Azure AD Workload Identity  
C. Azure AD Authentication Plugin for kubectl  
D. Azure AD Domain Services  

解答：C  

解説：  
- kubectl用のAzure ADプラグインを使い、ユーザー認証をAzure ADで行い、そのトークンをKubernetes RBAC制御に利用する。  
- Pod Identity/Workload IdentityはマネージドIDで、Domain Servicesはドメインコントローラー機能。  

---

### 問2.15
設問：Azure VM環境で「ネスト仮想化（Nested Virtualization）」を有効にする前提条件はどれか？  
A. VM SKUがDv3/Ev3以上  
B. VMがWindows Server 2008 R2  
C. Azure Spot VMである  
D. VMがクラシックデプロイモデル  

解答：A  

解説：  
- Dv3やEv3などのシリーズはネスト仮想化に対応し、Hyper-Vホスト機能をVM上で動作させることができる。  
- 古いOSやクラシックモデル、Spot VMは対象外。  

---

### 問2.16
設問：コンテナイメージ配布時に改ざんを防ぐため、署名付きイメージを利用する標準技術はどれか？  
A. Notary（Docker Content Trust）  
B. TLS相互認証  
C. OAuth 2.0  
D. JWT  

解答：A  

解説：  
- NotaryとTUF (The Update Framework) により、コンテナイメージに対して署名・検証を行い、改ざんや置き換えリスクを低減する。  

---

### 問2.17
設問：Intel SGXやAMD SEVなどのプロセッサベース技術（Enclave Technology）は主にどの層で機能するか？  
A. アプリケーション層  
B. 仮想化ハイパーバイザー層  
C. プロセッサマイクロアーキテクチャ層  
D. ネットワーク層  

解答：C  

解説：  
- EnclaveはCPU内部のマイクロアーキテクチャレベルで動作し、メモリ暗号化やコード検証をハードウェアで実現する。  

---

### 問2.18
設問：多くのパブリッククラウドが準拠しているISO/IEC 27017は何に関する国際標準か？  
A. クラウドサービスのセキュリティ管理  
B. データプライバシー保護  
C. ISMS全般  
D. SLA管理  

解答：A  

解説：  
- ISO/IEC 27017はクラウドサービスプロバイダーと利用者の責任共有、ガイダンスを規定。Azureも27017/27018に適合している。  

---

### 問2.19
設問：オンプレミスおよびマルチクラウドの仮想マシンを単一の制御プレーンで管理し、セキュリティベースライン適用を自動化するAzureサービスはどれか？  
A. Azure Arc-enabled Servers  
B. Azure Policy  
C. Azure Blueprints  
D. Azure DevOps  

解答：A  

解説：  
- Azure Arcはオンプレ／他クラウドのサーバーをAzureリソースとして登録し、ポリシー適用やセキュリティセンタ連携が可能になる。  

---

### 問2.20
設問：仮想マシンの災害復旧（Disaster Recovery）をAzure上で実現するサービスはどれか？  
A. Azure Site Recovery  
B. Azure Backup  
C. Azure Monitor  
D. Azure Traffic Manager  

解答：A  

解説：  
- Site RecoveryはVMレプリケーション、フェールオーバー／フェールバック機能を提供し、DR計画の自動化とテストをサポートする。  
- Azure Backupはバックアップ、Monitorは監視、Traffic ManagerはDNSレベルのロードバランシング。  

---

Domain 2の20問を提示しました。  
次はDomain 3「Secure Network and Communication Infrastructure」を作成します。準備ができましたらお知らせください。
