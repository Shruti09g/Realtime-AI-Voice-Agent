# Speech Assistant with Twilio Voice and OpenAI Realtime API

This application demonstrates how to integrate **Twilio Voice**, **Twilio Media Streams**, and **OpenAI's Realtime API** using Python to create an AI-powered speech assistant. The assistant facilitates a two-way voice conversation by transferring audio between Twilio and OpenAI via WebSockets.

For a full tutorial, visit [Twilio's guide](https://www.twilio.com/en-us/voice-ai-assistant-openai-realtime-api-python).

## Prerequisites

You need the following:

- **Python 3.9+**  
  Install from [python.org](https://www.python.org/downloads/). Development tested on version `3.9.13`.

- **Twilio Account**  
  [Sign up for free](https://www.twilio.com/try-twilio).

- **Twilio Phone Number with Voice Capabilities**  
  Follow [these instructions](https://help.twilio.com/articles/223135247-How-to-Search-for-and-Buy-a-Twilio-Phone-Number-from-Console).

- **OpenAI Account and API Key**  
  Sign up at [OpenAI](https://platform.openai.com/).

- **OpenAI Realtime API Access**  
  Request access to the Realtime API.

## Setup Instructions

Follow these steps to set up and run the app locally.

### Step 1: Install ngrok and Expose a Local Server

1. Download **ngrok** from [here](https://ngrok.com/).
2. Start a tunnel on port `5050`:

   ```bash
   ngrok http 5050
   ```

3. Copy the `Forwarding` URL from the output (e.g., `https://[your-ngrok-subdomain].ngrok.app`). You’ll need this for the Twilio setup.

> **Note:** If you change the server port in `main.py`, update the ngrok command accordingly.

### Step 2: (Optional) Use a Virtual Environment

Set up a virtual environment to avoid cluttering the global Python environment:

```bash
python3 -m venv env
source env/bin/activate
```

### Step 3: Install Dependencies

Install the required packages:

```bash
pip install -r requirements.txt
```

### Step 4: Configure Twilio

#### Update Phone Number Settings

1. Go to **Phone Numbers** > **Manage** > **Active Numbers** in the [Twilio Console](https://console.twilio.com/).
2. Select the phone number you purchased for this app.
3. Update the **A Call Comes In** setting to **Webhook** and enter the ngrok URL followed by `/incoming-call`. Example:

   ```
   https://[your-ngrok-subdomain].ngrok.app/incoming-call
   ```

4. Save the configuration.

### Step 5: Set Up the Environment File

1. Create an `.env` file in the project directory:

   ```bash
   cp .env.example .env
   ```

2. Open `.env` and add your OpenAI API key:

   ```env
   OPENAI_API_KEY=your_openai_api_key_here
   ```

## Running the Application

1. Start the development server:

   ```bash
   python main.py
   ```

2. Keep the ngrok tunnel running in a separate terminal.

## Testing the Application

1. Call the Twilio phone number you configured.
2. Follow the introduction and start speaking to the AI Assistant.
3. Enjoy your conversation!
