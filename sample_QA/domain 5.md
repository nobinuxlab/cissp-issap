# Domain 5：Security Architecture Evaluation and Assessment（20問）

CISSP-ISSAP Domain 5「Security Architecture Evaluation and Assessment」に準拠した20問です。設問は日本語と英語原文を併記し、解説ではAzure や Microsoft Defender など具体的製品を例示しながら解説します。

---

### 問5.1  
設問：セキュリティアーキテクチャのギャップ分析（Gap Analysis）を行う主な目的はどれか？  
英語原文：What is the primary purpose of performing a security architecture gap analysis?  

A. 将来の技術トレンドを予測する  
B. 現状の設計と要件／ベストプラクティスとの不整合を特定する  
C. システムのパフォーマンス問題を解決する  
D. コスト削減の機会を洗い出す  

解答：B  

解説：  
- ギャップ分析は現状のアーキテクチャと、規格（例：NIST SP 800-53）や自社ポリシーとの間にある不整合を明らかにし、改善策を導出する。  
- コストやパフォーマンスは二次的関心であり、主目的は要件適合性の評価。  

---

### 問5.2  
設問：Threat Modeling 手法のうち、データフロー図（DFD）を利用し脅威を可視化する代表的手法はどれか？  
英語原文：Which threat modeling technique uses Data Flow Diagrams (DFDs) to visualize and identify threats?  

A. PASTA (Process for Attack Simulation and Threat Analysis)  
B. OCTAVE  
C. STRIDE  
D. FAIR  

解答：C  

解説：  
- STRIDE はDFD 上で各要素（プロセス／データストア／インターフェース）を分析し、Spoofing, Tampering, Repudiationなどの脅威を可視化する。  
- PASTAはシナリオ重視、OCTAVEは組織リスク、FAIRは定量リスク分析に特化。  

---

### 問5.3  
設問：コードレビューで「静的アプリケーションセキュリティテスト（SAST）」を行うメリットはどれか？  
英語原文：What is a key benefit of performing Static Application Security Testing (SAST) during code review?  

A. 実行時の脆弱性をリアルタイム検知できる  
B. ソースコードレベルで脆弱性パターンを早期に発見できる  
C. マイクロサービス間通信を可視化できる  
D. ライブラリ依存関係を動的にスキャンできる  

解答：B  

解説：  
- SAST は開発サイクルの早期段階でソースコードをスキャンし、SQLインジェクションやクロスサイトスクリプティングなどの脆弱性を検出する。  
- 実行時分析はDAST、依存関係スキャンはSoftware Composition Analysis (SCA) の役割。  

---

### 問5.4  
設問：ペネトレーションテスト (Penetration Test) の結果をアーキテクチャ評価に活かす最適な方法はどれか？  
英語原文：What is the best way to incorporate penetration testing results into architecture assessment?  

A. 結果を運用チームだけで共有  
B. テストシナリオと脆弱性を設計ドキュメントにフィードバックし、再設計する  
C. テスト後 6 か月間は再テストを行わない  
D. テスト結果をそのままスコアとしてアーキテクチャ評価に用いる  

解答：B  

解説：  
- ペンテストの脆弱性・攻撃パスを設計ドキュメントへ反映し、アーキテクチャ設計段階で制御追加や修正を行う。  
- 運用チームだけの共有は不十分、6か月放置や単純スコアは改善策に結びつかない。  

---

### 問5.5  
設問：Security Architecture Review Board (SARB) の主な役割は何か？  
英語原文：What is the primary role of a Security Architecture Review Board (SARB)?  

A. 開発進捗のトラッキング  
B. 新規アーキテクチャ変更のセキュリティ適合性を審査・承認  
C. 予算承認フローの管理  
D. 運用インシデントの即時対応  

解答：B  

解説：  
- SARB は新規設計やアーキテクチャ変更に対してリスクやベストプラクティスとの適合性を審査し、承認または改善指示を行うガバナンス機能。  
- 開発管理や予算、インシデント対応は別組織が担う。  

---

### 問5.6  
設問：Continuous Control Monitoring (CCM) を実装する際に有効な Azure サービスの組み合わせはどれか？  
英語原文：Which combination of Azure services is effective for Continuous Control Monitoring (CCM)?  

A. Azure Policy + Azure Monitor + Microsoft Defender for Cloud  
B. Azure DevOps + Azure Repos + Azure Pipelines  
C. Azure Batch + Azure Functions + Azure Logic Apps  
D. Azure SQL + Azure Synapse Analytics  

解答：A  

解説：  
- Azure Policy でガバナンス違反を検知／自動修復、Azure Monitor でメトリクス収集、Defender for Cloud でセキュリティアラート監視を行うことで、CCM を実現する。  

