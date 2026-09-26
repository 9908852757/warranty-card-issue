# Cetus Warranty Card

A static app for creating Cetus warranty PDFs and preparing styled Gmail emails.
No Google app registration, API connection, server or database is required.

## Use

1. Enter the client, vehicle, purchase and product details.
2. Select any combination of artificial leather (2 years), genuine leather
   (3 years) and electronics (1 year), or type the warranty period manually.
3. Choose a sales person. Their contact details fill automatically and remain
   editable. Blank contact fields are optional.
4. Leave the invoice blank to omit its label and value from the card and email.
5. Click **Download PDF**. The filename includes the client's name.
6. Click **1. Copy styled email**, then **2. Draft email**.
7. Gmail opens with the client, both CC addresses and subject already filled in.
   Paste into the body with Ctrl+V (Command+V on Mac), attach the downloaded PDF,
   check the From address, and send from Gmail.

The app supplies an empty draft body. Gmail may insert your usual signature.
Use normal paste and keep Gmail's **Plain text mode** off to retain the design.
If you change card details after copying, copy again and download the updated PDF.

The From address comes from the Gmail account opened in the browser. If you use
multiple accounts, expand **Choose a different Gmail account (optional)** and
enter the desired sending address. This selects an account; it does not change
the sales person on the card or create a sender alias.

Every draft includes ashwathsuresh@bableather.com and
sales@cetusautomotives.com in CC. The app never clicks Send.

## PDF attachment

Attach the PDF manually from Downloads or drag it into the Gmail draft. This
version uses a Gmail compose link and does not upload an attachment to Gmail.
PDF generation and the original warranty wording are unchanged.

## Host with GitHub and Vercel

Upload the hosting ZIP's extracted files at the repository root. Use Other,
no build command, and the root as output. The included vercel.json sets these.
The development source project instead serves its **dist** directory.

The standalone HTML also supports PDF generation locally. For the most reliable
clipboard behavior, use Chrome or Edge; the hosted version should use HTTPS.

## Data and source files

Client details stay in page memory until copied, downloaded or passed to Gmail.
Only the optional sending account address is stored as a browser preference.
No Gmail access tokens or passwords are requested or stored.

- dist/card-engine.js: card, styled email, sales presets and Gmail compose URL.
- dist/app.js: form, rich-text clipboard and draft workflow.
- dist/index.html and dist/styles.css: interface and styling.

Rebuild the standalone HTML after source edits. It includes the card logo and
all local code. The email logo loads from the Cetus website; recipients may need
to allow images. PDF text is a high-resolution image rather than selectable text.

See **Gmail Setup.md** for the email steps and **PDF-LIB-LICENSE.md** for pdf-lib.
