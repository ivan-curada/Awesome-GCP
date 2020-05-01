# Setting up CI/CD for ReactJS Single Page Apps using Cloud Build and Firebase

<https://www.crowdform.co.uk/blog/deploying-a-gatsby-site-to-firebase-with-google-cloud-build>

## Steps

### Prerequisites

- Install `firebase-cli` in codebase
  - `npm install -g firebase-cli`
- Create a GCP Project in GCP console/cli
  - `gcloud projects create [PROJECT_NAME]`
- Create a Firebase Project by associating the created GCP Project in Firebase console

### Setup Firebase

- Authenticate Firebase
  - `firebase login`
  - `firebase login --no-localhost` - if you're using GCP Cloud Shell
- Initialize Firebase Project
  - `firebase init`
  - Firebase CLI feature: `Hosting`
  - Existing Firebase Project: `[PROJECT_NAME]`
  - Output: `public`
  - Configure as a single-page-app?: `N`
  - Overwrite: `N`
- Build Application
  - `npm run build`
  - `gatsby build`
- Check if build is successful
  - `npm run serve`
  - `gatsby serve`
- Deploy to Firebase
  - `firebase deploy`

### Setup GCP

- Create Cloud Build Trigger
  - Create `[BUILD_NAME]`
  - Link the repository
  - Choose Trigger: `push to master`
- Copy Build Instructions `cloudbuild.yaml` to repository root

### Authorizing Firebase

```
You’ll notice from the YAML file that there is “ $_TOKEN” in the Firebase deploy command. With CloudBuild there is a feature called variable substitution that when the build runs these will be substituted with config specified in the build trigger. We will use this to pass the firebase authorization token so that the site can be deployed.

To retrieve your Firebase access token On your local machine and within the project directory run the follow command, this allows firebase to work with continuous integration systems and will return a token to be saved in the trigger settings.
```
- Retrieve Firebase access token
  - `firebase login:ci`
  - `firebase login --no-localhost`
- Go to Cloud Build Trigger > `[BUILD_NAME]` > Substitution Variables and paste the token
  - `_TOKEN :{firebase_generated_token}`

### Trigger Build

- push changes to repository
  - `cloudbuild.yaml`

## cloudbuild.yaml

``` yaml
steps: 
  - name: node:10.15.1 
    entrypoint: yarn 
    args: ["install"] 
  - name: node:10.15.1 
    entrypoint: yarn 
    args: ["add", "firebase-tools"]
  - name: node:10.15.1 
    entrypoint: yarn 
    args: ["build"] 
  - name: "node:10.15.1" 
    entrypoint: "./node_modules/.bin/firebase" 
    args: ["deploy", "--project", "$PROJECT_ID", "--token", "$_TOKEN"]
```