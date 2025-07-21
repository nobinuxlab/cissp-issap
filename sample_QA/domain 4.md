# Domain 4：Secure Data Storage and Lifecycle Management（20問）

CISSP-ISSAP Domain 4「Secure Data Storage and Lifecycle Management」に準拠した20問です。設問は日本語と英語原文を併記し、Microsoft Azure製品事例も交えて解説します。

---

### 問4.1  
設問：Azure Data Lake Storage Gen2 でデータを保存時に SSE-CMK (Server-Side Encryption with Customer-Managed Keys) を利用するには何を構成すべきか？  
（英語原文：To use SSE-CMK with Azure Data Lake Storage Gen2, which configuration is required?）

A. Storage Account の Encryption Scope に CMK を指定  
B. Azure Disk Encryption を適用  
C. Always Encrypted を有効化  
D. Azure Confidential VM 上にデータを格納  

解答：A  

解説：  
- SSE-CMK では Storage Account の Encryption Scope（暗号化範囲）に Azure Key Vault の Customer-Managed Key（CMK）を設定し、データ書き込み時に指定キーで自動暗号化する。  
- Azure Disk Encryption は VM OS/データディスク、Always Encrypted は SQL Database クライアント側暗号化、Confidential VM はデータ使用時暗号化。  

---

### 問4.2  
設問：Transparent Data Encryption（TDE）と Always Encrypted の主な違いは何か？  
（英語原文：What is the primary difference between Transparent Data Encryption (TDE) and Always Encrypted?）

A. TDE はストレージ層で暗号化、Always Encrypted はクライアント側で暗号化  
B. TDE はホスト OS を暗号化、Always Encrypted はディスクを暗号化  
C. 両者とも同じレイヤーで動作  
D. Always Encrypted は Azure Key Vault を必要としない  

解答：A  

解説：  
- TDE はデータベースファイル・バックアップの暗号化を透過的に行い、サーバ側で復号／暗号化を実施。  
- Always Encrypted はクライアントドライバーがアプリケーション層で暗号化キーを用いて列単位の暗号／復号を行い、サーバは平文を扱わない。  

---

### 問4.3  
設問：Azure Blob Storage に不変ストレージ（WORM：Write Once, Read Many）を実装する機能はどれか？  
（英語原文：Which feature implements Write Once, Read Many (WORM) in Azure Blob Storage?）

A. コンテナ単位のイミュータブルポリシー（Immutability Policy）  
B. ソフトデリート（Soft Delete）  
C. ライフサイクル管理（Lifecycle Management）  
D. Managed Disk Encryption  

解答：A  

解説：  
- イミュータブルポリシーを有効化したコンテナでは、保管期間中の削除・上書きを禁止し、規制コンプライアンスを実現。  
- ソフトデリートは誤削除復旧、ライフサイクル管理はTier移行・自動削除、Managed Disk Encryption は VM ディスク暗号化。  

---

### 問4.4  
設問：Azure Blob Storage のライフサイクル管理ルールで「アクセス頻度が低いデータを180日後にArchiveに移行」させたい。どのフィルター条件を設定すべきか？  
（英語原文：Which filter condition should you set to move rarely accessed data to Archive after 180 days?）

A. lastAccessTime ≥ 180 days  
B. creationTime ≥ 180 days  
C. accessTier = Hot  
D. blobType = PageBlob  

解答：A  

解説：  
- lastAccessTime フィルターを用い、最終アクセスから指定日数経過したオブジェクトをArchive層に移行できる。  
- creationTime は作成日ベース、accessTier と blobType は移行対象絞り込みではなく属性指定。  

---

### 問4.5  
設問：企業データの自動分類とメタデータ管理に最適な Azure サービスはどれか？  
（英語原文：Which Azure service is best suited for automated data classification and metadata management?）

A. Azure Purview  
B. Azure Policy  
C. Azure Defender for Storage  
D. Azure StorSimple  

解答：A  

解説：  
- Azure Purview はデータカタログと自動スキャン機能を備え、機密ラベル付与や系統系（データリネージ）を可視化する。  
- Policy はリソースガバナンス、Defender for Storage は脅威検知、StorSimple はハイブリッドストレージ。  

---

### 問4.6  
設問：Microsoft Information Protection（MIP）で機密度に応じたファイル保護を行うには何を利用すべきか？  
（英語原文：What should you use in Microsoft Information Protection (MIP) to enforce file protection by sensitivity?）

A. 感度ラベル（Sensitivity Labels）  
B. Azure AD Conditional Access  
C. Azure Disk Encryption  
D. Azure Key Vault シークレット  

解答：A  

解説：  
- 感度ラベルはドキュメントやメールに暗号化・アクセス制限をポリシーとして紐付け、EOP/Defenderとも連携してファイル持ち出し保護を実現。  
- Conditional Access は認証制御、Disk Encryption/Key Vault はストレージ／キー管理。  

