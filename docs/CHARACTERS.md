# キャラクター追加

- ネオン（ninja）：既存の主人公。既存の4枚のPNGをそのまま使用。
- ボルト（volt）：雷モチーフの黄色いロボ剣士。
- プリズム（prism）：白とミントの結晶剣士。
- エコー（echo）：ピンクのヘッドホンを着けた音響剣士。

キャラ選択はタイトルの「変更」から開きます。カードをタップして試着、「斬ってみる」でポーズ確認、「このキャラで遊ぶ」で確定します。戻るボタンはキャンセルです。選択はこの端末のlocalStorage（neon-blade-character）に保存します。ストレージが使えない環境でも、そのページを開いている間は選べます。

能力差はありません。移動、判定、HP、コース、曲は共通です。ボルト・プリズム・エコーはそれぞれ専用ブレイク音を使用します。選択画面の「斬ってみる」で音も試せます。ネオンは既存のbreak.mp3です。作成用プロンプトと組み込み状況はSE-PROMPTS.mdを参照してください。

## 素材

img/characters/volt.webp、prism.webp、echo.webp。
各画像は透明背景の2×2アトラスです。左上＝立ち、右上＝移動、左下＝斬る、右下＝ダメージ。描画時に該当部分を切り出すので、ファイルを12枚に分ける必要はありません。既存キャラの画像・楽曲ファイルは維持しています。ブロック移動音は新しい短い音に更新しています。

新素材は組み込み画像生成ツールで作成し、ゲーム用にアルファを保持したWebPへ圧縮しました。CLI/APIによる画像生成は使用していません。

## 画像生成のプロンプト

共通指定：

Create a production-ready transparent PNG sprite atlas for a colorful mobile 2D rhythm sword game. Use the existing hooded swordsman only as a reference for compact chibi proportions, LEFT-facing orientation, clean cel shading and a readable silhouette. Create a new original character, not a recolor. One square atlas divided invisibly into four equal quadrants: top-left idle with sword pointing left, top-right running left, bottom-left slashing left with one short swoosh, bottom-right recoiling from damage. Exactly four full-body poses of the same character at the same scale. Keep each pose fully within its own quadrant with transparent padding. Large head, small body and limbs, bold near-black outlines, polished flat two-tone cel shading, bright readable accents at 45-pixel game size. Genuine alpha transparency. No scene, floor, cast shadow, text, labels, panels or watermark. No photorealism or 3D rendering.

VOLT:
Character VOLT: cheerful fierce little robotic thunder swordsman, bright lemon-yellow angular helmet with two short lightning-shaped antenna fins, single black visor with white angled eyes, charcoal segmented compact body, yellow forearm and boot guards, short white scarf. Single broad yellow-white zigzag energy sword, mechanical not ninja. Heroic cute but cool.

PRISM:
Character PRISM: elegant little white and mint crystal swordswoman, white bob-shaped smooth helmet with a mint diamond crest, deep teal face opening and luminous mint eyes, white short cape and ivory/mint geometric armor, dark teal small limbs. One translucent mint straight crystal sword. Rounded poised silhouette, neither robot nor hooded ninja. Clear large simple surfaces.

ECHO:
Character ECHO: mischievous little music swordsman with huge circular hot-pink headphone earcups, dark plum rounded helmet with a pale pink horizontal visor, hot-pink short jacket over charcoal body, violet small boots and a short geometric magenta scarf. One pink-violet luminous straight tuning-fork sword with only a tiny split at its tip. Iconic circle motifs, energetic compact figure.

## 確認

Chromiumのスマホ相当画面390×844 / 320×568で、全キャラの選択・4ポーズ・移動・最初の移動ロック・選択キャンセル・再読み込み時の保存・既存SEの読み込みを確認。実機での操作感の評価は未実施です。