---

### 問5.7  
設問：SBOM（Software Bill of Materials）をセキュリティアセスメントに取り込む主なメリットはどれか？  
英語原文：What is the main benefit of incorporating SBOM (Software Bill of Materials) into security assessment?  

A. 実行時パフォーマンス向上  
B. ソフトウェア内の部品・ライブラリ依存関係を把握し、脆弱性を特定しやすくする  
C. ユーザーアクセスログを管理  
D. システムのバックアップ自動化  

解答：B  

解説：  
- SBOM はインストール済みコンポーネントをリスト化し、既知の脆弱性（CVE）とのマッピングを容易にして脆弱性管理を迅速化する。  

---

### 問5.8  
設問：リスクアセスメントの定量的手法 FAIR（Factor Analysis of Information Risk）の特徴は何か？  
英語原文：What characterizes the quantitative risk assessment method FAIR (Factor Analysis of Information Risk)?  

A. フレームワークが包括的過ぎて使いづらい  
B. 定性的なスコアのみを出力する  
C. 経済的影響（損失額）を見積もることに重点を置く  
D. ISO/IEC 27001 の必須要件である  

解答：C  

解説：  
- FAIR はリスクを貨幣価値で表現し、損失頻度や影響度を定量モデルに基づき評価する。  
- 定性的なフレームワークではなく、金額ベースの定量化が特徴。  

---

### 問5.9  
設問：PCI DSS レベル1 準拠のクラウド環境評価で特に重視すべき項目はどれか？  
英語原文：In assessing a cloud environment for PCI DSS Level 1 compliance, which area is most critical?  

A. ストレージサイズの最適化  
B. カード会員データの暗号化とキー管理  
C. パフォーマンステストの実施  
D. 予算管理プロセス  

解答：B  

解説：  
- PCI DSS ではカード会員データ（PAN等）の暗号化及びキー管理が最重要で、FIPS 140-2 準拠の HSM（Azure Key Vault Managed HSM）利用が推奨される。  

---

### 問5.10  
設問：ISO/IEC 27001 の内部監査でチェックすべき「A.12 運用セキュリティ」のコントロール例はどれか？  
英語原文：Which control example under “A.12 Operational Security” should be checked in an ISO/IEC 27001 internal audit?  

A. アクセス制御ポリシーの文書化  
B. システム変更管理プロセスの遵守状況  
C. 取引先与信チェック  
D. 投資評価手法  

解答：B  

解説：  
- A.12.1.2 などでシステム変更管理（Change Management）の適用・承認プロセスを評価し、不正変更や設定ミスのリスクを抑制する。  

---

### 問5.11  
設問：セキュリティメトリクスとして KPI（Key Performance Indicator）と KRI（Key Risk Indicator）の主な違いは何か？  
英語原文：What is the main difference between a KPI (Key Performance Indicator) and a KRI (Key Risk Indicator) in security metrics?  

A. KPI はリスクを示し、KRI は業務実績を示す  
B. KPI はプロセス／実行状況を測定し、KRI はリスク発生の兆候を測定  
C. KPI と KRI は同じ意味で使われる  
D. KRI は財務指標のみを扱う  

解答：B  

解説：  
- KPI はパッチ適用率／脆弱性修正時間など実行プロセスの性能評価指標、KRI はインシデント発生率やリスク増加の先行指標として機能する。  

---

### 問5.12  
設問：FedRAMP 認証を受けたサービスプロバイダーの評価ドキュメント「Security Assessment Report (SAR)」の目的は何か？  
英語原文：What is the purpose of the FedRAMP “Security Assessment Report (SAR)” document?  

A. サービスの費用見積もりを提示する  
B. 独立監査機関が実施したコントロール評価の詳細結果をまとめる  
C. SLA の詳細条件を記載する  
D. 事業継続計画を説明する  

解答：B  

解説：  
- SAR は第三者評価機関（3PAO）がFedRAMPコントロール（NIST SP 800-53）への準拠状況をテスト結果とともに報告し、認証プロセスの根拠となる。  

---

### 問5.13  
設問：セキュリティ設計レビュー (Security Design Review) の成果物として不適切なのはどれか？  
英語原文：Which of the following is NOT an appropriate deliverable of a Security Design Review?  

A. 脅威モデリング結果レポート  
B. コントロールギャップ分析シート  
C. アーキテクチャ実装コード  
D. リスク対応計画  

解答：C  

解説：  
- 設計レビューでは脅威やギャップ、リスク対応を文書化するが、実装コード自体はレビュー成果物ではなく、レビュー対象になる。  

