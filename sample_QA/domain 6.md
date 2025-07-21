# Domain 6：Identity and Access Management Architecture（20問）

CISSP-ISSAP Domain 6「Identity and Access Management Architecture」に準拠した20問のサンプル問題です。日本語設問と英語原文を併記し、Microsoft Entra ID（旧Azure AD）など具体的事例を交えた解説を行います。

---

### 問6.1  
設問：オンプレミスActive DirectoryとAzure ADを連携する際に利用する推奨ツールはどれか？  
英語原文：Which tool is recommended for synchronizing on-premises Active Directory with Azure AD?  

A. Azure AD Connect  
B. Azure Migrate  
C. Azure Site Recovery  
D. Azure Arc  

解答：A  

解説：  
- Azure AD ConnectはオンプレADとMicrosoft Entra IDのパスワードハッシュ同期（PHS）／パススルー認証（PTA）／フェデレーション同期を設定できるハイブリッドID同期待機能。  
- Azure Migrateはサーバー移行、Site RecoveryはDR、Arcはハイブリッド管理用途。  

重要用語：  
- パスワードハッシュ同期（PHS: Password Hash Sync）  
- パススルー認証（PTA: Pass-through Authentication）  

---

### 問6.2  
設問：OAuth 2.0 の Authorization Code Grant フローでクライアントが最初に取得するのはどれか？  
英語原文：In OAuth 2.0 Authorization Code Grant flow, what does the client receive first?  

A. アクセストークン（Access Token）  
B. 認可コード（Authorization Code）  
C. リフレッシュトークン（Refresh Token）  
D. 署名付き ID トークン（ID Token）  

解答：B  

解説：  
- クライアントは最初に認可サーバからAuthorization Codeを受け取り、次にCodeを用いてAccess TokenやID Tokenを取得する。  
- Microsoft Entra IDではPKCE（Proof Key for Code Exchange）を併用し、Code盗聴防止強化が推奨される。  

関連用語：  
- PKCE（Proof Key for Code Exchange）  
- ID トークン（OIDC ID Token）  

---

### 問6.3  
設問：SAML 2.0 における SP-Initiated フローの特徴はどれか？  
英語原文：What characterizes an SP-Initiated flow in SAML 2.0?  

A. ユーザーが最初にサービスプロバイダー（SP）へアクセスする  
B. ユーザーが最初にアイデンティティプロバイダー（IdP）へアクセスする  
C. フロー中にOAuthトークンを使用する  
D. SPは常にフェデレーション Metadata を提供しない  

解答：A  

解説：  
- SP-Initiatedではユーザーがアプリ（SP）にアクセスすると、SPがIdPへSAML AuthnRequestをリダイレクトし、認証後にアサーションが返される。  
- Microsoft Entra IDをIdPとしたSAMLアプリ登録でも同様の流れを設定可能。  

---

### 問6.4  
設問：Zero Trustにおけるアイデンティティ保護（Identity Protection）の主な目的は何か？  
英語原文：What is the primary goal of Identity Protection in a Zero Trust model?  

A. シングルサインオンの実装  
B. リスクベース条件付きアクセスで不審なサインインを防止  
C. パスワードポリシーの強制のみ  
D. フェデレーションサービスの廃止  

解答：B  

解説：  
- Microsoft Entra ID Identity Protectionではサインインリスク・ユーザーリスクを評価し、条件付きアクセス（Conditional Access）とMFAを組み合わせて不正アクセスをブロックする。  
- SSOやパスワードポリシーは別機能。  

---

### 問6.5  
設問：RBAC（Role-Based Access Control）とABAC（Attribute-Based Access Control）の主な相違点は何か？  
英語原文：What is the key difference between Role-Based Access Control (RBAC) and Attribute-Based Access Control (ABAC)?  

A. RBAC は属性を用いず、ABAC はユーザーやリソースの属性でポリシーを定義  
B. RBAC は MFA を必須とする  
C. ABAC はプリンシパル単位のロール割り当てのみ  
D. RBAC は動的ポリシーをサポートしない  

解答：A  

解説：  
- RBACはユーザーにロールを割り当て、ロールに権限を紐付ける静的制御。  
- ABACはユーザー属性（例：部署、リスクスコア）、リソース属性、環境条件を基に動的にアクセス可否を判断する。  
- Microsoft Entra ID PEP＆PDPを使ったカスタム条件付きアクセスポリシーはABAC的機能を提供。  

---

### 問6.6  
設問：パスワードレス認証の実装で推奨されるFIDO2認証キーの特徴はどれか？  
英語原文：What is a recommended feature of a FIDO2 security key for passwordless authentication?  

