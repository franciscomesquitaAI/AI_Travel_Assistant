# Assistant for Travelers

This project is a language assistant for travelers, enabling users to generate useful phrases in a selected language based on their travel needs. Users can input text, record audio, and select their destination country to receive tailored travel phrases.

---

## Features

- **Multi-modal Input:** Accepts both text and audio inputs for tasks such as ordering food, asking for directions, and more.
- **Language-Specific Responses:** Generates phrases in the language of the selected destination country.
- **Few-shot Learning:** Utilizes example-based learning to produce context-specific responses.
- **Speech-to-Text Integration:** Transcribes audio inputs using OpenAI's Whisper model.
- **User-Friendly Interface:** Built with Gradio for an interactive and easy-to-use experience.

---

## Installation

### Prerequisites

1. **Install FFmpeg**  
   FFmpeg is required for audio processing. Install it using one of the following methods:

   - macOS:  
     ```bash
     brew install ffmpeg
     ```
   - Conda:  
     ```bash
     conda install -c conda-forge ffmpeg
     ```

2. **Clone the Repository**  
   Clone the GitHub repository to your local machine:
   ```bash
   git clone https://github.com/<your-username>/<repo-name>.git
   cd <repo-name>
   ```

3.	Install Dependencies
Install the required Python libraries using pip:

```bash
pip install langchain_community
pip install gradio
pip install git+https://github.com/openai/whisper.git
pip install whisper
```

---

## Usage

**Launch the Application**

Run the application using the following command:

```bash
python <script_name>.py
```

The application will launch locally at:

```bash
http://127.0.0.1:7860
```

To create a public link, you can set the share=True parameter in the demo.launch() method:

```python
demo.launch(share=True, debug=True)
```

**Steps to Use**
	1.	Enter your task as text (e.g., “order food”) or record your voice.
	2.	Select your destination country (France, Germany, Italy, or Spain).
	3.	Adjust the slider to specify how many phrases you need.
	4.	Click Generate Response to view the translated phrases.

---

## Key Functions

**Language Retrieval**

Retrieves the target language for the selected country from the JSON file utils/country_to_language.json.

```python
def get_language(country, file):
    with open(file, 'r') as f:
        data = json.load(f)
    return data[country]
```

**Few-shot Learning**

Loads example phrases from utils/fewshot_learning.txt to enhance contextual learning.

```python
def get_examples(file):
    with open(file, 'r') as f:
        data = f.read()
    return data
```

**Audio Transcription**

Transcribes audio inputs into text using the Whisper model for further processing.

```python
def transcribe_audio(audio_file):
    model = whisper.load_model("base")
    audio = whisper.load_audio(audio_file, sr=16000)
    audio_tensor = torch.from_numpy(audio).to(torch.float32)
    result = model.transcribe(audio_tensor, fp16=False)['text']
    return result
```

---

## Development Environment

•	Python Version: 3.12
•	Frameworks: Gradio, Langchain
•	Model: OpenAI Whisper
•	Environment: Conda Travel_assistance

Check if FFmpeg is installed correctly:

```python
import shutil
print(shutil.which("ffmpeg"))
```

Expected output (path to your FFmpeg installation): /opt/anaconda3/envs/Travel_assistance/bin/ffmpeg

If FFmpeg is missing, install it as per the Installation section.

---

Future Enhancements
	•	Add support for more countries and languages.
	•	Enhance audio transcription options for higher accuracy.
	•	Integrate translation APIs for expanded language support.
	•	Enable cloud sharing for collaborative travel planning.

---

License

This project is licensed under the MIT License.
