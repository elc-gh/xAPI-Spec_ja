# Experience API
## Advanced Distributed Learning (ADL) Co-Laboratories

### 2014.2.18 日本語版
### 「Tin Canプロジェクト」
特定非営利活動法人日本イーラーニングコンソシアムとモバイルラーニングコンソシアムは、共同で「Tin Canプロジェクト」を発足しました。この文書は、「Tin Canプロジェクト」メンバーが、Experience API（v1.0.0）を日本語に翻訳したものです。

この文書についての問い合わせは、以下にお願いします。

tincan@elc.or.jp

### 「Tin Canプロジェクト」　日本語版制作メンバー（五十音順）

伊藤彰孝（株式会社ベネッセコーポレーション）

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
<s>
>This document was authored by members of the Experience API Working Group (see list on pp. 7-8) in support of the Office of the Deputy Assistant Secretary of Defense (Readiness) Advanced Distributed Learning (ADL) Initiative. Please send all feedback and inquiries to helpdesk@adlnet.gov  
</s>

>この文書は、Experience API ワーキンググループのメンバー（2.2.1 の表を参照）が、国防次官補室（即応性担当）の Advanced Distributed Learning (ADL) イニシアティブを支援し作成しました。フィードバックやお問い合わせは、helpdesk@adlnet.gov までお送りください。
<div style="page-break-after: always;"></div>
## <s>Table of Contents</s> 目次
*	1.0.	[<s>Revision History</s>改定履歴](#revhistory)  
*	2.0.	[<s>Role of the Experience API</s>Experience API の役割](#roleofxapi)
	*	2.1.	[<s>ADL's Role in the Experience API</s>xAPI における ADL の位置づけ](#adlrole)  
 	*	2.2.	[<s>Contributors</s>貢献者](#contributors)
 		*	2.2.1.	[<s>Working Group Participants</s>ワーキンググループの参加者](#wg)  
		*	2.2.2.	[<s>Requirements Gathering Participants</s>要求仕様収集への貢献者](#reqparticipants) 
	*	2.3	[<s>Reading Guidelines for the Non-Technically Inclined</s>技術に詳しくない人への読み方ガイドライン](#readingguidelines)
*	3.0.	[<s>Definitions</s>用語の定義](#defintions)  
*	4.0.	[<s>Statement</s>ステートメント](#statement)  
    *	4.1.	[<s>Statement Properties</s>ステートメントプロパティ](#stmtprops)  
        *	4.1.1.	[<s>ID</s>id (識別子)](#stmtid)  
        *	4.1.2.	[<s>Actor</s>Actor (アクタ)](#actor)  
        *	4.1.3.	[<s>Verb</s>Verb (動詞)](#verb)  
        *	4.1.4.	[<s>Object</s>Object (目的語)](#object)  
        *	4.1.5.	[<s>Result</s>Result (結果)](#result)  
        *	4.1.6.	[<s>Context</s>Context (文脈)](#context)  
        *	4.1.7.	[<s>Timestamp</s>Timestamp (タイムスタンプ)](#timestamp)  
        *	4.1.8.	[<s>Stored</s>Stored](#stored)  
        *	4.1.9.	[<s>Authority</s>Authority (権限)
        *	](#authority)  
        *	4.1.10.	[<s>Version</s>Version (バージョン)](#version)  
        *	4.1.11.	[<s>Attachments</s>Attachments (添付資料)](#attachments)  
        *	4.1.12.	[<s>Data Constraints</s>データの制約](#dataconstraints)  
    *	4.2.	[<s>Retrieval of Statements</s>ステートメントの検索](#retstmts)  
	*	4.3.	[<s>Voided</s>無効](#voided)  
	*	4.4.	[<s>Signed Statements</s>署名付きステートメント](#signature)  
*	5.0.	[<s>Miscellaneous Types</s>各種タイプ](#misctypes)  
    *	5.1.	[<s>Document</s>ドキュメント](#miscdocument)  
    *	5.2.	[<s>Language Map</s>言語マップ](#misclangmap)  
    *	5.3.	[<s>Extensions</s>拡張](#miscext)  
    *	5.4.	[<s>Identifier Metadata</s>識別子メタデータ](#miscmeta)  
*	6.0.	[<s>Runtime Communication</s>ランタイム通信](#rtcom)  
    *	6.1.	[<s>Encoding</s>エンコーディング](#encoding)  
    *	6.2.	[<s>API Versioning</s>API のバージョン管理](#apiversioning)  
    *	6.3.	[<s>Concurrency</s>同時実行](#concurrency)  
    *	6.4.	[<s>Security</s>セキュリティ](#security)  
		*	6.4.1.	[<s>Authentication Definitions</s>各シナリオの取り扱い方法](#authdefs)  
		*	6.4.2.	[<s>OAuth Authorization Scope</s>OAuth 認証スコープ](#oauthscope)  
*	7.0.	[<s>Data Transfer (REST)</s>Data Transfer (REST)](#datatransfer)  
    *	7.1.	[<s>Error Codes</s>エラーコード](#errorcodes)  
    *	7.2.	[<s>Statement API</s>ステートメント API](#stmtapi)  
    *	7.3.	[<s>Document APIs</s>ドキュメント API](#docapis)  
    *	7.4.	[<s>State API</s>ステート API](#stateapi)  
    *	7.5.	[<s>Activity Profile API</s>アクティビティプロファイル API](#actprofapi)  
    *	7.6.	[<s>Agent Profile API</s>エージェントプロファイル API](#agentprofapi)  
    *	7.7.	[<s>About resource</s>About リソース](#aboutresource)  
    *	7.8.	[<s>Cross Origin Requests</s>クロスオリジンリクエスト](#cors)  
    *	7.9.	[<s>Validation</s>バリデーション](#validation)  
    *	7.10.	[<s>HTTP HEAD</s>HTTP HEAD](#httphead)  
*	[Appendix A: <s>Bookmarklet</s>ブックマークレット](#AppendixA)  
*	[Appendix B: <s>Creating an "IE Mode" Request</s>IE 用リクエスト作成](#AppendixB)  
*	[Appendix C: <s>Example definitions for Activities of type "cmi.interaction"</s>アクティビティタイプ "cmi.interaction" のための体儀例](#AppendixC)  
*	[Appendix D: <s>Example Statements</s>ステートメント例](#AppendixD)  
*	[Appendix E: <s>Converting Statements to 1.0.0</s>1.0.0 へステートメントを変換](#AppendixE)   
*	[Appendix F: <s>Example Signed Statement</s>署名ステートメント例](#AppendixF)

<a name="revhistory"/>  
<div style="page-break-after: always;"></div>
## 1.0 <s>Revision History</s> 改定履歴
###### <s>0.8 (Project Tin Can API Deliverable) to 0.9 (March 31, 2012)</s>0.8 (Project Tin Can API の配布）から 0.9 (2012/03/31)  
<s>  
Rustici Software, who delivered the Project Tin Can API, made modifications to the API prior to the April 2012 Kickoff Meeting. It was voted in this meeting to move those changes into the current specification and revision to 0.9.
</s>

Project Tin Can API を提供した Rustici Software が、2012年4月のキックオフ会議に先立ち、API に対する改定を行った。会議において投票が行われ、それらの改定を仕様書に取り込み、第0.9版とすることが議決された。

###### <s>0.90 to 0.95 (August 31, 2012)</s> 0.90 から 0.95 (2012/08/31)

<s>
"Core" Verbs and Activity types were removed from the specification. References to these verbs in results, context, interactions, and Activity Definitions were also  removed. It was recommended that implementers prefer community defined verbs to creating their own verbs.
</s>

"コア"とされる動詞とアクティビティタイプが仕様書より削除された。また、結果、文脈、インタラクション、およびアクティビティ定義における、それらの動詞への参照も同時に削除された。実装者には、自ら動詞を定義するよりも、コミュニティが定義した動詞を利用することが推奨された。

- <s>Verbs, Activity types, and extension keys are now URIs</s>動詞、アクティビティタイプ、拡張キーを URI とする。
- <s>Restructured and added language around some of the other implementation details and scope.</s>いくつかの実装詳細と対象範囲を整理し、説明を追加した。
- <s>Changed from using a person-centric view of Agents to a persona-centric view.</s>エージェントについて、個人指向の視点からペルソナ指向の視点を用いるように変更。
- <s>Friend of a Friend (FOAF) Agent merging requirement was removed.</s>友達の友達 (FOAF) エージェントの結合要求を削除。
- <s>Agent Objects must now have exactly 1 uniquely identifying property, instead of at least one.</s>エージェントオブジェクトは、（１つ以上の一意 ID プロパティではなく）ただ１つの一意 ID プロパティを持つように変更。

###### <s>0.95 to 1.0.0 (April 26, 2013)</s> 0.95 から 1.0.0 (2013/4/26) 
<s>Various refinements and clarifications including:</s>

以下のような多数の改善と明確化を行った。

- <s>Adding attachments</s>添付文書の概念を追加。

- <s>Activity metadata is now stored as JSON rather than XML</s>アクティビティのメタデータを XML ではなく JSON に変更。
- <s>Changes to voiding Statements</s>ステートメントの無効化に関する変更。
- <s>Clarification and naming of the Document APIs</s>ドキュメント API の追加。
- <s>Changes to querying the Statement API</s>ステートメント API の検索に関する変更。
- <s>Signed Statements</s>署名付きステートメントの追加。

<a name="roleofxapi"/>

## 2.0 <s>Role of the Experience API</s> Experience API の役割
<s>  
The Experience API is a service that allows for statements of experience to be delivered to and stored securely in a Learning Record Store (LRS). These statements of experience are typically learning experiences, but the API can address statements of any kind of experience. The Experience API is dependent on Activity Providers to create and track these learning experiences; this specification provides a data model and associated components on how to accomplish these tasks.
</s>

Experience API (xAPI) は経験に関するステートメントを、Learning Record Store (LRS) に配送し、安全に記録するためのサービスである。これらの経験に関するステートメントは、典型的には学習経験を示す物であるが、API はどのような経験に関するステートメントも扱うことができる。xAPI は、アクティビティプロバイダがこれらの学習経験を生成、蓄積することを目的としており、本仕様はその動作を実現するためのデータモデルと関連するコンポーネントを提供する。

<s>Specifically, the Experience API provides:</s>

xAPI は以下を提供する。

* <s>The structure and definition of Statement, State, learner, Activity and Objects, which are the means by which experiences are conveyed by a Activity Provider.</s>アクティビティプロバイダによって経験が伝達される手段としての、ステートメント、状態、学習者、アクティビティ、オブジェクトの構造と定義

* <s>Data Transfer methods for the storage and retrieval (but not validation) of these Objects to/from a Learning Record Store. Note that the systems storing or retrieving records need not be Activity Providers. LRSs may 
communicate with other LRSs, or reporting systems.</s>上記のオブジェクトの LRS に対する記録と取り出し（検証は含まない）のためのデータ転送手段。情報を記録または取り出すシステムは、アクティビティプロバイダである必要はないことに注意。LRS は他の LRS やレポーティングシステムと通信をすることがある

* <s>Security methods allowing for the trusted exchange of information between the Learning Record Store and trusted sources.</s>LRS とデータソースとの間での信頼のおける情報通信を可能にするセキュリティ手段

<s>
The Experience API is the first of many envisioned technologies that will enable a richer architecture of online learning and training. Authentication services, querying services, visualization services, and personal data services are some examples of additional technologies which the Experience API is designed to support. While the implementation details of these services are not specified here, the Experience API is designed with this larger architectural vision in mind.
</s>

xAPI はオンライン学習とトレーニングに関する高機能なアーキテクチャを提供する一連の技術提案の端緒となる。xAPI の適用例として、認証サービス、検索サービス、可視化サービス、個人データサービスなどが考えられる。本仕様には、これらのサービスの実装詳細については示されていないが、xAPI は大きなアーキテクチャ思想を前提に設計されている。

<a name="adlrole"/>

### 2.1 <s>ADL's Role in the Experience API</s> xAPI における ADL の位置づけ

<s>  
The Advanced Distributed Learning (ADL) Initiative has taken on the roles of steward and facilitator in the development of the Experience API. The Experience API is seen as one piece of the ADL Training and Learning Architecture, which facilitates learning anytime and anywhere. ADL views the Experience API as an evolved version of SCORM that can support similar use cases, but can also support many of the use cases gathered by ADL and submitted by those involved in distributed learning that SCORM could not enable.  
</s>

Advanced Distributed Learning (ADL) イニシアティブは xAPI の開発における、事務局やファシリテータとしての役割を担っている。xAPI は、学習をいつでもどこでも行えるような ADL のトレーニングと学習のためのアーキテクチャの一部と位置付ける。ADL は、 xAPI を同じようなユースケースをサポートできる SCORM の拡張とみているだけでなく、ADL や分散学習に係る人たちによって提案された 、SCORM が実現できないユースケースもサポートするものと考える。

<a name="contributors"/> 

### 2.2 <s>Contributors</s> 貢献者

> <s>_"My thanks to everyone who contributed to the Experience API project. Many of you have called into the weekly meetings and helped to shape the specification into something that is useful for the entire distributed learning community. Many of you assisted in releasing code samples, products, and documentation to aid those who are creating and adopting the specification.  I'd also like to thank all of those who were involved in supplying useful, honest information about your organization's use of SCORM and other learning best practices. Through the use-cases, shared experiences, and knowledge you have shared, ADL and the community clearly identified the first step in creating the Training and Learning Architecture--the Experience API.  You are truly the community leaders on which we depend to make our training and education the very best."_ </s>

> _Experience API プロジェクトに貢献していただいた皆さんに感謝いたします。多くの皆さんが毎週のミーティングに参加し、本仕様書を分散学習コミュニティ全体に対して有用なものとなるように仕上げる支援をしてくれました。また、多くの皆さんが、仕様書を作成、編集している人たちの助けになるように、コードサンプルや製品、文書などを提供してくれました。各自の組織における SCORM の利用や学習に関するベストプラクティスの有用で正直な情報を提供していただいた皆様にも感謝したいと思います。皆さんから提供いただいたユースケース、経験と知識に基づいて、ADL とコミュニティはトレーニングと学習に関するアーキテクチャの第一歩 – Experience API を明確に定義することができました。皆さんこそが、最高のトレーニングと教育を提供するために私たちが頼りにできるコミュニティリーダーです。_

Kristy S. Murray, Ed.D.  
Director, ADL Initiative  
OSD, Training Readiness & Strategy (TRS)  

<a name="wg"/>

### 2.2.1 <s>Working Group Participants</s> ワーキンググループの参加者  

<table>
	<tr><th><s>_Name_</s>名前</th><th><s>_Organization_</s>組織</th></tr>
	<tr><td>Aaron Silvers</td><td>ADL</td></tr>
	<tr><td>Al Bejcek</td><td>NetDimensions</td></tr>
	<tr><td>Ali Shahrazad</td><td>SaLTBOX</td></tr>
	<tr><td>Andrew Downes</td><td>Epic</td></tr>
	<tr><td>Andy Johnson</td><td>ADL</td></tr>
	<tr><td>Andy Whitaker</td><td>Rustici Software</td></tr>
	<tr><td>Anthony Altieri</td><td>American Red Cross</td></tr>
	<tr><td>Anto Valan</td><td>Omnivera Learning Solutions</td></tr>
	<tr><td>Avron Barr</td><td>Aldo Ventures, Inc.</td></tr>
	<tr><td>Ben Clark</td><td>Rustici Software</td></tr>
	<tr><td>Bill McDonald</td><td>Boeing</td></tr>
	<tr><td>Brian J. Miller</td><td>Rustici Software</td></tr>
	<tr><td>Chad Udell</td><td>Float Mobile Learning</td></tr>
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

<a name="reqparticipants"/> 

#### 2.2.2 <s>Requirements Gathering Participants</s> 要求仕様収集への貢献者

<s>
In collection of requirements for the Experience API, many people and organizations provided invaluable feedback to the Sharable Content Object Reference Model (SCORM®), distributed learning efforts, and learning technology efforts in general.  While not an exhaustive listing, the white papers gathered in 2008 by the Learning Education and Training Standards Interoperability (LETSI) group, the Rustici Software _UserVoice_ website, one-on-one interviews and various blogs were important sources from which requirements were gathered for the Experience API specification.
</s>

xAPI の要求の収集において、多くの人々や組織から、SCORM®、分散学習、および学習テクノロジ一般について、個別のフィードバックを得ることができた。全てを挙げることはできないが、学習教育研修システムの相互運用性 (LESTI) グループによって 2008 年にまとめられたホワイトペーパー、Rustici Software 社の _UserVoice_ ウェブサイト、個別のインタビュー、およびさまざまなブログ記事は、xAPI の仕様をまとめるための重要な情報源となった。

<a name="readingguidelines"/> 

### 2.3 <s>Reading Guidelines for the Non-Technically Inclined</s> 技術に詳しくない人への読み方ガイドライン

<s>
This is a definitive document which describes how the Experience API is to be implemented across a variety of systems. It is a technical document authored specifically for individuals and organizations implementing this technology with the intent of such individuals developing interoperable tools, systems and services that are independent of each other and interoperable with each other. 
</s>

本文書は、さまざまなシステムに対して、xAPI の実装方法を示す正式文書である。また、本文書は、この技術を実装する個人と組織に向け、実装者が、独立で相互運用可能なツール、システム、およびサービスを開発できることを目指した技術文書である。

<s>
Whenever possible, the language and formatting used in this document is intended to be _considerate_ of non-technical readers because various tools, systems and services are based on the specification set described below. For this reason, sections that provide a _high-level overview_ of a given facet of the Experience API are labeled **description** or **rationale**. Items in this document labeled as **requirements**, **details** or **examples** are more technical. 
</s>

さまざまなツール、システムおよびサービスが、ここに定義される仕様に基づいて設計されるため、可能な限り、この文書中の文言や形式は、技術に詳しくない人にも_配慮_されている。そのために、xAPI の各部分の_概要説明_には、**説明**または**背景**という見出しをつけている。技術的な部分については、**必要条件**、**詳細**、または**例**という見出しをつけている。

<a name="defintions"/>
 
## 3.0 <s>Definitions</s> 用語の定義

* [<s>Activity</s>アクティビティ](#def-activity)
* [<s>Activity Provider</s>アクティビティプロバイダ (AP)](#def-activity-provider)
* [<s>Actor</s>アクタ (Actor)](#def-actor)
* [<s>Authentication</s>認証 (Authentication)](#def-authentication)
* [<s>Authorization</s>認可 (Authorization)](#def-authorization)
* [<s>Client</s>クライアント](#def-client)
* [<s>Community of Practice</s>実践コミュニティ](#def-community-of-practice)
* [<s>Experience API</s>Experience API (xAPI)](#def-experience-api)
* [<s>Immutable</s>イミュータブル](#def-immutable)
* [<s>Internationalized Resource Idenfier (IRI)</s>IRI (Internationalized Resource Identifier)](#def-iri)
* [<s>Inverse Functional Identifier</s>逆関数識別子 (Inverse Functional Identifier)](#def-inverse-functional-identifier)
* [<s>Learning Management System (LMS)</s>LMS](#def-learning-management-system)
* [<s>Learning Record Store (LRS)</s>LRS](#def-learning-record-store)
* [<s>MUST / SHOULD / MAY</s>～しなければならない (MUST)/～すべきである (SHOULD)/～してもよい (MAY)](#def-must-should-may)
* [<s>Profile</s>プロファイル](#def-profile)
* [<s>Registration</s>登録事項 (Registration)](#def-registration)
* [<s>Representational State Transfer (REST)</s>REST (REpresentational State Transfer)](#def-rest)
* [<s>Service</s>サービス](#def-service)
* [<s>Statement</s>ステートメント](#def-statement)
* [<s>Tin Can API (TCAPI)</s>Tin Can API (TCAPI)](#def-tcapi)
* [<s>Verb</s>動詞 (Verb)](#def-verb)

<a name="def-activity" />

__<s>Activity</s>アクティビティ__: <s>Something with which an Actor interacted. It can be a unit of instruction, experience, or performance that is to be tracked in meaningful combination with a Verb. Interpretation of 
Activity is broad, meaning that Activities can even be tangible Objects.</s>

アクタが相互作用を行った、何らかの対象である。動詞との意味のある組合せによって記録される「教示や経験、成果」の単位となりうる。アクティビティは幅広く解釈でき、またアクティビティは具体物を指す場合もある。

<a name="def-activity-provider" />

__<s>Activity Provider (AP)</s>アクティビティプロバイダ__: <s>The software object that is communicating with the LRS to record information about a learning experience. May be similar to a SCORM package in that it is possible to bundle learning assets with the software object that performs this communication, but an Activity Provider may also be separate from the experience it is reporting about.</s>

LRS と通信し、学習経験についての記録を行うソフトウェアオブジェクト。学習アセットや通信可能なオブジェクトをまとめた SCORM パッケージに似ているが、アクティビティプロバイダは伝達しようとしている経験そのものから切り離されることがある。

<a name="def-actor" />

__<s>Actor</s>アクタ__: <s>An identity or persona of an individual or group tracked using Statements as doing an action (Verb) within an Activity.</s>

個人やグループのアイデンティティや外的側面。それはステートメントを用い、アクティビティの中で動作しながら記録される。

<a name="def-authentication" />

__<s>Authentication</s>認証 (Authentication)__: <s>The concept of verifying the identity of a user or system. Authentication 
allows interactions between the two "trusted" parties.</s>

ユーザやシステムのアイデンティティを確認すること。認証によって、2つの「信頼された」対象どうしの間のやり取りが可能になる。

<a name="def-authorization" />

__<s>Authorization</s>認可 (Authorization)__: <s>The affordance of permissions based on a user or system's role; the process of making one user or system "trusted" by another.</s>

ユーザやシステムの役割に応じ、何らかの利用許可を与えること。それはあるユーザやシステムを他者から信頼されるようにする過程である。

<a name="def-client" />

__<s>Client</s>クライアント__: - <s>Refers to any entity that may interact with an LRS. A Client can be an Activity Provider, reporting tool, an LMS, or another LRS.</s>

LRS とやり取りしうる全ての物。クライアントはアクティビティプロバイダや報告ツール、 LMS や他の LRS にもなりうる。

<a name="def-community-of-practice" />

__<s>Community of Practice</s>実践コミュニティ__: <s>A group, usually connected by a common cause, role or purpose, which operates in a common modality.</s>

共通の動機や役割、目的によって結ばれることの多いグループである。またその集団は共通の様式のもとで行動する。

<a name="def-experience-api" />

__<s>Experience API (xAPI)</s>Experience API (xAPI)__: <s>The API defined in this document, the product of "Project Tin Can". A simple, lightweight way for any permitted Actor to store and retrieve extensible learning records, learner and learning experience profiles, regardless of platform.  </s>

この文書の中で規定される API であり、Tin Can プロジェクトの成果物である。許可を受けたアクタが「拡張可能な学習記録や学習者プロファイル、学習経験プロファイル」を保存し、また取り出すための簡素で軽量な方法である。またそれはプラットフォームに依存しない。

<a name ="def-immutable" />

__<s>Immutable</s>イミュータブル__:  <s>Adjective used to describe things which cannot be changed. With some exceptions, Statements in the xAPI are immutable. This ensures that when Statements are shared between LRSs, multiple copies of the Statement remain
the same.</s>

変わることのない事象を記述するための形容詞。若干の例外を除き、xAPI のステートメントはイミュータブル(不変)である。イミュータブルは、ステートメントが LRS 間で共有されるときに、複製されたステートメントの間の同一性を保つことを保証する。

<a name="def-iri" />

__<s>Internationalized Resource Identifiers (IRI)</s>IRI (Internationalized Resource Identifiers)__: <s>A unique identifier which may be an IRL. In the xAPI, all IRIs should be a full absolute IRI including a scheme. Relative IRIs should not be used. IRLs should be defined within a domain controlled by the person creating the IRL.</s>

IRL でありうる一意な識別子。xAPI では、全ての IRI はスキームを含む完全な絶対 IRI となるべきである。相対 IRI は使われるべきではない。 IRL は IRL を作る者がコントロールするドメインの中で、定義されるべきである。

<a name="def-inverse-functional-identifier" />

__<s>Inverse Functional Identifier</s>逆関数識別子 (Inverse Functional Identifier)__: <s>An identifier which is unique to a particular persona or group. Used to identify Agents and Groups.</s>

特定の人物やグループに対する一意な識別子。行為者やグループを特定するために用いられる。

<a name="def-learning-management-system" />

__<s>Learning Management System (LMS)</s>Learning Management System (LMS)__: <s>"A software package used to administer one or more courses to one or more learners. An LMS is typically a web-based system that allows learners to authenticate themselves, register for courses, complete courses and take assessments" (Learning Systems Architecture Lab definition). In this document the term will be used in the context of existing systems implementing learning standards.</s>

Learning Systems Architecture Lab (訳注: カーネギーメロン大) の定義によれば、LMS は1人以上の学習者に1つ以上の学習コースを提供するためのソフトウェア・パッケージである。 LMS は一般に学習者を認証し、コースに登録し、コースを修了させ、評価するための Web ベースのシステムである。本仕様書においては、標準規格を実装する既存のシステムという文脈のもとで、 LMS という用語を用いる。

<a name="def-learning-record-store" />

__<s>Learning Record Store (LRS)</s>Learning Record Store (LRS)__: <s>A system that stores learning information. Prior to the xAPI most LRSs were Learning Management Systems (LMSs); however this document uses the term LRS to be clear that a full LMS is not necessary to implement the xAPI. The xAPI is dependent on an LRS to function.</s>

学習に関する情報を蓄えるためのシステム。 xAPI が登場する前は、ほとんどの LRS は LMS だった。だが本仕様書で LRS という用語を用いる場合、「 xAPI の実装のためにフル仕様の LMS が必要とは限らない」ということを、強調しておきたい。 xAPI はその機能を果たすために、(訳注: LMS でなく) LRS のほうを必要とする。

<a name="def-must-should-may" />

__<s>MUST / SHOULD / MAY</s>～しなければならない (MUST)/～すべきである (SHOULD)/～してもよい (MAY)__: <s>Three levels of obligation with regards to conformance to the xAPI specification. A system that fails to implement a MUST (or a MUST NOT)requirement is non-conformant. Failing to meet a SHOULD requirement is not a violation of conformity, but goes against best practices. MAY indicates an option, to be decided by the developer with no consequences for conformity.</s>

xAPI 仕様への適合性に関する、3つのレベルでの約束ごと。MUST 条件(または MUST NOT 条件)を満たさないシステムは、 xAPI に適合しない。 SHOULD 条件を満たさないシステムは適合性に反してはいないが、ベストプラクティスには相応しくない。 MAY 条件は適合性を気にせずに開発者が選択できるオプションである。

<a name="def-profile" />

__<s>Profile</s>プロファイル__: <s>A construct where information about the learner or activity is kept, typically in name/document pairs that have meaning to an instructional system component.</s>

一般的に「教育システムの要素として意味を持つ、名前と文書の組」によって学習者やアクティビティの情報を保持する構成体である。

<a name="def-registration" />

__<s>Registration</s>登録事項 (Registration)__: <s>An instance of a learner experiencing a particular Activity.</s>

特定のアクティビティを経験する学習者のインスタンスである。

<a name="def-rest" />

__<s>Representational State Transfer (REST)</s>REST (REpresentational State Transfer)__: <s>An architecture for designing networked web Services. It relies on HTTP methods and uses current web best practices.</s>

ネットワーク化された web サービスを接続するためのアーキテクチャである。 REST は HTTP のメソッドを信頼し、現在の web のベストプラクティスを役立てる。

<a name="def-service" />

__<s>Service</s>サービス__: <s>A software component responsible for one or more aspects of the distributed learning process. An LMS typically combines many services to design a complete learning 
experience.</s>

分散学習環境の一つ以上の局面に責任を持つ、ソフトウェアの構成要素である。一般的に LMS は、学習経験全体をデザインするために複数のサービスを結合させる。

<a name="def-statement" />

__<s>Statement</s>ステートメント__: <s>A simple construct consisting of ```<actor (learner)>``` ```<verb>``` ```<object>```, with ```<result>```, in ```<context>``` to track an aspect of a learning experience. A set of several Statements may be used to track complete details about a learning experience.</s>

学習経験の一局面を記録する「文脈」において、「アクタ(学習者)、動詞、オブジェクト」の3つ組からなり「結果」を有する、単純な構成体である。いくつかのステートメントの組は、学習経験に関する完全な詳細情報を記録するために使われうる。

<a name="def-tcapi"/>

__<s>Tin Can API (TCAPI)</s>Tin Can API (TCAPI)__: <s>The previous name of the API defined in this document, often used in informal references to the Experience API.</s>

本仕様書で定義される API の、以前の名称である。 xAPI へのインフォーマルな呼称として用いられる。

<a name="def-verb" />

__<s>Verb</s>動詞 (Verb)__: <s>Defines the action being done by the Actor within the Activity within a Statement. </s>

ステートメント中のアクティビティにおける、アクタの行為を定義するものである。

<a name="statement"/> 

## 4.0 <s>Statement</s> ステートメント
  
<s>The Statement is the core of the xAPI. All learning events are stored as Statements. A Statement is akin to a sentence of the form "I did this".</s>

ステートメントは xAPI の中心概念である。全ての学習イベントはステートメントとして記録される。ステートメントは、"I did this" といった文と似た構造を持つ。


<a name="stmtprops"/>

### 4.1 <s>Statement Properties</s> ステートメントプロパティ

<s>Actor, Verb, and Object are required, all other properties are optional. Properties can occur in any order, but are limited to one use each. Each property is discussed below.  
</s>

アクタ、動詞、および目的語は必須で、それ以外のプロパティは任意である。プロパティの順序は自由であるが、それぞれ一度しか指定できない。以下に、各プロパティを示す。


<table>
	<tr><th><s>Property</s>プロパティ</th><th><s>Type</s>タイプ</th><th><s>Description</s>説明</th></tr>
	<tr><td>id</td><td>UUID</td>
	<td><s>UUID assigned by LRS if not set by the Activity Provider.</s>アクティビティプロバイダが設定しない場合に、LRS によって割り当てられた UUID。</td></tr>
	<tr><td><a href="#actor">actor</a></td><td>Object</td>
	<td><s>Who the Statement is about, as an <a href="#agent">Agent</a> or <a href="#group">Group</a> Object. Represents the "I" in "I Did This".</s>ステートメントが誰に関するものか（<a href="#agent">Agent</a> や <a href="#group">Group</a> として）。"I Did This" の中の "I" に対応。</td></tr>
	<tr><td><a href="#verb">verb</a></td><td>Object</td>
	<td><s>Action of the Learner or Team Object. Represents the "Did" in "I Did This".</s>学習者やチームオブジェクトの行う行為。"I Did This" の "Did" に相当。</td></tr>
	<tr><td><a href="#object">object</a></td><td>Object</td>
	<td><s>Activity, Agent, or another Statement that is the Object of the Statement. Represents the "This" in "I Did This". Note that Objects which are provided as a value for this field should include an "objectType" field. If not specified, the Object is assumed to be an Activity.</s>
	ステートメントの目的語となる アクティビティ、エージェント、または別のステートメント。"I Did This" の "This" に相当。この項目の値として提供される目的語には "objectType" フィールドを含むべきであることに注意。指定しない場合は目的語はアクティビティであるとみなされる。</td></tr>
	<tr><td><a href="#result">result</a></td><td>Object</td>
	<td><s>Result Object, further details representing a measured outcome relevant to the specified Verb.</s>
	動詞に関する測定結果を示す結果オブジェクト。
</td></tr>
	<tr><td><a href="#context">context</a></td><td>Object</td>
	<td><s>Context that gives the Statement more meaning. Examples: a team the Actor is working with, altitude at which a scenario was attempted in a flight simulator.</s>
	ステートメントに意味を補う文脈情報。例：アクタが所属するチームの情報。フライトシミュレータにおいて、あるシナリオが実行されたときの高度の情報。</td></tr>
	<tr><td><a href="#timestamp">timestamp</a></td><td>Date/Time</td>
	<td><s>Timestamp (Formatted according to <a href="https://en.wikipedia.org/wiki/ISO_8601#Combined_date_and_time_representations">ISO 8601</a>) of when the events described within this Statement occurred. If not provided, LRS should set this to the value of "stored" time.</s>
	このステートメントで示されたイベントの発生時刻を示すタイムスタンプ（<a href="https://en.wikipedia.org/wiki/ISO_8601#Combined_date_and_time_representations">ISO 8601</a> 形式に従う）。指定されない場合、LRS は "stored" のタイムスタンプをここに設定すべきである。
	</td></tr>
	<tr><td><a href="#stored">stored</a></td><td>Date/Time</td>
	<td><s>Timestamp (Formatted according to <a href="https://en.wikipedia.org/wiki/ISO_8601#Combined_date_and_time_representations">ISO 8601</a>) of when this Statement was recorded. Set by LRS.</s>
	このステートメントが記録された時刻を示すタイムスタンプ（<a href="https://en.wikipedia.org/wiki/ISO_8601#Combined_date_and_time_representations">ISO 8601</a> 形式に従う）。LRS によって設定される。
	</td></tr>
	<tr><td><a href="#authority">authority</a></td><td>Object</td>
	<td><s>Agent who is asserting this Statement is true. Verified by the LRS based on authentication, and set by LRS if left blank.</s>
	このステートメントが正しいものであると主張する Agent を示す。LRS の認証機構により確認され、指定がない場合は LRS によって設定される。
	</td></tr>
	<tr><td><a href="#version">version</a></td><td>Version</td>
	<td><s>The Statement’s associated xAPI version, formatted according to <a href="http://semver.org/spec/v1.0.0.html">Semantic Versioning 1.0.0</a>.</s>
	<a href="http://semver.org/spec/v1.0.0.html">セマンティックバージョニング 1.0.0</a> 形式で示したステートメントの xAPI バージョン。
	</td></tr>
	<tr>
		<td><a href="#attachments">attachments</a></td>
		<td>Array of attachment Objects</td>
	    <td><s>Headers for attachments to the Statement</s>ステートメントに対する添付文書のヘッダー。</td>
	</tr>
</table>  
<s>Aside from (potential or required) assignments of properties during LRS processing ("id", "authority", "stored", "timestamp", "version") Statements are immutable. Note that the content of Activities that are referenced in Statements is not considered part of the Statement itself. So while the Statement is immutable, the Activities referenced　by that Statement are not. This means a deep serialization of a Statement into JSON will change if the referenced Activities change (see the
[Statement API's](#stmtapi) "format" parameter for details).  </s>

LRS によりプロパティ（"id", "authority", "stored", "timestamp", "version") が割り当てられる場合を除き、ステートメントは不変である。ただし、ステートメント中で参照されているアクティビティの内容は、ステートメントそのものの一部とはみなさないことに注意が必要である。よって、ステートメントは不変だが、ステートメントによって参照される アクティビティは不変ではない。これは、参照されるアクティビティが変更された時、ステートメントのディープコピーによって生成される JSON も変更されることを意味する（ステートメント API の "format" パラメータ参照）。

<s>An example of the simplest possible Statement using all properties that MUST or SHOULD be used:  </s>

必須または推奨とされる全てのプロパティを用いる最も簡素なステートメントの例。


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
<s>See [Appendix D: Example Statements](#AppendixD) for more examples. </s>
[Appendix D: ステートメントの例](#AppendixD) 参照

<a name="stmtid"/> 

#### 4.1.1 <s>id</s> id (識別子) 

###### <s>Description</s>説明

<s>A UUID (see [RFC 4122](http://www.ietf.org/rfc/rfc4122.txt)　for requirements, and the UUID must be in standard string form).</s>

UUID（仕様は [RFC 4122](http://www.ieft.org/rfc/rfc4122.txt) 参照。UUID は標準的な文字列形式でなければならない）

###### <s>Requirements</s>必要条件

* <s>Ids MUST be generated by the LRS if a Statement is received without an id.</s>受信ステートメントに ID が指定されていなかった場合、LRS が ID を生成しなければならない。
* <s>Ids SHOULD be generated by the Activity Provider.</s>ID はアクティブティプロバイダによって生成されるべきである。

<a name="actor"/>

#### 4.1.2 <s>Actor</s> Actor (アクタ)  

###### <s>Description</s>説明
<s>A mandatory Agent or Group Object.</s>

必須の Agent または Group オブジェクト。

<a name="agent"/>

##### 4.1.2.1 <s>When the Actor ObjectType is Agent</s> アクタのオブジェクト型が Agent の時
###### <s>Description</s>説明
<s>An Agent (an individual) is a persona or system.</s>

Agent（個人）は、人またはシステムである。


###### <s>Details</s>詳細

* <s>An Agent MUST be identified by one (1) of the four types of Inverse Functional Identifiers (see <a href="#inversefunctional"> 4.1.2.3 Inverse Functional Identifier</a>);</s>Agent は、逆関数識別子（<a href="#inversefunctional"> 4.1.2.3 逆関数識別子</a> 参照）の４つのタイプの１つによって定義されなければならない。
* <s>An Agent MUST NOT include more than one (1) Inverse Functional Identifier;</s>Agent に、１つを超える逆関数識別子を設定してはならない。
* <s>An Agent SHOULD NOT use Inverse Functional Identifiers that are also used as a Group identifier.</s>Agent は Group 識別子としても使われている逆関数識別子を使うべきではない。


<s>The table below lists the properties of Agent Objects.</s>

Agent オブジェクトのプロパティを以下の表に示す。

<table border ="1">
	<tr><th><s>Property</s>プロパティ</th><th><s>Type</s>タイプ</th><th><s>Description</s>説明</th><th><s>Required</s>必須</th></tr>
	<tr><td>objectType</td><td>string</td><td><s>"Agent". This property is optional except when the Agent is used as a Statement's Object.</s>
	"Agent"。Agent が目的語の場合は必須である。
	</td><td>no</td></tr>
	<tr><td>name</td><td>String</td><td><s>Full name of the Agent.</s>Agent のフルネーム。</td><td>no</td></tr>
	<tr><td colspan="2"><s>see <a href="#inversefunctional"> 4.1.2.3 Inverse Functional Identifier</a></s><a href="#inversefunctional"> 4.1.2.3 逆関数識別子</a>参照</td>
	    <td><s>An Inverse Functional Identifier unique to the Agent.</s>Agent に固有の逆関数識別子。</s></td><td>yes</td></tr>
</table>


<a name="group"/>

##### 4.1.2.2 <s>When the Actor ObjectType is Group</s> アクタのオブジェクト型が Group の時
###### <s>Description</s>説明

<s>A Group represents a collection of Agents and can be used in most of the same situations an Agent can be used. There are two types of Groups, anonymous and identified.</s>

Group は Agent の集合を意味し、Agent を指定できる状況の大部分において、使用することができる。Group は、匿名と指名の２種類がある。

###### <s>Requirements</s>必要条件

* <s>A system consuming Statements MUST consider each Anonymous Group distinct even if it has an identical set of members.</s>ステートメントを利用するシステムは、複数の匿名グループが同じメンバーで構成されている場合においても、それらを異なるものとして扱わなければならない。
* <s>A system consuming Statements MUST NOT assume that Agents in the 'member' property comprise an exact list of Agents　in a given anonymous or Identified Group.</s>ステートメントを利用するシステムは、'member' プロパティに示された Agent が、与えられた匿名または指名のグループに属する Agent の厳密なリストであるとみなしてはならない。


###### <s>Requirements for Anonymous Groups</s>匿名グループに関する必要条件

* <s>An Anonymous Group MUST include a 'member' property listing constituent Agents.</s>匿名グループは、構成要員である Agent をリスト化した 'member' プロパティを持たなければならない。
* <s>An Anonymous Group MUST NOT contain Group Objects in the 'member' property.</s>匿名グループは、'member' プロパティにグループオブジェクトを含んではならない。
* <s>An Anonymous Group MUST NOT include any Inverse Functional Identifiers.</s>匿名グループは、いかなる逆関数識別子も含んではならない。

###### <s>Requirements for Identified Groups</s>指名グループに関する必要条件

* <s>An Identified Group MUST include exactly one (1) Inverse Functional Identifier.</s>指名グループは、厳密に１つの逆関数識別子を含まなければならない。
* <s>An Identified Group MUST NOT contain Group Objects in the 'member' property.</s>指名グループは、'member' プロパティにグループオブジェクトを含んではならない。
* <s>An Identified Group SHOULD NOT use Inverse Functional Identifiers that are also used as Agent identifiers.</s>指名グループは、Agent の識別子としても使われる逆関数識別子を使うべきではない。
* <s>An Identified Group MAY include a 'member' property listing constituent Agents.</s>指名グループは、構成要員である Agent をリスト化する 'member' プロパティを含んでもよい。


###### <s>Details</s>詳細

<s>An Anonymous Group is used describe a cluster of people where there is no ready identifier for this cluster, e.g. an ad hoc team.</s>

匿名グループは、一時的なチームなど、定められた名称が存在しない人々の集まりを示すために用いられる。

<s>The table below lists all properties of an Anonymous Group.</s>

匿名グループのすべてのプロパティを、下の表に示す。

<table border ="1">
	<tr><th><s>Property</s>プロパティ</th><th><s>Type</s>タイプ</th><th><s>Description</s>説明</th><th><s>Required</s>必須</th></tr>
	<tr><td>objectType</td><td>String</td><td>"Group". </td><td>yes</td></tr>
	<tr><td>name</td><td>String</td><td><s>Name of the group.</s>グループの名称。</td><td>no</td></tr>
	<tr><td>member</td><td>Array of <a href="#agent">Agent Objects</a></td><td><s>The members of this Group.</s>このグループのメンバー。</td><td>yes</td></tr>
</table>

<s>An Identified Group is used to uniquely identify a cluster of Agents.</s>

指名グループは Agent の集合を一意に特定するために用いられる。

<s>The table below lists all properties of an Identified Group.</s>

指名グループのすべてのプロパティを、下の表に示す。

<table border ="1">
	<tr><th><s>Property</s>プロパティ</th><th><s>Type</s>タイプ</th><th><s>Description</s>説明</th><th><s>Required</s>必須</th></tr>
	<tr><td>objectType</td><td>String</td><td>"Group". </td><td>yes</td></tr>
	<tr><td>name</td><td>String</td><td><s>Name of the group.</s>グループの名称。</td><td>no</td></tr>
	<tr><td>member</td><td>Array of <a href="#agent">Agent Objects</a></td><td><s>The members of this Group.</s>このグループのメンバー。</td><td>no</td></tr>
	<tr><td colspan="2"><s>see <a href="#inversefunctional"> 4.1.2.3 Inverse Functional Identifier</a></s><a href="#inversefunctional"> 4.1.2.3 逆関数識別子</a>参照
</td>
	    <td><s>An Inverse Functional Identifier unique to the Group.</s>グループを一意に示す逆関数識別子。
</td><td>yes</td></tr>	
</table>


<a name="inversefunctional">

##### 4.1.2.3 <a>Inverse Functional Identifier</a> 逆関数識別子
###### <s>Description</s>説明

<s>An "Inverse Functional Identifier" is a value of an Agent or Identified Group that is guaranteed to only ever refer to that Agent or Identified Group.</s>

逆関数識別子は、その Agent や指名グループを参照することが、将来にわたり保証されている Agent や指名グループに関する値を示す。

###### <s>Rationale</s>背景

<s>Learning experiences become meaningless if they cannot be attributed to identifiable　individuals and/or groups. In an xAPI Statement this is accomplished with a set of　Inverse Functional Identifiers loosely inspired on the widely accepted FOAF principle　(see: <a href="http://xmlns.com/foaf/spec/#term_Agent"> Friend Of A Friend</a>).</s>

もし特定可能な個人やグループなどに関連付けられないのであれば、学習経験記録は意味のないものになってしまう。xAPI ステートメントでは、これを、広く受け入れられている FOAF 原則（<a href="http://xmlns.com/foaf/spec/#term_Agent"> Friend Of A Friend</a> 参照）を参考にした逆関数識別子の組み合わせによって実現する。


###### <s>Details</s>詳細

<s>The table below lists all possible Inverse Functional Identifier properties.</s>

逆関数識別子の取りうる全てのプロパティを以下の表に示す。

<table border ="1">
	<tr><th><s>Property</s>プロパティ</th><th><s>Type</s>タイプ</th><th><s>Description</s>説明</th></tr>
	<tr><td>mbox</td><td>mailto IRI</td><td><s>The required format is "mailto:email address". <br>
	Only email addresses that have only ever been and will ever be assigned to this Agent, but no others, should be used for this property and mbox_sha1sum.</s>
	要求されるフォーマットは "mailto:email address" である。<br>
	この Agent に対して過去、未来を通じて割り当てられたメールアドレスのみを、このプロパティと mbox_sha1sum に利用すべきである。</td></tr>
	<tr><td>mbox_sha1sum</td><td>String</td><td><s>The SHA1 hash of a mailto IRI (i.e. the value of an mbox property). An LRS MAY include Agents with a matching hash when a request is based on an mbox.</s>mailto IRI（例：mbox プロパティの値）の SHA1 ハッシュ値。LRS は、リクエストが mbox に関係する場合は、対応するハッシュ値をもつ Agent を含んでもよい。</td></tr>
	<tr><td>openID</td><td>URI</td><td><s>An openID that uniquely identifies the Agent.</s>Agent を一意に特定する OpenID。</td></tr>
	<tr><td>account</td><td><a href="#agentaccount">Object</a></td><td><s>A user account on an existing system e.g. an LMS or intranet.</s>LMS やイントラネットなどの既存のシステムにおけるユーザーアカウント。</td></tr>	
</table>


<a name="agentaccount"/>

###### <s>Account Object</s>Account オブジェクト

###### <s>Description</s>説明 

<s>
A user account on an existing system, such as a private system (LMS or intranet) or a public system (social networking site).
</s>

非公開のシステム（LMS またはイントラネット）や公開されたシステム（ソーシャルネットワーキングサイト）などの既存システムのユーザーアカウント。


###### <s>Details</s>詳細

* <s>If the system that provides the account Object uses OpenID, the Activity Provider SHOULD use the openID property instead of an account Object.</s>アカウントオブジェクトを提供するシステムが OpenID を利用しているのであれば、アクティビティプロバイダはアカウントオブジェクトではなく、OpenID プロパティを利用すべきである。
* <s>If the Activity Provider is concerned about revealing personally identifiable　information about an Agent or Group, it SHOULD use an opaque account name (for example an　account number) to identify all Statements about a person while maintaining anonymity.</s>アクティビティプロバイダが Agent や Group について、個人を特定可能な情報を公開するのを懸念する場合は、匿名性を保ちつつその人についてのすべてのステートメントを識別可能にするために、意味を持たないアカウント名（例：アカウント番号）を利用すべきである。

<s>The table below lists all properties of Account Objects.</s>

Account オブジェクトのすべてのプロパティを以下の表に示す。

<table border ="1">
	<tr><th><s>Property</s>プロパティ</th><th><s>Type</s>タイプ</th><th><s>Description</s>説明</th></tr>
	<tr><td>homePage</td><td>IRL</td><td><s>The canonical home page for the system the account is on. This is based on FOAF's accountServiceHomePage.</s>アカウントが利用されているシステムの正式のホームページ。これは、FOAF の accountServiceHomePage に基づく。</td></tr>
	<tr><td>name</td><td>String</td><td><s>The unique id or name used to log in to this account. This is based on FOAF's accountName.</s>
	このアカウントにログインするためのユニーク ID またはアカウント名。これは FOAF の accountName に基づく。</td></tr>
</table>


###### <s>Example</s>例

<s>This example shows an Agent identified by an opaque account:</s>

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

<a name="verb"/>

#### 4.1.3 <s>Verb</s> Verb (動詞)

###### <s>Description</s>説明
<s>The Verb defines the action between Actor and Activity.</s>

動詞はアクタとアクティビティとの間の行動を定義する。

###### <s>Rationale</s>背景

<s>
The Verb in an xAPI Statement describes the action performed during the learning experience. The xAPI does not specify any particular Verbs. (With one exception, namely the reserved Verb <a href="#voided">'http://adlnet.gov/expapi/verbs/voided'</a>). Instead, it defines how to create Verbs so that communities of practice can establish Verbs meaningful to their members and make them available 
for use by anyone. A predefined list of Verbs would be limited by definition and might not be able to effectively capture all possible future learning experiences. 
</s>

xAPI ステートメント中の動詞は、学習経験中に行われた行動を説明する。xAPI が動詞を特別に定義することはない。(例外として予約動詞 ‘http://adlnet.gov/expapi/verbs/voided’ がある)。その代わりに、xAPI では実践コミュニティが、メンバー間での意思疎通のために動詞を作成し、さらには一般でも利用可能にするように動詞を作成する方法を定義している。あらかじめ定義された動詞をリスト化するという考えには制約があり、将来に亘って可能性のある学習経験全てを効率的に扱うこともできないと考えられる。


###### <s>Requirements</s>必要条件

<s>
Verbs appear in Statements as Objects consisting of an IRI and a set of display names corresponding to multiple languages or dialects which provide human-readable meanings of the Verb. 
</s>

動詞はステートメント中にオブジェクトとして現れ、それは IRI と、動詞に関して人間が理解できる意味を複数の言語や方言に対応させた表示名とからなる。

* <s>The display property MUST be used to illustrate the meaning which is already determined by the Verb IRI.</s>displayプロパティは、動詞IRIにより既に決められた意味を例示するために用いられなければならない。
* <s>A system reading a Statement MUST use the Verb IRI to infer meaning.</s>ステートメントを解釈するシステムは、意味の特定のために 動詞IRI を利用しなければならない。
* <s>The display property MUST NOT be used to alter the meaning of a Verb.</s>display プロパティは、動詞の意味を変えるために利用されてはならない。
* <s>A system reading a Statement MUST NOT use the display property to infer any meaning from the Statement.</s>ステートメントを解釈するシステムは、ステートメントの意味の理解のために display プロパティを利用してはならない。
* <s>A system reading a Statement MUST NOT use the display property for any purpose other than display to a human. Using the display property for aggregation or categorization of Statements is an example of violating this requirement.</s>ステートメントを解釈するシステムは、display プロパティを、人間に対して提示する以外のいかなる用途にも用いてはならない。display プロパティを用いてステートメントを集約したりカテゴリ分けしたりすることは、この必要条件に対する違反の例となる。
* <s>The display property SHOULD be used by all Statements.</s>display プロパティは全てのステートメントに用意されるべきである。
* <s>The IRI contained in the id SHOULD be human-readable and imply the Verb meaning.</s>ID に含まれる IRI は人間が理解できる形で、動詞の意味を示すべきである。

###### <s>Details</s>詳細

<s>The table below lists all properties of the Verb Object.</s>

以下の表に動詞オブジェクトの全てのプロパティを示す。


<table>
	<tr><th><s>Property</s>プロパティ</th><th><s>Type</s>タイプ</th><th><s>Description</s>説明</th></tr>
	<tr>
		<td>id</td>
		<td>IRI</td>
		<td><s>Corresponds to a Verb definition. Each Verb definition corresponds to the meaning of a Verb, not the word. The IRI should be human-readable and contain the Verb meaning.</s>
		動詞の定義を示す。それぞれの動詞の定義は、単語ではなく動詞の意味に対応する。IRI は人間が理解できる形で、動詞の意味を含んでいるべきである。</td>
	</tr>

	<tr>
		<td>display</td>
		<td><a href="#misclangmap"><s>Language Map</s>言語マップ</a></td>
		<td><s>The human readable representation of the 
		Verb in one or more languages. This does not have any impact on the meaning of the Statement, but serves to give a human-readable display of the meaning already determined by the chosen Verb.</s>
		
		一つ以上の言語で示された、人間が理解できる形での動詞の表現。ステートメントが表す意味について全く影響力を持たないが、選択された動詞によって既に決定されている意味を人間が理解できる形で表現する機能を提供する。</td>
	</tr>

</table>

###### <s>Example</s>例

```
{
	"verb" : { 
		"id":"http://www.adlnet.gov/XAPIprofile/ran(travelled_a_distance)", 
		"display":{
			"en-US":"ran",
			"es" : "corrió" 
		} 
	}
}
``` 

<s>The Verb in the example above is included for illustrative purposes only. This is not intended to imply that a Verb with this meaning has been defined with this id. This applies to all example verbs given in this 
specification document, with the exception of the reserved Verb <a href="#voided">'http://adlnet.gov/expapi/verbs/voided'</a>. </s>

上の例での動詞は例示目的でのみ示されている。これは、この意味を持った動詞がこの ID で定義されていることを意味するものではない。この原則は、予約動詞 (‘http://adlnet.gov/expapi/verbs/voided’) を除く、本仕様書のすべての動詞の例について適用される。
			
##### 4.1.3.1 <s>Use in Language and Semantics of Verbs</s> 動詞の言語と意味に関する用法

###### <s>Details</s>詳細
_<s>Semantics</s>意味_

<s>The IRI represented by the Verb id identifies the particular semantics of a word, not the word itself. </s>

Verb ID によって表される IRI は、その単語そのものではなく、単語に関する特定の意味を示す。

<s>For example, the English word "fired" could mean different things depending on context, such as "fired a 
weapon", "fired a kiln", or "fired an employee". In this case, an IRI MUST identify one of these specific meanings, not the word "fired". </s>

例えば、英単語の “fired” は、”銃を撃つ(fired)” や “窯で焼く(fired)”、”従業員を解雇する(fired)” など、文脈に応じて異なる意味を持ち得る。この例においては、IRI は “fired” が単語として持ちうる意味ではなく、それらのうちの特定の１つの意味を示さなければならない。

<s>The display property has some flexibility in tense. While the Verb IRIs are expected to remain in the past tense, if conjugating verbs to another tense (using the same Verb) within the Activity makes sense, it is allowed.</s>

display プロパティでは時制に関してある程度の自由度を残している。動詞 IRI は過去形であることが期待されるが、対象のアクティビティについて（同じ動詞で）異なる時制にしたほうが妥当な場合は、そのようにしてもよい。

_<s>Language</s>言語_

<s>A Verb in the Experience API is an IRI, and denotes a specific meaning not tied to any particular language. </s>

xAPI における動詞は IRI であり、いかなる言語にも依存しない固有の意味を示す。

<s>For example, a particular Verb IRI such as http://example.org/firearms#fire might denote the action of firing a gun, or the Verb IRI http://example.com/فعل/خواندن might denote the action of reading a book. </s>

例えば、http://example.org/firearms#fire のような特定の動詞 IRI は銃を撃つといった行動を意味し、http://example.com/لعف/ندناوخ のような動詞 IRI は本を読むといった行動を意味する。

##### 4.1.3.2 <s>Use in Communities of Practice</s> 実践コミュニティに関する用法

###### <s>Requirements for Communities of Practice</s>実践コミュニティ向けの必要条件

* <s>Anyone establishing a new Verb MUST own the IRI, or MUST have permission from the owner to use it to denote an xAPI Verb;</s>新しい動詞を定義する場合は IRI を所有しているか、xAPI の 動詞を示すために IRI を利用する許可をその所有者から得なければならない。
* <s>Anyone establishing a new Verb SHOULD make a human-readable description of the intended usage of the Verb 
accessible at the IRI.</s>新しい動詞を定義する場合は、動詞の想定される用途についての人間が理解できる定義を、IRI にてアクセス可能にしておくべきである。


###### <s>Requirements for Activity Providers</s>アクティビティプロバイダ向けの必要条件

* <s>Activity Providers SHOULD use a corresponding existing Verb whenever possible.</s>アクティビティプロバイダは、可能な限り既存の対応する動詞を利用すべきである。
* <s>Activity Providers MAY create and use a Verb if no suitable Verb exists.</s>アクティビティプロバイダは、適切な動詞が存在しない場合、動詞を作成し利用してもよい。

###### <s>Details</s>詳細

<s>Communities of practice will, at some point in time, need to establish new Verbs to meet the needs of their constituency.</s>

実践コミュニティでは、その構成員の要求にこたえるために、どこかの段階で新たな動詞を定義する必要が出てくる。

<s>Therefore, it is expected that xAPI generates profiles, lists, and repositories that become centered on Verb 
vocabularies.  ADL is one such organization that is creating a companion document containing Verbs for xAPI.  In fulfillment of the requirements above, a collection of IRIs of recommended Verbs exists.  There are times when Activity Providers may wish to use a different Verb for the same meaning.</s>

そのため、xAPI は動詞の語彙の中心となるプロファイル、リスト、リポジトリ等を作成することが望まれる。ADL もそのような組織の一つとして、xAPI における動詞についての解説文書を制作している。上の要求を満たすために、推奨される動詞の IRI 集が存在する。異なるアクティビティプロバイダ間で、同じ意味に対して、異なる動詞を利用したくなることも想定される。

<a name="object"/>

####4.1.4 Object（目的語）


###### <s>Description</s>説明

<s>The Object of a Statement can be an Activity, Agent/Group, Sub-Statement, or Statement Reference. It is the "this" part of the Statement, i.e. "I did this". </s>

ステートメントにおける目的語は、アクティビティ、エージェント／グループ、サブステートメント、もしくはステートメントの参照などがあり得る。
目的語は、ステートメントにおいて“対象”として表現される部分に当たる。
例えば、“私はこれをした。 ( I did this )”のステートメントでは「これ( this )」にあたる。


<s>Some examples:</S>例：

* <s>The Object is an Activity: "Jeff wrote an essay about hiking."</s>目的語がアクティビティの場合：“ジェフはハイキングに関するエッセイを書いた”

* <s>The Object is an Agent: "Nellie interviewed Jeff."</s>目的語がエージェントの場合：“ネリーはジェフの面談を行った”


* <s>The Object is a Sub-Statement or Statement Reference (different implementations, but similar when human-read): 
"Nellie commented on 'Jeff wrote an essay about hiking.'"</s>目的語がサブステートメントもしくはステートメントの参照の場合（異なる手段ではあるが人が理解できる）：“ジェフはハイキングに関するエッセイを書いた”についてネリーはコメントした。


###### <s>Details</s>詳細

<s>Objects which are provided as a value for this field SHOULD include an "object
>Type" field. If not specified, the objectType is assumed to be "Activity". Other valid values 
are: <a href="#agentasobj">Agent</a>, <a href="#agentasobj">Group</a>, <a href="#substmt">Sub-Statement</a> or [StatementRef](#stmtref)</a>.
The properties of an Object change according to the objectType.</s>

このフィールドの値として提供されるオブジェクトは "objectType" フィールドを持つべきである。指定が無ければ、 "objectType" は "Activity" と認識される。その他の有効な値は、 <a href="#agentasobj">Agent</a>, <a href="#agentasobj">Group</a>, <a href="#substmt">Sub-Statement</a> もしくは [StatementRef](#stmtref)</a> となるオブジェクト のプロパティは、 objectType に応じて変わる。

<a name="activity" />

##### <s>4.1.4.1 When the ObjectType is Activity</s> ObjectType がアクティビティの場合

<s>A Statement may represent an Activity as the Object of the Statement. The following table lists the Object 
properties in this case.</s>

ステートメントは、ステートメントの 目的語としてアクティビティを示すことができる。本ケースにおけるオブジェクトのプロパティは以下の表の通り。

<table>
	<tr><th><s>Property</s>プロパティ</th><th><s>Type</s>タイプ</th></th><th><s>Description</s>説明</th></tr>
	<tr>
		<td>objectType</td>
		<td>String</td>
		<td><s>MUST be "Activity" when present. Optional in all cases.</s>利用する場合は “Activity”を設定しなければならない。　全ての場合においてオプションとなる。

</td>
	</tr>
	<tr>
		<td><a href="#acturi">id</a></td><td>IRI</td>
		<td><s>An identifier for a single unique Activity. Required.</s>一意のアクティビティの識別子。必須。</td>
	</tr>
	<tr>
		<td><a href="#actdef">definition</a></td>
		<td>Object</td>
		<td><s>Optional Metadata, <a href="#actdef">See below</a></s>オプションのメタデータ, <a href="actdef">以下のアクティビティ定義を参照</a>。

</td>
	</tr>
</table>

<a name="actdef" />

##### <s>Activity Definition</s>アクティビティ定義

###### <s>Details</s>詳細

<s>The table below lists the properties of the Activity Definition Object:</s>アクティビティ定義オブジェクト


<table>
	<tr><th><s>Property</s>プロパティ</th><th><s>Type</s>タイプ</th><th><s>Use</s>利用</th><th><s>Description</s>説明</th></tr>
	<tr>
		<td>name</td>
		<td><a href="#misclangmap"><s>Language Map</s>言語マップ</a></td>
		<td><s>Recommended</s>推奨</td>
		<td><s>The human readable/visual name of the Activity</s>可読／可視化したアクティビティの名称</td>
	</tr>
	<tr>
		<td>description</td>
		<td><a href="misclangmap"><s>Language Map</s>言語マップ</a></td>
		<td><s>Recommended</s>推奨</td>
		<td><s>A description of the Activity</s>アクティビティの説明</td>
	</tr>
	<tr>
		<a name="acttype" />
		<td>type</td>
		<td>IRI</td>
		<td><s>Recommended</s>推奨</td>
		<td><s>The type of Activity.</s>アクティビティのタイプ</td>
	</tr>
	<tr>
		<td>moreInfo</td>
		<td>IRL</td>
		<td><s>Optional</s>任意</td>
		<td><s>SHOULD resolve to a document human-readable information about the Activity, which MAY include a way to 'launch' the Activity.</s>アクティビティの「実施」の仕方を含むなど、アクティビティに関する（人が理解できる情報である）文書を指し示すべきである。
		</td>
	</tr>
	<tr>
		<td colspan="4"><s>Interaction properties, See: <a href="#interactionacts">Interaction Activities</a></S>Interaction propertiesについては、 Interaction Activities を参照</td>
	</tr>
	<tr>
		<td>extensions</td>
		<td>Object</td>
		<td><s>Optional</s>任意</td>
		<td><s>A map of other properties as needed (see: <a href="#miscext">Extensions</a>)</s>必要に応じて格納する他のプロパティに関するマップ
			（<a href="#miscext">Extensions</a> 参照）</td>
	</tr>
</table>

__<s>Note</s>注記:__ <s>IRI fragments (sometimes called relative IRLs) are not valid IRIs. As with Verbs, it is recommended that Activity Providers look for and use established, widely adopted, Activity types.</s>	

IRI フラグメント (相対 IRL とも言う) は有効な IRI ではない。また、動詞と同じく、アクティビティプロバイダは、確立され広く適用されているアクティビティタイプを探して利用することが推奨される。

<s>An LRS should update its internal representation of an Activity's definition upon receiving a Statement with the same Activity id, but with a different definition of the Activity from the one stored, but only if it considers the Activity Provider to have the authority to do so.  </s>

LRS は、同じアクティビティ ID のステートメントを受け取った場合で、記録されたものと異なるアクティビティの定義を受信した場合には、内部表現を更新するべきだが、アクティビティプロバイダがその権限を持つ場合に限る。
>

<a name="acturi" />

##### <s>Activity id  </s>アクティビティ ID

###### <s>Requirements for Activity Ids</s>アクティビティ ID の必要条件

* <s>An Activity id MUST be unique.</s>アクティビティ ID は一意でなければならない。
* <s>An Activity id MUST always reference the same Activity.</s>アクティビティ ID は常に同じアクティビティを参照しなければならない。
* <s>An Activity id SHOULD use a domain that the creator is authorized to use for this purpose.</s>アクティビティ ID は作成者がこの目的のために許可されたドメインを使用すべきである。
* <s>An Activity id SHOULD be created according to a scheme that makes sure all Activity ids within that domain remain unique.</s>アクティビティ ID はそのドメイン内の全てのアクティビティ IDが一意になるようなスキームで作成されるべきである。
* <s>An Activity id MAY point to metadata or the IRL for the Activity.</s>アクティビティ ID はメタデータやアクティビティのIRLを示してもよい。


###### <s>Requirements for the LRS</s>LRS の必要条件

* <s>An LRS MUST ignore any information which indicates two authors or organizations may have used the same Activity id.</s>2人の著者または２つの組織が同じアクティビティ ID を使用している可能性がある場合、 LRS は全ての情報を無視しなければならない。
* <s>An LRS MUST NOT treat references to the same id as references to different Activities.</s>LRS は同じ ID への複数の参照を、異なるアクティビティへの複数の参照として取り扱ってはならない。

* <s>Upon receiving a Statement with an Activity Definition that differs from the one stored, an LRS SHOULD decide whether it considers the Activity Provider to have the authority to change the definition and SHOULD update the stored Activity Definition accordingly if that decision is positive.</s>格納されたものとは異なるアクティビティ定義でステートメントを受信した場合、 LRS はアクティビティプロバイダが定義を変更する権限を持っているかを判断すべきで、もし持っていると判断した場合は、記録されたアクティビティの定義を更新するべきである。

* <s>An LRS MAY accept small corrections to the Activity’s definition. For example, it would be okay for an LRS to accept spelling fixes, but it may not accept changes to correct responses.</s>LRS は、アクティビティの定義に関する小修正を受け入れてもよい。例えば、スペルの訂正である。但し、正解を変更してはならない。

###### <s>Requirements for the Activity Provider</s>アクティビティプロバイダの必要条件

* <s>An Activity Provider MUST ensure that Activity ids are not re-used across multiple Activities.</s>アクティビティプロバイダは、アクティビティ ID が複数のアクティビティで重複利用されないことを保証しなければならない。

* <s>An Activity Provider MUST only generate states or Statements against a certain Activity id that are compatible and consistent with states or Statements previously stored against the same id.</s>アクティビティプロバイダは、以前に同じ ID に対して記録された状態またはステートメントと一致し、互換性のあるアクティビティ ID に対してのみ、その状態またはステートメントを生成しなければならない。

* <s>An Activity Provider MUST NOT allow new versions (i.e. revisions or other platforms) of the Activity to break compatibility.</s>アクティビティプロバイダは、アクティビティのバージョン更新時（リビジョンや他のプラットフォームによる）に互換性を崩させてはならない。

	
###### <s>Details</s>詳細

<s>If it were possible to use the same id for two different Activities, the validity of Statements about these Activities could be questioned. This means an LRS may never treat (references to) the same Activity id as belonging to two different Activities, even if it thinks this was intended. Namely, when a conflict with another system occurs, it’s not possible to determine the intentions. </s>

2つの異なるアクティビティに同じ ID を使用するが可能であった場合、これらのアクティビティに関するステートメントの妥当性は疑問視される。これは、故意にそうされていたとしても、１つのアクティビティ ID を使用して2つの異なるアクティビティを区別できないを意味する。すなわち、他のシステムと矛盾が生じた場合、それが意図的かどうかを究明するはできない。

<a name="actmeta" />

##### <s>Activity Metadata</s>アクティビティメタデータ

###### <s>Requirements</s>必要条件

* <s>If an Activity IRI is an IRL, an LRS SHOULD attempt to GET that IRL, and include in HTTP　headers: "Accept: application/json, */*". This SHOULD be done as soon as practical after the LRS　first encounters the Activity id.</s>もしアクティビティの IRI が IRL だった場合、 "Accept: application/json, */*" を HTTP ヘッダーに入れて、その IRL の GET を試みるべきである。これは LRS がアクティビティ ID を検知したら直ぐに実施しなければならない。


* <s>Upon loading JSON which is a valid Activity Definition from an IRL used as an Activity id, an LRS SHOULD incorporate the loaded definition into its internal definition for that Activity, while preserving names or definitions not included in the loaded definition.</s>アクティビティ ID として使用した IRL から有効なアクティビティ定義の JSON をロードした際、LRS はロードした定義にない名前や定義を残しながら、ロードした定義をアクティビティの内部的な定義に組み込むべきである。

* <s>An Activity with an IRL identifier MAY host metadata using the <a href="#actdef">Activity Definition</a> JSON format which is used in Statements, with a Content-Type of "application/json"</s>IRL 識別子を持つアクティビティは、ステートメントで利用される <a href="#actdef">Activity Definition</a> JSON フォーマットを用いて Content-Type を "application/json" に設定したメタデータを提供してもよい。

* <s>Upon loading any document from which the LRS can parse an Activity Definition from an IRL used as an Activity id, an LRS MAY consider this definition when determining　its internal representation of that Activity's　definition.</s>アクティビティ定義の内部表現を決定する際に LRS はアクティビティ ID として使われる IRL からアクティビティ定義を解析することができ、そこから任意のドキュメントを読み込むときに、 LRS はこの定義を考慮することができる。

<a name="interactionacts" />

##### <s>Interaction Activities  </s>インタラクション　アクティビティ

###### <s>Rationale</s>背景

<s>Traditional e-learning has included structures for interactions or assessments. As a way to allow these practices and structures to extend Experience API's utility, this specification includes built-in definitions for interactions, which borrows from the SCORM 2004 4th Edition Data Model. These definitions are intended to provide a simple and familiar utility for recording interaction data. These definitions are simple to use, and consequently limited. It is expected that communities of 
practice requiring richer interactions definitions will do so through the use of extensions to an Activity's type and definition.  </s>

従来の eラーニングはインタラクションとアセスメントが組み込まれた構造をもっている。それらの実情と構造を xAPI にも拡張するために、本仕様では SCORM 2004 第4版のデータモデルを参考にしたインタラクションの定義を含んでいる。これらの定義はインタラクションのデータを記録するためのシンプルで使い慣れた仕組みを提供することを目的としている。これらの定義はシンプルで使いやすいが、制約もある。より高機能なインタラクションの定義が必要な実践コミュニティは、アクティビティのタイプと定義の拡張を利用することによりそれを実現できる。


###### <s>Requirements</s>必要条件

* <s>Interaction Activities MUST have a valid interactionType.</s>インタラクションアクティビティには、有効な interactionType が含まれていなければならない

* <s>Interaction Activities SHOULD have the Activity type http://adlnet.gov/expapi/activities/cmi.interaction".</s>インタラクションアクティビティは、アクティビティタイプとして、http://adlnet.gov/expapi/activities/cmi.interaction を持つべきである。

* <s>An LRS, upon consuming a valid interactionType, MAY validate the remaining properties as specified in the table below and MAY return HTTP 400 "Bad Request" if the remaining properties are not valid for the Interaction Activity.</s>有効な interactionType を受信した場合、 LRS は残りのプロパティを下記の表に沿って確認し、もし残りのプロパティがインタラクションアクティビティに対して有効でない場合は、HTTP 400 "Bad Request" を返してもよい。

###### <s>Details</s>詳細

<s>The table below lists the properties for Interaction Activities.</s>

以下の表はインタラクションアクティビティのプロパティを表す。

<table>
	<tr><th><s>Property</s>プロパティ</th><th><s>Type</s>タイプ</th><th><s>Description</s>説明</th></tr>
	<tr>
		<td>interactionType</td>
		<td>String</td>
		<td><s>As in "cmi.interactions.n.type" as defined in the SCORM 2004 4th Edition Run-Time Environment.</s>SCORM2004 4th 版のRun-Time Environmentで定義している"cmi.interactions.n.type"</td>
	</tr>
	<tr>
		<td>correctResponsesPattern</td>
		<td>An array of strings</td>
		<td><s>Corresponds to "cmi.interactions.n.correct_responses.n.pattern" as defined in the SCORM 2004 4th Edition Run-Time Environment, where the final <em>n</em> is the index of the array.</s>SCORM2004 4th 版の Run-Time Environment で定義している" cmi.interactions.n.correct_responses.n.pattern "に対応し、最後の n は配列のインデックスとなる</td>
	</tr>
	<tr>
		<td>choices | scale | source | target | steps</td>
		<td>Array of interaction components</td>
		<td><s>Specific to the given interactionType (<a href="#interactionType">see below</a>).</s>interactionType (後述参照)にて特定</td>
	</tr>
</table>  

##### <s>Interaction Components  </s>インタラクションのコンポーネント

###### <s>Requirements</s>必要条件

* <s>Within an array of interaction components, all id values MUST be distinct.</s>インタラクションコンポーネントの配列中で、全ての ID は異なる値でなければならない。

* <s>An interaction component's id value SHOULD not have whitespace.</s>インタラクションコンポーネントの ID には空白があってはならない

###### <s>Details</s>詳細

<s>Interaction components are defined as follows: </s> 

インタラクションコンポーネントの定義は以下の通り

<table>
	<tr><th><s>Property</s>プロパティ</th><th><s>Type</s>タイプ</th><th><s>Description</s>説明</th></tr>
	<tr>
		<td>id</td>
		<td>String</td>
		<td><s>A value such as used in practice for "cmi.interactions.n.id" as
            defined in the SCORM 2004 4th Edition Run-Time Environment</s>SCORM2004 4th 版の Run-Time Environment で定義している " cmi.interactions.n.id" で実際に使用する値</td> 
	<tr>
		<td>description</td>
		<td><a href="#misclangmap"><s>Language Map</s>言語マップ</a></td>
		<td><s>A description of the interaction component 
			(for example, the text for a given choice in a multiple-choice interaction)</s>インタラクションコンポーネントの表現（例えば、複数選択インタラクションで選択されたテキスト）</td>

	</tr>
</table>

<a name="interactionType" />

<s>The following table shows the supported lists of CMI interaction components for an interaction Activity with the given interactionType.</s>

インタラクションアクティビティにおける interactionType でサポートしている CMI インタラクションコンポーネントは以下の表の通り。

<table>
	<tr><th><s>interactionType</s>インタラクションタイプ</th><th><s>supported component list(s)</S>サポートしているコンポーネントのリスト</th><tr>
	<tr><td>choice, sequencing</td><td>choices</td></tr>
	<tr><td>likert</td><td>scale</td></tr>
	<tr><td>matching</td><td>source, target</td></tr>
	<tr><td>performance</td><td>steps</td></tr>
	<tr><td>true-false, fill-in, numeric, other</td><td>[No component lists defined]</td></tr>
</table>

<s>See [Appendix C](#AppendixC) for examples of Activity Definitions for each of the cmi.interaction types.</s>

各cmi.interactionタイプのアクティビティ定義は [Appendix C](#AppendixC) のサンプルを参照。

<a name="agentasobj" />

##### 4.1.4.2 <s>When the "Object" is an Agent or a Group</s> 目的語が単体のエージェントもしくはグループだった場合

###### <s>Requirements</s>必要条件

* <s>Statements that specify an Agent or Group as an Object MUST specify an 'objectType' property. </s>単体のエージェントもしくはグループを参照しているステートメントは必ず 'objectType' プロパティを明示しなくてはならない

<s>See [Section 4.1.2 Actor](#actor) for details regarding Agents.  </s>

エージェントの詳細については Section 4.1.2 Actor (アクタ） を参照

<a name="stmtasobj" />

##### 4.1.4.3 <s>When the "Object" is a Statement</s> 目的語がステートメントだった場合

###### <s>Rationale</s>背景

<s>There are two possibilities for using a Statement as an Object.  First, an Object can take on the form of a Statement that already exists by using a Statement Reference. A common use case for Statement References is grading or commenting on an experience that could be tracked as an independent event.  The special case of voiding a Statement would also use a Statement Reference.
Second, an Object can be brand new Statement by using a Sub-Statement.  A common use case for Sub-Statements would be any experience that would be misleading as its own Statement. Each type is defined below.</s>

目的語としてステートメントを取るのには、２つの場合がある。第一に、目的語は、既に存在するステートメントの参照を用いることにより、ステートメントの形をとることができる。ステートメント参照の一般的な例としては、独立のイベントとして扱うことができる経験に対する評価やコメントの付与があげられる。第二に、サブステートメントを利用することにより、目的語は独立したステートメントの形をとることができる。サブステートメントの一般的な利用法は、単独のステートメントでは誤解されるような経験についてである。それぞれのタイプの定義は以下の通り。


<a name="stmtref" />

##### <s>Statement References</s>ステートメント参照


###### <s>Description</s>説明
<s>A Statement Reference is a pointer to another pre-existing Statement.</s>

ステートメント参照は、他の既存ステートメントへのポインタである。


###### <s>Requirements</s>必要条件

* <s>A Statement Reference MUST specify an "objectType" property with the value "StatementRef".</s>ステートメント参照は、objectType プロパティとして "StatementRef" を指定しなければならない。

* <s>A Statement Reference MUST set the "id" property to the UUID of a Statement.</s>ステートメント参照は、ステートメントの UUID を "id" プロパティにセットしなければならない。


<s>The table below lists all properties of a Statement Reference Object:</s>

以下の表では、ステートメント参照オブジェクトの全プロパティを一覧表示している

<table border ="1">
	<tr><th><s>Property</s>プロパティ</th><th><s>Type</s>タイプ</th><th><s>Description</s>説明</th></tr>
	<tr><td>objectType</td><td>String</td><td><s>In this case, MUST be "StatementRef".</s>この場合、 "StatementRef" としなければならない</td></tr>
	<tr><td>id</td><td>UUID</td><td><s>The UUID of a Statement. </s>ステートメントの UUID
	</td></tr>
</table>

###### <s>Example</s>例

<s>Assuming that some Statement has already been stored with the id 8f87ccde-bb56-4c2e-ab83-44982ef22df0, the following example shows how a comment could be issued on the original Statement, using a new Statement:</s>  

あるステートメントが ID 8f87ccde-bb56-4c2e-ab83-44982ef22df0 として既に記録されていると仮定したとき、以下の例では、どの様にして新しいステートメントで元のステートメントにコメントを発行するかを示している。

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

<a name="substmt" />

##### <s>Sub-Statements</s>サブステートメント

<s>A Sub-Statement is a new Statement included as part of a parent Statement.</s>

サブステートメントは、親ステートメントの一部として含まれる新しいステートメントである



###### <s>Requirements</s>必要条件

* <s>A Sub-Statement MUST specify an "objectType" property with the value "SubStatement".</s>サブステートメンは、"objectType" プロパティで"SubStatement"として明示しなくてはならない
* <s>A Sub-Statement MUST be validated as a Statement in addition to other Sub-Statement requirements.</s>サブステートメントは、他のサブステートメントの必要要件に加えて、ステートメントとして評価されなければならない
* <s>A Sub-Statement MUST NOT have the "id", "stored", "version" or "authority" properties.</s>サブステートメントは、"id", "stored", "version" or "authority"プロパティを持ってはならない
* <s>A Sub-Statement MUST NOT contain a Sub-Statement of their own i.e. cannot be nested.</s>サブステートメント内に、サブステートメントを含んではならない。すなわち、入れ子にはできない。


###### <s>Example</s>例

<s>One interesting use of Sub-Statements is in creating Statements of intention. For example, using Sub-Statements we can create Statements of the form ```"<I> <planned> (<I> <did> <this>)"```  to indicate that we've planned to take some action. The concrete example that follows logically states that "I planned to visit 'Some Awesome Website'". </s>

サブステートメントの興味深い使い方の一つは、意図を示すステートメントの構築である。例えば、サブステートメントを使って、何らかのアクションを起こそうとしたことを示す目的で ```"<I> <planned> (<I> <did> <this>)"``` といった形式のステートメントを作成することができる。次の具体例では、 "I planned to visit 'Some Awesome Website'" を示している。

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

<a name="result" />

#### 4.1.5 <s>Result</s> Result（結果）

###### <s>Description</s>説明
<s>An optional field that represents a measured outcome related to the Statement in which it is included.</s>

ステートメントの取込み結果を計るためのオプションフィールド

###### <s>Details</s>詳細
<s>The following table contains the properties of the Results Object.</s>

以下の表には結果オブジェクトのプロパティが一覧表示されている



<table border="1">
<tr><th><s>Property</s>プロパティ</th><th><s>Type</s>タイプ</th><th><s>Description</s>説明</th></tr>
<td>score</td>
<td>Object</td>
<td><s>The score of the Agent in relation to the success or quality of the experience. <a href ="#Score">See: Score</a></a></s> エージェントのスコア。<a href ="#Score">Score</a></a> を参照</td>

</tr>
<tr><td>success</td><td>Boolean</td><td><s>Indicates whether or not the attempt on the Activity was successful.</s>アクティビティの試みが成功したかどうかを表す</td>
</tr>
<tr><td>completion</td><td>Boolean</td><td><s>Indicates whether or not the Activity was completed.</s>アクティビティが完了したかどうかを表す</td>
</tr>
<tr>
<td>response</td><td>String</td><td><s>A response appropriately formatted for the given Activity.</s>アクティビティのために適切にフォーマットされたレスポンス</td>
</tr>
<tr>
<td>duration</td><td><s>Formatted according to <a href="https://en.wikipedia.org/wiki/ISO_8601#Durations">ISO 8601</a>
with a precision of 0.01 seconds</s>ISO 8601 に基づいた	ステートメントが発生してからの経過時間
	0.01秒の精度の
	フォーマット
</td><td><s>Period of time over which the Statement occurred.</s>ステートメントが発生してからの経過時間</td>
</tr>
<tr>
<td>extensions</td><td>Object</td><td><s>A map of other properties as needed.
<a href="#miscext">See: Extensions</a></s>必要に応じて追加される他のプロパティを表すマップ。
		Extensions を参照
</td>
</tr>
</table> 

<a name="Score" />

##### 4.1.5.1 <s>Score</s> スコア（Score)

###### <s>Description</s>説明
<s>An optional numeric field that represents the outcome of a graded Activity achieved by an Agent.</s>

エージェントによって達成された、類別されたアクティビティの結果を表わすオプションの数字フィールド

###### <s>Requirements</s>必要条件

* <s>The Score Object SHOULD include 'scaled' if a logical percent based score is known.</s>論理的なパーセント基準のスコアが既知の場合は、スコアオブジェクトは 'scaled' を組み込むべきである。

* <s>The Score Object SHOULD NOT be used for scores relating to progress or completion.  Consider using an extension from an extension profile instead.</s>スコアオブジェクトは、進捗もしくは完了に関連するスコアのために使用すべきではない。代わりに拡張プロファイルの拡張機能の利用を検討すること。

###### <s>Details</s>詳細

<s>The table below defines the Score Object. </s>

以下の表は、スコアオブジェクトの定義である。

<table border ="1">
	<tr><th><s>Property</s>プロパティ</th><th><s>Type</s>タイプ</th><th><s>Description</s>説明</th></tr>
	<tr><td>scaled</td><td><s>Decimal number between -1 and 1, inclusive</s>-1から1までの十進数</td><td><s>Cf. 'cmi.score.scaled' in SCORM 2004 4th Edition</s>SCORM2004 4th 版の 'cmi.score.scaled' を参照</td></tr>
	<tr><td>raw</td><td><s>Decimal number between min and max (if present, otherwise unrestricted), inclusive</s> min と max の間の十進数	'cmi.score.raw'を参照
	（現状、そうでなければ無制限）</td><td><s>Cf. 'cmi.score.raw'</s>'cmi.score.raw' を参照</td></tr>
	<tr><td>min</td><td><s>Decimal number less than max (if present)</s>maxよりも小さい十進数 </td><td><s>Cf. 'cmi.score.min'</s>'cmi.score.min' を参照</td></tr>
	<tr><td>max</td><td><s>Decimal number greater than min (if present)</s>minよりも大きい十進数 </td><td><s>Cf. 'cmi.score.max'</s>'cmi.score.max' を参照</td></tr>
</table>

<a name="context"/>

#### 4.1.6 <s>Context</s>Context (文脈)

###### <s>Description</s>説明
<s>An optional field that provides a place to add contextual information to a Statement. All properties are optional.</s>

文脈依存の情報をステートメントに付加するための任意のフィールド。全てのプロパティは任意である。

###### <s>Rationale</s>背景
<s>
The "context" field provides a place to add some contextual information to a Statement. It can store information such as the instructor for an experience, if this experience happened as part of a team Activity, or how an experience fits into some broader activity.
</s>

context フィールドは文脈依存の情報をステートメントに付加する機会を提供する。
それは経験が集団活動の一部として行われた場合には、その経験の教授者の名前や、経験がより大きな活動にどのように組み込まれるか、といった情報を記録することができる。

###### <s>Requirements</s>必要条件

<s>

 * The revision property MUST NOT be used if the Statement's Object is an Agent or Group.
 * The platform property MUST NOT be used if the Statement's Object is an Agent or Group.
 * The language property MUST NOT be used if not applicable or unknown.
* The revision property SHOULD be used to track fixes of minor issues (like a spelling error).
* The revision property SHOULD NOT be used if there is a major change in learning objectives,
pedagogy, or assets of an Activity. (Use a new Activity id instead).

</s>

* ステートメントの目的語がエージェントやグループであるなら、revision プロパティは使用してはいけない。
* ステートメントの目的語がエージェントやグループであるなら、platform プロパティは使用してはいけない。
* 適用できないか未知であるなら、 language プロパティは使用してはいけない。
* revision プロパティは(綴り間違いのような)軽微な問題の修正を記録する際に用いるべきである。
* revision プロパティは、アクティビティの学習目標、教授法、または資産における大きな変化があるならば、用いるべきでない。そのような場合は新しいアクティビティを用いてほしい。


###### <s>Details</s>詳細

<table>
<tr><th><s>Property</s>プロパティ</th><th><s>Type</s>タイプ</th><th><s>Description</s>説明</th></tr>
<tr>
<td>registration</td>
<td>UUID</td>
<td><s>The registration that the Statement is associated with.</s>
ステートメントが関連している登録
</td>
</tr>
<tr>
<td>instructor</td>
<td>Agent (may be a group)</td>
<td><s>Instructor that the Statement relates to, if not included as the Actor of the statement.</s>
ステートメントのアクタに含まれない場合、ステートメントが関係する教授者
</td>
</tr>
<tr>
<td>team</td>
<td>Group</td>
<td><s>Team that this Statement relates to, if not included as the Actor of the statement.</s>
ステートメントのアクタに含まれない場合、ステートメントが関係する集団
</td>
</tr>
<tr>
<td>contextActivities</td>
<td>contextActivities Object</td>
<td><s>A map of the types of learning activity context that this Statement is related to. Valid context types are: "parent", "grouping", "category" and "other".</s>
このステートメントが関係する、学習活動コンテキストのタイプを持つマップ。有効なコンテキストタイプは "parent" 、 "grouping" 、 "category" 、そして "other" である。
</td>
</tr>
<tr>
<td>revision</td>
<td>String</td>
<td><s>Revision of the learning activity associated with this Statement. Format is free.</s>
このステートメントに関わる学習活動のリビジョン。形式は任意である。
</td>
</tr>
<tr>
<td>platform</td>
<td>String</td>
<td><s>Platform used in the experience of this learning activity.</s>
この学習活動の経験で用いられるプラットフォーム。
</td>
</tr>
<tr>
<td>language</td>
<td>String (as defined in RFC 5646 )</td>
<td><s>Code representing the language in which the experience being recorded in this Statement (mainly) occurred in, if applicable and known.</s>
利用可能または既知である場合、このステートメントで記録される経験が(主に)発生した際の言語コード。
</td>
</tr>
<tr>
<td>statement</td>
<td>[Statement Reference] (#stmtref)</td>
<td><s>Another Statement which should be considered as context for this Statement.</s>
このステートメントのコンテキストと見なされる、他のステートメント。
</td>
</tr>
<tr>
<td>extensions</td>
<td>Object</td>
<td><s>A map of any other domain-specific context relevant to this Statement. For example, in a flight simulator altitude, airspeed, wind, attitude, GPS coordinates might all be relevant (See Extensions)</s>
このステートメントに関連する、他の、ドメイン特化コンテキストのマップ。例えばフライトシミュレータにおける高度、対気速度、風、飛行姿勢、 GPS 座標の全ては関連を持ちうる。

(5.3　『拡張機能』参照)
</td>
</tr>
</table>

###### <s>Note</s>注記
<s>
Revision has no behavioral implications within the scope of xAPI. It is simply stored, so that it is available for reporting tools.
</s>

リビジョンは xAPI の範囲内で、何らかの動作に影響を与えることはない。それは、単に報告ツールが利用できるように記録される。

##### 4.1.6.1 <s>Registration Property</s> Registrationプロパティ
####### <s>Description</s>説明
<s>An instance of a learner undertaking a particular learning activity.
</s>

特定の学習活動を行っている学習者のインスタンス。

####### <s>Details</s>詳細
<s>When an LRS is an integral part of an LMS, the LMS likely supports the concept of registration. The xAPI applies the concept of registration more broadly. A registration could be considered to be an attempt, a session, or could span multiple Activities. There is no expectation that completing an Activity ends a registration. Nor is a registration necessarily confined to a single Agent.
</s>

LRS が LMS の不可欠な部分である場合、LMS は登録の概念を持つことが予想される。xAPI では、登録という概念はより広く適用される。登録は学習の試行や学習期間に関するものと見なすことができ、また一つの記録が登録のアクティビティにわたることも可能である。また、学習活動の完了が登録の終了を意味するとは限らない。そして登録は、一つのエージェントには限定されない。

##### 4.1.6.2 <s>ContextActivities Property</s> ContextActivities プロパティ
####### <s>Description</s>説明
<s>A map of the types of learning activity context that this Statement is related to.
</s>

このステートメントが関連する、学習活動コンテキストのタイプのマップ。

####### <s>Rationale</s>背景
<s>Many Statements do not just involve one Object Activity that is the focus, but relate to other contextually relevant Activities. "Context activities" allow for these related Activities to be represented in a structured manner.
</s>

多くのステートメントは現在対象となる一つのオブジェクト・アクティビティのみを含むわけではなく、文脈上関連する他の活動にも関わる。
"Context activities" はこれらの関連するアクティビティを構造化して表すことを可能にする。

####### <s>Requirements</s>必要条件

<s>

* Every key in the contextActivities Object MUST be one of parent, grouping, category, or other.
* Every value in the contextActivities Object MUST be either a single Activity object or an array of Activity objects.
* The LRS MUST return every value in the contextActivities Object as an array, even if it arrived as a single Activity object;
* The LRS MUST return single Activity Objects as an array of length one containing the same Activity.
* The Client SHOULD ensure that every value in the contextActivitiesOobject is an array of Activity objects instead of a single Activity object.

</s>

* contextActivities オブジェクトの全てのキーは、 parent 、 grouping 、 category 、あるいは other の中の一つでなければならない。
* contextActivities オブジェクトの全ての値は、一つの Activity オブジェクトか、 Activity オブジェクトの配列でなければならない。
* LRS は contextActivities オブジェクトの値は、それを単一の Activity オブジェクトとして受信した場合でも、配列として返さなければならない。
* LRS は単一の Activity オブジェクトを返す場合、その Activity を含む要素数1の配列として返さなければならない。
* クライアントは、 contextActivities オブジェクト中の全ての値が Activity オブジェクトの配列であり、単独の Activity オブジェクトの形を取らないようにすべきである。

####### <s>Details</s>詳細
<s>There are four valid context types. All, any or none of these MAY be used in a given Statement:</s>

4つの有効なコンテキストタイプがある。対象のステートメント中で、これらの全てが使われたり、どれかが使われたり、あるいはどれも使われないということがある。

<s>
1. Parent: an Activity with a direct relation to the activity which is the Object of the Statement. In almost all cases there is only one sensible parent or none, not multiple. For example: a Statement about a quiz question would have the quiz as its parent Activity.
2. Groupling: an Activity with an indirect relation to the activity which is the Object of the Statement. For example: a course that is part of a qualification. The course has several classes. The course relates to a class as the parent, the qualification relates to the class as the grouping.
3. Category:  an Activity used to categorize the Statement. "Tags" would be a synonym. Category SHOULD be used to indicate a "profile" of xAPI behaviors, as well as other categorizations. For example: Anna attempts a biology exam, and the Statement is tracked using the CMI-5 profile. The Statement's Activity refers to the exam, and the category is the CMI-5 profile.
4. Other: a context Activity that doesn't fit one of the other fields. For example: Anna studies a textbook for a biology exam. The Statement's Activity refers to the textbook, and the exam is a context Activity of type "other".

</s>

1. Parent: ステートメントの目的語であるアクティビティへの、直接の関わりを持つアクティビティ。ほとんどの場合、ただ一つの明確な親を持つか、あるいは一つも持たない。複数持つことはない。例えば、クイズの設問についてのステートメントは parent アクティビティとして「クイズ」を持つ。
2. Grouping: ステートメントの目的語であるアクティビティへの、間接的な関わりを持つアクティビティ。
例: 資格取得の一部をなす講座。講座は複数回の講義で構成される。講座は講義に対して parent の関係にあり、資格取得は講義に対して grouping の関係にある。
3. Category: ステートメントを分類するためのアクティビティ。「タグ」と同義である。カテゴリは(他の分類と同様に) xAPI の挙動の "profile" を示すために用いられるべきである。例えば、アンナは生物学の試験に挑戦する。そしてステートメントは(訳注: AICC の) CMI-5 プロファイルを用いて記録される。そのステートメントのアクティビティは試験を参照し、そのカテゴリは CMI-5 プロファイルとなる。
4. Other: 他のフィールドのいずれにも合わない context アクティビティ。例えば、アンナは生物学の試験のために教科書を使い学んでいる。このステートメントのアクティビティは教科書を参照し、試験は other タイプのコンテキスト・アクティビティとなる。

<s>Single Activity Objects are allowed as values so that 0.95 Statements will be compatible with 1.0.0.</s>

0.95 版のステートメントが、1.0.0 版と互換性を保つために、単独の Activity オブジェクトを値として使っても構わない。

###### <s>Note</s>注記
<s>The values in this section are not for expressing all the relationships the Statement Object has. Instead, they are for expressing relationships appropriate for the specific Statement (though the nature of the Object will often be important in determining that). For instance, it is appropriate in a Statement about a test to include the course the test is part of as parent, but not to include every possible degree program the course could be part of in the grouping value.
</s>

この節は、ステートメントオブジェクトが持つ全ての関係性を説明するためのものではない。説明しているのは、(オブジェクトの性質がそれを決定するのにしばしば重要であるのだが)特定のステートメントに適合する関係性についてである。
例えば、テストについてのステートメントに、そのテストを利用している講座を parent として含めるのは妥当だが、grouping の値として、関連の可能性がある全ての学位プログラムを並べるのは妥当とは言えない。

####### <s>Example</s>例
<s>Consider the following hierarchical structure: "Questions 1 to 6" are part of "Test 1" which in turn belongs to the course "Algebra 1". The six questions are registered as part of the test by declaring "Test 1" as their parent. Also they are grouped with other Statements about "Algebra 1" to fully mirror the hierarchy. This is particularly useful when the Object of the Statement is an Agent, not an Activity. "Andrew mentored Ben with context Algebra 1".
</s>

次のような階層構造を考えてほしい。
「設問1から6」は「テスト1」に含まれ、同様にテスト1は「代数学1」講座に属している。
6つの設問は「テスト1」を親と宣言することで、テストの一部として登録される。また、それらは「代数学1」の他のステートメントと共に grouping され、階層高層が完全に複写される。ステートメントの目的語が(アクティビティでなく)エージェントであるときに、これは特に有用である。「アンドリューは、代数学1のコンテキストでベンを指導した」。

```
{
    "parent" : [{
    "id" : "http://example.adlnet.gov/xapi/example/test 1"
	}],
    "grouping" : [{
    "id" : "http://example.adlnet.gov/xapi/example/Algebra1"
    }]
}

```

<a name="timestamp"/>

#### 4.1.7 <s>Timestamp</s> Timestamp (タイムスタンプ)

###### <s>Description</s>説明

<s>The time at which a Statement was generated.
</s>

ステートメントが生成された時刻。

###### <s>Requirements</s>必要条件
<s>

* A timestamp MUST be formatted according to ISO 8601.
* A timestamp SHOULD include the time zone.
* A timestamp SHOULD be the current or a past time when it is outside of a Sub-Statement.
* A timestamp MAY be truncated or rounded to a precision of at least 3 decimal digits for seconds
(millisecond precision MUST be preserved).
* A timestamp MAY be a moment in the future, to denote a deadline for planned learning, provided it is included inside a Sub-Statement.

</s>

* timestamp は ISO 8601 に従う形式でなければならない。
* timestamp はタイムゾーンを含むべきである。
* サブ・ステートメントの外部である場合、 timestamp は現在または過去の時刻となるべきである。
* timestamp は、秒を少なくとも3桁の精度で切り捨てられるか、あるいは丸められてもよい(ミリ秒の精度は保たれなければならない)。
* timestamp は、それがサブ・ステートメントに含まれるならば、計画した学習の期限を示すために未来の時刻としてもよい。

###### <s>Details</s>詳細
<s>A timestamp in a Statement related to learning that occurs outside of the system can differ from Stored (the system time of the event). Namely, there can be delays between the occurrence of the experience and the reception of the corresponding Statement by the LRS. Another cause is when Statements are propagated to other systems.
</s>

システムの外部で発生する学習に関わるステートメントのタイムスタンプは、システムが保存していた時刻とは異なる場合がある。たとえば、経験が発生してから LRS がステートメントを受信するまでの間に、遅延が発生することがある。もう一つの理由として、ステートメントが他のシステムに伝播されるときの遅延がある。

<a name="stored"/>

#### 4.1.8 <s>Stored</s> Stored

###### <s>Description</s>説明

<s>The time at which a Statement is stored by the LRS.
</s>

ステートメントが LRS に記録された時刻。

<s>The stored property is the literal time the Statement was stored. Use Timestamp to track a time at which the Statement was generated.
</s>

stored プロパティは、ステートメントが記録されたときの正確な時刻である。ステートメントが発生したときの時刻を記録する際は、 Timestamp を使ってほしい。

###### <s>Requirements</s>必要条件
<s>

* The stored property MUST be formatted according to ISO 8601.
* The stored property SHOULD include the time zone.
* The stored property SHOULD be the current or a past time.
* The stored property MAY be truncated or rounded to a precision of at least 3 decimal digits for seconds (millisecond precision MUST be preserved).

</s>

* stored プロパティは ISO 8601 に従う形式でなければならない。
* stored プロパティはタイムゾーンを含むべきである。
* stored プロパティは現在または過去の時刻となるべきである。
* stored プロパティは、秒を少なくとも3桁の精度で切り捨てられるか、あるいは丸められてもよい(ミリ秒の精度は保たれなければならない)。

<a name="authority"/>

#### 4.1.9 <s>Authority</s>Authority (権限)

###### <s>Description</s>説明

<s>The authority property provides information about whom or what has asserted that this Statement is true.
</s>

authority プロパティは「誰、または何がこのステートメントが真であると主張するか」の情報を提供する。

###### <s>Requirements</s>必要条件
<s>

* Authority MUST be an Agent, except in 3-legged OAuth, where it must be a Group with two Agents. The two Agents represent an application and user together.
* The LRS MUST include the user as an Agent as the entire authority if the user connects directly (using HTTP Basic Authentication) or is included as part of a Group.
* The LRS MUST ensure that all Statements stored have an authority.
* The LRS SHOULD overwrite the authority on all stored received Statements, based on the credentials used to send those Statements.
* The LRS MAY leave the submitted authority unchanged but SHOULD do so only where a strong trust relationship has been established, and with extreme caution.
* The LRS MAY identify the user with any of the legal identifying properties if a user connects directly (using HTTP Basic Authentication) or a part of a 3-legged OAuth.

</s>

* Authority は 3-legged OAuth を除き、2つのエージェントによってグループが形成されてしまう場面においては、1個のエージェントが該当しなければならない。この2つのエージェントは、アプリケーションとユーザを表す。
* ユーザが HTTP ベーシック認証を用いて直接接続する場合やグループの一員である場合、 LRS は全体の権限を持つエージェントとしてユーザを取り込まなければならない。
* LRS は記録された全てのステートメントが権限を持っていることを確認しなければならない。
* LRS はこれらのステートメントを送信するための資格情報に基づいて、全ての記録された受信済ステートメントにおける権限を上書きすべきである。
* LRS は受信した権限を変更せずに残してもよいが、強い信頼関係が確立された場合に限るべきであり、また残す際には細心の注意を払う必要がある。
* ユーザが HTTP ベーシック認証を用いて直接接続する場合、あるいは 3-legged OAuth の一部である場合、 LRS は正当な識別プロパティによってユーザを識別してもよい。

###### <s>Details</s>詳細

<s>The asserting authority represents the authenticating user of some system or application.
</s>

権限を主張するということは、システムやアプリケーション上でのユーザを認証することを意味する。

##### <s>OAuth Credentials as Authority</s>権限としての OAuth 資格情報

####### <s>Description</s>説明

<s>This is a workflow for use of OAuth. 2-legged and 3-legged OAuth are both supported.
</s>

これは OAuth 利用のフローである。 2-legged と 3-legged の OAuth がサポートされる。

####### <s>Requirements</s>必要条件
<s>

* The authority MUST contain an Agent Object that represents the OAuth consumer, either by itself, or as part of a group in the case of 3-legged OAuth.
* The Agent representing the OAuth consumer MUST be identified by account.
* The Agent representing the OAuth consumer MUST use the consumer key as the “account name”field.
* If the Agent representing the OAuth consumer is a registered application, the token request endpoint MUST be used as the account homePage.
* If the Agent representing the OAuth consumer is not a registered application, the temporary credentials endpoint MUST be used as the account homePage.
* An LRS MUST NOT trust the application portion of the authority in the event the account name is from the same source as the unregistered application. (Multiple unregistered applications could choose the same consumer key. As a result, there is no consistent way to verify this combination of temporary credentials and the account name.)
* Each unregistered consumer SHOULD use a unique consumer key.

</s>

* authority は OAuth consumer を示すエージェントオブジェクトか、エージェントオブジェクトそのもの、もしくは 3-legged OAuth の場合にはグループの一部としてのエージェントオブジェクトを含まなければならない。
* OAuth consumer を表すエージェントは、アカウントによって識別されなければならない。
* OAuth consumer を示すエージェントは、「アカウント名」のフィールドとして consumer キーを用いなければならない。
* OAuth consumer を示すエージェントが登録済アプリケーションであるならば、トークンリクエストエンドポイントはアカウントのホームページとして用いられなければならない。
* OAuth consumer を示すエージェントが登録済アプリケーションでない場合は、一時的な資格情報のエンドポイントがアカウントのホームページとして用いられなければならない。
* LRS は、アカウント名が未登録のアプリケーションと同一のソースによる権限のアプリケーション部分を、信頼してはならない。(複数の未登録アプリケーションは、同じ consumer キーを選択できる。その結果として、一時的な資格情報とアカウント名の組合せを検証するための、信頼できる方法は存在しない。)
* 未登録のそれぞれの consumer は、一意な consumer キーを使うべきである。

####### <s>Details</s>詳細

<s>This workflow assumes a Statement is stored using a validated OAuth connection and the LRS creates or modifies the authority property of the Statement.
</s>

このワークフローは、ステートメントが検証済 OAuth コネクションを用いて格納され、 LRS がステートメントの authority プロパティを作成、または変更することを仮定している。

<s>In a 3-legged OAuth workflow, authentication involves both and OAuth consumer and a user of the OAuth service provider. For instance, requests made by an authorized Twitter plug-in on their Facebook account will include credentials that are specific not only to Twitter as a Client application, or them as a user, but the uniqe combination of both.
</s>

3-legged OAuth ワークフローでは、認証は "OAuth consumer" と「 OAuth サービスプロバイダのユーザ」の両方を含む。例えば、 Facebook アカウントにおける、許可された Twitter プラグインからの要求は、クライアントアプリケーションとしての Twitter やユーザに対するだけでなく、両者の固有の結びつきに対する資格情報を含んでいる。

####### <s>Example</s>例

<s>The pairing of an OAuth consumer and a user.</s>
OAuth consumer とユーザのペア。

```
￼"authority": {
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

<a name="version"/>

#### 4.1.10 <s>Version</s>Version (バージョン)

###### <s>Description</s>説明

<s>Version information in Statements helps systems that process data from an LRS get their bearings. Since the Statement data model is guaranteed consistent through all 1.0.x versions, in order to support data flow among such LRSs the LRS is given some flexibility on Statement versions that are accepted.
</s>

LRS からのデータを処理するシステムは、ステートメントのバージョン情報によって、それらの挙動を決めることができる。ステートメントデータモデルが全てのバージョン 1.0.x を通じて一貫性が保証されるので、 LRS 間のデータフローをサポートするために、 LRS には受け入れられるステートメントのバージョンにおける柔軟性が与えられる。

###### <s>Requirements</s>必要条件

* <s>Version MUST be formatted as laid out for the API version header in API Versioning.</s>バージョンは API Versioning 仕様中の API バージョンヘッダのレイアウト形式に従わなければならない。

###### <s>LRS Requirements</s>LRS の必要条件
<s>

* An LRS MUST accept all Statements where their version starts with "1.0." if they otherwise validate.
* An LRS MUST reject all Statements with a version specified that does not start with "1.0."
* Statements returned by an LRS MUST retain the version they are accepted with. If they lack a version, the version MUST be set to 1.0.0

</s>

* 有効なステートメントについて、 LRS は "1.0." で始まるバージョンの全てのステートメントを受け入れなければならない。
* "1.0." から始まらないように指定されたバージョンの全てのステートメントを、 LRS は拒否しなければならない。
* LRS によって返されるステートメントは、受け入れられたときのバージョンを保持しなければならない。バージョン情報が存在しないなら、バージョンは 1.0.0 に設定されなければならない。

###### <s>Client Requirements</s>クライアントの必要条件
<s>

* If Clients set the Statement version, they MUST set it to 1.0.0
* Clients SHOULD NOT set the Statement version.

</s>

* クライアントがステートメントのバージョンを設定するならば、それは 1.0.0 でなければならない。
* クライアントはステートメントのバージョンを設定すべきではない。

<a name="attachments"/></a>

#### 4.1.11 <s>Attachments</s>Attachments (添付資料)

###### <s>Description</s>説明
<s>A digital artifact providing evidence of a learning experience.</s>学習経験の証跡を提供するデジタル文書

###### <s>Rationale</s>背景
<s>In some cases an attachment may logically be an important part of a learning record. Think of a simulated communication with ATC, an essay, a video, etc. Another example of such an attachment is (the image of) a 
certificate that was granted as a result of an experience. It is useful to have a way to store these attachments in and retrieve them from an LRS. </s>
場合により、添付文書は論理的に学習記録の重要な部分となる可能性がある。航空管制との通信シミュレーション、エッセイ、ビデオなどを考えてみてほしい。添付文書の他の例としては、経験の結果として与えられた修了証書（の画像）がある。これらの添付文書を LRS に記録したり LRS から読み出したりする方法があることは有益である。


###### <s>Requirements for Attachment Statement Batches</s>添付文書ステートメントバッチのための必要条件

<s>A Statement batch, Statement results, or single Statement that includes attachments:</s>
添付文書を含むステートメントバッチ、ステートメントの結果、または、１つのステートメントは、以下の条件を満たす:

* <s>MUST be of type "application/json" and include a fileUrl for every attachment EXCEPT for Statement results when the attachments filter is false or</s>
添付文書フィルタが false の場合のステートメントの結果を除き、"application/json"  タイプで、全ての添付文書毎に fileUrl を含まなければならない。または

* <s>MUST conform to the definition of multipart/mixed in RFC 1341 and:</s>
RFC1341 における multipart/mixed の定義に準拠しなければならない。かつ、以下の条件を満たさなければならない:

    * <s>The first part of the multipart document MUST contain the Statements themselves, with type "applicaton/json".</s>
multipart 文書の最初にはステートメント自身が "application/json" タイプで含まれる。

    * <s>Each additional part contains the raw data for an attachment and forms a logical part of the Statement. This capability will be available when issuing PUT or POST against the Statement resource.</s>
他の追加部分は、添付文書の生のデータを含み、ステートメントの論理部分を形成する。この機能はステートメントリソースに対して PUT や POST が発行されたときに利用可能である。

	* <s>MUST include a X-Experience-API-Hash field in each part's header after the first (statements) part.</s>
最初の（ステートメント）部分に続く各部分のヘッダーには X-Experience-API-Hash フィールドを含まなければならない。

	* <s>This field MUST be set to match the "sha2" property of the attachment declaration corresponding to the attachment included in this part.</s>
このフィールドは、この部分に含まれる添付文書に一致した添付文書宣言の "shar2" プロパティと一致していなければならない。

	* <s>MUST include a Content-Transfer-Encoding field with a value of "binary" in each part's header after the first (statements) part.</s>
最初の（ステートメント）部分に続くそれぞれのパートのヘッダーに、"Content-Transfer-Encoding" の値として "binary" を含めなければならない。

    * <s>SHOULD only include one copy of an attachment's data when the same attachment is used in multiple Statements that are sent together.</s>
複数のステートメントが同時に送られ、同じ添付文書が使われた時は、１つの添付文書のデータだけを含むべきである。

    * <s>SHOULD include a Content-type field in each part's header, for the first part this MUST be "application/json".</s>
各部分のヘッダーには Content-type フィールドを含むべきであり、最初の部分は application/json タイプにしなければならない。

###### <s>Requirements for the LRS</s>LRSの必要条件

* <s>An LRS MUST include attachments in the Transmission Format described above when requested by the Client (see Section [7.2 "Statement API"](#stmtapi)).</s>
クライアントから要求があった場合は、LRS は上記に示す転送形式で添付文書を含まなければならない。（[7.2 ステートメント API](#stmtapi)参照）

* <s>An LRS MUST NOT pull Statements from another LRS without requesting attachments.</s>
LRS は添付文書の要求なしでは他の LRS からステートメントを引き出してはならない。

* <s>An LRS MUST NOT push Statements into another LRS without including attachment data received, if any, for those attachments.</s>
LRS は、受け取った添付文書データがある場合は、それらを添付することなく、ステートメントを他の LRS に送ってはならない。

* <s>When receiving a PUT or POST with a document type of "application/json",</s>
"application/json" のドキュメントタイプの文書を PUT や POST で受け取る場合、

    * <s>An LRS MUST accept batches of Statements which contain either no attachment Objects, or only attachment Objects with a populated fileUrl.</s>
LRS は、添付文書オブジェクトを含まないか、あるいは投入された fileUrl を持つ添付文書オブジェクトのみを含む場合に、ステートメントのバッチを受入れなければならない。
* <s>Otherwise:</s>
上記以外の時に：
    * <s>An LRS MUST accept batches of Statements via the Statements resource PUT or POST that contain attachments in the Transmission Format described above.</s>
LRS は、上記で示した転送フォーマットでの添付文書を含むステートメントリソースの PUT または POST 経由でステートメントのバッチを受入れなければならない。
    * <s>An LRS MUST reject batches of Statements having attachments that neither contain a fileUrl nor match a received attachment part based on their hash.</s>
LRS は、fileUrl を含まないか、ハッシュに基づき受け取った添付文書の部分と一致しない添付文書を持つステートメントのバッチを拒否しなければならない。
    * <s>An LRS SHOULD assume a Content-Transfer-Encoding of binary for attachment parts.</s>
LRS は添付文書の部分に対してバイナリの Content-Transfer-Encoding を前提とすべきである。
* <s>An LRS MAY reject (batches of) Statements that are larger than the LRS is configured to allow.</s>
LRS は、その LRS が許可された設定より大きいステートメント（のバッチ）を拒否することができる。

__<s>Note</s>注記:__ <s>There is no requirement that Statement batches using the mime/multipart format contain attachments.</s>
mime/multipart フォーマットを使うステートメントバッチが添付文書を含む場合は、何の必要条件もない。


###### <s>Requirements for the Client</s>クライアントの必要条件

* <s>The Client MAY send Statements with attachments as described above.</s>
クライアントは上記で記述された添付文書を含むステートメントを送ることができる。
* <s>The Client MAY send multiple Statements where some or all have attachments if using "POST".</s>
クライアントは、POST を利用するときに、そのうちのいくつかが添付文書を含むかあるいはすべてが添付文書を含む複数のステートメントを送ることができる。
* <s>The Client MAY send batches of type "application/json" where every attachment Object has a fileUrl, ignoring all requirements based on the "multipart/mixed" format.</s>
クライアントは、"multipart/mixted" 形式に基づく全ての必要条件を無視し、全ての添付文書オブジェクトが fileUrl を持つ "application/json" タイプのバッチを送ることができる。

###### <s>Details</s>詳細
<s>The table below lists all properties of the Attachment Object.</s>
以下のテーブルは添付文書オブジェクトのすべてのプロパティを示す。
<table>
	<tr><th><s>Property</s>プロパティ</th><th><s>Type</s>タイプ</th><th><s>Description</s>説明</th><th><s>Required</s>必須</th></tr>
	<tr>
		<a name="attachmentUsage" /></a>

		<td>usageType</td>
		<td>IRI</td>
		<td><s>Identifies the usage of this attachment. For example: one expected use case for attachments is to include a "completion certificate". A type IRI corresponding to this usage should be coined, and used with completion certificate attachments.</s>
この添付文書の利用方法を規定する。例えば、添付文書の期待されるユースケースの１つに「修了証明」を含むことがある。この用途に対応するタイプ IRI を作成し、修了証明添付文書と一緒に利用されるべきである。

		<td>yes</td>
	</tr>
	<tr>
		<td>display</td>
		<td><a href="#misclangmap">Language Map</a></td>
		<td><s>Display name (title) of this attachment.</s>この添付文書の名前（タイトル）を表示する。</td>
		<td>yes</td>
	</tr>
	<tr>
		<td>description</td>
		<td><a href="#misclangmap">Language Map</a></td>
		<td><s>A description of the attachment</s>添付文書の説明</td>
		<td>no</td>
	</tr>
	<tr>
		<td>contentType</td>
		<td><a href="https://www.ietf.org/rfc/rfc2046.txt?number=2046">Internet Media Type</a></td>
		<td><s>The content type of the attachment.</s>添付文書のコンテンツタイプ</td>
		<td>yes</td>
	</tr>
	<tr>
		<td>length</td>
		<td>integer</td>
		<td><s>The length of the attachment data in octets</s>オクテットで示した添付文書データの長さ

		</td>
		<td>yes</td>
	</tr>
	<tr>
		<td>sha2</td>
		<td>base64</td>
		<td><s>The SHA-2 hash of the attachment data. A minimum key size of 256 bits is recommended.</s>添付文書データの SHA-2 ハッシュ。最低256ビット以上のキーが推奨される。</td>
		<td>yes</td>
	</tr>
	<tr>
		<td>fileUrl</td>
		<td>IRL</td>
		<td><s>an IRL at which the attachment data may be retrieved, or from which it used to be retrievable. </s>添付文書データが取り出されうる IRL、あるいは、取り出しが可能であった IRL。</td>
		<td>no</td>
	</tr>
</table>

_<s>Procedure for the exchange of attachments</s>添付文書交換の手続き_

1. <s>A Statement including an attachment is construed according to the Transmission Format described below.</s>
添付文書を含むステートメントは、以下に記述する転送フォーマットにより構成される。

2. <s>The Statement is sent to the receiving system using a Content-Type of "multipart/mixed". The attachments are placed at the end of such transmissions.</s>
ステートメントは、"multipart/mixed" のコンテンツタイプで、受け側のシステムに送られる。添付文書は転送の最後に配置される。

3. <s>The receiving system decides whether to accept or reject the Statement based on the information in the first part.</s>
受け側のシステムは、最初の部分にある情報に基づき、ステートメントを受入れるか拒否するかを決定する。

4. <s>If it accepts the attachment, it can match the raw data of an attachment　with the attachment header in a Statement by comparing the SHA-2 of the raw　data to the SHA-2 declared in the header. It MUST not do so any other way.</s>
仮に添付文書を受入れたときに、生データの SHA-2 とヘッダーで宣言された SHA-2 とを比較することで、ステートメントにある添付文書ヘッダーと生のデータを照合することができる。他の方法で照合してはならない。


###### <s>Example</s>例

<s>Below is an example of a very simple Statement with an attachment. Please note the following:</s>
添付文書を含むステートメントの非常に簡単な例である。以下の点に注意してほしい：

* <s>The boundary in the sample was chosen to demonstrate valid character classes;</s>
以下の例の boundary は有効な文字クラスを例示するために選択されたものである。

* <s>The selected boundary does not appear in any of the parts;</s>
選択された boundary は、エンコードされた各添付文書のどの部分にもマッチしない。

* <s>For readability the sample attachment is text/plain. Even if it had been a 'binary' type like 'image/jpeg' no encoding would be done, the raw octets would be included;</s>
読みやすくするために、添付文書の例は text/plain にしている。仮に、image/jpeg のようにバイナリタイプであったとしても、符号化されず、生のオクテットデータがそのまま含まれる。
* <s>Per RFC 1341, the boundary is <CRLF> followed by -- followed by the boundary string declared in the header.</s>
RFC 1341 より、boundary は ```<CRLF>``` のあとに、さらにその後のヘッダーで定義された boundary 文字列を続けたものとなる。

<s>Don't forget the ```<CRLF>```  when building or parsing these messages.</s>
これらのメッセージを構築あるいは構文解析する場合に```<CRLF>```を忘れてはいけない。

<s>Headers</s>ヘッダー:

````
Content-Type: multipart/mixed; boundary=abcABC0123'()+_,-./:=?
X-Experience-API-Version:1.0.0
````

<s>Content</s>コンテンツ:

````
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
````


<a name="dataconstraints"/></a>

#### 4.1.12 <s>Data Constraints</s> データの制約

###### <s>Description</s>説明

<s>All the properties used in Statements are restricted to certain types, and those types constrain the behavior of systems processing Statements. For clarity, certain key requirements are documented here, emphasizing where compliant systems have a responsibility to act in certain ways.</s>
ステートメントで使われる全てのプロパティはあるタイプに制限されている。また、それらのタイプはステートメントを処理するシステムの動作を制約している。明確化のために、どの部分において、準拠するシステムが特定の振る舞いを行う責任があるかを強調し、いくつかの主な必要条件をここに記述する。

###### <s>Requirements for the Client</s>クライアントの必要条件

<s>The following requirements reiterate especially important requirements already included elsewhere, to emphasize, clarify, and provide implementation guidance.</s>
実行ガイダンスを強調し、明確化し、提供するために、以下の必要条件は、他にすでに含まれている特に重要な必要条件を繰り返している。

* <s>Values requiring IRIs MUST be sent with valid IRIs. Please use a library to construct them instead of string concatenation. Complete IRI validation is extremely difficult, so much of the burden for ensuring data portability is on the Client.</s>
値として送信される IRI は有効なものでなければならない。IRI の生成には、文字列結合ではなく、ライブラリを利用すべきである。IRI の完全な検証は非常に難しいため、データの可搬性を担保する責任の大部分はクライアント側にある。

* <s>Keys of language maps MUST be sent with valid RFC 5646 language tags, for similar reasons.</s>
同様の理由から、言語マップのキーは、有効な RFC 5646 言語タグと一緒に送られなければならない。


###### <s>Requirements for the LRS</s>LRS の必要条件

* <s>The LRS MUST reject Statements</s>
以下の場合、LRS はステートメントを拒否しなければならない。

    * <s>with any null values (except inside extensions).</s>
値がない場合（拡張の中を除く）

    * <s>with strings where numbers are required, even if those strings contain numbers.</s>
数値が必要な場所に文字列が与えられている場合。（その文字列に数字が含まれる場合でも）

    * <s>with strings where booleans are required, even if those strings contain booleans.</s>
2値が必要な場所に文字列が与えられている場合。（その文字列に2値が含まれる場合でも）
    * <s>with any non-format-following key or value, including the empty string, where a string with a particular format (such as mailto IRI, UUID, or IRI) is required.</s>
特別な形式（mailto, IRI, UUID, または IRI）の文字が必要な場所に、空文字列を含む、形式に合わないキーまたは値が与えられている場合。
    * <s>where the case of a key does not match the case specified in the standard.</s>
あるキーのケースが標準で規定されたケースに合わない場合。

    * <s>where the case of a value restricted to enumerated values does not match an enumerated value given in the standard exactly.</s>
値のケースが数字の値に制限されていて、標準で示された数字の値に一致しない場合。

* <s>The LRS MUST reject Statements containing IRL, IRI, or IRI values without a scheme.</s>
LRS はスキーマを持たない、IRL、IRI、または IRI の値を含むステートメントを拒否しなければならない。
* <s>The LRS MUST at least validate that the sequence of token lengths for language map keys matches the [RFC 5646](http://tools.ietf.org/html/rfc5646) standard.</s>
LRS は少なくとも、言語マップキーのトークンの長さのシーケンスが [RFC 5646](http://tools.ietf.org/html/rfc5646) 標準に一致することを認証しなければならない。
* <s>The LRS MUST process and store numbers with at least the precision of IEEE 754 32-bit floating point numbers.</s>
LRS は、数字を最低限 IEEE754 32ビットの精度で処理して記録しなければならない。
* <s>The LRS MUST validate parameter values to the same standards required for values of the same types in Statements.</s>
LRS はステートメントにある同じタイプの値の検証と同じ基準で、パラメータの値の検証を行わなければならない。
__<s>Note</s>注記:__ <s>string parameter values are not quoted as they are in JSON.</s>
JSON とは異なり、文字列パラメータの値は引用符でくくられない。
* <s>The LRS MAY use best-effort validation for IRL, IRI, and IRI formats to satisfy the non-format-following rejection requirement.</s>
LRS が形式不適合による拒絶の必要条件を満たすためには、IRL, IRI, および IRI フォーマットについてベストエフォートの検証をすればよい。
* <s>The LRS MAY use best-effort validation for language map keys to satisfy the non-format-following rejection requirement.</s>
LRS は、言語マップキーが形式に合わない要求拒否を満たすために、ベストエフォート検証を使うことができる。


<a name="retstmts"/></a> 

### 4.2 <s>Retrieval of Statements</s> ステートメントの検索

###### <s>Description</s>説明
<s>A collection of Statements can be retrieved by performing a query on the "statements" endpoint, see Section [7.2 "Statement API"](#stmtapi) for details. </s>一連のステートメントは検索クエリを "statements" とすることで、検索が可能となる。詳細は[7.2 ステートメント API](#stmtapi)を参照。

###### <s>Details</s>詳細
<s>The following table shows the data structure for the results of queries on the Statement API.</s>
下の表はステートメント API の検索結果のためのデータ構造を示している。
<table>
	<tr><th><s>Property</s>プロパティ</th><th><s>Type</s>タイプ</th><th><s>Description</s>説明</th></tr>
	<tr><td><s>statements</s>statements</td><td><s>Array of Statements</s>Array of Statements</td>
		<td><s>List of Statements. If the list returned has been limited (due to pagination), and there are more results, they will be located at the "statements" property within the container located at the IRL provided by the "more" element of this Statement result Object.
</s>ステートメントのリスト。さらに結果があるのに，戻ってきたリストが（ページ制限により）制限されていたら，コンテイナに含まれる "statements" プロパティに配置されるだろう。コンテイナは，ステートメント結果オブジェクトのさらなる要素によって提供される IRL に置かれる。
		</td>
	</tr>
	<tr><td>more</td><td>IRL</td>
		<td><s>Relative IRL that may be used to fetch more results, including the full path and optionally a query string but excluding scheme, host, and port. Empty string if there are no more results to fetch.</s>
追加の結果を取り込むために用いられる相対 IRL。フルパスとオプションのクエリ文字列で、スキーム、ホスト、ポートの情報を含まない。
<br/><br/>
			<s>This IRL must be usable for at least 24 hours after it is returned by the LRS. In order to avoid the need to store these IRLs and associated query data, an LRS may include all necessary information within the IRL to continue the query, but should avoid generating extremely long IRLs. The consumer should not attempt to interpret any meaning from the IRL returned.</s>
この IRL は LRS によって戻された後、少なくとも24時間は利用可能でなければならない。これらの IRL と関連するクエリデータを保存しておく必要性を避けるために、LRS はクエリを実行するのに必要な全ての情報を IRL に含めてもよいが、非常に長い IRL の生成は避けるべきである。利用者は IRL の戻り値から意味を解釈すべきではない。
		</td>
	</tr>
</table>

<a name="voided"/></a>

#### 4.3 <s>Voided</s> 無効

###### <s>Rationale</s>背景

<s>The certainty that an LRS has an accurate and complete collection of data is guaranteed by the fact that Statements cannot be logically changed or deleted. This immutability of Statements is a key factor in enabling the distributed nature of Experience API.</s>
ステートメントが論理的に変更されたり削除されたりすることは無い、という事実によって、LRS が正確で完全なデータを収集しているという確実性が保証される。このステートメントの不変性が、xAPI の分散性を可能にする重要な要因である。


<s>However, not all Statements are perpetually valid once they have been issued. Mistakes or other factors could require that a previously made Statement is marked as invalid. This is called "voiding a Statement" and the reserved Verb “http://adlnet.gov/expapi/verbs/voided" is used for this purpose. Any Statement that voids another cannot itself be voided.</s>
しかしながら、すべてのステートメントが、一度発行されると永久に有効である、ということではない。誤りや他の要因で、以前に作られたステートメントを無効とマークすることが必要になることがある。これを、”ステートメントの無効化"と呼び、予約された動詞 “http://adlnet.gov/expapi/verbs/voided" はこの目的で使用される。他のステートメントを無効化するステートメント自身を無効化することはできない。

###### <s>Requirements</s>必要条件

* <s>When issuing a Statement that voids another, the Object of that voiding Statement MUST have the "objectType" field set to "StatementRef".</s>
他のステートメントを無効化するステートメントを発行するときは、無効化ステートメントの目的語は "objectType" フィールドを "StatementRef" に設定しなければならない
* <s>When issuing a Statement that voids another, the Object of that voiding Statement MUST specify the id of the statement-to-be-voided by its "id" field.</s>
他のステートメントを無効化するステートメントを発行するとき、無効化ステートメントの目的語では、無効化すべきステートメントの ID を ID フィールドで指定しなければならない。
* <s>Upon receiving a Statement that voids another, the LRS SHOULD reject the entire request which includes the voiding Statement with HTTP 403 'Forbidden' if the request is not from a source authorized to void Statements.</s>
他のステートメントを無効化するステートメントを受け取ったとき、LRS は、その要求がステートメントの無効化を認められたソースからの要求でない場合は、HTTP 403 'Forbidden' にて、無効化ステートメントを含むリクエスト全体を拒否すべきである。
* <s>Upon receiving a Statement that voids another, the LRS SHOULD return a descriptive error if the target Statement cannot be found.</s>
他のステートメントを無効化するステートメントを受け取ったとき、LRS は、もし、対象ステートメントが見つからなかったときは、説明を含むエラーを返すべきである。
* <s>Upon receiving a Statement that voids another, the LRS MAY roll back any changes to Activity or Agent definitions which were introduced by the Statement that was just voided;</s>
他のステートメントを無効化するステートメントを受け取ったとき、LRS は無効化されたステートメントによって、もともと導入されたアクティビティやエージェントの定義に対する変更をロールバックしてもよい。
* <s>An Activity Provider that wants to "unvoid" a previously voided Statement SHOULD issue that Statement again under a new id</s>
以前の無効ステートメントを有効化するアクティビティプロバイダは新しい id で再度ステートメントを発行すべきである。
* <s>A reporting system SHOULD NOT show voided or voiding Statements by default.</s>
レポートシステムは無効化された、または無効化するためのステートメントを標準では表示すべきではない。

###### <s>Note: See ["Statement References"](#stmtref) in [Section 4.1.4.3 When the "Object" is a Statement](#stmtasobj) 
for details about making references to other Statements.  To see how voided statements behave when queried, See [StatementRef](#queryStatementRef) in 7.2 Statement API).</s>
注記: 他のステートメントの参照作成に関する詳細については、[4.1.4.3 目的語がステートメントだった場合](#stmtasobj) の[ステートメント参照](#stmtref)  を参照して欲しい。呼ばれた際にいかに無効化ステートメントが振舞うかについては、7.2　ステートメント APIの [StatementRef](#queryStatementRef) を参照してほしい。

###### <s>Example</s>例
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

<s>This example Statement voids a previous Statement which it identifies with the Statement id 
"e05aa883-acaf-40ad-bf54-02c8ce485fb0".</s>
このステートメントの例は、ステートメント id が "e05aa883-acaf-40ad-bf54-02c8ce485fb0" で示される以前のステートメントを無効化する。


<a name="signature"/></a>

#### 4.4 <s>Signed Statements</s> 署名付きステートメント

##### <s>Description</s>説明
<s>A Statement may include a <a href="https://en.wikipedia.org/wiki/Digital_signature"> digital signature</a> to provide strong and durable evidence of the authenticity and integrity of the Statement.</s>
ステートメントは、強固で耐久性のあるステートメントの信頼性と完全性を提供するために<a href="http://ja.wikipedia.org/wiki/デジタル署名">デジタル署名</a>を含むことができる。

##### <s>Rationale</s>背景
<s>Some Statements will have regulatory or legal significance, or otherwise require strong　and durable evidence of their authenticity and integrity. It may be necessary to verify　these Statements without trusting the system they were first recorded in, or perhaps　without access to that system. Digital signatures will enable a third-party system　to validate such Statements.</s>
ステートメントの中には規制上のあるいは法的に重要なものもあるだろう。また、強固で耐久性のある信頼性と完全性の証跡を必要とするだろう。これらのステートメントを最初に記録されたシステムを信頼せずに、あるいはシステムにアクセスせずに確認する必要があるかもしれない。デジタル署名は、第三者システムがそのようなステートメントを確認することを可能にする。


##### <s>Requirements</s>必要条件

* <s>A Signed Statement MUST include a JSON web signature (JWS) as defined here:
http://tools.ietf.org/html/draft-ietf-jose-json-web-signature, as an attachment with a usageType of "http://adlnet.gov/expapi/attachments/signature" and a contentType of "application/octet-stream".</s>
署名付きステートメントは、 usageType が "http://adlnet.gov/expapi/attachments/signature" で、contentType が "application/octet-stream"　である、添付文書として定義される、JSON web signature (JWS) を含まなければならない： http://tools.ietf.org/html/draft-ietf-jose-json-web-signature

* <s>The JWS signature MUST have a payload of a valid JSON serialization of the Statement generated　before the signature was added.</s>
署名が付加される前に、JWS 署名は、生成されたステートメントの有効な JSON の連続のデータ本体を持たなければならない。

* <s>The JWS signature MUST use an algorithm of "RS256","RS384", or "RS512".</s>JWS 署名は "R256"、"RS384"、または "RS512" のアルゴリズムを使用しなければならない。

* <s>The JWS signature SHOULD have been created based on the private associated with an　X.509 certificate.</s>
JWS 署名は、X.509 証明と関連した秘密鍵に基づいて生成されるべきである。

* <s>If X.509 was used to sign, the JWS header SHOULD include the "x5c" property containing　the associated certificate chain.</s>
仮に、X.509 が署名に使われたなら、JWS のヘッダーは関連した証明書チェーンを内包する "x5c" プロパティを含むべきである。

* <s>The LRS MUST reject requests to store Statements that contain malformed signatures,　with HTTP 400 and SHOULD include a message describing the problem in the response.
In order to verify signatures are well formed, the LRS MUST do the following:</s>
LRS は、HTTP 400 で不正な形式の署名を内蔵するステートメントを記録する要求を拒否しなければならず、応答には問題を説明するメッセージを含むべきである。署名が正しい形式であることを検証するために、LRS は以下のことを実行しなければならない。
    * <s>Decode the JWS signature, and load the signed serialization of the Statement from the JWS signature payload.</s>
JWS 署名を復号化して、JWS の署名データから、一連の署名付きステートメントを取り出す。
    * <s>Validate that the "original" Statement is logically equivalent to the received Statement.</s>
オリジナルステートメントは論理的に受理したステートメントと同じである、ということを証明する。
    	* <s>When making this equivilance check, differences which could have been caused by allowed or required LRS processing of "id", "authority", "stored", "timestamp", or "version" MUST be ignored.</s>
この同等性をチェックする時に、許可または必要とされる LRS の "id", "authority", "stored", "timestamp" または "version" の処理がもたらす差は無視されなければならない。
    * <s>If the JWS header includes an X.509 certificate, validate the signature against that certificate as defined in JWS.</s>
JWS ヘッダーが X.509 証明書を含むならば、JWS で定義されている手法で、その署名を証明書で認証する。

* <s>Clients MUST NOT assume a signature is valid simply because an LRS has accepted it.</s>
クライアントは、単に LRS が受入れたという理由で、署名が有効であると仮定してはならない。

##### <s>Details</s>詳細

<s>Signed Statements include a JSON web signature (JWS) as an attachment. This allows the original serialization of the Statement to be included along with the signature. For interoperability, the "RSA + SHA" series of JWS algorithms have been selected, and for discoverability of the signer X.509 certificates SHOULD be used.</s>
署名付きステートメントは、JSON web署名(JWS) を添付文書として含む。このことにより、ステートメントの原本をシリアル化したものが、署名とともに添付されることが可能となる。相互運用性のために、JWS のアルゴリズムの "RSA+SHA" シリーズが選択され、署名者の発見可能性のために、X.509 証明書が使われるべきである。

<s>See <a href="#AppendixF">Appendix F: Example Signed Statement</a> for an example.</s>
例は<a href="#AppendixF">Appendix F: 署名ステートメント例</a>を参照。 

##### <s>Note</s>注記: <s>The step of validating against the included X.509 certificate is intended as a way to catch mistakes in the signature, not as a security measure. Clients MUST NOT assume a signature is valid simply because an LRS has accepted it. The steps to authenticate a signed Statement will vary based on the degree of certainty required and are outside the scope of this specification.</s>
含まれる X.509 証明書に対して認証するステップは、安全対策のためではなく、署名の中に誤りを発見するためのものである。クライアントは、LRS が受入れたという理由だけで、署名が有効であると仮定してはならない。署名付きステートメントを認証するステップは、要求される確実性の度合いにより変化するものであり、この仕様の規定外である。

<a name="misctypes"/>
## 5.0 <s>Miscellaneous Types</s> 各種タイプ</a>

<a name="miscdocument"/>
### 5.1 <s>Document</s> ドキュメント</a>

###### <s>Description</s>説明
<s>The Experience API provides a facility for Activity Providers to save arbitrary data in the form of documents, which may be related to an Activity, Agent, or combination of both.</s>

xAPI により、アクティビティプロバイダは、アクティビティやエージェント、もしくは、それら双方の組合せに関連したドキュメント形式による任意のデータを記録することが容易になる。

###### <s>Details</s>詳細
<table>
 <tr>
	<th>
<s>Property</s>プロパティ
	</th><th>
<s>Type</s>タイプ
	</th><th>
<s>Description</s>説明
	</th>
 </tr>
 <tr>
	<td>
ID
	</td><td>
String
	</td><td>
<s>Set by AP, unique within state scope (learner, activity).</s>

AP（アクティビティプロバイダ）によって規定される。それは状態の範囲（学習者、アクティビティ）内において一意である。
	</td>
 </tr>
 <tr>
	<td>
updated
	</td><td>
Timestamp
	</td><td>
<s>When the document was most recently modified.</s>ドキュメントが最後に修正された時刻
	</td>
 </tr>
 <tr>
	<td>
contents
	</td><td>
Arbitrary binary data
	</td><td>
<s>The contents of the document.</s>ドキュメントの内容
	</td>
 </tr>
</table>

###### <s>Note</s>注記
<s>In the REST binding, State is a document, not an Object. The id is stored in the IRL, updated is HTTP header information, and contents is the HTTP document itself.</s>

RESTバインディングにおいて、状態はドキュメントでありオブジェクトでは無い。そのID は IRL に指定され、updated は HTTP ヘッダ情報として、contents は HTTP のドキュメントそのものとして与えられる。

<a name="misclangmap"/>
### 5.2 <s>Language Map</s> 言語マップ</a>

###### <s>Description</s>説明

<s>A language map is a dictionary where the key is an [RFC 5646 Language Tag](http://tools.ietf.org/html/rfc5646), and the value is a string in the language specified in the tag. This map should be populated as fully as possible based on the knowledge of the string in question in different languages.</s>

言語マップは [RFC 5646言語タグ](http://tools.ietf.org/html/rfc5646) をキーとし、そのタグで指定された言語で記述された文字列を値とする辞書である。このマップは、その対象となる異なる言語において、その文字列の知識が及ぶ限り出来るだけ充実させるべきである。

<a name="miscext"/>
### 5.3 <s>Extensions</s> 拡張</a>

###### <s>Description</s>説明

<s>Extensions are defined by a map. The keys of that map MUST be IRLs, and the values MAY be any JSON value or data structure. The meaning and structure of extension values under an IRL key are defined by the person who coined the IRL, who SHOULD be the owner of the IRL, or have permission from the owner. The owner of the IRL SHOULD make a human-readable description of the intended meaning of the extension supported by the IRL accessible at the IRL. A learning record store MUST NOT reject an Experience API Statement based on the values of the extensions map.</s>

拡張はマップによって定義される。マップのキーは IRL でなければならないこと、そして、その値は JSON の値か、もしくはデータ構造であってよい。IRL キー下における拡張が持つ値の意味と構造は、IRL の作成者（その IRL の所有者であるべき者）、または所有者から権限を与えられている者によって定義される。IRL の所有者は、IRL でサポートされた拡張が意図する意味の人が理解できる形式での説明を、IRL が指定する場所においてアクセス可能にするべきである。LRS は拡張マップの値に基づく xAPI のステートメントを拒絶してはならない。

<s>Extensions are available as part of Activity Definitions, as part of statement context, or as part of some statement result. In each case, they're intended to provide a natural way to extend those elements for some specialized use. The contents of these extensions might be something valuable to just one application, or it might be a convention used by an entire community of practice.</s>

拡張は、アクティビティ定義の一部として、ステートメント文脈の一部として、もしくは、あるステートメントの結果の一部として利用可能なものである。それぞれのケースにおいて、それらは、ある特定の利用のための要素を拡張する自然な方法を提供しようとするものである。こうした拡張のコンテンツは、ある一つのアプリケーションに役立つものであったり、もしくは、実践コミュニティ全体における規定かもしれない。

<s>Extensions should logically relate to the part of the statement where they are present. Extensions in Statement context should provide context to the core experience, while those in the result should provide elements related to some outcome. For Activities, they should provide additional information that helps define an Activity within some custom application or community.</s>

拡張は、それらが現れるステートメントの対応部分と論理的に関連づけられるべきである。ステートメント文脈における拡張は、中心的な経験に対する文脈を提供すべきであり、一方で、結果の文脈では、いくつかの成果に関連する要素を提供すべきである。アクティビティにおいては、拡張は、あるカスタムアプリケ－ションやコミュニティ内におけるアクティビティを定義することの手助けとなる追加情報を提供すべきである。

###### <s>Note</s>注記

<s>A statement should not be totally defined by its extensions, and be meaningless otherwise. Experience API Statements should be capturing experiences among Actors and Objects, and SHOULD always strive to map as much information as possible into the built in elements, in order to leverage interoperability among Experience API conformant tools.</s>

一つのステートメントが、その拡張によって全体的に定義されてしまい、拡張なしには無意味になってしまうようにすべきではない。xAPI のステートメントはアクタとオブジェクト間の経験を記録すべきであり、そして、xAPI 準拠のツール間の相互運用性を大きく高めるために、できるだけ多くの情報を既存の要素にマッピングするよう、常に努力すべきである。

<a name="miscmeta"/>
### 5.4 <s>Identifier Metadata</s> 識別子メタデータ</a>

###### <s>Description</s>説明

<s>There are several types of IRI identifiers used in this specification:</s>

この仕様において利用される、いくつかの IRI 識別子のタイプが存在する：

* <a href="#verb"><s>Verb</s>動詞</a>
* <a href="#acturi"><s>Activity id</s>アクティビティ ID</a>
* <a href="#acttype"><s>Activity type</s>アクティビティタイプ</a>
* <a href="#miscext"><s>extension key</s>拡張キー</a>
* <a href="#attachmentUsage"><s>attachment usage type</s>添付文書使用タイプ</a>

<s>For Activity ids, see <a href="#actdef">Activity Definition</a>.</s>

アクティビティ ID については、<a href="#actdef">アクティビティ定義</a> を参照のこと。

<s>For all other identifiers, metadata MAY be provided in the following JSON format:</s>

すべての他の識別子については、メタデータは次の JSON フォーマットで提供される：

<table>
 <tr>
	<th>
<s>Property</s>プロパティ
	</th><th>
<s>Type</s>タイプ
	</th><th>
<s>Description</s>説明
	</th>
 </tr><tr>
	<td>
name
	</td><td>
<a href="#misclangmap">Language Map</a>
	</td><td>
<s>The human readable/visual name</s>人が読める／見られる 名前
	</td></tr>
 <tr>
	<td>
description
	</td><td>
<a href="#misclangmap">Language Map</a>
	</td><td>
<s>description</s>説明
	</td>
 </tr>
</table>

###### <s>Requirements</s>必要条件

<s>If metadata is provided, both name and description SHOULD be included.</s>

メタデータが提供されている場合、名前と説明の双方が含まれるべきである。

<s>*For any of the identifier IRIs above, if the IRI is an IRL that was coined for use with this specification, the owner of that IRL SHOULD make this JSON metadata available at that IRL when the IRL is requested and a Content-Type of "application/json" is requested.</s>

* 上記、識別子としての IRI において、もし、IRI が本仕様によって作られた IRL であるなら、その IRL の所有者は、その IRL が "Content-Type: application/json" がリクエストされた際に、この JSON メタデータを IRL の場所において利用可能にすべきである。

<s>* If this metadata is provided as described above, it is the canonical source of information about the identifier it describes.</s>

* 上記に記述されたメタデータが提供された場合、それは、その識別子説明の情報の正規のソースである。

<s>* Other sources of information MAY be used to fill in missing details, such as translations, or take the place of this metadata entirely if it was not provided or cannot be loaded.This MAY include metadata in other formats stored at the IRL of an identifier, particularly if that identifier was not coined for use with this specification.</s>

* 翻訳等不足する詳細情報を埋めるために、あるいは提供されていなかったり読み込めない場合は、このメタデータを完全に置き換えるために、他の情報源を使ってもよい。特にその識別子が本仕様で利用する目的で作成されなかった場合においては、このメタデータは、識別子の IRL に記録された他のフォーマット内のメタデータを含んでもよい。

<s><a href="#verb-lists-and-repositories">As with Verbs</a>, we recommend that Activity Providers look for and use established, widely adopted identifiers for all types of IRI identifier other than Activity id. Where an identifier already exists, the Activity Provider:</s>

<a href="#verb-lists-and-repositories">動詞と同様</a>、他のアクティビティ ID 以外のあらゆるタイプの IRI 識別子のために既に使われていて広く採用されている識別子を、アクティビティ・プロバイダは探して利用することを推奨する。識別子が既に存在する場合は、アクティビティ・プロバイダは：

<s>* SHOULD use the corresponding existing identifier;</s>

* 対応する既存の識別子を使用するべきであり；

<s>* MAY create and use their own Verbs where a suitable identifier does not already exist.</s>

* 適切な既存の識別子が存在していなければ、独自の動詞を作成して使用してもよい。

<a name="rtcom"/></a>

## 6.0 <s>Runtime Communication</s> ランタイム通信

<s>Sections 6 and 7 detail the more technical side of the Experience API, dealing with how Statements are transferred between Activity Provider and LRS. A number of libraries 
are under development for a range of technologies (including JavaScript) which handle this part of the specification. It therefore may not be necessary for content developers to fully understand every detail of this part of the specification.</s>

６章、７章では、アクティビティプロバイダと LRS の間でどのようにステートメントが転送されるかについて取扱いながら、 xAPI のより技術的な側面を詳しく説明する。いくつかのライブラリは、この章の仕様を取り扱う一連の技術（ Java Script を含む）に対して開発中である。そのため、コンテンツ開発者がこの章の仕様を全て詳細に理解しなくてもよい。

<a name="encoding"/></a>

### 6.1 <s>Encoding</s> エンコーディング

###### <s>Requirement</s>必要事項
* <s> All strings MUST be encoded and interpreted as UTF-8. </s> 
全ての文字列は UTF-8 形式でエンコードし解釈しなければならない。

<a name="apiversioning"/></a>

### 6.2 <s>API Versioning</s> API のバージョン管理

###### <s>Rationale</s>背景

<s>Future revisions of the specification may introduce changes such as properties added to Statements.</s>

本仕様の将来の改訂版においては、ステートメントにプロパティを追加するような変更を導入するかもしれない。

<s>Systems retrieving Statements may then receive responses that include Statements of different versions. The version header allows for these version differences to be handled correctly, and to ascertain that no partial or mixed LRS version implementations exist.</s>

そのため、ステートメントを読み出すシステムは、異なるバージョンのステートメントを含むレスポンスを受け取るかもしれない。このようなバージョンの違いをバージョンヘッダにより正確に取り扱うことができ、不完全または混在状態のバージョンの実装が存在していないことを確かめることができる。

<s>Using Semantic Versioning will allow Clients and LRSs to reliably know whether they're compatible or not as the specification changes.</s>

セマンティックバージョニングを利用することで、仕様に変更が加えられても、クライアントと LRS は相互に互換性があるかどうかを確実に知ることができる。

###### <s>Requirements</s>必要条件

<s>Every request from a Client and every response from the LRS must include an HTTP header with the name “X-Experience-API-Version" and the version as the value.
Starting with 1.0.0, xAPI will be versioned according to [Semantic Versioning 1.0.0](http://semver.org/spec/v1.0.0.html)</s>

クライアントからのすべてのリクエストや LRS からの全てのレスポンスは、"X-Experience-API-Version" を名前、バージョンを値とする HTTP ヘッダーを持たなければならない。1.0.0版より、 xAPI は [セマンティックバージョニング 1.0.0](http://semver.org/spec/v1.0.0.html) に従いバージョン付けされる。

<s>Example</s>例:  ``X-Experience-API-Version : 1.0.0``

####### <s>Requirements for the LRS</s>LRS に対する必要条件:

* <s>MUST include the "X-Experience-API-Version" header in every response.</s>
全てのレスポンスに "X-Experience-API-Version" ヘッダを含めなければならない。
* <s>MUST set this header to "1.0.0".</s>
このヘッダには "1.0.0" を設定しなければならない。
* <s>MUST accept requests with a version header of "1.0" as if the version header was "1.0.0".</s>
バージョンヘッダに ”1.0” が設定されたリクエストは、バージョンヘッダが ”1.0.0” であるとみなして受入れなければならない。
* <s>MUST reject requests with version header prior to "1.0.0" unless such requests are routed to a fully conformant implementation of the prior version specified in the header.</s>
"1.0.0" より前のバージョンヘッダが設定されたリクエストは、ヘッダ内に指定された以前のバージョンに完全に準拠した実装へ渡されない限りは拒否しなければならない。
* <s>MUST reject requests with a version header of "1.1.0" or greater.</s>
"1.1.0" もしくはそれ以上のバージョンヘッダが設定されたリクエストは拒否しなければならない。
* <s>MUST make these rejects by responding with an HTTP 400 error including a short description of the problem.</s>
これらの拒否は、問題に関する短い説明を含んだ HTTP 400 エラーで応答しなければならない。


####### <s>Requirements for the Client</s>クライアントに対する必要条件:

* <s>SHOULD tolerate receiving responses with a version of "1.0.0" or later.</s>
"1.0.0" もしくはそれ以降のバージョンが設定された応答を受けとることを許容すべきである。
* <s>SHOULD tolerate receiving data structures with additional properties.</s>
追加されたプロパティを含むデータ構造を受けとることを許容すべきである。
* <s>SHOULD ignore any properties not defined in version 1.0.0 of the spec.</s>
バージョン “1.0.0” 仕様で規定されていないプロパティはすべて無視すべきである。


####### <s>Converting Statements to other versions</s>他のバージョンへのステートメントの変換:

* <s>Systems MUST NOT convert Statements of newer versions into a prior version format, e.g., in order to handle version differences.</s>
システムは、例えばバージョンの違いを取り扱うために新しいバージョンのステートメントを前のバージョン形式に変換してはならない。
* <s>Systems MAY convert Statements of older versions into a newer version only by following the methods described in <a href="#AppendixE">Appendix E: Converting Statements to 1.0.0</a>.</s>
システムは、 <a href="#AppendixE">Appendix E：1.0.0へステートメントを変換</a> に記載された方法に従った場合のみ 古いバージョンのステートメントを新しいバージョン形式に変換してもよい。

<a name="concurrency"/></a>
### 6.3 <s>Concurrency</s> 同時実行

##### <s>Description</s>説明
<s>Concurrency control makes certain that an API consumer does not PUT changes based on old data into an LRS.</s>

同時実行制御は API 利用者が LRS に古いデータに基づく変更を PUT しないことを確実にする。

##### <s>Details</s>詳細
<s>xAPI will use HTTP 1.1 entity tags ([ETags](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.19)) to implement optimistic concurrency control in the portions of the API where PUT may overwrite existing data, being:</s>

xAPI は、 PUT が既存のデータ実体を上書きする API の一部において、楽観的な同時実行制御を実装するために、 HTTP1.1 エンティティタグ（ [ETags](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.19) ）を使用する予定である。その部分は次の通り。

* State API
* Agent Profile API 
* Activity Profile API

<s>The State API will permit PUT Statements without concurrency headers, since state conflicts are unlikely. The requirements below only apply to Agent Profile API and Activity Profile API.</s>

状態の矛盾がほとんど発生しないことから、 ステート API は同時実行ヘッダなしの PUT ステートメントを許容する予定である。以下の必要条件は、 エージェントプロファイル API とアクティビティプロファイル API にのみ適用される。


##### <s>Client requirements</s>クライアントに対する必要条件

<s>An xAPI Client using either Agent Profile API or Activity Profile API…</s>

Agent Profile API または Activity Profile API を使用する xAPI クライアントは

* <s>MUST include the [If-Match](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.24) header or MUST include the If-None-Match header.</s>
[If-Match](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.24) ヘッダを含むか If-None-Match ヘッダを含まなければならない。 

##### <s>LRS requirements</s>LRS に対する必要条件

<s>The LRS that responds to a GET request</s>

LRS が GET リクエストに応答する際には

* <s>MUST add an ETag HTTP header to the response.</s>
ETag HTTP ヘッダをレスポンスに追加しなければならない。
* <s>MUST calculate the value of this header to be a hexidecimal string of the  SHA-1 digest of the contents.</s>
このヘッダの値がコンテンツ部分の SHA-1 ダイジェストの 16 進数文字列となるように計算しなければならない。
* <s>MUST enclose the header in quotes.</s>
ヘッダを引用符で囲わなければならない。

<s>The reason for specifying the LRS ETag format is to allow API consumers that can't read the ETag header to calculate it themselves.</s>

LRS ETag 形式を設定する理由は、 ETag ヘッダを読込めない API 利用者が自らその値を計算することを可能とするためである。

<s>The LRS that responds to a PUT request</s>

LRS が PUT リクエストに応答する際には

* <s>MUST handle the [If-Match](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.24) header as described in RFC2616, HTTP 1.1 if it contains an ETag, in order to detect modifications made after the consumer last fetched the document.</s>
RFC2616 (HTTP 1.1) にて説明されるとおり、 If-Match ヘッダが ETag を含む場合は、利用者が文書を最後に取り込んだあとに修正が行われたか検出するために [If-Match](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.24) ヘッダを取り扱わなければならない。
* <s>MUST handle the [If-None-Match](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.26) header as described in RFC2616, HTTP 1.1 if it contains "*", in order to to detect when there is a resource present that the consumer is not aware of.</s>
RFC2616 （"*" を含む場合は HTTP1.1 ）で定める [If-None-Match](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.26) ヘッダを、利用者が気づかないリソース提供があるときに検出するために取り扱わなければならない。


<s>If the header precondition in either of the above cases fails, the LRS</s>

上記のいずれの場合もヘッダの前提条件に当てはまらない場合、 LRS は

* <s>MUST return HTTP status 412 "Precondition Failed".</s>
HTTP status 412 "Precondition Failed" を返さなければならない。
* <s>MUST NOT make a modification to the resource.</s>
リソースを変更させてはならない。

<s>If a PUT request is received without either header for a resource that already exists, the LRS</s>

PUT リクエストをいずれのヘッダもなく既存のリソースに対して受け取った場合は、 LRS は

* <s>MUST return HTTP status 409 "Conflict".</s>
HTTP status 409 "Conflict" を返さなければならない。
* <s>MUST return a plain text body explaining that the consumer SHOULD</s>
利用者がすべきことを説明するテキスト形式の本文を返さなければならない。
	- <s>check the current state of the resource.</s>
	リソースの現在の状態をチェックすべきである。
	- <s>set the "If-Match" header with the current ETag to resolve the conflict.</s>
	競合を解消するために現在の ETag を設定した "If-Match" ヘッダをセットすべきである。
* <s>MUST NOT make a modification to the resource.</s>
リソースを変更してはならない。


<a name="security"/></a>

### 6.4 <s>Security</s> セキュリティ

###### <s>Rationale</s>背景

<s>In order to balance interoperability and the varying security requirements of different environments, several authentication options are defined.</s>

相互運用性と異なる環境における様々なセキュリティの必要条件とのバランスを取るために、いくつかの認証オプションを定める。

###### <s>Requirement</s>必要条件

<s>The LRS MUST support authentication using at least one of the following methods:</s>

LRS は次の手段のうち少なくとも一つを使用した認証をサポートしなければならない。

- <s>OAuth 1.0 (rfc5849), with signature methods of "HMAC-SHA1", "RSA-SHA1", and "PLAINTEXT"</s>
OAuth 1.0 （ RFC 5849 ） ( "HMAC-SHA1"、"RSA-SHA1" および "PLAIN TEXT" の署名方式を利用する）
- <s>HTTP Basic Authentication</s>
HTTP　基本認証
- <s>Common Access Cards (implementation details to follow in a later version)</s>
Common Access Cards　（実装は今後のバージョンでフォローされ詳細化される）
- <s>The LRS MUST handle making, or delegating, decisions on the validity of Statements,and determining what operations may be performed based on the credentials used.</s>
LRS はステートメントの有効性に関して判断するか委任するかを決め、使用された証明書に基づいて、どのような処理を行うかを決定しなければならない。


###### <s>Authentication scenarios</s>認証シナリオ

<s>The below matrix describes the possible authentication scenarios.</s>

以下の表において、想定される認証のシナリオを示す。


<s>A **registered application** is an application that will authenticate to the LRS as an OAuth  consumer that has been registered with the LRS.
A **known user** is a user account on the LRS, or on a system which the LRS trusts to define users.</s>

**登録されたアプリケーション**とは、 LRS に既に登録された OAuth consumer として LRS に認証されているアプリケーションである。**認識された利用者**とは LRS または LRS がユーザを定義することを委託しているシステム上のユーザアカウントである。

<table border="1">
<tr><th></th><th><s>Known user</s>認識された利用者</th><th><s>User unknown</s>認識されていない利用者</th></tr>
<tr>
<td><s>Application is registered</s>アプリケーションが登録される場合</td>
<td><s>Standard workflow for OAuth.</s>OAuth に対応する標準ワークフローが適用される。</td>
<td><s>LRS trusts application to access xAPI without additional user credentials. OAuth token steps are not invoked</s>LRS は付加的な利用者証明書を持たない xAPI アクセスを行うアプリケーションを信頼する。 OAuth トークンステップは呼び出されない。
</td>
</tr>
<tr>
<td><s>Application is not registered</s>アプリケーションが登録されていない場合</td>
<td><s>The application Agent is not identified as a registered Agent and the LRS cannot make assumptions on its identity.</s>アプリケーションエージェントは登録されたエージェントとして識別されないので、 LRS はその識別を前提とすることはできない。</td>
<td></br></td>
</tr>
<tr>
<td><s>No application</s>アプリケーションがない場合</td>
<td><s>HTTP Basic Authentication is used instead of OAuth, since no application is involved.</s>アプリケーションが呼び出されないため、 HTTP 基本認証が OAuth の代わりに利用される。</td>
<td></br></td>
</tr>
<tr>
<td><s>No authentication</s>認証なしの場合</td>
<td align="center"colspan="2"><s>MAY be supported by the LRS, possibly for testing purposes.</s>テストを目的とする場合などで LRS によりサポートされてもよい。</td>

</tr>

</table> 

	
<a name="authdefs"/></a>

#### 6.4.1 <s>How To Handle Each Scenario</s> 各シナリオの取り扱い方法

##### <s>General</s>概要

* <s>The LRS must record the application's name and a unique consumer key (identifier).</s>
LRS はアプリケーションの名前と一意な consumer key （識別子）を記録しなければならない。
* <s>The LRS must provide a mechanism to complete this registration, or delegate to another system that provides such a mechanism.The means by which this registration is accomplished are not defined by OAuth or the xAPI.</s>
LRS はこの登録を完了するためのメカニズムを提供するか、同様のメカニズムを提供する別システムに委譲しなければならない。この登録を実現する方法は OAuth または xAPI で定義されていない。

##### <s>Application registered + known user</s>登録されたアプリケーション＋認識された利用者

* <s>Use endpoints below to complete the standard workflow.</s>
標準ワークフローを完了するために以下のエンドポイントを利用する。
* <s>If this form of authentication is used  to record Statements and no  authority  is specified, the LRS should record the  authority  as a group consisting of an Agent representing the registered application, and an Agent representing the known user.</s>
この認証形式がステートメントを記録する際に何も権限が指定されずに利用される場合は LRS は登録されたアプリケーションを表すエージェントと認識されたユーザを表すエージェントからなるグループとして権限を記録すべきである。

##### <s>Application registered + user unknown</s>登録されたアプリケーション＋認識されていない利用者

* <s>LRS will honor requests that are signed using OAuth with the registered application's credentials and with an empty token and token secret.</s>
 LRS は登録されたアプリケーションの証明書と空のトークンとトークンシークレットで OAuth を使用して署名されたリクエストを受け取るだろう。
* <s>If this form of authentication is used  to record Statements and no  authority  is specified, the LRS should record the  authority as the Agent representing the registered application.</s>
もしこの認証形式がステートメントの記録の際に何も権限が指定されずに使用される場合は、 LRS は登録されたアプリケーションを表すエージェントとしての権限を記録すべきである。

##### <s>Application not registered + known user</s> 登録されていないアプリケーション＋認識された利用者

* <s>Use a blank consumer secret;</s>
空白の consumer secret を利用すること。
* <s>Call "Temporary Credential" request;</s>
"Temporary Credential" リクエストを呼び出すこと。
* <s>Specify "consumer_name" and other usual parameters;
User will then see "consumer_name" plus a warning that the identity of the application requesting authorization cannot be verified.</s>
"consumer name" と他の一般的なパラメータを設定すること。そのため、利用者は "consumer name" と認証をリクエストしたアプリケーションの識別子が確認できないという警告を目にするだろう。
* <s>the LRS MUST record an  authority that includes both that application and the authenticating user, as a group,since OAuth specifies an application.</s>
OAuth がアプリケーションを指定するため、 LRS はアプリケーションと認証しているユーザの両方をグループとして含む権限を記録しなければならない。

##### <s>No application + known user</s> アプリケーションがない＋認識された利用者

* <s>Use username/password combination that corresponds to an LRS login.</s>
LRS ログインに対応するユーザ名／パスワードの結合情報を用いること。
* <s>Authority to be recorded as the Agent identified by the login, **unless…**</s>
権限はログインにより識別されるエージェントとして記録される。但し、以下の場合を除く。
	* <s>other Authority is specified **and…**</s>
	他の権限情報が指定される。かつ、
	* <s>LRS trusts the known user to specify this Authority.</s>
	LRS はこの権限情報を指定する認識された利用者を信頼する。

##### <s>No authorization</s>認証なし

* <s>Requests should include headers for HTTP Basic Authentication based on a blank username and password, in order to distinguish an explicitly unauthenticated request from a request that should be given a HTTP Basic Authentication challenge.</s>
明らかに認証されていないリクエストと　HTTP　基本認証チャレンジが提供されなければならないリクエストを区別するために、リクエストには空白のユーザ名とパスワードに基づく　HTTP　基本認証のためのヘッダを含めるべきである。


##### <s>Requirements</s>必要条件

<s>The LRS:</s>

LRS を

* <s>MUST be able to be configured for complete support of the xAPI:</s>
 xAPI へ完全に対応させるためには以下のとおり設定できなければならない。
	* <s>With any of the above methods.</s>上記のいずれかの手順によること。
	* <s>In any of the workflow scenarios above.</s>上記のいずれかのワークフローシナリオによること。
* <s>MAY (for security reasons):</s> （セキュリティ上の理由で）以下のとおり設定してもよい。
	* <s>Support a subset of the above methods.</s>上記の手順のサブセットをサポートすること。
	* <s>Limit the known users or registered applications.</s>認識された利用者または登録されたアプリケーションを制限すること。
* <s>SHOULD at a minimum supply Oauth with "HMAC-SHA1" and "RSA-SHA1" signatures.</s>
 "HMACS-SHA1" および "RSA-SHA1" による署名を用いた OAuth を最低でも提供すべきである。


<a name="oauthscope"/></a>

#### 6.4.2 <s>OAuth Authorization Scope</s> OAuth 認証スコープ

##### <s>Description</s>説明
<s>These are recommendations for scopes which should enable an LRS and an application communicating using the xAPI to negotiate a level of access which accomplishes what the
application needs while minimizing the potential for misuse. The limitations of each scope are in addition to any security limitations placed on the user account associated with the request.</s>

LRS と xAPI を利用して通信するアプリケーションが、間違った利用の可能性を最小限にしつつアプリケーションの要求に応えるアクセスレベルを調整できるようにするためにスコープに対する推奨を示す。それぞれのスコープの制限は、リクエストに関連するユーザアカウントへの任意のセキュリティ制限に加わるものである。


##### <s>Requirements</s>必要条件
<s>The LRS:</s>

LRS は

* <s>MUST accept a scope parameter as defined in [OAuth 2.0](https://tools.ietf.org/html/draft-ietf-oauth-v2-22%22%20%5Cl%20%22section-3.3);</s>
[OAuth 2.0](https://tools.ietf.org/html/draft-ietf-oauth-v2-22%22%20%5Cl%20%22section-3.3) で定義されたスコープパラメータを受入れなければならない。
* <s>MUST assume a requested scope of "statements/write" and "statements/read/mine" if no
scope is specified;</s>
もしスコープが指定されていない場合は "statements/write" と "statements/read/mine" のリクエストスコープと仮定しなければならない。
* <s>MUST support the scope of "all" as a minimum;</s> 
最低限として "all" のスコープをサポートしなければならない。
* <s>MAY support other scopes.</s>
その他のスコープをサポートしてもよい。

<s>An xAPI Client:</s>

xAPI クライアントは

* <s>SHOULD request only the minimal needed scopes, to increase the chances that the request will be granted.</s>
リクエストが許可される機会を増やすために、最低限必要なスコープのみ要求すべきである。

##### <s>Details</s>詳細

<s>The following table lists xAPI scope values:</s>

以下の表で xAPI スコープ値を一覧にする。
<table>
	<tr><th><s>Scope</s>スコープ</th><th><s>Permission</s>許可</th></tr>
	<tr><td>statements/write</td><td><s>write any Statement</s>任意のステートメントを書き込む</td></tr>

	<tr>
		<td>statements/read/mine</td>
		<td><s>read Statements written by "me", that is with an authority matching what the LRS would assign if writing a Statement with the current token.</s>"自分" が書いたステートメントを読込む、つまり、現在のトークンでステートメントを書くと仮定した場合に LRS が割り当てるであろう権限に一致した権限を所有していることに相当する。

		</td>
	</tr>
	<tr><td>statements/read</td><td><s>read any Statement</s>任意のステートメントを読込む</td>
	<tr>
		<td>state</td>
		<td><s>read/write state data, limited to Activities and Actors associated with the current token to the extent it is possible to determine this relationship.</s>この関係を決定できる範囲で現在のトークンに関係するアクティビティとアクタに制限された状態データを読込む／書込む。
		</td>
	</tr>
	<tr>
		<td>define</td>
		<td><s>(re)Define Activities and Actors. If storing a Statement when this is not granted, ids will be saved and the LRS may save the original Statement for audit purposes, but should not update its internal representation of any Actors or Activities.</s>アクティビティとアクタを（再）定義する。もし認められないままステートメントを保存した場合、 ids が保存され LRS は調査を目的としたステートメントの原文を保存するかもしれないが、 アクタまたはアクティビティの内部表現で上書きすべきではない。
		</td>
	</tr>
	<tr>
		<td>profile</td>
		<td><s>read/write profile data, limited to Activities and Actors associated with the current token to the extent it is possible to determine this relationship.</s>この関係を決定できる範囲で現在のトークンに関係するアクティビティとアクタに制限されたプロファイルデータを読込む／書込む。
		</td>
	</tr>
	<tr><td>all/read</td><td><s>unrestricted read access</s>制限なしの読込みアクセス</td></tr>
	<tr><td>all</td><td><s>unrestricted access</s>制限なしのアクセス</td></tr>
</table>

###### <s>OAuth Extended Parameters</s> OAuth 拡張パラメータ 
<s>Note that the parameters "consumer_name" and "scope" are not part of OAuth 1.0, and therefore if used should be passed as query string or form parameters, not in the OAuth header.</s>

"consumer_name" や "scope" といったパラメータは OAuth1.0 に含まれないので注意すること。そのためもし使われていた場合は OAuth ヘッダとしてではなくクエリ文字列やフォームパラメータとみなして引き渡すべきである。


###### <s>OAuth Endpoints </s> OAuth エンドポイント
<table>
	<tr>
		<th>Name</th>
		<th>Endpoint</th>
		<th>Example</th>
	</tr>
	<tr>
		<td><s>Temporary Credential Request</s>Temporary Credential リクエスト</td>
		<td>OAuth/initiate</td>
		<td>http://example.com/xAPI/OAuth/initiate</td>
	</tr>
	<tr>
		<td><s>Resource Owner Authorization</s>Resource Owner 認可</td>
		<td>OAuth/authorize</td>
		<td>http://example.com/xAPI/OAuth/authorize</td>
	</tr>
	<tr>
		<td><s>Token Request</s>トークンリクエスト</td>
		<td>OAuth/token</td>
		<td>http://example.com/xAPI/OAuth/token </td>
	</tr>
</table>

###### <s>Example</s> 例 
<s>The list of scopes determines the set of permissions that is being requested. For example, an instructor might grant "statements/read" to a reporting tool, but the LRS would still limit that tool to Statements that the instructor could read if querying the LRS with their credentials directly (such as Statements relating to their students).</s>

スコープのリストは、リクエストされている許可の設定を決定する。例えば、インストラクタは "statements/read" をレポートツールのために許可するかもしれない。しかし、 LRS はインストラクタが LRS に対して直接認証をして問合せをすることによって読込めるステートメント（たとえば自分の生徒に関するステートメント）のみにツールを制限することができる。

## 7.0 Data Transfer (REST)
<s>
This section describes that the xAPI consists of 4 sub-APIs: Statement, State, Agent, and Activity Profile. These four sub-APIs of the Experience API are handled via RESTful HTTP methods. The Statement API can be used by itself to track learning records.
</s>

このセクションでは xAPI を構成する４つのサブ API （ステートメント、ステート、エージェント プロファイル、アクティビティ プロファイル）について説明する。4つのサブ API  は RESTful な HTTP メソッドによって処理される。ステートメント API は学習記録を追跡するために単独で利用することができる。

<s>
__Note:__ In all of the example endpoints given in the specification, "http://example.com/xAPI/" is the example IRL of the LRS and everything after this represents the endpoint which MUST be used. 
</s>

__注:__この仕様書では、LRS の IRL （エンドポイント）を "http://example.com/xAPI/" としている。実装時には、任意のエンドポイントを必ず用意する必要がある。

######<s> LRS Requirements</s>LRS の必要条件

<s>
The LRS MUST reject with ```HTTP 400 Bad Request``` status (see below) any request to any of these APIs using any parameters:
* the LRS does not recognize (__Note:__ LRSs may recognize and act on parameters not in this specification).
* that match parameters described in this specification in all but case.
</s>

LRS はこれらの API に対するあらゆるリクエストについて、パラメータが以下の条件に該当する場合、```HTTP 400 Bad Request``` ステータスで拒絶しなければならない。

* LRS が認識できないパラメータである（__注釈：__：LRS はこの仕様書に記載のないパラメータを認識して、動作する可能性がある）。

* 本仕様に記述されるパラメータと一致するが、大文字小文字の別が異なる。

<a name="errorcodes" /> 

### 7.1<s> Error Codes</s> エラーコード

<s>
The list below offers some general guidance on HTTP error codes that could be returned from various methods in the API. An LRS MUST return the error code most appropriate to the error condition based on the list below, and SHOULD return a message in the response explaining the cause of the error.  
</s>

以下のリストは API の様々なメソッドから返される HTTP エラーコードに関する一般的なガイドである。LRS はエラーの状況に最も合致するエラーコードを返さなければならない。また LRS はエラーの原因を説明するメッセージを返すべきである。

<s>
* ```400 Bad Request``` - Indicates an error condition caused by an invalid or missing argument. The term "invalid arguments" includes malformed JSON or invalid Object structures.
</s>

* ```400 Bad Request``` - 引数が無効もしくは欠落していることを起因とするエラー状態を表す。「引数が無効」とは、不正な JSON または無効なオブジェクト構造を含む。

<s>
* ```401 Unauthorized``` - Indicates that authentication is required, or in the case authentication has been posted in the request, that the given credentials have been refused.
</s>

* ```401 Unauthorized``` - 認証が必要、もしくはリクエスト中の認証資格情報が拒否されたことを表す。


<s>
* ```403 Forbidden``` - Indicates that the request is unauthorized for the given credentials. Note this is different than refusing the credentials given. In this case, the credentials have been validated, but the authenticated Client  is not allowed to perform the given action.
</s>

* ```403 Forbidden``` - 与えられた認証資格情報ではリクエストを拒否されたことを表す。認証資格情報自体の拒否とは異なるので注意すること。このケースでは、認証資格情報は確認されたものの、認証されたクライアントでは指定されたアクションを実行することが許可されなかったことを表す。

<s>
* ```404 Not Found``` - Indicates the requested resource was not found. May be returned by any method that returns a uniquely identified resource, for instance, any State or Agent Profile or Activity Profile API call targeting a specific document, or the method to retrieve a single Statement.
</s>

* ```404 Not Found``` - 要求されたリソースが見つからなかったことを表す。その例としては特定の文書を対象とする ステート、エージェントプロファイル、アクティビティプロファイル API callや、単一のステートメントを返すメソッドなどが挙げられる。

<s>
* ```409 Conflict``` - Indicates an error condition due to a conflict with the current state of a resource, in the case of State API, Agent Profile or Activity Profile API calls, or in the Statement PUT call. See Section [6.3 concurrency](#concurrency) for more details.
</s>

* ```409 Conflict``` - ステート API やエージェントプロファイル API 、アクティビティプロファイル API、もしくはステートメント PUT 呼び出しの際に発生する、リソースの現在の状態との競合を起因とするエラー状態を表す。詳細は[6.3 同時実行](#concurrency) を参照のこと。


<s>
* ```412 Precondition Failed``` - Indicates an error condition due to a failure of a precondition posted with the request, in the case of State or Agent Profile or Activity Profile API calls. See Section [6.3 Concurrency](#concurrency) for more details.
</s>

* ```412 Precondition Failed``` - State API や Agent Profile API 、Activity Profile API 呼び出しの際に発生する、リクエストともにポストされた前提条件の失敗に起因するエラーを表す。詳細は[6.3 同時実行](#concurrency)を参照のこと。


<s>
* ```413 Request Entity Too Large``` - Indicates that the LRS has rejected the Statement or document because its size is larger than the maximum allowed by the LRS. The LRS is free to
choose any limit and MAY vary this limit on any basis, e.g., per authority, but MUST be configurable to accept Statements of any size.
</s>

* ```413 Request Entity Too Large``` - LRS が許容するサイズを超過していることを理由に、LRS がステートメントもしくはドキュメントを拒否したことを表す。LRS はサイズの制限値を自由に設定できる。また LRS は任意の条件ごと（例：権限単位）にこの制限値を変更してもよい。ただしステートメントについてはあらゆるサイズのものを受け入れるよう設定できなければならない。

<s>
* ```500 Internal Server Error``` - Indicates a general error condition, typically an unexpected exception in processing on the server.
</s>

* ```500 Internal Server Error``` - サーバ上に予期しない例外処理が発生した場合など、一般的なエラー状態を表す。

<a name="stmtapi"/> 

### 7.2<s> Statement API</s> ステートメント API

<s>
The basic communication mechanism of the Experience API.  
</s>

xAPI の基本的な通信メカニズム


######<s> PUT Statements</s> PUT ステートメント

<s>
Example endpoint: ```http://example.com/xAPI/statements```
</s>

エンドポイントの例: ```http://example.com/xAPI/statements```

<s>
Stores Statement with the given id.
</s>

与えられた id でステートメントを格納する。

<s>
Returns: ```204 No Content```  
</s>

戻り値: ```204 No Content```


<table>
	<tr><th><s>Parameter</s>パラメータ</th><th><s>Type</s>タイプ</th><th><s>Default</s>デフォルト値</th><th><s>Description</s>説明</th></tr>
	<tr><td>statementId</td><td>String</td><td> </td><td><s>Id of Statement to record</s>記録するためのステートメント id</td></tr>
</table>

######<s> POST Statements</s> POST ステートメント

<s>
Example endpoint: ```http://example.com/xAPI/statements```
</s>

エンドポイントの例: ```http://example.com/xAPI/statements```

<s>
Stores a Statement, or a set of Statements. Since the PUT method targets a specific Statement id, POST must be used rather than PUT to save multiple Statements, or to save one Statement without first generating a Statement id. An alternative for systems that generate a large amount of Statements is to provide the LRS side of the API on the AP, and have the LRS query that API for the list of updated (or new) Statements periodically. This will likely only be a realistic option for systems that provide a lot of data to the LRS.  
</s>

ステートメントもしくはステートメント群を格納する。PUT メソッドは特定のステートメント id をターゲットにするので、複数のステートメントを保存する場合や、ステートメント ID  を最初に生成せずに単一のステートメントを保存する場合には PUT ではなく POST を使用しなければならない。大量のステートメント群を生成するシステムのための代替策は AP 上の API の LRS 側を提供することである。そして定期的にステートメント群を更新（もしくは新規）するよう LRS からその API を照会する。これは大量のデータを LRS に提供するようなシステムにおいてのみ現実的なオプションといえる。

<s>
Returns: ```200 OK```, Statement id(s) (UUID).  
</s>

戻り値: ```200 OK```, ステートメント id(s) (UUID).

######<s> Common requirements for PUT and POST</s> PUT と POST に対する一般的な必要条件

<s>
An LRS MUST NOT make any modifications to its state based on a receiving a Statement with a statementID that it already has a Statement for. Whether it responds with
```409 Conflict``` or ```204 No Content```, it MUST NOT modify the Statement or any other Object.
</s>

既にステートメントの割り当てられているステートメント ID をもったステートメントを受信した場合でも、LRS はその状態にいかなる変更も行ってはならない。```409 Conflict```もしくは```204 No Conent```で応答するかにかかわらず、ステートメントもしくはその他のあらゆるオブジェクトを変更してはならない。

<s>
If the LRS receives a Statement with an id it already has a Statement for, it SHOULD verify the received Statement matches the existing one and return ```409 Conflict``` if they do not match.
</s>

もし LRS が受信したステートメントの ID がすでに LRS に存在していれば、受信したステートメントが既存のものと合致するか検証し、合致しない場合には ```409 Conflict``` を返すべきである。

<s>
The LRS MAY respond before Statements that have been stored are available for retrieval.
</s>

LRS は格納されたステートメントが検索可能となる前に応答してもよい。


###### GET Statements

<s>
Example endpoint: ```http://example.com/xAPI/statements```
</s>

エンドポイントの例: ```http://example.com/xAPI/statements```

<s>
This method may be called to fetch a single Statement or multiple Statements. If the　statementId or　voidedStatementId parameter is specified a single Statement is returned.
</s>

このメソッドは単一のステートメントもしくは複数のステートメントを取得するために呼び出すことができる。ステートメント ID もしくは voidedStatement id がパラメータとして指定されている場合には、単一のステートメントが戻り値として返される。


<s>
Otherwise returns: A [StatementResult](#retstmts) Object,
a list of Statements in reverse chronological order based on "stored" time, subject to permissions and maximum list length. If additional results are available, an IRL to retrieve them will be included in the StatementResult 
Object.
</s>

それ以外の戻り値：権限と最大リスト長の制約の中で、"stored" 時間の新しい順に並べたステートメントのリストである [ステートメントの結果](#retstmts) オブジェクト。追加の結果が利用可能な場合には、それらを取得するための IRL　は　StatementResult　オブジェクトに含まれる。

<s>
Returns: ```200 OK```, Statement or [Statement Result](#retstmts) (See [Section 4.2](#retstmts) for details)
</s>

戻り値: ```200 OK```, ステートメントもしくは[ステートメントの結果](#retstmts) (詳細は[4.2](#retstmts)参照)


<table>
	<tr><th><s>Parameter</s>パラメータ</th><th><s>Type</s>タイプ</th><th><s>Default</s>デフォルト値</th><th><s>Description</s>説明</th></tr>
	<tr><td>statementId</td><td>String</td><td> </td><td><s>ID of Statement to fetch</s>取得するためのステートメントの ID</td></tr>
	<tr><td>voidedStatementId</td><td>String</td><td> </td><td><s>ID of voided Statement to fetch. see <a href="#voidedStatements">Voided Statements</a></s>取得するための無効なステートメントの ID。詳細は <a href="#voidedStatements">VoidedStatement</a> を参照。</td></tr>
	<tr><td>agent</td><td>Agent or Identified Group Object (JSON)</td><td> </td>
		<td><s>Filter, only return Statements for which the specified Agent or group is the Actor or Object of the Statement.</s>指定されたエージェントやグループが、ステートメントのアクタやオブジェクトであるステートメントのみをフィルタして返す。
			<ul><li><s> Agents or identified groups are equal when the same Inverse Functional Identifier is used in each Object compared and those Inverse Functional Identifiers have equal values.</s>各オブジェクトで同じ逆機能識別子が利用され、それらの逆機能識別子が等しい値を持つ場合、エージェントもしくは識別されたグループは等しい。
			</li><li><s>For the purposes of this filter, groups that have members which match the specified Agent based on their Inverse Functional Identifier as described above are considered a match</s>このフィルタの目的のために、上記逆機能識別子に基づいて同一であるとみなされた特定のエージェントと一致するメンバを持つグループは等しいとみなされる。</li></ul>
			<br><br><s>See <a href="#actor">agent/group</a> Object definition for details.</s>詳細は<a href="#actor">エージェント/グループオブジェクトの定義</a>参照。
		</td>
	</tr>
	<tr><td>verb</td><td>Verb id (IRI)</td><td> </td>
		<td><s>Filter, only return Statements matching the specified verb id.</s>フィルタし、特定の verb id とマッチしたステートメントのみを返す。</td>
	</tr>
	<tr><td>activity</td><td>Activity id (IRI)</td><td> </td>
		<td><s>Filter, only return Statements for which the Object of the Statement is an Activity with the specified id.</s>フィルタし、指定された id をもつアクティビティをオブジェクトとするステートメントのみを返す。
		</td>
	</tr>
	<tr><td>registration</td><td>UUID</td><td> </td>
		<td><s>Filter, only return Statements matching the specified registration id. Note that although frequently a unique registration id will be used for one Actor assigned to one Activity, this should not be assumed. If only Statements for a certain Actor or Activity should be returned, those parameters should also be specified.</s>フィルタし、指定した registration id に一致するステートメントを返す。あるアクティビティに割り当てられるあるアクタに対して、一意の登録 ID が割り当てられることが多いが、それを前提とすべきでないことに注意が必要である。特定のアクタもしくはアクティビティのためのステートメントのみが返されるべき場合には、それらのパラメータもあわせて指定すべきである。</td>
	</tr>
	<tr><td>related_activities</td><td>Boolean</td><td>False</td>
		<td><s>Apply the Activity filter broadly. Include Statements for which the Object, any of the context Activities, or any of those properties in a contained SubStatement match the Activity parameter, instead of that parameter's normal behavior. Matching is defined in the same way it is for the 'Activity' parameter."</s>アクティビティ フィルタを広く適用する。オブジェクトや、あらゆる文脈のアクティビティ、もしくはパラメータ本来の正常な動作ではなく、アクティビティ パラメータにマッチするサブ ステートメントを含むプロパティをもつステートメントを含む。マッチングはアクティビティ パラメータと同様の方式で定義される。
		</td>
	</tr>
	<tr><td>related_agents</td><td>Boolean</td><td>False</td>
		<td><s>Apply the Agent filter broadly. Include Statements for which the Actor, Object, authority, instructor, team, or any of these properties in a contained SubStatement match the Agent parameter, instead of that parameter's normal behavior. Matching is defined in the same way it is for the 'agent' parameter.</s>エージェント フィルタを広く適用する。パラメータ本来の正常な動作ではなく、エージェント パラメータにマッチするアクタやオブジェクト、権限、インストラクタ、チームもしくはそれらのあらゆるプロパティをもつプロパティを含む。マッチングはエージェント パラメータと同様の方式で定義される。
		</td>
	</tr>
	<tr><td>since</td><td>Timestamp</td><td> </td>
		<td><s>Only Statements stored since the specified timestamp (exclusive) are returned.</s>指定された  timestamp よりあと（ timestamp の時刻は含まない）に記録されたステートメントのみを返す。</td>
	</tr>
	<tr><td>until</td><td>Timestamp</td><td> </td>
		<td><s>Only Statements stored at or before the specified timestamp are returned.</s>指定された timestamp と同時またはそれ以前に記録されたステートメントのみを返す。</td>
	</tr>
	<tr><td>limit</td><td>Nonnegative Integer</td><td>0</td>
		<td><s>Maximum number of Statements to return. 0 indicates return the maximum the server will allow.</s>返すステートメントの最大数。0 はサーバが許容する最大値を返すことを表す。</td>
	</tr>
	<tr><td>format</td><td>String: ("ids", "exact", or "canonical")</td><td>exact</td>
		<td><s>If "ids", only include minimum information necessary in Agent, Activity, and group Objects to identify them. For anonymous groups this means including the minimum information needed to identify each member.
		If "exact", return Agent, Activity, and group Objects populated exactly as they were when the Statement was received.</s>「 ids 」の場合、エージェントやアクティビティ、そしてグループオブジェクトを識別するために最低限必要な情報のみを含む。匿名グループにおいては各メンバを識別するために必要な最低限の情報を意味する。「 exact 」の場合、ステートメントが受理された際と完全に同一なエージェントやアクティビティ、そしてグループオブジェクトを返す。<br/><br/>
			
		<s>If "canonical", return Activity Objects populated with the canonical definition of the Activity Objects as determined by the LRS, after applying the language filtering process defined below, and return the original Agent Objects as in "exact" mode.

		Activity Objects contain Language Map Objects for name and description. Only one language should be returned in each of these maps.</s>「 canonical 」の場合、以下に定義する言語フィルタを適用し、オリジナルのエージェント オブジェクトを「 exact 」モードで返したのち、 LRS により判断され、正規の定義を含んだアクティビティ オブジェクトを返す。アクティビティ オブジェクトは名前と説明のために Language Map オブジェクトを含む。これらのマップではひとつの言語のみが返されるべきである。<br/><br/>

		<s>In order to provide these strings in the most relevant language, the LRS will apply the Accept-Language header as described in <a href="http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html">
		RFC 2616</a> (HTTP 1.1), except that this logic will be applied to each language map individually to select which language entry to include, rather than to the resource (list of Statements) as a whole.

		An LRS requesting Statements for the purpose of importing them SHOULD use a format of "exact".</s>これらの文字列を最も関連度の高い言語で提供するために LRS は、 <a href="http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html">RFC 2616</a> (HTTP 1.1)で解説されている通り、Accept-Language ヘッダを適用する。ただし、全体としてリソース（ステートメントのリスト）に適用される場合ではなく、このロジックが各言語マップに個別に適用される場合はこの限りではない。LRS がこれらをインポートすることを目的としてステートメントを要求する場合には、「 exact 」フォーマットを用いるべきである。
		</td>
	</tr>
	<tr><td>attachments</td><td>Boolean</td><td>False</td>
		<td><s>If true LRS MUST use the multipart response format and include all attachments as described in <a href="#attachments">4.1.11. Attachments</a>, otherwise the LRS MUST NOT include attachment raw data and MUST send the prescribed response with Content-Type application/json.</s>trueの場合、LRS は<a href="#attachments">4.1.11. Attachments</a>で解説している通り、マルチパートレスポンスフォーマットを用いなければならず、あらゆる添付文書を含めなければならない。それ以外の場合には LRS は添付文書の生データを含めてはならず、Content-Type application/json の形式で所定の応答を送信しなければならない。</td>
	</tr>
	<tr><td>ascending</td><td>Boolean</td><td>False</td>
		<td><s>If true, return results in ascending order of stored time</s>true の場合、格納された時間の昇順で結果を返す。</td>
	</tr>
</table>

<s>
The LRS MUST reject with an ```HTTP 400``` error any requests to this resource which:
</s>

以下の場合、LRS はこれらリソースに対するリクエストに対して```HTTP 400```エラーで拒絶しなければならない。

<s>
* contain both statementId and voidedStatementId parameters
</s>
* ステートメント ID と voidedStatementId 両方のパラメータを含む場合。

<s>
* contain statementId or voidedStatementId parameters, and also contain any other parameter besides "attachments" or "format".
</s>

* ステートメント ID または voidedStatementId のパラメータを含み、また「 attachments 」もしくは「 format 」以外のパラメータを含む場合。

<s>
The LRS MUST include the header "X-Experience-API-Consistent-Through", in <a href="https://en.wikipedia.org/wiki/ISO_8601#Combined_date_and_time_representations">ISO 8601
combined date and time</a> format, on all responses to Statements requests, with a value of the timestamp for which all Statements that have or will have a "stored" property before that time are known with reasonable certainty to be available for retrieval. This time SHOULD take into account any temporary condition, such as excessive load, which might cause a delay in Statements becoming available for retrieval.
</s>

LRS はステートメントリクエストに対するあらゆる応答に対して「 X-Experience-API-Consistent-Through 」ヘッダを <a href="https://en.wikipedia.org/wiki/ISO_8601#Combined_date_and_time_representations">ISO 8601 combined date and time</a> フォーマットを含まなければならない。その値は、指定されたタイプスタンプ以前の "stored" プロパティを持つ全てのステートメントが、妥当な確からしさで取り出し可能になっていることを示すタイムスタンプである。この時間は、ステートメントが検索可能となるまでの遅延をもたらす過剰負荷などの任意の一時的な状態を考慮すべきである。

######<s> Note</s> 注記

<s>
Due to query string limits, this method MAY be called using POST and form fields if necessary. The LRS MUST differentiate a POST to add a Statement or to list Statements based on the parameters passed.  
</s>

クエリ文字列の制限により、このメソッドは POST と form filed を使用して呼び出してもよい。LRS は、ステートメントを追加するための POST と、複数のステートメントをリストする POST とを、渡されるパラメータに応じて区別しなければならない。

<a name="queryStatementRef" /></a>


######<s> Filter Conditions for StatementRefs</s> StatementRefs のためのフィルタ条件

<s>
For filter parameters which are not time or sequence based (that is, other than since, until, or limit), Statements which target another Statement (by using a StatementRef as the Object of the Statement) will meet the filter condition if the targeted Statement meets the condition. The time and sequence based parameters must still be applied to the Statement making the StatementRef in this manner. This rule applies recursively, so that "Statement a" is a match when a targets b which targets c and the filter conditions described above match for "Statement c".
</s>

フィルタパラメータが時間やシーケンスベースでない場合（つまり since、until もしくは limit 以外の場合）で、（ステートメントのオブジェクトとして StatementRef を使用して）他のステートメントを参照する時、その参照先のステートメントが条件を満たす場合は、参照元のステートメント自身も条件を満たす。時間やシーケンスベースのパラメータはこの方法で StatementRef を行うステートメントに対しても適用する必要がある。このルールは再帰的に適用される。すなわち、ステートメント A が B を参照し、B が C を参照している状況で、上に示すフィルタ条件がステートメント C に当てはまるなら、ステートメント A もフィルタ対象となる。

<s>
For example, consider the Statement "Ben passed explosives training", and a follow up Statement: "Andrew confirmed \<StatementRef to original Statement\>". The follow up
Statement will not mention "Ben" or "explosives training", but when fetching Statements with an Actor filter of "Ben" or an Activity filter of "explosives training", both Statements match and will be returned so long as they fall into the time or sequence being fetched.
</s>
たとえば、"ベンは爆発物のトレーニングに合格した"というステートメントと、"アンドリューは\<StatementRef to original Statement\>を確認した"というフォローアップのステートメントがあったとする。フォローアップステートメントでは、"ベン"にも"爆発物のトレーニング"にも触れていないが、アクタのフィルタで"ベン"またはアクティビティのフィルタで"爆発物のトレーニング"を指定してステートメントを取り出した場合、時間とシーケンスの条件に合致している限り、両方のステートメントがマッチし返答される。

<s>
This section does not apply when retrieving Statements with statementId or voidedStatementId.
</s>
これらの条件はステートメントをステートメント ID や voidedStatementId で検索した場合には適用されされない。


######<s> Note</s> 注釈

<s>
StatementRefs used in the statement field in context do not affect how Statements are filtered.
</s>
コンテキストのステートメント フィールドで用いられる StatementRefs は、ステートメントのフィルタに対して影響を与えない。

<a name="voidedStatements" /></a>

######<s> Voided Statements</s> 無効なステートメント

<s>
The LRS MUST not return any Statement which has been voided, unless that Statement has been requested by voidedStatementId. The LRS MUST still return any Statements targetting the voided 
Statement when retrieving Statements using explicit or implicit time or sequence based retrieval, unless they themselves have been voided, as described in [the section on filter conditions for StatementRefs](#queryStatementRef). This includes the voiding Statement, which cannot be voided. Reporting tools can identify the presence and statementId of any voided Statements by the target of the voiding Statement. Reporting tools wishing to retrieve voided Statements SHOULD request these individually by voidedStatementId.
</s>

LRS は voidedStatementId によりリクエストされたステートメントでない限り、無効となったステートメントを返してはならない。LRS は、 [StatementRefs によるフィルタ条件](#queryStatementRef) で示した通り、時間またはシーケンス基準による直接・間接の取り出しの場合には、ステートメント自体が無効化されている場合を除き、無効化されたステートメントを参照しているステートメントも返さなければならない。これは、自分自身を無効化することのできない、無効化ステートメントを含む。レポーティングツールは無効化ステートメントのターゲットを用いてあらゆる無効化ステートメントの存在とステートメント ID を識別することができる。レポーティングツールは voidedStatementId を用いて個別に無効化されたステートメントをリクエストすべきである。

<a name="docapis" />

### 7.3<s> Document APIs</s> ドキュメント API

<s>
The three Document APIs provide [document](#miscdocument) storage for learning activity providers and Agents. The details of each API are found in the following sections, and the information in this section applies to all three APIs.
</s>

3つのドキュメント API はアクティビティプロバイダとエージェントのためにドキュメントストレージを提供する。各 API の詳細は次のセクションで説明する。このセクションで説明する内容はこれら3つの API すべてに適用される。


######<s> New Agents and Activities</s> 新規エージェントとアクティビティ

<s>
An Activity Provider MAY send documents to any of the document APIs for Activities and Agents that the LRS does not have prior knowledge of. The LRS MUST NOT reject documents on the basis of not having prior knowledge of the Activity and/or Agent. 
</s>

アクティビティプロバイダは、LRS が事前知識を持たないアクティビティとエージェントに関する文書を、いずれの文書 API に送ってもよい。LRS はアクティビティおよび/またはエージェントの予備知識を持っていないことを理由にしてドキュメントを拒絶してはならない。



######<s> POST to store application/json arrays of variables</s> application/json 配列を変数に格納するための POST メソッド

<table>
	<tr>
		<th>API</th>
		<th><s>Method</s>メソッド</th>
		<th><s>Endpoint</s>エンドポイント</th>
		<th><s>Example</s>例</th>
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

<s>
APs MAY use Documents of content type "application/json" to store sets of variables. For example a document contains:
</s>

AP は変数セットを格納するためにコンテンツタイプ application/json のドキュメントを利用してもよい。
例えばドキュメントは次の情報を含むとする：

```
{
	"x" : "foo",
	"y" : "bar"
}
```  

<s>
When an LRS receives a POST request with content type application/json for an existing document also of content type application/json, it MUST merge the posted document with the existing document. In this context merge is defined as:
</s>

LRS がコンテンツタイプが application/json の既存のドキュメントについて、POST リクエストをコンテンツタイプ application/json で受け取った場合、ポストされてきたドキュメントを既存ドキュメントにマージしなければならない。この文脈において「マージ」とは次のように定義する。

<s>
* de-serialize the Objects represented by each document
</s>

* 複数の文書に分割されたオブジェクトをデシリアライズする

<s>
* for each property directly defined on the Object being posted, set the corresponding property on the existing Object equal to the value from the posted Object.
</s>
  
* ポストされたオブジェクトに直接定義されたプロパティごとに、既存オブジェクトに対して対応するプロパティの値をセットする。

<s>  
* store any valid json serialization of the existing Object as the document referenced in the request
</s>

* リクエストの参考ドキュメントとして、既存オブジェクトの有効な json のシリアライズ性を格納します。

<s>
Note that only top-level properties are merged, even if a top-level property is an Object the entire contents of each original property are replaced with the entire contents of each new property.
</s>

最上位階層のプロパティのみがマージされることに注意が必要である。たとえ最上位階層のプロパティ（の値）がオブジェクトであっても、それぞれの元のプロパティの値すべてが、新しいプロパティの値に完全に置き換えられる。

<s>
For example, this document is POSTed with the same id as the existing document above:
</s>

例えば、既に存在する上記ドキュメントを POST したものと同一 ID で、再度このドキュメントが POST された場合：

```
{
	"x" : "bash",
	"z" : "faz"
}
```  

<s>
the resulting document stored in the LRS is:
</s>

LRS に格納されるドキュメントの結果は次の通りとなる。

```
{
	"x" : "bash",
	"y" : "bar",
	"z" : "faz"
}
```

<s>
If the original document exists, and the original document or the document being posted do not have a Content-Type: of "application/json", or if either document can not be parsed as JSON Objects, the LRS MUST respond with HTTP status code 400 "Bad Request", and MUST NOT update the target document as a result of the request. 
</s>

オリジナルのドキュメントが存在し、元のドキュメントもしくは post されてきたドキュメントのコンテンツタイプが application/json でない場合、あるいはどちらのドキュメントも JSON オブジェクトとして解析できない場合、LRS は HTTP のステータスコード400 "Bad Request" で応答しなければならず、リクエストに対してターゲットとするドキュメントをアップデートしてはならない。

<s>
If the original document does not exist, the LRS MUST treat the request the same as it would a PUT request and store the document being posted.
</s>

元のドキュメントが存在しない場合、LRS は PUT リクエストと同様に取り扱い、POST されてきたドキュメントを保存しなければならない。


<s>
If the merge is successful, the LRS MUST respond with HTTP 
status code 204 "No Content".
</s>

マージが成功した場合、LRS は HTTP ステータスコード 204 "No Content" で応答しなければならない。


<s>
If an AP needs to delete a property, it SHOULD use a PUT request to replace the whole document as described below. 
</s>

AP がプロパティを削除する必要がある場合、後述するように PUT リクエストを用いてドキュメント全体を差し替えるべきである。

<a name="stateapi"/> 

### <s>7.4 State API</s> ステートAPI

<s>
Generally, this is a scratch area for Activity Providers that do not have their own internal storage, or need to persist state across devices. When using the State API, be aware of how the stateId parameter affects the semantics of the call. If it is included, the GET and DELETE methods will act upon a single defined state document identified by "stateId". Otherwise, GET will return the available ids, and DELETE will delete all state in the context given through the other parameters.  
</S>

一般に、これはアクティビティプロバイダが独自の内部記憶領域を持たない、あるいは、複数の端末間で状態の共有が必要な場合などに利用されるスクラッチ領域である。ステート API を使用するとき、 stateId パラメータが呼び出しの意味にどのような影響を与えるかということに注意すべきである。もし stateId パラメータが含まれる場合、 GET と  DELETE メソッドは、 "stateId" によって指定される単独のステート文書に対して実行される。そうでない場合は、 GET は利用可能な ID を返し、 DELETE はその他のパラメータを通じて与えられた文脈の全てのステートを削除する。

###### <s>PUT | POST | GET | DELETE activities/state</s>PUT | POST | GET | DELETE アクティビティ/ステート

<s>
Example endpoint: http://example.com/xAPI/activities/state
</s>

エンドポイント例: http://example.com/xAPI/activities/state

<s>
Stores, fetches, or deletes the document specified by the given stateId that exists in the context of the specified Activity, Agent, and registration （if specified）.  
</s>

アクティビティ、エージェント、そして登録（存在すれば）からなる文脈に与えられた stateId によって指定される文書を記録、取り込み、又は削除する。


Returns: (PUT | POST | DELETE) 204 No Content, (GET) 200 OK - State Content  
<table>
	<tr><th><s>Parameter</s>パラメータ</th><th><s>Type</s>タイプ</th><th><s>Required</s>必須</th><th><s>Description</s>説明</th></tr>
	<tr><td>activityId</td><td>String</td><td>yes</td>
		<td><s>The Activity id associated with this state.</s>このステートと関連したアクティビティID</td>
	</tr>
	<tr><td>agent</td><td>JSON</td><td>yes</td>
		<td><s>The Agent associated with this state.</s>このステートと関連したエージェント</td>
	</tr>
	<tr><td>registration</td><td>UUID</td><td>no</td>
		<td><s>The registration id associated with this state.</s>このステートと関連した登録</td>
	</tr>
	<tr><td>stateId</td><td>String</td><td>yes</td>
		<td><s>The id for this state, within the given context.</s>与えられた文脈における、このステートのID</td>
	</tr>
</table>

###### <s>GET activities/state</s>GET アクティビティ/ステート

<s>
Example endpoint: http://example.com/xAPI/activities/state
</s>

エンドポイント例: http://example.com/xAPI/activities/state

<s>
Fetches ids of all state data for this context （Activity + Agent \［ + registration if specified\］）. If "since" parameter is specified, this is limited to entries that have been stored or updated since the specified timestamp（exclusive）.  
</s>

この文脈（アクティビティ＋エージェント［指定された場合の登録］）における全てのステートデータのidを取り込む。 もし、 "since" パラメータが指定されている場合、指定された timestamp （その時刻を含まない）よりあとに記録または更新されたエントリのみに制限される。


<s>
Returns: 200 OK, Array of ids  
</s>

戻り値: 200 OK, Array of ids

<table>
	<tr><th><s>Parameter</s>パラメータ</th><th><s>Type</s>タイプ</th><th><s>Required</s>必須</th><th><s>Description</s>説明</th></tr>
	<tr><td>activityId</td><td>String</td><td>yes</td>
		<td><s>The Activity id associated with these states.</s>
		これらのステートと関連したアクティビティ ID</td>
	</tr>
	<tr><td>agent</td><td>JSON</td><td>yes</td>
		<td><s>The Actor associated with these states.</s>
		これらのステートと関連したエージェント</td>
	</tr>
	<tr><td>registration</td><td>UUID</td><td>no</td>
		<td><s>The registration id associated with these states.</s>
		これらのステートと関連した登録</td>
	</tr>
	<tr><td>since</td><td>Timestamp</td><td>no</td>
		<td><s>Only ids of states stored since the specified timestamp (exclusive) are returned.</s>
			指定された timestamp（その時刻を含まない）よりあとに記録されたステート ID のみが返却される。

</td>
	</tr>
</table>

###### <s>DELETE activities/state</s>DELETE アクティビティ/ステート

<s>
Example endpoint: http://example.com/xAPI/activities/state
</s>

エンドポイント例: http://example.com/xAPI/activities/state

<s>
Deletes all state data for this context （Activity + Agent \[+ registration if specified\]）.  
</s>

この文脈（アクティビティ＋エージェント［指定された場合は登録］）における全てのステートデータを削除する。

<s>
Returns: 204 No Content  
</s>

戻り値: 204 No Content

<table>
	<tr><th><s>Parameter</s>パラメータ</th><th><s>Type</s>タイプ</th><th><s>Required</s>必須</th><th><s>Description</s>説明</th></tr>
	<tr><td>activityId</td><td>String</td><td>yes</td>
		<td><s>The Activity id associated with this state.</s>このステートと関連したアクティビティ ID</td>
	</tr>
	<tr><td>agent</td><td>JSON</td><td>yes</td>
		<td><s>The Actor associated with this state.</s>このステートと関連したエージェント</td>
	</tr>
	<tr><td>registration</td><td>UUID</td><td>no</td>
		<td><s>The registration id associated with this state.</s>このステートと関連した登録 ID
</td>
	</tr>
</table>


<a name="actprofapi"/> 

### <s>7.5 Activity Profile API</s> アクティビティ プロファイル API

<s>
The Activity Profile API is much like the State API, allowing for arbitrary key / document pairs to be saved which are related to an Activity. When using the Activity Profile API for manipulating documents, be aware of how the profileId parameter affects the semantics of the call. If it is included, the GET and DELETE methods will act upon a single defined document identified by "profileId". Otherwise, GET will return the available ids, and DELETE will delete all state in the context given through the other parameters.  
</s>

アクティビティ プロファイル API は、ステート API と似ているものであり、任意のキー / 文書のペアをアクティビティに関連させて保存することを可能とする。文書操作のためにアクティビティ プロファイル API を使用するとき、 profileId パラメータが呼び出しの意味にどのような影響を与えるかということに注意すべきである。もし profileId パラメータが含まれる場合、 GET と  DELETE メソッドは、 "profileId" によって定義される単独の文書に従って実行される。 そうでない場合は、 GET は利用可能な id を返し、 DELETE はその他のパラメータを通じて与えられた文脈の全てのステートを削除する。

<s>
The Activity Profile API also includes a method to retrieve a full description of an Activity from the LRS.  
</s>

アクティビティ プロファイル API もまた、 LRS からアクティビティの全ての説明を読みだすメソッドを含んでいる。

###### <s>GET activities</s>GET アクティビティ

<s>
Example endpoint: http://example.com/xAPI/activities
</s>

エンドポイント例: http://example.com/xAPI/activities

<s>
Loads the complete Activity Object specified.  
</s>

指定された全アクティビティオブジェクトをロードする。

<s>
Returns: 200 OK - Content  
</s>

戻り値: 200 OK, Content

<table>
	<tr><th><s>Parameter</s>
		パラメータ</th><th><s>Type</s>タイプ</th><th><s>Required</s>必須</th><th><s>Description</s>説明</th></tr>
	<tr><td>activityId</td><td>String</td><td>yes</td>
		<td><s>The id associated with the Activities to load.</s>
ロードするアクティビティと関連したアクティビティ ID</td>
	</td>
</table>

###### <s>PUT | POST | GET | DELETE activities/profile</s>PUT | POST | GET | DELETE アクティビティ/プロファイル

<s>
Example endpoint: http://example.com/xAPI/activities/profile
</s>

エンドポイント例: http://example.com/xAPI/activities/profile

<s>
Saves/retrieves/deletes the specified profile document in the context of the specified Activity.  
</s>

指定されたアクティビティの文脈で特定のプロファイル文書を保存 / 読み出し / 削除する。

<s>
Returns: (PUT | POST | DELETE) 204 No Content, (GET) 200 OK - Profile Content  
</s>

戻り値: (PUT | POST | DELETE) 204 No Content, (GET) 200 OK, Profile Content


<table>
	<tr><th><s>Parameter</s>パラメータ</th><th><s>Type</s>タイプ</th><th><s>Required</s>必須</th><th><s>Description</s>説明</th></tr>
	<tr><td>activityId</td><td>String</td><td>yes</td>
		<td><s>The Activity id associated with this profile.</s>
このプロファイルと関連したアクティビティ ID</td>
	</tr>
	<tr><td>profileId</td><td>String</td><td>yes</td>
		<td><s>The profile id associated with this profile.</s>
このプロファイルと関連したプロファイル ID</td>
	</tr>
</table>

###### <s>GET activities/profile</s>GET アクティビティ/プロファイル

<s>
Example endpoint: http://example.com/xAPI/activities/profile
</s>

エンドポイント例: http://example.com/xAPI/activities/profile

<s>
Loads ids of all profile entries for an Activity. If "since" parameter is specified, this is limited to entries that have been stored or updated since the specified timestamp （exclusive).  
</s>

アクティビティのために全てのプロファイルエントリの id をロードする。 もし、 "since" パラメータが指定されている場合、指定された timestamp （その時刻を含まない）よりあとに記録または更新されたエントリのみに制限される。

<s>
Returns: 200 OK - List of ids  
</s>

戻り値: 200 OK, List of ids

<table>
	<tr><th><s>Parameter</s>パラメータ</th><th><s>Type</s>タイプ</th><th><s>Required</s>必須</th><th><s>Description</s>説明</th><tr>
	<tr><td>activityId</td><td>String</td><td>yes</td>
		<td><s>The Activity id associated with these profiles.</s>

これらのプロファイルと関連したアクティビティ ID</td>
	</tr>
	<tr><td>since</td><td>Timestamp</td><td>no</td>
		<td><s>Only ids of profiles stored since the specified timestamp (exclusive) are returned.</s>
指定された timestamp （その時刻を含まない）よりあとに記録されたプロファイル ID のみが返却される</td>
	</tr>
</table>


<a name="agentprofapi"/> 

### <s>7.6 Agent Profile API</s> エージェント プロファイル API

<s>
The Agent Profile API is much like the State API, allowing for arbitrary key / document pairs to be saved which are related to an Agent. When using the Agent Profile API for manipulating documents, be aware of how the profileId parameter affects the semantics of the call. If it is included, the GET and DELETE methods will act upon a single defined document identified by "profileId". Otherwise, GET will return the available ids, and DELETE will delete all state in the context given through the other parameters.  
</s>

エージェントプロファイル API はステート API と似ているものであり、任意のキー / 文書のペアをエージェントと関連させて保存することを可能とする。 文書操作のためにエージェント プロファイル API を使用するとき、 profileId パラメータが呼び出しの意味にどのような影響を与えるかということに注意すべきである。もし profileId パラメータが含まれる場合、 GET と DELETE メソッドは、 "profileId" によって定義される単独の文書に従って実行される。そうでない場合は、 GET は利用可能な id を返し、 DELETE はその他のパラメータを通じて与えられた文脈の全てのステートを削除する。

<s>
The Agent Profile API also includes a method to retrieve a special Object with combined information about an Agent derived from an outside service, such as a directory service.  
</s>

エージェントプロファイル API もまた、ディレクトリサービスなどの外部サービスから派生したエージェントに関する結合情報と一体となった、特殊なオブジェクトを読みだすメソッドを含んでいる。

###### <s>GET agents</s>GET エージェント

<s>
Example endpoint: http://example.com/xAPI/agents
</s>

エンドポイント例: http://example.com/xAPI/agents

<s>
Return a special, Person Object for a specified Agent. The Person Object is very similar to an Agent Object, but instead of each attribute having a single value, each attribute has an array value, and it is legal to include multiple identifying properties. Note that the argument is still a normal Agent Object with a single identifier and no arrays. Note that this is different from the FOAF concept of person, person is being used here to indicate a person-centric view of the LRS Agent data, but Agents just refer to one persona （a person in one context）.  
</s>

指定されたエージェントに対して特別の、 Person オブジェクトを返却する。 Person オブジェクはエージェントオブジェクトと非常に似ているが、それぞれの要素が単一の値を持つ代わりに、それそれの要素が配列の値を持ち、複数の識別プロパティを含むことが許されている。ここで留意すべきは、引数が単一の識別子を持つ通常のエージェントオブジェクトであり、配列ではないということである。これは FOAF の person 概念とは異なることに注意してほしい。ここでは person は LRS エージェントデータの person 中心の観点を示す存在として使用されるのであり、しかし、エージェントは、ただ一つのペルソナ（一つの文脈における person ）を参照しているのである。

<s>
An LRS capable of returning multiple identifying properties for a Person Object SHOULD require the connecting credentials have increased, explicitly given permissions. An LRS SHOULD reject insufficiently privileged requests with 403 "Forbidden". If an LRS does not have any additional information about an Agent to return, the LRS MUST still return a Person when queried, but that Person Object will only include the information associated with the requested Agent.  
</s>

Person オブジェクトに複数の識別プロパティを返却する能力がある LRS は、明示的にパーミッションを与えて、連結する資格情報が増加することを要求すべきである。LRS は 403 "Forbidden" で、権限の不十分なリクエストを拒絶すべきである。 LRS がエージェントに関して返答すべき追加情報を持たない場合、照会時に Person を返却しなければならないが、 Person オブジェクトはリクエストされたエージェントと関連した情報のみを含む。


###### <s>Person properties</s>Person プロパティ

<s>
All array properties must be populated with members with the same definition as the similarly named property from Agent Objects.  
</s>

全ての配列プロパティは、エージェントオブジェクトからの類似命名されたプロパティと同じ定義で要素を追加しなければならない。

<table>
	<tr><th><s>Property</s>プロパティ</th><th><s>Type</s>タイプ</th><th><s>Description</s>説明</th></tr>
	<tr><td>objectType</s></td><td>String</td><td>"Person". <s>Required.</s>必須</td></tr>
	<tr><td>name</td><td>Array of strings.</td><td> <s>Optional. List of names of Agents to retrieve.</s>
任意. 読み出しするエージェント名リスト</td></tr>
	<tr>
		<td><a href="http://xmlns.com/foaf/spec/%22%20%5Cl%20%22term_mbox">mbox</a></td>
		<td>Array of IRIs in the form "mailto:email address".</td>
		<td><s>List of e-mail addresses of Agents to retrieve.</s>
読み出しするエージェントのｅメールアドレス リスト</td>
	</tr>
	<tr>
		<td><a href="http://xmlns.com/foaf/spec/%22%20%5Cl%20%22term_mbox_sha1sum">mbox_sha1sum</a></td>
		<td>Array of strings.</td>
		<td><s>List of the SHA1 hashes of mailto IRIs (such as go in an mbox property).</s>
mailto IRIs (例えば mbox プロパティなど).の SHA1 ハッシュリスト</td>
	</tr>
	<tr>
		<td>openid*</td>
		<td>Array of strings.</td>
		<td><s>List of openids that uniquely identify the Agents to retrieve.</s>
読み出しするエージェントを一意的に識別する openid リスト</td>
	</tr>
	<tr>
		<td>account*</td>
		<td>Array of account objects.</td>
		<td><s>List of accounts to match. Complete account Objects (homePage and name) must be provided.</s>
適合するアカウントリスト。完全なアカウントオブジェクト（ホームページや名前）が提供されなければならない。</td>
	</tr>
</table> 

<s>
See also: [Section 4.1.2.1 Agent](#agent).
</s>

参照:  Section 4.1.2.1 Agent.

<s>
Returns: 200 OK - Expanded Agent Object
</s>

戻り値 200 OK, Expanded Agent Object


<table>
	<tr><th><s>Parameter</s>パラメータ</th><th><s>Type</s>タイプ</th><th><s>Required</s>必須</th><th><s>Description</s>説明</th></tr>
	<tr><td>agent</td><td>Object (JSON)</td><td>yes</td>
		<td><s>The Agent representation to use in fetching expanded Agent information.</s>
拡張されたエージェント情報を取り込む際に使用するエージェント表現</td>
	</tr>
</table>  


###### <s>PUT | POST | GET | DELETE agents/profile</s>PUT | POST | GET | DELETE エージェント/プロファイル

<s>
Example endpoint: http://example.com/xAPI/agents/profile
</s>

エンドポイント例: http://example.com/xAPI/agents/profile

<s>
Saves/retrieves/deletes the specified profile document in the context of the specified Agent.  
</s>

指定されたエージェントの文脈で特定のプロファイル文書を保存/読み出し/削除する。

<s>
Returns: (PUT | POST | DELETE) 204 No Content, (GET) 200 OK - Profile Content  
</s>

戻り値:(PUT | POST | DELETE) 204 No Content, (GET) 200 OK - Profile Content  

<table>
	<tr><th><s>Parameter</s>パラメータ</th><th><s>Type</s>タイプ</th><th><s>Required</s>必須</th><th><s>Description</s>説明</th></tr>
	<tr><td>agent</td><td>Object (JSON)</td><td>yes</td>
		<td><s>The agent associated with this profile.</s>
このプロファイルと関連したエージェント</td>
	</tr>
	<tr><td>profileId</td><td>String</td><td>yes</td>
		<td><s>The profile id associated with this profile.</s>
このプロファイルと関連したプロファイル ID</td>
	</tr>
</table>  


###### <s>GET agents/profile</s>GET エージェント/プロファイル

<s>
Example endpoint: http://example.com/xAPI/agents/profile
</s>

エンドポイント例: http://example.com/xAPI/agents/profile

<s>
Loads ids of all profile entries for an Agent. If "since" parameter is specified, this is limited to entries that have been stored or updated since the specified timestamp （exclusive）.  
</s>

エージェントのために全てのプロファイルエントリの ID をロードする。 "since" パラメータが指定されている場合、指定された timestamp （その時刻を含まない）よりあとに記録または更新されたエントリのみに制限される。

<s>
Returns: 200 OK - List of ids  
</s>

戻り値: 200 OK , List of IDs

<table>
	<tr><th><s>Parameter</s>パラメータ</th><th><s>Type</s>タイプ</th><th><s>Required</s>必須</th><th><s>Description</s>説明</th></tr>
	<tr><td>agent</td><td>Object (JSON)</td><td>yes</td>
		<td><s>The Agent associated with this profile.</s>
このプロファイルと関連したエージェント</td>
	</tr>
	<tr><td>since</td><td>Timestamp</td><td>no</td>
		<td><s>Only ids of profiles stored since the specified timestamp 
			(exclusive) are returned</s>
指定された timestamp（その時刻を含まない）よりあとに記録されたプロファイル ID のみが返却される。</td>
	</tr>
</table>  

<a name="aboutresource"/> 

### <s>7.7. About resource</s> About リソース

###### <s>GET about</s>GET about

<s>
Example endpoint: http://example.com/xAPI/about
</s>

エンドポイント例: http://example.com/xAPI/about

###### <s>Description</s>説明


<s>
Returns JSON Object containing information about this LRS, including the xAPI version supported.
</s>

この LRS に関する情報（サポートする xAPI のバージョンを含む）を返答する。

###### <s>Rationale</s>背景

<s>
Primarily this resource exists to allow Clients that suport multiple xAPI versions to decide which version to use when communicating with the LRS. Extensions are included to allow other uses to emerge.
</s>

主に、このリソースは、複数の xAPI バージョンをサポートするクライアントに、 LRS との通信時にどのバージョンを使用するのかを決定させるために存在する。 拡張機能は他の用途が現れることを見越して含まれている。

###### <s>Details</s>詳細

<s>
Returns: 200 OK - Single 'about' JSON document.
</s>

戻り値: 200 OK - Single 'about' JSON document.


<table border="1">
<tr><th><s>property</s>プロパティ</th><th><s>type</s>タイプ</th><th><s>description</s>説明</th></tr>
<td>version</td><td>array of version strings</td><td><s>xAPI versions this LRS supports</s>
この LRS がサポートする xAPI バージョン</td>
</tr>
<tr>
<td>Extensions</td><td><a href="#miscext">Object</a></td><td><s>A map of other properties as needed.</s>
必要に応じた他のプロパティのマップ</td>
</tr>
</table>

###### <s>LRS Requirement</s>LRS 要件

<s>
* MUST return the JSON document described above, with a version property that includes the latest minor and patch version the LRS conforms to, for each major version.
</s>

* 各々のメジャーバージョンに対して、その LRS が準拠する最新のマイナーおよびパッチバージョンを示すバージョンプロパティを含んだ、上述した JSON 文書を戻さなければならない。


    * <s>For version 1.0.0 of this specification, this means that "1.0.0" MUST be included; "0.9" and "0.95" MAY be included. (For the purposes of this requirement, "0.9" and "0.95" are considered major versions.)</s>
     
    * この仕様書のバージョン 1.0.0 では、 "1.0.0" が含まれなければならないことを意味する。 "0.9" や "0.95" は含まれてもよい。（この要件の目的ため、 "0.9" や "0.95" はメジャーバージョンと考えられている。）

* <s>SHOULD allow unauthenticated access to this resource</s>

　　このリソースへの認証されていないアクセスを許可すべきである。

* <s>MUST NOT reject requests based on their version header as would otherwise be required by <a href="#apiversioning"/>6.2 API Versioning</a>.
</s>

　　6.2 API Versioning によって必要とされない限り、バージョンヘッダーに基づいてリクエストを拒絶してはならない。

<a name="cors"/>

### <s>7.8 Cross Origin Requests</s> クロス オリジン リクエスト

<s>
One of the goals of the xAPI is to allow cross-domain tracking, and even though xAPI seeks to enable tracking from applications other than browsers, browsers still need to be supported. Internet Explorer 8 and 9 do not implement Cross Origin Resource Sharing, but rather use their own Cross Domain Request API, which cannot use all of the xAPI as described above due to only supporting "GET" and "POST", and not allowing HTTP headers to be set.  
</s>

xAPI のゴールの一つは、クロスドメイントラッキングを許可することであり、 xAPI がブラウザ以外のアプリケーションからトラッキングができるようにしようとしていても、ブラウザはサポートされる必要がある。 Internet Explorer 8 と 9 は、クロスオリジンリソースシェアリングを実装しておらず、自身のクロスドメインリクエスト API を利用する。 "GET" と "POST" をサポートしているのみで、 HTTP ヘッダーへのセットを許可されていないため、上述した xAPI の全てを利用することはできない。

<s>
The following describes alternate syntax for consumers to use only when unable to use the usual syntax for specific calls due to the restrictions mentioned above. All LRSs must support this syntax.  
</s>

上記の制限により特定の呼び出しのための通常の構文を使用できないときにのみ消費者が使用すべき別の構文について、以下に述べる。全ての LRS はこの構文をサポートしなければならない。

<s>
__Method__: All xAPI requests issued must be POST. The intended xAPI method must be included as the only query string parameter on the request. 
</s>

__メソッド__: 発行された全 xAPI リクエストは POST されなければならない。対象とする xAPI メソッドはリクエスト上の唯一の問合せ文字列パラメータとして含まれなければならない。

<s>
(example: http://example.com/xAPI/statements?method=PUT)  
</s>

（例: http://example.com/xAPI/statements?method=PUT）  


<s>
__Headers__: Any required parameters which are expected to appear in the HTTP header must instead be included as a form parameter with the same name.  
</s>

__ヘッダー__: HTTP ヘッダーに記述すべき必須のパラメータは、同名の form パラメータとして与えなければならない。

<s>
__Content__: If the xAPI call involved sending content, that content must now be encoded and included as a form parameter called "content". The LRS will interpret this content as a UTF-8 string. Storing binary data is not supported with this syntax.  
</s>

__コンテンツ__: xAPI の呼び出しがコンテンツの送信を伴う場合、 "content" と呼ばれるフォームパラメータとしてコンテンツはエンコードされ、含まれなければならない。LRS は UTF-8 文字列としてこのコンテンツを解釈する。バイナリデータの記録は、この構文でサポートされない。

<s>
__Attachments__: Sending attachment data requires sending a
multipart/mixed request, therefore sending attachment data is not supported with this syntax. See [4.1.11. Attachments](#attachments) 
</s>

__添付文書__:添付文書データの送信は、multipart/mixed リクエストを送信する必要があり、それゆえ添付データの送信はこの構文でサポートされない。 4.1.11. Attachments を参照。

<s>
See [Appendix B](#AppendixB) for an example function written in JavaScript which transforms a normal request into one using this alternate syntax.  
</s>

通常リクエストをこの代替構文を使用して変換した JavaScript で記述した関数の例については Appendix B を参照。

<s>
It should also be noted that versions of Internet Explorer lower than 10 do not support Cross Domain Requests between HTTP and HTTPS. This means that for IE9 and lower, if the LRS is on an HTTPS domain, the Client sending the Statement must also be on HTTPS. If the LRS is on HTTP, the Client must be too.  
</s>

Internet Explorer 10 より低いバージョンが、HTTP と HTTPS 間でクロスドメインリクエストをサポートしていないことに留意すべきである。これは IE9 とそれ以下を意味しており、 LRS が HTTPS ドメイン上にある場合、ステートメントを送信するクライアントも HTTPS 上になければならない。 LRS が HTTP 上にある場合は，クライアントも HTTP 上になければならない。

<s>
There may be cases where there is a requirement for the Client Activity Provider to support IE8 and IE9 where the Client code is hosted on a different scheme (HTTP or HTTPS) from the LRS. In these cases, proxy is needed to communicate to the LRS. Two simple solutions might be to 1) set up a proxy pass through on the same scheme as the Client code to the LRS or 2) to host an intermediary server side LRS on the same scheme as the Client code to route Statements to the target LRS.  An LRS MAY choose to provide both HTTP and HTTPS endpoints to support this use case. HTTP is inherently less secure than HTTPS, and both LRS and Client should consider the security risks before making the decision to use this scheme. 
</s>

クライアントアクティビティプロバイダにとって、クライアントコードが LRS とは異なるスキーム（HTTP or HTTPS）上でホストされている IE8 と IE9 をサポートすることが要求されるケースがある。これらのケースにおいて、プロキシは LRS と通信するために必要とされる。
二つの簡単な解決策として:

1）   クライアントコードから LRS へ同じスキームのプロキシパススルーを構成する。あるいは、
2）   ターゲット LRS へのステートメント経路をクライアントコードと同じスキームとした、仲介サーバーサイド LRS をホストする

このユースケースをサポートするために、 LRS は HTTP と HTTPS エンドポイント両方の提供を選んでもよい。 HTTP は HTTPS よりも本質的に安全性が低くなるため、 LRS とクライアントの両方がこのスキームを利用する決定を下す前にセキュリティリスクを考慮すべきである。

<a name="validation"/> 

### <s>7.9 Validation</s> バリデーション

<s>
The function of the LRS within the xAPI is to store and retrieve Statements. As long as it has sufficient information to perform these tasks, it is expected that it does them. Validation of Statements in the Experience API is focused solely on syntax, not semantics. It SHOULD enforce rules regarding structure, but SHOULD NOT enforce rules regarding meaning. Enforcing the rules that ensure valid meaning among Verb definitions, Activity types, and extensions is the 
responsibility of the Activity Provider sending the Statement.  
</s>

xAPI 内での LRS の機能はステートメントを記録することや読み出すことである。これらのタスクを実行するための十分な情報がある限り、ステートメントの記録や読み出しが期待される。 Experience API でのステートメントのバリデーションは、もっぱら構文に集中され、意味には及ばない。構造に関するルールを施行すべきであり、意味に関するルールを施行すべきではない。
動詞の定義、アクティビティタイプ、そして拡張機能の中で有効な意味を保証するようなルールを施行することは、ステートメントを送信するアクティビティプロバイダの責任である。

<a name="httphead"/>

### <s>7.10. HTTP HEAD</s>HTTP HEAD

###### <s>Description</s>説明

<s>
The LRS will respond to HEAD requests by returning the meta information only, using the HTTP headers, and not the actual document.  
</s>

LRS は、実際のドキュメントを使用せず、 HTTP ヘッダーを使用してメタ情報を返却することだけで HEAD リクエストに応答する。

###### <s>Rationale</s>背景

<s>
Clients accessing the LRS may need to check if a particular Statement exists, or determine the modification date of documents such as state or Activity or Agent profile. Particularly for large documents it's more efficient not to get the entire document just to check its modification date.
</s>

LRS にアクセスするクライアントは、特定のステートメントが存在する場合にチェックを必要とし、ステート、アクティビティ、エージェントプロファイルのドキュメント修正日を決定することができる。特に大規模なドキュメントでは、ドキュメント修正日を確認する際、全体ドキュメントを取得しないため、より効率的である。

###### <s>LRS Requirements</s>LRS 必要条件


<s>
* The LRS MUST respond to any HTTP HEAD request as it would have responded to an otherwise
identical HTTP GET request except:
    * The message-body MUST be omitted.
    * The Content-Length header MAY be omitted, in order to avoid wasting LRS resources.
</s>

* LRS は（下記を）除外して、他の同一の HTTP GET リクエストに対する応答と同じように、どの HTTP HEAD リクエストにも応答しなければならない。<br>
	*メッセージボディは、省略しなければならない。<br>
	*LRS リソースの浪費を避けるために、 Content-Length ヘッダーは省略される。

<a name="AppendixA"/></a>
<div style="page-break-after: always;"></div>
## Appendix A: <s>Bookmarklet</s>ブックマークレット

An xAPI Bookmarklet enables individual user tracking with base authentication. Examples could be an "I think this," "I learned this," "I like this," or "I don't like this" Statement that allows self-reporting. The following is an example of such a bookmarklet, and the Statement that this bookmarklet would send if used on the page: http://adlnet.gov/xapi.

xAPI ブックマークレットは、基本認証によって個々のユーザをトラッキングすることを可能にする。例をあげると、自己申告を許す「私はこれを考える」、「私はこれを学ぶ」、「私はこれが好き」、もしくは「私はこれが嫌い」というステートメントである。以下は、ブックマークレットの一例であり、ページ（ http://adlnet.gov/xapi ）上で利用した場合、このブックマークレットが送るであろうステートメントである。


The bookmarklet MAY be provided by the LRS to track a specific user for behavior analytics.

ブックマークレットは、特定のユーザの行動分析のために追跡をするような LRS で提供されてもよい。

Therefore the LRS IRL, authentication, and Actor information is hard coded into the bookmarklet. Note that since the authorization token must be included in the bookmarklet, the LRS should provide a token with limited privileges, Ideally the token should enable the storage of self-reported learning Statements only. 

したがって、 LRS の IRL 、認証、およびアクタの情報は、ブックマークレット内にハードコードされる。認証トークンがブックマークレットに含まれるため、 LRS はトークンに対して限定された権限、理想的には、自己申告の学習に関するステートメントの記録のみの権限、を提供すべきことに注意が必要である。

The UUID SHOULD be included as part of the bookmarklet PUT Statement. If a Statement is POSTed without a UUID, the LRS MUST generate one.

UUID は、ブックマークレットの PUT ステートメントの一部として含まれるべきである。もしステートメントが UUID のないステートメントが POST された場合、 LRS が生成しなければならない。

In order to allow cross-domain reporting of Statements, a browser that supports the "Access-Control-Allow-Origin" and "Access-Control-Allow-Methods" headers must be used, such as IE 8+, FF 3.5+, Safari 4+, Safari iOS Chrome, or Android browser. Additionally the server must set the required headers.

ステートメントのクロスドメイン報告を可能にするためには、「 Access-Control-Allow-Origin 」と「 Access-Control-Allow-Methods 」のヘッダーをサポートするブラウザを使う必要がある（ IE8 以上、 Firefox3.5 以上、 Safari4 以上、 iOS 上の Chrome 、もしくは Android ブラウザ）。さらに、サーバは必要とされるヘッダーを付けなければならない。


In the example below, the following values in the first few lines should be replaced with your own values. All other values should be left as they are. 

以下の例について、先頭から数行の値は実際の値に置き換えて利用すること。それ以外の値は変更しないこと。

<table>
	<tr>
		<th>Value in example例文中に用いる値

</th>
		<th>Explanation説明</th>
	</tr>
	<tr>
		<td>http://localhost:8080/xAPI/</td>
		<td>Endpoint of the LRS to send the Statements to.ステートメントを送信する LRS のエンドポイント

</td>
	</tr>
	<tr>
		<td>dGVzdDpwYXNzd29yZA==</td>
		<td>Base 64 encoded username and password, usually in the form "username : password".通常 "username : password" の形式で Base 64 エンコードされるユーザ名とパスワード。

</td>
	</tr>
	<tr>
		<td>learner@example.adlnet.gov</td>
		<td>Email address of the learner using the bookmarklet.ブックマークレットを使用する学習者のメールアドレス</td>
	</tr>
</table>


<pre>
var url = "http://localhost:8080/xAPI/statements?statementId="+_ruuid();
var auth = "Basic dGVzdDpwYXNzd29yZA==";
var statement = {
	"actor" : { 
		"objectType" : "Agent", 
		"mbox" : "mailto:learner@example.adlnet.gov"
	},
	"verb" : {
		"id" : "",
		"display" : {}
	},
	"object" : {
		"id" : "",
		"definition" : {}
	}
};
var definition = statement.object.definition;

statement.verb.id = 'http://adlnet.gov/expapi/verbs/experienced';
statement.verb.display = { "en-US" : "experienced" };
statement.object.id = window.location.toString();
definition.type = "http://adlnet.gov/expapi/activities/link";

var xhr = new XMLHttpRequest();
xhr.open("PUT", url, true);
xhr.setRequestHeader("X-Experience-API-Version", "1.0");
xhr.setRequestHeader("Content-Type", "application/json");
xhr.setRequestHeader("Authorization", auth);
xhr.onreadystatechange = function() {
	if(xhr.readyState == 4) {
		alert(xhr.status + " : " + xhr.responseText);
	}
};
xhr.send(JSON.stringify(statement));

/*!
Modified from: Math.uuid.js (v1.4)
http://www.broofa.com
mailto:robert@broofa.com

Copyright (c) 2010 Robert Kieffer
Dual licensed under the MIT and GPL licenses.
*/
function _ruuid() {
	return 'xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx'.replace(/[xy]/g, function(c) {
		var r = Math.random()*16|0, v = c == 'x' ? r : (r&0x3|0x8);
		return v.toString(16);
	});
}

</pre>


###### Example Statement Using Bookmarklet ブックマークレットを使用したステートメント例

###### Headers ヘッダ

<pre>
<code>{
    "X-Experience-API-Version": "1.0.0",
    "Content-Type": "application/json; charset=UTF-8",
    "Authorization": "d515309a-044d-4af3-9559-c041e78eb446",
    "Referer": "http://adlnet.gov/xapi/",
    "Content-Length": "###",
    "Origin": "http://adlnet.gov"
}
</code></pre>


###### Method Pathメソッドパス  

<pre><code>PUT : /xAPI/Statements/?statementId=ed1d064a-eba6-45ea-a3f6-34cdf6e1dfd9

Body:
{
    "actor": {
        "objectType": "Agent",
        "mbox": "mailto:learner@example.adlnet.gov"
    },
    "verb" : {
        "id": "http://adlnet.gov/expapi/verbs/experienced",
        "display": {
            "en-US": "experienced"
        }
    },
    "object": {
        "id": "http://adlnet.gov/xapi/",
        "definition": {
            "type": "http://adlnet.gov/expapi/activities/link"
        }
    }
}
</code></pre>


<a name="AppendixB"/></a>

## Appendix B: <s>Creating an "IE Mode" Request</s>IE用リクエスト作成

<pre>

function getIEModeRequest(method, url, headers, data){

	var newUrl = url;

	// Everything that was on query string goes into form varsクエリストリングにある情報は全てフォーム変数に

	var formData = new Array();
	var qsIndex = newUrl.indexOf('?');
	if(qsIndex > 0){
		formData.push(newUrl.substr(qsIndex+1));
		newUrl = newUrl.substr(0, qsIndex);
	}

	// Method has to go on querystring, and nothing elseメソッドはクエリ―ストリングに入れる。それ以外は入れない
	newUrl = newUrl + '?method=' + method;

	// Headersヘッダ

	if(headers !== null){
		for(var headerName in headers){
			formData.push(
				headerName + "=" +
					encodeURIComponent(
						headers[headerName]));
		}
	}

	// The original data is repackaged as "content" form varオリジナルデータは "content" フォーム変数に再パックされる

	if(data !== null){
		formData.push('content=' + encodeURIComponent(data));
	}

	return {
		"method":"POST",
		"url":newUrl,
		"headers":{},
		"data":formData.join("&")
	};
}
</pre>


<a name="AppendixC"/></a>

## Appendix C: <s>Example definitions for Activities of type "cmi.interaction"</s>アクティビティタイプ「 cmi.interaction 」のための定義例

###### true-falsetrue/false


<pre>
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
</pre>

###### choice

<pre>

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
</pre>

###### fill-in

<pre>


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

</pre>


###### likert

<pre>

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

</pre>

###### matching

<pre>


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

</pre>


###### performance

<pre>


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

</pre>


###### sequencing

<pre>


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

</pre>


###### numeric

<pre>


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

</pre>


###### other

<pre>


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

</pre>


<a name="AppendixD"/></a>
 
## Appendix D: <s>Example statements</s>ステートメント例

Example of a simple statement (line breaks are for display purposes only):  簡単なステートメント例（改行は表示目的）

<pre>


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

</pre>

Typical simple completion with verb "attempted":  Verbの「 attempted 」を用いた一般的で簡単な完了

<pre>


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

</pre>


<a name="AppendixE"/></a>

## Appendix E: <s>Converting Statements to 1.0.0</s>1.0.0へステートメントを変換

######Rationale 背景
This is a 1.0.0 specification, and as such implementers should not have to consider prior versions of the specification. However, prior versions did see notable adoption. This data conversion is specified in order
to preserve the data tracked using earlier versions, and make it available to new implementers in a consistant manner.

これは、1.0.0の仕様であり、実装者が、従来のバージョンの仕様を考慮する必要がないように努めた。しかしながら、従来のバージョンは、注目に値する普及を示した。このデータコンバージョンは、旧バージョンを用いて記録されたデータを継続して活用でき、新しい実装者も同様の方式で利用できることを目指して作成した。


######Details 詳細

######Conversion of Statements created based on version 0.9 バージョン0.9を元に作られたステートメントのコンバージョン

A 1.0.0 system converting a Statement created in 0.9 MUST follow the steps below:

0.9から作成されたステートメントを変換する1.0.0システムは以下のステップに沿っていなければならない。

* If the Statement has been voided or uses Verbs, Activity types, or properties not included in the 0.9 specification, do not convert it. ステートメントが無効化された、または 0.9 版の仕様に含まれない動詞、アクティビティタイプまたはプロパティである場合は、変換をしない。

* Prefix "verb" with "http://adlnet.gov/expapi/verbs/". Verb に http://adlnet.gov/expapi/verbs/ の prefix をつける。

* Prefix any Activity ids which are not full absolute IRIs with "tag:adlnet.gov,2013:expapi:0.9:activities:" 絶対表記の IRI でないアクティビティ ID には、"tag:adlnet.gov,2013:expapi:0.9:activities:" の prefix をつける。

* Prefix any extension keys which are not full absolute IRIs with "tag:adlnet.gov,2013:expapi:0.9:extensions:" 完全な絶対 IRI でない拡張キーには、"tag:adlnet.gov,2013:expapi:0.9:activities:" の prefix をつける。

* Prefix Activity types with "http://adlnet.gov/expapi/activities/" アクティビティタイプに "http://adlnet.gov/expapi/activities/" の prefix を付ける。

* for each Agent (Actor): すべてのエージェント（アクタ）について：

    * Search for Inverse Functional Identifiers in this order: "mbox, mbox_sha1sum, openId, account". Keep the first populated Inverse Functional Identifier found and discard the rest. 「"mbox, mbox_sha1sum, openId, account"」、この順序で逆関数識別子を検索する。最初に見つけられた逆関数識別子を保持し、残りは破棄する。

    * For the above Inverse Functional Identifier, take the first element in the array and use that as the value of that Inverse Functional Identifier property, discarding any remaining elements. 上記の逆関数識別子については、配列で最初の要素を得る。そしてその逆関数識別子プロパティの値としてそれを利用し、残りの要素は破棄する。

    * If the "name" property is present, set it equal to the first element in the "name" array, discard the remaining elements. もしnameプロパティが存在する場合には、name配列の最初の要素にそれが等しくなるよう設定をし、残りの要素を破棄する。
    * Remove all remaining properties. 残りすべてのプロパティを削除する。

* Remove the "voided" property from the Statement, if present. Remember, if the value of the voided property is true, then the Statement MUST NOT be converted. もし存在するなら、ステートメントから " voided " プロパティを削除する。もし、" voided " プロパティの値が true なら、ステートメントは変換してはならない。

* Add "version": "1.0.0" 「version": "1.0.0"」を追加する。
* If an authority was not previously set, set the authority to an Agent identified by an account with a homePage set to the home page corresponding to the system performing the conversion and an accountName of "unknown". 権限が前もって設定されていない場合は、homePage に変換を実行したシステムに対応するホームページ、accountName に "unknown" を設定したアカウントによって定義されるエージェントを権限として設定する。

* if the Statement field in context was set, remove it from the Statement. コンテキストにおけるステートメントフィールドがセットされていた場合、ステートメントから削除すること。

* Preserve all other fields without modification, including "stored". Stored should still be updated if the Statement is passed to another system. 他すべてのフィールドは stored を含め、変更せずに保持すること。 stored はステートメントが他システムへ渡った場合についても最新化されるべきである。

######Conversion of Statements created based on version 0.95 バージョン0.95を元に作られたステートメントのコンバージョン

A 1.0.0 system converting a Statement created in 0.95 MUST follow the steps below: 0.95で作成されたステートメントを変換する1.0.0のシステムは、以下のステップに従わなければならない。

* If the Statement is voided, do not convert it. 無効となったステートメントは変換しないこと。

* Remove the "voided" property from the Statement, if present. Remember, if the value of the voided property is true, then the Statement MUST NOT be converted. 存在する場合、ステートメントから voided プロパティを削除すること。 voided プロパティの値が true である場合、ステートメントを変換してはならない。

* Add "version": "1.0.0" 「 version ": "1.0.0"」を追加する。
* If an authority was not previously set, set the authority to an Agent identified by an account with a homePage set to the home page corresponding to the system performing the conversion and an accountName of "unknown". もし権限が前もって与えられてないなら、コンバージョンと" unknown "というアカウント名を実行するシステムと対応するホームページに、ホームページ設定と一緒にアカウントによって識別されたエージェントに権限を与える。
* if the Statement field in context was set to anything other than a StatementRef, remove it from the Statement. もしコンテキストのステートメントフィールドが StatementRef 以外に設定されたら、ステートメントからフィールドを削除する。
* Preserve all other fields without modification, including "stored". Stored should still be updated if the Statement is passed to another system.  stored を含めたその他すべてのフィールドを変更なしで保存する。ステートメントが他のシステムに送られた場合は、 stored は更新される。



######Example 例


A 0.9 Statement: 0.9ステートメント

<pre>


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

</pre>


Converted to 1.0.0: 1.0.0に変換

<pre>


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

</pre>


<a name="AppendixF"/></a>
## Appendix F: <s>Example Signed Statement</s>署名ステートメント例
An example signed Statement, as described in: <a href="#signature">4.4 Signed Statements</a>.

4.4 署名ステートメントに記載された証明ステートメント例

The original Statement serialization to be signed. New lines in this example are included via CR+LF (0x0D + 0x0A).

署名されるべきオリジナルステートメントのリスト。この例では新しい行が「CR+LF (0x0D + 0x0A)」を含められる。

<pre>


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

</pre>


Example private key for X.509 certificate that will be used for signing:

署名に使用されるX.509証明書の秘密鍵例

<pre>


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

</pre>


Example public X.509 certificate 公開X.509証明書例

<pre>


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

</pre>


Example certificate authority certificate ＣＡ証明書例

<pre>

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

</pre>

JWS Header. Note that along with specifying the algorithm, the certificate chain for the signing certificate has been included.

ＪＷＳヘッダー。アルゴリズムを記すの一緒に、署名証明書のために証明書チェーンが含まれることに注意しなさい。

<pre>

```
{
    "alg": "RS256",
    "x5c": [
"MIIDATCCAmqgAwIBAgIJAMB1csNuA6
+kMA0GCSqGSIb3DQEBBQUAMHExCzAJBgNVBAYTAlVTMRIwEAYDVQQIEwlUZW5uZXNzZWUxGDAWBgNVBAoTD0V4YW1wbGUgQ29tcGFueTEQMA4GA1UEAxMHRXhhbXBsZTEiMCAGCSqGSIb3DQEJARYTZXhhbXBsZUBleGFtcGxlLmNvbTAeFw0xMzA0MDQxNTI4MzBaFw0xNDA0MDQxNTI4MzBaMIGWMQswCQYDVQQGEwJVUzESMBAGA1UECBMJVGVubmVzc2VlMREwDwYDVQQHEwhGcmFua2xpbjEYMBYGA1UEChMPRXhhbXBsZSBDb21wYW55MRAwDgYDVQQLEwdFeGFtcGxlMRAwDgYDVQQDEwdFeGFtcGxlMSIwIAYJKoZIhvcNAQkBFhNleGFtcGxlQGV4YW1wbGUuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDjxvZXF30WL4oKjZYXgR0ZyaX+u3y6+JqTqiNkFa/VTnet6Ly2OT6ZmmcJEPnq3UnewpHoOQ+GfhhTkW13j06j5iNn4obcCVWTL9yXNvJH+Ko+xu4Yl/ySPRrIPyTjtHdG0M2XzIlmmLqm+CAS+KCbJeH4tf543kIWC5pC5p3cVQIDAQABo3sweTAJBgNVHRMEAjAAMCwGCWCGSAGG+EIBDQQfFh1PcGVuU1NMIEdlbmVyYXRlZCBDZXJ0aWZpY2F0ZTAdBgNVHQ4EFgQUVs3v5afEdOeoYeVajAQE4v0WS1QwHwYDVR0jBBgwFoAUyVIc3yvra4EBz20I4BF39IAixBkwDQYJKoZIhvcNAQEFBQADgYEAgS/FF5D0Hnj44rvT6kgn3kJAvv2lj/fyjztKIrYS33ljXGn6gGyA4qtbXA23PrO4uc/wYCSDICDpPobh62xTCd9qObKhgwWOi05PSBLqUu3mwfAe15LJBJBqPVZ4K0kppePBU8m6aIZoH57L/9t4OoaL8yKs/qjKFeI1OFWZxvA=",
"MIIDNzCCAqCgAwIBAgIJAMB1csNuA6
+jMA0GCSqGSIb3DQEBBQUAMHExCzAJBgNVBAYTAlVTMRIwEAYDVQQIEwlUZW5uZXNzZWUxGDAWBgNVBAoTD0V4YW1wbGUgQ29tcGFueTEQMA4GA1UEAxMHRXhhbXBsZTEiMCAGCSqGSIb3DQEJARYTZXhhbXBsZUBleGFtcGxlLmNvbTAeFw0xMzA0MDQxNTI1NTNaFw0yMzA0MDIxNTI1NTNaMHExCzAJBgNVBAYTAlVTMRIwEAYDVQQIEwlUZW5uZXNzZWUxGDAWBgNVBAoTD0V4YW1wbGUgQ29tcGFueTEQMA4GA1UEAxMHRXhhbXBsZTEiMCAGCSqGSIb3DQEJARYTZXhhbXBsZUBleGFtcGxlLmNvbTCBnzANBgkqhkiG9w0BAQEFAAOBjQAwgYkCgYEA1sBnBWPZ0f7WJUFTJy5+01SlS5Z6DDD6Uye9vK9AycgV5B3+WC8HC5u5h91MujAC1ARPVUOtsvPRs45qKNFIgIGRXKPAwZjawEI2sCJRSKV47i6B8bDv4WkuGvQaveZGI0qlmN5R1Eim2gUItRj1hgcC9rQavjlnFKDY2rlXGukCAwEAAaOB1jCB0zAdBgNVHQ4EFgQUyVIc3yvra4EBz20I4BF39IAixBkwgaMGA1UdIwSBmzCBmIAUyVIc3yvra4EBz20I4BF39IAixBmhdaRzMHExCzAJBgNVBAYTAlVTMRIwEAYDVQQIEwlUZW5uZXNzZWUxGDAWBgNVBAoTD0V4YW1wbGUgQ29tcGFueTEQMA4GA1UEAxMHRXhhbXBsZTEiMCAGCSqGSIb3DQEJARYTZXhhbXBsZUBleGFtcGxlLmNvbYIJAMB1csNuA6+jMAwGA1UdEwQFMAMBAf8wDQYJKoZIhvcNAQEFBQADgYEADhwTebGk735yKhm8DqCxvNnEZ0NxsYEYOjgRG1yXTlW5pE691fSH5AZ+T6fpwpZcWY5QYkoN6DnwjOxGkSfQC3/
yGmcUDKBPwiZ5O2s9C+fE1kUEnrX2Xea4agVngMzR8DQ6oOauLWqehDB
+g2ENWRLoVgS+ma5/Ycs0GTyrECY="
    ]
}

</pre>

JWS signature JWS 署名

<pre>

ew0KICAgICJhbGciOiAiUlMyNTYiLA0KICAgICJ4NWMiOiBbDQogICAgICAgICJNSUlEQVRDQ0FtcWdBd0lCQWdJSkFNQjFjc051QTYra01BMEdDU3FHU0liM0RRRUJCUVVBTUhFeEN6QUpCZ05WQkFZVEFsVlRNUkl3RUFZRFZRUUlFd2xVWlc1dVpYTnpaV1V4R0RBV0JnTlZCQW9URDBWNFlXMXdiR1VnUTI5dGNHRnVlVEVRTUE0R0ExVUVBeE1IUlhoaGJYQnNaVEVpTUNBR0NTcUdTSWIzRFFFSkFSWVRaWGhoYlhCc1pVQmxlR0Z0Y0d4bExtTnZiVEFlRncweE16QTBNRFF4TlRJNE16QmFGdzB4TkRBME1EUXhOVEk0TXpCYU1JR1dNUXN3Q1FZRFZRUUdFd0pWVXpFU01CQUdBMVVFQ0JNSlZHVnVibVZ6YzJWbE1SRXdEd1lEVlFRSEV3aEdjbUZ1YTJ4cGJqRVlNQllHQTFVRUNoTVBSWGhoYlhCc1pTQkRiMjF3WVc1NU1SQXdEZ1lEVlFRTEV3ZEZlR0Z0Y0d4bE1SQXdEZ1lEVlFRREV3ZEZlR0Z0Y0d4bE1TSXdJQVlKS29aSWh2Y05BUWtCRmhObGVHRnRjR3hsUUdWNFlXMXdiR1V1WTI5dE1JR2ZNQTBHQ1NxR1NJYjNEUUVCQVFVQUE0R05BRENCaVFLQmdRRGp4dlpYRjMwV0w0b0tqWllYZ1IwWnlhWCt1M3k2K0pxVHFpTmtGYS9WVG5ldDZMeTJPVDZabW1jSkVQbnEzVW5ld3BIb09RK0dmaGhUa1cxM2owNmo1aU5uNG9iY0NWV1RMOXlYTnZKSCtLbyt4dTRZbC95U1BScklQeVRqdEhkRzBNMlh6SWxtbUxxbStDQVMrS0NiSmVINHRmNTQza0lXQzVwQzVwM2NWUUlEQVFBQm8zc3dlVEFKQmdOVkhSTUVBakFBTUN3R0NXQ0dTQUdHK0VJQkRRUWZGaDFQY0dWdVUxTk1JRWRsYm1WeVlYUmxaQ0JEWlhKMGFXWnBZMkYwWlRBZEJnTlZIUTRFRmdRVVZzM3Y1YWZFZE9lb1llVmFqQVFFNHYwV1MxUXdId1lEVlIwakJCZ3dGb0FVeVZJYzN5dnJhNEVCejIwSTRCRjM5SUFpeEJrd0RRWUpLb1pJaHZjTkFRRUZCUUFEZ1lFQWdTL0ZGNUQwSG5qNDRydlQ2a2duM2tKQXZ2MmxqL2Z5anp0S0lyWVMzM2xqWEduNmdHeUE0cXRiWEEyM1ByTzR1Yy93WUNTRElDRHBQb2JoNjJ4VENkOXFPYktoZ3dXT2kwNVBTQkxxVXUzbXdmQWUxNUxKQkpCcVBWWjRLMGtwcGVQQlU4bTZhSVpvSDU3TC85dDRPb2FMOHlLcy9xaktGZUkxT0ZXWnh2QT0iLA0KICAgICAgICAiTUlJRE56Q0NBcUNnQXdJQkFnSUpBTUIxY3NOdUE2K2pNQTBHQ1NxR1NJYjNEUUVCQlFVQU1IRXhDekFKQmdOVkJBWVRBbFZUTVJJd0VBWURWUVFJRXdsVVpXNXVaWE56WldVeEdEQVdCZ05WQkFvVEQwVjRZVzF3YkdVZ1EyOXRjR0Z1ZVRFUU1BNEdBMVVFQXhNSFJYaGhiWEJzWlRFaU1DQUdDU3FHU0liM0RRRUpBUllUWlhoaGJYQnNaVUJsZUdGdGNHeGxMbU52YlRBZUZ3MHhNekEwTURReE5USTFOVE5hRncweU16QTBNREl4TlRJMU5UTmFNSEV4Q3pBSkJnTlZCQVlUQWxWVE1SSXdFQVlEVlFRSUV3bFVaVzV1WlhOelpXVXhHREFXQmdOVkJBb1REMFY0WVcxd2JHVWdRMjl0Y0dGdWVURVFNQTRHQTFVRUF4TUhSWGhoYlhCc1pURWlNQ0FHQ1NxR1NJYjNEUUVKQVJZVFpYaGhiWEJzWlVCbGVHRnRjR3hsTG1OdmJUQ0JuekFOQmdrcWhraUc5dzBCQVFFRkFBT0JqUUF3Z1lrQ2dZRUExc0JuQldQWjBmN1dKVUZUSnk1KzAxU2xTNVo2RERENlV5ZTl2SzlBeWNnVjVCMytXQzhIQzV1NWg5MU11akFDMUFSUFZVT3RzdlBSczQ1cUtORklnSUdSWEtQQXdaamF3RUkyc0NKUlNLVjQ3aTZCOGJEdjRXa3VHdlFhdmVaR0kwcWxtTjVSMUVpbTJnVUl0UmoxaGdjQzlyUWF2amxuRktEWTJybFhHdWtDQXdFQUFhT0IxakNCMHpBZEJnTlZIUTRFRmdRVXlWSWMzeXZyYTRFQnoyMEk0QkYzOUlBaXhCa3dnYU1HQTFVZEl3U0JtekNCbUlBVXlWSWMzeXZyYTRFQnoyMEk0QkYzOUlBaXhCbWhkYVJ6TUhFeEN6QUpCZ05WQkFZVEFsVlRNUkl3RUFZRFZRUUlFd2xVWlc1dVpYTnpaV1V4R0RBV0JnTlZCQW9URDBWNFlXMXdiR1VnUTI5dGNHRnVlVEVRTUE0R0ExVUVBeE1IUlhoaGJYQnNaVEVpTUNBR0NTcUdTSWIzRFFFSkFSWVRaWGhoYlhCc1pVQmxlR0Z0Y0d4bExtTnZiWUlKQU1CMWNzTnVBNitqTUF3R0ExVWRFd1FGTUFNQkFmOHdEUVlKS29aSWh2Y05BUUVGQlFBRGdZRUFEaHdUZWJHazczNXlLaG04RHFDeHZObkVaME54c1lFWU9qZ1JHMXlYVGxXNXBFNjkxZlNINUFaK1Q2ZnB3cFpjV1k1UVlrb042RG53ak94R2tTZlFDMy95R21jVURLQlB3aVo1TzJzOUMrZkUxa1VFbnJYMlhlYTRhZ1ZuZ016UjhEUTZvT2F1TFdxZWhEQitnMkVOV1JMb1ZnUyttYTUvWWNzMEdUeXJFQ1k9Ig0KICAgIF0NCn0.ew0KICAgICJ2ZXJzaW9uIjogIjEuMC4wIiwNCiAgICAiaWQiOiAiMzNjZmY0MTYtZTMzMS00YzlkLTk2OWUtNTM3M2ExNzU2MTIwIiwNCiAgICAiYWN0b3IiOiB7DQogICAgICAgICJtYm94IjogIm1haWx0bzpleGFtcGxlQGV4YW1wbGUuY29tIiwNCiAgICAgICAgIm5hbWUiOiAiRXhhbXBsZSBMZWFybmVyIiwNCiAgICAgICAgIm9iamVjdFR5cGUiOiAiQWdlbnQiDQogICAgfSwNCiAgICAidmVyYiI6IHsNCiAgICAgICAgImlkIjogImh0dHA6Ly9hZGxuZXQuZ292L2V4cGFwaS92ZXJicy9leHBlcmllbmNlZCIsDQogICAgICAgICJkaXNwbGF5Ijogew0KICAgICAgICAgICAgImVuLVVTIjogImV4cGVyaWVuY2VkIg0KICAgICAgICB9DQogICAgfSwNCiAgICAib2JqZWN0Ijogew0KICAgICAgICAiaWQiOiAiaHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g_dj14aDRrSWlIM1NtOCIsDQogICAgICAgICJvYmplY3RUeXBlIjogIkFjdGl2aXR5IiwNCiAgICAgICAgImRlZmluaXRpb24iOiB7DQogICAgICAgICAgICAibmFtZSI6IHsNCiAgICAgICAgICAgICAgICAiZW4tVVMiOiAiVGF4IFRpcHMgJiBJbmZvcm1hdGlvbiA6IEhvdyB0byBGaWxlIGEgVGF4IFJldHVybiAiDQogICAgICAgICAgICB9LA0KICAgICAgICAgICAgImRlc2NyaXB0aW9uIjogew0KICAgICAgICAgICAgICAgICJlbi1VUyI6ICJGaWxpbmcgYSB0YXggcmV0dXJuIHdpbGwgcmVxdWlyZSBmaWxsaW5nIG91dCBlaXRoZXIgYSAxMDQwLCAxMDQwQSBvciAxMDQwRVogZm9ybSINCiAgICAgICAgICAgIH0NCiAgICAgICAgfQ0KICAgIH0sDQogICAgInRpbWVzdGFtcCI6ICIyMDEzLTA0LTAxVDEyOjAwOjAwWiINCn0.FWuwaPhwUbkk7h9sKW5zSvjsYNugvxJ-TrVaEgt_DCUT0bmKhQScRrjMB6P9O50uznPwT66oF1NnU_G0HVhRzS5voiXE-y7tT3z0M3-8A6YK009Bk_digVUul-HA4Fpd5IjoBBGe3yzaQ2ZvzarvRuipvNEQCI0onpfuZZJQ0d8
```

</pre>

Signed Statement 署名されたステートメント

<pre>


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
            "sha2": "dc9589e454ff375dd5dfd6f556d2583e231e8cafe55ef40102ddd988b79f86f0"
        }
    ]
}
```

</pre>

__Note:注記__ Attached signature not shown, see <a href="#attachments"> attachments</a> for attachment message format.

添付した署名が表示されない場合、<a href="#attachments"> で添付型メッセージのフォーマットを確認すること。
