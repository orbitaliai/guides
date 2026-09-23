# Build your first voice agent in the UI

[All guides](../toc_en.md) · **English (US)** · [Español (España)](es.md) · [Italiano](it.md)

An Orbitali voice agent combines a voice, a role, instructions, and the information it needs to help a caller. In this tutorial, you’ll prepare a simple FAQ agent using the web interface and learn where to configure and test it.

You need access to an Orbitali organization and its **Agents** page. No code or phone number is needed to follow the static-agent setup. A browser voice test requires a saved, active agent and microphone access.

**About this walkthrough:** we stop the creation flow before **Create agent**, then use the existing **FAQ English** agent to tour the interface. No new agent was created, no existing settings were changed, and no test call was started. Screenshots show the English UI as captured on September 23, 2026; your organization’s agents and available options may differ.

## 1. Choose an agent type

Open **Agents** in the sidebar and click **New agent**. This tutorial uses the manual flow; **Create with AI** is a separate entry point.

![New agent dialog with Static selected](images/01-agent-type.jpg)

The first decision is how the agent gets its instructions and performs custom actions:

| Type | How it works | When to choose it |
| --- | --- | --- |
| **Static** | Uses instructions stored in Orbitali, without custom HTTP or webhook tools. | A first FAQ or information agent without a backend. |
| **HTTP Tooling** | Uses stored instructions; each custom tool calls its own HTTP endpoint. | Actions connected to separate APIs. |
| **Webhook Tooling** | Routes custom tool calls through one server endpoint and can obtain instructions dynamically. | Workflows controlled by your backend. |

Choose **Static**, then **Next**. The agent type cannot be changed after creation, so choose based on the actions you expect to need. Static agents can still use built-in capabilities such as knowledge search once documents are ready.

## 2. Start from a template

Select **FAQ Concierge - English**, then **Continue**.

![Template picker with FAQ Concierge - English selected](images/02-template.jpg)

A template pre-fills the agent’s persona, greeting, and instructions. You can edit these fields before saving. **Blank** starts with an empty prompt; the other templates offer starting points for reception, support, and sales.

## 3. Review the unsaved configuration

On the **Agent** tab, give the agent a recognizable name, such as `My first FAQ agent`. Keep **Status** set to **draft** while preparing it, choose **English (US)** for this example, and select a voice.

![Unsaved agent configuration with Create agent visible](images/03-unsaved-agent.jpg)

| Setting | What it controls |
| --- | --- |
| **Name** | The name used to identify the agent in your organization. |
| **Status** | Whether the agent is a draft, active, or inactive. Browser testing requires active status. |
| **Language** | The language and locale for the conversation. |
| **Voice** | The voice profile, shown here as **Eve - Warm female**. |
| **AI identity disclosure** | The mandatory sentence Orbitali speaks before the greeting. |
| **Ambient sound** | Optional background audio that loops during the session. |
| **Tool-calling sound** | Optional audio played while the agent executes a tool. |
| **Inbound numbers** | Phone numbers linked to this agent for incoming calls. Leave these unlinked for a browser-only first test. |

The language of this article does not determine the agent’s language. The captured UI offers English (US), Spanish (Spain), and Spanish (US); an Italian translation of this guide does not imply an Italian voice-language option.

## 4. Give the agent a clear job

Open **Instructions**. The template has already populated the main fields.

![Template identity and greeting in the unsaved editor](images/04-template-instructions.jpg)

Use **Identity** for who the agent is, its role, and its tone. Use **Greeting** for its opening line. Use **Instructions**, further down the page, for what it should do and the rules it must follow.

For a first FAQ agent, adapt this starting point to your organization:

**Identity**

```text
You are the friendly FAQ assistant for [organization].
Speak in clear American English. Keep answers brief and ask one question at a time.
```

**Static greeting**

```text
Thanks for calling [organization]. What can I help you with today?
```

**Instructions**

```text
Answer questions about our services, hours, and policies using the knowledge base.
Search the knowledge base before answering factual questions.
If information is missing or unclear, say you do not have a confirmed answer.
Do not invent prices, opening hours, or commitments.
Do not promise a booking, transfer, or follow-up unless the required capability is configured.
Ask whether the answer helped before ending the conversation.
```

Replace the placeholder with your organization’s name. Prepare the supporting FAQ document too: instructions describe behavior, while knowledge documents provide facts.

