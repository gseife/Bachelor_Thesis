# Bachelor_Thesis
Repository of my Bachelor Thesis at UZH in the Spring Semester of 2025

## Abstract
#### Background
In today’s rapidly evolving labour market, skill-based hiring is crucial. This requires comprehensive and up-to-date skills ontologies. However, manually identifying and integrating new and emerging skills from vast numbers of job advertisements is cumbersome and impractical. This thesis addresses the challenge of automatically detecting novel skills of job advertisements to ensure ontologies remain current and relevant. 

#### Methods
This research proposes and evaluates a novel, multi-stage pipeline for detecting novel skills from job advertisements that are not yet present in an existing ontology. The approach first uses a large language model (LLM) to compare skill mentions extracted from job ads against ontology-matched skills, generating a list of potential ”novel skill candidates”. These candidates are then processed by a ”Turbo” module, that uses a re-matching and a configurable similarity threshold to filter out noise. Finally, an aggregation step combines token-order-insensitive string matching and DBSCAN clustering to group syntactically and semantically similar novel skills, significantly reducing the manual curation workload. 

#### Evaluation and Results
The pipeline was tested using three different LLMs (GPT-4o, Gemini-2.0-flash, and DeepSeek-V3) on datasets of Swiss job advertisements. The results demonstrate the system’s effectiveness in identifying genuine novelties while minimizing noise. The Turbo filtering mechanism reduced false positives by 82%, and aggregation step significantly reduced manual curation efforts by 97%, while still preserving 12% of the originally proposed novel skills in the 3% of the final output. Comparative analysis showed that Gemini-2.0-flash was the most effective
model for identifying true novelties, achieving a novelty detection ratio of up to 73%. An expert evaluation further validated the pipeline’s practical usability and potential for real-world implementation.

#### Conclusion
This thesis successfully demonstrates a scalable and efficient pipeline for novelty detection in skill extraction using LLMs. By combining automated detection with robust filtering and aggregation, the approach effectively balances automation and expert oversight. This approach and its derived system provides a valuable tool for maintaining dynamic skill ontologies, laying a strong foundation for future work in automated ontology maintenance.

## Setup 
A requirments.txt file is provided which contains all the needed libaries for the execution of the programm.

## Usage

### Prompt(prompt.py)
To run the prompt you will need an **API key** for the LLM service. 

### Turbo(post_processing.py)
The turbo can't be executed directly because the connecting API is an internal Program of x28 which isn't accesible to the public. To execute the turbo a matching api call needs to be implemented and the barrier needs to be adjusted accordingly. 

### Aggregation(aggregation.py)
To run the aggregation you will need an **API key** for the embedding service.

You can customize the behavior of the aggregation by adjusting the parameters in the `full_aggregation_pipeline` function:

- **`count_threshold`**: Controls how many low-frequency (long-tail) entries are grouped together.  
  A higher value results in more entries being considered part of the long tail.

- **`eps`**: Sets the maximum distance between embeddings for them to be considered semantically similar.  
  A higher value allows for looser semantic grouping.

- **`min_samples`**: Defines the minimum number of similar skills required to form a cluster.  
  A higher value results in fewer but more robust clusters.

- **`grouping_threshold`**: Determines how syntactically similar skills must be to be grouped.  
  A higher value enforces stricter similarity based on wording.
