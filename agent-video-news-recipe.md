# Automated News Video Generation — LLM Actionable Workflow

This workflow describes the precise, tool-oriented steps an AI assistant or LLM agent should follow to generate an end-to-end news video from today’s US news using modular tools (search, TTS, subclipping, merging, etc).

---

## Workflow Steps (LLM Instructions)

### 1. Fetch and Summarize Top News (US)
**Tool:** Web/news search API or AI-powered news summarizer  
**Steps:**
- Search reliable news sources for top 5 stories about the US for today.
- Summarize each story into a 1–2 sentence headline and short summary.
**Output:** JSON or markdown list of 5 news stories with headlines and summaries.

---

### 2. Script Drafting
**Tool:** LLM text generator  
**Steps:**
- Draft a broadcast-style script, one paragraph per news story.
- Include an intro and a concise closing statement.
**Input:** Summarized stories.
**Output:** News video script (plain text).

---

### 3. Voiceover Generation
**Tool:** AI Text-to-Speech (TTS)  
**Steps:**
- Use the script as input to a TTS system with a “news anchor” voice preset.
**Input:** Script text.
**Output:** Downloadable audio file (mp3/wav).

---

### 4. Transcribe Audio & Create Timeline
**Tool:** Speech-to-Text (STT)/audio segmenter  
**Steps:**
- Analyze the TTS voiceover to extract timestamped sections matching each story.
**Input:** Audio file.
**Output:** List of start/end timestamps and associated script sections.

---

### 5. Visual Asset Search & Subclipping
**Tool:** Stock video search API & video subclipper  
**Steps:**
- For each news story, issue search queries for relevant stock video (e.g., “US Capitol building”, “Wall Street”, etc.).
- Select a video for each section and use a subclip tool to extract an 8s (or less) clip from each source.
**Input:** Section summaries + keywords.
**Output:** List of short video clip download links.

---

### 6. Sequence Video Clips
**Tool:** Video merge/combine API  
**Steps:**
- Arrange video clips in the news script order, matching the timeline.
- Merge all subclips into a single video.
**Input:** Ordered video clip links.
**Output:** One combined news video file.

---

### 7. Overlay Voiceover on Video
**Tool:** Audio/video merger/muxer  
**Steps:**
- Merge the voiceover audio file onto the combined video so that speech matches visual segments.
**Input:** Combined video + voiceover file.
**Output:** Final news video with narration.

---

### 8. (Optional) Documentation
**Tool:** Markdown generator & GitHub API  
**Steps:**
- Document the news story sources, audio/video asset links, and workflow details.
- Save the workflow summary as a markdown file in the project repo for reference and reproducibility.

---

## Example Tool Table

| Step           | Tool API or Plugin Example                |
|----------------|------------------------------------------|
| News search    | Bing News Search, Google Custom Search    |
| Summarization  | OpenAI, Anthropic, in-context LLM         |
| TTS            | PlayAI, ElevenLabs, Google TTS            |
| STT            | OpenAI Whisper, AssemblyAI, PlayAI        |
| Stock video    | Pexels API, Pixabay, Shutterstock         |
| Subclip tool   | Video Subclip Automation (FFmpeg API etc.)|
| Video combine  | Video Combine/Concat API                  |
| Merge audio    | Audio/Video Merger/Muxer API              |
| Markdown file  | GitHub API, LLM markdown generator        |

---

## Meta

- Inputs: News topics, headline count, voiceover style settings (optional)
- Outputs: Final video URL, per-section logs, repo markdown summary

---

### To use:  
Give your LLM or automation agent this workflow and access to the required tools/APIs described above.

---
