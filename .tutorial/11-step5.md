# Step 5: Repeating the Q&A bot

You'll notice the program ends after asking a single question.

Let's fix that.

We're going to put our Q&A code inside of a `while` loop.

This will repeat the process until we stop running the program so that we can keep asking questions.


```python
import os
import openai

openai.api_key = os.getenv("OPENAI_API_KEY")

while True:
  question = input("\033[34mWhat is your question?\n\033[0m")

  completion = openai.ChatCompletion.create(
    model="gpt-3.5-turbo",
    messages=[
      {"role": "system", "content": "You are a helpful assistant. Answer the given question."},
      {"role": "user", "content": question}
    ]
  )

  print("\033[32m" + completion.choices[0].message.content + "\n")
```

We set the condition of the `while` loop to `True` which is a `boolean` value. Boolean values evaluate to either True or False.

Setting it to True means that it will keep running the code inside the `while` loop until we stop the program.