---

### 問5.14  
設問：Azure Blueprint を使ったセキュリティアセスメント自動化で提供できない機能はどれか？  
英語原文：Which functionality cannot be provided by Azure Blueprints when automating security assessment?  

A. リソースグループとポリシーの一括展開  
B. リソースのタグ付けルール適用  
C. ライブトラフィックの侵入検知  
D. カスタムロール定義の配布  

解答：C  

解説：  
- Blueprints はテンプレートとしてリソース配備／ポリシー適用／ロール配布を自動化する。侵入検知は Defender for Cloud など別サービスの領域。  

---

### 問5.15  
設問：リスクに基づく監査（Risk-Based Audit）の特徴はどれか？  
英語原文：Which describes a characteristic of a risk-based audit?  

A. 監査対象を固定し、毎年同じ手順で実施する  
B. リスク評価結果に応じて優先順位を付け、重点的に監査を行う  
C. 組織規模に関係なく同一のチェックリストを用いる  
D. 監査範囲を常に全システムとする  

解答：B  

解説：  
- リスクベース監査は定量／定性評価に基づき、重要度の高いリスク領域へリソースを集中して監査活動を行う。  

---

### 問5.16  
設問：Code Signing 証明書の有効性を継続的に検証し、不正なバイナリ配布を防止するために導入すべきプロセスはどれか？  
英語原文：What process should be implemented to continuously validate code signing certificates and prevent unauthorized binary distribution?  

A. 証明書有効期限の手動監査のみ  
B. CI/CD パイプライン内での自動署名検証  
C. 開発者による目視チェックのみ  
D. 実行環境でのランタイム署名スキップ  

解答：B  

解説：  
- CI/CD のビルド／リリースプロセスで証明書チェーン、失効状況、署名アルゴリズムを自動検証し、不正なバイナリがデプロイされないようにする。  

---

### 問5.17  
設問：セキュリティ成熟度モデル（CMMI 等）で「定義済み（Defined）」レベルに該当する特徴はどれか？  
英語原文：Which characteristic corresponds to the “Defined” level in a maturity model like CMMI?  

A. プロセスが組織内で標準化／ドキュメント化されている  
B. プロセス成果物がリアクティブに作成される  
C. プロセスが測定されず最適化されていない  
D. プロセスが初期段階で非公式に実施される  

解答：A  

解説：  
- Defined レベルではプロセスが組織標準として文書化され、プロジェクト間で一貫した実行が保証される。  

---

### 問5.18  
設問：セキュリティアセスメントで使用する「成熟度指標（Maturity Indicator）」「コンピテンシー指標（Competency Indicator）」の違いは何か？  
英語原文：What distinguishes a “Maturity Indicator” from a “Competency Indicator” in security assessments?  

A. Maturity はプロセス状態、Competency は個人のスキルレベルを評価  
B. 両者は同じものを指す  
C. Competency はシステム性能を示す  
D. Maturity は SLA 遵守率のみを測定  

解答：A  

解説：  
- Maturity Indicator は組織プロセスやツールの成熟度を示す指標、Competency Indicator は担当者やチームのスキル・知識を測る指標。  

---

### 問5.19  
設問：Security Control Framework（NIST, ISO, COBIT）間のギャップを比較する際に最適な手法はどれか？  
英語原文：Which approach is best for comparing gaps between different security control frameworks (NIST, ISO, COBIT)?  

A. マッピングマトリクスを作成し、コントロール要件を対比  
B. それぞれのフレームワークを個別に監査  
C. ガバナンスチームに一任  
D. 予算比率で評価  

解答：A  

解説：  
- マッピングマトリクスで NIST SP 800-53 のコントロールと ISO/IEC 27001 の Annex A を対比し、重複や不足を視覚化して体系的にギャップを分析する。  

---

### 問5.20  
設問：Continuous Red Teaming のメリットとして最も適切なのはどれか？  
英語原文：Which is the most appropriate benefit of Continuous Red Teaming?  

A. マニュアルによる年次評価のみで十分になる  
B. エンドポイント管理を廃止できる  
C. 実環境での攻撃シナリオを定期的に検証し、改善サイクルを迅速化できる  
D. ネットワークトラフィックを一切監視しない  

解答：C  

解説：  
- Continuous Red Teaming は攻撃者視点の演習を頻繁に行い、検知・対応体制の弱点をリアルタイムに把握して改善を加速する。  
- 年次評価や管理廃止は誤解であり、監視は必須。  

---

以上でDomain 5の20問を提供しました。  
次は Domain 6「Identity and Access Management Architecture」を作成します。準備ができましたらお知らせください。
