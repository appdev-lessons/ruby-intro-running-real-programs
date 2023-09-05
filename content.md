# Running real Ruby programs

[Here is a video for this lesson](https://share.descript.com/view/VqZhkytZJvC). You should not rely entirely on the video. PLEASE READ the below lesson as you are going through the steps, since there is much more detail in the text than in the video.

The runnable code blocks within lessons here are nice because they allow us to dive right into experimenting with Ruby expressions.

But, to write real programs, we need to be able to write files that can be thousands of lines long. Here within a code block, it's already annoying to scroll up and down when a program gets longer than 10 lines!

Even more importantly, we need to be able to create _multiple_ files that all collaborate together when executing the program. And, we need to pull in gems — code written by other people that we want to use.

Also, sometimes we want to run a program _interactively_ — we want it to stop and wait for end user input, or we (the developers) want to poke around at the program while it is running to help debug.

And, of course, we want to save our code forever by making Git commits and pushing them to GitHub.com; something that we can't do from runnable code blocks here.

For all these reasons and a bunch more, we need to start using a real environment to write our Ruby program. Codespaces to the rescue!

## Set up Codespace

Since this is not a graded project, you can [head directly to the ruby-sandbox repository and fork it to your own account](https://github.com/appdev-projects/ruby-sandbox/fork).

Once you've created a fork, [set up a Codespace](https://learn.firstdraft.com/lessons/55#start-your-first-codespace).

## Creating Ruby files

Once you have the repo forked and your Codespace setup, you should see a blank file explorer. You can right-click in the explorer pane (left side) and select "New File...", then give a file name; in this case we'll just call it `howdy.rb`. 

* Do not put any spaces in the filename, use underscores for longer names: `my_long_filename.rb`. 
* The file extension `.rb` is important, this tells the terminal and VSCode that this is a Ruby file and should be interpreted as such.

<!-- ![](/assets/ruby-scratch-1.png) -->
![](https://res.cloudinary.com/dmxgp9oq2/image/upload/v1687285925/ruby-scratch-1_neahsi.png)
{: .bleed-full }

Once you create the file `howdy.rb`, it should open automatically in the top pane (the code editor). Now you can type some Ruby into this file, exactly like you would if it were one of the embedded runnable code blocks from the lessons:

<!-- ![](/assets/ruby-scratch-2.png) -->
![](https://res.cloudinary.com/dmxgp9oq2/image/upload/v1687285925/ruby-scratch-2_fbviaa.png)
{: .bleed-full }

## Running Ruby files from the terminal

We no longer have a "Run" button as we did for our runnable code blocks to send the code you write in the editor to a Ruby interpreter. Instead, you will run each file directly in the terminal by typing `ruby ` followed by the filename at the bash prompt in our terminal:

```
ruby howdy.rb
```

<!-- ![](/assets/ruby-scratch-3.png) -->
![](https://res.cloudinary.com/dmxgp9oq2/image/upload/v1687286147/ruby-scratch-3_cgdgmh.png)

This will ingest the given file and run it in a Ruby interpreter, which is exactly what was happening under the hood when you were clicking "Run" on runnable code blocks.

- To re-run the command, you can use the <kbd>Up</kbd> and <kbd>Down</kbd> arrow keys to look at the history of all commands you've run in a particular terminal.
- You don't have to type out all of `howdy.rb` (or any other file name). Instead, begin typing it (e.g. `how`) and then press <kbd>Tab</kbd> on your keyboard to finish the line. This feature is known as "tab completion".

**The above two shortcuts will save you _a lot_ of typing and frustrating typos; please build the habit of using them!**

You can run the `ruby howdy.rb` command as many times as you like, and you will see the output of any `pp` print statements from your file in the terminal.

Now, let's explore some of the benefits of running the program yourself from the terminal!

## Breaking up our code across files

Now that we have full control over our environment, one thing we can do is break up our code into multiple files. Once our programs start getting to be hundreds and thousands of lines long, this becomes essential to stay organized and be able to find things quickly.

In addition to `howdy.rb`, create a second file called `goodbye.rb`:

```ruby
# /goodbye.rb

pp "See ya later!"
```

Now, in `howdy.rb`, use the `require` keyword to execute the contents of `goodbye.rb` at the end of the program:

```ruby
# /howdy.rb

my_string = "Hello, world!"
pp my_string

require "./goodbye.rb"
```

The argument to `require` is the _relative path_ to get from `howdy.rb` to `goodbye.rb`. The `.` stands for the parent folder of `howdy.rb`, and since they are in the same folder, `./goodbye.rb` was enough to specify the location of the other file precisely.

If all goes well, when you now run `ruby howdy.rb`, you should see that both files are being executed:

```
"Hello, world!"
"See ya later!"
```

The ability to `require` other files in our programs is extremely powerful. In addition to letting us organize our code better, it also allows us to re-use code easily.

But best of all — `require` let's us use code that _other people_ wrote....

## Gems

Ruby includes a robust system that makes it shockingly easy to share code with each other.

-  First, we write our Ruby code.
-  Then, we organize it into a particular file/folder structure.
-  Then, we compress the folder and give it the extension `.gem`, e.g. `our_fancy_code.gem`.
-  Then, we post it to a community-run server called `rubygems.org`.

At that point, we've shared our code with the world, and any other Ruby developer can download it, `require` it, and they're off to the races.

Some day, we'll write and share our own gem with the world. But for now, we'll focus on _using_ gems that others have written.

There's a very helpful gem called Active Support that I use in almost every one of my projects. It extends the built-in Ruby classes like `Integer` and `String` with handy methods like `ordinalize` and `pluralize`. Let's install it and give it a try:

First, we need to download the gem from rubygems.org to our computer (or Codespace, in our case). Ruby includes a built-in bash prompt command for that, `gem install`:

```
gem install activesupport
```

Next, we must `require` it in our program. Active Support includes a bunch of files; to load them all, we say:

```ruby
# /howdy.rb
require "active_support/all"
```

Now, we can use Active Support methods. Try the `Integer` method `ordinalize`:

```ruby
1.ordinalize    # => "1st"
2.ordinalize    # => "2nd"
53.ordinalize   # => "53rd"
2009.ordinalize # => "2009th"
-21.ordinalize  # => "-21st"
-134.ordinalize # => "-134th"
```

And the `String` methods `pluralize` and `singularize`:

```ruby
"table".pluralize     # => "tables"
"ruby".pluralize      # => "rubies"
"equipment".pluralize # => "equipment"

"tables".singularize    # => "table"
"rubies".singularize    # => "ruby"
"equipment".singularize # => "equipment"
```

Awesome! We probably could have written these methods ourselves, but it would have take a while to get the details right. Why not borrow?

[You can read more about all the methods that Active Support adds here.](https://guides.rubyonrails.org/active_support_core_extensions.html)

Most importantly, we've now opened the door to **a whole universe of powerful code** that we can pull into our programs, via gems.

## Bundler

Usually, we end up with many gems in a project. It would be a pain if we had to `gem install` each one individually, especially if we (or a teammate) started working on a different computer.

Ruby includes a nice system called Bundler to make it easier to use multiple gems in a project. Here's how it works:

Create a file in your project called `Gemfile` (no extension). At the top of that file, add the following:

```ruby
# /Gemfile

source "https://rubygems.org"
```

Below that line, you can pull in as many gems as you want with the `gem` method. For example, below I pull in `activesupport`  and a couple of other gems I use in almost every project:

```ruby
# /Gemfile

source "https://rubygems.org"

gem "activesupport"
gem "awesome_print"
gem "pry-byebug"
```

(We'll talk about what the other two gems do shortly.)

Now, I can install all of the gems at once with one command:

```
bundle install
```

Once this command completes, a new file will appear called `Gemfile.lock`. This is a record of what versions of the gems you installed just now. You should never modify `Gemfile.lock` manually; you only modify `Gemfile`, and let `bundle` handle updating `Gemfile.lock`.

Great! Now all three gems are installed on our computer. We can `require` them in our program and get to work.

## Get string (`gets`)

We can make our programs much more interesting if we allow the users of the program to interact with them by supplying input. We can do this with the `gets` method (pronounced "get S", short for "get string"), which will pause the program and wait for the user to type something in the terminal and press <kbd>return</kbd>. The return value of the `gets` method will be a `String` containing what the user typed, which we can store in a variable and then process further like any other `String`.

For example, rather than saying "Hello, world!", let's have the computer say hello to the user by name instead. When you run this program, it will pause after saying `"What's your name?"` and you will have to type something in and press <kbd>return</kbd>. **Click on the terminal to put focus there**, and then you'll be able to type into it.

Try this out in `howdy.rb`:

```ruby
pp "What's your name?"

their_name = gets

pp "Hello, " + their_name + "!"
```

Great! Our first user input. However, you'll notice a couple of things. First of all, there's a `\n` sneaking into the input. [`\n` is an _escape character_ representing a new line](https://learn.firstdraft.com/lessons/113#escape-characters), and it's in there because of the <kbd>return</kbd> that is pressed to submit the input.

If you want to see the newline in action, we can use a different printing method called `puts` (pronounced "put S", short for "put string"). `puts` is actually the printing method that is used most when crafting the final output of terminal programs; as opposed to `pp`, which is used most for _making the invisible visible_ while debugging. Try switching:

```ruby
pp "Hello, " + their_name + "!"
```

to

```ruby
puts "Hello, " + their_name + "!"
```

and see how the output is different.

You can see that the quotes around the string are removed, which makes sense if you're actually displaying output to a user and not debugging — users should not know or care about the quotes around Ruby string literals. And the newline character causes a line break when a string is printed with `puts`, as it should.

Most of the time, we'll stick with `pp`, since it provides more details while debugging; but it's good to know that `puts` exists.

### gets.chomp

We almost never want to keep the `\n` that results from the <kbd>return</kbd> keypress that submits the user's input. Fortunately, the handy `.chomp` method does exactly what we need — if there's a `\n` at the end of a string, it will remove it; if there isn't, it does nothing. So, in practice, when we call `gets` we almost always tack a `.chomp` on to it immediately. [Read more about `.chomp` in our Ruby reference](https://learn.firstdraft.com/lessons/33#chomp). Try modifying the program to:

```ruby
their_name = gets.chomp
```

and see how the program behaves now.

Since our goal is building _web applications_, not _terminal applications_, we won't be using `gets` very much. But it's nice to know about.

## Experimenting with `irb` 

Ruby includes a wonderful tool for interactive experimentation known as Interactive Ruby (IRB). 

To try it out, run the following at the bash prompt:

```
irb
```

You will see the prompt change from `%` bash prompt to `3.2.1 :001 >` (`3.2.1` for the Ruby version that our projects are setup with):

<!-- ![](/assets/ruby-scratch-4.png) -->
![](https://res.cloudinary.com/dmxgp9oq2/image/upload/v1687286240/ruby-scratch-4_tuavi2.png)

The `3.2.1 :001 >` prompt means that you've launched the IRB application. Here, you can run one line of Ruby at a time, and it will show you the return value without you needing to `pp`:

<!-- ![](/assets/ruby-scratch-5.png) -->
![](https://res.cloudinary.com/dmxgp9oq2/image/upload/v1687286418/ruby-scratch-5_uh3wa2.png)

IRB is an example of a Read-Evaluate-Print-Loop (REPL) — many languages provide REPLs. They're called "loops" because once you've launched a REPL, they continue to run, executing your commands one by one, until you quit out — they won't shut down on their own.

To exit IRB, type the command `exit`. This will return you to the bash command prompt (`%`).

**Note: be aware of which prompt you are at. You cannot run `ruby name_of_exercise.rb` in an active `irb` terminal. You will need to type `exit` to return to the normal bash terminal environment with the `%` bash prompt**:

<!-- ![](/assets/ruby-scratch-6.png) -->
![](https://res.cloudinary.com/dmxgp9oq2/image/upload/v1687286814/ruby-scratch-6_nrtuvw.png)
{: .bleed-full }

Even better, use the `+` icon in the terminal tab to keep a second, bash prompt terminal open. A great way to work is having one terminal dedicated to running the file at the bash prompt and a second terminal dedicated to `irb`, and navigating between the two terminals as needed.

A few other very important notes:

- If you get into a weird state in IRB (e.g. you forgot the closing `"` for a string), you can always <kbd>Ctrl</kbd>+<kbd>C</kbd> to reset to a clean prompt.
- If the output of a command is taller than the terminal pane, it will stop and wait for you to step through it line-by-line or page-by-page.
    - Press <kbd>return</kbd> to advance by 1 line.
    - Press <kbd>space</kbd> to advance by 1 page.
    - Press <kbd>Q</kbd> to jump all the way to the end of the output.

## Byebug

When you launch `irb`, it doesn't by default have any connection to any existing Ruby file; it starts out a blank slate, without any variables or anything.

But sometimes, we'll want to interactively experiment with a program that we're in the process of writing. You could do this by copy-pasting each line of the file, one-by-one; but there's a much better way: Byebug.

First, we need to add and require the gem:

```ruby
# /Gemfile

source "https://rubygems.org"

gem "pry-byebug"
```

Create a new Ruby program called `debugger.rb`:

```ruby
# /debugger.rb

require "pry-byebug"

f = "Your lucky number is "

l = rand(100)

pp f + l
```

If you run this program, you should see an error occur on Line 9. Let's debug it interactively! Update the program with a call to `byebug` on Line 9:

```ruby
# /debugger.rb

require "pry-byebug"

f = "Your lucky number is "

l = rand(100)

byebug

pp f + l
```

Run this file and see what happens.

The program should attempt to run, but then it will get stuck at an IRB-like prompt:

```
[2, 11] in /Users/raghubetina/code/scratch/requires/test.rb
    2:
    3: require "pry-byebug"
    4:
    5: f = "Your lucky number is "
    6:
    7: l = rand(100)
    8:
    9: byebug
   10:
=> 11: pp f + l
(byebug)
```

The `(byebug)` is a prompt. This is like an `irb` session, but at the moment in time where the `byebug` appeared in the code (this is called a **breakpoint**).

That means you can poke and prod at your variables `f` and `l`, experiment, and figure out how to fix the error. Neat!

Once you're done prodding, you can `continue` to have it keep going with the program (until the next breakpoint — you can add multiple).

You can also `step` to move the breakpoint forward by one line.

This interactive debugger takes some getting used to, but is a powerful tool in our belt for **making the invisible visible**. 

## Saving your work to GitHub

When you have some work in a file you want to save, make a git commit and push your work to save it on your fork of the `ruby-sandbox` repository on GitHub. This will save your work forever, in case the Codespace gets deleted. You should be committing and pushing a lot! Fill your `github.com/<your-username>/ruby-sandbox` repository with lots of `.rb` files as you work through the Ruby lessons, Ruby Gym exercises, and perform experiments in the future.

In our short example here, "initial commit". With that, you can go ahead and create another `.rb` file and begin working there. It's a good idea to make separate commits for individual files that you create.

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

- Approximately how long (in minutes) did this lesson take you to complete?
{: .free_text_number #time_taken title="Time taken" points="1" answer="any" }
	
---
