# Google Summer of Code 2024

<table style="font-size:0.95em; width:100%; border:none;">
    <tr>
        <td style="width:30%;"><strong>Name</strong></td>
        <td><a href="https://github.com/Raya679">Raya Chakravarty</a></td>
    </tr>
    <tr>
        <td><strong>Organisation</strong></td>
        <td><a href="https://www.incf.org/">INCF</a></td>
    </tr>
    <tr>
        <td><strong>Mentors</strong></td>
        <td>
            <a href="https://github.com/rmanaem">Arman Jahanpour</a>, 
            <a href="https://github.com/surchs">Sebastian Urchs</a>, 
            <a href="https://github.com/alyssadai">Alyssa Dai</a>, 
            <a href="mailto:bcmcpher@gmail.com">Brent McPherson</a>, 
            <a href="https://github.com/jbpoline">Jean-Baptiste Poline</a>
        </td>
    </tr>
    <tr>
        <td><strong>Project</strong></td>
        <td><a href="https://summerofcode.withgoogle.com/programs/2024/projects/W7ATppvz">A natural language interface for querying federated research data</a></td>
    </tr>
    <tr>
        <td><strong>Link to the project repository</strong></td>
        <td><a href="https://github.com/neurobagel/query-tool-ai">Github Repository</a></td>
    </tr>
</table>



## A natural language interface for querying federated research data 

[Neurobagel](https://www.neurobagel.org/) is a federated data ecosystem that enables researchers and other data users to locate and access research data that must remain at its original institute due to data governance requirements.

Currently, Neurobagel offers a graphical web query interface that interacts with the node APIs on the user's behalf, simplifying the process of formulating complex queries.

This project intends to build a chatbot that utilizes existing large language models (LLMs) to parse text provided by users into precise queries and reliably summarize the results for them. The chatbot should be able to receive and comprehend user prompts in natural language, initiate corresponding API calls using predefined Neurobagel parameters (like minimum age, maximum age, sex, etc.), interpret the results, and communicate that information back to the user. The goal is to choose open tools and models to allow for flexible hosting options.

## Understanding the codebase
To have a deeper understanding of the codebase visit [here](https://raya679.github.io/gsoc/codebase/).

## Contributions

A separate github repository [query-tool-ai](https://github.com/neurobagel/query-tool-ai) was established for the GSoC project, and all the code  was integrated into the project's main branch. Below are links to the key contributions I made:

- [LLM Extractions](https://github.com/neurobagel/query-tool-ai/pull/15)
- [Validations](https://github.com/neurobagel/query-tool-ai/pull/18)
- [Mapping to Term URLs](https://github.com/neurobagel/query-tool-ai/pull/20)
- [Set up continuous integration workflows](https://github.com/neurobagel/query-tool-ai/pull/22)
- [Added codespell to github action workflow](https://github.com/neurobagel/query-tool-ai/pull/34)
- [Generating API URL](https://github.com/neurobagel/query-tool-ai/pull/24)
- [Dockerization of the query-tool-ai code](https://github.com/neurobagel/query-tool-ai/pull/28)
- [FastAPI integration](https://github.com/neurobagel/query-tool-ai/pull/31)


## Future Scope 
- **Updates to the LLM Model:** Continuously updating and refining the LLM model to enhance output quality and minimize hallucinations.

## Conclusion

My GSoC experience has been incredibly rewarding and educational, significantly contributing to my future aspirations. I am deeply thankful to my mentors **Arman Jahanpour**, **Sebastian Urchs**, **Alyssa Dai**, **Brent McPherson**, **Jean-Baptiste Poline**, [INCF](https://www.incf.org/) and [Neurobagel](https://neurobagel.org/) for their unwavering guidance and support throughout the project. Their expertise and readiness to assist whenever needed have been invaluable. I also extend my gratitude to **Google** for offering such a fantastic opportunity to student developers worldwide.

I hope to continue collaborating with Neurobagel and INCF in the future and contribute further to its impactful projects.


                         