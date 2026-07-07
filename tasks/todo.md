# ゼロベース・リデザイン v3「THE UPTIME LINE」

計画: `/Users/atsushi/.claude/plans/quirky-drifting-haven.md`

## Todo

- [x] ブランチ `feat/redesign-v3` 作成（main から）
- [x] index.html 全面書き換え（Syne + IBM Plex Sans JP + JetBrains Mono、ニアブラック+インターナショナルオレンジ）
- [x] ヒーロー（巨大タイポ・アウトライン混合・縦書き名・ロード演出）
- [x] THE LINE（スクロール連動描画のキャリアタイムライン）
- [x] WORKS グリッド（ヘアライン分割・グレースケール→彩色ホバー）
- [x] LINKS / フッター「KEEP IT RUNNING.」
- [x] 品質フロア（reduced-motion / focus-visible / モバイル）
- [x] 検証（ヒーロー・ライン描画・モバイル・エラーゼロ）
- [x] コミット・push・PR 作成

## レビュー

- コンセプト「THE UPTIME LINE」: 2015年から途切れないキャリアを1本の発光ラインとして表現。スクロールに連動して stroke が伸びる（`spineFill` の scaleY、rAF + passive scroll）。
- パロディ要素は全廃（コンソール UI・ピクセルアート・コマンドパレット・ブート演出なし）。タイポグラフィ（Syne 800 の塗り/アウトライン混合、縦書き「大嶋淳司」）と余白で構成。
- 検証: ヒーロー/CAREER/WORKS/フッターの表示、ラインのスクロール連動（scaleY 0→0.096→0.60 を JS で確認）、モバイル 390px、コンソールエラーゼロ。
- 調整履歴: ヒーロー名のはみ出し（12.5vw→9.6vw + nowrap）のみ。
- 環境メモ: 検証用 Chrome はスクロール後のスクリーンショットが乱れる/真っ黒になる既知の癖あり。iframe 内スクロール + アニメーション無効化で実描画を確認する手法が有効。
