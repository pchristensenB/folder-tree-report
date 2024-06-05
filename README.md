# Folder Tree Report with Shared Links
Shows how a simple integration can be used to create an exportable folder tree report with shared links from Box. This repo is part of this Box Developer blog post: (https://medium.com/box-developer-blog/lets-talk-about-folder-tree-reports-50f85a0739ff)

Steps to setup including integration with Box (for testing this on a local web server with a developer token, see <a href='README_SIMPLE.md'>this page</a>

1. Create AWS lambda function

2. Deploy HTML and javascript to website

3. Configure Box Application and Web App Integration


## Create AWS Lambda function
For this you need a AWS account. https://aws.amazon.com/free/. AWS Lambda free tier is quite generous and allows 400K seconds of compute per month. See https://aws.amazon.com/lambda/pricing/

1. When you get to the AWS console, locate the Lambda page (type lambda in the search at the top) and 'Create function' - call it box-token-generator or similar. 

<img src="/img/lambda1.png" width="90%" height="90%">

2. In the repo folder 'box-token-generator' is both a zip file with the code and the actual code. If you want to use as is, upload the zip to the Lambda, if not you can change the code and zip and upload

<img src="/img/lambda2.png" width="90%" height="90%">

3. Add an API gateway trigger as below and copy the API endpoint as you will need it later

<img src="/img/lambda3.png" width="90%" height="90%">

<img src="/img/lambda4.png" width="90%" height="90%">

## Deploy to website
In this example I use GitHub Pages which allows you (free of charge) to serve HTML directly from a GitHub repo. https://pages.github.com/. Just setup the repo and add the files in the root of this repository to the pages repo and it will be available. 

The only change you need to make is to the index.html file. Line 43 has a URL placeholder, replace this with the URL from your AWS Lamdba function


## Configure Box Application and Web App Integration
For this you will need a Box account. If you have not already got one, sign up here for a free Box Developer account https://account.box.com/signup/developer

1. Once signed in goto https://developer.box.com and click the 'My Apps' in the upper right hand corner
2. This takes you to the developer console where you can create new app

<img src="/img/box1.png" width="90%" height="90%">

3. The app needs to be custom app, call it 'Folder Tree Report' or similar and fill out the details
4. Choose User Authentication (OAuth 2.0) as the authentication method
5. Make sure it has read and write scope

<img src="/img/box2.png" width="90%" height="90%">

6. Copy the client ID and client secret as you will need these later, save changes

<img src="/img/box4.png" width="90%" height="90%">

7. Copy the client secret and add it to the environment variable in your AWS Lamdba so you need to go back there for this

<img src="/img/env1.png" width="90%" height="90%">

<img src="/img/env2.png" width="90%" height="90%">

Configure the Web App Integration back in the Box Developer Console
1. Click the 'Integrations' tab and create new integration
2. Call it 'Folder Tree Report' or similar (this will be the name that will appear in the menu)
3. Set it to work on folders and requiring full permissions. 

<img src="/img/box6.png" width="90%" height="90%">

4. Set the callback URL to be your website  (eg. https://mygithubusername.github.io/index.html) and add '?clientId=THE_CLIENT_ID_YOU_CREATED_IN_SETTING_UP_THE_BOX_APP
5. Add call back parameters as below
6. Set it to open in a new tab

<img src="/img/box3.png" width="90%" height="90%">

You are now good to go. The integration will appear for folders and you can run it.. 
