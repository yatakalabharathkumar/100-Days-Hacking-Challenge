## 🗓️ Day 19/100 – HTML5 Audio & Video Tags

**Focus:** Native multimedia embedding in HTML5.

### 🎵 Audio Implementation
```html
<audio controls preload="metadata">
  <source src="background-music.mp3" type="audio/mpeg">
  <source src="background-music.ogg" type="audio/ogg">
  Your browser does not support the audio element.
</audio>

### 🎥 Video Implementation
<video width="800" height="450" controls poster="thumbnail.jpg">
  <source src="tutorial.mp4" type="video/mp4">
  <source src="tutorial.webm" type="video/webm">
  <track src="captions.vtt" kind="subtitles" srclang="en" label="English">
</video>

✅ Key Attributes Learnedcontrols – Shows native play/pause/volume UIsrc / <source> – Media file location + formatposter – Video thumbnail before playbackpreload – Loading strategy (auto/metadata/none)loop autoplay muted – Playback behavior🔍 Security ContextPotential Attack Surfaces:File upload vulnerabilities in user media submissionXSS via src attribute manipulationDoS via large media file uploadsMetadata leakage in EXIF/IPTC dataDay 19 Takeaway: Native HTML5 media makes websites engaging but introduces new security considerations around file handling and user content.
