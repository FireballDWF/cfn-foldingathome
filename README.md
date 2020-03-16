# cfn-foldingathome
> CloudFormation template for Folding@home on AWS spot instances.

This template creates an AWS spot instance fleet for running the [Folding@Home](https://foldingathome.org/) client.
Folding@home is a computing platform to assist disease research, for instance to find a cure for the COVID-19 virus.
The template uses G4-type instances with NVIDIA TESLA GPUs.
Please only deploy it on accounts where you have the permissions to do so.

WIP Please check whether the solution works for you.

## Usage

### Launch from AWS Console

Use template S3 URL: https://cfn-foldingathome.s3.amazonaws.com/foldingathome.yml

| Region         | Create Stack              |
|----------------|---------------------------|
| US East (N. Virginia) `us-east-1` | [Launch Stack](https://us-east-1.console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/create/review?templateURL=https://cfn-foldingathome.s3.amazonaws.com/foldingathome.yml&stackName=FoldingAtHome) |
| US East (Ohio) `us-east-2` | [Launch Stack](https://us-east-2.console.aws.amazon.com/cloudformation/home?region=us-east-2#/stacks/create/review?templateURL=https://cfn-foldingathome.s3.amazonaws.com/foldingathome.yml&stackName=FoldingAtHome) |
| US West (N. California) `us-west-1`| [Launch Stack](https://us-west-1.console.aws.amazon.com/cloudformation/home?region=us-west-1#/stacks/create/review?templateURL=https://cfn-foldingathome.s3.amazonaws.com/foldingathome.yml&stackName=FoldingAtHome) |
|US West (Oregon) `us-west-2` | [Launch Stack](https://us-west-2.console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/create/review?templateURL=https://cfn-foldingathome.s3.amazonaws.com/foldingathome.yml&stackName=FoldingAtHome) |
| Asia Pacific (Hong Kong) `ap-east-1`| [Launch Stack](https://ap-east-1.console.aws.amazon.com/cloudformation/home?region=ap-east-1#/stacks/create/review?templateURL=https://cfn-foldingathome.s3.amazonaws.com/foldingathome.yml&stackName=FoldingAtHome) |
| Asia Pacific (Mumbai) `ap-south-1` | [Launch Stack](https://ap-south-1.console.aws.amazon.com/cloudformation/home?region=ap-south-1#/stacks/create/review?templateURL=https://cfn-foldingathome.s3.amazonaws.com/foldingathome.yml&stackName=FoldingAtHome) |
| Asia Pacific (Seoul) `ap-northeast-2`| [Launch Stack](https://ap-northeast-2.console.aws.amazon.com/cloudformation/home?region=ap-northeast-2#/stacks/create/review?templateURL=https://cfn-foldingathome.s3.amazonaws.com/foldingathome.yml&stackName=FoldingAtHome) |
| Asia Pacific (Singapore) `ap-southeast-1` | [Launch Stack](https://ap-southeast-1.console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/stacks/create/review?templateURL=https://cfn-foldingathome.s3.amazonaws.com/foldingathome.yml&stackName=FoldingAtHome) |
| Asia Pacific (Sydney) `ap-southeast-2` | [Launch Stack](https://ap-southeast-2.console.aws.amazon.com/cloudformation/home?region=ap-southeast-2#/stacks/create/review?templateURL=https://cfn-foldingathome.s3.amazonaws.com/foldingathome.yml&stackName=FoldingAtHome) |
| Asia Pacific (Tokyo) `ap-northeast-1` | [Launch Stack](https://ap-northeast-1.console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks/create/review?templateURL=https://cfn-foldingathome.s3.amazonaws.com/foldingathome.yml&stackName=FoldingAtHome) |
| Canada (Central) `ca-central-1` | [Launch Stack](https://ca-central-1.console.aws.amazon.com/cloudformation/home?region=ca-central-1#/stacks/create/review?templateURL=https://cfn-foldingathome.s3.amazonaws.com/foldingathome.yml&stackName=FoldingAtHome) |
|Europe (Frankfurt) `eu-central-1` | [Launch Stack](https://eu-central-1.console.aws.amazon.com/cloudformation/home?region=eu-central-1#/stacks/create/review?templateURL=https://cfn-foldingathome.s3.amazonaws.com/foldingathome.yml&stackName=FoldingAtHome) |
| Europe (Ireland) `eu-west-1` | [Launch Stack](https://eu-west-1.console.aws.amazon.com/cloudformation/home?region=eu-west-1#/stacks/create/review?templateURL=https://cfn-foldingathome.s3.amazonaws.com/foldingathome.yml&stackName=FoldingAtHome) |
| Europe (London) `eu-west-2` | [Launch Stack](https://eu-west-2.console.aws.amazon.com/cloudformation/home?region=eu-west-2#/stacks/create/review?templateURL=https://cfn-foldingathome.s3.amazonaws.com/foldingathome.yml&stackName=FoldingAtHome) |
| Europe (Paris) `eu-west-3` | [Launch Stack](https://eu-west-3.console.aws.amazon.com/cloudformation/home?region=eu-west-3#/stacks/create/review?templateURL=https://cfn-foldingathome.s3.amazonaws.com/foldingathome.yml&stackName=FoldingAtHome) |
| Europe (Stockholm) `eu-north-1`| [Launch Stack](https://eu-north-1.console.aws.amazon.com/cloudformation/home?region=eu-north-1#/stacks/create/review?templateURL=https://cfn-foldingathome.s3.amazonaws.com/foldingathome.yml&stackName=FoldingAtHome) |
| Middle East (Bahrain) `me-south-1` | [Launch Stack](https://me-south-1.console.aws.amazon.com/cloudformation/home?region=me-south-1#/stacks/create/review?templateURL=https://cfn-foldingathome.s3.amazonaws.com/foldingathome.yml&stackName=FoldingAtHome) |
| South America (São Paulo) `sa-east-1` | [Launch Stack](https://sa-east-1.console.aws.amazon.com/cloudformation/home?region=sa-east-1#/stacks/create/review?templateURL=https://cfn-foldingathome.s3.amazonaws.com/foldingathome.yml&stackName=FoldingAtHome) |

### Launch from CLI

Replace `KeyName`, `Subnets` and `Vpcid` values:

```sh
aws cloudformation create-stack \
  --stack-name FoldingAtHome \
  --template-url https://cfn-foldingathome.s3.amazonaws.com/foldingathome.yml \
  --parameters \
    ParameterKey="FoldingAtHomeTeam",ParameterValue="0" \
    ParameterKey="InstanceCount",ParameterValue="1" \
    ParameterKey="KeyName",ParameterValue="mykeyname" \
    ParameterKey="Subnets",ParameterValue="subnet-12345678\,subnet-56781234" \
    ParameterKey="VpcId",ParameterValue="vpc-abcdefgh"
```

### Access Web UI

Forward port 7396 from the instance to localhost (replace `public-ip` with public IP address of the instance):

```sh
ssh ubuntu@public-ip -L 7396:localhost:7396
```

Now access the sWeb UI from: http://localhost:7396/

### Installation paths

Folding@home configuration is output to`/etc/fahclient/config.xml` .
Folding progress log output is written to `/var/lib/fahclient/log.txt`.
Show status of the service with `systemctl status FAHClient` .

## Release History

* 20.3.16
    * Initial version

## Resources

 - [Folding@home COVID-19 efforts](https://github.com/FoldingAtHome/coronavirus)
 - [Manual installation for Folding@home](https://foldingathome.org/support/faq/installation-guides/linux/manual-installation-advanced/)
 - [Ubuntu cloud images locator](https://cloud-images.ubuntu.com/locator/ec2/)
 - [Installation Instructions for CUDA Toolkit 10.2](https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1804&target_type=debnetwork)

## Meta

Janne Kataja – [@jkataja](https://twitter.com/jkataja) – fistname.lastname at gmail

Distributed under the Apache License v2 license. See ``LICENSE`` for more information.

GitHub [jkataja/cfn-foldingathome](https://github.com/jkataja/cfn-foldingathome)


