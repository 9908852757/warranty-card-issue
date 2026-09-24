# Cetus Warranty Card

A static browser app that creates the Cetus warranty PDF and sends the styled
email through the connected Gmail account, with the PDF attached automatically.
No server, database or client secret is required. Direct sending does require
one-time Google OAuth setup and a hosted website; see **Gmail Setup.md**.

## Use

1. Enter the client, vehicle, purchase and product details.
2. Type the warranty period in your own words.
3. Choose a sales person. Their contact details fill automatically and remain
   editable. Blank contact fields are optional.
4. Leave the invoice blank if it is not available. The invoice label and value
   are then omitted from both the card and email.
5. Connect the Gmail account you want to send from. Review the From, To, CC,
   message and PDF preview.
6. Click **Send styled email + PDF**. The app generates the current card and
   sends the formatted message with that PDF attached. No copying or pasting.

**Download PDF** remains available separately, including from the local HTML
file. Sending needs the hosted HTTPS app, internet access and Google permission.
You may need to reconnect Gmail after a refresh or when the connection expires.

Every email includes ashwathsuresh@bableather.com and
sales@cetusautomotives.com in CC. The sender is the Google account you connect;
selecting a sales person does not change it.

## Host with GitHub and Vercel

For the hosting ZIP, upload the extracted files at the repository root. The
included configuration uses Other, no build command and the root as output.
The development source project instead serves its **dist** directory.
Configure the Google connection for the final website address after hosting.

## Data and delivery

Client details remain in browser memory until Send is clicked. The app sends the
message and attachment directly to Google's Gmail API. Access tokens are held
only in memory, never in files or browser storage. Only the public OAuth client
ID may be saved as a local browser preference.

The Send button is disabled during delivery and after confirmed success for the
same details. The app never retries sending automatically. If a connection
failure makes delivery uncertain, check Gmail's Sent folder before enabling
another attempt. These guards last for the current page session.

The supplied logo is embedded in the card. Warranty wording is preserved. PDF
text is a high-resolution image, so it is not selectable. The styled email uses
the logo hosted on the Cetus website; recipients may need to allow images.

## Source files

- dist/card-engine.js: card, email template, sales presets and fixed CC.
- dist/gmail-mailer.js: Google connection, MIME email and Gmail send request.
- dist/gmail-config.js: optional shared public OAuth client ID.
- dist/app.js: form and sending workflow.

Rebuild the standalone HTML after editing these source files. The HTML package
includes all local code, the logo and pdf-lib; Google's sign-in library loads
online only for Gmail connection.

## Validation

Card rendering, optional invoice, manual warranty text, message encoding,
attachment contents and simulated Gmail responses are checked locally.
Live Gmail authorization and sending require the owner's Google client ID;
no live send is claimed until that setup is completed and verified.

PDF generation uses pdf-lib; see PDF-LIB-LICENSE.md in the hosting ZIP.
