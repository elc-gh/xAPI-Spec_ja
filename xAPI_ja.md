# Experience API
## Advanced Distributed Learning (ADL) Co-Laboratories

### 2014.8.1 日本語版
### 「Tin Canプロジェクト」
特定非営利活動法人日本イーラーニングコンソシアムとモバイルラーニングコンソシアムは、共同で「Tin Canプロジェクト」を発足しました。この文書は、「Tin Canプロジェクト」メンバーが、Experience API（v1.0.1）を日本語に翻訳したものです。

この文書についての問い合わせは、以下にお願いします。

tincan@elc.or.jp

### 「Tin Canプロジェクト」　日本語版制作メンバー（五十音順）

伊藤彰孝（株式会社 ベネッセコーポレーション）

勝田祥生（株式会社レビックグローバル）

加藤泰久（NTTラーニングシステムズ株式会社）

熊澤　剛（株式会社ヒューマンサイエンス）

佐伯秀雄（NTTラーニングシステムズ株式会社）

田中頼人（早稲田大学）

徳弘太郎（ヤマハ株式会社)

藤井直人（TinCanプロジェクト・リーダー　株式会社ヌーサイト）

星野忠明（エスエイティーティー株式会社）

程田恭介（株式会社富士通ラーニングメディア）

前田　宏（株式会社ジンジャーアップ）

> Copyright 2013 Advanced Distributed Learning (ADL) Initiative, U.S. Department of Defence

> Apache License, Version 2.0（以下、ライセンス）によって、ライセンスされています。ライ
> センスに従わない場合、この文章を利用することはできません。ライセンスのコピーは、
> http://www.apache.org/licenses/LICENSE-2.0 で入手することができます。

> 適用可能な法律による要求や、文書による合意がない場合、ライセンスに基づいて提供される
> ソフトウェアは "as-is" （現状のまま）を基本とし、表現されたか、あるいは暗示されかを問
> わず、いかなる保証や契約条件も提供しません。ライセンスにおいて示される許可事項や制限
> 事項については、ライセンス内の文言を確認してください。

>この文書は、Experience API ワーキンググループのメンバー（2.2.1 の表を参照）が、国防
>次官補室（即応性担当）の Advanced Distributed Learning (ADL) イニシアティブを支援し
>作成しました。フィードバックやお問い合わせは、helpdesk@adlnet.gov までお送りください。

<div style="page-break-after: always;"></div>

