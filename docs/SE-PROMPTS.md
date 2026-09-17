# Neon Blade — ElevenLabs SEプロンプト

以下は作成時に使った推奨設定です。ボルト・プリズムはユーザー提供音源、エコー・ブロック移動音は新しく生成して組み込み済みです。
Sound Effectsで使い、DurationはAutoから手動指定、LoopingはOFF。
Prompt influenceは最初は既定の30%で試してください。

| 用途 | 生成する長さ | 鳴ってほしい部分の長さ | 保存名 |
|---|---:|---:|---|
| ゴール | 1.5秒 | 約1.3秒＋短い余韻 | goal.mp3 |
| ボルトのブレイク | 0.5秒 | 約0.20秒 | break_volt.mp3 |
| プリズムのブレイク | 0.5秒 | 約0.25秒 | break_prism.mp3 |
| エコーのブレイク | 0.5秒 | 約0.20秒 | break_echo.mp3 |
| ブロックが1マス動く | 0.5秒 | 約0.08〜0.12秒 | block_move.mp3 |

0.5秒はElevenLabs APIで確認できた最短生成時間です。Web画面で0.5秒を指定できなければ、選べる最短時間で生成してください。先頭の無音や後ろの余白は、ダウンロード後に切り取る方針です。プロンプト内の時間は狙いであり、正確な長さを保証するものではありません。

## ゴール — 明るく弾ける達成音

```text
A joyful victory stinger for a colorful neon rhythm game. An immediate crisp sparkle impact, then three quick rising electronic bell tones resolving into a bright, satisfying major chord. Punchy and celebratory, clean modern arcade synths, tiny glittering tail. Finish within 1.5 seconds. No voice, no drums, no background music, no long reverb, no silence before the attack. Original melody.
```

現在の「輪が広がる→CLEAR!」に合う音。ブレイク音より華やかにします。既存のgoal.mp3を上書きするのは、生成した音を気に入ってからでOKです。

## ボルト — 黄の雷剣士

```text
One lightning sword break impact for a rhythm game. A razor-fast electric slash fused with a tight bright zap and a crunchy digital snap. Sharp, energetic and satisfying, not harsh. The main hit starts immediately and decays within 0.20 seconds; the rest is silent. One hit only. No thunder rumble, no voice, no music, no repeated hits, no long reverb or lead-in.
```

「ザシュッ＋パチッ」。雷鳴の長いゴロゴロ音は入れません。

## プリズム — 白とミントの結晶剣士

```text
One crystal sword break impact for a rhythm game. A swift silky slash fused with a clean glassy crack and a delicate high crystalline ping. Clear, cool and satisfying, with a soft sparkling decay under 0.25 seconds. Immediate attack, then silence. One hit only. No falling debris sequence, no ice storm, no voice, no music, no repeated hits, no long reverb.
```

「シャキン＋チン」。細かいガラスが何秒も落ち続ける音を避けます。

## エコー — ピンクの音響剣士

```text
One sonic sword break impact for a rhythm game. A short sweeping synth slash fused with a tight rubbery bass pluck and a crisp digital pop. Playful, punchy, clean and futuristic, audible on a phone speaker. Immediate attack and fast decay under 0.20 seconds; the rest is silent. One hit only. No melody, no drums, no voice, no echo repeats, no sustained sub-bass or long reverb.
```

「ビュッ＋ポン」。低音は短く、スマホでも聞こえる中音の芯を残します。

## ブロック移動 — 1拍に1回の小さな動作音

```text
One tiny tactile movement tick for a neon rhythm game tile snapping one grid cell forward. A soft synthetic tok with a very short airy swish, precise and dry, light and rounded rather than sharp. Immediate onset, total audible sound about 0.10 seconds, then silence. One tick only. No beat pattern, no bass boom, no voice, no music, no repeating clicks and no reverb.
```

ノーツ1個につき鳴らすのではなく、複数のノーツが同時に動いても1拍に1回だけ鳴らします（今の実装もこの形です）。ブレイクより控えめな音を選んでください。

## 組み込み状況（2026-09-17）

- ネオン：既存のaudio/break.mp3。
- ボルト：ユーザー指定のOne_lightning_sword__#4-1789649278166.mp3をaudio/break_volt.mp3へコピー。音源の内容は変更なし、ゲーム内ゲイン0.45。
- プリズム：ユーザー指定のOne_crystal_sword_br_#2-1789649497073.mp3をaudio/break_prism.mp3へコピー。音源の内容は変更なし、ゲーム内ゲイン0.60。
- エコー：新規生成し、余韻を約0.34秒に整理。元音量の0.55倍で書き出し、末尾30msをフェード。audio/break_echo.mp3。
- ブロック移動：新規生成し、冒頭約0.12秒を使用。生成音が非常に小さかったため65倍で書き出し、末尾35msをフェード。ゲーム内ゲイン0.22。audio/block_move.mp3を更新し、URLの?v=2で旧キャッシュを回避。
- 上記の秒数はデコードした音声長。MP3コンテナの時間表示はエンコーダーの余白分だけ長い場合があります。
- ブレイクは判定ごとの音量・ピッチ調整を維持。新キャラは専用音の個性を残すため、ネオン用PERFECT追加音を重ねません。
- 「斬ってみる」はプレビュー中のキャラの音を鳴らし、選択確定や成績には影響しません。
- ブロック移動音は、複数のノーツが同時に動いても1拍につき1回。
- 専用音の読み込みに失敗したキャラは、既存のブレイク音を使用。
- 既存のゴール音・曲・ルール・判定は維持。

## 確認した公式資料

- Sound Effectsの手動時間設定、Looping、Prompt influence：
  https://elevenlabs.io/docs/eleven-creative/playground/sound-effects
- APIのduration_secondsは0.5〜30秒：
  https://elevenlabs.io/docs/api-reference/text-to-sound-effects/convert

確認日：2026-09-17