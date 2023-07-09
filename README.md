# Gpt-Voice-Assistant
An interactive chatbot powered by AI that can listen, respond, and even speak. Engage in dynamic conversations with an AI companion using text and voice, all made possible with cutting-edge technologies like OpenAI and Eleven Labs. Start a dialogue and explore the fascinating world of AI conversation!

## Code Review: Project Functionality

1. **Libraries and Modules**
   - The project imports various libraries and modules such as `sounddevice`, `soundfile`, `numpy`, `openai`, `os`, `requests`, `re`, `colorama`, `datetime`, `base64`, `pydub`, and `dotenv`. These libraries provide functionalities like audio recording and playback, text-to-speech conversion, API communication, color formatting, and more.

2. **Environment Variables**
   - The project uses the `load_dotenv()` function to load environment variables from a file named `.env`. This allows sensitive information like API keys to be securely stored outside of the main code.

3. **Utility Functions**
   - The project defines several utility functions:
     - `open_file(filepath)`: Opens a file and reads its contents. It is used to retrieve the content of specific files in the project.
     - `print_colored(agent, text)`: Prints text with colored formatting. It assigns specific colors to different agents involved in the conversation.
     - `record_and_transcribe(duration, fs)`: Records audio for a specified duration, saves it as a WAV file, and then transcribes the audio content using OpenAI's audio transcription service.

4. **Retrieving API Keys**
   - The project retrieves the API keys needed for external services by accessing the values stored in environment variables. Specifically, it retrieves the API keys for OpenAI from the `openaiapikey2` variable and for Eleven Labs from the `elabapikey` variable.

5. **Conversation Setup**
   - The project sets up the conversation by initializing an empty list called `conversation1`. This list will store the conversation history between the user and the chatbot. Additionally, it reads the content of the file `chatbot1.txt` and assigns it to the variable `chatbot1`, which represents the initial content of the chatbot.

6. **Chat Functionality**
   - The project implements a function called `chatgpt` that interacts with OpenAI's chat model. This function takes parameters like API key, conversation history, chatbot content, user input, and various parameters for the chat model. It uses the OpenAI API to generate a response from the chatbot based on the given inputs.

7. **Text-to-Speech Functionality**
   - The project defines a function called `text_to_speech` that converts text into speech using Eleven Labs' text-to-speech API. This function sends a POST request to the API endpoint with the specified text, voice settings, and API key. If the response is successful (status code 200), the audio content is saved as an MP3 file and played back using the `pydub` library.

8. **Voice ID and Audio Playback**
   - The project sets the variable `voice_id1` with a specific voice identity (AcoYNi79OOiT50tw0ub0) used for the text-to-speech synthesis. Additionally, it imports the necessary modules for audio playback using `pydub` and `pydub.playback`.

9. **Conversation Loop**
   - The project enters an infinite loop that facilitates an ongoing conversation with the chatbot. Within each iteration of the loop, it performs the following steps:
     - Records audio for a specified duration using `sounddevice`.
     - Converts the recorded audio into a WAV file using `soundfile`.
     - Transcribes the audio content by sending the WAV file to OpenAI's audio transcription service.
     - Passes the transcribed message to the `chatgpt` function to get a response from the chatbot.
     - Prints the chatbot's response in colored format using `colorama`.
     - Removes unnecessary information from the response using regular expressions.
     - Converts the processed response to speech using the `text_to_speech` function.
     - Plays back the generated speech using `pydub.playback`.
