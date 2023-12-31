# OpenAI API Usage

## Config
```python
from apigptcloud import openai
openai.api_key = ""
openai.api_base = ""
```

## ChatCompletion
Request example:
```python
res = openai.ChatCompletion.create(
    model="gpt-3.5-turbo",
    messages=[
        {"role": "system", "content": "You are a helpful assistant."},
        {"role": "user", "content": "Hello!"}
    ],
    temperature=2,
)
```
Response example:
```json
{
    "id":"chatcmpl-7SKQgp3ry5w9ZB0A3mMcvYOFB1VYG",
    "object":"chat.completion",
    "created":1686986070,
    "model":"gpt-35-turbo",
    "choices":[
        {
            "index":0,
            "finish_reason":"stop",
            "message":{
                "role":"assistant",
                "content":"Hello, this message is from apigpt.cloud! How may I assist you today?"
            }
        }
    ],
    "usage":{
        "completion_tokens":18,
        "prompt_tokens":18,
        "total_tokens":36
    }
}
```
## Completion
Request example:
```python
res = openai.Completion.create(
    model="gpt-3.5-turbo",
    prompt="I am a apple, and you are",
    max_tokens=7,
    temperature=0
)
```
Response example:
```json
{
    "id": "cmpl-7TkgRTfjrz80goegsOC2nrkzi1WPm",
    "object": "text_completion",
    "created": 1687325319,
    "model": "gpt-35-turbo",
    "choices": [
    {
      "text": " 20 year old female and I",
      "index": 0,
      "finish_reason": "length",
      "logprobs": null
    }
    ],
    "usage": {
    "completion_tokens": 7,
    "prompt_tokens": 3,
    "total_tokens": 10
    }
}
```
## Embedding
Request example:
```python
res = openai.Embedding.create(
    model="gpt-3.5-turbo",
    input="The food was delicious and the waiter..."
)
```
Response example:
```json
{
    "object": "list",
    "data": [
    {
      "object": "embedding",
      "embedding": [
        0.0023064255,
        -0.009327292,
        .... (1536 floats total for ada-002)
        -0.0028842222,
      ],
      "index": 0
    }
    ],
    "model": "text-embedding-ada-002",
    "usage": {
    "prompt_tokens": 8,
    "total_tokens": 8
    }
}
```