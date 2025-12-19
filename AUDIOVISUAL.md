✔️ Method 1 — Convert with FFmpeg (best quality)

Since you already have FFmpeg installed, run this:
```
ffmpeg -i input.mp4 -c:v copy -c:a pcm_s16le output_fixed.wav
```

This generates a clean WAV file with 16-bit PCM, which Vegas Pro supports perfectly.

Then inside Vegas:

Import your video

Import output_fixed.wav

Mute or delete the original audio track

Sync if needed (should be frame-accurate)

✔️ Method 2 — Repackage the whole file (video unchanged)

If you prefer to create a new fixed video file:
```
ffmpeg -i input.mp4 -c:v copy -c:a pcm_s16le output_fixed.mp4
```

This keeps the same video, only changing the audio to 16-bit WAV inside the MP4 container.

✔️ Method 3 — Convert audio to AAC (small file, still compatible)
```
ffmpeg -i input.mp4 -c:v copy -c:a aac -b:a 192k output_fixed.mp4
```

This re-encodes audio to standard AAC (quality still good + 100% compatible with Vegas).
