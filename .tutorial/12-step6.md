# Step 6: Handling 'exit'

We can also add an `if` statement to check if we type 'exit' as our question.

This will stop the program.

```python
import os
import openai

openai.api_key = os.getenv("OPENAI_API_KEY")

while True:
  question = input("\033[34mWhat is your question?\n\033[0m")

  if question.lower() == "exit":
    print("\033[31mGoodbye!\033[0m")
    break
  
  completion = openai.ChatCompletion.create(
    model="gpt-3.5-turbo",
    messages=[
      {"role": "system", "content": "You are a helpful assistant. Answer the given question."},
      {"role": "user", "content": question}
    ]
  )

  print("\033[32m" + completion.choices[0].message.content + "\n")
```

We create an `if` statement that checks for a specific condition.

We call the built-in `lower()` method on our question variable which turns it into a lowercase string, and then we check if the text is equal to 'exit' and if so, we run the code inside the `if` statement.

The code prints "Goodbye!" in red text, and then the `break` "breaks" us out of the `while` loop which ends the program.