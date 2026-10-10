<p align="center">
  <img src=".github/banner.png" alt="UNICorn – a hand-drawn banner: an old laptop showing a chat, a speech bubble rising from it, a stack of university brochures" width="100%">
</p>

# AI-Conversational-Engine (UNICorn)

An early chatbot for the University of Nicosia, built in 2023 on the GPT-3 completion API. It answered questions about the university – programmes, contacts, campus life – by first searching its own embedded texts (the university website and transcribed conversations) and only then asking the model to write the reply. It could also take voice: recordings were transcribed and summarised before they reached the chat.

Mostly, it was a lesson in what language models could and couldn't do yet.

<p align="center">
  <img src="./diagram.svg" width="500px" alt="Diagram of the repository's modules">
</p>

## What's inside

| Path | What it does |
| --- | --- |
| `src/ai/embedding_generator.py`, `semantic_query_processor.py` | Embed the website pages and conversation transcripts once; find the passages closest to a question |
| `src/ai/gpt_chatbot.py`, `model_manager.py` | Build the prompt from those passages and get a completion |
| `src/ai/audio_preprocessor.py`, `transcript_analyzer.py`, `key_takeaways_extractor.py` | Turn a recording into a transcript, then into its key points |
| `src/scripts/long_audio_transcriber.py` | Transcribe a long recording, then clean the transcript up in 2,000-character chunks |
| `src/scripts/token_price_calculator.py` | Estimate what a conversation costs before running it |
| `src/web_chatbot/` | A small web chat: a Node server and an HTML/JS client in front of the Python model |
| `src/cli_chatbot/` | The same assistant in a terminal |

## Screenshots

The web version and the terminal version:

![Web version](https://github.com/HlexNC/UNIC_ChatBot/assets/66517969/e19f7eab-82c5-49bc-a124-61e25494918e)
![Terminal version](https://github.com/HlexNC/UNIC_ChatBot/assets/66517969/ce219d19-cb28-46a0-acfd-5b09245ee3dc)

## Running it

It needs two things this repository doesn't include: a `.env` file with an OpenAI API key, and the `data/` folder of embedded texts (`*_embedding.jsonl`) the search runs over. With both in place, install `requirements.txt`, then start either the web chat (`src/web_chatbot/`) or the terminal chat (`src/cli_chatbot/bash_chatbot.py`).

The GPT-3 completion models it was written for have since been retired, so running it today means pointing `model_manager.py` at a current chat model.

## Status

Archived as a 2023 project. You're welcome to fork it or reuse the code; I'd be glad to hear what for.

## License

[MIT](LICENSE)
