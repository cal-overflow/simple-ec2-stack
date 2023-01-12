# Basic EC2 Cloudformation stack
An example Cloudformation stack for provisioning
1. EC2 Instance
1. Auto-generated SSH Key for accessing the EC2 Instance
1. Security Group allowing incoming SSH access to the EC2 Instance

## Deploying

### CLI
You can deploy the stack via the [AWS SAM CLI](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/install-sam-cli.html). Once you have cloned the repository, run
```bash
$ sam deploy
```
By default, this will deploy the stack to the `us-east-1` region. You can change this value via the command line options or updating the value within the `samconfig.toml`.

### GitHub Actions
You can configure GitHub actions to deploy your stack whenever changes are made to the `main` branch. \
Although the workflow is already written, there are other steps required to have this deploy complete in a desired AWS account.

### 1. Create an IAM Role
In your AWS Account, create a new IAM Role with the permissions you deem necessary. This must include [Cloudformation](https://aws.amazon.com/cloudformation/). Refer to GitHub's docs for [Configuring OpenID Connect in AWS](https://docs.github.com/en/actions/deployment/security-hardening-your-deployments/configuring-openid-connect-in-amazon-web-services) for guidance.


### 2. Add essential secrets to your GitHub repository.

Add the following secrets via **Repository settings** > **Secrets** > **Actions**.

  - `IAM_ROLE_ARN` containing your IAM Role ARN from step 1.

### 5. Trigger a deploy
To trigger a deploy, simply commit changes to the `main` branch.
