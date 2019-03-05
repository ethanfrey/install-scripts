# Cloud Services

## AWS

Install [AWS cli](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html)

```shell
mkvirtualenv -p python3 aws
# workon aws
pip3 install awscli --upgrade
aws --version
```

Configure aws with your account

```shell
aws configure
```

Examples:

```shell
aws s3 ls
aws s3 sync s3://... /local/path
```