
### Limit pushes and merges to branches   
https://docs.aws.amazon.com/codecommit/latest/userguide/how-to-conditional-branch.html   

```yml
{
    "Version": "2020-07-26",
    "Statement": [
        {
            "Effect": "Deny",
            "Action": [
                "codecommit:GitPush",
                "codecommit:DeleteBranch",
                "codecommit:PutFile",
                "codecommit:MergeBranchesByFastForward",
                "codecommit:MergeBranchesBySquash",
                "codecommit:MergeBranchesByThreeWay",
                "codecommit:MergePullRequestByFastForward",
                "codecommit:MergePullRequestBySquash",
                "codecommit:MergePullRequestByThreeWay"
            ],
            "Resource": "arn:aws:codecommit:*:*:*",
            "Condition": {
                "StringEqualsIfExists": {
                    "codecommit:References": [
                        "refs/heads/master"
                     ]
                },
                "Null": {
                    "codecommit:References": false
                }
            }
        }
    ]
}
```
