# WhisperTranscriber

2025/4/13

```cmd
uv venv
.venv\Scripts\activate
uv pip install faster-whisper
uv pip install torch torchaudio --index-url https://download.pytorch.org/whl/cu126
python whisper-transcriber.py .\audio\Sample1\Sample1.mp3
```