## 目次
*   1.0.    [改定履歴](#revhistory)
*   2.0.    [Experience API の役割](#roleofxapi)
    *   2.1.    [xAPI における ADL の位置づけ](#adlrole)
    *   2.2.    [貢献者](#contributors)
        *   2.2.1.  [ワーキンググループの参加者](#wg)
        *   2.2.2.  [要求仕様収集への貢献者](#reqparticipants)
    *   2.3 [>技術に詳しくない人への読み方ガイドライン](#readingguidelines)
*   3.0.    [用語の定義](#defintions)
*   4.0.    [ステートメント](#statement)
    *   4.1.    [ステートメントプロパティ](#stmtprops)
        *   4.1.1.  [id (識別子)](#stmtid)
        *   4.1.2.  [Actor (アクタ)](#actor)
        *   4.1.3.  [Verb (動詞)](#verb)
        *   4.1.4.  [Object (目的語)](#object)
        *   4.1.5.  [Result (結果)](#result)
        *   4.1.6.  [Context (文脈)](#context)
        *   4.1.7.  [Timestamp (タイムスタンプ)](#timestamp)
        *   4.1.8.  [Stored](#stored)
        *   4.1.9.  [Authority (権限)](#authority)
        *   4.1.10. [Version (バージョン)](#version)
        *   4.1.11. [Attachments (添付資料)](#attachments)
        *   4.1.12. [データの制約](#dataconstraints)
    *   4.2.    [ステートメントの検索](#retstmts)
    *   4.3.    [無効](#voided)
    *   4.4.    [署名付きステートメント](#signature)
*   5.0.    [各種タイプ](#misctypes)
    *   5.1.    [ドキュメント](#miscdocument)
    *   5.2.    [言語マップ](#misclangmap)
    *   5.3.    [拡張](#miscext)
    *   5.4.    [識別子メタデータ](#miscmeta)
*   6.0.    [ランタイム通信](#rtcom)
    *   6.1.    [エンコーディング](#encoding)
    *   6.2.    [API のバージョン管理](#apiversioning)
    *   6.3.    [同時実行](#concurrency)
    *   6.4.    [セキュリティ](#security)
        *   6.4.1.  [各シナリオの取り扱い方法](#authdefs)
        *   6.4.2.  [OAuth 認証スコープ](#oauthscope)
*   7.0.    [Data Transfer (REST)](#datatransfer)
    *   7.1.    [エラーコード](#errorcodes)
    *   7.2.    [ステートメント API](#stmtapi)
        *   7.2.1 [PUT ステートメント](#stmtapiput)
        *   7.2.2 [POST ステートメント](#stmtapipost)
        *   7.2.3 [GET ステートメント](#stmtapiget)
        *   7.2.4 [無効化されたステートメント](#voidedStatements)
    *   7.3.    [ドキュメント API](#docapis)
    *   7.4.    [ステート API](#stateapi)
    *   7.5.    [アクティビティプロファイル API](#actprofapi)
    *   7.6.    [エージェントプロファイル API](#agentprofapi)
    *   7.7.    [About リソース](#aboutresource)
    *   7.8.    [クロスオリジンリクエスト](#cors)
    *   7.9.    [バリデーション](#validation)
    *   7.10.   [HTTP HEAD](#httphead)
*   [Appendix A: ステートメント例](#AppendixA)
*   [Appendix B: 異なるタイプのステートメントオブジェクト例](#AppendixB)
*   [Appendix C: アクティビティタイプ "cmi.interaction" のための定義例](#AppendixC)
*   [Appendix D: 1.0.0 形式のステートメントへの変換](#AppendixD)
*   [Appendix E: サイン付きステートメントの例](#AppendixE)
*   [Appendix F: 全てのエンドポイントの表](#AppendixF)

<div style="page-break-after: always;"></div>
<a name="revhistory"/></a>
## 1.0 改定履歴
###### 0.8 (Project Tin Can API の配布）から 0.9 (2012/03/31)

Project Tin Can API を提供した Rustici Software が、2012年4月のキックオフ会議に先立ち、API に対する改定を行った。会議において投票が行われ、それらの改定を仕様書に取り込み、第0.9版とすることが議決された。

###### 0.90 から 0.95 (2012/08/31)

"コア"とされる動詞とアクティビティタイプが仕様書より削除された。また、結果、文脈、インタラクション、およびアクティビティ定義における、それらの動詞への参照も同時に削除された。実装者には、自ら動詞を定義するよりも、コミュニティが定義した動詞を利用することが推奨された。

- 動詞、アクティビティタイプ、拡張キーを URI とする。
- いくつかの実装詳細と対象範囲を整理し、説明を追加した。
- エージェントについて、個人指向の視点からペルソナ指向の視点を用いるように変更。
- 友達の友達 (FOAF) エージェントの結合要求を削除。
- エージェントオブジェクトは、（１つ以上の一意 ID プロパティではなく）ただ１つの一意 ID プロパティを持つように変更。

###### 0.95 から 1.0.0 (2013/4/26)
以下のような多数の改善と明確化を行った。

- 添付文書の概念を追加。
- アクティビティのメタデータを XML ではなく JSON に変更。
- ステートメントの無効化に関する変更。
- ドキュメント API の追加。
- ステートメント API の検索に関する変更。
- 署名付きステートメントの追加。

[0.95...1.0.0](https://github.com/adlnet/xAPI-Spec/compare/0.95-spec...1.0.0)

###### 1.0.0 から 1.0.1 (2013/10/01)
以下を含む明確化と例示の追加。

- 多くの typo の修正
- 参考資料を追加

[1.0.0...1.0.1](https://github.com/adlnet/xAPI-Spec/compare/1.0.0...1.0.1)

###### 1.0.1 から 1.0.2 (2014/10/01)
- 表に任意/必須を追加
- インタラクションのコンポーネントにて抜けていた表のヘッダを追加
- 添付資料の yes/no を必須/任意に変更
- 'moreInfo' 要素の意図を明確化

[1.0.1...1.0.2](https://github.com/adlnet/xAPI-Spec/compare/1.0.1...1.0.2)


<div style="page-break-after: always;"></div>
<a name="roleofxapi"/></a>
## 2.0 Experience API の役割
Experience API (xAPI) は経験に関するステートメントを、Learning Record Store (LRS) に配
送し、安全に記録するためのサービスである。これらの経験に関するステートメントは、典型
的には学習経験を示す物であるが、API はどのような経験に関するステートメントも扱うこと
ができる。xAPI は、アクティビティプロバイダがこれらの学習経験を生成、蓄積することを目
的としており、本仕様はその動作を実現するためのデータモデルと関連するコンポーネントを
提供する。

xAPI は以下を提供する。

* アクティビティプロバイダによって経験が伝達される手段としての、ステートメント、状態、学
習者、アクティビティ、オブジェクトの構造と定義

* 上記のオブジェクトの LRS に対する記録と取り出し（検証は含まない）のためのデータ転送
手段。情報を記録または取り出すシステムは、アクティビティプロバイダである必要はないこと
に注意。LRS は他の LRS やレポーティングシステムと通信をすることがある

* LRS とデータソースとの間での信頼のおける情報通信を可能にするセキュリティ手段

xAPI はオンライン学習とトレーニングに関する高機能なアーキテクチャを提供する一連の技
術提案の端緒となる。xAPI の適用例として、認証サービス、検索サービス、可視化サービス、
個人データサービスなどが考えられる。本仕様には、これらのサービスの実装詳細について
は示されていないが、xAPI は大きなアーキテクチャ思想を前提に設計されている。

<a name="adlrole"/></a>
### 2.1 xAPI における ADL の位置づけ

Advanced Distributed Learning (ADL) イニシアティブは xAPI の開発における、事務局や
ファシリテータとしての役割を担っている。xAPI は、学習をいつでもどこでも行えるような
ADL のトレーニングと学習のためのアーキテクチャの一部と位置付ける。ADL は、 xAPI
を同じようなユースケースをサポートできる 共有可能なコンテンツオブジェクト参照もモデル
(SCORM )の拡張とみているだけでなく、ADL や分散学習に係る人たちによって提案された 、
SCORM が実現できないユースケースもサポートするものと考える。

<a name="contributors"/></a>
### 2.2 貢献者
> _Experience API プロジェクトに貢献していただいた皆さんに感謝いたします。多くの皆さんが
毎週のミーティングに参加し、本仕様書を分散学習コミュニティ全体に対して有用なものとなる
ように仕上げる支援をしてくれました。また、多くの皆さんが、仕様書を作成、編集している人た
ちの助けになるように、コードサンプルや製品、文書などを提供してくれました。各自の組織にお
ける SCORM の利用や学習に関するベストプラクティスの有用で正直な情報を提供していただ
いた皆様にも感謝したいと思います。皆さんから提供いただいたユースケース、経験と知識に基
づいて、ADL とコミュニティはトレーニングと学習に関するアーキテクチャの第一歩 - Experience API を明確に定義することができました。皆さんこそが、最高のトレーニングと教育を提供するため
に私たちが頼りにできるコミュニティリーダーです。_

Kristy S. Murray, Ed.D.<br>
Director, ADL Initiative<br>
OSD, Training Readiness & Strategy (TRS)

<a name="wg"/></a>
### 2.2.1 ワーキンググループの参加者

<table>
    <tr><th>名前</th><th>組織</th></tr>
    <tr><td>Aaron Silvers</td><td>ADL</td></tr>
    <tr><td>Al Bejcek</td><td>NetDimensions</td></tr>
    <tr><td>Ali Shahrazad</td><td>SaLTBOX</td></tr>
    <tr><td>Andrew Downes</td><td>Rustici Software</td></tr>
    <tr><td>Andy Johnson</td><td>ADL</td></tr>
    <tr><td>Andy Whitaker</td><td>Rustici Software</td></tr>
    <tr><td>Anthony Altieri</td><td>American Red Cross</td></tr>
    <tr><td>Anto Valan</td><td>Omnivera Learning Solutions</td></tr>
    <tr><td>Avron Barr</td><td>Aldo Ventures, Inc.</td></tr>
    <tr><td>Ben Clark</td><td>Rustici Software</td></tr>
    <tr><td>Bill McDonald</td><td>Boeing</td></tr>
    <tr><td>Brian J. Miller</td><td>Rustici Software</td></tr>
    <tr><td>Chad Udell</td><td>Float Mobile Learning</td></tr>
    <tr><td>Chris Handorf</td><td>Pearson</td></tr>
    <tr><td>Chris Sawwa</td><td>Meridian Knowledge Solutions</td></tr>
    <tr><td>Dan Allen</td><td>Litmos</td></tr>
    <tr><td>Dan Kuemmel</td><td>Sentry Insurance</td></tr>
    <tr><td>Dave Mozealous</td><td>Articulate</td></tr>
    <tr><td>David Ells</td><td>Rustici Software</td></tr>
    <tr><td>David N. Johnson</td><td>Clear Learning Systems</td></tr>
    <tr><td>Doug Hagy</td><td>Twin Lakes Consulting Corporation</td></tr>
    <tr><td>Eric Johnson</td><td>Planning and Learning Technologies, Inc.</td></tr>
    <tr><td>Fiona Leteney</td><td>Feenix e-learning</td></tr>
    <tr><td>Greg Tatka</td><td>Menco Social Learning</td></tr>
    <tr><td>Ingo Dahn</td><td>University Koblenz-Landau</td></tr>
    <tr><td>Jason Haag</td><td>ADL</td></tr>
    <tr><td>Jeff Place</td><td>Questionmark</td></tr>
    <tr><td>Jennifer Cameron</td><td>Sencia Corporate Web Solutions</td></tr>
    <tr><td>Jeremy Brockman</td><td> </td></tr>
    <tr><td>Jhorlin De Armas</td><td>Riptide Software</td></tr>
    <tr><td>Joe Gorup</td><td>CourseAvenue</td></tr>
    <tr><td>John Kleeman</td><td>Questionmark</td></tr>
    <tr><td>Jonathan Archibald</td><td>Brightwave</td></tr>
    <tr><td>Jonathan Poltrack</td><td>ADL</td></tr>
    <tr><td>Kris Miller</td><td>edcetra Training</td></tr>
    <tr><td>Kris Rockwell</td><td>Hybrid Learning Systems</td></tr>
    <tr><td>Lang Holloman</td><td> </td></tr>
    <tr><td>Lou Wolford</td><td>ADL</td></tr>
    <tr><td>Luke Hickey</td><td>dominKnow</td></tr>
    <tr><td>Marcus Birtwhistle</td><td>ADL</td></tr>
    <tr><td>Mark Davis</td><td>Exambuilder</td></tr>
    <tr><td>Matteo Scaramuccia</td><td> </td></tr>
    <tr><td>Megan Bowe</td><td>Rustici Software</td></tr>
    <tr><td>Melanie VanHorn</td><td>ADL</td></tr>
    <tr><td>Michael Flores</td><td>Here Everything's Better</td></tr>
    <tr><td>Michael Roberts</td><td>vTrainingRoom</td></tr>
    <tr><td>Mike Palmer</td><td>OnPoint Digital</td></tr>
    <tr><td>Mike Rustici</td><td>Rustici Software</td></tr>
    <tr><td>Nick Washburn</td><td>Riptide Software</td></tr>
    <tr><td>Nikolaus Hruska</td><td>ADL</td></tr>
    <tr><td>Pankaj Agrawal</td><td>Next Software Solutions</td></tr>
    <tr><td>Patrick Kedziora</td><td>Kedzoh</td></tr>
    <tr><td>Paul Esch</td><td>Nine Set</td></tr>
    <tr><td>Paul Roberts</td><td>Questionmark</td></tr>
    <tr><td>Rich Chetwynd</td><td>Litmos</td></tr>
    <tr><td>Richard Fouchaux</td><td>Ontario Human Rights  Commission</td></tr>
    <tr><td>Richard Lenz</td><td>Organizational Strategies, Inc.</td></tr>
    <tr><td>Rick Raymer</td><td></td></tr>
    <tr><td>Rob Chadwick</td><td>ADL</td></tr>
    <tr><td>Robert Lowe</td><td>NetDimensions</td></tr>
    <tr><td>Russell Duhon</td><td>SaLTBOX</td></tr>
    <tr><td>Stephen Trevorrow</td><td>Problem Solutions, LLC.</td></tr>
    <tr><td>Steve Baumgartner</td><td></td></tr>
    <tr><td>Steve Flowers</td><td>XPConcept</td></tr>
    <tr><td>Thomas Ho</td><td></td></tr>
    <tr><td>Tim Martin</td><td>Rustici Software</td></tr>
    <tr><td>Tom Creighton</td><td>ADL</td></tr>
    <tr><td>Walt Grata</td><td>ADL</td></tr>
</table>

<a name="reqparticipants"/></a>
#### 2.2.2 要求仕様収集への貢献者
xAPI の要求の収集において、多くの人々や組織から、SCORM®、分散学習、および学習テク
ノロジ一般について、個別のフィードバックを得ることができた。全てを挙げることはできないが、
学習教育研修システムの相互運用性 (LESTI) グループによって 2008 年にまとめられたホワ
イトペーパー、Rustici Software 社の _UserVoice_ ウェブサイト、個別のインタビュー、および
さまざまなブログ記事は、xAPI の仕様をまとめるための重要な情報源となった。

<a name="readingguidelines"/></a>
### 2.3 技術に詳しくない人への読み方ガイドライン

本文書は、さまざまなシステムに対して、xAPI の実装方法を示す正式文書である。また、本
文書は、この技術を実装する個人と組織に向け、実装者が、独立で相互運用可能なツール、
システム、およびサービスを開発できることを目指した技術文書である。

さまざまなツール、システムおよびサービスが、ここに定義される仕様に基づいて設計される
ため、可能な限り、この文書中の文言や形式は、技術に詳しくない人にも_配慮_されている。
そのために、xAPI の各部分の_概要説明_には、**説明**または**背景**という見出しをつけ
ている。技術的な部分については、**必要条件**、**詳細**、または**例**という見出しをつ
けている。

大まかにいうと、文書が技術的に見えたり、要求仕様のようである場合は、そのように解釈さ
れるべきである。特に、長く、より詳細な説明や表など、直感的でなく多くの要求について長
い解説をしているところについて当てはまる。

<div style="page-break-after: always;"></div>
<a name="definitions"/></a>
## 3.0 用語の定義

* [アクティビティ](#def-activity)
* [アクティビティプロバイダ (AP)](#def-activity-provider)
* [アクタ (Actor)](#def-actor)
* [認証 (Authentication)](#def-authentication)
* [認可 (Authorization)](#def-authorization)
* [ベースエンドポイント(Base Endpoint)](#def-baseendpoint)
* [クライアント](#def-client)
* [実践コミュニティ](#def-community-of-practice)
* [Experience API (xAPI)](#def-experience-api)
* [イミュータブル](#def-immutable)
* [IRI (Internationalized Resource Identifier)](#def-iri)
* [IRL (Internationalized Resource Locator)](#def-iri)
* [逆関数識別子 (Inverse Functional Identifier)](#def-inverse-functional-identifier)
* [LMS](#def-learning-management-system)
* [LRS](#def-learning-record-store)
* [～しなければならない (MUST)/～すべきである (SHOULD)/～してもよい (MAY)](#def-must-should-may)
* [プロファイル](#def-profile)
* [登録事項 (Registration)](#def-registration)
* [REST (REpresentational State Transfer)](#def-rest)
* [サービス](#def-service)
* [ステートメント](#def-statement)
* [Tin Can API (TCAPI)](#def-tcapi)
* [動詞 (Verb)](#def-verb)

<a name="def-activity" /></a>
__アクティビティ__: アクティビティは「私はこれをやった」中の「これ」に相当
する、目的語の一形式である。それはアクタが相互作用を行った、何らか
の対象である。動詞との意味のある組合せによって記録される「教示や経
験、成果」の単位となりうる。アクティビティは幅広く解釈でき、またアクティ
ビティは椅子(実際のものも、ヴァーチャルなものも)のような具体物を指す
場合もある。
「アンナはケーキのレシピを試しました」というステートメントでは、「レシピ」
は xAPI のステートメントにおけるアクティビティとなる。他に「本」「eラーニ
ングコース」「ハイキング」「会議」もアクティビティの例になる。

<a name="def-activity-provider" /></a>
__アクティビティプロバイダ__: LRS と通信し、学習経験についての記録を
行うソフトウェアオブジェクト。学習アセットや通信可能なオブジェクトをま
とめた SCORM パッケージに似ているが、アクティビティプロバイダは伝
達しようとしている経験そのものから切り離されることがある。

<a name="def-actor" /></a>
__アクタ__: 個人やグループのアイデンティティや外的側面。それはステー
トメントを用い、アクティビティの中で動作しながら記録される。

<a name="def-authentication" /></a>
__認証 (Authentication)__: ユーザやシステムのアイデンティティを確認す
ること。認証によって、2つの「信頼された」対象どうしの間のやり取りが可
能になる。

<a name="def-authorization" /></a>
__認可 (Authorization)__: ユーザやシステムの役割に応じ、何らかの利用
許可を与えること。それはあるユーザやシステムを他者から信頼されるよ
うにする過程である。

<a name="def-baseendpoint" /></a>
__ベースエンドポイント (Base Endpoint)__: 全ての xAPI エンドポイントに共通
する最長のパスで、最後の / を含む。例：ステートメントエンドポイントとして
http://example.com/xAPI/statements のベースエンドポイントは
http://example.com/xAPI/ となる。

<a name="def-client" /></a>
__クライアント__: - LRS とやり取りしうる全ての物。クライアントはアクティ
ビティプロバイダや報告ツール、 LMS や他の LRS にもなりうる。

<a name="def-community-of-practice" /></a>
__実践コミュニティ__: 共通の動機や役割、目的によって結ばれることの多
いグループである。またその集団は共通の様式のもとで行動する。

<a name="def-experience-api" /></a>
__Experience API (xAPI)__: この文書の中で規定される API であり、Tin
Can プロジェクトの成果物である。許可を受けたアクタが「拡張可能な学習
記録や学習者プロファイル、学習経験プロファイル」を保存し、また取り出
すための簡素で軽量な方法である。またそれはプラットフォームに依存しな
い。

<a name ="def-immutable" /></a>
__イミュータブル__:  変わることのない事象を記述するための形容詞。若干
の例外を除き、xAPI のステートメントはイミュータブル(不変)である。イミュ
ータブルは、ステートメントがLRS 間で共有されるときに、複製されたステ
ートメントの間の同一性を保つことを保証する。

<a name="def-iri" /></a>
__IRI (Internationalized Resource Identifiers)__: IRL でありうる一意な識別
子。xAPI では、全ての IRI はスキームを含む完全な絶対 IRI となるべきで
ある。相対 IRI は使われるべきではない。 IRL は IRL を作る者がコントロー
ルするドメインの中で、定義されるべきである。

__IRI (Internationalized Resource Identifiers)__: 一意な識別子で、
IRL であることもある。動詞、アクティビティ、またはアクティビティタイプな
どの目的語を特定するために使われる。URI とは異なり、IRI は各国の言語をサ
ポートするために、ASCII キャラクタ以外を利用することが出来る。

IRI は常にスキーマを含む。これは、本標準による要求ではないが、[RFC 3987]
(http://www.ietf.org/rfc/rfc3987.txt)に示される IRI の定義による。いわ
ゆる '相対 IRI' は、IRI ではない。

<a name="def-irl" /></a>
__Internationalized Resource Locator (IRL)__: この仕様書において、URL
を URI と読み替え可能な時、 IRL は IRI と読み替えられる。(URI と読み替
えるルールと、 IRI と読み替えるルールは同一)IRL を用いている実践コミュ
ニティが単に URL を用いることもある。それがxAPI の範疇で技術的に適切
でなかったとしても。

<a name="def-inverse-functional-identifier" /></a>
__逆関数識別子 (Inverse Functional Identifier)__: 特定の人物やグループに
対する一意な識別子。行為者やグループを特定するために用いられる。

<a name="def-learning-management-system" /></a>
__Learning Management System (LMS)__: Learning Systems Architecture Lab (訳注: カー
ネギーメロン大) の定義によれば、LMS は1人以上の学習者に1つ以上の学習コースを提
供するためのソフトウェア・パッケージである。 LMS は一般に学習者を認証し、コースに登
録し、コースを修了させ、評価するための Web ベースのシステムである。本仕様書におい
ては、標準規格を実装する既存のシステムという文脈のもとで、 LMS という用語を用いる。

<a name="def-learning-record-store" /></a>
__Learning Record Store (LRS)__: 学習に関する情報を蓄えるためのシステム。 xAPI が登
場する前は、ほとんどの LRS は LMS だった。だが本仕様書で LRS という用語を用いる場
合、「 xAPI の実装のためにフル仕様の LMS が必要とは限らない」ということを、強調してお
きたい。 xAPI はその機能を果たすために、(訳注: LMS でなく) LRS のほうを必要とする。

<a name="def-must-should-may" /></a>
__～しなければならない (MUST)/～すべきである (SHOULD)/～してもよい (MAY)__: xAPI
仕様への適合性に関する、3つのレベルでの約束ごと。MUST 条件(または MUST NOT 条件)
を満たさないシステムは、 xAPI に適合しない。 SHOULD 条件を満たさないシステムは適
合性に反してはいないが、ベストプラクティスには相応しくない。 MAY 条件は適合性を気
にせずに開発者が選択できるオプションである。

<a name="def-profile" /></a>
__プロファイル__: 一般的に「教育システムの要素として意味を持つ、名前と文書の組」に
よって学習者やアクティビティの情報を保持する構成体である。

<a name="def-registration" /></a>
__登録事項 (Registration)__: 特定のアクティビティを経験する学習者のインスタンスである。

<a name="def-rest" /></a>
__REST (REpresentational State Transfer)__: ネットワーク化された web サービスを接続
するためのアーキテクチャである。 REST は HTTP のメソッドを信頼し、現在の web のベ
ストプラクティスを役立てる。

<a name="def-service" /></a>
__サービス__: 分散学習環境の一つ以上の局面に責任を持つ、ソフトウェアの構成要素で
ある。一般的に LMS は、学習経験全体をデザインするために複数のサービスを結合させる。

<a name="def-statement" /></a>
__ステートメント__:学習経験の一局面を記録する「文脈」において、「アクタ(学習者)、
動詞、オブジェクト」の3つ組からなり「結果」を有する、単純な構成体である。いくつか
のステートメントの組は、学習経験に関する完全な詳細情報を記録するために使われうる。

<a name="def-tcapi"/></a>
__Tin Can API (TCAPI)__: 本仕様書で定義される API の、以前の名称である。 xAPI
へのインフォーマルな呼称として用いられる。

<a name="def-verb" /></a>
__動詞 (Verb)__: ステートメント中のアクティビティにおける、アクタの行為を定義するものである。

<div style="page-break-after: always;"></div>
<a name="statement"/></a>
## 4.0 ステートメント

###### 説明
ステートメントは xAPI の中心概念である。全ての学習イベントはステートメントとして記
録される。ステートメントは、"I did this" といった文と似た構造を持つ。

<a name="stmtprops"/></a>

### 4.1 ステートメントプロパティ

##### 詳細
下記テーブルに各ステートメントプロパティの詳細を示す。

<table>
    <tr><th>プロパティ</th><th>タイプ</th><th>説明</th><th>必須</th></tr>
    <tr><td>id</td><td>UUID</td>
    <td>アクティビティプロバイダが設定しない場合に、LRS によって割り当てられた UUID。</td><td>推奨</td></tr>
    <tr><td><a href="#actor">actor</a></td><td>Object</td>
    <td>ステートメントが誰に関するものか（<a href="#agent">Agent</a> や <a href="#group">Group</a> として）。"I Did This" の中の "I" に対応。</td><td>必須</td></tr>
    <tr><td><a href="#verb">verb</a></td><td>Object</td>
    <td>学習者やチームオブジェクトの行う行為。"I Did This" の "Did" に相当。</td><td>必須</td></tr>
    <tr><td><a href="#object">object</a></td><td>Object</td>
    <td>ステートメントの目的語となる アクティビティ、エージェント、または別のステートメント。"I Did This" の "This" に相当。この項目の値として提供される目的語には "objectType" フィールドを含むべきであることに注意。指定しない場合は目的語はアクティビティであるとみなされる。</td><td>必須</td></tr>
    <tr><td><a href="#result">result</a></td><td>Object</td>
    <td>動詞に関する測定結果を示す結果オブジェクト。</td><td>任意</td></tr>
    <tr><td><a href="#context">context</a></td><td>Object</td>
    <td>ステートメントに意味を補う文脈情報。例：アクタが所属するチームの情報。フライトシミュレータにおいて、あるシナリオが実行されたときの高度の情報。</td><td>任意</td></tr>
    <tr><td><a href="#timestamp">timestamp</a></td><td>Date/Time</td>
    <td>このステートメントで示されたイベントの発生時刻を示すタイムスタンプ（<a href="https://en.wikipedia.org/wiki/ISO_8601#Combined_date_and_time_representations">ISO 8601</a> 形式に従う）。指定されない場合、LRS は "stored" のタイムスタンプをここに設定すべきである。
    </td><td>任意</td></tr>
    <tr><td><a href="#stored">stored</a></td><td>Date/Time</td>
    <td>このステートメントが記録された時刻を示すタイムスタンプ（<a href="https://en.wikipedia.org/wiki/ISO_8601#Combined_date_and_time_representations">ISO 8601</a> 形式に従う）。LRS によって設定される。
    </td><td>LRS による設定</td></tr>
    <tr><td><a href="#authority">authority</a></td><td>Object</td>
    <td>このステートメントが正しいものであると主張する Agent または Group を示す。LRS の認証機構により確認され、指定がない場合は LRS によって設定される。</td>
    <td>任意</td></tr>
    <tr><td><a href="#version">version</a></td><td>Version</td>
    <td><a href="http://semver.org/spec/v1.0.0.html">セマンティックバージョニング 1.0.0</a> 形式で示したステートメントの xAPI バージョン。
    </td><td>非推奨</td></tr>
    <tr>
        <td><a href="#attachments">attachments</a></td>
        <td>Array of attachment Objects</td>
        <td>ステートメントに対する添付文書のヘッダー。</td><td>任意</td>
    </tr>
</table>

LRS によりプロパティ（"id", "authority", "stored", "timestamp", "version")
が割り当てられる場合を除き、ステートメントは不変である。ただし、ステー
トメント中で参照されているアクティビティの内容は、ステートメントそのもの
の一部とはみなさないことに注意が必要である。よって、ステートメントは不
変だが、ステートメントによって参照される アクティビティは不変ではない。
これは、参照されるアクティビティが変更された時、ステートメントのディー
プコピーによって生成される JSON も変更されることを意味する（ステート
メント API の "format" パラメータ参照）。

##### 必要条件
* ステートメントではプロパティを複数回設定してはならない
* ステートメントは "actor", "verb", "object" を利用しなければならない
* ステートメント内のプロパティの順序は問わない

必須または推奨とされる全てのプロパティを用いる最も簡素なステート
メントの例。

```
{
    "id": "12345678-1234-5678-1234-567812345678",
    "actor":{
        "mbox":"mailto:xapi@adlnet.gov"
    },
    "verb":{
        "id":"http://adlnet.gov/expapi/verbs/created",
        "display":{
            "en-US":"created"
        }
    },
    "object":{
        "id":"http://example.adlnet.gov/xapi/example/activity"
    }
}
```
[Appendix A: ステートメント例](#AppendixA) 参照


<a name="stmtid"/></a>
#### 4.1.1 id (識別子)

###### 説明
UUID（仕様は [RFC 4122](http://www.ieft.org/rfc/rfc4122.txt) 参照。UUID は標準的な文字列形式でなければならない）

###### 必要条件

* 受信ステートメントに ID が指定されていなかった場合、LRS が ID を生成しなければならない。
* ID はアクティブティプロバイダによって生成されるべきである。

<a name="actor"/></a>
#### 4.1.2 Actor (アクタ)

###### 説明
必須の Agent または Group オブジェクト。

<a name="agent"/></a>
##### 4.1.2.1 アクタのオブジェクト型が Agent の時
###### 説明
Agent（個人）は、人またはシステムである。

###### 詳細

* Agent は、逆関数識別子（<a href="#inversefunctional"> 4.1.2.3 逆関数識別子</a> 参照）の４つのタイプの１つによって定義されなければならない。
* Agent に、１つを超える逆関数識別子を設定してはならない。
* Agent は Group 識別子としても使われている逆関数識別子を使うべきではない。

Agent オブジェクトのプロパティを以下の表に示す。

<table border ="1">
    <tr><th>プロパティ</th><th>タイプ</th><th>説明</th><th>必須</th></tr>
    <tr><td>objectType</td><td>string</td><td>"Agent"。Agent が目的語の場合は必須である。
    </td><td>任意</td></tr>
    <tr><td>name</td><td>String</td><td>Agent のフルネーム。</td><td>任意</td></tr>
    <tr><td colspan="2"><a href="#inversefunctional"> 4.1.2.3 逆関数識別子</a>参照</td>
        <td>Agent に固有の逆関数識別子。</td><td>必須</td></tr>
</table>

<a name="group"/></a>
##### 4.1.2.2 アクタのオブジェクト型が Group の時
###### 説明

Group は Agent の集合を意味し、Agent を指定できる状況の大部分において、使用する
ことができる。Group は、匿名と指名の２種類がある。

###### 詳細

匿名グループは、一時的なチームなど、定められた名称が存在しない
人々の集まりを示すために用いられる。

匿名グループのすべてのプロパティを、下の表に示す。

<table border ="1">
    <tr><th>プロパティ</th><th>タイプ</th><th>説明</th><th>必須</th></tr>
    <tr><td>objectType</td><td>String</td><td>"Group". </td><td>必須</td></tr>
    <tr><td>name</td><td>String</td><td>グループの名称。</td><td>任意</td></tr>
    <tr><td>member</td><td>Array of <a href="#agent">Agent Objects</a></td><td>このグループのメンバー。</td><td>必須</td></tr>
</table>

指名グループは Agent の集合を一意に特定するために用いられる。

指名グループのすべてのプロパティを、下の表に示す。

<table border ="1">
    <tr><th>プロパティ</th><th>タイプ</th><th>説明</th><th>必須</th></tr>
    <tr><td>objectType</td><td>String</td><td>"Group". </td><td>必須</td></tr>
    <tr><td>name</td><td>String</td><td>グループの名称。</td><td>任意</td></tr>
    <tr><td>member</td><td>Array of <a href="#agent">Agent Objects</a></td><td>このグループのメンバー。</td><td>任意</td></tr>
    <tr><td colspan="2"><a href="#inversefunctional"> 4.1.2.3 逆関数識別子</a>参照</td>
        <td>グループを一意に示す逆関数識別子。
</td><td>必須</td></tr>
</table>

###### 必要条件

* ステートメントを利用するシステムは、複数の匿名グループが同じメンバーで構成されている場合においても、それらを異なるものとして扱わなければならない。
* アクティビティプロバイダは、グループに関する、複数のステートメントの発行、データの集約、または文書の登録や取出をする場合は、指名グループを使うべきである。
* アクティビティプロバイダは、匿名や指名グループの'member'要素に、全てあるいは一部分のエージェントのリストを入れても良い。

###### 匿名グループに関する必要条件

* 匿名グループは、構成要員である Agent をリスト化した 'member' プロパティを持たなければならない。
* 匿名グループは、'member' プロパティにグループオブジェクトを含んではならない。
* 匿名グループは、いかなる逆関数識別子も含んではならない。

###### 指名グループに関する必要条件

* 指名グループは、厳密に１つの逆関数識別子を含まなければならない。
* 指名グループは、'member' プロパティにグループオブジェクトを含んではならない。
* 指名グループは、Agent の識別子としても使われる逆関数識別子を使うべきではない。
* 指名グループは、構成要員である Agent をリスト化する 'member' プロパティを含んでもよい。

<a name="inversefunctional"></a>
##### 4.1.2.3 逆関数識別子
###### 説明
逆関数識別子は、その Agent や指名グループを参照することが、将来にわたり保証され
ている Agent や指名グループに関する値を示す。

###### 背景
もし特定可能な個人やグループなどに関連付けられないのであれば、学習経験記録は意
味のないものになってしまう。xAPI ステートメントでは、これを、広く受け入れられている
FOAF 原則（<a href="http://xmlns.com/foaf/spec/#term_Agent"> Friend Of A Friend</a> 参照）
を参考にした逆関数識別子の組み合わせによって実現する。

###### 詳細

逆関数識別子の取りうる全てのプロパティを以下の表に示す。

<table border ="1">
    <tr><th>プロパティ</th><th>タイプ</th><th>説明</th></tr>
    <tr><td><a href="http://xmlns.com/foaf/spec/#term_mbox">mbox</a></td><td>mailto IRI</td><td>
    要求されるフォーマットは "mailto:email address" である。<br>
    この Agent に対して過去、未来を通じて割り当てられたメールアドレスのみを、このプロパティと mbox_sha1sum に利用すべきである。</td></tr>
    <tr><td><a href="http://xmlns.com/foaf/spec/#term_mbox_sha1sum">mbox_sha1sum</a></td><td>String</td><td>mailto IRI（例：mbox プロパティの値）の SHA1 ハッシュ値。LRS は、リクエストが mbox に関係する場合は、対応するハッシュ値をもつ Agent を含んでもよい。</td></tr>
    <tr><td>openid</td><td>URI</td><td>Agent を一意に特定する OpenID。</td></tr>
    <tr><td>account</td><td><a href="#agentaccount">Object</a></td><td>LMS やイントラネットなどの既存のシステムにおけるユーザーアカウント。</td></tr>
</table>

<a name="agentaccount"/></a>
###### 4.1.2.4 Account オブジェクト

###### 説明

非公開のシステム（LMS またはイントラネット）や公開されたシステム（ソーシャルネット
ワーキングサイト）などの既存システムのユーザーアカウント。

###### 詳細

* アカウントオブジェクトを提供するシステムが OpenID を利用しているのであれば、アクティビティプロバイダはアカウントオブジェクトではなく、OpenID プロパティを利用すべきである。
*  アクティビティプロバイダが Agent や Group について、個人を特定可能な情報を公開するのを懸念する場合は、匿名性を保ちつつその人についてのすべてのステートメントを識別可能にするために、意味を持たないアカウント名（例：アカウント番号）を利用すべきである。

Account オブジェクトのすべてのプロパティを以下の表に示す。

<table border ="1">
    <tr><th>プロパティ</th><th>タイプ</th><th>説明</th><th>必須</th></tr>
    <tr><td>homePage</td><td>IRL</td><td>アカウントが利用されているシステムの正式のホームページ。これは、FOAF の accountServiceHomePage に基づく。</td><th>必須</th></tr>
    <tr><td>name</td><td>String</td><td>このアカウントにログインするためのユニーク ID またはアカウント名。これは FOAF の accountName に基づく。</td><th>必須</th></tr>
</table>

###### 例

意味を持たないアカウント名によって Agent を識別する例を示す。


```
{
    "objectType": "Agent",
    "account": {
        "homePage": "http://www.example.com",
        "name": "1625378"
    }
}
```

<a name="verb"/></a>
#### 4.1.3 Verb (動詞)

###### 説明
動詞はアクタとアクティビティとの間の行動を定義する。

###### 背景

xAPI ステートメント中の動詞は、学習経験中に行われた行動を説明する。xAPI が動詞
を特別に定義することはない。(例外として予約動詞 ‘http://adlnet.gov/expapi/verbs/voided’
がある)。その代わりに、xAPI では実践コミュニティが、メンバー間での意思疎通のため
に動詞を作成し、さらには一般でも利用可能にするように動詞を作成する方法を定義して
いる。あらかじめ定義された動詞をリスト化するという考えには制約があり、将来に亘って
可能性のある学習経験全てを効率的に扱うこともできないと考えられる。

###### 詳細

動詞はステートメント中にオブジェクトとして現れ、それは IRI と、動詞に関して人間が理
解できる意味を複数の言語や方言に対応させた表示名とからなる。
以下の表に動詞オブジェクトの全てのプロパティを示す。

<table>
    <tr><th>プロパティ</th><th>タイプ</th><th>説明</th><th>必須</th></tr>
    <tr>
        <td>id</td>
        <td>IRI</td>
        <td>動詞の定義を示す。それぞれの動詞の定義は、単語ではなく動詞の意
                          味に対応する。IRI は人間が理解できる形で、動詞の意味を含んでいる
                          べきである。</td>
        <td>必須</td>
    </tr>

    <tr>
        <td>display</td>
        <td><a href="#misclangmap">言語マップ</a></td>
        <td>一つ以上の言語で示された、人間が理解できる形での動詞の表現。ステー
                      トメントが表す意味について全く影響力を持たないが、選択された動詞に
                     よって既に決定されている意味を人間が理解できる形で表現する機能を提
                     供する。</td>
        <td>推奨</td>
    </tr>

</table>

###### 必要条件
* displayプロパティは、動詞IRIにより既に決められた意味を例示するために用いられなければならない。
* ステートメントを解釈するシステムは、意味の特定のために 動詞IRI を利用しなければならない。
* display プロパティは、動詞の意味を変えるために利用されてはならない。
* ステートメントを解釈するシステムは、ステートメントの意味の理解のために display プロパティを利用してはならない。
* ステートメントを解釈するシステムは、display プロパティを、人間に対して提示する以外のいかなる用途にも用いてはならない。display プロパティを用いてステートメントを集約したりカテゴリ分けしたりすることは、この必要条件に対する違反の例となる。
* display プロパティは全てのステートメントに用意されるべきである。
* ID に含まれる IRI は人間が理解できる形で、動詞の意味を示すべきである。

###### 例
以下に、推奨項目を含む動詞の例を示す。

```
{
    "id":"http://www.adlnet.gov/XAPIprofile/ran(travelled_a_distance)",
        "display":{
            "en-US":"ran",
            "es" : "corrió"
        }
}
```

上の例での動詞は例示目的でのみ示されている。これは、この意味を持った動詞がこ
の ID で定義されていることを意味するものではない。この原則は、予約動詞
 (‘http://adlnet.gov/expapi/verbs/voided’) を除く、本仕様書のすべての動詞の例に
ついて適用される。

##### 4.1.3.1 動詞の言語と意味に関する用法

###### 詳細
_意味_

Verb ID によって表される IRI は、その単語そのものではなく、単語に関する特定の意味を示す。

例えば、英単語の “fired” は、”銃を撃つ(fired)” や “窯で焼く(fired)”、”従業員を解雇する(fired)”
など、文脈に応じて異なる意味を持ち得る。この例においては、IRI は “fired” が単語として
持ちうる意味ではなく、それらのうちの特定の１つの意味を示さなければならない。

display プロパティでは時制に関してある程度の自由度を残している。動詞 IRI は過去形で
あることが期待されるが、対象のアクティビティについて（同じ動詞で）異なる時制にしたほう
が妥当な場合は、そのようにしてもよい。

_言語_

xAPI における動詞は IRI であり、いかなる言語にも依存しない固有の意味を示す。

例えば、http://example.org/firearms#fire のような特定の動詞 IRI は銃を撃つといった行
動を意味し、http://example.com/فعلﻝ/خوﻭاﺍندﺩنﻥ のような動詞 IRI は本を読むといった行動
を意味する。

##### 4.1.3.2 実践コミュニティに関する用法

###### 説明

実践コミュニティでは、その構成員の要求にこたえるために、どこかの段階で新たな動詞を
定義する必要が出てくる。

そのため、xAPI 実践コミュニティは動詞の語彙の中心となるプロファイル、リスト、リポジト
リ等を作成することが望まれる。ADL は、コミュニティに貢献するために xAPI における動詞
についての解説文書を制作している。下記の要求を満たすために、推奨される動詞の IRI 集が
存在する。異なるアクティビティプロバイダ間で、同じ意味に対して、異なる動詞を利用したく
なることも想定される。

###### 実践コミュニティ向けの必要条件

* 新しい動詞を定義する場合は IRI を所有しているか、xAPI の 動詞を示すために IRI を利用する許可をその所有者から得なければならない。
* 新しい動詞を定義する場合は、動詞の想定される用途についての人間が理解できる定義を、IRI にてアクセス可能にしておくべきである。

###### アクティビティプロバイダ向けの必要条件

* アクティビティプロバイダは、可能な限り既存の対応する動詞を利用すべきである。
* アクティビティプロバイダは、適切な動詞が存在しない場合、動詞を作成し利用してもよい。

<a name="object"/></a>
####4.1.4 Object(目的語)

###### 説明

ステートメントにおける目的語は、アクティビティ、エージェント／グループ、サブステートメント、もしくはステートメントの参照などがあり得る。
目的語は、ステートメントにおいて“対象”として表現される部分に当たる。
例えば、“私はこれをした。 ( I did this )”のステートメントでは「これ( this )」にあたる。

例：

* 目的語がアクティビティの場合：“ジェフはハイキングに関するエッセイを書いた”
* 目的語がエージェントの場合：“ネリーはジェフの面談を行った”
* 目的語がサブステートメントもしくはステートメントの参照の場合（異なる手段ではあるが人が理解できる）：“ジェフはハイキングに関するエッセイを書いた”についてネリーはコメントした。

###### 詳細

このフィールドの値として提供されるオブジェクトは "objectType" フィールドを持つべきで
ある。指定が無ければ、 "objectType" は "Activity" と認識される。その他の有効な値は、
 <a href="#agentasobj">Agent</a>, <a href="#agentasobj">Group</a>,
<a href="#substmt">Sub-Statement</a> もしくは [StatementRef](#stmtref) となる
オブジェクト のプロパティは、 objectType に応じて変わる。

<a name="activity"/></a>

##### 4.1.4.1 ObjectType がアクティビティの場合

####### 詳細

ステートメントは、ステートメントの 目的語としてアクティビティを示すことができる。本
ケースにおけるオブジェクトのプロパティは以下の表の通り。

<table>
    <tr><th>プロパティ</th><th>タイプ</th></th><th>説明</th><th>必須</th></tr>
    <tr>
        <td>objectType</td>
        <td>String</td>
        <td>利用する場合は “Activity”を設定しなければならない。</td>
        <td>全ての場合で任意</td>
    </tr>
    <tr>
        <td><a href="#acturi">id</a></td><td>IRI</td>
        <td>一意のアクティビティの識別子。</td>
        <td>必須</td>
    </tr>
    <tr>
        <td><a href="#actdef">definition</a></td>
        <td>Object</td>
        <td>メタデータ, <a href="actdef">以下のアクティビティ定義を参照</a>。</td>
        <td>任意</td>
    </tr>
</table>

もし異なる2つのアクティビティにおいて同じIDが使用できるとすると、これ
らのアクティビティに対する妥当性は疑問しされることになる。そのため意
図的だとしてもLRSは決して同じを2つの異なるアクティビティに紐付けて取
り扱うことがないことを意味する。つまり別のシステムでコンフリクトが生じ
た場合、意図的に定義づけることは不可能である。

###### <a name="actdef" />アクティビティ定義</a>
アクティビティを定義するオブジェクトは以下の表の通り。

<table>
    <tr><th>プロパティ</th><th>タイプ</th><th>説明</th><th>必須</th></tr>
    <tr>
        <td>name</td>
        <td><a href="#misclangmap">言語マップ</a></td>
        <td>可読／可視化したアクティビティの名称</td>
        <td>推奨</td>
    </tr>
    <tr>
        <td>description</td>
        <td><a href="misclangmap">言語マップ</a></td>
        <td>アクティビティの説明</td>
        <td>推奨</td>
    </tr>
    <tr>
        <a name="acttype" /></a>
        <td>type</td>
        <td>IRI</td>
        <td>アクティビティのタイプ</td>
        <td>推奨</td>
    </tr>
    <tr>
        <td>moreInfo</td>
        <td>IRL</td>
        <td>
        アクティビティについての人間が読むための情報をもつ文書を示す。文書には、アクティビティの実行の仕方を含めても良い。</td>
        <td>任意</td>
    </tr>
    <tr>
        <td colspan="4">Interaction propertiesについては、 Interaction Activities を参照</td>
    </tr>
    <tr>
        <td>extensions</td>
        <td>Object</td>
        <td>必要に応じて格納する他のプロパティに関するマップ（<a href="#miscext">Extensions</a> 参照）</td>
        <td>任意</td>
    </tr>
</table>

__注記:__ IRI フラグメント (相対 IRL とも言う) は有効な IRI ではない。また、動詞と同じく、
アクティビティプロバイダは、確立され広く適用されているアクティビティタイプを探して利用
することが推奨される。

###### <a name="acturi" />アクティビティ ID の必要条件</a>

* アクティビティ ID は一意でなければならない。
* アクティビティ ID は常に同じアクティビティを参照しなければならない。
* アクティビティ ID は作成者がこの目的のために許可されたドメインを使用すべきである。
* アクティビティ ID はそのドメイン内の全てのアクティビティ IDが一意になるようなスキームで作成されるべきである。
* アクティビティ ID はメタデータやアクティビティのIRLを示してもよい。

###### LRS の必要条件

* あるアクティビティ ID が複数の著者または組織によって利用されていると見なされる場合、LRS はアクションを実行してはならない。
* LRS は同じ ID への複数の参照を、異なるアクティビティへの複数の参照として取り扱ってはならない。
* 格納されたものとは異なるアクティビティ定義でステートメントを受信した場合、 LRS はアクティビティプロバイダが定義を変更する権限を持っているかを判断すべきで、もし持っていると判断した場合は、記録されたアクティビティの定義を更新するべきである。
* LRS は、アクティビティの定義に関する小修正を受け入れてもよい。例えば、スペルの訂正である。但し、正解を変更してはならない。

###### アクティビティプロバイダの必要条件

* アクティビティプロバイダは、アクティビティ ID が複数のアクティビティで重複利用されないことを保証しなければならない。
* アクティビティプロバイダは、以前に同じ ID に対して記録された状態またはステートメントと一致し、互換性のあるアクティビティ ID に対してのみ、その状態またはステートメントを生成しなければならない。
* アクティビティプロバイダは、アクティビティのバージョン更新時（リビジョンや他のプラットフォームによる）に互換性を崩させてはならない。

###### メタデータの必要条件

* もしアクティビティの IRI が IRL だった場合、 "Accept: application/json, */*" を HTTP
ヘッダーに入れて、その IRL の GET を試みるべきである。これは LRS がアクティビティ ID
を検知したら直ぐに実施しなければならない。

* アクティビティ ID として使用した IRL から有効なアクティビティ定義の JSON をロードした
際、LRS はロードした定義にない名前や定義を残しながら、ロードした定義をアクティビティ
の内部的な定義に組み込むべきである。

* IRL 識別子を持つアクティビティは、ステートメントで利用される
<a href="#actdef">Activity Definition</a> JSON フォーマットを用いて Content-Type を
 "application/json" に設定したメタデータを提供してもよい。

* アクティビティ定義の内部表現を決定する際に LRS はアクティビティ ID として使われる
IRL からアクティビティ定義を解析することができ、そこから任意のドキュメントを読み込む
ときに、 LRS はこの定義を考慮することができる。

<a name="interactionacts"/></a>
##### インタラクション　アクティビティ

###### 背景

従来の eラーニングはインタラクションとアセスメントが組み込まれた構造をもっている。
それらの実情と構造を xAPI にも拡張するために、本仕様では SCORM 2004 第4版の
データモデルを参考にしたインタラクションの定義を含んでいる。これらの定義はインタ
ラクションのデータを記録するためのシンプルで使い慣れた仕組みを提供することを目
的としている。これらの定義はシンプルで使いやすいが、制約もある。より高機能なイン
タラクションの定義が必要な実践コミュニティは、アクティビティのタイプと定義の拡張を
利用することによりそれを実現できる。

###### 詳細

以下の表はインタラクションアクティビティのプロパティを表す。

<table>
    <tr><th>プロパティ</th><th>タイプ</th><th>説明</th><td>必須</td></tr>
    <tr>
        <td>interactionType</td>
        <td>String</td>
        <td>SCORM2004 4th 版のRun-Time Environmentで定義している"cmi.interactions.n.type"</td>
        <td>任意</td>
    </tr>
    <tr>
        <td>correctResponsesPattern</td>
        <td>An array of strings</td>
        <td>SCORM2004 4th 版の Run-Time Environment で定義している" cmi.interactions.n.correct_responses.n.pattern "に対応し、最後の n は配列のインデックスとなる</td>
        <td>任意</td>
    </tr>
    <tr>
        <td>choices | scale | source | target | steps</td>
        <td>Array of interaction components</td>
        <td>interactionType (後述参照)にて特定</td>
        <td>任意</td>
    </tr>
</table>

###### デリミタに関する注意
SCORM 2004 第4版ランタイム環境は、文字列に関するなんらかの情報を伝える特定のデリミタを
追加することを許可している。これは、該当文書のセクション 4.1.1.6 予約されたデリミタに概要
が示され、RTE データモデル全体から参照されている。 これらのデリミタは SCORM 2004 第4版
ランタイム環境のセクション 4.2.9.1 Correct Responses Pattern データモデル要素詳細に定義さ
れているいくつかのインタラクションにおいて Correct Responses パターンの中で利用することが
できる。

セクション 4.1.1.6 と表 4.2.9.1 のデリミタの順序について一部矛盾がある。xAPI においては、4.2.9.1
で示されるデリミタの順序を正しいものとする。

###### 必要条件

* インタラクションアクティビティには、有効な interactionType が含まれていなければならない
* インタラクションアクティビティは、アクティビティタイプとして、http://adlnet.gov/expapi/activities/cmi.interaction を持つべきである。
* 有効な interactionType を受信した場合、 LRS は残りのプロパティを下記の表に沿っ
て確認し、もし残りのプロパティがインタラクションアクティビティに対して有効でない場合
は、HTTP 400 "Bad Request" を返してもよい。

##### インタラクションのコンポーネント

###### 詳細

インタラクションコンポーネントの定義は以下の通り

<table>
    <tr><th>プロパティ</th><th>タイプ</th><th>説明</th><th>必須</th></tr>
    <tr>
        <td>id</td>
        <td>String</td>
        <td>SCORM2004 4th 版の Run-Time Environment で定義している " cmi.interactions.n.id" で実際に使用する値</td>
        <td>必須</td>
    <tr>
        <td>description</td>
        <td><a href="#misclangmap">言語マップ</a></td>
        <td>インタラクションコンポーネントの表現（例えば、複数選択インタラクションで選択されたテキスト）</td>
        <td>任意</td>
    </tr>
</table>

<a name="interactionType"/></a>
インタラクションアクティビティにおける interactionType でサポートしている CMI インタ
ラクションコンポーネントは以下の表の通り。

<table>
    <tr><th>インタラクションタイプ</th><th>サポートしているコンポーネントのリスト</th><tr>
    <tr><td>choice, sequencing</td><td>choices</td></tr>
    <tr><td>likert</td><td>scale</td></tr>
    <tr><td>matching</td><td>source, target</td></tr>
    <tr><td>performance</td><td>steps</td></tr>
    <tr><td>true-false, fill-in, long-fill-in, numeric, other</td><td>[No component lists defined]</td></tr>
</table>

###### 必要条件

* インタラクションコンポーネントの配列中で、全ての ID は異なる値でなければならない。
* インタラクションコンポーネントの ID には空白があってはならない

###### 例

各cmi.interactionタイプのアクティビティ定義は　[Appendix C](#AppendixC)　のサンプルを参照。

<a name="agentasobj"/></a>
##### 4.1.4.2 目的語が単体のエージェントもしくはグループだった場合

###### 必要条件

* 単体のエージェントもしくはグループを参照しているステートメントは必ず 'objectType' プロパティを明示しなくてはならない

エージェントの詳細については Section 4.1.2 Actor (アクタ） を参照

<a name="stmtasobj"/></a>
##### 4.1.4.3 目的語がステートメントだった場合

###### 背景

目的語としてステートメントを取るのには、２つの場合がある。第一に、目的語は、既に存在
するステートメントの参照を用いることにより、ステートメントの形をとることができる。ステー
トメント参照の一般的な例としては、独立のイベントとして扱うことができる経験に対する評
価やコメントの付与があげられる。第二に、サブステートメントを利用することにより、目的
語は独立したステートメントの形をとることができる。サブステートメントの一般的な利用法
は、単独のステートメントでは誤解されるような経験についてである。それぞれのタイプの
定義は以下の通り。

<a name="stmtref"/></a>
##### ステートメント参照

###### 説明
ステートメント参照は、他の既存ステートメントへのポインタである。

###### 必要条件

* ステートメント参照は、objectType プロパティとして "StatementRef" を指定しなければならない。
* ステートメント参照は、ステートメントの UUID を "id" プロパティにセットしなければならない。設定する UUID が実在するステートメントに合致するように検証する義務を LRS は負わない。

以下の表では、ステートメント参照オブジェクトの全プロパティを一覧表示している

<table border ="1">
    <tr><th>プロパティ</th><th>タイプ</th><th>説明</th><th>必須</th></tr>
    <tr><td>objectType</td><td>String</td><td>この場合、 "StatementRef" としなければならない</td><td>必須</td></tr>
    <tr><td>id</td><td>UUID</td><td>ステートメントの UUID</td><td>必須</td></tr>
</table>

###### 例

あるステートメントが ID 8f87ccde-bb56-4c2e-ab83-44982ef22df0 として既に記録されて
いると仮定したとき、以下の例では、どの様にして新しいステートメントで元のステートメン
トにコメントを発行するかを示している。

```
{
    "actor" : {
        "objectType": "Agent",
        "mbox":"mailto:test@example.com"
    },
    "verb" : {
        "id":"http://example.com/commented",
        "display": {
            "en-US":"commented"
        }
    },
    "object" : {
        "objectType":"StatementRef",
        "id":"8f87ccde-bb56-4c2e-ab83-44982ef22df0"
    },
    "result" : {
        "response" : "Wow, nice work!"
    }
}
```

<a name="substmt"/></a>
##### サブステートメント

###### 説明
サブステートメントは、親ステートメントの一部として含まれる新しいステートメントである

###### 必要条件

* サブステートメンは、"objectType" プロパティで"SubStatement"として明示しなくてはならない
* サブステートメントは、他のサブステートメントの必要要件に加えて、ステートメントとして評価されなければならない
* サブステートメントは、"id", "stored", "version" or "authority"プロパティを持ってはならない
* サブステートメント内に、サブステートメントを含んではならない。すなわち、入れ子にはできない。

###### 例

サブステートメントの興味深い使い方の一つは、意図を示すステートメントの構築である。
例えば、サブステートメントを使って、何らかのアクションを起こそうとしたことを示す目的で
 ```"<I> <planned> (<I> <did> <this>)"``` といった形式のステートメントを作成することが
できる。次の具体例では、 "I planned to visit 'Some Awesome Website'" を示している。


```
{
    "actor": {
        "objectType": "Agent",
        "mbox":"mailto:test@example.com"
    },
    "verb" : {
        "id":"http://example.com/planned",
        "display":{
            "en-US":"planned"
        }
    },
    "object": {
        "objectType": "SubStatement",
        "actor" : {
            "objectType": "Agent",
            "mbox":"mailto:test@example.com"
        },
        "verb" : {
            "id":"http://example.com/visited",
            "display":{
                "en-US":"will visit"
            }
        },
        "object": {
            "id":"http://example.com/website",
            "definition": {
                "name" : {
                    "en-US":"Some Awesome Website"
                }
            }
        }
    }
}
```

<a name="result"/></a>
#### 4.1.5 Result（結果）

###### 説明
ステートメントの取込み結果を計るためのオプションフィールド

###### 詳細
以下の表には結果オブジェクトのプロパティが一覧表示されている

<table border="1">
<tr><th>プロパティ</th><th>タイプ</th><th>説明</th><th>必須</th></tr>
<td>score</td>
<td>Object</td>
<td>.エージェントのスコア。<a href ="#Score">Score</a></a> を参照</td>
<td>任意</td>
</tr>
<tr><td>success</td><td>Boolean</td><td>アクティビティの試みが成功したかどうかを表す</td>
<td>任意</td>
</tr>
<tr><td>completion</td><td>Boolean</td><td>アクティビティが完了したかどうかを表す</td>
<td>任意</td>
</tr>
<tr>
<td>response</td><td>String</td><td>アクティビティのために適切にフォーマットされたレスポンス</td>
<td>任意</td>
</tr>
<tr>
<td>duration</td><td>IISO 8601 に基づいた    ステートメントが発生してからの経過時間 0.01秒の精度のフォーマット
</td><td>ステートメントが発生してからの経過時間</td>
<td>任意</td>
</tr>
<tr>
<td>extensions</td><td>Object</td><td>必要に応じて追加される他のプロパティを表すマップ。Extensions を参照
</td>
<td>任意</td>
</tr>
</table>

<a name="Score"/></a>
##### 4.1.5.1 スコア（Score)

###### 説明
エージェントによって達成された、類別されたアクティビティの結果を表わすオプションの数字フィールド

###### 詳細

以下の表は、スコアオブジェクトの定義である。

<table border ="1">
    <tr><th>プロパティ</th><th>タイプ</th><th>説明</th><th>必須</th></tr>
    <tr><td>scaled</td><td>-1から1までの十進数</td><td>CORM2004 4th 版の 'cmi.score.scaled' を参照</td><td>推奨</td></tr>
    <tr><td>raw</td><td>min と max の間の十進数  'cmi.score.raw'を参照
    （現状、そうでなければ無制限）</td><td>'cmi.score.raw' を参照</td><td>任意</td></tr>
    <tr><td>min</td><td>maxよりも小さい十進数 </td><td>'cmi.score.min' を参照</td><td>任意</td></tr>
    <tr><td>max</td><td>minよりも大きい十進数 </td><td>'cmi.score.max' を参照</td><td>任意</td></tr>
</table>

###### 必要条件

* 論理的なパーセント基準のスコアが既知の場合は、スコアオブジェクトは 'scaled' を組み込むべきである。
* スコアオブジェクトは、進捗もしくは完了に関連するスコアのために使用すべきではない。代わりに拡張プロファイルの拡張機能の利用を検討すること。

<a name="context"/></a>
#### 4.1.6 Context (文脈)

###### 説明
文脈依存の情報をステートメントに付加するための任意のフィールド。全てのプロパティは任意である。

###### 背景
context フィールドは文脈依存の情報をステートメントに付加する機会を提供する。
それは経験が集団活動の一部として行われた場合には、その経験の教授者の名前や、経験がより大きな活動にどのように組み込まれるか、といった情報を記録することができる。

###### 詳細

<table>
<tr><th>プロパティ</th><th>タイプ</th><th>説明</th><th>必須</th></tr>
<tr>
<td>registration</td>
<td>UUID</td>
<td>ステートメントが関連している登録
</td>
<td>任意</td>
</tr>
<tr>
<td>instructor</td>
<td>Agent (may be a group)</td>
<td>ステートメントのアクタに含まれない場合、ステートメントが関係する教授者</td>
<td>任意</td>
</tr>
<tr>
<td>team</td>
<td>Group</td>
<td>ステートメントのアクタに含まれない場合、ステートメントが関係する集団</td>
<td>任意</td>
</tr>
<tr>
<td>contextActivities</td>
<td>contextActivities Object</td>
<td>このステートメントが関係する、学習活動コンテキストのタイプを持つマップ。有効なコンテキストタイプは "parent" 、 "grouping" 、 "category" 、そして "other" である。</td>
<td>任意</td>
</tr>
<tr>
<td>revision</td>
<td>String</td>
<td>このステートメントに関わる学習活動のリビジョン。形式は任意である。</td>
<td>任意</td>
</tr>
<tr>
<td>platform</td>
<td>String</td>
<td>この学習活動の経験で用いられるプラットフォーム。</td>
<td>任意</td>
</tr>
<tr>
<td>language</td>
<td>String (as defined in RFC 5646 )</td>
<td>利用可能または既知である場合、このステートメントで記録される経験が(主に)発生した際の言語コード。</td>
<td>任意</td>
</tr>
<tr>
<td>statement</td>
<td>[Statement Reference] (#stmtref)</td>
<td>このステートメントのコンテキストと見なされる、他のステートメント。</td>
<td>任意</td>
</tr>
<tr>
<td>extensions</td>
<td>Object</td>
<td>このステートメントに関連する、他の、ドメイン特化コンテキストのマップ。例えばフライトシミュレータにおける高度、対気速度、風、飛行姿勢、 GPS 座標の全ては関連を持ちうる。(『拡張機能』参照)
</td>
<td>任意</td>
</tr>
</table>

###### 必要条件

* revision プロパティを使う際は、ステートメントの目的語がアクティビティである場合のみにしなければならない。
* platform プロパティを使う際は、ステートメントの目的語がアクティビティである場合のみにしなければならない。
* 適用できないか未知であるなら、 language プロパティは使用してはいけない。
* revision プロパティは(綴り間違いのような)軽微な問題の修正を記録する際に用いるべきである。
* revision プロパティは、アクティビティの学習目標、教授法、または資産における大きな変化があるならば、用いるべきでない。そのような場合は新しいアクティビティを用いてほしい。

_注記：_ リビジョンは xAPI の範囲内で、何らかの動作に影響を与えることはない。それは、単に報告ツールが利用できるように記録される。

<a name="Registration"/></a>
##### 4.1.6.1 Registrationプロパティ
###### 説明
特定の学習活動を行っている学習者のインスタンス。

###### 詳細
LRS が LMS の不可欠な部分である場合、LMS は登録の概念を持つことが予想される。
xAPI では、登録という概念はより広く適用される。登録は学習の試行や学習期間に関す
るものと見なすことができ、また一つの記録が登録のアクティビティにわたることも可能
である。また、学習活動の完了が登録の終了を意味するとは限らない。そして登録は、
一つのエージェントには限定されない。

<a name="contextActivities"/></a>
##### 4.1.6.2 ContextActivities プロパティ

###### 説明
このステートメントが関連する、学習活動コンテキストのタイプのマップ。

###### 背景
多くのステートメントは現在対象となる一つのオブジェクト・アクティビティのみを含む
わけではなく、文脈上関連する他の活動にも関わる。"Context activities" はこれらの関連するアクティビティを構造化して表すことを可能にする。

###### 詳細
4つの有効なコンテキストタイプがある。対象のステートメント中で、これらの全てが使わ
れたり、どれかが使われたり、あるいはどれも使われないということがある。

1. __Parent__: ステートメントの目的語であるアクティビティへの、直接の関わり
を持つアクティビティ。ほとんどの場合、ただ一つの明確な親を持つか、あるいは
一つも持たない。複数持つことはない。例えば、クイズの設問についてのステート
メントは parent アクティビティとして「クイズ」を持つ。

2. __Grouping__: ステートメントの目的語であるアクティビティへの、間接的な関
わりを持つアクティビティ。
例: 資格取得の一部をなす講座。講座は複数回の講義で構成される。講座は講義に対
して parent の関係にあり、資格取得は講義に対して grouping の関係にある。

3. __Category__: ステートメントを分類するためのアクティビティ。「タグ」と同
義である。カテゴリは(他の分類と同様に) xAPI の挙動の "profile" を示すために用
いられるべきである。例えば、アンナは生物学の試験に挑戦する。そしてステート
メントは(訳注: AICC の) CMI-5 プロファイルを用いて記録される。そのステートメ
ントのアクティビティは試験を参照し、そのカテゴリは CMI-5 プロファイルとなる。

4. __Other__: 他のフィールドのいずれにも合わない context アクティビティ。例え
ば、アンナは生物学の試験のために教科書を使い学んでいる。このステートメントの
アクティビティは教科書を参照し、試験は other タイプのコンテキスト・アクティビ
ティとなる。

0.95 版のステートメントが、1.0.0 版と互換性を保つために、単独の Activity オブジェクトを
値として使っても構わない。

__注記:__ この節は、ステートメントオブジェクトが持つ全ての関係性を説明するた
めのものではない。説明しているのは、(オブジェクトの性質がそれを決定するのに
しばしば重要であるのだが)特定のステートメントに適合する関係性についてである。
例えば、テストについてのステートメントに、そのテストを利用している講座を parent
として含めるのは妥当だが、grouping の値として、関連の可能性がある全ての学位
プログラムを並べるのは妥当とは言えない。

###### 必要条件

* contextActivities オブジェクトの全てのキーは、 parent 、 grouping 、 category 、あるいは other の中の一つでなければならない。
* contextActivities オブジェクトの全ての値は、一つの Activity オブジェクトか、 Activity オブジェクトの配列でなければならない。
* LRS は contextActivities オブジェクトの値は、それを単一の Activity オブジェクトとして受信した場合でも、配列として返さなければならない。
* LRS は単一の Activity オブジェクトを返す場合、その Activity を含む要素数1の配列として返さなければならない。
* クライアントは、 contextActivities オブジェクト中の全ての値が Activity オブジェクトの配列であり、単独の Activity オブジェクトの形を取らないようにすべきである。

###### 例

次のような階層構造を考えてほしい。
「設問1から6」は「テスト1」に含まれ、同様にテスト1は「代数学1」講座に属している。
6つの設問は「テスト1」を親と宣言することで、テストの一部として登録される。また、そ
れらは「代数学1」の他のステートメントと共に grouping され、階層高層が完全に複写
される。ステートメントの目的語が(アクティビティでなく)エージェントであるときに、これ
は特に有用である。「アンドリューは、代数学1のコンテキストでベンを指導した」。

```
{
    "parent" : [
         {"id" : "http://example.adlnet.gov/xapi/example/test1"}
     ],
     "grouping" : [
         {"id" : "http://example.adlnet.gov/xapi/example/Algebra1"}
     ]
}

```

<a name="timestamp"/></a>
#### 4.1.7 Timestamp (タイムスタンプ)

###### 説明
経験が発生した時刻。

###### 詳細
ステートメント中のタイムスタンプは Stored (ステートメントが記録された時刻) と異なる場合がある。たとえば、経験が発生してから LRS がステートメントを受信するまでの間に、遅延が発生することがある。
経験がある期間にわたって発生した場合には、タイムスタンプは、開始、終了や
経験中の任意の時点を表すことができる。
さまざまな経験のタイムスタンプを記録するために、実践コミュニティは適切な
時点を定めることが期待される。例えば、レストランでの食事の経験を記録する
場合には開始のタイムスタンプを記録することが最適かもしれないが、資格の完
了経験を記録する場合には経験の最後のタイムスタンプを記録することが最適と
なるかもしれない。
これらの例は、単に例示のみを目的としており、規範的を意味するものではない。

###### 必要条件
* timestamp は ISO 8601 に従う形式でなければならない。
* timestamp はタイムゾーンを含むべきである。
* サブ・ステートメントの外部である場合、 timestamp は現在または過去の時刻となるべきである。
* timestamp は経験が発生した期間の中での任意の時点を指してよい。
* timestamp は、秒を少なくとも3桁の精度で切り捨てられるか、あるいは丸められてもよい(ミリ秒の精度は保たれなければならない)。
* timestamp は、それがサブ・ステートメントに含まれるならば、計画した学習の期限を示すために未来の時刻としてもよい。

<a name="stored"/></a>
#### 4.1.8 Stored

###### 説明
ステートメントが LRS に記録された時刻。

stored プロパティは、ステートメントが記録されたときの正確な時刻である。ステートメント中の経験が発生した時刻を記録する際は、 Timestamp を使ってほしい。

###### 必要条件

* stored プロパティは ISO 8601 に従う形式でなければならない。
* stored プロパティはタイムゾーンを含むべきである。
* stored プロパティは現在または過去の時刻となるべきである。
* stored プロパティは、秒を少なくとも3桁の精度で切り捨てられるか、あるいは丸められてもよい(ミリ秒の精度は保たれなければならない)。

<a name="authority"/></a>
#### 4.1.9 Authority (権限)

###### 説明
authority プロパティは「誰、または何がこのステートメントが真であると主張するか」の情報を提供する。

###### 詳細

権限を主張するということは、システムやアプリケーション上でのユーザを認証することを意味する。

###### 必要条件

* Authority は 3-legged OAuth を除き、2つのエージェントによってグループが形成されてしまう場面においては、1個のエージェントが該当しなければならない。この2つのエージェントは、アプリケーションとユーザを表す。
* ユーザが HTTP ベーシック認証を用いて直接接続する場合やグループの一員である場合、 LRS は全体の権限を持つエージェントとしてユーザを取り込まなければならない。
* LRS は記録された全てのステートメントが権限を持っていることを確認しなければならない。
* LRS はこれらのステートメントを送信するための資格情報に基づいて、全ての記録された受信済ステートメントにおける権限を上書きすべきである。
* LRS は受信した権限を変更せずに残してもよいが、強い信頼関係が確立された場合に限るべきであり、また残す際には細心の注意を払う必要がある。
* ユーザが HTTP ベーシック認証を用いて直接接続する場合、あるいは 3-legged OAuth の一部である場合、 LRS は正当な識別プロパティによってユーザを識別してもよい。

##### 権限としての OAuth 資格情報

###### 説明
これは OAuth 利用のフローである。 2-legged と 3-legged の OAuth がサポートされる。

###### 詳細
このワークフローは、ステートメントが検証済 OAuth コネクションを用いて格納され、 LRS
がステートメントの authority プロパティを作成、または変更することを仮定している。

3-legged OAuth ワークフローでは、認証は "OAuth consumer" と「 OAuth サービスプロ
バイダのユーザ」の両方を含む。例えば、 Facebook アカウントにおける、許可された Twitter
プラグインからの要求は、クライアントアプリケーションとしての Twitter やユーザに対す
るだけでなく、両者の固有の結びつきに対する資格情報を含んでいる。

###### 必要条件
* authority は OAuth consumer を示すエージェントオブジェクトか、エージェントオブジェクトそのもの、もしくは 3-legged OAuth の場合にはグループの一部としてのエージェントオブジェクトを含まなければならない。
* OAuth consumer を表すエージェントは、アカウントによって識別されなければならない。
* OAuth consumer を示すエージェントは、「アカウント名」のフィールドとして consumer キーを用いなければならない。
* OAuth consumer を示すエージェントが登録済アプリケーションであるならば、トークンリクエストエンドポイントはアカウントのホームページとして用いられなければならない。
* OAuth consumer を示すエージェントが登録済アプリケーションでない場合は、一時的な資格情報のエンドポイントがアカウントのホームページとして用いられなければならない。
* LRS は、アカウント名が未登録のアプリケーションと同一のソースによる権限のアプリケーション部分を、信頼してはならない。(複数の未登録アプリケーションは、同じ consumer キーを選択できる。その結果として、一時的な資格情報とアカウント名の組合せを検証するための、信頼できる方法は存在しない。)
* 未登録のそれぞれの consumer は、一意な consumer キーを使うべきである。

###### 例

OAuth consumer とユーザのペア。

```
?"authority": {
    "objectType" : "Group",
    "member": [
        {
            "account": {
                "homePage":"http://example.com/xAPI/OAuth/Token",
                "name":"oauth_consumer_x75db"
            }
}, {
            "mbox":"mailto:bob@example.com"
        }
] }

```

<a name="version"/></a>
#### 4.1.10 Version (バージョン)
###### 説明
LRS からのデータを処理するシステムは、ステートメントのバージョン情報によって、そ
れらの挙動を決めることができる。ステートメントデータモデルが全てのバージョン 1.0.x
を通じて一貫性が保証されるので、 LRS 間のデータフローをサポートするために、 LRS
には受け入れられるステートメントのバージョンにおける柔軟性が与えられる。

###### 必要条件
* バージョンは API Versioning 仕様中の API バージョンヘッダのレイアウト形式に従わなければならない。

###### LRS の必要条件
* 有効なステートメントについて、 LRS は "1.0." で始まるバージョンの全てのステートメントを受け入れなければならない。
* "1.0." から始まらないように指定されたバージョンの全てのステートメントを、 LRS は拒否しなければならない。
* LRS によって返されるステートメントは、受け入れられたときのバージョンを保持しなければならない。バージョン情報が存在しないなら、バージョンは 1.0.0 に設定されなければならない。

###### クライアントの必要条件
* クライアントがステートメントのバージョンを設定するならば、それは 1.0.0 でなければならない。
* クライアントはステートメントのバージョンを設定すべきではない。

<a name="attachments"/></a>
#### 4.1.11 Attachments (添付資料)

###### 説明
学習経験の証跡を提供するデジタル文書

###### 背景
場合により、添付文書は論理的に学習記録の重要な部分となる可能性がある。航空管制
との通信シミュレーション、エッセイ、ビデオなどを考えてみてほしい。添付文書の他の例
としては、経験の結果として与えられた修了証書（の画像）がある。これらの添付文書を
LRS に記録したり LRS から読み出したりする方法があることは有益である。

###### 詳細
以下のテーブルは添付文書オブジェクトのすべてのプロパティを示す。
<table>
    <tr><th>プロパティ</th><th>タイプ</th><th>説明</th><th>必須</th></tr>
    <tr>
        <a name="attachmentUsage" /></a>

        <td>usageType</td>
        <td>IRI</td>
        <td>この添付文書の利用方法を規定する。例えば、添付文書の期待されるユースケースの１つに「修了証明」を含むことがある。この用途に対応するタイプ IRI を作成し、修了証明添付文書と一緒に利用されるべきである。</td>
        <td>必須</td>
    </tr>
    <tr>
        <td>display</td>
        <td><a href="#misclangmap">Language Map</a></td>
        <td>この添付文書の名前（タイトル）を表示する。</td>
        <td>必須</td>
    </tr>
    <tr>
        <td>description</td>
        <td><a href="#misclangmap">Language Map</a></td>
        <td>添付文書の説明</td>
        <td>任意</td>
    </tr>
    <tr>
        <td>contentType</td>
        <td><a href="https://www.ietf.org/rfc/rfc2046.txt?number=2046">Internet Media Type</a></td>
        <td>添付文書のコンテンツタイプ</td>
        <td>必須</td>
    </tr>
    <tr>
        <td>length</td>
        <td>integer</td>
        <td>オクテットで示した添付文書データの長さ</td>
        <td>必須</td>
    </tr>
    <tr>
        <td>sha2</td>
        <td>String</td>
        <td>添付文書データの SHA-2 (SHA-256, SHA-384, SHA-512) ハッシュ。SHA-224は使うべきではない。最低256ビット以上のキーが推奨される。</td>
        <td>必須</td>
    </tr>
    <tr>
        <td>fileUrl</td>
        <td>IRL</td>
        <td>添付文書データが取り出されうる IRL、あるいは、取り出しが可能であった IRL。</td>
        <td>任意</td>
    </tr>
</table>

_添付文書交換の手続き_

1. 添付文書を含むステートメントは、以下に記述する転送フォーマットにより構成される。

2. ステートメントは、"multipart/mixed" のコンテンツタイプで、受け側のシステムに送られる。添付文書は転送の最後に配置される。

3. 受け側のシステムは、最初の部分にある情報に基づき、ステートメントを受入れるか拒否するかを決定する。

4. 仮に添付文書を受入れたときに、生データの SHA-2 とヘッダーで宣言された SHA-2 とを比較することで、ステートメントにある添付文書ヘッダーと生のデータを照合することができる。他の方法で照合してはならない。

###### 添付文書ステートメントバッチのための必要条件

添付文書を含むステートメントバッチ、ステートメントの結果、または、１つのステートメントは、以下の条件のうちの１つを満たさなければならない:

* 添付文書フィルタが false の場合のステートメントの結果を除き、"application/json"  タイプで、全ての添付文書毎に fileUrl を含まなければならない。
* RFC1341 (http://www.w3.org/Protocols/rfc1341/7_2_Multipart.html) における multipart/mixed の定義に準拠しなければならない。かつ、以下の条件を満たさなければならない:
    * multipart 文書の最初にはステートメント自身が "application/json" タイプで含まれる。
    * 他の追加部分は、添付文書の生のデータを含み、ステートメントの論理部分を形成する。この機能はステートメントリソースに対して PUT や POST が発行されたときに利用可能である。
	* 最初の（ステートメント）部分に続く各部分のヘッダーには X-Experience-API-Hash フィールドを含まなければならない。
	* このフィールドは、この部分に含まれる添付文書に一致した添付文書宣言の "shar2" プロパティと一致していなければならない。
	* 最初の（ステートメント）部分に続くそれぞれのパートのヘッダーに、
"Content-Transfer-Encoding" の値として "binary" を含めなければならない。
    * 複数のステートメントが同時に送られ、同じ添付文書が使われた時は、１つの添付文書のデータだけを含むべきである。
    * 各部分のヘッダーには Content-type フィールドを含むべきであり、最初の部分は application/json タイプにしなければならない。

###### LRSの必要条件

* クライアントから要求があった場合は、LRS は上記に示す転送形式で添付文書を含まなければならない。（[7.2 ステートメント API](#stmtapi)参照）
* LRS は添付文書の要求なしでは他の LRS からステートメントを引き出してはならない。
* LRS は、受け取った添付文書データがある場合は、それらを添付することなく、ステートメントを他の LRS に送ってはならない。
* "application/json" のドキュメントタイプの文書を PUT や POST で受け取る場合、 LRS は、添付文書オブジェクトを含まないステートメントのバッチを受入れなければならない。
* "application/json" のドキュメントタイプの文書を PUT や POST で受け取る場合、 LRS は、投入された fileUrl を持つ添付文書オブジェクトのみを含むステートメントのバッチを受入れなければならない。
* "multipart/mixed" のドキュメントタイプの文書を PUT や POST で受け取る場合、 LRS は、上述の転送フォーマットで、添付文書を含むステートメントのバッチを受入れなければならない。
* "multipart/mixed" のドキュメントタイプの文書を PUT や POST で受け取る場合、 LRS は、fileUrl を含まないか、あるいは、受信した添付文書の一部がハッシュに適合しない場合、添付文書を持つステートメントのバッチを拒否しなければならない。
* "multipart/mixed" のドキュメントタイプの文書を PUT や POST で受け取る場合、LRS は添付文書の部分に対してバイナリの Content-Transfer-Encoding を前提とすべきである。
* LRS は、その LRS が許可された設定より大きいステートメント（のバッチ）を拒否することができる。

__注記:__ mime/multipart フォーマットを使うステートメントバッチが添付文書を含む場合
は、何の必要条件もない。

###### クライアントの必要条件

* クライアントは上記で記述された添付文書を含むステートメントを送ることができる。
* クライアントは、POST を利用するときに、そのうちのいくつかが添付文書を含むかあるいはすべてが添付文書を含む複数のステートメントを送ることができる。
* クライアントは、"multipart/mixted" 形式に基づく全ての必要条件を無視し、全ての添付文書オブジェクトが fileUrl を持つ "application/json" タイプのバッチを送ることができる。

###### 例

添付文書を含むステートメントの非常に簡単な例である。以下の点に注意してほしい：

* 以下の例の boundary は有効な文字クラスを例示するために選択されたものである。
* 選択された boundary は、エンコードされた各添付文書のどの部分にもマッチしない。
* 読みやすくするために、添付文書の例は text/plain にしている。仮に、image/jpeg のようにバイナリタイプであったとしても、符号化されず、生のオクテットデータがそのまま含まれる。
* RFC 1341 より、boundary は ```<CRLF>``` のあとに、さらにその後のヘッダーで定義された boundary 文字列を続けたものとなる。

これらのメッセージを構築あるいは構文解析する場合に```<CRLF>```を忘れてはいけない。

ヘッダー:

```
Content-Type: multipart/mixed; boundary=abcABC0123'()+_,-./:=?
X-Experience-API-Version:1.0.0
````
コンテンツ:

```

--abcABC0123'()+_,-./:=?
Content-Type:application/json

{
    "actor": {
        "mbox": "mailto:sample.agent@example.com",
        "name": "Sample Agent",
        "objectType": "Agent"
    },
    "verb": {
        "id": "http://adlnet.gov/expapi/verbs/answered",
        "display": {
            "en-US": "answered"
        }
    },
    "object": {
        "id": "http://www.example.com/tincan/activities/multipart",
        "objectType": "Activity",
        "definition": {
            "name": {
                "en-US": "Multi Part Activity"
            },
            "description": {
                "en-US": "Multi Part Activity Description"
            }
        }
    },
    "attachments": [
        {
            "usageType": "http://example.com/attachment-usage/test",
            "display": { "en-US": "A test attachment" },
            "description": { "en-US": "A test attachment (description)" },
            "contentType": "text/plain; charset=ascii",
            "length": 27,
            "sha2": "495395e777cd98da653df9615d09c0fd6bb2f8d4788394cd53c56a3bfdcd848a"
        }
    ]
}
--abcABC0123'()+_,-./:=?
Content-Type:text/plain
Content-Transfer-Encoding:binary
X-Experience-API-Hash:495395e777cd98da653df9615d09c0fd6bb2f8d4788394cd53c56a3bfdcd848a

here is a simple attachment
--abcABC0123'()+_,-./:=?--
```

<a name="dataconstraints"/></a>
#### 4.1.12 データの制約

###### 説明

ステートメントで使われる全てのプロパティはあるタイプに制限されている。また、それらのタ
イプはステートメントを処理するシステムの動作を制約している。明確化のために、どの部分
において、準拠するシステムが特定の振る舞いを行う責任があるかを強調し、いくつかの主な
必要条件をここに記述する。

###### クライアントの必要条件

実行ガイダンスを強調し、明確化し、提供するために、以下の必要条件は、他にすでに
含まれている特に重要な必要条件を繰り返している。
IRI の完全な検証は非常に難しいため、データの可搬性を担保する責任の大部分はクライアント側にある。

* 値として送信される IRI は有効なものでなければならない。
* 同様の理由から、言語マップのキーは、有効な RFC 5646 (http://tools.ietf.org/html/rfc5646) 言語タグと一緒に送られなければならない。
* IRI の生成には、文字列結合ではなく、ライブラリを利用すべきである。
* 特別に指定されない限り、値は大文字/小文字を区別すると考えるべきである。
* 大文字/小文字の区別がないデータを送る場合は、小文字で送られるべきである。

###### LRS の必要条件

* 以下の場合、LRS はステートメントを拒否しなければならない。
    * 値がない場合（拡張の中を除く）
    * 数値が必要な場所に文字列が与えられている場合。（その文字列に数字が含まれる場合でも）
    * 2値が必要な場所に文字列が与えられている場合。（その文字列に2値が含まれる場合でも）
    * 特別な形式（mailto, IRI, UUID, または IRI）の文字が必要な場所に、空文字列を含む、形式に合わないキーまたは値が与えられている場合。
    * あるキーのケースが標準で規定されたケースに合わない場合。
    * 値のケースが数字の値に制限されていて、標準で示された数字の値に一致しない場合。
* LRS はスキーマを持たない、IRL、IRI、または IRI の値を含むステートメントを拒否しなければならない。
* LRS は少なくとも、言語マップキーのトークンの長さのシーケンスが [RFC 5646](http://tools.ietf.org/html/rfc5646) 標準に一致することを認証しなければならない。
* LRS は、数字を最低限 IEEE754 32ビットの精度で処理して記録しなければならない。
* LRS はステートメントにある同じタイプの値の検証と同じ基準で、パラメータの値の検証を行わなければならない。__注記:__ JSON とは異なり、文字列パラメータの値は引用符でくくられない。
* LRS は特別に指定されない限り、すべての値を大文字/小文字を区別して扱うべきである。
* LRS が形式不適合による拒絶の必要条件を満たすためには、IRL, IRI, および IRI フォーマットについてベストエフォートの検証をすればよい。
* LRS は、言語マップキーが形式に合わない要求拒否を満たすために、ベストエフォート検証を使うことができる。

<a name="retstmts"/></a>

### 4.2 ステートメントの検索

###### 説明
一連のステートメントは検索クエリを "statements" とすることで、検索が可能となる。詳細は[7.2 ステートメント API](#stmtapi)を参照。

###### 詳細
下の表はステートメント API の検索結果のためのデータ構造を示している。
<table>
    <tr><th>プロパティ</th><th>タイプ</th><th>説明</th><th>必須</th></tr>
    <tr>
        <td>statements</td>
        <td>Array of Statements</td>
        <td>ステートメントのリスト。さらに結果があるのに，戻ってきたリストが（ページ制限により）制限されていたら，コンテイナに含まれる "statements" プロパティに配置されるだろう。コンテイナは，ステートメント結果オブジェクトのさらなる要素によって提供される IRL に置かれる。

        ステートメントのリスト。（ページ区切りにより）戻されるリストが一部に制限されており、リストの続きがある場合、それらは結果の Statement オブジェクトの "more" 要素によって提供される IRL に存在するコンテナの "statements" プロパティに配置される。

        合致するステートメントがない場合は、このプロパティは空の配列をもつ。
        </td>
        <td>必須</td>
    </tr>
    <tr><td>more</td><td>IRL</td>
        <td>追加の結果を取り込むために用いられる相対 IRL。フルパスとオプションのクエリ文字列で、スキーム、ホスト、ポートの情報を含まない。
<br/><br/>

この IRL は LRS によって戻された後、少なくとも24時間は利用可能でなければならない。これらの IRL と関連するクエリデータを保存しておく必要性を避けるために、LRS はクエリを実行するのに必要な全ての情報を IRL に含めてもよいが、非常に長い IRL の生成は避けるべきである。利用者は IRL の戻り値から意味を解釈すべきではない。
        </td>
        <td>返されるリストの内容が制限される場合は必須、それ以外の場合は任意</td>
    </tr>
</table>

###### 必要条件

* more プロパティから取り出された IRL は、LRSによって戻された後、少なくとも24時間は利用可能でなければならない。
* LRSは、クエリが、IRL と関連するクエリデータを保存する必要性を避け続けるために、more プロパティの IRL 中に全ての必要な情報を含めても良い。
* LRSは more プロパティの中では、非常に長い IRL の生成は避けるべきである。
* LRS は、オリジナルのクエリが実行された時のバッチに含まれるたであろう、more プロパティ内の IRL がアクセスされたときに、クエリを再実行しても良い。その際に、
後に無効化されたステートメントを除外しても良い。
* または、LRS はオリジナルのクエリが実行されたときに返されるべきステートメント
と一致するように、more プロパティで返されるステートメントのリストをキャッシュ
しておいても良い。
* その場合、LRS はキャッシュされたステートメントのリストから、無効化されたステ
ートメントを削除しても良い。
* 利用者は more プロパティから返ってくる IRL の戻り値から意味を解釈すべきではない。

<a name="voided"/></a>

#### 4.3 無効

###### 背景

ステートメントが論理的に変更されたり削除されたりすることは無い、という事実によって、LRS が正確で完全なデータを収集しているという確実性が保証される。このステートメントの不変性が、xAPI の分散性を可能にする重要な要因である。

しかしながら、すべてのステートメントが、一度発行されると永久に有効である、ということではない。誤りや他の要因で、以前に作られたステートメントを無効とマークすることが必要になることがある。これを、”ステートメントの無効化"と呼び、予約された動詞 “http://adlnet.gov/expapi/verbs/voided" はこの目的で使用される。他のステートメントを無効化するステートメント自身を無効化することはできない。

###### 必要条件

* 他のステートメントを無効化するステートメントを発行するときは、無効化ステートメントの目的語は "objectType" フィールドを "StatementRef" に設定しなければならない
* 他のステートメントを無効化するステートメントを発行するとき、無効化ステートメントの目的語では、無効化すべきステートメントの ID を ID フィールドで指定しなければならない。
* LRS は、ステートメントその物が無効化ステートメントではなく、LRS がはじめのステートメントに対する無効化ステートメントを含む場合にのみステートメントを評価しなければならない。
* 他のステートメントを無効化するステートメントを受け取ったとき、LRS は、その要求がステートメントの無効化を認められたソースからの要求でない場合は、HTTP 403 'Forbidden' にて、無効化ステートメントを含むリクエスト全体を拒否すべきである。
* 他のステートメントを無効化するステートメントを受け取った場合、LRS は、無効化されるべきステートメントの Object が存在しないことを理由に、要求を拒絶するべきではない。
* 他のステートメントを無効化するステートメントを受け取ったとき、LRS は無効化されたステートメントによって、もともと導入されたアクティビティやエージェントの定義に対する変更をロールバックしてもよい。
* 以前の無効ステートメントを有効化するアクティビティプロバイダは新しい id で再度ステートメントを発行すべきである。
* レポートシステムは無効化された、または無効化するためのステートメントを標準では表示すべきではない。

__注記:__ 他のステートメントの参照作成に関する詳細については、[4.1.4.3 目的語がステートメントだった場合](#stmtasobj) の[ステートメント参照](#stmtref)  を参照して欲しい。呼ばれた際にいかに無効化ステートメントが振舞うかについては、7.2　ステートメント APIの [StatementRef](#queryStatementRef) を参照してほしい。

###### 例

このステートメントの例は、ステートメント id が "e05aa883-acaf-40ad-bf54-02c8ce485fb0" で
示される以前のステートメントを無効化する。

```
{
    "actor" : {
        "objectType": "Agent",
        "name" : "Example Admin",
        "mbox" : "mailto:admin@example.adlnet.gov"
    },
    "verb" : {
        "id":"http://adlnet.gov/expapi/verbs/voided",
        "display":{
            "en-US":"voided"
        }
    },
    "object" : {
        "objectType":"StatementRef",
        "id" : "e05aa883-acaf-40ad-bf54-02c8ce485fb0"
    }
}
```

<a name="signature"/></a>

#### 4.4 署名付きステートメント

##### 説明
ステートメントは、強固で耐久性のあるステートメントの信頼性と完全性を提供するた
めに<a href="http://ja.wikipedia.org/wiki/デジタル署名">デジタル署名</a>を含む
ことができる。

##### 背景
ステートメントの中には規制上のあるいは法的に重要なものもあるだろう。また、強固
で耐久性のある信頼性と完全性の証跡を必要とするだろう。これらのステートメントを
最初に記録されたシステムを信頼せずに、あるいはシステムにアクセスせずに確認す
る必要があるかもしれない。デジタル署名は、第三者システムがそのようなステートメ
ントを確認することを可能にする。

##### 詳細

署名付きステートメントは、JSON web署名(JWS) を添付文書として含む。このことにより、
ステートメントの原本をシリアル化したものが、署名とともに添付されることが可能となる。
相互運用性のために、JWS のアルゴリズムの "RSA+SHA" シリーズが選択され、署名
者の発見可能性のために、X.509 証明書が使われるべきである。

##### 必要条件

* 署名付きステートメントは、 usageType が "http://adlnet.gov/expapi/attachments/signature"
で、contentType が "application/octet-stream"　である、添付文書として定義される、
JSON web signature (JWS) を含まなければならない： http://tools.ietf.org/html/draft-ietf-jose-json-web-signature
* 署名が付加される前に、JWS 署名は、生成されたステートメントの有効な JSON の連続
のデータ本体を持たなければならない。
* JWS 署名は "R256"、"RS384"、または "RS512" のアルゴリズムを使用しなければならない。
* JWS 署名は、X.509 証明と関連した秘密鍵に基づいて生成されるべきである。
* 仮に、X.509 が署名に使われたなら、JWS のヘッダーは関連した証明書チェーンを内包す
る "x5c" プロパティを含むべきである。
* LRS は、HTTP 400 で不正な形式の署名を内蔵するステートメントを記録する要求を拒否しなければならない。
* LRS は、拒否したステートメントの応答には、メッセージを含むべきである。
署名が正しい形式であることを検証するために、LRS は以下のことを実行しなければならない。
    * JWS 署名を復号化して、JWS の署名データから、一連の署名付きステートメントを取り出す。
    * オリジナルステートメントは論理的に受理したステートメントと同じである、ということを証明する。
        * この同等性をチェックする時に、許可または必要とされる LRS の "id", "authority",
"stored", "timestamp" または "version" の処理がもたらす差は無視されなければならない。
    * JWS ヘッダーが X.509 証明書を含むならば、JWS で定義されている手法で、その署名
を証明書で認証する。
* クライアントは、単に LRS が受入れたという理由で、署名が有効であると仮定してはならない。

__注記:__ 含まれる X.509 証明書に対して認証するステップは、安全対策のためでは
なく、署名の中に誤りを発見するためのものである。署名付きステートメントを認証するステップは、要求される確実性の度合いにより変化するものであり、この仕様の規定外である。

#####　例
例は<a href="#AppendixE">Appendix E: 署名ステートメント例</a>を参照。

<div style="page-break-after: always;"></div>
<a name="misctypes"/></a>
## 5.0 各種タイプ</a>

<a name="miscdocument"/></a>

### 5.1 ドキュメント</a>

###### 説明
xAPI により、アクティビティプロバイダは、アクティビティやエージェント、もしくは、それら双方の
組合せに関連したドキュメント形式による任意のデータを記録することが容易になる。

###### 詳細
下記テーブルは、本仕様書のほかの部分のテーブルと異なり、JSON オブジェクトではなく一般的な
プロパティを示していることに注意。ID は IRL で指定され、"updated" は HTTP ヘッダで指定、
"contents" は（オブジェクトではなく）HTTP の文書そのものである。


<table>
 <tr>
    <th>プロパティ</th><th>
タイプ
    </th><th>
説明
    </th>
 </tr>
 <tr>
    <td>
ID
    </td><td>
String
    </td><td>
AP（アクティビティプロバイダ）によって規定される。エージェント、またはアクティビティのスコープ内において一意である。
    </td>
 </tr>
 <tr>
    <td>
updated
    </td><td>
Timestamp
    </td><td>
ドキュメントが最後に修正された時刻
    </td>
 </tr>
 <tr>
    <td>
contents
    </td><td>
Arbitrary binary data
    </td><td>
ドキュメントの内容
    </td>
 </tr>
</table>

<a name="misclangmap"/></a>
### 5.2 言語マップ</a>

###### 説明
言語マップは [RFC 5646言語タグ](http://tools.ietf.org/html/rfc5646) をキーとし、そのタグ
で指定された言語で記述された文字列を値とする辞書である。このマップは、その対象となる
異なる言語において、その文字列の知識が及ぶ限り出来るだけ充実させるべきである。

<a name="miscext"/></a>
### 5.3 拡張

###### 説明

拡張は、アクティビティ定義の一部として、ステートメント文脈の一部として、もしくは、
ステートメントの結果の一部として利用可能なものである。それぞれのケースにおいて、そ
れらは、ある特定の利用のための要素を拡張する自然な方法を提供しようとするものであ
る。こうした拡張のコンテンツは、ある一つのアプリケーションに役立つものであったり、も
しくは、実践コミュニティ全体における規定かもしれない。

###### 詳細

拡張はマップによって定義され、それが現れるステートメントの対応部分と論理的に関連づけ
られる。拡張の値は JSON 値やデータ構造である。ステートメント文脈における拡張は、中
心的な経験に対する文脈を提供し、一方で、結果の文脈では、いくつかの成果に関連する要素
を提供する。アクティビティにおいては、拡張は、あるカスタムアプリケーションやコミュニ
ティ内におけるアクティビティを定義することの手助けとなる追加情報を提供する。IRI キー
下における拡張が持つ値の意味と構造は、IRI の管理者によって定義される。

###### 必要条件

* 拡張マップのキーは IRI でなければならない
* LRS は拡張マップの値をもとにステートメントを拒否してはならない
* クライアントは xAPI 準拠のツール間の相互運用性を高めるために、できるだけ多くの情報を既存の要素にマッピングするよう、常に努力すべきである
* すべての拡張 IRI はコントローラを持つべきである
* IRL 拡張キーのコントローラは、拡張機能の意味を示す人間可読の説明を IRL にて利用可能に提供すべきである

__注記:__ 拡張のみで構成されるステートメントは、ほかのシステムが意味を理解することができないため、無意味である。

<a name="miscmeta"/></a>
### 5.4 識別子メタデータ

##### 説明
ステートメントにおける識別子についての追加の情報をすることができる。これによって、IRI を
解釈することなく、メタデータが内容の表現をすることを可能にする。

##### 詳細
この仕様において利用される、いくつかの IRI 識別子のタイプが存在する：
* <a href="#verb">>動詞</a>
* <a href="#acturi">アクティビティ ID</a>
* <a href="#acttype">アクティビティタイプ</a>
* <a href="#miscext">拡張キー</a>
* <a href="#attachmentUsage">添付文書使用タイプ</a>

アクティビティ ID についてのメタデータの提供については、<a href="#activity">アクティ
ビティ定義オブジェクト</a> を参照のこと。

それ以外の識別子に関するメタデータの提供については、以下のフォーマットを参照のこと。

<table>
        <tr><th>プロパティ</th><th>タイプ</th><th>説明</th><th>必須</th></tr>
        <tr>
        <td>name</td>
            <td><a href="#misclangmap">Language Map</a></td>
            <td>人が読める／見られる 名前</td>
            <td>任意</td>
       </tr>
       <tr>
        <td>description</td>
            <td><a href="#misclangmap">Language Map</a></td>
            <td>説明</td>
            <td>任意</td>
       </tr>
</table>

メタデータが上記のように提供される場合、それは識別子が示す情報についての標準的な情
報源となる。アクティビティ ID 以外に関し、すべてのタイプの IRI 識別子に、確立さ
れ広く認められている識別子を利用することをアクティビティプロバイダに対して推奨
する。

##### 必要条件

* 識別子に対してメタデータが提供されても良い
* メタデータが提供される場合、名前と説明の両方が含まれるべきである
* IRL は、IRL を作成した人物が管理するドメインにおいて定義されるべきである
* 上記、識別子としての IRI において、もし、IRI が本仕様によって作られた IRL であるな
ら、その IRL の管理者は、その IRL が "Content-Type: application/json" がリクエストさ
れた際に、この JSON メタデータを IRL の場所において利用可能にすべきである。
* 識別子が既に存在する場合、アクティビティプロバイダは既存の関連する識別子を利用すべきである
* アクティビティプロバイダは、適切な既存識別子が存在しない場合、独自の識別子を作成、利用しても良い。
* 識別子を定義する場合、アクティビティプロバイダは１ページが複数の識別子の定義を含むことが出来るように、アンカーを含む URI 群を利用しても良い。例：http://example.com/xapi/verbs#defenestrated
* 翻訳等不足する詳細情報を埋めるために、あるいは提供されていなかったり読み込め
ない場合は、このメタデータを完全に置き換えるために、他の情報源を使ってもよい。特
にその識別子が本仕様で利用する目的で作成されなかった場合においては、このメタデ
ータは、識別子の IRL に記録された他のフォーマット内のメタデータを含んでもよい。

<div style="page-break-after: always;"></div>
<a name="rtcom"/></a>
## 6.0 ランタイム通信

６章、７章では、アクティビティプロバイダと LRS の間でどのようにステートメントが転送
されるかについて取扱いながら、 xAPI のより技術的な側面を詳しく説明する。いくつか
のライブラリは、この章の仕様を取り扱う一連の技術（ Java Script を含む）に対して開
発中である。そのため、コンテンツ開発者がこの章の仕様を全て詳細に理解しなくても
よい。

<a name="encoding"/></a>

### 6.1 エンコーディング

###### 必要事項
* 全ての文字列は UTF-8 形式でエンコードし解釈しなければならない。

<a name="apiversioning"/></a>

### 6.2 API のバージョン管理

###### 背景

本仕様の将来の改訂版においては、ステートメントにプロパティを追加するような変更を
導入するかもしれない。

そのため、ステートメントを読み出すシステムは、異なるバージョンのステートメントを含
むレスポンスを受け取るかもしれない。このようなバージョンの違いをバージョンヘッダに
より正確に取り扱うことができ、不完全または混在状態のバージョンの実装が存在してい
ないことを確かめることができる。

セマンティックバージョニングを利用することで、仕様に変更が加えられても、クライアント
と LRS は互換性を確実に知ることができる。

###### 詳細

1.0.0版より、 xAPI は [セマンティックバージョニング 1.0.0]
(http://semver.org/spec/v1.0.0.html) に従いバージョン付けされる。
クライアントからのすべてのリクエストや LRS からの全てのレスポンスは、
"X-Experience-API-Version" を名前、バージョンを値とする HTTP ヘッダーを持たなけ
ればならない。

例:  ``X-Experience-API-Version : 1.0.1``

###### LRS の必要条件:

* LRS は全てのレスポンスに "X-Experience-API-Version" ヘッダを含めなければならない。
* LRS はこのヘッダに "1.0.1" を設定しなければならない。
* LRS はバージョンヘッダに ”1.0” が設定されたリクエストをバージョンヘッダが ”1.0.0” であるとみなして受入れなければならない。
* LRS は"1.0.0" より前のバージョンヘッダが設定されたリクエストをヘッダ内に指定された以前のバージョンに完全に準拠した実装へ渡されない限りは拒否しなければならない。
* LRS は"1.1.0" もしくはそれ以上のバージョンヘッダが設定されたリクエストを拒否しなければならない。
* LRS は問題に関する短い説明を含んだ HTTP 400 エラーで応答することにより拒否しなければならない。

###### クライアントの必要条件:

* クライアントは全てのリクエストに "X-Experience-API-Version" ヘッダを含めなければならない。
* クライアントはこのヘッダに "1.0.1" を設定しなければならない。
* クライアントは"1.0.0" もしくはそれ以降のバージョンが設定されたレスポンスを受けとることを許容すべきである。
* クライアントは追加されたプロパティを含むデータ構造を受けとることを許容すべきである。
* クライアントはバージョン “1.0.0” 仕様で規定されていないプロパティはすべて無視すべきである。

###### 変換の必要条件:

* システムは、例えばバージョンの違いを取り扱うために新しいバージョンのステートメントを前のバージョン形式に変換してはならない。
* システムは、 <a href="#AppendixD">Appendix D：1.0.0へステートメントを変換</a> に記載された方法に従った場合のみ 古いバージョンのステートメントを新しいバージョン形式に変換してもよい。

<a name="concurrency"/></a>
### 6.3 同時実行

##### 説明
同時実行制御は API 利用者が LRS に古いデータに基づく変更を PUT または POST しないことを確実にする。

##### 詳細
xAPI は、 PUT または POST が既存のデータ実体を上書きする API の一部において、楽観的な同時実行制御を実装するために、 HTTP1.1 エンティティタグ（ [ETags](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.19) ）を使用する予定である。その部分は次の通り。

* State API
* Agent Profile API
* Activity Profile API

状態の矛盾がほとんど発生しないことから、 ステート API は同時実行ヘッダなしの PUT または POST リクエストを許容する。
以下の必要条件は、 エージェントプロファイル API とアクティビティプロファイル API にのみ適用される。

##### クライアントの必要条件

* Agent Profile API または Activity Profile API を使用するクライアントは [If-Match](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.24) ヘッダ、または [If-None-Match](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.26) ヘッダを含まなければならない。

##### LRS に対する必要条件

* LRS が GET リクエストに応答する際には、ETag HTTP ヘッダをレスポンスに追加しなければならない。（LRS ETag 形式を設定する理由は、 ETag ヘッダを読込めない API 利用者が自らその値を計算することを可能とするためである。）
* LRS が GET リクエストに応答する際には、このヘッダの値がコンテンツ部分の SHA-1 ダイジェストの 16 進数文字列となるように計算しなければならない。
* LRS が GET リクエストに応答する際には、ヘッダを引用符で囲わなければならない。

* LRS が PUT リクエストに応答する際には、RFC2616 (HTTP 1.1) にて説明されるとおり、 If-Match ヘッダが ETag を含む場合は、利用者が文書を最後に取り込んだあとに修正が行われたか検出するために [If-Match](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.24) ヘッダを取り扱わなければならない。
* LRS が PUT リクエストに応答する際には、RFC2616 （"*" を含む場合は HTTP1.1 ）で定める [If-None-Match](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.26) ヘッダを、利用者が気づかないリソース提供があるときに検出するために取り扱わなければならない。
* POST リクエストに返答する LRS は、ETag が含まれる場合、サービス利用者が先の取り込み時点からの変更を検出できるように、RFC2616, HTTP 1.1 に示される通り [If-Match](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.24) ヘッダを処理すべきである。

* POST リクエストに返答する LRS は、"*" が含まれる場合、サービス利用者が気付かないリソースが存在するかを検出するために、RFC2616, HTTP 1.1 に示される通り [If-None-Match](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.26) ヘッダを処理すべきである。

上記の PUT リクエストのいずれの場合もヘッダの前提条件に当てはまらない場合、 LRS は

* HTTP status 412 "Precondition Failed" を返さなければならない。
* リソースを変更させてはならない。

上記にあげた POST リクエストのヘッダの前提条件が満たされなかった場合、LRS は

* HTTP 412 "Precondition Failed" を返すべきである
* リソースに対して変更を加えるべきではない

PUT リクエストをいずれのヘッダもなく既存のリソースに対して受け取った場合は、 LRS は

* HTTP status 409 "Conflict" を返さなければならない。
* 利用者がすべきことを説明するテキスト形式の本文を返さなければならない。
    - リソースの現在の状態をチェックすべきである。
    - 競合を解消するために現在の ETag を設定した "If-Match" ヘッダをセットすべきである。
* リソースを変更してはならない。

<a name="security"/></a>

### 6.4 セキュリティ

###### 背景

相互運用性と異なる環境における様々なセキュリティの必要条件とのバランスを取るために、いくつかの認証オプションを定める。

###### 詳細

以下の表において、想定される認証のシナリオを示す。

**登録されたアプリケーション**とは、 LRS に既に登録された OAuth consumer として LRS に認証されているアプリケーションである。
**認識された利用者**とは LRS または LRS がユーザを定義することを委託しているシステム上のユーザアカウントである。

<table border="1">
<tr><th></th><th>認識された利用者</th><th>認識されていない利用者</th></tr>
<tr>
<td><アプリケーションが登録される場合</td>
<td>OAuth に対応する標準ワークフローが適用される。</td>
<td>LRS は付加的な利用者証明書を持たない xAPI アクセスを行うアプリケーションを信頼する。 OAuth トークンステップは呼び出されない。
</td>
</tr>
<tr>
<td>アプリケーションが登録されていない場合</td>
<td>アプリケーションエージェントは登録されたエージェントとして識別されないので、 LRS はその識別を前提とすることはできない。</td>
<td></br></td>
</tr>
<tr>
<td>アプリケーションがない場合</td>
<td>アプリケーションが呼び出されないため、 HTTP 基本認証が OAuth の代わりに利用される。</td>
<td></br></td>
</tr>
<tr>
<td>認証なしの場合</td>
<td align="center"colspan="2">テストを目的とする場合などで LRS によりサポートされてもよい。</td>

</tr>

</table>

###### 必要条件

LRS は次の手段のうち少なくとも一つを使用した認証をサポートしなければならない。

- [OAuth 1.0  (RFC 5849 ) ](http://tools.ieft.org/html/rfc5849) ( "HMAC-SHA1"、"RSA-SHA1" および "PLAIN TEXT" の署名方式を利用する）
- HTTP　基本認証
- Common Access Cards　（実装は今後のバージョンでフォローされ詳細化される）
- LRS はステートメントの有効性に関して判断するか委任するかを決め、使用された証明書に
基づいて、どのような処理を行うかを決定しなければならない。

<a name="authdefs"/></a>

#### 6.4.1 各シナリオのプロセス

##### 必要条件

* LRS はアプリケーションの名前と一意な consumer key （識別子）を記録しなければならない。
* LRS はこの登録を完了するためのメカニズムを提供するか、同様のメカニズムを提供する別システムに委譲しなければならない。
* LRS は xAPI へ完全に対応させるためには次のとおり設定できなければならない。
    * 下記のいずれかの手順によること。
    * 下記のいずれかのワークフローシナリオによること。
* LRS は（セキュリティ上の理由で）次のとおり対応してもよい。
    * 下記の手順のサブセットをサポートすること。
    * 認識された利用者または登録されたアプリケーションを制限すること。
* LRS は"HMACS-SHA1" および "RSA-SHA1" による署名を用いた OAuth を最低でも提供すべきである。

##### 登録されたアプリケーション＋認識された利用者のプロセスと必要条件

* 標準的な OAuth ワークフローを完了するために [6.4.2 OAuth 認証スコープ](#OAuthスコープ)章のエンドポイントを利用する。（ここでは細部に触れない）
* この認証形式がステートメントを記録する際に何も権限が指定されずに利用される場合は LRS は登録されたアプリケーションを表すエージェントと認識されたユーザを表すエージェントからなるグループとして権限を記録すべきである。

##### 登録されたアプリケーション＋認識されていない利用者のプロセスと必要条件

* LRS は登録されたアプリケーションの証明書と空のトークンとトークンシークレットで OAuth を使用して署名されたリクエストを受け取るだろう。
* もしこの認証形式がステートメントの記録の際に何も権限が指定されずに使用される場合は、 LRS は登録されたアプリケーションを表すエージェントとしての権限を記録すべきである。

##### 登録されていないアプリケーション＋認識された利用者のプロセスと必要条件

* 空白の consumer secret を利用すること。
* "Temporary Credential" リクエストを呼び出すこと。
* "consumer name" と他の一般的なパラメータを設定すること。そのため、利用者は "consumer name" と認証をリクエストしたアプリケーションの識別子が確認できないという警告を目にするだろう。
* OAuth がアプリケーションを指定するため、 LRS はアプリケーションと認証しているユーザの両方をグループとして含む権限を記録しなければならない。

##### アプリケーションがない＋認識された利用者のプロセスと必要条件

* LRS ログインに対応するユーザ名／パスワードの結合情報を用いること。
* 権限はログインにより識別されるエージェントとして記録される。但し、次の場合を除く。
    * 他の権限情報が指定される。かつ、
    * LRS はこの権限情報を指定する認識された利用者を信頼する。

##### 認証なしのプロセスと必要条件

* 明らかに認証されていないリクエストと　HTTP　基本認証チャレンジが提供されなければならないリクエストを区別するために、リクエストには空白のユーザ名とパスワードに基づく　HTTP　基本認証のためのヘッダを含めるべきである。

<a name="oauthscope"/></a>

#### 6.4.2 OAuth 認証スコープ

##### 説明
LRS と xAPI を利用して通信するアプリケーションが、間違った利用の可能性を最小限に
しつつアプリケーションの要求に応えるアクセスレベルを調整できるようにするためにスコ
ープに対する推奨を示す。それぞれのスコープの制限は、リクエストに関連するユーザア
カウントへの任意のセキュリティ制限に加わるものである。

##### 詳細

以下の表で xAPI スコープ値を一覧にする。
<table>
    <tr><th>スコープ</th><th>許可</th></tr>
    <tr><td>statements/write</td><td>任意のステートメントを書き込む</td></tr>
    <tr>
        <td>statements/read/mine</td>
        <td>"自分" が書いたステートメントを読込む、つまり、現在のトークンでステートメントを書くと仮定した場合に LRS が割り当てるであろう権限に一致した権限を所有していることに相当する。
        </td>
    </tr>
    <tr><td>statements/read</td><td>任意のステートメントを読込む</td>
    <tr>
        <td>state</td>
        <td>この関係を決定できる範囲で現在のトークンに関係するアクティビティとアクタに制限された状態データを読込む／書込む。
        </td>
    </tr>
    <tr>
        <td>define</td>
        <td>アクティビティとアクタを（再）定義する。もし認められないままステートメントを保存した場合、 ids が保存され LRS は調査を目的としたステートメントの原文を保存するかもしれないが、 アクタまたはアクティビティの内部表現で上書きすべきではない。
        </td>
    </tr>
    <tr>
        <td>profile</td>
        <td>この関係を決定できる範囲で現在のトークンに関係するアクティビティとアクタに制限されたプロファイルデータを読込む／書込む。
        </td>
    </tr>
    <tr><td>all/read</td><td>制限なしの読込みアクセス</td></tr>
    <tr><td>all</td><td>制限なしのアクセス</td></tr>
</table>

###### OAuth 拡張パラメータ
"consumer_name" や "scope" といったパラメータは OAuth1.0 に含まれないので
注意すること。そのためもし使われていた場合は OAuth ヘッダとしてではなくクエリ
文字列やフォームパラメータとみなして引き渡すべきである。


###### OAuth エンドポイント
<table>
    <tr>
        <th>名前</th>
        <th>エンドポイント</th>
        <th>例</th>
    </tr>
    <tr>
        <td>Temporary Credential リクエスト</td>
        <td>OAuth/initiate</td>
        <td>http://example.com/xAPI/OAuth/initiate</td>
    </tr>
    <tr>
        <td>Resource Owner 認可</td>
        <td>OAuth/authorize</td>
        <td>http://example.com/xAPI/OAuth/authorize</td>
    </tr>
    <tr>
        <td>トークンリクエスト</td>
        <td>OAuth/token</td>
        <td>http://example.com/xAPI/OAuth/token </td>
    </tr>
</table>

###### 例
スコープのリストは、リクエストされている許可の設定を決定する。例えば、インストラクタは
"statements/read" をレポートツールのために許可するかもしれない。しかし、 LRS はイン
ストラクタが LRS に対して直接認証をして問合せをすることによって読込めるステートメント
（たとえば自分の生徒に関するステートメント）のみにツールを制限することができる。

##### 必要条件

* LRS は[OAuth 2.0](http://tools.ietf.org/html/rfc6749#section-3.3) で定義されたスコープパラメータを受入れなければならない。
* LRS はもしスコープが指定されていない場合は "statements/write" と "statements/read/mine" のリクエストスコープと仮定しなければならない。
* LRS は最低限として "all" のスコープをサポートしなければならない。
* LRS はその他のスコープをサポートしてもよい。
* クライアントはリクエストが許可される機会を増やすために、最低限必要なスコープのみ要求すべきである。

<div style="page-break-after: always;"></div>
<a name="datatransfer"/></a>
## 7.0 Data Transfer (REST)
このセクションでは xAPI を構成する４つのサブ API （ステートメント、ステート、エージェント プロファイル、アクティビティ プロファイル）について説明する。4つのサブ API  は RESTful な HTTP メソッドによって処理される。ステートメント API は学習記録を追跡するために単独で利用することができる。

__注:__この仕様書中のエンドポイントの例では、"http://example.com/xAPI/" を LRS のベース
エンドポイントの例としている。その後、他のすべての IRI の構文は、使用される特定のエンドポ
イントを示す。

###### 必要条件

* LRS はこれらの API に対する、本仕様書が想定する文脈において認識できないパラメータを持つあらゆるリクエストに対して、 "HTTP 400 Bad Request" ステータスで拒絶しなければならない。（__注釈：__：LRS はこの仕様書に記載のないパラメータを認識して、動作する可能性がある）
* LRS はこれらの API に対する、「本仕様中にはあるが大文字小文字が一致していない」あらゆるリクエストに対して、 "HTTP 400 Bad Request" ステータスで拒絶しなければならない。
* 一連のステートメント中のいずれかのステートメントが拒絶された場合、 LRS はその一連のステートメントを拒絶しなければならない。

<a name="errorcodes" /></a>
### 7.1 エラーコード

###### 説明

以下のリストは API の様々なメソッドから返される HTTP エラーコードに関する一般的なガイドである。LRS はエラーの状況に最も合致するエラーコードを返さなければならない。また LRS はエラーの原因を説明するメッセージを返すべきである。

###### 詳細

* ```400 Bad Request``` - 引数が無効もしくは欠落していることを起因とするエラー状態を表す。「引数が無効」とは、不正な JSON または無効なオブジェクト構造を含む。

* ```401 Unauthorized``` - 認証が必要、もしくはリクエスト中の認証資格情報が拒否されたことを表す。

* ```403 Forbidden``` - 与えられた認証資格情報ではリクエストを拒否されたことを表す。
認証資格情報自体の拒否とは異なるので注意すること。このケースでは、認証資格情報
は確認されたものの、認証されたクライアントでは指定されたアクションを実行することが許可されなかったことを表す。

* ```404 Not Found``` - 要求されたリソースが見つからなかったことを表す。その例としては特定の文書を対象とする ステート、エージェントプロファイル、アクティビティプロファイル API callや、単一のステートメントを返すメソッドなどが挙げられる。

* ```409 Conflict``` - ステート API やエージェントプロファイル API 、アクティビティプロファイル API、もしくはステートメント PUT または POST 呼び出しの際に発生する、リソースの現在の状態との競合を起因とするエラー状態を表す。詳細は[6.3 同時実行](#concurrency) を参照のこと。

* ```412 Precondition Failed``` - State API や Agent Profile API 、Activity Profile API呼び出しの際に発生する、リクエストともにポストされた前提条件の失敗に起因するエラーを表す。詳細は[6.3 同時実行](#concurrency)を参照のこと。

* ```413 Request Entity Too Large``` - LRS が許容するサイズを超過していることを理由に、LRS がステートメントもしくはドキュメントを拒否したことを表す。LRS はサイズの制限値を自由に設定できる。また LRS は任意の条件ごと（例：権限単位）にこの制限値を変更してもよい。ただしステートメントについてはあらゆるサイズのものを受け入れるよう設定できなければならない。

* ```500 Internal Server Error``` - サーバ上に予期しない例外処理が発生した場合など、一般的なエラー状態を表す。

###### 必要条件

* LRS は上記リスト中のエラーの状態に対する最も適切なエラーコードを返さなければならない。

* LRS はレスポンス中において、エラーの原因を説明するメッセージを返すべきである。

<a name="stmtapi"/></a>

### 7.2 ステートメント API

###### 説明

Experience API の基本的な通信手段である。

<a name="stmtapiput"/></a>
####7.2.1 PUT　ステートメント

###### 詳細

エンドポイントの例: ```http://example.com/xAPI/statements```

与えられた id でステートメントを格納する。

戻り値: ```204 No Content```

<table>
	<tr><th>パラメータ</th><th>タイプ</th><th>デフォルト値</th><th>説明</th><th>必須</th></tr>
	<tr><td>statementId</td><td>String</td><td> </td><td>記録するためのステートメント id</td><td>必須</td></tr>
</table>

###### 必要条件

* 既にステートメントの割り当てられているステートメント ID をもったステートメントを受信した場合でも、LRS はその状態にいかなる変更も行ってはならない。```409 Conflict```もしくは```204 No Conent```で応答するかにかかわらず、ステートメントもしくはその他のあらゆるオブジェクトを変更してはならない。
* もし LRS が受信したステートメントの ID がすでに LRS に存在していれば、受信したステートメントが既存のものと合致するか検証し、合致しない場合には ```409 Conflict``` を返すべきである。
* LRS は格納されたステートメントが検索可能となる前に応答してもよい。

<a name="stmtapipost"/></a>
####7.2.2 POST ステートメント

###### 詳細

エンドポイントの例: ```http://example.com/xAPI/statements```

ステートメントもしくはステートメント群を格納する。PUT メソッドは特定のステートメント id
 をターゲットにするので、複数のステートメントを保存する場合や、ステートメント ID  を
最初に生成せずに単一のステートメントを保存する場合には PUT ではなく POST を使用
しなければならない。大量のステートメント群を生成するシステムのための代替策は AP
上の API の LRS 側を提供することである。そして定期的にステートメント群を更新（もしく
は新規）するよう LRS からその API を照会する。これは大量のデータを LRS に提供する
ようなシステムにおいてのみ現実的なオプションといえる。

戻り値: ```200 OK```, ステートメント id(s) の配列 (UUID).

###### 必要条件

既にステートメントの割り当てられているステートメント ID をもったステートメントを受信した
場合でも、LRS はその状態にいかなる変更も行ってはならない。```409 Conflict```もしくは
```200 OK```で応答するかにかかわらず、ステートメントもしくはその他のあらゆる
オブジェクトを変更してはならない。

もし LRS が受信したステートメントの ID がすでに LRS に存在していれば、受信したステー
トメントが既存のものと合致するか検証し、合致しない場合には ```409 Conflict``` を返すべ
きである。

LRS は格納されたステートメントが検索可能となる前に応答してもよい。

* GET ステートメントは、必要に応じ、クエリーストリングスとしてフォームフィールドをもつ POST としても呼べるが制約がある。詳細は、[7.8 クロスオリジンリクエスト] (#78-cross-origin-requests) を参照のこと。

* LRSは、POST が、ステートメントの追加か、複数ステートメントのリストのどちらであるかを引き渡すパラメータによって弁別可能にしなければならない。詳細は、[7.8 クロスオリジンリクエスト] (#78-cross-origin-requests) を参照のこと。


<a name="stmtapiget"/></a>
###### 7.2.3 GET ステートメント

###### 詳細

エンドポイントの例: ```http://example.com/xAPI/statements```

このメソッドは単一のステートメントもしくは複数のステートメントを取得するために呼び出
すことができる。ステートメント ID もしくは voidedStatement id がパラメータとして指定され
ている場合には、単一のステートメントが戻り値として返される。

それ以外の戻り値：権限と最大リスト長の制約の中で、"stored" 時間の新しい順に並べた
ステートメントのリストである [ステートメントの結果](#retstmts) オブジェクト。追加の結果
が利用可能な場合には、それらを取得するための IRL　は　StatementResult　オブジェクト
に含まれる。

戻り値: ```200 OK```, ステートメントもしくは[ステートメントの結果](#retstmts) (詳細は[4.2](#retstmts)参照)

<table>
    <tr><th>パラメータ</th><th>タイプ</th><th>デフォルト値</th><th>説明</th><th>必須</th></tr>
    <tr><td>statementId</td><td>String</td><td> </td><td>取得するためのステートメントの ID</td><td>任意</td></tr>
    <tr><td>voidedStatementId</td><td>String</td><td> </td><td>取得するための無効なステートメントの ID。詳細は <a href="#voidedStatements">VoidedStatement</a> を参照。</td><td>任意</td></tr>
    <tr><td>agent</td><td>Agent or Identified Group Object (JSON)</td><td> </td>
        <td>指定されたエージェントやグループが、ステートメントのアクタやオブジェクトであるステートメントのみをフィルタして返す。
            <ul><li>各オブジェクトで同じ逆機能識別子が利用され、それらの逆機能識別子が等しい値を持つ場合、エージェントもしくは識別されたグループは等しい。
            </li><li>このフィルタの目的のために、上記逆機能識別子に基づいて同一であるとみなされた特定のエージェントと一致するメンバを持つグループは等しいとみなされる。</li></ul>
            <br><br>詳細は<a href="#actor">エージェント/グループオブジェクトの定義</a>参照。
        </td><td>任意</td>
    </tr>
    <tr><td>verb</td><td>Verb id (IRI)</td><td> </td>
        <td>フィルタし、特定の verb id とマッチしたステートメントのみを返す。</td><td>任意</td>
    </tr>
    <tr><td>activity</td><td>Activity id (IRI)</td><td> </td>
        <td>フィルタし、指定された id をもつアクティビティをオブジェクトとするステートメントのみを返す。
        </td><td>任意</td>
    </tr>
    <tr><td>registration</td><td>UUID</td><td> </td>
        <td>フィルタし、指定した registration id に一致するステートメントを返す。あるアクティビティに割り当てられるあるアクタに対して、一意の登録 ID が割り当てられることが多いが、それを前提とすべきでないことに注意が必要である。特定のアクタもしくはアクティビティのためのステートメントのみが返されるべき場合には、それらのパラメータもあわせて指定すべきである。</td><td>任意</td>
    </tr>
    <tr>
        <td>related_activities</td>
        <td>Boolean</td>
        <td>false</td>
        <td>アクティビティ フィルタを広く適用する。オブジェクトや、あらゆる文脈のアクティビティ、もしくはパラメータ本来の正常な動作ではなく、アクティビティ パラメータにマッチするサブ ステートメントを含むプロパティをもつステートメントを含む。マッチングはアクティビティ パラメータと同様の方式で定義される。
        </td><td>任意</td>
    </tr>
    <tr>
        <td>related_agents</td>
        <td>Boolean</td>
        <td>false</td>
        <td>エージェント フィルタを広く適用する。パラメータ本来の正常な動作ではなく、エージェント パラメータにマッチするアクタやオブジェクト、権限、インストラクタ、チームもしくはそれらのあらゆるプロパティをもつプロパティを含む。マッチングはエージェント パラメータと同様の方式で定義される。
        </td><td>任意</td>
    </tr>
    <tr><td>since</td><td>Timestamp</td><td> </td>
        <td>指定された  timestamp よりあと（ timestamp の時刻は含まない）に記録されたステートメントのみを返す。</td><td>任意</td>
    </tr>
    <tr><td>until</td><td>Timestamp</td><td> </td>
        <td>指定された timestamp と同時またはそれ以前に記録されたステートメントのみを返す。</td><td>任意</td>
    </tr>
    <tr><td>limit</td><td>Nonnegative Integer</td><td>0</td>
        <td>返すステートメントの最大数。0 はサーバが許容する最大値を返すことを表す。</td><td>任意</td>
    </tr>
    <tr><td>format</td><td>String: ("ids", "exact", or "canonical")</td><td>exact</td>
        <td>「 ids 」の場合、エージェントやアクティビティ、そしてグループオブジェクトを識別するために最低限必要な情報のみを含む。匿名グループにおいては各メンバを識別するために必要な最低限の情報を意味する。「 exact 」の場合、ステートメントが受理された際と完全に同一なエージェントやアクティビティ、そしてグループオブジェクトを返す。LRS がこれらをインポートすることを目的としてステートメントを要求する場合には、「 exact 」フォーマットを用いるべきである。<br/><br/>
        「 canonical 」の場合、以下に定義する言語フィルタを適用し、オリジナルのエージェント オブジェクトを「 exact 」モードで返したのち、 LRS により判断され、正規の定義を含んだアクティビティ オブジェクトを返す。<br/><br/>

            <b>Canonical 言語プロセス:</b> アクティビティ オブジェクトは名前と説明のために Language Map オブジェクトを含む。これらのマップではひとつの言語のみが返されるべきである。<br/><br/>
                「 canonical 」のみのフォーマットの場合、ひとつの言語がそれぞれのマップに返されるべきである。最も関連性のある言語を選択するために、LRSは、 <a href="http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html">RFC 2616</a> (HTTP 1.1)で解説されている通り、Accept-Language ヘッダを適用する。ただし、全体としてリソース（ステートメントのリスト）に適用される場合ではなく、このロジックが各言語マップに個別に適用される場合はこの限りではない。
        </td><td>任意</td>
    </tr>
    <tr><td>attachments</td><td>Boolean</td><td>False</td>
        <td>trueの場合、LRS は以前に解説している通り、マルチパートレスポンスフォーマットを用いなければならず、あらゆる添付文書を含めなければならない。falseの場合には LRS はContent-Type application/json の形式で所定の応答を送信し、添付ファイルを使用することはできません。</td><td>任意</td>
    </tr>
    <tr>
        <td>ascending</td>
        <td>Boolean</td>
        <td>false</td>
        <td>true の場合、格納された時間の昇順で結果を返す。</td><td>任意</td>
    </tr>
</table>

###### 必要条件

* LRS はこれらリソースに対するリクエストに対してステートメント ID と voidedStatementId 両方のパラメータを含む場合、```HTTP 400```エラーで拒絶しなければならない。

* LRS はこれらリソースに対するリクエストに対してステートメント ID または voidedStatementId のパラメータを含み、また「 attachments 」もしくは「 format 」以外のパラメータを含む場合、```HTTP 400```エラーで拒絶しなければならない。。

* クエリフィルタ条件に合致するステートメントがない場合でも、LRS は ```HTTP 200``` および [StatementResult](#retstmts) オブジェクトを返さなければならない。この場合、statements プロパティは空の配列をもつ。

* LRS はステートメントリクエストに対するあらゆる応答に対して「 X-Experience-API-Consistent-Through 」ヘッダを <a href="https://en.wikipedia.org/wiki/ISO_8601#Combined_date_and_time_representations">ISO 8601 combined date and time</a> フォーマットを含まなければならない。その値は、指定されたタイプスタンプ以前の "stored" プロパティを持つ全てのステートメントが、妥当な確からしさで取り出し可能になっていることを示すタイムスタンプである。この時間は、ステートメントが検索可能となるまでの遅延をもたらす過剰負荷などの任意の一時的な状態を考慮すべきである。

* GET statementのattachmentプロパティが使用されており「 true 」の場合、LRSはマルチパートレスポンスフォーマットを使用し、<a href="#attachments">4.1.11</a>で説明されているようにすべてのattachmentsが含まれなければならない。

* GET statementのattachmentプロパティが使用されており「 false 」の場合、LRSはattachment raw dataを含めてはならず、application/jsonに報告しなければならない。

<a name="queryStatementRef" /></a>

###### StatementRefs のためのフィルタ条件

フィルタパラメータが時間やシーケンスベースでない場合（つまり since、until もしく
は limit 以外の場合）で、（ステートメントのオブジェクトとして StatementRef を使用
して）他のステートメントを参照する時、その参照先のステートメントが条件を満たす
場合は、参照元のステートメント自身も条件を満たす。時間やシーケンスベースのパ
ラメータはこの方法で StatementRef を行うステートメントに対しても適用する必要が
ある。このルールは再帰的に適用される。すなわち、ステートメント A が B を参照し、
B が C を参照している状況で、上に示すフィルタ条件がステートメント C に当てはま
るなら、ステートメント A もフィルタ対象となる。

たとえば、"ベンは爆発物のトレーニングに合格した"というステートメントと、"アンドリュー
は\<StatementRef to original Statement\>を確認した"というフォローアップのステー
トメントがあったとする。フォローアップステートメントでは、"ベン"にも"爆発物のトレー
ニング"にも触れていないが、アクタのフィルタで"ベン"またはアクティビティのフィルタ
で"爆発物のトレーニング"を指定してステートメントを取り出した場合、時間とシーケン
スの条件に合致している限り、両方のステートメントがマッチし返答される。

これらの条件はステートメントをステートメント ID や voidedStatementId で検索した
場合には適用されされない。

__注釈:__コンテキストのステートメント フィールドで用いられる StatementRefs は、ステート
メントのフィルタに対して影響を与えない。

<a name="voidedStatements" /></a>

###### 7.2.4 無効なステートメント

###### 必要条件

* LRS は voidedStatementId によりリクエストされたステートメントでない限り、無効となった
ステートメントを返してはならない。
* LRS は、 [StatementRefs によるフィルタ条件]
(#queryStatementRef) で示した通り、時間またはシーケンス基準による直接・間接の取り
出しの場合には、ステートメント自体が無効化されている場合を除き、無効化されたステー
トメントを参照しているステートメントも返さなければならない。これは、自分自身を無効化
することのできない、無効化ステートメントを含む。レポーティングツールは無効化ステー
トメントのターゲットを用いてあらゆる無効化ステートメントの存在とステートメント ID を識
別することができる。
* レポーティングツールは voidedStatementId を用いて個別に無効化
されたステートメントをリクエストすべきである。

<a name="docapis" /></a>

### 7.3 ドキュメント API

3つのドキュメント API はアクティビティプロバイダとエージェントのためにドキュメントストレー
ジを提供する。各 API の詳細は次のセクションで説明する。このセクションで説明する内容は
これら3つの API すべてに適用される。

###### 詳細
<table>
    <tr>
        <th>API</th>
        <th>メソッド</th>
        <th>エンドポイント</th>
        <th>例</th>
    </tr>
    <tr>
        <td>State API</td>
        <td>POST</td>
        <td>activities/state</td>
        <td>http://example.com/xAPI/activities/state</td>
    </tr>
    <tr>
        <td>Activity Profile API</td>
        <td>POST</td>
        <td>activities/profile</td>
        <td>http://example.com/xAPI/activities/profile</td>
    </tr>
    <tr>
        <td>Agent Profile API</td>
        <td>POST</td>
        <td>agent/profile</td>
        <td>http://example.com/xAPI/agents/profile</td>
    </tr>
</table>

###### 必要条件

* アクティビティプロバイダは、LRS が事前知識を持たないアクティビティとエージェントに関する文書を、いずれの文書 API に送ってもよい。
* LRS はアクティビティおよび/またはエージェントの予備知識を持っていないことを理由にしてドキュメントを拒絶してはならない。

###### JSON 手続きの必要条件
アクティビティプロバイダが、変数を JSON オブジェクトとして、コンテンツタイプが application/json のドキュメントに保存するならば、POST を利用して変数の組として、それらを扱うことができる。

以下のプロセスにより、プロセスとプロセスの必要条件順を追って検証する。
例えばドキュメントは次の情報を含むとする


```
{
	"x" : "foo",
	"y" : "bar"
}
```

LRS がコンテンツタイプが application/json の既存のドキュメントについて、POST リクエストをコンテンツタイプ application/json で受け取った場合、ポストされてきたドキュメントを既存ドキュメントにマージしなければならない。この文脈において「マージ」とは次のように定義する。
* 複数の文書に分割されたオブジェクトをデシリアライズする
* ポストされたオブジェクトに直接定義されたプロパティごとに、既存オブジェクトに対して対応するプロパティの値をセットする。
* リクエストの参考ドキュメントとして、既存オブジェクトの有効な json のシリアライズ性を格納します。

最上位階層のプロパティのみがマージされることに注意が必要である。たとえ最上位階層
のプロパティ（の値）がオブジェクトであっても、それぞれの元のプロパティの値すべてが、
新しいプロパティの値に完全に置き換えられる。

例えば、既に存在する上記ドキュメントを POST したものと同一 ID で、再度このドキュメン
トが POST された場合：

```
{
    "x" : "bash",
    "z" : "faz"
}
```

LRS に格納されるドキュメントの結果は次の通りとなる。

```
{
    "x" : "bash",
    "y" : "bar",
    "z" : "faz"
}
```

オリジナルのドキュメントが存在し、元のドキュメントもしくは post されてきたドキュメントのコンテンツタイプが application/json でない場合、あるいはどちらのドキュメントも JSON オブジェクトとして解析できない場合、LRS は HTTP のステータスコード ```400 Bad Request``` で応答しなければならず、リクエストに対してターゲットとするドキュメントをアップデートしてはならない。

元のドキュメントが存在しない場合、LRS は PUT リクエストと同様に取り扱い、POST
されてきたドキュメントを保存しなければならない。

マージが成功した場合、LRS は HTTP ステータスコード ```204 No Content``` で応答しなければならない。

AP がプロパティを削除する必要がある場合、後述するように PUT リクエストを用いてドキュメント全体を差し替えるべきである。

<a name="stateapi"/></a>

### 7.4 ステートAPI

##### 説明

一般に、これはアクティビティプロバイダが独自の内部記憶領域を持たない、あるい
は、複数の端末間で状態の共有が必要な場合などに利用されるスクラッチ領域であ
る。

##### 詳細

呼び出しの意味は stateId パラメータによって決められる。もし stateId パラメータが
含まれる場合、 GET と  DELETE メソッドは、 "stateId" によって指定される単独のス
テート文書に対して実行される。そうでない場合は、 GET は利用可能な ID を返し、
DELETE はその他のパラメータを通じて与えられた文脈の全てのステートを削除する。

###### 単一文書 (PUT | POST | GET | DELETE)

エンドポイント例: http://example.com/xAPI/activities/state

アクティビティ、エージェント、そして登録（存在すれば）からなる文脈に与えられた
stateId によって指定される文書を記録、変更、取り込み、または削除する。

戻り値: (PUT | POST | DELETE): ```204 No Content```<br>
戻り値: (GET): ```200 OK```, State Content

<table>
    <tr><th>パラメータ</th><th>タイプ</th><th>説明</th><th>必須</th></tr>
    <tr>
        <td>activityId</td>
        <td>Activity id (IRI)</td>
        <td>このステートと関連したアクティビティID</td>
        <td>必須</td>
    </tr>
    <tr><td>agent</td>
        <td>Agent object (JSON)</td>
        <td>このステートと関連したエージェント</td>
        <td>必須</td>
    </tr>
    <tr><td>registration</td><td>UUID</td>
        <td>このステートと関連した登録</td><td>任意</td>
    </tr>
    <tr><td>stateId</td><td>String</td>
        <td>与えられた文脈における、このステートのID</td><td>必須</td>
    </tr>
</table>

###### 複数文書の GET
エンドポイント例: http://example.com/xAPI/activities/state

この文脈（アクティビティ＋エージェント［指定された場合の登録］）における全てのステート
データのidを取り込む。 もし、 "since" パラメータが指定されている場合、指定された
 timestamp （その時刻を含まない）よりあとに記録または更新されたエントリのみに制
限される。

戻り値: ```200 OK```, Array of ids

<table>
    <tr><th>パラメータ</th><th>タイプ</th><th>説明</th><th>必須</th></tr>
    <tr>
        <td>activityId</td>
        <td>Activity id (IRI)</td>
        <td>これらのステートと関連したアクティビティ ID</td>
        <td>必須</td>
    </tr>
    <tr>
        <td>agent</td>
        <td>Agent object (JSON)</td>
        <td>これらのステートと関連したエージェント</td><td>必須</td>
    </tr>
    <tr><td>registration</td><td>UUID</td>
        <td>これらのステートと関連した登録</td><td>任意</td>
    </tr>
    <tr><td>since</td><td>Timestamp</td>
        <td>指定された timestamp（その時刻を含まない）よりあとに記録されたステート ID のみが返却される。
</td><td>任意</td>
    </tr>
</table>

###### 複数文書の DELETE
エンドポイント例: http://example.com/xAPI/activities/state

この文脈（アクティビティ＋エージェント［指定された場合は登録］）における全てのステ
ートデータを削除する。

戻り値: ```204 No Content```
<table>
    <tr><th>パラメータ</th><th>タイプ</th><th>説明</th><th>必須</th></tr>
    <tr>
        <td>activityId</td>
        <td>Activity id (IRI)</td>
        <td>このステートと関連したアクティビティ ID</td>
        <td>必須</td>
    </tr>
    <tr>
        <td>agent</td>
        <td>Agent object (JSON)</td>
        <td>このステートと関連したエージェント</td>
        <td>必須</td>
    </tr>
    <tr><td>registration</td><td>UUID</td>
        <td>このステートと関連した登録 ID</td><td>任意</td>
    </tr>
</table>

<a name="actprofapi"/></a>

### 7.5 アクティビティ プロファイル API

##### 説明

アクティビティ プロファイル API は、ステート API と似ているものであり、任意の
キー / 文書のペアをアクティビティに関連させて保存することを可能とする。

##### 詳細

呼び出しの意味は profileId パラメータによって決められる。含まれる場合は、GET
メソッドは、 "profileId" によって定義される単独の文書に従って実行される。
そうでない場合は、 GET は利用可能な id を返す。

アクティビティ プロファイル API もまた、 LRS からアクティビティの全ての説明を読み
だすメソッドを含んでいる。

###### 全アクティビティオブジェクトの GET

エンドポイント例: http://example.com/xAPI/activities

指定された全アクティビティオブジェクトをロードする。

戻り値: ```200 OK```, Content

<table>
    <tr><th>パラメータ</th><th>タイプ</th><th>説明</th><th>必須</th></tr>
    <tr>
        <td>activityId</td>
        <td>Activity id (IRI)</td>
        <td>ロードするアクティビティと関連したアクティビティ ID</td><td>必須</td>
    </td>
</table>

###### 単一文書の PUT | POST | GET | DELETE

エンドポイント例: http://example.com/xAPI/activities/profile

指定されたアクティビティの文脈で特定のプロファイル文書を記録、変更、取り込み、または削除する。

戻り値 (PUT | POST | DELETE): ```204 No Content```<br>
戻り値 (GET): ```200 OK```, Profile Content
<table>
    <tr><th>パラメータ</th><th>タイプ</th><th>説明</th><th>必須</th></tr>
    <tr>
        <td>activityId</td>
        <td>Activity id (IRI)</td>
        <td>このプロファイルと関連したアクティビティ ID</td><td>必須</td>
    </tr>
    <tr><td>profileId</td><td>String</td>
        <td>このプロファイルと関連したプロファイル ID</td><td>必須</td>
    </tr>
</table>

###### 複数文書の GET

エンドポイント例: http://example.com/xAPI/activities/profile

アクティビティのために全てのプロファイルエントリの id をロードする。 もし、 "since"
パラメータが指定されている場合、指定された timestamp （その時刻を含まない）よりあ
とに記録または更新されたエントリのみに制限される。

戻り値: ```200 OK```, List of ids
<table>
    <tr><th>パラメータ</th><th>タイプ</th><th>説明</th><th>必須</th><tr>
    <tr>
        <td>activityId</td>
        <td>Activity id (IRI)</td>
        <td>これらのプロファイルと関連したアクティビティ ID</td><td>必須</td>
    </tr>
    <tr><td>since</td><td>Timestamp</td>
        <td>指定された timestamp （その時刻を含まない）よりあとに記録されたプロファイル ID のみが返却される</td><td>任意</td>
    </tr>
</table>

<a name="agentprofapi"/></a>

### 7.6 エージェント プロファイル API

##### 解説

エージェントプロファイル API はステート API と似ているものであり、任意のキー / 文書
のペアをエージェントと関連させて保存することを可能とする。

##### 詳細

呼び出しの意味は stateId パラメータによって決められる。含まれる場合は、GET
メソッドは、 "profileId" によって定義される単独の文書に従って実行される。
そうでない場合は、 GET は利用可能な id を返す。

エージェントプロファイル API もまた、ディレクトリサービスなどの外部サービスから
派生したエージェントに関する結合情報と一体となった、特殊なオブジェクトを読みだ
すメソッドを含んでいる。

###### 複合情報の GET

##### 詳細
エンドポイント例: http://example.com/xAPI/agents

指定されたエージェントに対して特別の、Person オブジェクトを返却する。Person
オブジェクはエージェントオブジェクトと非常に似ているが、それぞれの要素が単一
の値を持つ代わりに、それそれの要素が配列の値を持ち、複数の識別プロパティを
含むことが許されている。ここで留意すべきは、パラメータが単一の識別子を持つ通常の
エージェントオブジェクトであり、配列ではないということである。これは FOAF の
person 概念とは異なることに注意してほしい。ここでは person は LRS エージェント
データの person 中心の観点を示す存在として使用されるのであり、しかし、エー
ジェントは、ただ一つのペルソナ（一つの文脈における person）を参照しているの
である。

##### 必要条件
* Person オブジェクトに複数の識別プロパティを返却する能力がある LRS は、明示的
にパーミッションを与えて、連結する資格情報が増加することを要求すべきである。
* LRS は 403 "Forbidden" で、権限の不十分なリクエストを拒絶すべきである。
* LRS がエージェントに関して返答すべき追加情報を持たない場合、照会時に Person
を返さなければならないが、Person オブジェクトはリクエストされたエージェントと
関連した情報のみを含む。

###### Person プロパティ

##### 詳細

<table>
    <tr><th>プロパティ</th><th>タイプ</th><th>説明</th><th>必須</th></tr>
    <tr>
        <td>objectType</td>
        <td>String</td>
        <td>"Person"</td>
        <td>必須</td>
    </tr>
    <tr>
        <td>name</td>
        <td>Array of strings.</td>
        <td>読み出されたエージェント名リスト</td>
        <td>必須</td>
    </tr>
    <tr>
        <td><a href="http://xmlns.com/foaf/spec/#term_mbox">mbox</a></td>
        <td>Array of IRIs in the form "mailto:email address".</td>
        <td>読み出されたエージェントのｅメールアドレス リスト</td>
        <td>任意</td>
    </tr>
    <tr>
        <td><a href="http://xmlns.com/foaf/spec/#term_mbox_sha1sum">mbox_sha1sum</a></td>
        <td>Array of strings.</td>
        <td>mailto IRIs (例えば mbox プロパティなど) の SHA1 ハッシュリスト</td>
        <td>任意</td>
    </tr>
    <tr>
        <td>openid*</td>
        <td>Array of strings.</td>
        <td>読み出されたエージェントを一意的に識別する openid リスト</td>
        <td>任意</td>
    </tr>
    <tr>
        <td>account*</td>
        <td>Array of account objects.</td>
        <td>適合するアカウントリスト。完全なアカウントオブジェクト（ホームページや名前）が提供されなければならない。</td>
        <td>任意</td>
    </tr>
</table>

参照:  Section 4.1.2.1 Agent.

戻り値: ```200 OK```, Person Object


<table>
    <tr><th>パラメータ</th><th>タイプ</th><th>説明</th><th>必須</th></tr>
    <tr>
        <td>agent</td>
        <td>Agent object (JSON)</td>
        <td>拡張されたエージェント情報を取り込む際に使用するエージェント表現</td><td>必須</td>
    </tr>
</table>

##### 必要条件

全ての配列プロパティは、Agent Object の類似して名付けられたプロパティと
同じ定義によって設定されなければならない。

###### 単一 Agent または Profile の PUT | POST | GET | DELETE

エンドポイント例: http://example.com/xAPI/agents/profile

指定されたエージェントの文脈で特定のプロファイル文書を記録、変更、取り込み、または削除する。

戻り値 (PUT | POST | DELETE): ```204 No Content```
戻り値 (GET): ```200 OK```, Profile Content

<table>
    <tr><th>パラメータ</th><th>タイプ</th><th>説明</th><th>必須</th></tr>
    <tr>
        <td>agent</td>
        <td>Agent object (JSON)</td>
        <td>このプロファイルと関連したエージェント</td><td>必須</td>
    </tr>
    <tr><td>profileId</td><td>String</td>
        <td>このプロファイルと関連したプロファイル ID</td><td>必須</td>
    </tr>
</table>

###### 複数 Agent または Profile の GET
エンドポイント例: http://example.com/xAPI/agents/profile

エージェントのために全てのプロファイルエントリの ID をロードする。 "since" パラメータ
が指定されている場合、指定された timestamp （その時刻を含まない）よりあとに記録ま
たは更新されたエントリのみに制限される。

戻り値: ```200 OK```, List of IDs

<table>
    <tr><th>パラメータ</th><th>タイプ</th><th>説明</th><th>必須</th></tr>
    <tr>
        <td>agent</td>
        <td>Agent object (JSON)</td>
        <td>このプロファイルと関連したエージェント</td><td>必須</td>
    </tr>
    <tr><td>since</td><td>Timestamp</td>
        <td>指定された timestamp（その時刻を含まない）よりあとに記録されたプロファイル ID のみが返却される。</td><td>任意</td>
    </tr>
</table>

<a name="aboutresource"/></a>

### 7.7 About リソース

###### 説明
この LRS に関する情報（サポートする xAPI のバージョンを含む）を返答する。

###### 背景
主に、このリソースは、複数の xAPI バージョンをサポートするクライアントに、 LRS と
の通信時にどのバージョンを使用するのかを決定させるために存在する。 拡張機能は
他の用途が現れることを見越して含まれている。

###### 詳細

##### 情報の GET

エンドポイントの例：http://example.com/xAPI/about

戻り値: ```200 OK```,Single 'about' JSON document.
<table border="1">
<tr><th>プロパティ</th><th>タイプ</th><th>説明</th><td>必須</td></tr>
<td>version</td><td>array of version strings</td><td>この LRS がサポートする xAPI バージョン</td>
<td>必須</td>
</tr>
<tr>
<td>Extensions</td><td><a href="#miscext">Object</a></td><td>必要に応じた他のプロパティのマップ</td><td>任意</td>
</tr>
</table>

###### 必要条件
* LRS は各々のメジャーバージョンに対して、その LRS が準拠する最新のマイナーおよびパッチ
バージョンを示すバージョンプロパティを含んだ、上述した JSON 文書を戻さなければならない。
    * この仕様書のバージョン 1.0.0 では、 "1.0.0" が含まれなければならないことを意味する。
"0.9" や "0.95" は含まれてもよい。（この要件の目的ため、 "0.9" や "0.95" はメジャーバージョン
と考えられている。）
* LRS はこのリソースへの認証されていないアクセスを許可すべきである。
* LRS は <a href="#apiversioning">6.2 API Versioning </a>によって必要とされない限り、
バージョンヘッダーに基づいてリクエストを拒絶してはならない。

<a name="cors"/></a>

### 7.8 クロス オリジン リクエスト

##### 説明

xAPI のゴールの一つは、クロスドメイントラッキングを許可することであり、 xAPI がブラ
ウザ以外のアプリケーションからトラッキングができるようにしようとしていても、ブラウザ
はサポートされる必要がある。 Internet Explorer 8 と 9 は、クロスオリジンリソースシェア
リングを実装しておらず、自身のクロスドメインリクエスト API を利用する。 "GET" と
"POST" をサポートしているのみで、 HTTP ヘッダーへのセットを許可されていないため、
上述した xAPI の全てを利用することはできない。

##### 詳細/必要条件

上記の制限により特定の呼び出しのための通常の構文を使用できないときにのみ利用側
が使用すべき別の構文について、以下に述べる。

__メソッド__: 発行された全 xAPI リクエストは POST されなければならない。対象とする
xAPI メソッドはリクエスト上の唯一の問合せ文字列パラメータとして含まれなければならない。
（例: http://example.com/xAPI/statements?method=PUT）

__ヘッダー__: HTTP ヘッダーに記述すべき必須のパラメータは、同名の form パラメータ
として与えなければならない。

__コンテンツ__: xAPI の呼び出しがコンテンツの送信を伴う場合、 "content" と呼ばれる
フォームパラメータとしてコンテンツはエンコードされ、含まれなければならない。LRS は
UTF-8 文字列としてこのコンテンツを解釈する。バイナリデータの記録は、この構文でサ
ポートされない。

__添付文書__:添付文書データの送信は、multipart/mixed リクエストを送信する必要があり、
それゆえ添付データの送信はこの構文でサポートされない。 4.1.11. Attachments を参照。

・LRS は上記の文法を実装しなければならない。

Internet Explorer 10 より低いバージョンが、HTTP と HTTPS 間でクロスドメインリクエスト
をサポートしていないことに留意すべきである。これは IE9 とそれ以下を意味しており、 LRS
が HTTPS ドメイン上にある場合、ステートメントを送信するクライアントも HTTPS 上になけ
ればならない。 LRS が HTTP 上にある場合は，クライアントも HTTP 上になければならない。

クライアントアクティビティプロバイダにとって、クライアントコードが LRS とは異なるスキー
ム（HTTP or HTTPS）上でホストされている IE8 と IE9 をサポートすることが要求されるケー
スがある。これらのケースにおいて、プロキシは LRS と通信するために必要とされる。
二つの簡単な解決策として:

1）   クライアントコードから LRS へ同じスキームのプロキシパススルーを構成する。あるいは、
2）   ターゲット LRS へのステートメント経路をクライアントコードと同じスキームとした、仲介
サーバーサイド LRS をホストする

* このユースケースをサポートするために、LRS は HTTP と HTTPS エンドポイントの両方を
提供してもよい。
* LRS とクライアントは、このスキームの利用を決定する前に、セキュリティリスクを考慮す
べきである。

<a name="validation"/></a>

### 7.9 バリデーション

##### 説明

xAPI 内での LRS の機能はステートメントを記録したり読み出したりすることである。
これらのタスクを実行するための十分な情報がある場合には、その実行が期待される。
Experience API でのステートメントのバリデーションは、構文に対してのみ行われ、
意味の判断は行わない。動詞の定義、アクティビティタイプ、そして拡張機能の組み合わ
せで有効な意味を保証するようなルールを強制するのは、ステートメントを送信するアク
ティビティプロバイダの責任である。

##### 必要条件

・LRS は構造に関するルールを強制すべきである
・LRS は意味に関するルールを強制すべきではない


<a name="httphead"/></a>

### 7.10 HTTP HEAD

###### 説明
LRS は、実際のドキュメントを使用せず、 HTTP ヘッダーを使用してメタ情報を返却するこ
とだけで HEAD リクエストに応答する。

###### 背景

LRS にアクセスするクライアントは、特定のステートメントが存在する場合にチェックを必要
とし、ステート、アクティビティ、エージェントプロファイルのドキュメント修正日を決定すること
ができる。特に大規模なドキュメントでは、ドキュメント修正日を確認する際、全体ドキュメン
トを取得しないため、より効率的である。

###### LRS 必要条件

* LRS は（下記を）除外して、他の同一の HTTP GET リクエストに対する応答と同じように、どの HTTP HEAD リクエストにも応答しなければならない。<br>
    *メッセージボディは、省略しなければならない。<br>
    *LRS リソースの浪費を避けるために、 Content-Length ヘッダーは省略される。


<div style="page-break-after: always;"></div>
<a name="AppendixA"/></a>
## Appendix A: ステートメント例

簡単なステートメント例（改行は表示目的）

```
{
    "id":"fd41c918-b88b-4b20-a0a5-a4c32391aaa0",
    "actor":{
        "objectType": "Agent",
        "name":"Project Tin Can API",
        "mbox":"mailto:user@example.com"
    },
    "verb":{
        "id":"http://adlnet.gov/expapi/verbs/created",
        "display":{
            "en-US":"created"
        }
    },
    "object":{
        "id":"http://example.adlnet.gov/xapi/example/simplestatement",
        "definition":{
            "name":{
                "en-US":"simple statement"
            },
            "description":{
                "en-US":"A simple Experience API statement. Note that the LRS
                does not need to have any prior information about the Actor (learner), the
                verb, or the Activity/object."
            }
        }
    }
}
```
Verbの「 attempted 」を用いた一般的で簡単な完了

```
{
    "actor":{
        "objectType": "Agent",
        "name":"Example Learner",
        "mbox":"mailto:example.learner@adlnet.gov"
    },
    "verb":{
        "id":"http://adlnet.gov/expapi/verbs/attempted",
        "display":{
            "en-US":"attempted"
        }
    },
    "object":{
        "id":"http://example.adlnet.gov/xapi/example/simpleCBT",
        "definition":{
            "name":{
                "en-US":"simple CBT course"
            },
            "description":{
                "en-US":"A fictitious example CBT course."
            }
        }
    },
    "result":{
        "score":{
            "scaled":0.95
        },
        "success":true,
        "completion":true
    }
}
```

利用できる大部分のプロパティを紹介している長いステートメント例。この例は、ステートメントが権限を含んでLRSによって戻され、LRSが設定したプロパティが記録されることを示す。

```
{
    "id": "6690e6c9-3ef0-4ed3-8b37-7f3964730bee",
    "actor": {
        "name": "Team PB",
        "mbox": "mailto:teampb@example.com",
        "member": [
            {
                "name": "Andrew Downes",
                "account": {
                    "homePage": "http://www.example.com",
                    "name": "13936749"
                },
                "objectType": "Agent"
            },
            {
                "name": "Toby Nichols",
                "openid": "http://toby.openid.example.org/",
                "objectType": "Agent"
            },
            {
                "name": "Ena Hills",
                "mbox_sha1sum": "ebd31e95054c018b10727ccffd2ef2ec3a016ee9",
                "objectType": "Agent"
            }
        ],
        "objectType": "Group"
    },
    "verb": {
        "id": "http://adlnet.gov/expapi/verbs/attended",
        "display": {
            "en-GB": "attended",
            "en-US": "attended"
        }
    },
    "result": {
        "extensions": {
            "http://example.com/profiles/meetings/resultextensions/minuteslocation": "X:\\meetings\\minutes\\examplemeeting.one"
        },
        "success": true,
        "completion": true,
        "response": "We agreed on some example actions.",
        "duration": "PT1H0M0S"
    },
    "context": {
        "registration": "ec531277-b57b-4c15-8d91-d292c5b2b8f7",
        "contextActivities": {
            "parent": [
                {
                    "id": "http://www.example.com/meetings/series/267",
                    "objectType": "Activity"
                }
            ],
            "category": [
                {
                    "id": "http://www.example.com/meetings/categories/teammeeting",
                    "objectType": "Activity",
                    "definition": {
                        "name": {
                            "en": "team meeting"
                        },
                        "description": {
                            "en": "A category of meeting used for regular team meetings."
                        },
                        "type": "http://example.com/expapi/activities/meetingcategory"
                    }
                }
            ],
            "other": [
                {
                    "id": "http://www.example.com/meetings/occurances/34257",
                    "objectType": "Activity"
                },
                {
                    "id": "http://www.example.com/meetings/occurances/3425567",
                    "objectType": "Activity"
                }
            ]
        },
        "instructor" :
        {
            "name": "Andrew Downes",
            "account": {
                "homePage": "http://www.example.com",
                "name": "13936749"
            },
            "objectType": "Agent"
        },
        "team":
        {
            "name": "Team PB",
            "mbox": "mailto:teampb@example.com",
            "objectType": "Group"
        },
        "platform" : "Example virtual meeting software",
        "language" : "tlh",
        "statement" : {
            "objectType":"StatementRef",
            "id" :"6690e6c9-3ef0-4ed3-8b37-7f3964730bee"
        }

    },
    "timestamp": "2013-05-18T05:32:34.804Z",
    "stored": "2013-05-18T05:32:34.804Z",
    "authority": {
        "account": {
            "homePage": "http://cloud.scorm.com/",
            "name": "anonymous"
        },
        "objectType": "Agent"
    },
    "version": "1.0.0",
    "object": {
        "id": "http://www.example.com/meetings/occurances/34534",
        "definition": {
            "extensions": {
                "http://example.com/profiles/meetings/activitydefinitionextensions/room": {"name": "Kilby", "id" : "http://example.com/rooms/342"}
            },
            "name": {
                "en-GB": "example meeting",
                "en-US": "example meeting"
            },
            "description": {
                "en-GB": "An example meeting that happened on a specific occasion with certain people present.",
                "en-US": "An example meeting that happened on a specific occasion with certain people present."
            },
            "type": "http://adlnet.gov/expapi/activities/meeting",
            "moreInfo": "http://virtualmeeting.example.com/345256"
        },
        "objectType": "Activity"
    }
}
```


<div style="page-break-after: always;"></div>
<a name="AppendixB"/></a>
## Appendix B: 違うタイプのステートメントオブジェクトの例

ステートメントのオブジェクトは、アクティビティ、グループ、ステートメントになることができる。
この付録は、それぞれの例を示す。

###### Activity アクティビティ
```
{
    "id": "http://www.example.co.uk/exampleactivity",
    "definition": {
        "name": {
            "en-GB": "example activity",
            "en-US": "example activity"
        },
        "description": {
            "en-GB": "An example of an activity",
            "en-US": "An example of an activity"
        },
        "type": "http://www.example.co.uk/types/exampleactivitytype"
    },
    "objectType": "Activity"
}
```

###### Agent エージェント
```
{
    "name": "Andrew Downes",
    "mbox": "mailto:andrew@example.co.uk",
    "objectType": "Agent"
}
```

###### Group グループ

この例は、メンバーを含む指名グループを示す。
```
{
    "name": "Example Group",
    "account" : {
        "homePage" : "http://example.com/homePage",
        "name" : "GroupAccount"
    },
    "objectType": "Group",
    "member": [
            {
                "name": "Andrew Downes",
                "mbox": "mailto:andrew@example.com",
                "objectType": "Agent"
            },
            {
                "name": "Aaron Silvers",
                "openid": "http://aaron.openid.example.org",
                "objectType": "Agent"
            }
        ]
}
```


###### Statement ステートメント

この例は、オブジェクトがステートメントリファレンスであるサブステートメントを示す。
```
{
        "objectType": "SubStatement",
        "actor" : {
            "objectType": "Agent",
            "mbox":"mailto:agent@example.com"
        },
        "verb" : {
            "id":"http://example.com/confirmed",
            "display":{
                "en":"confirmed"
            }
        },
        "object": {
            "objectType":"StatementRef",
            "id" :"9e13cefd-53d3-4eac-b5ed-2cf6693903bb"
        }
    }
```


<div style="page-break-after: always;"></div>
<a name="AppendixC"/></a>

## Appendix C: アクティビティタイプ「 cmi.interaction 」のための定義例

###### true-false true/false

```
"definition": {
    "description": {
        "en-US": "Does the xAPI include the concept of statements?"
    },
    "type": "http://adlnet.gov/expapi/activities/cmi.interaction",
    "interactionType": "true-false",
    "correctResponsesPattern": [
        "true"
    ]
}
```

###### choice 選択
```
"definition": {
    "description": {
        "en-US": "Which of these prototypes are available at the beta site?"
    },
    "type": "http://adlnet.gov/expapi/activities/cmi.interaction",
    "interactionType": "choice",
    "correctResponsesPattern": [
        "golf[,]tetris"
    ],
    "choices": [
        {
            "id": "golf",
            "description": {
                "en-US": "Golf Example"
            }
        },
        {
            "id": "facebook",
            "description": {
                "en-US": "Facebook App"
            }
        },
        {
            "id": "tetris",
            "description": {
                "en-US": "Tetris Example"
            }
        },
        {
            "id": "scrabble",
            "description": {
                "en-US": "Scrabble Example"
            }
        }
    ]
}
```

###### fill-in
```
"definition": {
    "description": {
        "en-US": "Ben is often heard saying: "
    },
    "type": "http://adlnet.gov/expapi/activities/cmi.interaction",
    "interactionType": "fill-in",
    "correctResponsesPattern": [
        "Bob's your uncle"
    ]
}
```

###### long-fill-in
```
"definition": {
    "description": {
        "en-US": "What is the purpose of the xAPI?"
    },
    "type": "http://adlnet.gov/expapi/activities/cmi.interaction",
    "interactionType": "long-fill-in",
    "correctResponsesPattern": [
        "{case_matters=false}{lang=en}To store and provide access to learning experiences."
    ]
}
```

###### likert
```
"definition": {
    "description": {
        "en-US": "How awesome is Experience API?"
    },
    "type": "http://adlnet.gov/expapi/activities/cmi.interaction",
    "interactionType": "likert",
    "correctResponsesPattern": [
        "likert_3"
    ],
    "scale": [
        {
            "id": "likert_0",
            "description": {
                "en-US": "It's OK"
            }
        },
        {
            "id": "likert_1",
            "description": {
                "en-US": "It's Pretty Cool"
            }
        },
        {
            "id": "likert_2",
            "description": {
                "en-US": "It's Damn Cool"
            }
        },
        {
            "id": "likert_3",
            "description": {
                "en-US": "It's Gonna Change the World"
            }
        }
    ]
}
```

###### matching
```
"definition": {
    "description": {
        "en-US": "Match these people to their kickball team:"
    },
    "type": "http://adlnet.gov/expapi/activities/cmi.interaction",
    "interactionType": "matching",
    "correctResponsesPattern": [
        "ben[.]3[,]chris[.]2[,]troy[.]4[,]freddie[.]1"
    ],
    "source": [
        {
            "id": "ben",
            "description": {
                "en-US": "Ben"
            }
        },
        {
            "id": "chris",
            "description": {
                "en-US": "Chris"
            }
        },
        {
            "id": "troy",
            "description": {
                "en-US": "Troy"
            }
        },
        {
            "id": "freddie",
            "description": {
                "en-US": "Freddie"
            }
        }
    ],
    "target": [
        {
            "id": "1",
            "description": {
                "en-US": "Swift Kick in the Grass"
            }
        },
        {
            "id": "2",
            "description": {
                "en-US": "We got Runs"
            }
        },
        {
            "id": "3",
            "description": {
                "en-US": "Duck"
            }
        },
        {
            "id": "4",
            "description": {
                "en-US": "Van Delay Industries"
            }
        }
    ]
}
```

###### performance
```
"definition": {
    "description": {
        "en-US": "This interaction measures performance over a day of RS sports:"
    },
    "type": "http://adlnet.gov/expapi/activities/cmi.interaction",
    "interactionType": "performance",
    "correctResponsesPattern": [
        "pong[.]1:[,]dg[.]:10[,]lunch[.]"
    ],
    "steps": [
        {
            "id": "pong",
            "description": {
                "en-US": "Net pong matches won"
            }
        },
        {
            "id": "dg",
            "description": {
                "en-US": "Strokes over par in disc golf at Liberty"
                }
            },
        {
            "id": "lunch",
            "description": {
                "en-US": "Lunch having been eaten"
            }
        }
    ]
}
```

###### sequencing
```
"definition": {
    "description": {
        "en-US": "Order players by their pong ladder position:"
    },
    "type": "http://adlnet.gov/expapi/activities/cmi.interaction",
    "interactionType": "sequencing",
    "correctResponsesPattern": [
        "tim[,]mike[,]ells[,]ben"
    ],
    "choices": [
        {
            "id": "tim",
            "description": {
                "en-US": "Tim"
            }
        },
        {
            "id": "ben", "description": {
                "en-US": "Ben"
            }
        },
        {
            "id": "ells",
            "description": {
                "en-US": "Ells"
            }
        },
        {
            "id": "mike",
            "description": {
                "en-US": "Mike"
            }
        }
    ]
}
```

###### numeric
```
"definition": {
    "description": {
        "en-US": "How many jokes is Chris the butt of each day?"
    },
    "type": "http://adlnet.gov/expapi/activities/cmi.interaction",
    "interactionType": "numeric",
    "correctResponsesPattern": [
        "4:"
    ]
}
```

###### other
```
"definition": {
    "description": {
        "en-US": "On this map, please mark Franklin, TN"
    },
    "type": "http://adlnet.gov/expapi/activities/cmi.interaction",
    "interactionType": "other",
    "correctResponsesPattern": [
        "(35.937432,-86.868896)"
    ]
}
```


<div style="page-break-after: always;"></div>
<a name="AppendixD"/></a>

## Appendix D: 1.0.0へステートメントを変換

###### 背景

これは、1.0.0の仕様であり、実装者が、従来のバージョンの仕様を考慮する必要がないように努めた。しかしながら、従来のバージョンは、注目に値する普及を示した。このデータコンバージョンは、旧バージョンを用いて記録されたデータを継続して活用でき、新しい実装者も同様の方式で利用できることを目指して作成した。

######Details 詳細

######バージョン0.9を元に作られたステートメントのコンバージョン

0.9から作成されたステートメントを変換する1.0.0システムは以下のステップに沿っていなければならない。

* ステートメントが無効化された、または 0.9 版の仕様に含まれない動詞、アクティビティタイプまたはプロパティである場合は、変換をしない。
* Verb に http://adlnet.gov/expapi/verbs/ の prefix をつける。
* 絶対表記の IRI でないアクティビティ ID には、"tag:adlnet.gov,2013:expapi:0.9:activities:" の prefix をつける。
* 完全な絶対 IRI でない拡張キーには、"tag:adlnet.gov,2013:expapi:0.9:activities:" の prefix をつける。
* アクティビティタイプに "http://adlnet.gov/expapi/activities/" の prefix を付ける。
* すべてのエージェント（アクタ）について：
    * 「"mbox, mbox_sha1sum, openId, account"」、この順序で逆関数識別子を検索する。最初に見つけられた逆関数識別子を保持し、残りは破棄する。
    * 上記の逆関数識別子については、配列で最初の要素を得る。そしてその逆関数識別子プロパティの値としてそれを利用し、残りの要素は破棄する。
    * もしnameプロパティが存在する場合には、name配列の最初の要素にそれが等しくなるよう設定をし、残りの要素を破棄する。
    * 残りすべてのプロパティを削除する。
* もし存在するなら、ステートメントから " voided " プロパティを削除する。もし、" voided " プロパティの値が true なら、ステートメントは変換してはならない。
* 「"version": "1.0.0"」を追加する。
* 権限が前もって設定されていない場合は、homePage に変換を実行したシステムに対応するホームページ、accountName に "unknown" を設定したアカウントによって定義されるエージェントを権限として設定する。
* コンテキストにおけるステートメントフィールドがセットされていた場合、ステートメントから削除すること。
* 他すべてのフィールドは stored を含め、変更せずに保持すること。 stored はステートメントが他システムへ渡った場合についても最新化されるべきである。



######バージョン0.95を元に作られたステートメントのコンバージョン

0.95で作成されたステートメントを変換する1.0.0のシステムは、以下のステップに従わなければならない。

* 無効となったステートメントは変換しないこと。
* 存在する場合、ステートメントから voided プロパティを削除すること。 voided プロパティの値が true である場合、ステートメントを変換してはならない。
* 「 version ": "1.0.0"」を追加する。
* もし権限が前もって与えられてないなら、コンバージョンと" unknown "というアカウント名を実行するシステムと対応するホームページに、ホームページ設定と一緒にアカウントによって識別されたエージェントに権限を与える。
* もしコンテキストのステートメントフィールドが StatementRef 以外に設定されたら、ステートメントからフィールドを削除する。
* stored を含めたその他すべてのフィールドを変更なしで保存する。ステートメントが他のシステムに送られた場合は、 stored は更新される。

######Example 例


A 0.9 ステートメント

```
{
    "id": "d1eec41f-1e93-4ed6-acbf-5c4bd0c24269",
    "actor": {
        "objectType": "Person",
        "name": [
            "Joe Schmoe",
            "Joseph Schmoseph"
        ],
        "mbox": [
            "mailto:joe@example.com"
        ],
        "openid": [
            "http://openid.com/joe-schmoe"
        ]
    },
    "verb": "completed",
    "inProgress": false,
    "object": {
        "objectType": "Activity",
        "id": "http://www.example.com/activities/001",
        "definition": {
            "name": {
                "en-US": "Example Activity"
            },
            "type": "course"
        }
    },
    "result": {
        "completion": true
    },
    "context": {
        "instructor": {
            "objectType": "Person",
            "lastName": [
                "Dad"
            ],
            "firstName": [
                "Joe's"
            ],
            "mbox": [
                "mailto:joesdad@example.com"
            ]
        },
        "contextActivities": {
            "parent": {
                "objectType": "Activity",
                "id": "non-absolute-activity-id",
                "definition": {
                    "name": {
                        "en-US": "Another Activity"
                    }
                }
            }
        }
    },
    "timestamp": "2012-06-01T19:09:13.245Z",
    "stored": "2012-06-29T15:41:39.165Z"
}
```

Converted to 1.0.0: 1.0.0に変換
```
{
    "version": "1.0.0",
    "id": "d1eec41f-1e93-4ed6-acbf-5c4bd0c24269",
    "actor": {
        "objectType": "Agent",
        "name": "Joe Schmoe",
        "mbox": "mailto:joe@example.com"
    },
    "verb": {
        "id": "http://adlnet.gov/expapi/verbs/completed",
        "display": {
            "en-US": "completed"
        }
    },
    "object": {
        "objectType": "Activity",
        "id": "http://www.example.com/activities/001",
        "definition": {
            "name": {
                "en-US": "Example Activity"
            },
            "type": "http://adlnet.gov/expapi/activities/course"
        }
    },
    "result": {
        "completion": true
    },
    "context": {
        "instructor": {
            "objectType": "Agent",
            "mbox": "mailto:joesdad@example.com"
        },
        "contextActivities": {
            "parent": [
                {
                    "objectType": "Activity",
                    "id": "tag:adlnet.gov,2013:expapi:0.9:activities:non-absolute-activity-id",
                    "definition": {
                        "name": {
                            "en-US": "Another Activity"
                        }
                    }
                }
            ]
        }
    },
    "timestamp": "2012-06-01T19:09:13.245Z",
    "stored": "2012-06-29T15:41:39.165Z",
    "authority": {
        "objectType": "Agent",
        "account": {
            "homePage": "http://www.example.com",
            "name": "unknown"
        }
    }
}
```


<div style="page-break-after: always;"></div>
<a name="AppendixE"/></a>
## Appendix E: 署名ステートメント例
「4.4 署名ステートメント」に記載された署名ステートメント例

署名されるべきオリジナルステートメントのリスト。この例では、新しい行が「CR+LF (0x0D + 0x0A)」を含められる。

```
{
    "version": "1.0.0",
    "id": "33cff416-e331-4c9d-969e-5373a1756120",
    "actor": {
        "mbox": "mailto:example@example.com",
        "name": "Example Learner",
        "objectType": "Agent"
    },
    "verb": {
        "id": "http://adlnet.gov/expapi/verbs/experienced",
        "display": {
            "en-US": "experienced"
        }
    },
    "object": {
        "id": "https://www.youtube.com/watch?v=xh4kIiH3Sm8",
        "objectType": "Activity",
        "definition": {
            "name": {
                "en-US": "Tax Tips & Information : How to File a Tax Return "
            },
            "description": {
                "en-US": "Filing a tax return will require filling out either a 1040, 1040A or 1040EZ form"
            }
        }
    },
    "timestamp": "2013-04-01T12:00:00Z"
}
```

署名に使用されるX.509証明書の秘密鍵例

```
-----BEGIN RSA PRIVATE KEY-----
MIICXAIBAAKBgQDjxvZXF30WL4oKjZYXgR0ZyaX+u3y6+JqTqiNkFa/VTnet6Ly2
OT6ZmmcJEPnq3UnewpHoOQ+GfhhTkW13j06j5iNn4obcCVWTL9yXNvJH+Ko+xu4Y
l/ySPRrIPyTjtHdG0M2XzIlmmLqm+CAS+KCbJeH4tf543kIWC5pC5p3cVQIDAQAB
AoGAOejdvGq2XKuddu1kWXl0Aphn4YmdPpPyCNTaxplU6PBYMRjY0aNgLQE6bO2p
/HJiU4Y4PkgzkEgCu0xf/mOq5DnSkX32ICoQS6jChABAe20ErPfm5t8h9YKsTfn9
40lAouuwD9ePRteizd4YvHtiMMwmh5PtUoCbqLefawNApAECQQD1mdBW3zL0okUx
2pc4tttn2qArCG4CsEZMLlGRDd3FwPWJz3ZPNEEgZWXGSpA9F1QTZ6JYXIfejjRo
UuvRMWeBAkEA7WvzDBNcv4N+xeUKvH8ILti/BM58LraTtqJlzjQSovek0srxtmDg
5of+xrxN6IM4p7yvQa+7YOUOukrVXjG+1QJBAI2mBrjzxgm9xTa5odn97JD7UMFA
/WHjlMe/Nx/35V52qaav1sZbluw+TvKMcqApYj5G2SUpSNudHLDGkmd2nQECQFfc
lBRK8g7ZncekbGW3aRLVGVOxClnLLTzwOlamBKOUm8V6XxsMHQ6TE2D+fKJoNUY1
2HGpk+FWwy2D1hRGuoUCQAXfaLSxtaWdPtlZTPVueF7ZikQDsVg+vtTFgpuHloR2
6EVc1RbHHZm32yvGDY8IkcoMfJQqLONDdLfS/05yoNU=
-----END RSA PRIVATE KEY-----
```

公開X.509 証明書例

```
-----BEGIN CERTIFICATE-----
MIIDATCCAmqgAwIBAgIJAMB1csNuA6+kMA0GCSqGSIb3DQEBBQUAMHExCzAJBgNV
BAYTAlVTMRIwEAYDVQQIEwlUZW5uZXNzZWUxGDAWBgNVBAoTD0V4YW1wbGUgQ29t
cGFueTEQMA4GA1UEAxMHRXhhbXBsZTEiMCAGCSqGSIb3DQEJARYTZXhhbXBsZUBl
eGFtcGxlLmNvbTAeFw0xMzA0MDQxNTI4MzBaFw0xNDA0MDQxNTI4MzBaMIGWMQsw
CQYDVQQGEwJVUzESMBAGA1UECBMJVGVubmVzc2VlMREwDwYDVQQHEwhGcmFua2xp
bjEYMBYGA1UEChMPRXhhbXBsZSBDb21wYW55MRAwDgYDVQQLEwdFeGFtcGxlMRAw
DgYDVQQDEwdFeGFtcGxlMSIwIAYJKoZIhvcNAQkBFhNleGFtcGxlQGV4YW1wbGUu
Y29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDjxvZXF30WL4oKjZYXgR0Z
yaX+u3y6+JqTqiNkFa/VTnet6Ly2OT6ZmmcJEPnq3UnewpHoOQ+GfhhTkW13j06j
5iNn4obcCVWTL9yXNvJH+Ko+xu4Yl/ySPRrIPyTjtHdG0M2XzIlmmLqm+CAS+KCb
JeH4tf543kIWC5pC5p3cVQIDAQABo3sweTAJBgNVHRMEAjAAMCwGCWCGSAGG+EIB
DQQfFh1PcGVuU1NMIEdlbmVyYXRlZCBDZXJ0aWZpY2F0ZTAdBgNVHQ4EFgQUVs3v
5afEdOeoYeVajAQE4v0WS1QwHwYDVR0jBBgwFoAUyVIc3yvra4EBz20I4BF39IAi
xBkwDQYJKoZIhvcNAQEFBQADgYEAgS/FF5D0Hnj44rvT6kgn3kJAvv2lj/fyjztK
IrYS33ljXGn6gGyA4qtbXA23PrO4uc/wYCSDICDpPobh62xTCd9qObKhgwWOi05P
SBLqUu3mwfAe15LJBJBqPVZ4K0kppePBU8m6aIZoH57L/9t4OoaL8yKs/qjKFeI1
OFWZxvA=
-----END CERTIFICATE-----
```

CA証明書例

```
-----BEGIN CERTIFICATE-----
MIIDNzCCAqCgAwIBAgIJAMB1csNuA6+jMA0GCSqGSIb3DQEBBQUAMHExCzAJBgNV
BAYTAlVTMRIwEAYDVQQIEwlUZW5uZXNzZWUxGDAWBgNVBAoTD0V4YW1wbGUgQ29t
cGFueTEQMA4GA1UEAxMHRXhhbXBsZTEiMCAGCSqGSIb3DQEJARYTZXhhbXBsZUBl
eGFtcGxlLmNvbTAeFw0xMzA0MDQxNTI1NTNaFw0yMzA0MDIxNTI1NTNaMHExCzAJ
BgNVBAYTAlVTMRIwEAYDVQQIEwlUZW5uZXNzZWUxGDAWBgNVBAoTD0V4YW1wbGUg
Q29tcGFueTEQMA4GA1UEAxMHRXhhbXBsZTEiMCAGCSqGSIb3DQEJARYTZXhhbXBs
ZUBleGFtcGxlLmNvbTCBnzANBgkqhkiG9w0BAQEFAAOBjQAwgYkCgYEA1sBnBWPZ
0f7WJUFTJy5+01SlS5Z6DDD6Uye9vK9AycgV5B3+WC8HC5u5h91MujAC1ARPVUOt
svPRs45qKNFIgIGRXKPAwZjawEI2sCJRSKV47i6B8bDv4WkuGvQaveZGI0qlmN5R
1Eim2gUItRj1hgcC9rQavjlnFKDY2rlXGukCAwEAAaOB1jCB0zAdBgNVHQ4EFgQU
yVIc3yvra4EBz20I4BF39IAixBkwgaMGA1UdIwSBmzCBmIAUyVIc3yvra4EBz20I
4BF39IAixBmhdaRzMHExCzAJBgNVBAYTAlVTMRIwEAYDVQQIEwlUZW5uZXNzZWUx
GDAWBgNVBAoTD0V4YW1wbGUgQ29tcGFueTEQMA4GA1UEAxMHRXhhbXBsZTEiMCAG
CSqGSIb3DQEJARYTZXhhbXBsZUBleGFtcGxlLmNvbYIJAMB1csNuA6+jMAwGA1Ud
EwQFMAMBAf8wDQYJKoZIhvcNAQEFBQADgYEADhwTebGk735yKhm8DqCxvNnEZ0Nx
sYEYOjgRG1yXTlW5pE691fSH5AZ+T6fpwpZcWY5QYkoN6DnwjOxGkSfQC3/yGmcU
DKBPwiZ5O2s9C+fE1kUEnrX2Xea4agVngMzR8DQ6oOauLWqehDB+g2ENWRLoVgS+
ma5/Ycs0GTyrECY=
-----END CERTIFICATE-----
```

JWSヘッダー。アルゴリズムを記すのと一緒に、署名証明書のために証明書チェーンが含まれることに注意しなさい。

```
{
    "alg": "RS256",
    "x5c": [
        "MIIDATCCAmqgAwIBAgIJAMB1csNuA6+kMA0GCSqGSIb3DQEBBQUAMHExCzAJBgNVBAYTAlVTMRIwEAYDVQQIEwlUZW5uZXNzZWUxGDAWBgNVBAoTD0V4YW1wbGUgQ29tcGFueTEQMA4GA1UEAxMHRXhhbXBsZTEiMCAGCSqGSIb3DQEJARYTZXhhbXBsZUBleGFtcGxlLmNvbTAeFw0xMzA0MDQxNTI4MzBaFw0xNDA0MDQxNTI4MzBaMIGWMQswCQYDVQQGEwJVUzESMBAGA1UECBMJVGVubmVzc2VlMREwDwYDVQQHEwhGcmFua2xpbjEYMBYGA1UEChMPRXhhbXBsZSBDb21wYW55MRAwDgYDVQQLEwdFeGFtcGxlMRAwDgYDVQQDEwdFeGFtcGxlMSIwIAYJKoZIhvcNAQkBFhNleGFtcGxlQGV4YW1wbGUuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDjxvZXF30WL4oKjZYXgR0ZyaX+u3y6+JqTqiNkFa/VTnet6Ly2OT6ZmmcJEPnq3UnewpHoOQ+GfhhTkW13j06j5iNn4obcCVWTL9yXNvJH+Ko+xu4Yl/ySPRrIPyTjtHdG0M2XzIlmmLqm+CAS+KCbJeH4tf543kIWC5pC5p3cVQIDAQABo3sweTAJBgNVHRMEAjAAMCwGCWCGSAGG+EIBDQQfFh1PcGVuU1NMIEdlbmVyYXRlZCBDZXJ0aWZpY2F0ZTAdBgNVHQ4EFgQUVs3v5afEdOeoYeVajAQE4v0WS1QwHwYDVR0jBBgwFoAUyVIc3yvra4EBz20I4BF39IAixBkwDQYJKoZIhvcNAQEFBQADgYEAgS/FF5D0Hnj44rvT6kgn3kJAvv2lj/fyjztKIrYS33ljXGn6gGyA4qtbXA23PrO4uc/wYCSDICDpPobh62xTCd9qObKhgwWOi05PSBLqUu3mwfAe15LJBJBqPVZ4K0kppePBU8m6aIZoH57L/9t4OoaL8yKs/qjKFeI1OFWZxvA=",
        "MIIDNzCCAqCgAwIBAgIJAMB1csNuA6+jMA0GCSqGSIb3DQEBBQUAMHExCzAJBgNVBAYTAlVTMRIwEAYDVQQIEwlUZW5uZXNzZWUxGDAWBgNVBAoTD0V4YW1wbGUgQ29tcGFueTEQMA4GA1UEAxMHRXhhbXBsZTEiMCAGCSqGSIb3DQEJARYTZXhhbXBsZUBleGFtcGxlLmNvbTAeFw0xMzA0MDQxNTI1NTNaFw0yMzA0MDIxNTI1NTNaMHExCzAJBgNVBAYTAlVTMRIwEAYDVQQIEwlUZW5uZXNzZWUxGDAWBgNVBAoTD0V4YW1wbGUgQ29tcGFueTEQMA4GA1UEAxMHRXhhbXBsZTEiMCAGCSqGSIb3DQEJARYTZXhhbXBsZUBleGFtcGxlLmNvbTCBnzANBgkqhkiG9w0BAQEFAAOBjQAwgYkCgYEA1sBnBWPZ0f7WJUFTJy5+01SlS5Z6DDD6Uye9vK9AycgV5B3+WC8HC5u5h91MujAC1ARPVUOtsvPRs45qKNFIgIGRXKPAwZjawEI2sCJRSKV47i6B8bDv4WkuGvQaveZGI0qlmN5R1Eim2gUItRj1hgcC9rQavjlnFKDY2rlXGukCAwEAAaOB1jCB0zAdBgNVHQ4EFgQUyVIc3yvra4EBz20I4BF39IAixBkwgaMGA1UdIwSBmzCBmIAUyVIc3yvra4EBz20I4BF39IAixBmhdaRzMHExCzAJBgNVBAYTAlVTMRIwEAYDVQQIEwlUZW5uZXNzZWUxGDAWBgNVBAoTD0V4YW1wbGUgQ29tcGFueTEQMA4GA1UEAxMHRXhhbXBsZTEiMCAGCSqGSIb3DQEJARYTZXhhbXBsZUBleGFtcGxlLmNvbYIJAMB1csNuA6+jMAwGA1UdEwQFMAMBAf8wDQYJKoZIhvcNAQEFBQADgYEADhwTebGk735yKhm8DqCxvNnEZ0NxsYEYOjgRG1yXTlW5pE691fSH5AZ+T6fpwpZcWY5QYkoN6DnwjOxGkSfQC3/yGmcUDKBPwiZ5O2s9C+fE1kUEnrX2Xea4agVngMzR8DQ6oOauLWqehDB+g2ENWRLoVgS+ma5/Ycs0GTyrECY="
    ]
}
```

JWS 署名

```
ew0KICAgICJhbGciOiAiUlMyNTYiLA0KICAgICJ4NWMiOiBbDQogICAgICAgICJNSUlEQVRDQ0FtcWdBd0lCQWdJSkFNQjFjc051QTYra01BMEdDU3FHU0liM0RRRUJCUVVBTUhFeEN6QUpCZ05WQkFZVEFsVlRNUkl3RUFZRFZRUUlFd2xVWlc1dVpYTnpaV1V4R0RBV0JnTlZCQW9URDBWNFlXMXdiR1VnUTI5dGNHRnVlVEVRTUE0R0ExVUVBeE1IUlhoaGJYQnNaVEVpTUNBR0NTcUdTSWIzRFFFSkFSWVRaWGhoYlhCc1pVQmxlR0Z0Y0d4bExtTnZiVEFlRncweE16QTBNRFF4TlRJNE16QmFGdzB4TkRBME1EUXhOVEk0TXpCYU1JR1dNUXN3Q1FZRFZRUUdFd0pWVXpFU01CQUdBMVVFQ0JNSlZHVnVibVZ6YzJWbE1SRXdEd1lEVlFRSEV3aEdjbUZ1YTJ4cGJqRVlNQllHQTFVRUNoTVBSWGhoYlhCc1pTQkRiMjF3WVc1NU1SQXdEZ1lEVlFRTEV3ZEZlR0Z0Y0d4bE1SQXdEZ1lEVlFRREV3ZEZlR0Z0Y0d4bE1TSXdJQVlKS29aSWh2Y05BUWtCRmhObGVHRnRjR3hsUUdWNFlXMXdiR1V1WTI5dE1JR2ZNQTBHQ1NxR1NJYjNEUUVCQVFVQUE0R05BRENCaVFLQmdRRGp4dlpYRjMwV0w0b0tqWllYZ1IwWnlhWCt1M3k2K0pxVHFpTmtGYS9WVG5ldDZMeTJPVDZabW1jSkVQbnEzVW5ld3BIb09RK0dmaGhUa1cxM2owNmo1aU5uNG9iY0NWV1RMOXlYTnZKSCtLbyt4dTRZbC95U1BScklQeVRqdEhkRzBNMlh6SWxtbUxxbStDQVMrS0NiSmVINHRmNTQza0lXQzVwQzVwM2NWUUlEQVFBQm8zc3dlVEFKQmdOVkhSTUVBakFBTUN3R0NXQ0dTQUdHK0VJQkRRUWZGaDFQY0dWdVUxTk1JRWRsYm1WeVlYUmxaQ0JEWlhKMGFXWnBZMkYwWlRBZEJnTlZIUTRFRmdRVVZzM3Y1YWZFZE9lb1llVmFqQVFFNHYwV1MxUXdId1lEVlIwakJCZ3dGb0FVeVZJYzN5dnJhNEVCejIwSTRCRjM5SUFpeEJrd0RRWUpLb1pJaHZjTkFRRUZCUUFEZ1lFQWdTL0ZGNUQwSG5qNDRydlQ2a2duM2tKQXZ2MmxqL2Z5anp0S0lyWVMzM2xqWEduNmdHeUE0cXRiWEEyM1ByTzR1Yy93WUNTRElDRHBQb2JoNjJ4VENkOXFPYktoZ3dXT2kwNVBTQkxxVXUzbXdmQWUxNUxKQkpCcVBWWjRLMGtwcGVQQlU4bTZhSVpvSDU3TC85dDRPb2FMOHlLcy9xaktGZUkxT0ZXWnh2QT0iLA0KICAgICAgICAiTUlJRE56Q0NBcUNnQXdJQkFnSUpBTUIxY3NOdUE2K2pNQTBHQ1NxR1NJYjNEUUVCQlFVQU1IRXhDekFKQmdOVkJBWVRBbFZUTVJJd0VBWURWUVFJRXdsVVpXNXVaWE56WldVeEdEQVdCZ05WQkFvVEQwVjRZVzF3YkdVZ1EyOXRjR0Z1ZVRFUU1BNEdBMVVFQXhNSFJYaGhiWEJzWlRFaU1DQUdDU3FHU0liM0RRRUpBUllUWlhoaGJYQnNaVUJsZUdGdGNHeGxMbU52YlRBZUZ3MHhNekEwTURReE5USTFOVE5hRncweU16QTBNREl4TlRJMU5UTmFNSEV4Q3pBSkJnTlZCQVlUQWxWVE1SSXdFQVlEVlFRSUV3bFVaVzV1WlhOelpXVXhHREFXQmdOVkJBb1REMFY0WVcxd2JHVWdRMjl0Y0dGdWVURVFNQTRHQTFVRUF4TUhSWGhoYlhCc1pURWlNQ0FHQ1NxR1NJYjNEUUVKQVJZVFpYaGhiWEJzWlVCbGVHRnRjR3hsTG1OdmJUQ0JuekFOQmdrcWhraUc5dzBCQVFFRkFBT0JqUUF3Z1lrQ2dZRUExc0JuQldQWjBmN1dKVUZUSnk1KzAxU2xTNVo2RERENlV5ZTl2SzlBeWNnVjVCMytXQzhIQzV1NWg5MU11akFDMUFSUFZVT3RzdlBSczQ1cUtORklnSUdSWEtQQXdaamF3RUkyc0NKUlNLVjQ3aTZCOGJEdjRXa3VHdlFhdmVaR0kwcWxtTjVSMUVpbTJnVUl0UmoxaGdjQzlyUWF2amxuRktEWTJybFhHdWtDQXdFQUFhT0IxakNCMHpBZEJnTlZIUTRFRmdRVXlWSWMzeXZyYTRFQnoyMEk0QkYzOUlBaXhCa3dnYU1HQTFVZEl3U0JtekNCbUlBVXlWSWMzeXZyYTRFQnoyMEk0QkYzOUlBaXhCbWhkYVJ6TUhFeEN6QUpCZ05WQkFZVEFsVlRNUkl3RUFZRFZRUUlFd2xVWlc1dVpYTnpaV1V4R0RBV0JnTlZCQW9URDBWNFlXMXdiR1VnUTI5dGNHRnVlVEVRTUE0R0ExVUVBeE1IUlhoaGJYQnNaVEVpTUNBR0NTcUdTSWIzRFFFSkFSWVRaWGhoYlhCc1pVQmxlR0Z0Y0d4bExtTnZiWUlKQU1CMWNzTnVBNitqTUF3R0ExVWRFd1FGTUFNQkFmOHdEUVlKS29aSWh2Y05BUUVGQlFBRGdZRUFEaHdUZWJHazczNXlLaG04RHFDeHZObkVaME54c1lFWU9qZ1JHMXlYVGxXNXBFNjkxZlNINUFaK1Q2ZnB3cFpjV1k1UVlrb042RG53ak94R2tTZlFDMy95R21jVURLQlB3aVo1TzJzOUMrZkUxa1VFbnJYMlhlYTRhZ1ZuZ016UjhEUTZvT2F1TFdxZWhEQitnMkVOV1JMb1ZnUyttYTUvWWNzMEdUeXJFQ1k9Ig0KICAgIF0NCn0.ew0KICAgICJ2ZXJzaW9uIjogIjEuMC4wIiwNCiAgICAiaWQiOiAiMzNjZmY0MTYtZTMzMS00YzlkLTk2OWUtNTM3M2ExNzU2MTIwIiwNCiAgICAiYWN0b3IiOiB7DQogICAgICAgICJtYm94IjogIm1haWx0bzpleGFtcGxlQGV4YW1wbGUuY29tIiwNCiAgICAgICAgIm5hbWUiOiAiRXhhbXBsZSBMZWFybmVyIiwNCiAgICAgICAgIm9iamVjdFR5cGUiOiAiQWdlbnQiDQogICAgfSwNCiAgICAidmVyYiI6IHsNCiAgICAgICAgImlkIjogImh0dHA6Ly9hZGxuZXQuZ292L2V4cGFwaS92ZXJicy9leHBlcmllbmNlZCIsDQogICAgICAgICJkaXNwbGF5Ijogew0KICAgICAgICAgICAgImVuLVVTIjogImV4cGVyaWVuY2VkIg0KICAgICAgICB9DQogICAgfSwNCiAgICAib2JqZWN0Ijogew0KICAgICAgICAiaWQiOiAiaHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g_dj14aDRrSWlIM1NtOCIsDQogICAgICAgICJvYmplY3RUeXBlIjogIkFjdGl2aXR5IiwNCiAgICAgICAgImRlZmluaXRpb24iOiB7DQogICAgICAgICAgICAibmFtZSI6IHsNCiAgICAgICAgICAgICAgICAiZW4tVVMiOiAiVGF4IFRpcHMgJiBJbmZvcm1hdGlvbiA6IEhvdyB0byBGaWxlIGEgVGF4IFJldHVybiAiDQogICAgICAgICAgICB9LA0KICAgICAgICAgICAgImRlc2NyaXB0aW9uIjogew0KICAgICAgICAgICAgICAgICJlbi1VUyI6ICJGaWxpbmcgYSB0YXggcmV0dXJuIHdpbGwgcmVxdWlyZSBmaWxsaW5nIG91dCBlaXRoZXIgYSAxMDQwLCAxMDQwQSBvciAxMDQwRVogZm9ybSINCiAgICAgICAgICAgIH0NCiAgICAgICAgfQ0KICAgIH0sDQogICAgInRpbWVzdGFtcCI6ICIyMDEzLTA0LTAxVDEyOjAwOjAwWiINCn0.FWuwaPhwUbkk7h9sKW5zSvjsYNugvxJ-TrVaEgt_DCUT0bmKhQScRrjMB6P9O50uznPwT66oF1NnU_G0HVhRzS5voiXE-y7tT3z0M3-8A6YK009Bk_digVUul-HA4Fpd5IjoBBGe3yzaQ2ZvzarvRuipvNEQCI0onpfuZZJQ0d8
```

署名されたステートメント

```
{
    "version": "1.0.0",
    "id": "33cff416-e331-4c9d-969e-5373a1756120",
    "actor": {
        "mbox": "mailto:example@example.com",
        "name": "Example Learner",
        "objectType": "Agent"
    },
    "verb": {
        "id": "http://adlnet.gov/expapi/verbs/experienced",
        "display": {
            "en-US": "experienced"
        }
    },
    "object": {
        "id": "https://www.youtube.com/watch?v=xh4kIiH3Sm8",
        "objectType": "Activity",
        "definition": {
            "name": {
                "en-US": "Tax Tips & Information : How to File a Tax Return "
            },
            "description": {
                "en-US": "Filing a tax return will require filling out either a 1040, 1040A or 1040EZ form"
            }
        }
    },
    "timestamp": "2013-04-01T12:00:00Z",
    "attachments": [
        {
            "usageType": "http://adlnet.gov/expapi/attachments/signature",
            "display": { "en-US": "Signature" },
            "description": { "en-US": "A test signature" },
            "contentType": "application/octet-stream",
            "length": 4235,
            "sha2": "672fa5fa658017f1b72d65036f13379c6ab05d4ab3b6664908d8acf0b6a0c634"
        }
    ]
}
```

__注記:__ 添付した署名が表示されない場合、 attachments で添付型メッセージのフォーマットを確認すること。


<div style="page-break-after: always;"></div>
<a name="AppendixF"/></a>

## Appendix F: すべてのエンドポイントの表

<table>
    <tr>
        <th>Endpoint (Base IRI of the LRS Precedes Each Endpoint)</th>
        <th>Function</th>
    </tr>
    <tr>
        <td>statements</td>
        <td>Statement Storage/Retrieval</td>
    </tr>
    <tr>
        <td>agents</td>
        <td>Agent Object Storage/Retrieval</td>
    </tr>
    <tr>
        <td>agents/profile</td>
        <td>Agent Profile API</td>
    </tr>
    <tr>
        <td>activities</td>
        <td>Activity Object Storage/Retrieval</td>
    </tr>
    <tr>
        <td>activities/profile</td>
        <td>Activity Profile API</td>
    </tr>
    <tr>
        <td>activities/state</td>
        <td>State API</td>
    </tr>
    <tr>
        <td>about</td>
        <td>LRS Information</td>
    </tr>
    <tr>
        <td>OAuth/initiate</td>
        <td>Temporary Credential Request</td>
    </tr>
    <tr>
        <td>OAuth/authorize</td>
        <td>Resource Owner Authorization</td>
    </tr>
    <tr>
        <td>OAuth/token</td>
        <td>Token Request</td>
    </tr>
</table>
>
