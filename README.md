# test-auto-pr

some hardcoded PR values and changes

```js
export function activate(ctx: sourcegraph.ExtensionContext): void {
    const pullRequest: PullRequest = {
        destinationOwner: 'rvantonder',
        destinationRepo: 'test-auto-pr',
        destinationBranch: 'master',
        sourceBranch: 'my-feature-branch-ext',
        subject: 'PR Title',
        description: 'PR description'
    };

    const changesetCommit: ChangesetCommit = {
        sourceFiles: [
            { path: 'a/b/c/birb.md', content: 'henlo' },
            { path: 'README.md', content: '# test-auto-pr\nblah blah' }
        ],
        authorName: 'Rijnard van Tonder',
        authorEmail: 'rvantonder@gmail.com',
        commitMessage: 'commit message'
    };
    ctx.subscriptions.add(
        sourcegraph.commands.registerCommand('pr.issuePullRequest', () =>
            issuePullRequest({ pullRequest, changesetCommit })
        )
    );
}
```
