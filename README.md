# iNAZO-scraping

[北海道大学 成績分布ＷＥＢ公開システム](https://educate.academic.hokudai.ac.jp/seiseki/GradeDistSerch.aspx)から成績分布をスクレイピングするツールです。成績分布を CSV の形式で保存、または DB にデータの保存が可能です。
(※ 旧成績には非対応です)

## Usage

先にインストール済みの Chrome のバージョンに対応した WebDriver を事前にダウンロードしてパスを通す。

```bash
# 成績分布のスクレイピング
$ go run . scraping <year> <semester> <facultyID>

# CSVをデータベースに登録
$ go run . updateGrade
```

**学期**
|semester|学期|
| -- | -- |
|1|1 学期|
|2|2 学期|

**学部 ID の対応表**
| ID | 学部 |
| -- | -- |
|00| 全学教育|
|02| 総合教育部|
|05| 文学部|
|07| 教育学部|
|11| 現代日本学プログラム課程|
|15| 法学部|
|17| 経済学部|
|22| 理学部|
|25| 工学部|
|34| 農学部|
|36| 獣医学部|
|38| 水産学部|
|42| 医学部|
|43| 歯学部|
|44| 薬学部|
|all| 一度に全学部の成績分布を取得|

### Example

2022 年度 1 学期工学部の成績分布の取得

```bash
$ go run . scraping 2022 1 02
```

## OUTPUT

成績分布の CSV ファイルは `data/<year-semester>/<faculty>.csv`に出力される。

**CSV の構造**
|順番|項目|型|
|-|-|-|
|1|授業科目名|string|
|2|講義題目名|string|
|3|クラス|string|
|4|担当教員名|string|
|5|年度|int|
|6|学期|int|
|7|学部|string|
|8|履修者数|int|
|9|GPA|float|
|10|A+(人数)|int|
|11|A(人数)|int|
|12|A-(人数)|int|
|13|B+(人数)|int|
|14|B(人数)|int|
|15|B-(人数)|int|
|16|C+(人数)|int|
|17|C(人数)|int|
|18|D(人数)|int|
|19|D-(人数)|int|
|20|F(人数)|int|
