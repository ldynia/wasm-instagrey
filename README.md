# WASM Instagrey

## OS Dependencies

```bash
# Rust
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
cargo install wasm-pack

# NodeJs
sudo apt-get update && sudo apt-get install -y nodejs npm
```

## HTML5

```bash
# Build
wasm-pack build --target web backend/
cp -r backend/pkg frontend/html5

# Serve
python3 -m http.server --directory frontend/html5
docker stop app && docker run -d --rm --name app --publish 8080:80 --volume $PWD/frontend/html5:/usr/share/nginx/html nginx
```

## NodeJS

```bash
# Build
wasm-pack build --target bundler backend/

# Setup
sudo rm -rf /usr/local/lib/node_modules
cd backend/pkg/
sudo npm link
cd ../../frontend/nodejs/
npm link backend
npm install

# Serve
npm run serve
```