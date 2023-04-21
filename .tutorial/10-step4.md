# Step 4: Make an OpenAI request

We now need to make a request to the OpenAI API.

To do this, we're going to take a code snippet from the [OpenAI docs](https://platform.openai.com/docs/api-reference/chat/create?lang=python).

We'll be making a Chat Completion request. Chat Completions are the type of completions that you see in ChatGPT. This is the most common type of request to make with OpenAI.

In the docs on the right, you'll see a code example. Make sure to select the "Python" option from the dropdown.

We're going to add similar code to our program in between the question variable and the print statement:

```python
import os
import openai

openai.api_key = os.getenv("OPENAI_API_KEY")

question = input("\033[34mWhat is your question?\n\033[0m")

completion = openai.ChatCompletion.create(
    model="gpt-3.5-turbo",
    messages=[
      {"role": "system", "content": "You are a helpful assistant. Answer the given question."},
      {"role": "user", "content": question}
    ]
  )

print(question)
```

Let's run through what this does.

1st, we create a `completion` variable.

2nd, we make a request to OpenAI's "chat completion" endpoint via the openai library we imported.

That request takes in two parameters:

1. The model to use. In this case, we're using `gpt-3.5-turbo` (the default ChatGPT model).
2. The messages to pass it as input. The 1st message is a `system` message with a basic prompt that says "You are a helpful assistant. Answer the given question." This instructs the AI how to behave. The 2nd message is a user message - our message - which passes in our question that we saved to the question variable.

Now, instead of printing our question, we want to print the response from OpenAI.

```python
print("\033[32m" + completion.choices[0].message.content + "\n")
```

We did 3 things here:

1. Style our print statement as green text
2. Access the response via `completion.choices[0].message.content`
3. Add a new line character to add spacing to our CLI

We used the + syntax to add each of these to a single print statement.

Now run the program again to ask your AI bot a question and get a response!