---

### 問4.7  
設問：Bring Your Own Key（BYOK）で Azure Key Vault に鍵をインポートする際、FIPS 140-2 Level 2 準拠を満たすオプションはどれか？  
（英語原文：Which option meets FIPS 140-2 Level 2 compliance when importing keys via BYOK into Azure Key Vault?）

A. Managed HSM を使用  
B. ソフトウェア保管キーをインポート  
C. Azure Disk Encryption Key Vault エクスポートキー  
D. Azure App Service 証明書  

解答：A  

解説：  
- Managed HSM は FIPS 140-2 Level 2/3 準拠のハードウェアセキュリティモジュールをクラウド提供し、BYOK でのキー格納に最適。  
- ソフトウェアキーは準拠外、Disk Encryption エクスポートキー／App Service 証明書は用途が異なる。  

---

### 問4.8  
設問：分散鍵管理で n-of-m スキーム（例：Shamir’s Secret Sharing）を採用する主なメリットはどれか？  
（英語原文：What is the main benefit of using an n-of-m scheme like Shamir’s Secret Sharing in distributed key management?）

A. キーの可用性と冗長性を向上しつつ、単一障害点を排除  
B. 暗号化パフォーマンスを劇的に向上  
C. キー管理ポリシーを不要にする  
D. クライアント側暗号化を省略  

解答：A  

解説：  
- n-of-m スキームは鍵を複数の断片に分割し、一部の断片で復元可能にすることで、キーの可用性とセキュリティを両立。  
- パフォーマンス向上やポリシー削減、クライアント暗号化省略は主目的ではない。  

---

### 問4.9  
設問：バックアップの「3-2-1 ルール」を Azure 上で実践する最適な組み合わせはどれか？  
（英語原文：Which combination best implements the 3-2-1 backup rule in Azure?）

A. Azure VM→Managed Disk Snapshots→Geo-Redundant Storage (GRS)  
B. Azure VM→Local SSD→Azure Monitor  
C. Azure SQL→TDE→Always On 可用性グループ  
D. Azure Files→File Sync→Blob Storage  

解答：A  

解説：  
- 3 枚のバックアップ（スナップショット＋GRS 複製）、2 種類のメディア（ディスク＋Blob）、1 つのオフサイト複製（GRS）でルールを満たす。  
- 他選択肢は要件不十分または用途が異なる。  

---

### 問4.10  
設問：SSD ドライブのメディア消去に NIST SP 800-88 の「Clear」として該当する手法はどれか？  
（英語原文：Which method corresponds to “Clear” per NIST SP 800-88 for SSD media sanitization?）

A. 暗号化キーの破棄  
B. デガウス  
C. 上書きパターンを複数回書き込む  
D. 物理破壊  

解答：A  

解説：  
- SSD ではドライブ全体を暗号化 (Self-Encrypting Drive) し、消去時に暗号化キーを破棄する「Crypto Erase」が Clear に該当。  
- デガウス／物理破壊は Purge／Destroy、上書きは HDD 向け。  

---

### 問4.11  
設問：Azure Blob Storage のイミュータブルポリシーをコンプライアンスに適用する際、保持ロック (Retention Policy Lock) の効果は何か？  
（英語原文：What is the effect of enabling retention policy lock in Azure Blob Storage immutability policy?）

A. 既存ポリシーの削除・無効化を永続的に禁止  
B. ソフトデリートの復元期間延長  
C. ライフサイクルルールの自動適用  
D. Blob タイプを変更可能にする  

解答：A  

解説：  
- Retention Policy Lock を有効化すると、保持期間中はポリシー自体の変更・解除ができず、法規対応の証跡を保証する。  

---

### 問4.12  
設問：GDPR の「消去権（Right to Erasure）」を遵守するため、バックアップデータから個人情報を削除する最適手順はどれか？  
（英語原文：Which procedure best supports GDPR’s Right to Erasure when removing personal data from backups?）

A. バックアップから該当レコードを削除し、インクリメンタルバックアップを再実行  
B. バックアップをすべて廃棄  
C. バックアップ上の暗号化キーを破棄  
D. ディスクの再フォーマット  

解答：A  

解説：  
- 該当レコード削除→ベースバックアップとインクリメンタル再実行で個人データを除去し、最小限の影響で消去権に対応。  
- バックアップ全面廃棄は業務継続性を損なう。  

---

### 問4.13  
設問：オンプレミスファイルサーバにある機密ファイルを自動検出し、クラウドに移行する際に利用すべき Microsoft サービスはどれか？  
（英語原文：Which Microsoft service should you use to automatically discover and migrate sensitive files from on-premises file servers to the cloud?）

A. Azure Information Protection Scanner  
B. Azure Migrate  
C. Azure Bastion  
D. Azure Policy  

