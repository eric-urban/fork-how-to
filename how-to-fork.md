# How to fork a GitHub repository

If you want to contribute to a GitHub repository where you don’t have write access, you will need to fork the repository. You don’t need to create a fork (and likely shouldn’t) if you have write access to the repository to merge commits. Regardless, if you want a copy of the repository as a starting point for your own project, then you should create a fork. 

Creating a fork is copying the original repository (upstream repo) to your own GitHub account. Your copy includes the files, branches, tags, and commit history up to that point. Pull requests and issues from the upstream repo are not included. Forks retain a reference to the upstream repo so you can get changes. 

Install and [Set up Git](https://docs.github.com/en/get-started/quickstart/set-up-git) if you want to follow along and complete the steps below.

## Fork the repo

Forking a repository is straightforward. Make sure you are signed into GitHub and go to the repo you want to fork. In this example, we'll fork the [AWS CLI repo](https://github.com/aws/aws-cli). Select **Fork** in the top right corner. 

![Fork repo icon](/media/fork-icon.png)

This will fork your own copy of the repository to your account. For example, if you forked from <https://github.com/aws/aws-cli>, then your copy is at <https://github.com/YOUR-ACCOUNT/aws-cli>.  

Just as the maintainers of the upstream repository can clone, branch, and merge changes in their repository, you can clone, branch, and merge changes in your own copy of the repository.

## Clone the repo

You could edit individual files and submit a pull request all without leaving GitHub. But if you are making changes across multiple files, you’ll want to download and edit files locally. 

Clone your repository to your local environment.

```
% git clone https://github.com/YOUR-ACCOUNT/aws-cli.git
% cd aws-cli
```

Add a remote reference to the upstream repository and merge its current ```develop``` branch. The [AWS CLI repo](https://github.com/aws/aws-cli) maintainers welcome pull requests via their ```develop``` branch. 

```
% git remote add upstream https://github.com/aws/aws-cli.git
% git fetch upstream
% git merge upstream/develop
```

Optionally you can confirm that you have references both to your repo (origin) and upstream.

```
% git remote -v

origin	https://github.com/YOUR-ACCOUNT/aws-cli.git (fetch)
origin	https://github.com/YOUR-ACCOUNT/aws-cli.git (push)
upstream	https://github.com/aws/aws-cli.git (fetch)
upstream	https://github.com/aws/aws-cli.git (push)
```

## Create a branch for your changes

Although you could submit a pull request upstream from your main branch, it’s a good practice to work in a new branch. 

```
% git checkout -b my-contribution
```

Make your changes. Add, update, or remove files. For example, edit [CONTRIBUTING.md](https://github.com/aws/aws-cli/blob/develop/CONTRIBUTING.md).

```
% git add CONTRIBUTING.md
% git commit -m "description of changes"
```

## Get upstream changes

Every so often you can fetch the latest commits from the upstream repo. This is optional and makes it easier for maintainers of the upstream repo to review your pull request.   

```
% git fetch upstream
% git rebase upstream/develop
```

## Push your changes

Changes in your branch need to be pushed to your GitHub repository before you can submit a pull request upstream. The response will include the URL where you can submit your pull request.

```
% git push origin my-contribution

remote: Create a pull request for 'contribution-dev' on GitHub by visiting:
remote:      https://github.com/YOUR-ACCOUNT/aws-cli/pull/new/my-contribution
```

If you close the terminal or otherwise lose track of the URL, you can find your branch at <https://github.com/YOUR-ACCOUNT/aws-cli/branches>. As needed, you can make additional changes in your branch before sending them upstream for review.

## Submit your pull request

Now you can create a pull request and submit your changes for maintainers of the upstream repo to review. 

1. Go to the URL provided when you pushed your changes. Following this example, you would go to <https://github.com/YOUR-ACCOUNT/aws-cli/pull/new/my-contribution> 
1. Confirm the branch that you are submitting and enter a description of the changes.

    ![Confirm base and forked branches](/media/create-pull-request.png)

1. Select **Create pull request** to submit your changes for review. 

Now you can move on to other fun projects while you wait for a response. 

## Delete the repo

When you no longer need a copy of the repository (for example, your pull request has been accepted), then you can delete your copy of the repository. Deleting your fork will not affect the upstream repository in any way. 

1. Go to your repository at <https://github.com/YOUR-ACCOUNT/aws-cli> and select **Settings**. 

    ![Repo settings menu](/media/settings-delete-repo.png)

1. In the **Danger Zone** section at the bottom of the settings page, select **Delete this repository**. 
1. Follow the instructions to confirm that you understand the action is irreversible. 

## More options

Often there are multiple paths to the same destination. Here are some fork options to consider.

### Fork with the GitHub CLI

The [GitHub CLI](https://cli.github.com/) brings GitHub concepts to the terminal. Some of the commands are more intuitive or provide shortcuts compared to standard git commands. For example, you can fork, clone, and add an upstream remote in one step with the ```gh repo fork``` subcommand. 

### Fork by editing upstream

You might want to propose a change in someone else’s repository, and don’t necessarily plan on making future contributions. You can create a fork by editing a file in the original repository. You might have even done this before without realizing that a fork was created for you. 

1. Go to the file you want to edit in GitHub. 
1. Select the pencil icon to open edit mode and make changes. 

    ![Pencil icon to edit the file](/media/edit-pencil-icon.png)

1. Enter your commit message and then select **Propose changes**.

Here’s what happens next in parallel:

- Your own copy of the repository is forked to your account. For example, if you forked from <https://github.com/aws/aws-cli>, then your copy is at <https://github.com/YOUR-ACCOUNT/aws-cli>. 
- A new branch with your commit is created in your repository. For example, <https://github.com/YOUR-ACCOUNT/aws-cli/tree/patch-1> 
- You are redirected to a URL where you can compare your changes with the original. 

As needed, you can make additional changes in your branch before sending them upstream for review. 

## More resources

- [Set up Git](https://docs.github.com/en/get-started/quickstart/set-up-git) 
- [Fork a repo](https://docs.github.com/en/get-started/quickstart/fork-a-repo#about-forks) 
- [Creating a pull request from a fork](https://docs.github.com/en/github/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request-from-a-fork) 
