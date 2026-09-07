# 📝 The Longform Desk

An autonomous agent that outlines, researches, drafts section by section, and revises for Medium-ready longform content.

## Overview

The Longform Desk is a browser-based AI agent designed to generate high-quality, publication-ready articles through an iterative workflow. The agent handles the entire writing pipeline: outlining, web research, section drafting, full-draft revision, and editor feedback integration.

## Features

- **Autonomous Workflow**: The agent operates independently, deciding its own strategy for research and writing
- **Web Research Integration**: Performs targeted web searches to gather information on demand
- **Section-by-Section Writing**: Builds articles methodically, one section at a time
- **Editor Critique System**: Sends full drafts to an independent editor (gpt-4o-mini) for scoring and feedback
- **Iterative Revision**: Rewrites sections based on editor feedback until quality targets are met
- **Live Preview**: Watch the article come together in real-time on the page
- **Export Options**: Copy or download finished articles as Markdown
- **Step Budget Management**: Operates within configurable step limits with warnings when approaching budget exhaustion

## How It Works

```
1. [Agent] Set outline → Define title, subtitle, planned sections
2. [Agent] Search → Gather information with web searches
3. [Agent] Draft → Write sections based on research
4. [Agent] Review Full Draft → Read entire article into context
5. [Agent] Get Critique → Send to editor for scoring
6. [Agent] Rewrite (if needed) → Improve sections based on feedback
7. [Repeat] Until quality score is met
8. [Agent] Publish → Finalize and deliver article
```

## Getting Started

### Requirements

- OpenAI API key (for gpt-4o or similar model)
- Modern web browser (Chrome, Firefox, Safari, Edge)
- Internet connection for web search functionality

### Usage

1. **Load the HTML file** in your browser
2. **Enter your OpenAI API key** in the password field (sent only to OpenAI, not stored)
3. **Fill the commission slip**:
   - **Article brief**: Topic or concept for the article
   - **Style**: Tone (narrative, analytical, conversational, etc.)
   - **Target reader**: Who is this for?
   - **Target word count**: Approximate length (e.g., 2000)
   - **Minimum editor score**: Quality threshold (0-10)
4. **Optional settings**:
   - Enable/disable web search
   - Choose LLM model (gpt-4o, gpt-4.1)
   - Set step budget (max reasoning steps)
5. **Click "Run agent"** to start the writing process

### Understanding the Interface

**Left panel (Margin Notes)**:
- Real-time trace of agent reasoning
- Shows searches performed, sections written, critiques received
- Color-coded by type: thinking, tools, results, critiques, errors

**Right panel (Article)**:
- Live preview of the article as it's written
- Displays title, byline, and sections
- Copy to clipboard or download Markdown button

## Configuration Options

| Option | Default | Purpose |
|--------|---------|---------|
| Model | gpt-4o | LLM to use for writing (cheaper: gpt-4o-mini) |
| Step budget | 25 | Max reasoning steps before forcing publish |
| Min editor score | 6 | Quality threshold (won't publish below this unless budget exhausted) |
| Use web search | Yes | Allow agent to search the web for research |

## Example Output

The agent produces publication-ready Markdown with:
- Clear hierarchy (h2 for sections, h3 for subsections)
- Readable paragraphs and lists
- Blockquotes for emphasis
- Code blocks where relevant
- Proper formatting for Medium/publishing platforms

## Tips for Best Results

- **Specific briefs**: "The rise of AI in healthcare: opportunities and risks" works better than "AI"
- **Clear audience**: Specify if writing for executives, engineers, general audience, etc.
- **Realistic word counts**: 2000-5000 words gives the agent room to develop ideas
- **Research-heavy topics**: The agent performs best with topics that benefit from web research
- **Quality thresholds**: Set min score to 7+ for publication-ready content

## Cost

Approximate costs per run:
- **Cheap run** (gpt-4o-mini, 10 steps): ~$0.20–0.50
- **Standard run** (gpt-4o, 25 steps): ~$1.00–2.50
- **Thorough run** (gpt-4o, 40 steps): ~$2.00–4.00

*Costs vary by article length, research requirements, and revision iterations.*

## Architecture

**Frontend**: Pure HTML/CSS/JavaScript (no build step required)

**Integrations**:
- OpenAI Chat API (gpt-4o, gpt-4.1, gpt-4o-mini)
- Web search via Perplexity API
- Marked.js for Markdown rendering

**Tool Set** (available to agent):
- `web_search(query)` - Search the web
- `set_outline(title, subtitle, planned_sections)` - Define article structure
- `write_section(heading, markdown)` - Write a new section
- `rewrite_section(section_number, heading, markdown)` - Revise existing section
- `read_full_draft()` - Retrieve entire article for review
- `get_critique()` - Send draft to independent editor
- `publish(title, subtitle, tags)` - Finalize and deliver

## Error Handling

- **Search disabled**: Agent adapts if web search is unavailable
- **API errors**: Clear error messages in the margin notes; agent can retry
- **Budget exhausted**: Forces publication with best draft so far
- **Editor unavailable**: Agent uses its own judgment to continue

## Privacy

- API keys are sent **only** to OpenAI and Perplexity APIs directly from your browser
- No keys are stored or logged
- Keys are cleared on page refresh
- Article content is not retained after the session ends

## Future Enhancements

- [ ] Custom system prompts for specialized writing styles
- [ ] Integration with publication APIs (Medium, Substack, Ghost)
- [ ] Image research and insertion
- [ ] Real-time collaboration with human editors
- [ ] Analytics on rewrite iterations and common feedback patterns

## License

MIT

## Questions?

For issues, feature requests, or feedback, please open an issue on GitHub.
