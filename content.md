# Ruby Sandbox

* Table of Contents
{:toc}

As you are learning, and especially as you are trying to solve the upcoming Ruby Gym exercises, it can be very helpful to have a place to experiment with Ruby code. 

We have created an un-graded repository for you to experiment with Ruby in a Codespace VSCode environment. The sandbox we prepared offers additional functionality beyond the embedded REPLs in our Ruby lessons. With our `appdev-projects/ruby-sandbox` repo, you have the ability to:

* create as many Ruby `.rb` files as you like,
* run the Ruby files in the terminal,
* save your work to GitHub by committing and pushing, and
* experiment in the interactive Ruby `irb` terminal environment.

Have a look through these sections for details about each of these items, and keeping the workspace bookmarked so you can open it whenever you need a place to experiment or store your knowledge.

## Launch and fork the repo

Click the load button below open the Grades interface. This is **not a graded assignment**, and the load button will just give you access to fork the repo.

LTI{Load Ruby Sandbox}(https://grades.firstdraft.com/launch)[S9ymPy6WCsn18gLbByVbZQ7k]{vfdtzJb5bLYqYwuqgeRKpc5d}(0)[Ruby Sandbox]

Recall, when you load a Grades project, you'll arrive at a page with several links. Your first step will be to open the link that looks like `appdev-projects/<project-name>` (in this case `appdev-projects/ruby-sandbox`) in a new tab. Once you've done so, click the link for "Project Setup" for a reference on **forking**, and the link for "Codespaces" for a reference on starting a Codespace and getting to work on **your fork** of the repo:

<!-- ![](/assets/launch-grades-project-1.png) -->
![](https://res.cloudinary.com/dmxgp9oq2/image/upload/v1686700730/launch-grades-project-1_urrcyo.png)

## Creating Ruby files

Once you have the repo forked and your Codespace setup, you should see a blank file explorer. You can right-click in the explorer panel and select "New File...", then give a file name; in this case we'll just call it `howdy.rb`. 

* Do not put any spaces in the filename, use underscores for longer names: `my_long_filename.rb`. 
* The file extension `.rb` is important, this tells the terminal and VSCode that this is a Ruby file and should be interpreted as such.

<!-- ![](/assets/ruby-scratch-1.png) -->
![](https://res.cloudinary.com/dmxgp9oq2/image/upload/v1687285925/ruby-scratch-1_neahsi.png)
{: .bleed-full }

Once you create the file `howdy.rb`, it should open automatically in the top panel (the code editor). Now you can type some Ruby into this file, exactly like you would if it were one of the embedded REPLs:

<!-- ![](/assets/ruby-scratch-2.png) -->
![](https://res.cloudinary.com/dmxgp9oq2/image/upload/v1687285925/ruby-scratch-2_fbviaa.png)
{: .bleed-full }

## Running Ruby files in the terminal

We no longer have a "Run" button as we did for our REPLs to send the code you write in the editor to a Ruby interpreter. Instead, you will run each file directly in the terminal by typing:

```
ruby howdy.rb
```

<!-- ![](/assets/ruby-scratch-3.png) -->
![](https://res.cloudinary.com/dmxgp9oq2/image/upload/v1687286147/ruby-scratch-3_cgdgmh.png)

This will ingest the given file and run it in a Ruby interpreter, which is exactly what was happening under the hood when you were clicking "Run" on the REPLs.

To re-run the command, you can use the <kbd>Up</kbd> and <kbd>Down</kbd> arrow keys to look at the history of all commands you've run in a particular terminal. If you don't want to type out `howdy.rb` (or any other file name), just begin typing it (e.g. `ho`) and then press <kbd>Tab</kbd> on your keyboard to finish the line. Use tab completion!

You can run the `ruby howdy.rb` command as many times as you like, and you will see the output of any `pp` print statements from your file in the terminal. **However**, there's a better way to experiment with your code than just running the file many times; with the interactive Ruby terminal environment: `irb`.

## Experimenting in an `irb` terminal

The `irb` interactive Ruby terminal environment is available in all of our Codespaces, including the `ruby-sandbox`. Simply type

```
irb
```

into the terminal to begin a fresh session. 

You will see the command prompt change from `%` to `3.2.1 :001 >` (`3.2.1` for the Ruby version that our projects are setup with):

<!-- ![](/assets/ruby-scratch-4.png) -->
![](https://res.cloudinary.com/dmxgp9oq2/image/upload/v1687286240/ruby-scratch-4_tuavi2.png)

The terminal can now be treated as a line-by-line Ruby interpreter! That means you can create variables and write code to explore and experiment.

<!-- ![](/assets/ruby-scratch-5.png) -->
![](https://res.cloudinary.com/dmxgp9oq2/image/upload/v1687286418/ruby-scratch-5_uh3wa2.png)

Every time you start an `irb` terminal, it does not know anything about the variables or other code in your current editor. You can type things in manually, or you can copy-paste from your editor to the `irb` terminal to check the behavior. **This is an extremely powerful way to explore your code.**

You should be typing code into the `irb` terminal _a lot_ as you work through various exercises, rather than just typing code in the editor and running it over and over by clicking the "Run" button on a REPL or typing `ruby name_of_file.rb` into the sandbox terminal. 

**Note: You cannot run `ruby name_of_exercise.rb` in an active `irb` terminal. You will need to type `exit` to return to the normal terminal environment with the `%` command prompt**:

<!-- ![](/assets/ruby-scratch-6.png) -->
![](https://res.cloudinary.com/dmxgp9oq2/image/upload/v1687286814/ruby-scratch-6_nrtuvw.png)
{: .bleed-full }

Even better, use the `+` icon in the terminal panel to keep a second, normal terminal open. A great way to work is having one terminal dedicated to running the file and a second terminal dedicated to `irb`, and navigating between the two terminals as needed.

## Saving your work to GitHub

When you have some work in a file you want to save, make a git commit and push your work to save it on your fork of the `ruby-sandbox` repository on GitHub. This will save your work forever, in case the Codespace gets deleted. You should be committing and pushing a lot! Fill your `github.com/<your-username>/ruby-sandbox` repository with lots of `.rb` files as you work through the Ruby lessons and Ruby Gym exercises. 

In our short example here, your commit message could be "howdy.rb file says hello". With that, you can go ahead and create another `.rb` file and begin working there. It's a good idea to make separate commits for individual files that you create.

Follow the instructions in our [git workflow manual for the steps to commit and push](https://learn.firstdraft.com/lessons/50).

## Bookmark the sandbox

You can and should bookmark your Codespace for the `ruby-sandbox`, so that it:

* doesn't get deleted, and
* is easy to find when you want to re-open it.

The sandbox will boot up very quickly if you keep it bookmarked.

To do so, navigate to [your GitHub Codespaces dashboard at github.com/codespaces](https://github.com/codespaces), scroll down to find the Codespace (look for `<your-username>/ruby-sandbox`), click the `...` menu, and select "Keep codespace":

<!-- ![](/assets/ruby-scratch-7.png) -->
![](https://res.cloudinary.com/dmxgp9oq2/image/upload/v1687287463/ruby-scratch-7_i6dnwi.png)

Now, anytime you want to re-open the space, you can just navigate back to the dashboard and select the `...` menu > "Open in" > "Open in browser".

----
