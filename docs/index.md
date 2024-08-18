# Google Summer of Code 2024

|  |  |
| --- | --- |
| Name | [Raya Chakravarty](https://github.com/Raya679)                            |
| Organisation | [INCF](https://www.incf.org/) |
| Mentor | [Arman Jahanpour](https://github.com/rmanaem) , [Sebastian Urchs](https://github.com/surchs) , [Alyssa Dai](https://github.com/alyssadai) , [Brent McPherson](mailto:bcmcpher@gmail.com) , [Jean-Baptiste Poline](https://github.com/jbpoline)|
| Project | [A natural language interface for querying federated research data ](https://summerofcode.withgoogle.com/programs/2024/projects/W7ATppvz) |
| Link to the project Repository | [Github Repository](https://github.com/neurobagel/query-tool-ai) |

## A natural language interface for querying federated research data 

[Neurobagel](https://www.neurobagel.org/) is a federated data ecosystem that enables researchers and other data users to locate and access research data that must remain at its original institute due to data governance requirements.

Currently, Neurobagel offers a graphical web query interface that interacts with the node APIs on the user's behalf, simplifying the process of formulating complex queries.

This project intends to build a chatbot that utilizes existing large language models (LLMs) to parse text provided by users into precise queries and reliably summarize the results for them. The chatbot should be able to receive and comprehend user prompts in natural language, initiate corresponding API calls using predefined Neurobagel parameters (like minimum age, maximum age, sex, etc.), interpret the results, and communicate that information back to the user. The goal is to choose open tools and models to allow for flexible hosting options.


<div style="text-align: center;">
  <a href="https://github.com/neurobagel/query-tool-ai" style="
    display: inline-block;
    padding: 10px 20px;
    font-size: 16px;
    color: #ffffff;
    background-color: #000000;
    text-decoration: none;
    border-radius: 5px;
  ">Git Repsitory</a>
</div>

## Understanding the codebase
To have a deeper understanding of the codebase visit [here](https://raya679.github.io/gsoc/codebase/).

## Contributions
Below are some of the major pull requests (PRs) that were merged during this period:

- [PR #15: LLM Extractions](https://github.com/neurobagel/query-tool-ai/pull/15)
- [PR #18: Validations](https://github.com/neurobagel/query-tool-ai/pull/18)
- [PR #20: Mapping to Term URLs](https://github.com/neurobagel/query-tool-ai/pull/20)
- [PR #24: Generating API URL](https://github.com/neurobagel/query-tool-ai/pull/24)
- [PR #28: Dockerization of the query-tool-ai code](https://github.com/neurobagel/query-tool-ai/pull/28)
- [PR #31: FastAPI integration](https://github.com/neurobagel/query-tool-ai/pull/31)

## Future Scope 
- **Complete UI Integration:** Moving forward, a key focus will be on fully integrating the user interface (UI) to provide a seamless and intuitive experience for end-users.
- **Updates to the LLM Model:** Continuously updating and refining LLM models to enhance output quality and minimize hallucinations.

## Conclusion

My GSoC experience has been incredibly rewarding and educational, significantly contributing to my future aspirations. I am deeply thankful to my mentors **Arman Jahanpour**, **Sebastian Urchs**, **Alyssa Dai**, **Brent McPherson**, **Jean-Baptiste Poline**, [INCF](https://www.incf.org/) and [Neurobagel](https://neurobagel.org/) for their unwavering guidance and support throughout the project. Their expertise and readiness to assist whenever needed have been invaluable. I also extend my gratitude to **Google** for offering such a fantastic opportunity to student developers worldwide.

I hope to continue collaborating with Neurobagel and INCF in the future and contribute further to its impactful projects.


                         