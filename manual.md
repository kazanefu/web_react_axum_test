```bash
sudo apt update
sudo apt install build-essential pkg-config libssl-dev

# Rust
curl https://sh.rustup.rs -sSf | sh
source $HOME/.cargo/env

# Node
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt install -y nodejs

# Rustとnodeのバージョンを確認して正常にインストールできたか確認
rustc --version
node -v

# フロントエンド部分のセットアップ
npm create vite@latest frontend
# React + TypeScript を選択
cd frontend
npm install
npm run dev

# バックエンド部分のセットアップ
# プロジェクトのルートディレクトリでgitを使うので--vcs none
cargo new backend --vcs none
cd backend
```
Cargo.tomlに以下の依存関係を追加
```toml
[dependencies]
axum = "0.8.8"
tokio = { version = "1", features = ["full"] }
serde = { version = "1", features = ["derive"] }
serde_json = "1"
uuid = { version = "1", features = ["v4"] }
tower-http = { version = "0.6.8", features = ["cors"] }
sqlx = { version = "0.8.6", features = ["sqlite", "runtime-tokio-rustls", "macros"] }
bcrypt = "0.18.0"
```

フロントエンドをCloudflare Pagesで公開
/frontendで
```bash
npm run build
```