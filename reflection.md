# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
- List at least two concrete bugs you noticed at the start  
  (for example: "the secret number kept changing" or "the hints were backwards").

When I first ran the game, the functionality was somewhat intact, but it was broken in a few key ways. When the guessed number was higher than the secret number, the game would incorrectly tell me to guess higher. Also the Hard difficulty was easier than the Normal difficulty by having a smaller range of possible secret numbers and more attempts. Finally, the new game state always call the range 1-100, even if the user selected a different difficulty level.

---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).

I used Claude Code for this project. One correct suggestion was when I asked how to keep a variable from resetting in Streamlit when I click a button, and it suggested using `st.session_state`. I verified this by implementing the change and seeing that the secret number no longer changed with each button click. An incorrect suggestion was when I asked for help fixing the hints, and it suggested changing the logic to check if the guessed number was less than or greater than the secret number, but it didn't account for the fact that the hints were reversed. I verified this by testing the game and realizing that the hints were still incorrect, which led me to realize that I needed to reverse the conditions in the logic.

---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
- Did AI help you design or understand any tests? How?

I decided a bug was really fixed by running the game and testing the specific functionality that was broken. I didn't use formal test cases like pytest; instead, I tested everything by just running the Streamlit app and interacting with it directly. Some of the manual tests I ran included guessing a number and checking if the hints were correct—for example, I guessed a number that was higher than the secret number and checked if the hint said "Guess lower". I tested the session state fix by clicking the submit button multiple times and verifying that the secret number did not change. AI helped me understand what manual tests to run for the game logic, such as testing the hint functionality and the game over conditions by running the app and checking different scenarios.

---

## 4. What did you learn about Streamlit and state?

- In your own words, explain why the secret number kept changing in the original app.
- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?
- What change did you make that finally gave the game a stable secret number?

The secret number kept changing in the original app because Streamlit reruns the entire script every time a user interacts with it (like clicking a button). This means that any variables defined in the script are reset to their initial values on each interaction, which is why the secret number was changing. Streamlit "reruns" refer to this behavior of re-executing the script from top to bottom whenever an event occurs. To manage state across these reruns, Streamlit provides `st.session_state`, which allows you to store values that persist across interactions. The change I made to give the game a stable secret number was to store the secret number in `st.session_state` so that it retains its value even when the script reruns after a button click.

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.

One habit I want to reuse in future projects is the practice of writing tests for my code, as it helps ensure that my fixes are effective and that I can catch any regressions. Next time I work with AI on a coding task, I would be more cautious about accepting suggestions without thoroughly understanding them and verifying their correctness. This project has made me realize that while AI can be a powerful tool for generating code, it's essential to critically evaluate its suggestions and not rely on it blindly, as it can sometimes provide incorrect or misleading information.
