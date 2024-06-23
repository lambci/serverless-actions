# 🐑 Serverless GitHub Actions 🚀

<img src="self-hosted.png" width="407" align="right">

Run hundreds of concurrent [GitHub Actions runners](https://docs.github.com/en/free-pro-team@latest/actions/hosting-your-own-runners)
without needing to maintain servers. See a demo of it in action at the AWS re:Invent 2020 session [No more idling](https://www.youtube.com/watch?v=JGdc2tnEhM4).

## What is it?

LambCI Serverless Actions enable you to run your GitHub Actions workflows on AWS Lambda and Google Cloud Run (Azure to come),
and container-based services such as AWS Fargate or AWS CodeBuild.

LambCI manages the connection to GitHub Actions and sends events over [Event Bridge](https://aws.amazon.com/eventbridge/) or [PubSub](https://cloud.google.com/pubsub). The serverless resources live in your cloud account, so you only pay while your workflows are running.

<img src="architecture.png" width="1024">

## Why would you want this over hosted GitHub Actions?

1. More (much moar) concurrency, no queueing 🚀
2. Per-second (or ms) billing, on your cloud account ⏱
3. Use IAM to access your cloud resources 🔒
4. Access to different instance sizes/capabilities (eg GPUs) 👩‍👩‍👧‍👦

## Why would you want this over another CI tool?

1. First-class citizen in the GitHub UI 🎩
2. No need to context switch or manage accounts elsewhere 🏠
3. Familiar, well-documented build specs 📃
4. Use thousands of plugins/actions from the GH community 🏙

## Project Philosophy

1. Don't reinvent the UI – stay in GitHub as much as possible. Organizations don't want yet-another tool to login to, and context-switching is a productivity killer.
2. Reducing build times is the goal. Serverless technologies are the means via fast start times and massive parallelization, but they can also be paired with vertical scaling (eg GPU CodeBuild instances).
3. All the software that runs your builds should be open-source. This includes the [GitHub Actions runner](https://github.com/actions/runner) and all the "glue"  necessary for invoking it (to be released soon).
4. Be a hub for all serverless-CI related resources. Serverless environments differ from traditional environments – typically they're more constrained in disk space. Provide guidance on how to operate in this context, including creating and curating Actions that work in these environments.


## Security

GitHub Action payloads are encrypted ([at GitHub's end](https://github.com/actions/runner/blob/e291ebc58ae5fcf82b8c25b8ea64ba3a2c073617/docs/design/auth.md)) using RSA public/private key pairs. You can control this key (if you wish) so LambCI will have no visibility into the workflow job or secrets. So long as the resources in your account have access to the private key, they can decrypt the payload and run the workflow jobs in isolation.

## When?

Soon, soon! Add your email to the list over at [LambCI's homepage](https://www.lambci.com) to get updates on when this will be available to try out.

## Other Questions?
Come and chat over in the [GitHub Discussions](https://github.com/lambci/serverless-actions/discussions) space. You can also reach out on Twitter at [@lamb_ci](https://twitter.com/lamb_ci).
