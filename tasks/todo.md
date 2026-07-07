# ゼロベース・リデザイン v4「THE UPTIME LINE — SPECTACLE」

計画: `/Users/atsushi/.claude/plans/quirky-drifting-haven.md`（v3 計画 + 全部盛り方向の追加指示）

## Todo

- [x] v3 の骨格（Syne タイポ + ライン + コンテンツ）を維持
- [x] 動くオーロラ背景（orange/violet/cyan の3ブロブ、blur 90px）
- [x] カーソル連動ノードネットワーク canvas（接続線・吸引・ping リング）
- [x] ネオングロー（ヒーロー OSHIMA=オレンジ輪郭+パルス、ATSUSHI=グラデーションシーン）
- [x] ガラス質感（nav ピル・spec・works カード、backdrop-blur + グレア）
- [x] 3D チルト（works カード + spec、カーソル追従グレア付き）
- [x] カーソルスポットライト・ライン先端の発光チップ・live ノードのリング波紋
- [x] reduced-motion 全対応（canvas/spotlight/tilt/シーン停止）・pointer:fine 判定
- [x] 検証（ヒーロー・CAREER・WORKS・フッター・モバイル390px・エラーゼロ）
- [x] コミット・push（PR #5 に追加）

## レビュー

- v3「静的でミニマル」→ v4「全部盛りスペクタクル」へ。ユーザーの「めっちゃかっこいい」=動きと光の演出だった。
- 修正した不具合: `.hero h1 .fill` の animation ショートハンドが `.line-inner` の riseup を上書きし名前が非表示になった（詳細度 (0,2,1)>(0,2,0)）。マークアップを `<span class="line-inner"><b class="fill">` に分離して解決。
- パフォーマンス配慮: パーティクル数は面積比で 28〜85、dpr cap 2、document.hidden で rAF 停止、tilt は rAF スロットル。
- 検証環境の癖（スクロール後キャプチャの黒落ち）は継続。iframe + アニメ無効化で実描画確認。
