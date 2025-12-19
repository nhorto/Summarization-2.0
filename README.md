# Weekly Consulting Summary Automation

Automated pipeline for generating professional weekly consulting summary reports from daily transcript files.

## Overview

This tool converts daily `.srt` transcript files from consulting sessions into a professionally formatted Word document summary report, matching the style and quality of your gold standard reports.

## Pipeline

```
Daily .srt files → Daily summaries → Master weekly summary → Word document
```

## Features

### Enhanced Over V2
- ✅ **Improved Prompts**: Better narrative flow and professional consultant tone
- ✅ **Word Document Output**: Automatic `.docx` generation with proper formatting
- ✅ **Opening Paragraph**: Auto-generated thank you and week focus
- ✅ **Closing Paragraph**: Auto-generated summary and availability statement
- ✅ **Better Organization**: Topic-based sections matching gold standard structure
- ✅ **Anti-Hallucination**: Strict safeguards against invented content

### Preserved From V2
- ✅ **Chunking Strategy**: Handles long transcripts with overlap
- ✅ **Topic Organization**: Functional consulting areas (Estimating, Project Management, etc.)
- ✅ **Critical Instructions**: No hallucinations, no assumptions, factual accuracy only

## Directory Structure

```
consulting-summary-automation/
├── transcripts/           # Place your .srt or .txt files here
├── summaries_daily/       # Daily summaries (generated)
├── summaries_master/      # Weekly master summaries (generated)
├── output/                # Final Word documents (generated)
├── summarize_enhanced.py  # Main script
├── requirements.txt       # Python dependencies
├── .env                   # Your API configuration (create from .env.example)
└── README.md             # This file
```

## Setup

### 1. Install Dependencies

```bash
cd ~/Documents/consulting-summary-automation
pip install -r requirements.txt
```

Or using `uv` (PAI preference):

```bash
uv pip install -r requirements.txt
```

### 2. Configure API Key

Copy the example environment file and add your OpenAI API key:

```bash
cp .env.example .env
# Edit .env and add your OPENAI_API_KEY
```

### 3. Add Transcript Files

Place your `.srt` or `.txt` transcript files in the `transcripts/` folder.

## Usage

### Run Manually

```bash
python summarize_enhanced.py
```

### Run via PAI Skill

Once the PAI skill is installed (see below), you can use:

```
/WeeklySummary
```

Or just mention it in conversation:
```
"Generate my weekly consulting summary"
```

## Output

The script generates:

1. **Daily Summaries** (`summaries_daily/`): One summary per transcript file
2. **Master Summary** (`summaries_master/`): Combined weekly summary (plain text)
3. **Word Document** (`output/`): Professionally formatted `.docx` file with:
   - Date header
   - Opening paragraph (thank you + week focus)
   - Topic-based sections with formatted headers and bullets
   - Closing paragraph (summary + availability)
   - Signature line

## Key Improvements

### Enhanced Prompts

**Daily Summaries:**
- Better topic organization matching consulting report style
- Clearer instructions for narrative bullet points
- Professional past-tense writing

**Master Summary:**
- Improved consolidation and de-duplication
- Better subsection organization
- Natural weaving of what was covered, found, accomplished, and next steps

**Opening/Closing:**
- Dedicated prompts for professional intro and conclusion
- Context-aware based on report content
- Warm, appreciative, supportive tone

### Word Document Formatting

- Date at top
- Proper heading hierarchy
- Formatted bullet points with indentation
- Professional spacing and layout
- Calibri font, 11pt (standard business document)

## Anti-Hallucination Safeguards

Every LLM prompt includes critical instructions:
- ✅ Only use information explicitly stated in source material
- ✅ No assumptions, guesses, or unsupported conclusions
- ✅ No invented details, recommendations, or action items
- ✅ Strict factual accuracy requirement

## Model Configuration

Default model: `gpt-4o-mini` (fast and cost-effective)

To use a different model, edit `.env`:
```
OPENAI_MODEL_NAME=gpt-4o
```

Options:
- `gpt-4o-mini` - Fast, cost-effective (default)
- `gpt-4o` - More capable, higher quality
- `gpt-4-turbo` - Good balance

## Troubleshooting

### No summaries generated
- Check that `.srt` or `.txt` files exist in `transcripts/`
- Verify `OPENAI_API_KEY` is set correctly in `.env`

### Poor quality output
- Try using a more capable model (`gpt-4o` instead of `gpt-4o-mini`)
- Check that transcript files contain substantive content
- Ensure transcripts are reasonably clean (not too many errors)

### Word document formatting issues
- Ensure `python-docx` is installed: `pip install python-docx`
- Check for special characters or formatting in the generated text

## PAI Integration

This project includes a PAI skill for easy workflow automation. See the skill documentation for details.

## Future Enhancements (Phase 3)

Potential future improvements:
- TypeScript CLI rewrite (full PAI stack alignment)
- Claude API integration (better reasoning)
- Custom output templates
- Batch processing for multiple weeks
- Integration with cloud storage (Dropbox, Google Drive, etc.)

## Support

For questions or issues, contact the PAI administrator or refer to the original implementation at:
`/Users/nicholashorton/Documents/LLM Sumarization/`

---

**Version:** 3.0 (Enhanced)
**Last Updated:** December 2025
