#本リポジトリの目的

独立行政法人国立病院機構(以下、「機構」という。)は、電子カルテシステムから標準化された形式(SS-MIX2形式)の診療情報を収集し、一元的に集約するデータベース(以下、「診療情報データベース」という。) を構築し、またその実施方法を手順書としてまとめる事業 (以下、「本事業」という。) を実施している。本事業においては「SS-MIX2 Ver.1.2c」に準拠したSS-MIX2出力モジュールを本事業に参加する各病院に導入することとしており、本ドキュメント群は、そのモジュールに搭載すべき機能について記載した技術仕様及び、提供するマスター類である。

##docフォルダ内の構成
* ssmix_specification.md SS-MIX2を用いた診療情報データベース構築の為のSS-MIX2モジュール技術仕様書
* separated_strage.md ストレージを複数ボリュームに分割する場合の考慮
* index_db.md インデックスデータベース
* transaction_strage.md トランザクションストレージ
* vital_sign_def.md  バイタル検査結果通知に関する定義
* cp932_JIS_convart.md  環境依存文字　変換テーブル
* ascii_unit.md 単位のASCII文字変換
* jlac10_units.md JLAC10ごとの単位
* convert_unit.md 単位変換
* split_value.md 複合検査結果値の分離
* convert_to_sn.md 定性結果・不等号の表現
* late_order.md 過去日付のオーダー
* bacteria_test.md 細菌検査オーダー/結果
* dietary_order.md OMD(食事オーダー)
* doctor_info.md ADT-01(担当医の変更/担当医の取り消し)
* exponential_notation.md(指数表記)
* exception_case.md(例外事例)
* unspecified_icd10.md(ICD-10不明病名)

##masterフォルダ内の構成
* convert_to_sn.ptn 定性結果・不等号の変換用正規表現パターンファイル
* iso_units.md HL7標準 第7章 表7-9 共通ISO単位&ISO+拡張
* ascii_unit.tsv doc\ascii_unit.mdの表を縦積みにしたもの

##sampleフォルダ内の構成
* standard_root 標準化ストレージのルートディレクトリ
    * 0123456789_20080126_OML-11_081251234567800_200802031630123_01_1: 検体検査結果通知(細菌培養同定検査)ファイルのサンプル

* extended_root 拡張ストレージのルートディレクトリ
    * 0123456789_20160101_L-OBSERVATIONS^OBSERVATIONS^99ZL01_000000020160101_201601011500321_1: バイタル検査結果通知1日1ファイルのサンプル
    * 0123456789_20160101_L-OBSERVATIONS^OBSERVATIONS^99ZL01_000002016010115_201601011500321_1: バイタル検査結果通知1日複数ファイルのサンプル