A. 公開鍵／秘密鍵ペアをデバイス内で生成  
B. 秘密鍵をクラウドに保存  
C. HTTPのみをサポート  
D. OTPベースのみ  

解答：A  

解説：  
- FIDO2/WebAuthnではデバイス内でキーを生成・保護し、秘密鍵はデバイス外に流出しない仕組み。  
- OTPやクラウド保存は過去方式で、FIDO2は公開鍵暗号でパスワードレスを実現。  

関連用語：  
- WebAuthn  
- CTAP（Client to Authenticator Protocol）  

---

### 問6.7  
設問：SCIM（System for Cross-domain Identity Management）の主目的は何か？  
英語原文：What is the primary purpose of SCIM (System for Cross-domain Identity Management)?  

A. ユーザー／グループのプロビジョニング／デプロビジョニングの自動化  
B. シングルサインオンを実装  
C. IDフェデレーションのメタデータ管理  
D. 多要素認証フローの標準化  

解答：A  

解説：  
- SCIMはHTTP/REST APIとJSONを使い、IDライフサイクル管理（ユーザー作成、属性同期、削除）を自動化し、クラウドアプリケーションと統合する標準規格。  

---

### 問6.8  
設問：Microsoft Entra ID の PIM（Privileged Identity Management）で実現できない機能はどれか？  
英語原文：Which of the following cannot be accomplished using Microsoft Entra ID Privileged Identity Management (PIM)?  

A. 特権ロールの昇格要求ワークフロー  
B. アクセスレビューのスケジュール  
C. グローバル管理者の永続的割り当て自動拒否  
D. ロールの最小特権原則適用  

解答：C  

解説：  
- PIMでは昇格時に承認要求、期間限定アクセス、MFA強制、アクセスレビュー設定が可能。  
- ただし「永続的割り当て」をシステムが自動で拒否する機能はなく、手動レビューやガバナンスポリシー運用が必要。  

---

### 問6.9  
設問：OAuth 2.0 の Client Credentials Grant を利用するユースケースとして最適なのはどれか？  
英語原文：Which use case is most appropriate for OAuth 2.0 Client Credentials Grant?  

A. バックエンドサービス間の非対話型認証  
B. ユーザーログイン時の認証  
C. リソースオーナーによるパスワードリセット  
D. ブラウザベースのSPA認証  

解答：A  

解説：  
- Client Credentials Grantはサービス間通信（daemon-to-daemon）向けで、ユーザー介在なしにAccess Token取得し、APIを呼び出す場合に利用。  
- SPAやユーザー認証時にはAuthorization Code Grantを使用。  

---

### 問6.10  
設問：多要素認証（MFA）の「Something You Are」に該当する要素はどれか？  
英語原文：Which factor corresponds to “Something You Are” in Multi-Factor Authentication?  

A. 指紋認証  
B. ワンタイムパスワード  
C. スマートカード  
D. パスワード  

解答：A  

解説：  
- MFA要素は「Something You Know（知識）」「Something You Have（所持）」「Something You Are（生体情報）」。  
- 指紋や顔認証は生体情報、OTPは所持・知識混合、スマートカードは所持、パスワードは知識要素。  

---

### 問6.11  
設問：Identity Governance における Access Review の主目的は何か？  
英語原文：What is the primary purpose of Access Reviews in Identity Governance?  

A. アプリケーションのアップデートを管理  
B. 権限の適切性を定期的に検証し、不要権限を削除  
C. ネットワーク設定を最適化  
D. パスワードポリシーを更新  

解答：B  

解説：  
- Microsoft Entra ID Access Reviewsでは、グループやアプリケーションのアクセス権を定期的に関係者にレビューさせ、不必要な権限を自動除去し、最小権限を維持する。  

---

### 問6.12  
設問：B2Bコラボレーションで利用されるAzure AD機能はどれか？  
英語原文：Which Azure AD feature is used for B2B collaboration?  

A. 外部ユーザー招待（Guest Invitation）  
B. Azure AD Join  
C. Azure AD Connect Health  
D. Azure AD Connect Sync  

解答：A  

解説：  
- B2Bではゲストユーザー招待機能を使い、外部パートナーをAzure ADテナントに追加し、条件付きアクセスやアクセスレビューで管理できる。  

---

### 問6.13  
設問：IDフェデレーションのメタデータ交換に利用される標準XMLファイルはどれか？  
英語原文：Which standard XML file is used for metadata exchange in identity federation?  

A. SAML Metadata  
B. OAuth Discovery Document  
C. SCIM Schema  
D. OpenAPI Specification  

解答：A  

