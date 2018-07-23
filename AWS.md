### IAM Policies
These step will allow you to create the necessary policies for all required ansible commands.
Repeat each for all files in `docs/aws_policies`.

1. Click [Policies](https://console.aws.amazon.com/iam/home#/policies)
1. Click `Create Policy`
1. Find `Create Your Own Policy`
1. Click `Select`.
1. Field `Policy Name`: Enter something like `ansible_{{file_name}}`.
1. Field `Policy Document`: Paste contents of `{{file_name}}` into field.
1. Click `Create Policy`.

### IAM Group

1. Click [Groups](https://console.aws.amazon.com/iam/home#/groups)
1. Click `Create New Group`.
1. Enter `ansible`.
1. Click `Next Step`.
1. Select all `ansible_*` policies (created above).
1. Click `Next Step`.
1. Click `Create Group`.

Also attach `AdministratorAccess`.

### IAM User

1. Click [Users](https://console.aws.amazon.com/iam/home#/users)
1. Click `Add user`.
1. Field `User name`: Enter `ansible`.
1. Check `Programmatic access`.
1. Click `Next: Permissions`.
1. Select group `ansible` (created above).
1. Click `Next: Review`.
1. Click `Create user`.
1. Save `Access key ID` and `Secret access key` to localhost.
1. Click `Close`.
