---
title: Scheduled Agents
description: Set up an agent that runs on its own — on a schedule or on demand — to do recurring work for you.
---

A **Scheduled Agent** is a saved piece of work that Logic AI runs on its own — either on a schedule you set or whenever you press **Run Now**. It's the same assistant you chat with, given a standing goal and turned loose to complete it without you sitting there.

Good candidates are the recurring things you'd otherwise do by hand:

- *"Every Monday at 8am, email me a summary of new leads from last week."*
- *"Each morning, find opportunities closing this week with no activity in 5 days and post them to the Sales Chatter group."*
- *"On the 1st of the month, create a follow-up task for every account with an open renewal."*

## Creating an agent

You don't fill out a form — you just ask in the chat. Describe what you want done and how often, for example *"Every Monday at 8am, email me a summary of new leads."* Logic AI turns that into an agent: a name, the instructions it will follow each run, the schedule, and the tools it's allowed to use. It confirms the details with you before saving.

New agents show up in the **Scheduled Agents** tab.

## The Scheduled Agents tab

Each agent appears as a card showing its name, when it last ran and how that went, and a **Scheduled** badge if it runs on a timer. From a card you can:

- **View** — open the agent to see its schedule, instructions, and full run history
- **Edit** — change anything about the agent (see below)
- **Run Now** — trigger a run immediately, without waiting for the schedule

Open a run to see exactly what the agent did — its steps are grouped and tool calls are collapsed by default so you can skim, then expand any step for detail. While a run is active, its status updates on its own.

## Editing an agent

Press **Edit** and the agent opens in a chat sheet — just tell Logic AI what to change: *"run it every weekday instead of Mondays,"* *"also include closed-lost deals,"* or *"stop sending the email, just post to Chatter."* You can change the name, the instructions, the schedule (or remove it to make the agent run-on-demand only), which tools it may use, the model, and whether it's active.

You can also delete an agent from its edit view. Deleting an agent also cancels its schedule.

## What an agent can do — and can't

An agent runs with the **same permissions and tools as you**. It can only see and change records you could, and it can only use tools your admin has enabled for agents. If you ask an agent to use a tool that needs admin approval, Logic AI tells you which one.

A few things to know:

- **Runs cost credits**, the same as a normal chat, and count toward your [usage limits](/products/logicai/docs/admin-usage-limits). An agent stops after a set number of steps (its *max turns*) so a single run can't run away.
- Because an agent runs unattended, there's **no one to click "approve"** mid-run — so an agent only ever uses the tools it was given, within your permissions.
- Schedules only fire while the agent is **active**.

## Turning the feature on or off

Scheduled Agents are **on by default**. Admins can turn the feature off — for the whole org or per user — from the [Policies](/products/logicai/docs/admin-policies) tab, and control which tools agents are allowed to use there too.
