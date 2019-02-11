# Terraform AWS Code Pipeline

This project borrows and merges concepts and cloudformation templates from [Integrating Git with AWS CodePipeline](https://aws.amazon.com/blogs/devops/integrating-git-with-aws-codepipeline/) and [Continuous Infrastructure Delivery Pipeline with AWS CodePipeline, CodeBuild and Terraform](https://ruempler.eu/2017/02/26/continuous-infrastructure-delivery-pipeline-aws-codepipeline-codebuild-terraform/)

[BitbucketToS3PipelineSource.template](./BitbucketToS3PipelineSource.template) uses AWS Quickstart to integrate an external git repository (ex: Bitbucket) as a [AWS CodePipeline](https://console.aws.amazon.com/codesuite/codepipeline/home?region=us-east-1) source to kick off builds.

[TerraformPipeline.template](./TerraformPipeline.template) sets up a pipeline in AWS CodePipeline to trigger on updates to the source bucket defined by [BitbucketToS3PipelineSource.template](./BitbucketToS3PipelineSource.template). The convention is to run a `terraform plan` then `terraform apply`, passing the `polan.out` between stages. This process may be updated to include a manual approval between the `plan` and `apply` stages.
