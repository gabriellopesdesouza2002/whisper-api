# 🧠 Whisper API

API local de transcrição de áudio com **OpenAI Whisper**, compatível com o formato da OpenAI (`/v1/audio/transcriptions` e `/v1/chat/completions`).

[![Docker Pulls](https://img.shields.io/docker/pulls/gabriellopesdesouza2002/whisper-api?style=for-the-badge)](https://hub.docker.com/r/gabriellopesdesouza2002/whisper-api) [![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)](https://python.org) [![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi)](https://fastapi.tiangolo.com)

## 🚀 Funcionalidades

- 🎙️ Transcrição de áudio com suporte a múltiplos formatos (.mp3, .wav, .flac, etc)
- 🔐 Proteção com autenticação Bearer (API_KEY)
- 📦 Compatível com chamadas da OpenAI (padrão /v1/audio/transcriptions)
- 💬 Suporte experimental ao endpoint /v1/chat/completions com entrada de áudio via base64
- ⚡ Pronto para uso com Docker ou n8n

## ▶️ Como executar

```bash
docker pull gabriellopesdesouza2002/whisper-api:latest
docker run -d -p 5001:5001 \
  --env API_KEY=sua-chave \
  --env WHISPER_MODEL=small \
  gabriellopesdesouza2002/whisper-api:latest
```

## 📥 Exemplo de requisição

```bash
curl -X POST http://localhost:5001/v1/audio/transcriptions \
  -H "Authorization: Bearer SUA_CHAVE_AQUI" \
  -F model=whisper-1 \
  -F file=@/caminho/para/arquivo.mp3
```

## 🔐 Variáveis de ambiente

| Variável | Descrição | Obrigatória |
|---|---|---|
| WHISPER_MODEL | Modelo do Whisper (tiny, small, etc) | ✅ |
| API_KEY | Chave de acesso da API via Bearer | ✅ |

## 🧪 Testado com

- Docker Compose
- n8n (HTTP Request + Binary File)
- Postman / cURL

## 🐳 Docker Hub

Imagem disponível no Docker Hub: [gabriellopesdesouza2002/whisper-api](https://hub.docker.com/r/gabriellopesdesouza2002/whisper-api)

## Stack

```
python:3.11.10-slim + ffmpeg + uvicorn + fastapi + torch + whisper
```
