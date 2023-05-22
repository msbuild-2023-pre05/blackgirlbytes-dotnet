# Lab 2.1 - The Web-based Editor

The web-based editor introduces a lightweight editing experience that runs entirely in your browser. With the web-based editor, you can navigate files and source code repositories from GitHub, and make and commit code changes. You can open any repository, fork, or pull request in the editor.

The web-based editor is available to everyone for free on GitHub.com.

The web-based editor provides many of the benefits of Visual Studio Code, such as search, syntax highlighting, and a source control view. You can also use Settings Sync to share your own VS Code settings with the editor. For more information, see "Settings Sync" in the VS Code documentation.

The web-based editor runs entirely in your browser’s sandbox. The editor doesn’t clone the repository, but instead uses the GitHub Repositories extension to carry out most of the functionality that you will use. Your work is saved in the browser’s local storage until you commit it. You should commit your changes regularly to ensure that they're always accessible.

## Exercise 1 - Making a simple change

In this exercise, we'll make a simple change to a file in our repository. We'll also show how you can link your work to an issue using built-in extensions and work with pull requests.

1. Navigate to the Code tab of your repository
2. Press the `.` key on your keyboard. Note the URL change as we go to github.dev.
3. Spend a few minutes familiarising yourself with VS Code running in the browser.
    <details>

    In particular, make note of what you can and can't do:
    - You can navigate through folders in the repository and edit files
    - You're able to use _some_ extensions
    - You can view and work with GitHub issues and pull requests
    - You can't run or debug your code
    - You can't use the terminal
    </details>

4. Click on the Extensions icon on the Activity Bar (to the left) to bring up the extensions view. Note the extensions that have been installed.
5. Now click on the GitHub icon on the Activity Bar
6. In the Issues section on the lower half, expand `My Issues` to see all the issues you've created.
7. Find the `📝 Change page title` issue
8. Hover over the issue and click the → button to starting working on it. When prompted to name the new branch, choose a meaningful name.
    <details>

    When you click this button, Two things will happen:
    - A new branch will be created for your repository
    - The web editor will reopen, switched to the new branch
    </details>

9. In the Explorer, find `src/ReadingTime6.Web/Views/Home/Index.cshtml` and click the file
10. In the editor, make a change to the `It's Reading Time!` text so it reads `My Reading Time!`. Save your changes.
11. Click on the Source Control icon in the Activity Bar.
12. Click the `+` icon next to your changed file (this is equivalent to a `git add` command).
13. Write a commit message, then click the ✓ icon at the top.
    <details>
    This is equivalent to a `git commit` command. If you include the ID of the issue, prefixed by a `#` (e.g. `Fixes #3`), this commit will be automatically linked to that issue.
    
    If you're used to working locally, this feels like a commit and a push in one. It's important to remember with the web editor that we haven't cloned our code - we're working directly in the repository!
    </details>

 At this point, we've made a change, and we've committed it to our branch. The next thing we need to do is make a pull request.

14. In the same Source Control window, click the pull request icon ![pull request icon](images/web-editor-pr-icon.png) to the left of the ✓.
15. Add an appropriate title and description.
    <details>

    **Important:** Make sure you're committing from the branch you just created in your own repository to the main branch in that repository. While it's almost certainly going to be correct in this case, it's good practice to check. If you're working on a fork, the defaults may not be what you want!
    </details>

16. Click on the file in the `Compare Changes` section to see a diff of the changes you made.
    <details>
    Before clicking the `Create` button, look at the status bar at the bottom of the VS Code window. You should see the branch you're on, and GitHub in blue.
    </details>
17. Ok, now click `Create`.
    <details>
    Look at the status bar again, and see that you've been taken to review mode - there will be a Pull Request reference alongside the other pieces of information.
    </details>
18. Examine the view on the left, showing the details of the pull request. You can click on individual files to see the diff, and drill down into any commits that make up this pull request.
    <details>
    Note: This is a very simple example of a pull request you created yourself. However, this is the same view you will get if you use the web-based editor in the context of a pull request you're reviewing!
    </details>
19. Leave a comment either in the pull request details in the main window, or in the view on the left.
20. When you're ready, merge the change using either the `Merge Pull Request` button (then `Create Merge Commit`) in the main window, or the `Create Merge Commit` button on the left view.
    <details>
    There are different types of merge and they each have advantages and disadvantages. For this workshop we're just going to use the default.
    </details>
21. Click `Delete Branch...` then `Ok` in the prompt that appears at the top of the screen.
    <details>
    Note: You don't have to delete the branch if you don't want to! However, because we've merged the pull request into our main branch, we don't need it any more. It's good practice to remove branches when you don't need them, lest we end up with a pile of old code!
    </details>
22. Finally, look at the status bar at the bottom of the window. You'll see that we're back in our main branch with our changes merged.

> **What have you learned?**
> - How to [open a web-based editor](https://docs.github.com/en/codespaces/the-githubdev-web-based-editor)
> - How to work with the [GitHub Repositories extension](https://marketplace.visualstudio.com/items?itemName=GitHub.remotehub) in the web-based editor.
> - How to [submit a pull request](https://docs.github.com/en/codespaces/the-githubdev-web-based-editor#create-a-pull-request) from the web-based editor