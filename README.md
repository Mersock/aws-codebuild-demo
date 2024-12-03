# aws-codebuild



## Getting started

To make it easy for you to get started with GitLab, here's a list of recommended next steps.

Already a pro? Just edit this README.md and make it your own. Want to make it easy? [Use the template at the bottom](#editing-this-readme)!

## Add your files

- [ ] [Create](https://docs.gitlab.com/ee/user/project/repository/web_editor.html#create-a-file) or [upload](https://docs.gitlab.com/ee/user/project/repository/web_editor.html#upload-a-file) files
- [ ] [Add files using the command line](https://docs.gitlab.com/ee/gitlab-basics/add-file.html#add-a-file-using-the-command-line) or push an existing Git repository with the following command:

```
cd existing_repo
git remote add origin https://gitlab.com/true-dc-exist/poc/aws-codebuild.git
git branch -M main
git push -uf origin main
```

## Prerequisite
- ECR 
- Create [secrets manager](https://aws.amazon.com/secrets-manager/) (optional)
- Create [ECR] (https://aws.amazon.com/ecr/) (require)

## Attach permission for Code build role in IAM

### Permission for ECR (require)
```
{
	"Version": "2012-10-17",
	"Statement": [
		{
			"Effect": "Allow",
			"Action": [
				"ecr:CompleteLayerUpload",
				"ecr:UploadLayerPart",
				"ecr:InitiateLayerUpload",
				"ecr:BatchCheckLayerAvailability",
				"ecr:PutImage",
				"ecr:BatchGetImage"
			],
			"Resource": "arn:aws:ecr:ap-southeast-1:340752821097:repository/codebuild-demo"
		},
		{
			"Effect": "Allow",
			"Action": "ecr:GetAuthorizationToken",
			"Resource": "*"
		}
	]
}
```

### Permission for secret manager (optional)
```
{
	"Version": "2012-10-17",
	"Statement": [
		{
			"Sid": "Stmt1733198940592",
			"Action": [
				"secretsmanager:GetSecretValue"
			],
			"Effect": "Allow",
			"Resource": "arn:aws:secretsmanager:ap-southeast-1:340752821097:secret:nicely/codebuild-demo-9SPwfN"
		}
	]
}
```

