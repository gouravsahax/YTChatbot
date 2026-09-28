# YouTube Video Chatbot

A simple, conversational AI chatbot that lets you chat about any YouTube video using its transcript. Powered by **LangGraph**, **Chroma**, and **Groq**.

## Setup

1. **Install requirements:**
   ```bash
   pip install -r requirements.txt
   ```

2. **Configure Environment Variables:**
   Create a `.env` file in the root folder and add your Groq API key:
   ```env
   GROQ_API_KEY=your_groq_api_key_here
   ```

## Usage

Run the script from your project root:
```bash
python YTChatbotLG.py
```

1. **Enter a YouTube video link** when prompted. (e.g., `https://youtu.be/video_id`)
2. **Start chatting!** The bot will use the video's transcript to answer your questions.
3. **Press Ctrl+C** to end the conversation.

## Project Structure

```text
.
├── YTChatbotLG.py        # The main chatbot script
├── .env                  # Your API keys (you need to create this)
└── requirements.txt      # Python dependencies
```

When you run the script, it will also generate:
- `<video_id>.txt`: The downloaded transcript for the video.
- `chroma_db/`: A directory for the Chroma vector database storage.

## How It Works
- **Transcript Extraction**: Downloads the video transcript using `youtube_transcript_api`.
- **Embeddings & Vector Store**: Text is chunked and stored in a local Chroma database using Hugging Face embeddings.
- **LangGraph**: Maintains the conversational memory and guides the AI's response generation.
- **RAG Generation**: The Groq LLM fetches relevant context from the video to answer your questions accurately.