解答：A  

解説：  
- AIP Scanner はオンプレミスのファイルサーバをスキャンし、機密ラベル付与→Azure Blob/Security Centre連携でクラウド保護へ自動移行可能。  

---

### 問4.14  
設問：Microsoft Purview eDiscovery で「法的保留（Legal Hold）」を設定すると発生する効果は何か？  
（英語原文：What effect does placing a Legal Hold in Microsoft Purview eDiscovery have?）

A. 保留対象アイテムの改変・削除を防止  
B. データを自動アーカイブ  
C. MFA を強制  
D. データ暗号化鍵をローテーション  

解答：A  

解説：  
- Legal Hold を設定すると、対象メール・ドキュメントは検索時にも削除・編集不可となり、証拠保全を担保する。  

---

### 問4.15  
設問：電子署名を Azure Key Vault で安全に行うための最適なアプローチはどれか？  
（英語原文：Which approach is best for performing secure digital signatures using Azure Key Vault?）

A. ハードウェアセキュリティモジュール (HSM) キーを用いた署名 API  
B. ソフトウェアシークレットにエクスポートして署名  
C. クライアント証明書でマニュアル署名  
D. Azure Disk Encryption キーを共有  

解答：A  

解説：  
- Managed HSM の非エクスポート鍵を Key Vault Signing API 経由で利用し、署名プロセスをハードウェア分離で実行。  

---

### 問4.16  
設問：Azure Blob のソフトデリート (Soft Delete) とイミュータブルポリシーの棲み分けとして正しいものはどれか？  
（英語原文：Which statement correctly differentiates soft delete from immutability policy in Azure Blob?）

A. ソフトデリートは誤削除復旧、イミュータブルポリシーは削除禁止  
B. 両者とも削除を防止する  
C. ソフトデリートは WORM 保護、イミュータブルは復元のみ  
D. どちらもポリシーロックが不要  

解答：A  

解説：  
- Soft Delete は削除後に一定期間復元可能にし、Immutability は保持期間中の削除・上書きを禁止する。  

---

### 問4.17  
設問：Azure VM のディスク暗号化 (Azure Disk Encryption) と Azure Storage Service Encryption (SSE) の違いとして誤っているものはどれか？  
（英語原文：Which statement about Azure Disk Encryption vs. Storage Service Encryption (SSE) is FALSE?）

A. Disk Encryption は VM OS/データディスクを BitLocker/DM-Crypt で暗号化  
B. SSE は Blob/Table/Queue データを自動暗号化  
C. SSE は Azure Files を暗号化しない  
D. Disk Encryption には Key Vault キーが必要  

解答：C  

解説：  
- SSE は Azure Files も含めたストレージサービス全体を暗号化可能（Azure Files SSE 対応）。  

---

### 問4.18  
設問：Confidential Computing を用いて「データ使用時の暗号化」を実現できる Azure サービスはどれか？  
（英語原文：Which Azure service provides encryption of data in use via Confidential Computing?）

A. Azure Confidential Computing VM  
B. Azure Key Vault  
C. Azure Storage Service Encryption  
D. Azure Backup  

解答：A  

解説：  
- Confidential VM は Intel SGX/AMD SEV を活用し、メモリ内データをハードウェアで暗号化しつつ処理可能にする。  

---

### 問4.19  
設問：FIPS 140-2 準拠のキー管理をクラウドネイティブで実現する際、選択すべきコンポーネントはどれか？  
（英語原文：Which component should you choose to achieve FIPS 140-2 compliance in cloud-native key management?）

A. Azure Key Vault Managed HSM  
B. Azure App Service シークレット  
C. Azure Disk Encryption  
D. Azure Information Protection  

解答：A  

解説：  
- Managed HSM は FIPS 140-2 Level 2/3 認定を受けた HSM を SaaS で提供し、クラウド鍵管理の基盤となる。  

---

### 問4.20  
設問：監査ログを Log Analytics ワークスペースに保存し、コストを最適化するための適切なデータ保持とテーブル設定はどれか？  
（英語原文：What is the appropriate data retention and table settings to optimize cost when storing audit logs in a Log Analytics workspace?）

A. 30日保持＋Archive テーブルへの移行ルール設定  
B. 無制限保持＋Retention Lock  
C. 14日保持＋Daily Export  
D. 90日保持＋Live テーブルの自動スケーリング  

解答：A  

解説：  
- 直近 30 日間を Live テーブルに保持し、古いログを Archive テーブルに移行することでホットストレージコストを削減できる。  
- 無制限や長期間 Live 保存はコスト増、Daily Export は運用負荷増加。  

---

Domain 4 の20問を提示しました。  
次は Domain 5「Security Architecture Evaluation and Assessment」を作成します。準備できましたらお知らせください。
