# chatGPT-voice-assistant
Speak to ChatGPT and have it speak back.

When run microphone audio is passed to a speech-to-text engine for transcription, which is then passed to ChatGPT, who's response is spoken using a text-to-speech engine.

# Technologies
Google Cloud, text to Speech

Whisper, speech to text

Gradio, user interface

revChatGPT, ChatGPT authentication

VLC, audio playback (Windows)

# Google Cloud Authentication
To use Google's voice-to-speech service you'll need to generate a service key. Start a new project, open up the cloud shell, and use the following commands:

```
xxxxx@cloudshell:~ (taskertalk-357107)$ history
    1  gcloud auth list
    2  gcloud config list project
    3  gcloud services enable texttospeech.googleapis.com
    4  export PROJECT_ID=$(gcloud config get-value core/project)
    5  gcloud iam service-accounts create my-tts-sa   --display-name "my tts service account"
    6  gcloud projects add-iam-policy-binding ${PROJECT_ID}   --member serviceAccount:my-tts-sa@${PROJECT_ID}.iam.gserviceaccount.com   --role roles/serviceusage.serviceUsageConsumer
    7  gcloud iam service-accounts keys create ~/key.json   --iam-account my-tts-sa@${PROJECT_ID}.iam.gserviceaccount.com
    8  export GOOGLE_APPLICATION_CREDENTIALS=~/key.json
    9  ls
   10  cat key.json
   11  history
xxxxx@cloudshell:~ (taskertalk-357107)$ ^C
```

# Sources
Most of this code base is the work of [bhattbhavesh91](https://github.com/bhattbhavesh91/voice-assistant-whisper-chatgpt/blob/main/OpenAI-Whisper-ChatGPT-Notebook.ipynb). I combined their work with example code found in both the [OpenAiAuth](https://github.com/acheong08/OpenAIAuth) and GoogleCloud docs with minor modifications.
