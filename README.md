# LeadCash: AI Lead-to-Cash Automation (n8n)
## Demo videos
1. Workflow canvas: [https://drive.google.com/file/d/1jkpO-FBg95oOE3QL69gEXdtj2zjOtYHk/view?usp=drivesdk]
2. Price question: [https://drive.google.com/file/d/1v08mbIScAEmOw6cX1_jn-gwCuRbH9_75/view?usp=drivesdk]
3. Booking request: [https://drive.google.com/file/d/12p-0uyQJ8D5IYjQyAkofpMu71XPg4VNP/view?usp=drivesdk]
4. Booking saved to sheet: [https://drive.google.com/file/d/1dTGuM6hrnmDe4R8u5ejdh0MgdMa-zBKR/view?usp=drivesdk]
  
A demo automation built for a fictional web agency. It captures leads, scores them with AI, routes them, follows up, and creates invoices when a deal is won.

Built on free tiers. Every tool can be swapped for a paid one.

## What it does
1. Lead fills a web form
2. Email is validated, duplicates are rejected
3. Company website is fetched and summarized by AI
4. AI scores the lead 0-100, and a code step sets the tier
5. Hot: CRM record, AI-drafted reply, human approval on Telegram, then Gmail
6. Warm: added to a 3-step follow-up sequence
7. Cold: logged only
8. Deal won: Stripe test invoice is created and emailed
9. Any failure sends a Telegram alert and is logged

## Workflows
- WF0 Error Handler
- WF1 Lead Intake (main)
- WF2 Enrich Lead (sub-workflow)
- WF3 Score Lead (sub-workflow)
- WF4 Follow-up Sequence (daily schedule)
- WF5 Deal Won Invoice (polls every 15 min)

## Stack
n8n Cloud, Google Gemini, Google Sheets, Airtable, Gmail, Telegram, Stripe (test mode), Cal.com

## Design choices
- AI output is validated by code, not trusted
- Retries and timeouts on external calls
- Website fetch fails gracefully
- Human approval before emailing hot leads
- Duplicate invoices prevented

## Notes
Demo project on sample data, not a client engagement.

## Support Agent (Telegram)

A customer messages a nail studio on Telegram. An AI agent answers questions about services and prices using a Google Sheet price list. It only offers services from that list. When a customer wants to book, the agent collects the name, service, date and time. A structured marker then triggers a check, and only then is the booking saved to a Bookings sheet and a confirmation sent. Non-text messages get a polite reply.

Known limits: no live slot check yet (double booking possible), no owner alert for large bookings, text only, and the service rule is enforced by the prompt, not by code.

By [Gaurav] | [gauravmiglani992@gmail.com]