**This is the stopping point for our creation walkthrough.** **Create agent** would save the new agent. We leave it unclicked and return to **Agents**. When building your own agent, saving it as a draft is the step that unlocks knowledge uploads and further setup; the remaining screenshots use an existing agent instead.

## 5. Explore a saved agent: FAQ English

Open **FAQ English** from the agent list.

![FAQ English configuration and navigation](images/05-faq-config.jpg)

This example is already **active**, uses **English (US)** and **Eve**, and has no linked inbound number. Its **Config** tab corresponds to **Agent** in the creation editor.

FAQ English is a **Webhook Tooling** agent, unlike the static agent prepared above. It therefore has extra backend settings, including **Server URL**, farther down the configuration page. These are not needed for a simple static FAQ agent. Do not copy this demo agent’s integration settings into your own configuration.

The top navigation separates the work into **Config**, **Instructions**, **Knowledge**, **Tools**, and **Web chat**, with **History** and **Logs** for reviewing activity.

### Instructions: persona, greeting, and behavior

![FAQ English identity and greeting](images/06-faq-instructions.jpg)

FAQ English’s identity describes its role as an Orbitali website assistant. Its greeting starts the conversation, and its instructions farther down describe how to answer questions and use configured tools.

For webhook agents, instructions can be **Static** or **Dynamic**. Static instructions are stored in the editor; dynamic instructions come from the configured server at call start. A beginner static agent uses stored instructions. **Outbound greeting** applies to outbound calls and falls back to the static greeting when empty.

### Knowledge: give the agent reliable facts

![Knowledge upload form and ready FAQ document](images/07-faq-knowledge.jpg)

The **Knowledge** tab accepts TXT, Markdown, and PDF files. FAQ English has an **Orbitali FAQ** document marked **ready**. The displayed chunks are the smaller sections created during indexing so the agent can retrieve relevant information.

For your own saved agent, enter a document name and a description explaining when it should be used, choose the file, wait for processing, and review and save its details. Confirm that it is **ready** before relying on it in a test. Uploading knowledge is unavailable until the agent has been saved.

Start with one focused FAQ covering real services, hours, policies, and approved answers. Tell the agent to search it and acknowledge missing information.

### Tools: understand what the agent can do

![Built-in tools and connected MCP tools](images/08-faq-tools.jpg)

The built-in tools explain core capabilities:

- **hang_up** ends a call gracefully and is always available.
- **transfer_call** requires a configured transfer number.
- **search_knowledge** requires ready knowledge documents.

The **MCP Tools** section lists tools from connected MCP servers. Checked tools are enabled for this agent. Connections and available tools depend on your organization.

![FAQ English webhook tools for availability, booking, and lead notifications](images/08b-faq-webhook-tools.jpg)

FAQ English also has custom webhook tools: **check_availability**, **create_booking**, and **send_slack_lead**. These are examples of connected actions, not capabilities you get merely by writing their names in a prompt. A static first agent does not need these custom tools. Configuring backend integrations is beyond this tutorial.

## 6. Test in the browser when your agent is ready

On a saved, active agent, open **Config → Test agent**.

![Browser voice test dialog before starting a session](images/09-test-agent.jpg)

When testing your own agent:

1. Save changes in both configuration and instructions, and make the agent **active**. Unsaved changes or a non-active status disable browser testing.
2. Click **Test agent**, then **Start test**.
3. Allow microphone access if prompted and speak. The dialog displays the conversation transcript.
4. Ask a question covered by the FAQ, then one it does not answer. Check that the agent uses the source information and admits what it does not know.
5. Check the disclosure, greeting, voice, and pacing. Use **Stop test** to finish.

Our screenshot stops before **Start test**. **Test call**, shown in the Instructions section, is a separate outbound telephone test; it is not the browser microphone test.

## 7. Review and choose a channel

Use **History** to review call and web chat activity and **Logs** to investigate runtime events. After testing, refine unclear instructions or missing knowledge and try the same questions again.

For incoming telephone calls, connect your carrier and link an appropriate number through **Inbound numbers → Link number**. For a website, **Web chat** provides launcher settings and an embed snippet, subject to your plan. Neither is required to understand the creation flow or use the browser test on a saved, active agent.

Before moving on, check that your agent has a clear role, a suitable voice and greeting, ready source documents, and sensible responses to both known and unknown questions.
