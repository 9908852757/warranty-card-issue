# One-time Gmail connection

The app sends the styled email and warranty PDF directly through Gmail. Google
requires an app connection for this. Being signed into Gmail in another tab is
not enough. The website itself stays static.

## 1. Host the app

Upload the hosting ZIP's extracted files to your GitHub repository and import
it in Vercel. Use the final HTTPS website address for the following setup.

## 2. Create the Google connection

1. Open [Google Cloud Console](https://console.cloud.google.com/) with the
   company account that will manage the app. Select or create a project.
2. Under **APIs & Services → Library**, enable **Gmail API**.
3. Open **Google Auth platform** and complete the app's branding and audience.
   Use **Internal** when the project belongs to your Workspace organization
   and every sender is in that organization. Otherwise use **External** and
   add the intended sender accounts as test users while testing. Follow
   Google's publication requirements before wider use.
4. Under **Data Access**, add these scopes: `openid`, `email`, and
   `https://www.googleapis.com/auth/gmail.send`.
   The app requests permission to send email and identify the sending address;
   it does not request inbox-reading access.
5. Under **Clients → Create client**, choose **Web application**.
6. In **Authorized JavaScript origins**, add the exact hosted origin, such as
   `https://YOUR-PROJECT.vercel.app`. Use your real URL, with no path or trailing
   slash. Add a custom domain separately if you use one. For local development,
   add `http://localhost:8765` and `http://127.0.0.1:8765` if needed.
7. Create the client and copy its **Client ID**, which ends in
   `.apps.googleusercontent.com`. Do not put the client secret in this app.

This app uses Google's browser popup/token flow, not a server callback.

## 3. Connect in the warranty app

1. Open the hosted app in Chrome or Edge.
2. Expand **One-time Gmail setup**, paste the public web client ID and save.
3. Click **Connect Gmail**, choose the sending account, and review Google's
   permission request. The From address appears after connection succeeds.
4. Enter a card, review it, and click **Send styled email + PDF**. This action
   sends the email immediately, including the PDF and both fixed CC recipients.

Each sender connects their own account. The ID is remembered in that browser.
For a shared preconfigured site, set `clientId` in `dist/gmail-config.js` before
rebuilding, or edit the `window.CetusGmailConfig` line in the standalone HTML.
The client ID is public configuration, never a password or access token.

## If Google refuses the connection

Check the exact website origin, Gmail API activation, audience/test-user list
and any company administrator restrictions. A file opened directly from your
computer cannot authorize this browser OAuth flow; use the hosted URL instead.

## Google references

- [Create a web OAuth client](https://developers.google.com/workspace/guides/create-credentials)
- [Configure consent and audience](https://developers.google.com/workspace/guides/configure-oauth-consent)
- [Browser token flow](https://developers.google.com/identity/oauth2/web/guides/use-token-model)
- [Gmail send scope](https://developers.google.com/workspace/gmail/api/auth/scopes)
- [Send messages with attachments](https://developers.google.com/workspace/gmail/api/guides/sending)
