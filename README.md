# 概要
- Public このプロジェクトでは、OpenAI o1 proが出力したプロットタイプの分類データからデータベースを作り、ランダムに取り出したプロットのリファレンスから物語のプロットのアイデアを生成します。
- このプロジェクトは、ChatGPT Proで使用できる、OpenAIのo1 pro modeの検証を兼ねています

# 手順
- ChatGPT Proのo1 pro modeに、物語のプロットを分類させます
  - [prot-type.md](https://github.com/masa-jp-art/prot-type-db/blob/main/prot-type.md)
- 出力されたプロットタイプをスプレッドシートに転記してデータベースを作ります
  - [20250102-prot-type-snapshot](https://docs.google.com/spreadsheets/d/1vLihxLF6ICbKBCVnP6tBbZEoWA-eDNM095_UnNLsTyg/)
- Google colabでプログラムを動かし、キャラクターとあらすじを生成します
  - [code-for-google-colab.py](https://github.com/masa-jp-art/prot-type-db/blob/main/code-for-google-colab.py)
 
# 関連
- [OpenAI o1 pro mode検証:マンガのプロットタイプデータベースが作れるか](https://note.com/msfmnkns/n/nec75b5ce0db0)

## 用語と用例

ここでの「プロットタイプ」は、出来事の展開を発想するための型です。たとえば [分類資料](prot-type.md)の「旅（クエスト）」では、目的、障害、転換、クライマックス、結末を手掛かりにします。架空の例なら「失った記憶を探す主人公が、旅先で目的を問い直す」といった案を、人物設定と組み合わせて考えられます。型は完成した物語や唯一の正解ではありません。

## 分類の背景と成立

概要にある通り、o1 pro modeに物語のプロットを分類させ、その出力を再利用できる参照データにする検証が出発点です。収録内容は生成AIによる創作用の整理で、特定の物語論の原典を網羅・再現した標準分類と断定するものではありません。分類を作る工程と、人物設定からプロット案を生成する工程を分けています。

## 技術的な流れと展開

[Colab用コード](code-for-google-colab.py)は Google認証でシートを開き、`prot` シートの2列目から見出しを除いて1件をランダム選択します。それを主人公・サブキャラクター・対立者の設定と一緒にOpenAI APIへ渡してプロットを出力します。シートURL・人物設定・API設定は利用者が用意する必要があります。

同じ人物で異なる型を試したり、同じ型に別の人物を当てて展開案を比較するための出発点として利用できます。出力は企画素材として確認・編集するもので、作品の独創性や完成度、APIの現在の互換性を保証するものではありません。

