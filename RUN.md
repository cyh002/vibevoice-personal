# VibeVoice Studio - Quick Run Guide

## Setup & Start
```bash
source venv/bin/activate
pip install -r requirements.txt
python -m app.main
```

Server runs at: `https://vibevoicetts.tail.cyhriside.quest`

## API Endpoints

* `GET /api/voices` — list voices
* `POST /api/voices/upload` — upload voice
* `POST /api/voices/record` — record voice
* `POST /api/generate` — generate speech
* `GET /api/audio/{filename}` — download audio

## Testing Commands

### Health Check
```bash
curl httpss://vibevoicetts.tail.cyhriside.quest/api/health
```

### List Voices
```bash
curl https://vibevoicetts.tail.cyhriside.quest/api/voices
```

### Generate Speech
```bash
curl -X POST https://vibevoicetts.tail.cyhriside.quest/api/generate \
  -H "Content-Type: application/json" \
  -d '{
    "text": "Hello, this is a test of voice synthesis",
    "voice_name": "chris-english",
    "cfg_scale": 2.0,
    "num_speakers": 1
  }' \
  -o response.json
```

### Download Audio
```bash
curl -X GET https://vibevoicetts.tail.cyhriside.quest/api/audio/filename.wav -o output.wav
```

### Upload Voice
```bash
curl -X POST https://vibevoicetts.tail.cyhriside.quest/api/voices/upload \
  -F "file=@/path/to/voice.wav" \
  -F "name=MyVoice"
```

## Listen to Audio
```bash
# Direct browser: https://vibevoicetts.tail.cyhriside.quest/api/audio/filename.wav
# Command line:
mpv https://vibevoicetts.tail.cyhriside.quest/api/audio/filename.wav
vlc output.wav
```

## Web Interface
Open `https://vibevoicetts.tail.cyhriside.quest` for full UI testing