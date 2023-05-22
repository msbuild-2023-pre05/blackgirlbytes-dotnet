# Lab 4 - GitHub Actions Basics

In this lab you'll get to know the basics of working with GitHub Actions.

## Exercise 1 - Adding a Workflow file

In this first exercise, you'll create a simple workflow using GitHub Actions.

1.	Using a web browser, access your lab repo that you have been using today.

1.	Click the **Actions** link on the toolbar.

    > You’ll see several popular workflows.

1. While you can start from scratch, click the **Configure** button for **Simple workflow**.

    > If you don't see it at the top, scroll/search for it.

1. Change the name from **blank.yml** to **simple.yml**.

    > Inside the editor you'll see lots starter YML to get you going. 

1. Now, inside the editor, change **line 3** from `name: CI` to `name: Simple`.

1. Now, take a moment to read the comments (they being with a `#` mark) and 'code' that explain what the workflow file will do when run.

1. If you look at the block of code from line 5 to line 14, you'll see three different ways for the system to start executing the workflow (see below). You're going to comment out lines **8** to **11**. 

    ``` YML  
    # Controls when the workflow will run
    on:
    # Triggers the workflow on push or pull request events but only for the "main" branch
    push:
        branches: [ "main" ]
    pull_request:
        branches: [ "main" ]

    # Allows you to run this workflow manually from the Actions tab
    workflow_dispatch:
    ```

    > By doing this you'll be able to iterate on the workflow file and only run workflows when you're ready. Once it's good, you can uncomment / adjust the other items.

1. When ready, click the **Commit changes ...** button.

1. Feel free to add an extended description. For simplicity, you'll commit directly to Main so just click the **Commit changes** button when ready.

1. Click the **Actions** link on the toolbar.

1. In the left bar, click **Simple** under *All workflows*.

1. Notice how a bar appears stating "This workflow has a workflow_dispatch event trigger." with a button to the far right.

1. Click the **Run workflow** button to see what options exist. With the *main* branch selected, click the **Run workflow** button.

    > After a couple of seconds, your workflow will show up in the list.

1. Pick you workfllow to watch it run by clicking the title hyperlink.

1. Examine the workflow run screen until it completes. Look at the build log? Do you see all the messages? Do you notice anything interesting?

1. Return to the **Actions** home page. 

1. Notice the fiter options above the **Run workflow** button. This makes it easy to find a specfic run by filtering by *Event*, *Status*, *Branch*, and/or *Actor*. Give it a try.

1.  When ready, move on to the next exercise.
   
## Exercise 2 - Adding Jobs and More Control 

In this exercise, you'll modify the workflow to use jobs and some other fun stuff.

1. the **Actions** home page, 

1. In the left bar, click **Simple** under *All workflows*.

1. Under the **Simple** title (which appears to the right of the *New workflow* button), click the hyperlink for **simple.yml**.

1. This takes you to the code view. At the top of the view, click the **pencil** icon to return to the workflow editor.

1. First delete all of the code below line 17. Doesn't it feel good to delete code? Your file should look like the following now:

    ``` yml
    # This is a basic workflow to help you get started with Actions

    name: Simple

    # Controls when the workflow will run
    on:
    # Triggers the workflow on push or pull request events but only for the "main" branch
    # push:
    #  branches: [ "main" ]
    # pull_request:
    #  branches: [ "main" ]

    # Allows you to run this workflow manually from the Actions tab
    workflow_dispatch:

    # A workflow run is made up of one or more jobs that can run sequentially or in parallel
    jobs:
    ```

1.  At line 15 add the following to add a checkbox option when starting a dispatch workflow to tell the workflow whether it should run job 3 or not. (**Note** the first line in the code snippet below, 'workflow_dispatch:', *already* exists in your workflow file as line 14; don't add a 2nd line. This is to help you get the indentation correct).

    ``` yml
    workflow_dispatch:
        # Inputs the workflow accepts.
        inputs:
        run-job-3:
            description: "Run job 3"
            required: true
            type: boolean
    ```

1.  Now add the following code snippet at the bottom of the file at about line 24 under the existing **jobs** line.

    ``` yml
    job-1:
        name: Job 1
        runs-on: ubuntu-latest
        steps:
        - name: Output for Job 1
        run: echo "Hello from Job 1. Run Job 3 equals ${{ github.event.inputs.run-job-3 }}" 

    job-2:
        name: Job 2
        runs-on: ubuntu-latest
        needs:
        - job-1
        steps:
        - name: Output for Job 2
        run: echo "Hello from Job 2"

    job-3:
        name: Job 3
        if: github.event.inputs.run-job-3 == 'true'
        runs-on: ubuntu-latest
        needs:
        - job-1
        steps:
        - name: Output for Job 3
        run: echo "Hello from Job 3"

    job-4:
        name: Job 4
        runs-on: ubuntu-latest
        needs:
        - job-2
        - job-3
        steps:
        - name: Output for Job 4
        run: echo "Hello from Job 4"

    ```

    > There's a lot of code but it's very simple. It basically let's you run four jobs at the same time. However, job 3 only runs if the user checks the checkbox (which you'll see in a moment) when manually starting the job.

1. When ready, click the **Commit changes ...** button.

1. Feel free to add an extended description. For simplicity, you'll commit directly to Main so just click the **Commit changes** button when ready.

1. Click the **Actions** link on the toolbar.

1. In the left bar, click **Simple** under *All workflows*.

1. Click the **Run workflow** button to see what options exist. You now have a new checkbox labled **Run job 3**. Select the checkbox and with the *main* branch selected, click the **Run workflow** button.

    > After a couple of seconds, your workflow will show up in the list.

1. Pick you workfllow to watch it run by clicking the title hyperlink.

1. Examine the workflow run screen until it completes. Look at the build log? Do you see all the messages? Do you notice anything interesting? Does the job visualization look like you expected?

1. Repeat the process. This time remove the check mark so that job 3 does **not** run.

Huzzah! :sparkles: you're done with this lab. Move on to the next **Actions** lab.
