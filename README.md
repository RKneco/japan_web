# 📑 日本ウェブプロジェクト (フルスタック)

このプロジェクトは、**Spring Boot** と **React** を統合管理するマルチモジュールレポジトリです。

## 📂 プロジェクト構成

```text
japan_web (Root)
 ├── backend/          # Spring Boot (Java 17, Gradle)
 ├── frontend/         # React (JavaScript)
 └── .gitignore        # IDE 設定およびライブラリ除外管理

```

## 🛠️ 初期開発環境の設定 (共通)

### 1. IntelliJ プロジェクトの連携

* **Backend:** `backend/build.gradle` ファイルを右クリックし、**'Add as Gradle Project'**を選択します。
* **VCS 設定:** `Settings` > `Version Control` > `Directory Mappings`にて、下位フォルダの個別マッピングをすべて削除し、ルート (`japan_web`)のみを登録します。

### 2. ブランチ戦略

* **ブランチ名:** 基本の開発ブランチは `dev`です。
* **作業フロー:** 各自、機能別のブランチ(`feat/機能名`)を作成して作業を行い、GitHub上で `dev` ブランチに対して **Pull Request(PR)**を作成します。
* **ブランチ保護:** `dev` ブランチへの直接 `Push`は制限されており、チームメンバーの承認を経て `Merge`が可能となります。

---

## 🖥️ Backend (Spring Boot)

### 主要設定

* **CORS 許可:** フロントエンド(Port 3000)との通信のため、`WebConfig` クラスにてアクセスを許可しています。
* **API 確認:** `HelloController` などを通じて、バックエンドの正常動作を確認できます。

### 実行方法

```bash
cd backend
./gradlew bootRun

```

---

## 🌐 Frontend (React)

### 主要設定

* **環境変数:** `frontend/.env` ファイルにバックエンドの API アドレスが設定されています。
* **API 通信:** HTTP 通信のために `axios` ライブラりを使用しています。
* **Proxy:** `package.json`に `http://localhost:8080`のプロキシ設定がされており、CORS エラーを防止します。

### 実行方法

```bash
cd frontend
npm install   # 初回のみ実行
npm start     #

```

---

## ⚠️ 注意事項 (必読)

1. **入れ子の .git 削除:** Reactのインストール時に生成される `frontend/.git` フォルダは削除済みです。今後、再インストールする際も内部に `.git` フォルダが生成されないよう注意してください。
2. **大文字・小文字の区別:** Javaのクラス名とファイル名は、大文字・小文字が一致している必要があります。(例: `WebConfig.java`)
3. **.gitignore 管理:** `node_modules`, `.idea`, `build/`などのビルド成果物や設定ファイルが GitHubにpushされないよう注意してください。

4. ---

