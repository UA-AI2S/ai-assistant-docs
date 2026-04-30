# Getting a List of Models

There are three ways to obtain a list models:

1. Go to [this page](../models-current.md) to view the list of CyVerse models. This list does not include models from external inference services e.g., Jetstream2.
2. Viewing your models in the Course Details
3. Using your API Key to view your models

## Viewing your models in the Course Details

Your available models will be visible in the AI-VERDE application. These are the steps:

1. Go to https://chat.cyverse.ai
2. After successfully logging in, click on the Details button of your course
3. Click on the "API Key" tab
4. The "Available Models" section will list all the models your course has access to

## Using your API Key to view your models

After obtaining your API Key from your course/team, you can obtain a detailed list of available models using curl:

```
curl -s -L "https://llm-api.cyverse.ai/v1/models" -H "Authorization: Bearer $OPENAI_API_KEY" -H 'Content-Type: application/json'
```

Alternatively, you can use `jq` or python's json module to view the output in a more human readable format.

Option 1: If you have `jq` installed:
```
curl -s -L "https://llm-api.cyverse.ai/v1/models" -H "Authorization: Bearer $OPENAI_API_KEY" -H 'Content-Type: application/json'|jq
```

Option 2: If you have python's json module installed:
```
curl -s -L "https://llm-api.cyverse.ai/v1/models" -H "Authorization: Bearer $OPENAI_API_KEY" |python -m json.tool
```

