# Example 3: a tutorial, from over-explained to over-trimmed to lean

A tutorial for the fictional SaaS "Acme Forms": collect RSVPs for an event with a form and get each answer posted to a chat channel.
This example shows two failure modes. The first draft narrates the screen. The second cuts it with reference-mode rules alone and comes out curt. The third keeps the short path and puts the voice back.

## Draft 1: over-explained

```md
# Collecting RSVPs with Acme Forms

This tutorial explains how to create a form in Acme Forms, add questions, publish it,
and connect it to a chat channel. Acme Forms is a powerful form builder that lets you
easily collect responses from anyone.

## Step 1: Open the dashboard

Sign in to Acme Forms. The dashboard appears. On the left side of the screen there is a
sidebar with "Forms", "Responses", "Integrations", and "Settings". Click "Forms".
The Forms screen opens. If you have no forms yet, "No forms yet" is shown.

## Step 2: Create a form

Click the "New form" button in the top-right corner. A dialog titled "Create form" appears.
Enter a name in the "Form name" field (up to 100 characters). Click "Create".
"Form created" is shown at the bottom of the screen and the form editor opens.

## Step 3: Add questions

| Field | Description |
| --- | --- |
| "Question type" | Selects the type of question. |
| "Question text" | The text of the question. |
| "Required" | Makes the question required. |
| "Description" | An optional description. |

Click "Add question", choose "Multiple choice", enter "Will you attend?", and add the
options "Yes" and "No". Turn on "Required". Repeat for "Name".

## Step 4: Publish

Click "Publish". The status changes from "Draft" to "Published". Click "Copy link".

## Step 5: Connect a channel

Open "Integrations", click "Chat", click "Connect", and choose a channel.

## Troubleshooting

### "Form name is required" is shown
Enter a form name.

### "You have reached the form limit" is shown
Your plan's form limit has been reached. Delete a form or upgrade.

### Responses don't appear in the channel
Make sure the integration is connected.

## Summary

In this tutorial you created a form, added questions, published it, and connected a channel.
```

## Draft 2: trimmed with reference rules only

```md
# Collecting RSVPs

Create a form and post its responses to a chat channel.

## Before you start

- In your chat workspace, the Acme Forms app must be allowed to post in the target channel.

## Steps

1. Create a form under "New form".
2. Add a "Multiple choice" question and a "Name" question.
3. "Publish". Copy the link.
4. Connect a channel under "Integrations" → "Chat".

## Notes

| Change | Effect on the published form |
| --- | --- |
| Questions | Applied on "Publish" |
| Integration | Immediate |

Responses submitted before connecting are not posted.
```

Accurate and short, but it reads like a list of commands. "'Publish'. Copy the link." is not a sentence. The table assumes the reader already expects edits to need re-publishing. Nothing tells the reader when they are done.

## Draft 3: lean tutorial

```md
# Collect RSVPs and get each answer in your chat

Let's set up an RSVP form whose answers show up in your team's chat as they come in.
You won't need to check a spreadsheet; each reply posts to the channel you pick.

## Before you start

**Allow the Acme Forms app to post in the channel you'll use.** Do this in your chat
workspace's app settings. Acme Forms can't change it for you, and without it the
connection succeeds but nothing is ever posted.

## 1. Create the form

Create a new form and give it a name only you need to recognize, such as "Team dinner".

## 2. Add two questions

Add a multiple-choice question, "Will you attend?", with "Yes" and "No", and a short-text
question for the person's name. Mark both as required so you don't get anonymous replies.

## 3. Connect the channel

Under "Integrations", connect "Chat" and pick the channel. Do this before you share the
link: answers that arrive before the channel is connected are never posted.

## 4. Publish and try it

Press "Publish", open the link in a private window, and answer it yourself.
If your reply shows up in the channel, you're done. Share the link.

## Changing the form later

Edits to questions stay in the draft until you press "Publish" again, so people keep
seeing the old version until then. Changes to the channel take effect immediately.

## When nothing shows up in the channel

If the form says your answer was sent but the channel stays empty, check the app
permission from "Before you start". That is the only failure that shows no error.
```

## What changed, and why

| From draft 1 | Decision | Reason |
| --- | --- | --- |
| Preamble and "powerful form builder" | Cut | Preamble and marketing; replaced by the outcome framed as what the reader gets |
| Steps 1–2: sidebar, dialog, toast | Cut to one sentence | The screen makes the next move obvious |
| Field table | Cut | Only two fields matter for this goal; they are named in the step |
| Two troubleshooting entries with self-explaining messages | Cut | The message already says what to do |
| "Summary" | Cut | Restates the page |
| Chat app permission | Moved to "Before you start", in bold | Happens outside the product, and fails silently |
| Order: connect before sharing | Added | Answers before connecting are lost; the reader needs this before the step, not after |

| From draft 2 | Decision | Reason |
| --- | --- | --- |
| "'Publish'. Copy the link." | Rewritten as a sentence with a "try it" step | The reader needs to know when they are done |
| The changes table | Turned into two sentences with the why | Two rows don't need a table; the reason ("people keep seeing the old version") is what makes it stick |
| No why anywhere | Added a clause where a choice matters | "Mark both as required so you don't get anonymous replies" |
| Neutral opening | Invitation at the start and at "try it" | Guiding voice at the two moments that matter; plain everywhere else |

By word count, draft 3 is close to draft 1 (about 90%) and nearly three times draft 2. Length is not what changed. Draft 1 spent its words narrating the screen and missed both silent failures (the chat permission, and answers lost before connecting). Draft 3 spends the same words on those, on the order of the steps, and on telling the reader when they are done. Draft 2 is shorter only because it dropped the why and the "try it" step.
