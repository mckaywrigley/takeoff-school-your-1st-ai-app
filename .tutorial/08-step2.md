# Step 2: Set your api key

Now you need to set your api key.

```python
openai.api_key = os.getenv("OPENAI_API_KEY")
```

This uses the os module to retrieve the environment variable called "OPENAI_API_KEY" and assign it to the api_key property in the openai library.

Now you're all set to make requests to OpenAI!