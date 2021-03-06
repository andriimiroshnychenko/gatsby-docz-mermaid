# Gatsby Docz with Mermaid

## Setup

```sh
$ yarn # npm i
```

## Start developing

```sh
$ yarn dev # npm run dev
```

## Build

```sh
$ yarn build # npm run build
```

## Serve built app

```sh
$ yarn serve # npm run serve
```

## Deploying with Pulumi to S3 with authentication

- [Install Pulumi](https://www.pulumi.com/docs/get-started/install/).
- [Install AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html) and configure your credentials. 
- Configure the `Pulumi.prod.yml` file.  
  - aws:region  
    The AWS region to create the resources. 
  - site:dir  
    The site files directory, (in case of this project, the site files are built in `public` folder).
  - site:name  
    The site name for creating the resources (it needs to be in slug format).
  - site:log-requests  
    Set to true if you want to save the CloudFront request logs (it will create a S3 Bucket for it).
- Build your site files.  
- Compress the lambda function.  

```sh
$ yarn lambda:build # npm run lambda:build
```

- Deploy

```sh
$ yarn deploy # npm run deploy
```

- Choose `Yes` and wait for the resources creation, it will take a while so be patience.
- When the process is finished you need to link the Auth Lambda Function with your CloudFront distribution manually (deploy to Lambda@Edge), because there's a Bug in AWS that doesn't permit to do such thing through its API, you can read more about in this [thread](https://forums.aws.amazon.com/thread.jspa?messageID=925495).

This deploy setup was made based on this [article](https://douglasduhaime.com/posts/s3-lambda-auth.html). 
