# VibeVoice Studio - Quick Run Guide

## Setup & Start
```bash
source .venv/bin/activate
pip install -r requirements.txt
python -m app.main
```

Server runs at: `http://localhost:8716`

## API Endpoints

* `GET /api/voices` — list voices
* `POST /api/voices/upload` — upload voice
* `POST /api/voices/record` — record voice
* `POST /api/generate` — generate speech
* `GET /api/audio/{filename}` — download audio

## Testing Commands

### Health Check
```bash
curl http://localhost:8716/api/health
```

### List Voices
```bash
curl http://localhost:8716/api/voices
```

### Generate Speech
```bash
curl -X POST http://localhost:8716/api/generate \
  -H "Content-Type: application/json" \
  -d '{
    "text": "Hello, this is a test of voice synthesis",
    "voice_id": "d0b84353-3dfb-41da-bb30-a9d354b8a5fd",
    "cfg_scale": 1.3,
    "num_speakers": 1
  }' \
  -o response.json
```

### Download Audio
```bash
curl -X GET http://localhost:8716/api/audio/filename.wav -o output.wav
```

### Upload Voice
```bash
curl -X POST http://localhost:8716/api/voices/upload \
  -F "file=@/path/to/voice.wav" \
  -F "name=MyVoice"
```

## Listen to Audio
```bash
# Direct browser: http://localhost:8716/api/audio/filename.wav
# Command line:
mpv http://localhost:8716/api/audio/filename.wav
vlc output.wav
```

## Web Interface
Open `http://localhost:8716` for full UI testing