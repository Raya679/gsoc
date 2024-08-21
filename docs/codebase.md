# Details of the codebase

## Overview 

The code is divided into three main parts:

  - [Extracting Information](#extracting-information): This part focuses on extracting the necessary details from the user's natural language query and converting them into a JSON format.

  - [Mapping to TermURLs](#mapping-to-term-urls): Here, the extracted information is converted into corresponding termURLs, if needed.

  - [Generating the API URL](#generating-the-api-url): Finally, this section creates the final API URL that needs to be called, using the processed information.

The project's workflow process was as follows:
![image](https://github.com/user-attachments/assets/a3ab306d-b09b-448d-9749-0b0a024dde97)


## Extracting Information 

This code defines a Python script that extracts specific information from user queries using a natural language processing model. Here's a brief description of its functionality:

- Parameters Model: 

    - The script defines a `Parameters` class using Pydantic, which outlines the expected fields for the extracted information, such as age limits, sex, diagnosis, control status, and others.

- Information Extraction Function:

    - The `extract_information` function utilizes the LangChain library and large language models to process the user's natural language query.
    - A prompt template and a JSON output parser are used to extract and format the required information according to the Parameters model.
    - The function includes a retry mechanism to handle failures, ensuring the robustness of the extraction process.

- Model Selection:

     - The choice of the LLM model was critical to the success of the information extraction component. Initially, extensive experimentation was conducted with various open-source ChatOllama models like `llama`, `gemma` and `mistral`. Among these, the `mistral` model was chosen as it provided the best results in extracting the necessary information.
     - However, even with `mistral`, some hallucinations were observed, which required careful handling and validation to ensure accurate outputs.
     - Later, experimentation was extended to include closed source models like `openai/chatgpt-4o-latest`. This model demonstrated significantly better results, with almost no hallucinations, making it a superior choice for ensuring the accuracy and reliability of the extracted information.

     To understand the model selection process in detail visit [here](https://raya679.github.io/gsoc/models/).




## Mapping to Term URLs

- Functionality:

    - Functions are defined to retrieve TermURL values based on specific input labels, such as diagnosis, assessment, sex, and image modality.
    - For each type of input, the corresponding TermURL is fetched by searching through predefined mappings and abbreviations.

- Mappings:

    - The mappings are stored in predefined dictionaries or other structures, enabling quick lookup and conversion of extracted terms into their corresponding TermURLs.


## Generating the API URL
This component constructs the final API URL using the processed information:

- Extract Information:

     - It starts by using the extract_information function to process the user query and extract relevant parameters.

- Validation:

    - The extracted information undergoes validation, particularly for age-related data and diagnosis/control status. Adjustments are made as necessary to ensure the validity of the data.

- URL Mapping:

    - The extracted terms (such as sex, diagnosis, assessment, and image modality) are converted into their corresponding TermURLs using the predefined mapping functions.

- Parameter Construction:

    - Query parameters are constructed from the extracted information. If any terms are unsupported, they are added to a list for further handling.

- Construct API URL:

    - The base API URL is combined with the constructed parameters to form the full API URL. If unsupported terms are found, the function returns an error message instead of the URL.


## Dockerization and FastAPI Integration

As the Neurobagel query tool AI was a standalone tool,the next phase was to integrate an API and containerize the tool. 
I set up the API entrypoint using FastAPI, and since the extraction of infromation from the user query is handled by Ollama's LLMs, I built upon the Docker image provided by Ollama to extend its functionality.


Additionally, I created detailed documentation covering various setup options for the tool, including both local and Dockerized versions. The documentation includes instructions for accessing the tool through  command-line guidance for server configurations.