解説：  
- SAML Metadata XMLにはIdP/SPのエンドポイント、証明書情報、バインディング方式などが記述され、パートナー間で自動設定を可能にする。  

---

### 問6.14  
設問：IDプロビジョニングのベストプラクティスとして誤っているものはどれか？  
英語原文：Which is NOT a best practice for identity provisioning?  

A. 最小特権でアカウントを作成  
B. 自動プロビジョニング／デプロビジョニングを導入  
C. 単一の管理者アカウントを全員に共有  
D. アクセスレビューを設定  

解答：C  

解説：  
- 共有管理者アカウントは責任追跡を不可能にし、アカウントの誤用リスクを増大させるため、各ユーザーに固有アカウントを割り当てるべき。  

---

### 問6.15  
設問：Federated Authentication において、信頼を確立するために交換する英数字キーは何と呼ばれるか？  
英語原文：In federated authentication, what is the alphanumeric key exchanged to establish trust?  

A. 証明書フィンガープリント（Certificate Thumbprint）  
B. クライアントID  
C. セッションID  
D. Cookie  

解答：A  

解説：  
- IdP/SP間で交換／設定する証明書のThumbprintを利用し、正しい証明書かを検証してフェデレーション信頼を確立する。  

---

### 問6.16  
設問：Access Token と Refresh Token の主要な違いは何か？  
英語原文：What is the main difference between an Access Token and a Refresh Token?  

A. 有効期間（lifetime）が短いのが Access Token  
B. Access Token は常に JWT である  
C. Refresh Token はリソースアクセスに直接使用  
D. Access Token はクライアント認証に使われる  

解答：A  

解説：  
- Access Token は短時間（数分〜数時間）で有効期限切れとなり、API呼び出しに使われる。  
- Refresh Token は長期間有効で、再認証なしに新たなAccess Tokenを取得するために用いる。  

---

### 問6.17  
設問：プリンシパル・オブ・レスト（Principle of Least Privilege）適用において、RBACロールの「分離権限（Segregation of Duties）」を確保する方法はどれか？  
英語原文：How do you enforce Segregation of Duties when applying the Principle of Least Privilege using RBAC roles?  

A. 相反する操作を可能にするロールを同一ユーザーに割り当てる  
B. 相反する権限を持つロールセットを異なるグループに分け、レビューを強制  
C. 管理者アカウントを無制限に付与  
D. すべてのユーザーに同じロールを付与  

解答：B  

解説：  
- Segregation of Dutiesは一人のユーザーが相反操作を実行できないよう、ロールを分離し、アクセスレビューや承認ワークフローを組み合わせる。  

---

### 問6.18  
設問：パスワードリセットのセルフサービス機能をAzure ADで実装する際、追加で設定が必要なのはどれか？  
英語原文：When implementing self-service password reset in Azure AD, what must you configure additionally?  

A. 認証用連絡先情報（電話番号またはメール）  
B. セキュリティグループのネーミング規則  
C. Azure Site Recovery の構成  
D. Azure DDoS Protection のポリシー  

解答：A  

解説：  
- SSPR(Self-Service Password Reset)では、ユーザーが電話番号や代替メールアドレスで本人確認できるように、認証用連絡先情報の登録を必須に設定する必要がある。  

---

### 問6.19  
設問：OAuth 2.0 の Device Code Grant フローに最適なユースケースはどれか？  
英語原文：Which scenario is most suitable for the OAuth 2.0 Device Code Grant flow?  

A. 入力デバイスが制限されたIoTデバイスでのユーザー認証  
B. ブラウザベースのシングルページアプリケーション  
C. サーバーレス関数のバックエンド認証  
D. ウェブブラウザからの標準ログイン  

解答：A  

解説：  
- Device Code Grantはユーザー入力が困難なデバイス（IoT、スマートTV）向けに、別デバイスでコードを入力し認証するフローを提供する。  

---

### 問6.20  
設問：パスワードポリシーで「文字の複雑性（Password Complexity）」を要求するときに必要な設定項目として誤っているものはどれか？  
英語原文：Which of the following is NOT required when enforcing password complexity in policy settings?  

A. 最小文字数  
B. 大文字・小文字の混在  
C. 特殊文字の使用  
D. パスワード履歴の保存数  

解答：D  

解説：  
- 文字の複雑性要件には長さ、大文字・小文字・数字・特殊文字の組み合わせ設定が含まれる。  
- パスワード履歴は再利用防止のポリシーであり、複雑性要件ではない。  

---

以上でDomain 6の20問を提供しました。  
本シリーズで125問すべてのサンプル問題を提示し終えましたが、追加で解説強化や模擬試験形式のPDF生成などご要望があればお知らせください。
