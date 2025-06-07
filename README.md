# Bachelor_Thesis
Repository of my Bachelor Thesis at UZH in the Spring Semester of 2025

## Abstract
Insert english abstract

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