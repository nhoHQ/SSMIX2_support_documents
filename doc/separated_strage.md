# ストレージを複数ボリュームに分割する場合の考慮
更新日: 2021/12/28

## 趣旨

SS-MIX2 標準化ストレージ 構成の説明と構築のガイドライン Ver.1.2g P5では、

>②「標準化ストレージ」および「拡張ストレージ」を複数のボリュームに分割して管理する場合の考慮  
>1. 格納される診療情報の期間に応じてボリュームを分割する必要がある場合  
>2. データ種別に応じてボリュームを分割する必要がある場合  
>3. 医科・歯科のシステムに対応する場合、ADT-の内容がそれぞれに異なるため、それぞれにストレージを設ける必要がある場合  
>4. 複数の医療施設のストレージを１ヶ所で管理する場合  
>上記のごとく、さまざまな利用目的から「標準化ストレージ」または「拡張ストレージ」を複数ボリュームに分割するケースが考えられる（後述4.4を参照）。この場合には、医療施設IDに続けて、何らかの識別子を付設して「ルートフォルダー」のフォルダー名を設定することを視野に入れる。

としている。

本事業では、『1.格納される診療情報の期間に応じてボリュームを分割する必要がある場合』について、次のように解釈する。  
これは、格納する医療情報が長期間に渡るケースや、DICOM画像を拡張ストレージに格納する必要があるケースなど、標準化ストレージや拡張ストレージが単一のストレージ（HDD)に格納出来ない容量・ボリュームになることを想定している。  
この場合、標準化ストレージおよび拡張ストレージ配下の**『診療日』に応じてルートディレクトリを分割することを推奨**する。ADT-00のように日付の概念を持たないものは、**日付の概念を持たない情報だけのルートフォルダを別に設ける。**
