To use this, you need gitlab. Gitlab will automatically start a so called pipeline when a push comes to a repository under control. That can also be mirrored from github for example.

But to make this work you need to define environment variables FIREBASE_DEPLOY_KEY and FIREBASE_PROJECT_ID, where FIREBASE_PROJECT_ID is the firebase project to deploy to and the FIREBASE_DEPLOY_KEY is a access token created using the command line: `firebase login:ci`

