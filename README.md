This project is a language assistant for travellers, enabling users to generate useful phrases in a selected language based on their travel needs. Users can input text, record audio, and select their destination country to receive tailored travel phrases.
It is inspired on: 

---
### Main features

- **Multi-modal Input:** Accepts both text and audio inputs for tasks such as ordering food, asking for directions, and more.

- **Language-Specific Responses:** Generates phrases in the language of the selected destination country.

- **Few-shot Learning:** Utilizes example-based learning to produce context-specific responses.

- **Speech-to-Text Integration:** Transcribes audio inputs using OpenAI's Whisper model.

- **Local open-source LLM:** It uses a local LLM (mistral-nemo) served using Ollama.

- **User-Friendly Interface:** Built with Gradio for an interactive and easy-to-use experience.

---
## Technical features

There are some interesting features that i want to highlight here.

1. **Multimodal input support**
The application allows users to input commands via **text** or **audio**. Audio inputs are processed using **OpenAI Whisper**, a robust speech-to-text model for transcribing audio into actionable text. The below image is presented in their github repository \[1]:

![AI Travel Assistant Whisper model](https://i.imgur.com/pOXeNu3.png)

2.  **Language Model Integration**

Powered by **LangChain Ollama LLM** \[2], this application uses the **Mistral-Nemo** \[3] model to provide contextually relevant and language-specific responses.

<ins>Why did i choose this model?</ins>

- **State-of-the-Art Performance**: Mistral-Nemo is a cutting-edge language model designed for high-quality natural language understanding and generation. It excels at tasks requiring contextual comprehension, such as summarization, translation, and conversational AI.

- **Compact and Efficient**: This model is optimized for performance and efficiency, offering powerful capabilities without the heavy resource demands of larger models. This makes it ideal for applications requiring fast response times, even on limited hardware.

- **Multilingual Support**: Mistral-Nemo demonstrates exceptional few-shot and zero-shot learning abilities, allowing it to generate high-quality responses with minimal examples. This aligns perfectly with the use of a small dataset (e.g., fewshot_learning.txt) to guide the model.

- **Few-Shot and Zero-Shot Capabilities**: Mistral-Nemo demonstrates exceptional few-shot and zero-shot learning abilities, allowing it to generate high-quality responses with minimal examples.

- **Seamless Integration with LangChain**: It integrates smoothly with the LangChain framework, making it easier to incorporate into modular applications like this one. This reduces development complexity and accelerates implementation.

3. **Language-Specific Context**

The application references a **JSON file (**utils/country_to_language.json**)** to map countries to their corresponding languages. This ensures accurate language-specific responses for popular destinations such as France, Germany, Italy, and Spain.

Users receive responses in the selected destination’s native language, making communication more authentic and effective. For example, if a user selects Germany, the application generates outputs in German.

<ins>Adding more countries or languages is as simple as updating the JSON file, allowing the application to scale easily.</ins>

4. **In-context learning**

The system incorporates **few-shot learning** by referencing example queries stored in utils/fewshot_learning.txt. These examples guide the model on how to respond effectively.

By combining these examples with the user’s query, the system generates highly relevant and accurate outputs. Also, developers can add more examples to the file to improve model performance or adapt the system for specific regions or user groups.

5. **Gradio Interface for User Interaction**

I used Gradio library \[4] to make a clean and usable UI that make possible to users understand and interact with the app effortlessly. Look at how application looks like below:

![AI Travel Assistant applook](https://i.imgur.com/a7Rtvts.png)

---

## Examples

Let me share with you some examples on how it works.

**Note:** This is not just a translation system, it creates multiple ways to say something and related things on the same context. Then, you can choose what you think it suits you the best.

1. How can i ask where is the closest train station on Italy?

![AI Travel Assistant ask train italy](https://i.imgur.com/7eLR97W.png)

2. How to ask about the best restaurant to have dinner on the city (Spain)?

![AI Travel Assistant restaurant spain](https://i.imgur.com/QKT5rmG.png)

3. How to know what is the equivalent to "thank you" and how to proper compliment someone (France)?
 
![AI Travel Assistant compliment example](https://i.imgur.com/CJgjAud.png)

<ins>Audio examples works the same but instead of write the input, you talk to the selected microphone.</ins>

---

# Future directions

- **Expanding Language and Country Support**: Incorporate additional languages and countries by enhancing the utils/country_to_language.json file. This will broaden the application’s reach, making it more inclusive for travelers visiting diverse destinations. Introduce dialect support (e.g., Swiss German or Canadian French) to cater to regional variations in language usage.

- **Enhanced Speech Recognition**: Upgrade the **audio transcription** system by integrating Whisper’s larger, more accurate models or exploring alternative speech-to-text systems. 

- **Context-Aware Conversations**: Develop a **session memory** mechanism to allow the assistant to retain information about the user’s preferences and previously asked queries. For example, remembering dietary restrictions when learning food-related phrases. A whole chatbot with a "normal" conversation would be a very good and interesting improvment.

- **Personalized Recommendations**: Integrate a recommendation system that suggests **sentences adapted to user-specific needs**, such as business travelers, solo adventurers, or families with children. Allow users to save or bookmark frequently used phrases for quick reference during their trips.

- **A lot more can be done:** Improvments can be done on AI model, integration with travel ecosystems, exploration of gamifications functionalities, broader task coverage, and much more.

---
# References

\[1]: [https://github.com/openai/whisper](https://github.com/openai/whisper)

\[2]: [https://python.langchain.com/docs/integrations/llms/ollama/](https://python.langchain.com/docs/integrations/llms/ollama/)

\[3]: [https://mistral.ai/news/mistral-nemo/](https://mistral.ai/news/mistral-nemo/)

\[4]: [https://www.gradio.app/](https://www.gradio.app/) 

