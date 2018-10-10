In the real world, beside your production system you should have a test system that is technically identical to the production system. In the past that was usually a pain point, because it meant to buy and maintain identical hardware. But that pain has gone in the time of cloud computing. 

In case of firebase that only means that you deal with different projectIds in your settings. That is the only difference, which ensures that you get meaningful results when test on the testing system. 

You need to be sure which concrete version is runnning on production and which one is on the test-system. For that reason I am a big fan of Continous Deployment using GitLab Pipeline and a feature branch strategy with a dev and production branch used for deploymenxts to the test and production system. 

That means that there is a branch called `develop`, which is, as soon as somebody pushes changes to that branches, automatically deployed to the test system. And there is a branch called `master` that goes automatically to the production system.

To use this, you need gitlab. Gitlab will automatically start a so called pipeline when a push comes to a repository under control. That can also be mirrored from github for example. If you have a mirrored repository where GitLab pulls from, you may need to enable pipeline triggering in your project's Settings > Repository > Pull from a remote repository > Trigger pipelines for mirror updates.

But to make this work you need to define environment variables FIREBASE_DEPLOY_KEY and FIREBASE_PROJECT_ID, where FIREBASE_PROJECT_ID is the firebase project to deploy to and the FIREBASE_DEPLOY_KEY is a access token created using the command line: `firebase login:ci`

Nice Article about it: https://medium.com/evenbit/automatically-deploy-to-firebase-with-gitlab-ci-546f194c44d8 

