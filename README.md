# Debate Crew

Welcome to the Debate Crew project, powered by [crewAI](https://crewai.com). This project creates an AI-powered debate system where multiple agents collaborate to conduct structured debates on any given topic. The system features a debater agent that argues both sides of a motion and a judge agent that evaluates the arguments to determine the winner.

## How It Works

The Debate Crew consists of two specialized AI agents:

1. **Debater Agent** - A compelling debater that can argue both for and against any given motion
2. **Judge Agent** - An impartial judge that evaluates the arguments and determines which side is more convincing

The debate process follows a structured format:
1. The debater presents arguments **in favor** of the motion
2. The debater presents arguments **against** the motion  
3. The judge evaluates both arguments and declares a winner

## Installation

Ensure you have Python >=3.10 <3.14 installed on your system. This project uses [UV](https://docs.astral.sh/uv/) for dependency management and package handling.

First, if you haven't already, install uv:

```bash
pip install uv
```

Next, navigate to your project directory and install the dependencies:

```bash
crewai install
```

### Configuration

**Add your API keys to the `.env` file:**
- `OPENAI_API_KEY` - For the debater agent (using GPT-4o-mini)
- `ANTHROPIC_API_KEY` - For the judge agent (using Claude Sonnet 4)

## Running the Project

To start a debate, run this command from the root folder of your project:

```bash
crewai run
```

By default, the system will debate the motion: *"Nametags are needs to be put on things to prevent them from being lost"*

### Customizing the Debate

To change the debate topic, modify the `motion` variable in `src/debate/main.py`:

```python
inputs = {
    'motion': 'Your custom debate motion here',
}
```

## Output

The debate results are saved in the `output/` directory:
- `propose.md` - Arguments in favor of the motion
- `oppose.md` - Arguments against the motion  
- `decide.md` - The judge's decision and reasoning

## Project Structure

```
debate/
├── src/debate/
│   ├── config/
│   │   ├── agents.yaml    # Agent definitions and configurations
│   │   └── tasks.yaml     # Task definitions for the debate process
│   ├── crew.py           # Main crew orchestration logic
│   └── main.py           # Entry point and input configuration
├── output/               # Generated debate results
└── knowledge/            # Additional context and user preferences
```

## Customization

- **Modify Agents**: Edit `src/debate/config/agents.yaml` to change agent roles, goals, or models
- **Modify Tasks**: Edit `src/debate/config/tasks.yaml` to adjust the debate process
- **Add Logic**: Modify `src/debate/crew.py` to add custom tools or specific arguments
- **Change Inputs**: Modify `src/debate/main.py` to add custom debate motions or parameters

## Example Usage

The system can debate any topic you specify. For example:
- "Social media has a positive impact on society"
- "Remote work is more productive than office work"
- "AI will replace most human jobs in the next decade"

Each debate will generate structured arguments and a reasoned decision from an impartial judge.
