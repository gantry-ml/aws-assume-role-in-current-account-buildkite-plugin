# AWS Assume Role in Current Account Buildkite Plugin

A Buildkite plugin to assume an IAM role in the account that your buildkite agent is running in. 
You can specify a role either by a role name, or full ARN. If an ARN is not supplied, the current account ID is retrieved with a call to `aws sts get-caller-identity` and the full ARN is constructed.

## Example:

```yml
steps:
  - command: "make deploy"
    plugins:
      - gantry-ml/assume-role-in-current-account
          role: "my-deployment-role"
          duration: 300 # duration in seconds that the token will be valid. default: 900
          region: us-east-1 # optional
```

## Configuration

### `role` (required, string)
The role name or ARN to assume.  If an ARN is not supplied, the current account ID is retrieved with a call to `aws sts get-caller-identity` and the full ARN is constructed.

### `duration` (optional, string)
The duration that the assumed credentials will be valid. 
> Default: 900 (15 minutes).

### `region` (optional, string)
Sets `AWS_REGION` and `AWS_DEFAULT_REGION` before assuming the role.
> Default: null
