# Quick Start Guide

Get your weekly consulting summary automation running in 5 minutes.

## Initial Setup (One-Time)

### 1. Install Dependencies

```bash
cd ~/Documents/consulting-summary-automation
pip install -r requirements.txt
```

Or using `uv`:
```bash
uv pip install -r requirements.txt
```

### 2. Configure API Key

```bash
# Copy example config
cp .env.example .env

# Edit .env and add your OpenAI API key
# OPENAI_API_KEY=sk-...
```

**Get your API key:** https://platform.openai.com/api-keys

## Weekly Usage

### 1. Add Transcript Files

Place your `.srt` or `.txt` files in the `transcripts/` folder:

```bash
# Example: Copy this week's recordings
cp ~/path/to/recordings/*.srt ~/Documents/consulting-summary-automation/transcripts/
```

### 2. Run Summarization

```bash
cd ~/Documents/consulting-summary-automation
python summarize_enhanced.py
```

### 3. Get Your Report

Find the Word document in the `output/` folder:

```bash
open output/
```

The file will be named: `Weekly_Consulting_Summary_YYYYMMDD_HHMMSS.docx`

## Using PAI Skill

If you prefer to use the PAI skill:

```
"Generate my weekly consulting summary"
```

Or use the skill name:
```
/WeeklySummary
```

## Cleanup (Optional)

After generating your report, you can clean up the intermediate files:

```bash
# Clear transcripts (after backing them up elsewhere)
rm transcripts/*.srt

# Clear daily summaries (optional - these are intermediate files)
rm summaries_daily/*.txt

# Keep output/ files - these are your final reports
```

## Troubleshooting

### "No transcript files found"
→ Make sure `.srt` or `.txt` files are in `transcripts/` folder

### "OPENAI_API_KEY is not set"
→ Create `.env` file from `.env.example` and add your API key

### "ModuleNotFoundError"
→ Run `pip install -r requirements.txt`

### Poor quality output
→ Try using `gpt-4o` model in `.env`:
```
OPENAI_MODEL_NAME=gpt-4o
```

## Model Options

Edit `.env` to change the model:

| Model | Speed | Quality | Cost |
|-------|-------|---------|------|
| `gpt-4o-mini` | ⚡⚡⚡ Fast | Good | $ |
| `gpt-4o` | ⚡⚡ Moderate | Excellent | $$ |
| `gpt-4-turbo` | ⚡ Slower | Great | $$$ |

**Recommendation:** Start with `gpt-4o-mini` (default). If quality isn't good enough, upgrade to `gpt-4o`.

## Next Steps

- Read the full [README.md](README.md) for detailed information
- Check the [PAI Skill documentation](/Users/nicholashorton/PAI/.claude/skills/WeeklySummary/SKILL.md)
- Review your first output and adjust model if needed

---

**Need help?** Check the main README.md or contact PAI administrator.
