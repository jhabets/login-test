# Setup 

## Node
Download and install the latest Node installer from [nodejs.org](https://nodejs.org/en/download/).

On my fairly new Windows install, the 14.15 version of the installer asked me for permission to install additional tools such as Python and Visual Studio Builder tools. I checked yes, which also adds Chocolatey.

## Deno

Deno is the next node.  I find deno-webview to be slightly easier to use than Electron.

```
choco install deno
deno --version
```

## AWS CLI

Use Chocolately to install the AWS CLI v2.  Close and reopen the terminal to see `aws` as a valid command.
```
choco install awscli
aws help
```

Configure AWS with your API key/secret.  I use us-west-2 as my default region.
```
aws configure
```

## Install AWS CDK

AWS CDK is a Cloud Development Kit that compiles code into Cloudformation templates that deploy AWS infrastructure.

[Getting Started with AWS CDK](https://docs.aws.amazon.com/cdk/latest/guide/getting_started.html)

```
npm install -g aws-cdk
cdk --version
```

You might need to change Execution Policies to allow cdk to run.  My first time running I received this warning: 
> "...\npm\cdk.ps1 cannot be loaded because running scripts is disabled on this system. For more information, see about_Execution_Policies at https:/go.microsoft.com/fwlink/?LinkID=135170"

I set my CurrentUser policy to RemoteSigned with:
```
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```


## AWS Amplify CLI

Install the command line tools for AWS Amplify, a framework for building full stack applications with web/mobile frontends and AWS backends.

```
npm install -g @aws-amplify/cli
```

Configure Amplify to use a new IAM user with AdminAccess

```
amplify configure
```

## Typescript

I'm slowly migrating from vanilla javascript to Typescript, being pushed along by Deno and AWS CDK and Svelte.

```
npm -g install typescript
```

## Svelte

Svelte is a framework for building web-components for webpages. It is similar to React and Vue, but has an upfront compile step that generates small javascript.

It's a bit easier for me to understand than React, so I'll be using it for webview based UI development.

Unlike the previous NPM installed packages, Svelte will be installed locally to the project instead of globally.  The script below will create a new project folder from the sveltejs/template git repo.

```
npx degit sveltejs/template my-svelte-project
cd my-svelte-project
npm install
```