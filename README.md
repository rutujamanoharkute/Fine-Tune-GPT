# Fine-Tune-GPT
# Youtube video Link : https://youtu.be/yW0Bma_v92o

```markdown
# Fine-Tuning GPT Model for RecipeMaster Chatbot

## Project Overview

This project involves fine-tuning a GPT model to create a chatbot named "RecipeMaster," which specializes in Indian recipes. The fine-tuned model is trained to understand and generate responses about Indian food culture and specific recipes based on user queries.

## Table of Contents

- [Project Overview](#project-overview)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
- [Dataset Preparation](#dataset-preparation)
- [Fine-Tuning Process](#fine-tuning-process)
- [Evaluation](#evaluation)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgments](#acknowledgments)

## Getting Started

### Prerequisites

Ensure you have the following installed:

- Python 3.8 or higher
- Required Python packages (listed in `requirements.txt`)
- OpenAI API key for model training and inference

### Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/your-username/your-repo-name.git
   cd your-repo-name
   ```

2. Install the dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Dataset Preparation

1. **Data Collection**: The dataset used for fine-tuning is stored in a JSONL file (`data.jsonl`). This dataset includes conversations about Indian recipes, formatted with roles such as `system`, `user`, and `assistant`.

2. **Data Loading**:
   ```python
   import json

   data_path = "data.jsonl"

   # Load the dataset
   with open(data_path, 'r', encoding='utf-8') as f:
       dataset = [json.loads(line) for line in f]

   print("Num examples:", len(dataset))
   print("First example:", dataset[0])
   ```

3. **Data Validation**: The dataset is validated to ensure proper formatting, including checks for missing keys or incorrect roles.

## Fine-Tuning Process

1. **Loading Pre-trained GPT Model**:
   ```python
   from openai import OpenAI
   client = OpenAI()

   # List available models
   models = client.models.list()
   print("Available models:")
   for model in models:
       print(model.id)
   ```

2. **Fine-Tuning**:
   The fine-tuning process involves specifying the model ID and providing the dataset for training. Ensure that the dataset is properly preprocessed and formatted.

3. **Inference**:
   ```python
   completion = client.chat.completions.create(
       model="ft:gpt-3.5-turbo-0125:personal::9rtzv3yx",  # Replace with your specific model identifier
       messages=[
           {"role": "system", "content": "You are RecipeMaster, an expert in Indian recipes."},
           {"role": "user", "content": "hello"}
       ]
   )
   print(completion.choices[0].message)
   ```

## Evaluation

Evaluate the model by interacting with it and assessing the relevance and accuracy of the responses. Example queries could include asking for specific recipes or general information about Indian cuisine.

## Usage

Once fine-tuned, the model can be used in various applications, including:

- Chatbots specializing in Indian recipes
- Culinary virtual assistants
- Content generation for recipe websites

Example usage:
```python
input_text = "What's the Masala Karela Recipe?"
output = model.generate(tokenizer.encode(input_text, return_tensors='pt'))
print(tokenizer.decode(output[0], skip_special_tokens=True))
```

## Contributing

Contributions are welcome! Please open an issue or submit a pull request with any improvements or fixes.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

## Acknowledgments

 OpenAI community for their tools and support.

```

This README file is structured to reflect the process and content of your Jupyter notebook, guiding users through setup, fine-tuning, and usage of the GPT model. Adjust any section as needed to fit your project specifics.


