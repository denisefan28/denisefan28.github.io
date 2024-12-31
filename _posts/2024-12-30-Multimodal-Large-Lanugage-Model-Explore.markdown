---
layout: post
title:  "Multimodal Large Lanuage Model Explore - Pipecat AI"
date:   2024-12-30 16:57:26 -0400
categories: LLM, multimodal, chatbot
---

A few months ago, I started brainstorming ideas for my eco-op project. Considering my interest in multimodal large language models, I decided to create an emotional stress support chatbot to give me more fun through my first winter in Canada.

My initial thought was to use a locally served language model, such as Ollama, which should not pose any issues. The experience can be similar to gpt4all. While gpt4all offers a pure text chat experience, I still need text-to-voice and voice-to-text modules to support basic voice chat functionality.

![Alt text](../_imgs/3-1.png)

When we initiate a conversation, we create a session and manage it by maintaining the session data. Naturally, this involves adding a service to the architecture for session-level management. Additionally, this service can host the text-to-voice and voice-to-text conversion modules.

![Alt text](../_imgs/3-2.png)

It seems sufficient, but it's not good enough. The voice chat experience is different from text chat. A bunch of text messages are sent to the service, then the service concatenates the text messages with prompts and sends them to the LLM. After the LLM generates the response text, the message is sent back to the client side. It's acceptable to wait to process a large amount of text messages. To me, it's totally acceptable, but it's not acceptable for voice applications.

So now the question is, how do we properly handle the audio stream? After doing some research, I decided to choose the Pipecat framework, which is an open-source Python framework for building voice and multimodal conversational AI agents.

Luckly, the RTVI has two example projects. I can use them as a start point to create my own voice chat bot.

Before I start to run the demo using this framework, there are several services I need to register :

| No. | Website| Description | Must Have? |
|---  |-----   | ---------   | ---------- |
|1    |https://dashboard.daily.co | Leverage daily to create meeting room. Instead of create everything by myself, I can use meetings create a virtual place to chat with my bot. One advantages of using | Y |
|2    |https://play.cartesia.ai/voices | A text to speech service and it provides instant voice clone and voice design functionality| Y |
|3    |https://console.groq.com/       | A fast AI inference service. I choose this inference API instead of calling OpenAI API is because of a issue [`using correct API key instead saying invalid API key #3`](https://github.com/pipecat-ai/rtvi-infra-examples/issues/3) . I can update to use openAI or my local served service later. | N |

After sucessfully create the service API. I need to update my API key to RTVI examples:

- [rtvi-infra-examples](https://github.com/denisefan28/rtvi-infra-examples)
- [rtvi-client-web](https://github.com/denisefan28/rtvi-client-web)


![Alt text](../_imgs/3-3.png)

Launch the backend service (rtvi-infra-examples) and then start the client UI (rtvi-client-web). In the end I can succssfully start the demo project.

Building an emotional stress support chatbot using multimodal large language models has been an good experience. By leveraging various services and frameworks like Pipecat, Daily, Cartesia, and Groq, I was able to create a functional and interactive voice chat application. I look forward to further refining this project and exploring new functions of Pipecat.