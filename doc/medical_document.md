# 医師記録等
更新日:2017/08/25
## 趣旨
本事業では、各社のSS-MIX2モジュールの拡張ストレージへの出力機能を利用し、以下の情報を出力することを求めている。その際、SS-MIX2 拡張ストレージ構成の説明と構築ガイドライン Ver.1.2d（以下、ガイドライン）に記載している仕様に対応していること。また、トランザクションストレージ、インデックスデータベースも同時に生成すること。

* 経過記録
* 退院時サマリー
* 診療情報提供書
* 災害時Jspeed+データ

以下に仕様を示す。

## ドキュメントデータ 物理構造
    |-- 拡張ストレージ ルートフォルダ
        |-- 患者ID 先頭3文字
            |-- 患者ID 4～6文字
                |-- 患者ID
                    |-- 診療日
                        |-- データ種別
                            |-- コンテンツフォルダ
                                |--主文書ファイル


## 診療日
特に指定しない。

## データ種別
ガイドライン P4 (4)「データ種別フォルダ」について に則ること。
```
[ローカル文書コード]^ローカル文書名称^[ローカルコード体系コード]^標準文書コード^標準文書名称^標準コード体系コード
```
以下のように標準コードに対しローカルコードが複数あることは許容される。
```
L12345^入院診療録^99ZZZ^11506-3^経過記録^LN
L12346^外来診療録^99ZZZ^11506-3^経過記録^LN
```

No|データ種別|種別名称|HL7メッセージ型|
|---|---|---|---|
|2|^（ローカル名称）^^11506-3^経過記録^LN|診療録（外来/入院含む）|HL7 CDA R2|
|2.1|^（ローカル名称）^^34108-1^外来診療録^LN|診療録（外来）（入院・外来が別の場合）|HL7 CDA R2|
|2.2|^（ローカル名称）^^34112-3^入院診療録^LN|診療録（入院）（入院・外来が別の場合）|HL7 CDA R2|
|3|^（ローカル名称）^^18842-5^退院時サマリー^LN|退院時サマリー|HL7 CDA R2|
|4|^（ローカル名称）^^57133-1^紹介状^LN|診療情報提供書|HL7 CDA R2|
|5|L-JSPEED^災害時JSPEED記録^99ZL01^74465-6^災害時JSPEED記録^LN|災害時ＪＳＰＥＥＤ記録|HL7 CDA R2|




## コンテンツフォルダ
ガイドライン Ver.1.2d P5 (5)「コンテンツフォルダ」について に則ること。
```
患者ID_診療日_データ種別コード_特定キー_発生日時_診療科コード_コンディションフラグ
```
いずれの文書も削除は想定していないが、電子カルテシステムによっては修正はあり得ると考える。その場合、ガイドライン P6 ④修正が発生する場合 に則り改版すること。


## 主文書ファイル
XML CDA R2で出力すること。XMLファイル以外に画像ファイルやCSSファイル等を出力してもかまわない。

### HEADER部
いずれの文書もJAHIS　診療文書構造化記述規約 共通編 Ver.1.0に則ること。  
P27 6.3.11.検査・診療等行為 "documentationOf/ServiceEvent" によると、documentationOfの制約・多重度は0..1となっているが、
経過記録、退院時サマリ、災害時JSPEED記録についてはこれを1..1と読み替えること。  
経過記録、災害時JSPEED記録はserviceEvent classCode(サービスイベントクラスコード)をENC(診察)とし、effectiveTime(実施日)はlow value、high valueともに記録タイミングを出力すること。  
退院時サマリはserviceEvent classCode(サービスイベントクラスコード)をACCM(入院、滞在)とし、effectiveTime(実施日)はlow valueに入院タイミング、high valueに退院タイミングを出力すること。  
タイミングの粒度は日以上であれば良い。

### BODY部
#### 診療情報提供書
診療情報提供書は、日本HL7協会 診療情報提供書規格（医療機関への紹介状）Ver1.00に則ること。  
#### 災害時JSPEED記録

* 概要

Ｊｓｐｅｅｄ情報については、Additional Documentセクションに記載するものとする。また、textタグ内に情報を順に1行にカンマ区切りで書き出すものとする。

*  説明ブロック仕様

表 Additional Document 説明ブロックXML 仕様

|XPath| Card.| 値 |説明|
|---|---|---|---|
|section|||[/ClinicalDocument/component/structuredBody/component/section]|
|templateId |1..1|
| @root| R |2.16.840.1.113883.10.20.35.2.1|
|code |1..1|
| @code |R| 77599-9 |セクションコード|
| @displayName |R| ADDITIONAL DOCUMENTATION|セクションコードを示す文字列|
| @codeSystem |R| 2.16.840.1.113883.6.1| セクションコードのコード体系を示すOID|
| @codeSystemName |O| LOINC| セクションコードのコード体系を示す文字列|
|title|0..1|
| text() |M| Jspeed DOCUMENTATION|セクションのタイトル記載文字列固定値ではないが、記載している文字列「Jspeed DOCUMENTATION」を推奨する|
|text |1..1|
| text()| M| |セクションのテキスト記載文字列.以下の情報を順に1行にカンマ区切りで書き出すものとする。なお、最終フィールドのバージョン情報以外は非必須である。また数値以外のデータは””で囲むこと|

