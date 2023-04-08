DistilRoBERTa base is a distilled version of the RoBERTa-base model, with 6 layers, 768 dimension, and 12 heads, and 82M parameters, it is faster than RoBERTa-base. The model is primarily intended for fine-tuning on whole sentence-based tasks such as sequence classification, token classification, and question answering but should not be used to generate harmful or alienating content. There is a risk of bias in the generated predictions as it may include harmful stereotypes. It is developed by Victor Sanh, Lysandre Debut, Julien Chaumond and Thomas Wolf of Hugging Face and is licensed under Apache 2.0. Users are encouraged to check out the RoBERTa-base model card for more information. When getting started with the model, it is recommended to use fine-tuned versions on the task that interests you.

> The above summary was generated using ChatGPT. Review the [original model card](https://huggingface.co/distilroberta-base) to understand the data used to train the model, evaluation metrics, license, intended uses, limitations and bias before using the model.

### Inference samples

Inference type|Python sample (Notebook)|CLI with YAML
|--|--|--|
Real time|[fill-mask-online-endpoint.ipynb](https://aka.ms/azureml-infer-online-sdk-fill-mask)|[fill-mask-online-endpoint.sh](https://aka.ms/azureml-infer-online-cli-fill-mask)
Batch | todo


### Finetuning samples

Task|Use case|Dataset|Python sample (Notebook)|CLI with YAML
|---|--|--|--|--|
Text Classification|Emotion Detection|[Emotion](https://huggingface.co/datasets/dair-ai/emotion)|[emotion-detection.ipynb](https://aka.ms/azureml-ft-sdk-emotion-detection)|[emotion-detection.sh](https://aka.ms/azureml-ft-cli-emotion-detection)
Token Classification|Token Classification|[Conll2003](https://huggingface.co/datasets/conll2003)|[token-classification.ipynb](https://aka.ms/azureml-ft-sdk-token-classification)|[token-classification.sh](https://aka.ms/azureml-ft-cli-token-classification)
Question Answering|Extractive Q&A|[SQUAD (Wikipedia)](https://huggingface.co/datasets/squad)|[extractive-qa.ipynb](https://aka.ms/azureml-ft-sdk-extractive-qa)|[extractive-qa.sh](https://aka.ms/azureml-ft-cli-extractive-qa)


### Model Evaluation

|Task|Use case|Dataset|Python sample (Notebook)|
|---|--|--|--|
|Fill Mask|Fill Mask|[imdb](https://huggingface.co/datasets/imdb)|[evaluate-model-fill-mask.ipynb](https://aka.ms/azureml-eval-sdk-fill-mask/)|


### Sample inputs and outputs (for real-time inference)

#### Sample input
```json
{
    "inputs": {
        "input_string": ["Paris is the <mask> of France.", "Today is a <mask> day!"]
    },
    "parameters": {
        "top_k": 2
    }
}
```

#### Sample output
```json
[
    [
        {
            "score": 0.6790168285369873,
            "token": 812,
            "token_str": " capital",
            "sequence": "Paris is the capital of France."
        },
        {
            "score": 0.051780153065919876,
            "token": 32357,
            "token_str": " birthplace",
            "sequence": "Paris is the birthplace of France."
        }
    ],
    [
        {
            "score": 0.20368757843971252,
            "token": 3610,
            "token_str": " busy",
            "sequence": "Today is a busy day!"
        },
        {
            "score": 0.09197165817022324,
            "token": 2721,
            "token_str": " beautiful",
            "sequence": "Today is a beautiful day!"
        }
    ]
]
```