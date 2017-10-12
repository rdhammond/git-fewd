# Design Pattern Basics

Design patterns are a tricky concept because there's no actual code involved with them. **A design pattern is a way of thinking.** You can write code to use them, but the pattern itself is just a concept. Think of it as the blueprint to your code's building. You don't want to run out there and fumble around with 2x4s trying to figure out how to build a wall, right? It's already been done before, and by tons of people. Just use the same method for wall-building everyone else does. That's the point of design patterns: you can recognize how different parts of your code do and should fit together, because it's been done so often there's already a word for it.

Design patterns almost *require* object oriented programming, since you're describing the way things fit together. Even if you were going to use a functional language, you'd still have to make a packet of data called a *struct* to pass around. (You don't have to worry about knowing that, and also don't ever do it. I'm saving you from yourself here.) The fact that we're dealing with ES5 Javascript, a prototyped language, makes things much more complicated. Happily, there's only a handful of patterns you'll use with pure front end development. You'll see a lot more once you get into full stack development, but for now, we'll focus on the ones you'll need for this class. Afterwards, we'll discuss some common patterns out in the wild. You probably won't need them right away, but the next time you see them, you'll (hopefully) recognize them.

## Common Front End Patterns

### MVC

MVC stands for **Model/View/Controller** and is a cornerstone of modern web design. It's really more of a full stack development thing, but you'll bump into it all over the place, so now's a good time to learn it. MVC separates code into three conceptual layers:

1) **Model.** This is where the actual data is stored. When you grab a user's info out of the database, and it has name, number, password, etc. all bundled up into one packet of info, that's a model.

2) **View.** This is the part the user sees. It's *almost* always going to be an HTML page. MVC thrives on having pages with generic "placeholders" that the controller can drop info into before it's shown. It's pretty much the entire point of its existence.

3) **Controller.** This is where the magic happens. The controller gets the right model, uses that info to fill out the view, then sends the result to the user.

By separating everything out into its own department, it suddenly becomes way easier to reuse code and make small changes. Remember, our job as coders is to avoid *spaghetti code.* With MVC, it's much easier to figure out what's wrong. Is the data incorrect? You want the model. Want to know why something's not showing up where it should? Check the controller. Page looks weird? Check the view. On top of this, if you suddenly want to change the way the site looks, you don't have to touch any other working code. Just change the view, and you're done! When code is put into separate areas like this, it's called **decoupled.** One of the goals of design patterns is avoid coupling. It's much easier to pop a module out and fix it then it is to go digging through an entire tangled codebase.

MVC is used over and over and *over* again in the web world. Angular (which you'll see later on) is MVC. Microsoft has its own flavor, MVC.NET. MVC is all the rage, and it's a really good idea to know what it means and how it works.

### Observer

Next to MVC, Observer is probably the most common pattern you'll encounter. You'll hear Observers called listeners, events, pub/sub (publication/subscription), and more. Once you know what to look for, the terms won't matter much.

An Observer does what is says: sits back and waits for a specific signal. This signal is called the **Subject.** When the observer sees the Subject change, it reacts---usually by running some code. This is a much bigger deal than it sounds. Consider this:

1) **Observers can be added and removed on the fly.** This is referred to as *subscription.* You can choose when and how long an observer should watch for a signal, even while your program is running.

2) **Multiple Observers can be hooked into a single Subject.** When a single Subject changes, *every* Observer watching it is triggered. You don't need to worry about calling each one in turn. Fire the Subject once, and you're done.

3) **Observers don't need to know about each other---even when observing the same Subject.** All they care about is Subject changes. Whatever the other Observers do is their business.

Here's an example: You have a program that needs to read from the keyboard, write what the user types to a file, and log every line to a database. You don't need to hunt down every single write and call the logging function afterwards. Make the log an Observer, and use file writes as the Subject. Whenever you write to a file, it'll trigger the Subject, and the Observer will handle logging. You don't have to call the same function over and over again. In fact, you don't even have to think about it anymore!

## Other Common Patterns

You probably won't need these patterns for this class. But, you'll probably hear them mentioned by other programmers, and it's good to know what they mean. Since patterns are tied with object oriented programming, we'll describe these in terms of **objects** (self-contained bundles of code) and **calls** (executing a function).

<dl>
<dt>Adapter</dt>
<dd>Takes information from a call, changes it around, and sends it to another call. You can use two previously unrelated objects without having to touch either one.</dd>
<dt>Iterator</dt>
<dd>Provides a handy way to walk through a list of items, i.e. an array. Tired of calculating indexes? Make an iterator object with the functionality you want, point it at your array, and never have to worry about typing out a math formula again.</dd>
<dt>Proxy</dt>
<dd>Pretends to be a certain kind of object, but does some extra work before the call gets forwarded to the *real* object. (i.e. "Talk to me first, and I'll pass your message along.") If you're familiar with **proxy servers**---a server that determines who gets to see certain web pages, like Twitter---it's the exact same concept.</dd>
<dt>Factory</dt>
<dd>An object that creates another object. Objects can usually handle their own creation, but sometimes it's useful to add some extra decisions on top of that, i.e. which *kind* of object to make. That's what a factory is for.</dd>
<dt>Singleton</dt>
<dd>A single object that is guaranteed to exist in one place for the entire run of the program and nowhere else. Anybody that wants to use that object can't create their own. They'll have to use the singleton instead.</dd>
<dt>Lock</dt>
<dd>In modern computing, a program can do several things at the same time. It's incredibly easy for a program to step on its own feet if there's a bunch of workers in the same section of code. A **lock** keeps everyone out of the call until you're finished with it.</dd>
<dt>Repository</dt>
<dd>A repository is a generic interface for storing and retrieving data---usually, a database. The advantage is that they all work the same way. It's just a matter of what each repository points to.</dd>
</dl>

Some of these have been simplified, of course, because there's a *lot* of high level computer science tied up in design patterns. But, this should give you the basic idea.

## When Not to Use Design Patterns

Once you learn patterns, you'll start recognizing them as you look at code. That's great! That's the whole point! You may even want to use a bunch yourself!

Slow down on that one.

Don't get me wrong, you should absolutely learn design patterns *and* employ them. But, don't start tossing design patterns into whatever you're working on assuming they'll automatically make things better. You can very easily put a square peg in a round hole if you're not careful, and using the wrong design pattern at the beginning can make life very difficult later on. Don't be *afraid* to use them----just show them the proper amount of respect. You't can't just toss in a few and call it a day.