表 text内データ記述仕様

|Field No|Title|日本語名称|値||説明|
|---|---|---|---|---|---|
|1|ID||||Free text (A unique alphanumeric code recommended.)|
|2|MDSa||||1:<1 2:1=<, <5 3:5=<, <65  4:65=< 本プロジェクトにおいては下記のデータ入力時にチェックボックス等で選択させた場合にデータをセットする|
|3|Age||||年齢　本プロジェクトにおいては患者基本情報の情報から取得してデータをセットする|
|4|M/Y|Month or Year|||MM/YYYY (M:Month Y:Year)　本プロジェクトにおいては患者基本情報の情報から取得してデータをセットする|
|5|MDS1|Male|||1:Yes 0:No|
|6|MDS2|Female non-pregnant|||1:Yes 0:No|
|7|MDS3|Female pregnant|||1:Yes 0:No|
|8|MDS4|Major head / spine injury|||1:Applicable 0:Not Applicable|
|9|MDS5|Major torso injury|||1:Applicable 0:Not Applicable|
|10|MDS6|Major extremity injury|||1:Applicable 0:Not Applicable|
|11|MDS7|Moderate injury|||1:Applicable 0:Not Applicable|
|12|MDS8|Minor injury|||1:Applicable 0:Not Applicable|
|13|MDS9|Acute respiratory infection|||1:Applicable 0:Not Applicable|
|14|MDS10|Acute watery diarrhea|||1:Applicable 0:Not Applicable|
||MDS11|Acute bloody diarrhea|||1:Applicable 0:Not Applicable|
||MDS12|Acute jaundice syndrome|||1:Applicable 0:Not Applicable|
||MDS13|Measles suspected|||1:Applicable 0:Not Applicable|
||MDS14|Meningitis suspected|||1:Applicable 0:Not Applicable|
||MDS15|Tetanus suspected|||1:Applicable 0:Not Applicable|
||MDS16|Acute flaccid paralysis|||1:Applicable 0:Not Applicable|
||MDS17|Acute haemorrhagic fever|||1:Applicable 0:Not Applicable|
||MDS18|Fever of unknown origin|||1:Applicable 0:Not Applicable|
||MDS19|Surgical emergency (Non-trauma)|||1:Applicable 0:Not Applicable|
||MDS20|Medical emergency|||1:Applicable 0:Not Applicable|
||MDS21|Skin disease|||1:Applicable 0:Not Applicable|
||MDS22|Acute mental health and psychosocial problem|||1:Applicable 0:Not Applicable|
||MDS23|Obstetric complicated|||1:Applicable 0:Not Applicable|
||MDS24|Severe Acute Malnutrition (SAM) *|||1:Applicable 0:Not Applicable|
||MDS25|Other diagnosis, not specified above|||1:Applicable 0:Not Applicable|
||MDS26|Major procedure except limb amputation and obsteric|||1:Applicable 0:Not Applicable|
||MDS27|Minor procedure|||1:Applicable 0:Not Applicable|
||MDS28|Limb amputation excluding digits *|||1:Applicable 0:Not Applicable|
||MDS29|Normal Vaginal Delivery (NVD)|||1:Applicable 0:Not Applicable|
||MDS30|Caesarean section|||1:Applicable 0:Not Applicable|
||MDS31|Obstetrics others|||1:Applicable 0:Not Applicable|
||MDS32|Discharge without F/U|||1:Applicable 0:Not Applicable|
||MDS33|Discharge with F/U|||1:Applicable 0:Not Applicable|
||MDS34|Admission|||1:Applicable 0:Not Applicable|
||MDS35|Referral / Transfer *|||1:Applicable 0:Not Applicable|
||MDS36|Left against medical advice|||1:Applicable 0:Not Applicable|
||MDS37|Dead on arrival|||1:Applicable 0:Not Applicable|
||MDS38|Death within facility *|||1:Applicable 0:Not Applicable|
||MDS39|Requiring long term rehabilitation *|||1:Applicable 0:Not Applicable|
||MDS40|Directly related to disaster|||1:Applicable 0:Not Applicable|
||MDS41|Indirectly related to disaster|||1:Applicable 0:Not Applicable|
||MDS42|Not related to disaster|||1:Applicable 0:Not Applicable|
||MDS43|Vulnerable child|||1:Applicable 0:Not Applicable|
||MDS44|Vulnerable adult |||1:Applicable 0:Not Applicable|
||MDS45|Sexual Gender Based Violence (SGBV)|||1:Applicable 0:Not Applicable|
||MDS46|Violence (non-SGBV)|||1:Applicable 0:Not Applicable|
|60|MDS Version|J-Speed(MDS)バージョン番号|||"JPN1.00"とする|


*XMLサンプル
```
<section>
 <templateId root="2.16.840.1.113883.10.20.35.2.1" />
 <code code="77599-9" codeSystem="2.16.840.1.113883.6.1" codeSystemName="LOINC" displayName="ADDITIONAL
DOCUMENTATION" />
 <title>Jspeed DOCUMENT</title>
 <text>
 00001234,3,43,03/1974,1,0,0,0,0,1,0,....,"JPN1.00"
 </text>
</section>
```

#### その他の文書
その他の文書は、XMLの文法に則ること。
