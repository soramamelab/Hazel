# Coffee Hazel

**Coffee Hazel** は、焙煎中のΔH₂O（ドラム内水分変化量）をリアルタイムで計測し、1ハゼ（First Crack）のタイミングを自動検出するデスクトップアプリケーションです。

株式会社宙豆ラボ制作のCoffee Hazel センサーからデータを Wi-Fi 経由で取得し、ΔH₂O とΔH₂O変化率のグラフをライブ表示します。スマートフォン・タブレットからも同一 Wi-Fi 上でアクセス可能です。

© 2026 SORAMAME LAB INC. All rights reserved.

---

## 主な機能

- **リアルタイムグラフ** — ΔH₂O（上段）とΔH₂O変化率（下段）を 2 秒間隔で更新
- **1ハゼ自動検出** — ΔH₂O変化率が閾値を超えるとアラートとチャイム音で通知
- **投入・チャージ自動検出** — ΔH₂Oの急変動（正負両方向）から生豆投入を検知し、グラフを 0 分に自動整列
- **豆プリセット** — 豆ごとに設定一式を保存・切り替え
- **CSV エクスポート** — 焙煎データを CSV で保存
- **CSV Viewer** — 過去の焙煎 CSV を読み込んでグラフ表示
- **スマホアクセス** — QR コードで同一 Wi-Fi 上のスマホからリアルタイム確認

---

## インストール

### macOS

1. [Releases](https://github.com/soramamelab/Hazel/releases) から `CoffeeHazel-v2.1.0.dmg` をダウンロード
2. DMG を開き、`Coffee Hazel.app` をアプリケーションフォルダにドラッグ＆ドロップ
3. 初回起動時は右クリック →「開く」で Gatekeeper の警告をスキップ

### Windows

[Releases](https://github.com/soramamelab/Hazel/releases) から `HazelSetup.exe` をダウンロードして実行してください。

### Ubuntu / Linux

[Releases](https://github.com/soramamelab/Hazel/releases) から `coffee-hazel_2.0.1_amd64.deb` をダウンロードし、以下を実行してください。

```bash
sudo dpkg -i coffee-hazel_2.0.1_amd64.deb
sudo apt --fix-broken install   # 依存パッケージ不足時
```

インストール後は `coffee-hazel` コマンド、またはアプリケーションメニューの「Coffee Hazel」から起動できます。詳細は [manual.md](manual.md#インストールubuntu--linux) を参照してください。

---

## 必要環境

- Coffee Hazel センサー（株式会社　宙豆ラボ製）
- PC と Coffee Hazel センサーが同じ Wi-Fi ネットワークに接続されていること

---

## スクリーンショット

> アプリ起動後、ブラウザで `http://localhost:8050` にアクセスしても同じ画面を利用できます。

---

## ドキュメント

詳しい使い方は [manual.md](manual.md) を参照してください。

---

## バージョン履歴

| バージョン | 内容 |
|-----------|------|
| **V2.1.0** | macOS版をIntel Mac（x86_64）対応に。Apple Silicon（M1/M2/M3）はRosetta 2経由で引き続き動作 |
| **V2.0.2** | 1ハゼ検出しきい値スライダーおよび急変動しきい値スライダーに現在値の数値表示を追加 |
| **V2.0.1** | ΔH₂O・ΔH₂O変化率に用語統一。投入・チャージ自動検出を急変動（正負両方向）に変更。更新間隔デフォルト 2 秒。アプリアイコン追加。著作権表示追加。Ubuntu 用 `.deb` パッケージを追加 |
