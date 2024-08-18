# Model selection

In the process of extracting the information from user queries, several LLMs were tested and evaluated. The goal was to identify a model that could accurately extract all necessary parameters without introducing hallucinations or errors. 

Below is a summary of the models tested and their performance in this context.

## [google/flan-t5-xxl](https://huggingface.co/google/flan-t5-xxl)

The `google/flan-t5-xxl model`, a large-scale Transformer model fine-tuned on various NLP tasks, was one of the initial models tested for extracting parameters from user queries. Known for its versatility in handling complex language tasks, this model was integrated into the project using the `Hugging Face Hub`. 

**Performance overview** 

 1. **Extracting all parameters together** 

    prompt: How many female subjects older than 50 with a Parkinson’s diagnosis?

    ![image](https://github.com/Raya679/Healthcare-Chatbot/assets/113240231/e7ae683f-60f9-4696-b91e-d979f6a9d85e)

    **Issue** - While the model performed well in terms of fluency and coherence, it exhibited a significant flaw: it introduced assumptions not present in the original query. For example, it added values like `imaging_sessions` and `phenotypic_sessions`, which were not mentioned by the user.
 
 2. **Extracting values one by one**

    To address the issue of assumptions, a strategy was employed where each parameter was extracted individually using separate scripts:
  
    - extract_age.py 
      ![image](https://github.com/Raya679/Healthcare-Chatbot/assets/113240231/a6fd1306-3889-4a6a-99d3-760e54eae5b9)
    - extract_sex.py
      ![image](https://github.com/Raya679/Healthcare-Chatbot/assets/113240231/3aff87fd-f6a1-4a7e-b2be-0f3448ebd950)
    - extract_sessions
       ![image](https://github.com/Raya679/Healthcare-Chatbot/assets/113240231/a0505380-eeeb-4cfe-8442-93462a63d078)

    **Issue**: While this approach reduced the likelihood of hallucinations, it introduced other challenges. The `google/flan-t5-xxl model` has a rate limit when accessed via the Hugging Face Hub, which constrained the speed and scalability of this approach. 
    Additionally, the model struggled with categorical values such as `diagnosis`, `assessment tool`, `health-control`, and `image-modality`, where its accuracy was inconsistent.
     
## [llama-2](https://ollama.com/library/llama2:chat) 
`Llama-2` is an advanced language model known for its large size and ability to handle complex language tasks. Despite these capabilities, its performance in this specific context was found to be lacking in accuracy. The model was integrated using the `ChatOllama` framework, and its performance was evaluated on the task of extracting structured information from user queries.

**Performance overview** 

Despite the high expectations due to its size and architecture, Llama-2 struggled to deliver accurate results for this task. The model often provided outputs that were either incomplete or contained errors, particularly when extracting detailed parameters from complex queries

   **Example of LLM Response -**  
     ![image](https://github.com/Raya679/Healthcare-Chatbot/assets/113240231/2026f9fe-2de6-4381-b944-ea9d3447b97f)

   **Issue**: The model failed to accurately extract some of the key elements of the query, leading to incorrect or incomplete responses. This lack of precision made it unsuitable for the specific needs of this project, where accuracy in parameter extraction is crucial.
     
## [gemma](https://ollama.com/library/gemma) 
The `gemma` model is a large language model designed for natural language processing tasks. It aims to improve upon previous models like `llama-2` by offering enhanced performance in tasks such as text generation, information extraction, and question answering.The model was implemented using the `ChatOllama` framework and tested on queries requiring the extraction of structured data.

**Performance overview** 

Compared to `llama-2`, `gemma` demonstrated better accuracy in extracting information from user queries. However, it still struggled with hallucinations, where the model would generate information not present in the original query or misinterpret the provided data. 

  **Example of LLM Response -** 
    ![image](https://github.com/Raya679/Healthcare-Chatbot/assets/113240231/9ea0108e-7103-4c00-a963-9eb4c49b8d37)
    ![image](https://github.com/Raya679/Healthcare-Chatbot/assets/113240231/f8bea6d3-8f26-43a5-93ed-03cc63b5855a)
    ![image](https://github.com/Raya679/Healthcare-Chatbot/assets/113240231/1f31e7b0-8492-4aef-ab6a-fa3153a877f9)
    ![image](https://github.com/Raya679/Healthcare-Chatbot/assets/113240231/dc8de042-29f9-4d6d-a71b-9b1580be63b4)
    ![image](https://github.com/Raya679/Healthcare-Chatbot/assets/113240231/07d8f0be-5ec7-439e-8ac5-8337ddda5400)
    
   **Issue**: While the `gemma` LLM showed improvements over `llama-2` in extracting relevant information, it still struggled with hallucinations. The model occasionally generated incorrect or irrelevant details that were not part of the original query. These hallucinations, though less frequent, could lead to misleading or inaccurate outputs, especially in cases requiring precise categorical information like diagnosis, assessment tools, or imaging modalities.

Despite its better performance in some areas, the inconsistency in handling specific queries made it unreliable for scenarios where accuracy is critical.

## [mistral](https://ollama.com/library/mistral)

The` mistral` LLM is a state-of-the-art language model developed by Ollama, known for its impressive capabilities in natural language understanding and generation. It is designed to handle a wide range of language tasks, including text generation, comprehension, and contextual understanding.The model was implemented using the `ChatOllama` framework and tested on queries requiring the extraction of structured data.
    
**Performance overview** 

   - `mistral` excelled in accurately extracting parameters like age, sex, and diagnosis from user queries, making it ideal for detailed information extraction.
   - It showed fewer hallucinations compared to models like `llama-2` and `gemma`, providing more reliable outputs by avoiding the generation of irrelevant data
   - `mistral` effectively integrated with structured data models like Pydantic, allowing for seamless mapping of extracted information to predefined schemas.

    
    
  **Examples of LLM Response** -
    ![image](https://github.com/Raya679/Healthcare-Chatbot/assets/113240231/5be2f93a-16cc-4759-a830-83f79fc28d44)


## Open-source vs closed source models

### Open-Source Models
Open-source models, such as `mistral`, offer the advantage of accessibility and customization, allowing users to modify and integrate them into various applications. These models provide significant benefits in terms of transparency and flexibility. However, they are not without limitations.

In the case of `mistral`, an open-source model, there were notable issues with handling certain parameter extractions. For instance, it occasionally struggled with identifying and interpreting vague age ranges such as "above 40" or "below 60." 

### Closed-Source Models
Closed-source models, while less customizable, often come with robust support and fine-tuning specific to accuracy and performance. They are typically developed with extensive resources and advanced techniques that address various limitations seen in open-source alternatives.

To address the challenges experienced with open-source models, experimentation was extended to closed-source options such as `openai/chatgpt-4o-latest`. This model demonstrated superior performance in extracting information with almost no hallucinations. It effectively handled ambiguous queries and accurately interpreted parameters like age ranges, providing reliable and precise outputs.

### Examples
- Examples of `mistral` unable to identify context of age.
![Screenshot from 2024-08-16 11-03-02](https://github.com/user-attachments/assets/37dca154-13f2-4249-b4ba-6953cb28debc)

- Examples of `openai/chatgpt-4o-latest` giving accurate answers to the same questions.
![Screenshot from 2024-08-16 10-59-53](https://github.com/user-attachments/assets/c87b743f-82b6-41ff-a534-6b0100b15cf1)

## Summary
While open-source models like `mistral` offer valuable benefits, they can exhibit limitations such as handling specific parameter nuances. Closed-source models, such as `openai/chatgpt-4o-latest`, often provide enhanced accuracy and reliability, making them a preferable choice for applications where precision is critical.