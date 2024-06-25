# dictnv-icp-exercise

{
  "version": 1,
  "dfx": "0.19.0",
  "canisters": {
    "backend": {
      "type": "custom",
      "main": "backend/index.ts",
      "candid": "backend/index.did",
      "candid_gen": "automatic",
      "build": "npx azle backend",
      "wasm": ".azle/backend/backend.wasm",
      "gzip": true,
      "assets": [["backend/database/migrations", "migrations"]],
      "metadata": [
        {
          "name": "candid:service",
          "path": "backend/index.did"
        },
        {
          "name": "cdk:name",
          "content": "azle"
        }
      ]
    },
    "frontend": {
      "type": "assets",
      "dependencies": ["backend"],
      "frontend": {
        "entrypoint": "frontend/build/index.html"
      },
      "source": ["frontend/build"]
    },
    "internet-identity": {
      "type": "custom",
      "candid": "https://github.com/dfinity/internet-identity/releases/download/release-2023-09-08/internet_identity.did",
      "wasm": "https://github.com/dfinity/internet-identity/releases/download/release-2023-09-08/internet_identity_dev.wasm.gz",
      "remote": {
        "id": {
          "ic": "rdmx6-jaaaa-aaaaa-aaadq-cai"
        }
      }
    }
  }
}