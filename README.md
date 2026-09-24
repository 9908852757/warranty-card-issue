# Cetus Warranty Card

This is a static, self-contained warranty-card app. It needs no backend,
database, API keys, dependencies to install, or build step.

## Use on your computer

Open index.html in Chrome or Edge. Enter the details, select a sales person,
and download the PDF. Open the Gmail draft, attach the downloaded PDF, then
send it from Gmail.

All five sales names are preset. Their phone, email and location fill in
automatically and remain editable. Phone and email may be left blank.

Every Gmail draft includes these CC recipients:
- ashwathsuresh@bableather.com
- sales@cetusautomotives.com

Gmail uses the signed-in account. For multiple signed-in accounts, use the
optional sending-address field and check the From address in Gmail.
The sales person selected on the card does not change your Gmail account.

## Host using GitHub and Vercel

1. Extract this ZIP.
2. Upload the extracted files to the root of your GitHub repository.
   Upload the files themselves, not the ZIP.
3. Import that repository into Vercel.
4. Choose the Other framework preset. Leave the build command empty.
   The included vercel.json sets the output directory to the repository root.
5. Deploy.

index.html is the entire app. Keep PDF-LIB-LICENSE.md with it.

## Details

The original warranty wording and black-and-gold landscape design are
retained. The downloaded one-page PDF uses the same image as the preview.
PDF text is rendered as a high-resolution image and is not selectable.

Client details are processed in the browser and are not saved by the app.
Opening Gmail passes the recipient, CC, subject and body to Gmail. You add
the PDF attachment manually. The app never sends an email automatically.

Only the app and its setup files are included here. Customer spreadsheets,
test records and the source Word document are not part of this package.

Vercel reference: https://vercel.com/docs/builds/configure-a-build
