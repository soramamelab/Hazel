# Coffee Hazel

**Coffee Hazel** は、焙煎中のΔH₂O（ドラム内水分変化量）をリアルタイムで計測し、1ハゼ（First Crack）のタイミングを自動検出するデスクトップアプリケーションです。

株式会社宙豆ラボ制作のCoffee Hazel センサーからデータを **Wi-Fi または Bluetooth (BLE)** 経由で取得し、ΔH₂O とΔH₂O変化率のグラフをライブ表示します。スマートフォン・タブレットからも同一 Wi-Fi 上でアクセス可能です。

© 2026 SORAMAME LAB INC. All rights reserved.

---

## 主な機能

- **リアルタイムグラフ** — ΔH₂O（上段）とΔH₂O変化率（下段）を 2 秒間隔で更新
- **1ハゼ自動検出** — ΔH₂O変化率が閾値を超えるとアラートとチャイム音で通知
- **投入・チャージ自動検出** — ΔH₂Oの急変動（正負両方向）から生豆投入を検知し、グラフを 0 分に自動整列
- **豆プリセット** — 豆ごとに設定一式を保存・切り替え
- **CSV エクスポート** — 焙煎データを CSV で保存
- **グラフ画像エクスポート** — 表示中のグラフを PNG / JPG / PDF で保存
- **CSV Viewer** — 過去の焙煎 CSV を読み込んでグラフ表示
- **スマホアクセス** — QR コードで同一 Wi-Fi 上のスマホからリアルタイム確認
- **QR コード印刷ページ** — スマホアクセス用の QR コードを印刷して掲示できる（シェアロースター向け）
- **Bluetooth (BLE) 接続** — 2.4GHz Wi-Fi が使えない環境でも Bluetooth 経由でセンサーに直接接続

---

## インストール

### macOS

CPUに合わせてDMGを選択してください（Apple メニュー →「このMacについて」で確認）。

| Mac の種類 | ダウンロードするファイル |
|-----------|----------------------|
| Apple Silicon（M1 / M2 / M3 など） | [`CoffeeHazel-v2.3.1-AppleSilicon.dmg`](https://github.com/soramamelab/Hazel/releases/download/v2.3.1/CoffeeHazel-v2.3.1-AppleSilicon.dmg) |
| Intel Mac | [`CoffeeHazel-v2.3.1-Intel.dmg`](https://github.com/soramamelab/Hazel/releases/download/v2.3.1/CoffeeHazel-v2.3.1-Intel.dmg) |

1. 上記のファイルをダウンロード
2. DMG を開き、`Coffee Hazel.app` をアプリケーションフォルダにドラッグ＆ドロップ
3. 初回起動時に「"Coffee Hazel"は開いていません」と表示された場合（Apple公証を受けていないアプリに出る標準の警告です）:
   - **macOS 15（Sequoia）以降**: 警告を閉じ → システム設定 →「プライバシーとセキュリティ」→「このまま開く」→ Touch ID またはパスワードで許可
   - **macOS 14（Sonoma）以前**: アプリケーションフォルダで右クリック →「開く」→「開く」

### Windows

[Releases](https://github.com/soramamelab/Hazel/releases) から `HazelSetup.exe` をダウンロードして実行してください。（対応OS: Windows 10 以降）

> 起動後に画面が表示されない場合は、WebView2 ランタイムが未導入の可能性があります。[Evergreen Bootstrapper](https://developer.microsoft.com/microsoft-edge/webview2/) からインストールしてください。詳細は [manual.md](manual.md#10-トラブルシューティング) を参照してください。

### Ubuntu / Linux

[Releases](https://github.com/soramamelab/Hazel/releases) から `coffee-hazel_2.3.1_amd64.deb` をダウンロードし、以下を実行してください。（対応OS: Ubuntu 22.04 / 24.04）

```bash
sudo dpkg -i coffee-hazel_2.3.1_amd64.deb
sudo apt --fix-broken install   # 依存パッケージ不足時
```

インストール後は `coffee-hazel` コマンド、またはアプリケーションメニューの「Coffee Hazel」から起動できます。詳細は [manual.md](manual.md#インストールubuntu--linux) を参照してください。

> **Bluetooth を使う場合（Linux）**: BlueZ が必要です。`.deb` パッケージには依存関係として含まれているため、通常は追加作業不要です。

---

## 接続モード

設定サイドバーの「接続モード」で **Wi-Fi** と **Bluetooth** を切り替えられます。

| モード | 必要な環境 | 特徴 |
|--------|-----------|------|
| **Wi-Fi**（デフォルト） | PC と Coffee Hazel が同じ 2.4GHz Wi-Fi に接続 | スマホからも同時アクセス可能 |
| **Bluetooth** | PC の Bluetooth 4.0 以上（BLE対応） | 2.4GHz Wi-Fi がない環境でも使用可能 |

> **Bluetooth モードのご注意**  
> PC が Coffee Hazel センサーに直接接続します。スマートフォンや他デバイスからの同時アクセスはできません。

---

## 必要環境

- Coffee Hazel センサー（株式会社　宙豆ラボ製、ファームウェア V2.2 以降）
- **Wi-Fi モード**: PC と Coffee Hazel センサーが同じ 2.4GHz Wi-Fi ネットワークに接続されていること
- **Bluetooth モード**: PC に Bluetooth 4.0 以上（BLE対応）が搭載されていること

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
| **V2.3.1** | **Linux版: 起動直後にクラッシュする不具合を修正** — ビルド環境の古いGTK/WebKitGTKライブラリが同梱されており、新しいUbuntu（24.04など）でシンボル不整合により起動できない問題を解消 |
| **V2.3.0** | **グラフ画像の保存（PNG / JPG / PDF）**・**QRコード印刷ページ**を追加。スマホアクセス時の保存UIを改善（PC側にフォルダ選択ダイアログが開く問題を修正）。X軸メモリを1分間隔に固定。焙煎終了後は1ハゼの「いいえ（取消）」バーを非表示に |
| **V2.2.3** | **Ubuntu 22.04 で起動できない問題を修正**（glibc互換性対応、22.04 / 24.04 両対応に） |
| **V2.2.2** | アプリ画面のバージョン表示を自動化（VERSION ファイルから取得）。リリースノートを CHANGELOG から自動生成するようビルドを改善 |
| **V2.2.1** | **Windows: 上書きインストール時の起動クラッシュを修正** — 旧バージョンのファイルが残って新バージョンと混在し起動に失敗する問題を解消。v2.2.0 以前で発生済みの場合も本バージョン以降の上書きインストールで解消 |
| **V2.2.0** | **Bluetooth (BLE) 接続モード追加** — 2.4GHz Wi-Fi 不要で Coffee Hazel センサーに直接接続可能に。設定サイドバーで Wi-Fi / Bluetooth を切り替え |
| **V2.1.1** | macOS版をApple Silicon用・Intel用の2種類のDMGに分離。macOS 15以降のGatekeeper回避手順を更新 |
| **V2.1.0** | macOS版をIntel Mac（x86_64）対応に。Apple Silicon（M1/M2/M3）はRosetta 2経由で引き続き動作 |
| **V2.0.2** | 1ハゼ検出しきい値スライダーおよび急変動しきい値スライダーに現在値の数値表示を追加 |
| **V2.0.1** | ΔH₂O・ΔH₂O変化率に用語統一。投入・チャージ自動検出を急変動（正負両方向）に変更。更新間隔デフォルト 2 秒。アプリアイコン追加。著作権表示追加。Ubuntu 用 `.deb` パッケージを追加 |
