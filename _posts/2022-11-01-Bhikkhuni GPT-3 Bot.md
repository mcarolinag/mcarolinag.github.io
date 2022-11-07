---
layout: post
title: Bhukkuni your mindful GPT-3 chatbot
---


It has been a long time since I last updated this blog!

I put together a chatbot using GPT-3 for fun and I thought this would be a great opportunity for a new post.

The GPT-3 model was developed by OpenAI and it has a very accessible playground. You may need an account to access the playground and API. Here is a link to the playground https://beta.openai.com/playground. The playground is very helpful to get a general idea of the model output while toggling the parameters. A description of the parameters available in the playground is in OpenAI’s documentation https://beta.openai.com/docs/api-reference/models/retrieve.

In this case, I used Completions for this task. The prompt for the bot is shown below. 


![prompt](/blog/images/'Screen Shot 2022-11-03 at 4.46.07 PM.png' "GPT-3 Playground inputs")
 

I copied the code from “View Code” in the payground top menu and included it in a function ask defined below.

```
def ask(question, chat_log=None):

   prompt_text= f"{chat_log}{restart_sequence}: {question}{start_sequence}:"
   
   response = openai.Completion.create(
               model="text-davinci-002",
               prompt=prompt_text,
               temperature=0.84,
               max_tokens=150,
               top_p=1,
               frequency_penalty=0,
               presence_penalty=0.5)
               
   story=response['choices'][0]['text']
   
   return str(story)
   ```
The prompt_text for each new question includes the history of the conversation, chat_log. The chat-log was maintained up to date by appending the last question and answer pair to the chat_log.

```
def append_interaction_to_chat_log(question,answer,chat_log=None):
 if chat_log is None:
   chatlog= session_prompt
 return f"{chat_log}{restart_sequence} {question}{start_sequence}{answer}"
```
The implementation was done by developing a small application in Flask. This application received the text message, got an answer from the function ‘ask’, appended the answer to the chat log and responded to the text message via Twilio.

If you are curious and would like to chat with Bhukkinhi, you may text her at (424) 622 -1594!

