# Step 3: Input a question

We need a way to ask our question.

To do this, we're going to create a variable named question.

We're going to use the built-in `input` function so that we can enter an input and assign it to the question variable we created. We added in a \n - a `newline` character - at the end of the question so that our input starts on a new line.

We'll also add a `print` statement that prints our question out to the console.

```python
import os
import openai

openai.api_key = os.getenv("OPENAI_API_KEY")

question = input("What is your question?\n")

print(question)
```

Go ahead and hit the big green "Run" button and try it out - you can now enter in a question and have it printed out!

To style the input a bit, we're going to make the text blue.

```python
question = input("\033[34mWhat is your question?\n\033[0m")
```

The `\033[34m` at the start sets the text to green, and the `\033[0m` at the end resets it back to white.