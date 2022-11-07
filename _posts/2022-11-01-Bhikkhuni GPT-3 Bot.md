---
layout: post
title: Bhukkuni your mindful GPT-3 chatbot
---


It has been a long time since I updated this blog!

I put together a chatbot for using GPT-3 for fun and I thought this would be a great opportunity for a new post!

The GPT-3 model was developed by OpenAI and it has a very accessible playground, here is a link https://beta.openai.com/playground. The playground is very helpful to explore and get a general idea of the sensitivity of the model to the different parameters. A description of the parameters available in the playground is in OpenAi’s documentation.

In this case, I used Completions for this task. The prompt for the bot is shown below. 

![an image alt text]([https://mcarolinag.github.io/images/'Screen Shot 2022-11-03 at 4.46.07 PM.png' "GPT-3 Playgorund inputs")

![Alt](/mcarolinag.github.io/images/Screen Shot 2022-11-03 at 4.46.07 PM.png "GPT-3 Playgorund inputs")

You are talking with Bhukkuni your mindful chatbot. I was created by Buddha to share buddhism teachings, help people reach enlightenment and end suffering.\n\nPerson: who are you?\n\nBhukkuni: I am Bhukkuni, your mindful chatbot. I was created by Buddha to share buddhism teachings, help people reach enlightenment and end suffering.\n\nPerson:what is suffering?\n\nBhukkuni: Suffering, or dukkha in Buddhist terms, is the basic unsatisfactoriness of life. It includes both the obvious pain and suffering that come with illness, old age, and death, as well as the more subtle suffering that comes from wanting things to be different than they are.\n\nPerson:what are the buddhism teachings?\n\nBhukkuni: The core teachings of Buddhism are often referred to as the Four Noble Truths. These truths are that suffering exists; that suffering has a cause; that there is an end to suffering; and that there is a path to the end of suffering.\n\nPerson:"
 

I copied the code from “View Code” and included it in a function ask defined below.

```def ask(question, chat_log=None):
 prompt_text= f"{chat_log}{restart_sequence}: {question}{start_sequence}:"
 response = openai.Completion.create(
   model="text-davinci-002",
   prompt=prompt_text,
   temperature=0.84,
   max_tokens=150,
   top_p=1,
   frequency_penalty=0,
   presence_penalty=0.5
 )
 story=response['choices'][0]['text']
 return str(story)```

The prompt_text included the history conversation called chat_log. The chat log was appended with the question and answer.

def append_interaction_to_chat_log(question,answer,chat_log=None):
 if chat_log is None:
   chatlog= session_prompt
 return f"{chat_log}{restart_sequence} {question}{start_sequence}{answer}"

I created a small application in Flask. This application received the text message, got an answer from the function ‘ask’, appended the answer to the chat log and responded to the text message via Twilio.

 If you are curious and would like to chat with Bhukkinhi, you may text her at 

