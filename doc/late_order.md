# 過去日付のオーダー
更新日: 2021/12/28

## 趣旨
多くの電子カルテには、昨日以前のオーダーを登録出来るユーザーインターフェースが存在している。その場合の診療日の考え方について、機構の認識を以下に示す。

### 診療日の考え方
SS-MIX2 標準化ストレージ 構成の説明と構築ガイドライン Ver.1.2g P9～10の _3.1.1(3)「診療日フォルダー」について_ では、
オーダーは基本的にオーダー日を診療日としており、ORC-9(トランザクション日時)と対応している。
昨日以前を指定してオーダーした場合、SS-MIX2の診療日は __オーダー登録をした日__ となる。
