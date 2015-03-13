Hi.  I'm `John Haugeland`, and I'm here to talk to you today about my idiot library `"Flocks."`

In this talk I'll tell you
 * why I `+ * prefer simplicity to features`,
 * talk about  `+ * why Flocks is different`,
 * explain `+ * what Flocks does`,
 * show you `+ * a brief example`, and then
 * describe `+ * where to find information` if you're interested.

.

----

.

# Why I prefer simplicity to features.

The state layer ends up being a large part of most applications.

Simplicity tends to lead to `more maintainable` software.

I believe that complexity in the state layer is pernicious, the way the price of electricity is: it costs you at the factory, at the shipper, at the store, and at the home.  It's not a one time cost.  My goal is to reduce that complexity by as far as I know how.

`Flocks` is my effort to cut that complexity towards zero.

.

----

.

# Why Flocks is different.

Flocks is an `application layer` for `+React`.  Flocks does the same class of job as Flux ... and Mori, Cortex, Ancient Oak, Fluxxor, Baobab, McFly, Delorean, Nimbus, Newton, Reflux, Fynx, and so on.

Flocks manages /at/ /least/ the `rendering state` of your application.  It can be convenient to use it to manage the complete `+application state`, and I often do.

The central goal of Flocks is `EXTREME SIMPLICITY`.  And I'm not kidding.  To get started there's only `two functions` and `+one data member` to learn, and then you're off to the races.  There are other tools in there too, but they can wait until they're useful.

Despite being simple, Flocks also gives you some things that Flux doesn't, such as centralization, atomicity, and transactionality.

.

----

.

# What Flocks does.

What flocks actually does is `straightforward`.

Flocks makes a closure we'll call "The Flocks Instance" `* "Flocks Instance" closure`, then `+ * hides your render state` in it, mounts and manages your root control `+ * mounts/manages root`, then returns an object with functions that update the state `+ * returns an update object`.

Most of Flocks is `hidden from you inside a mixin`, but it's written in a way that you can work directly with the datastructures if you want to.  All you do is write ` * Flocks.createControl` instead of `+ * ~~React.createControl~~`

A Flocks instance is created with a ` * React component` and a `+ * mount point`, and whatever initial data you want to start your control with.

`+{{mount code example}}`

You don't have to use the Flocks createClass decorator; it's just low noise, which is good in a lightning talk.  It's the plumbing mixin.

Calling that creator will return an object - the `Flocks Updater` - with some functions on it.  The only one I'll talk about today is "set", but there are a bunch of other useful things in there too.  Those functions are also available inside of `Flocks Controls` automatically.

We call that piece of render state in the closure the `+Flocks context`.  This encompasses what people generally use props, state, contexts, flux stores, and so forth to do.  The mindset is "if it gets rendered into the UI, then it's render state."  With that mindset, React fulfills its promise of being a dead simple, top down patch renderer for the DOM.

The Flocks Updater operates on the Flocks Context.  Set, predictably, sets a value on the flocks context.  And that's actually a complete setup; when you use set, Flocks will turn around and re-mount and re-render for you.  Case closed.  We're done.

.

----

.

# A brief example.

Using the Flocks Context from inside a control is simple: it's just `this.fctx` on any Flocks Control.

Using Flocks Updater functions like set is similarly simple.  Set, for example, is `+this.fset()`.

So honestly, it's this simple:

    `spinner widget code example`

As you can see there are two buttons and a number.

The number gets its value from the `+{circle the flocks context}` `+Flocks Context`.

Each button has an onclick which uses the `+{circle the two set functions}` `+Flocks Updater set function` to change the value.

And the rest is just handled by re-mounting and the React diffing algorithm.  Nothing to learn, nothing to do, nothing to implement, no patterns to restructure your code around.  No dispatchers, no actions, no events, no stores.  No relationships.  No binding.

Just set the data and let it play out declaratively.  Like a directed graph, or a spreadsheet.

It's super liberating.

.

----

.

# Where to find information

Wooo, I have a `propaganda site`!  It's `+http://flocks.rocks/ {make this colorful}`.

That has like dozens and dozens of
 * `three examples`.  And more planned.  Also the
 * `documentation` and a few
 * `introductory texts` which I plan to expand.

One of the examples - the site itself - is an
 * `isomorphic app`, soon to be a `+* --single-page-app--`, built in `+* gulp`, which transforms `+markdown to static html`, pipes it through `+* twemoji`, builds `+* sass`, `+* closure compiles`, `+* css uglifies`, pushes into `+* s3`, and serves from `+* cloudfront`.  The code is already on `+* github`, the site is running, and a step by step tutorial showing how to build this from the ground up is on the way.
 * `Tutorial (Promises, promises)`

I'm also on IRC in the currently empty `freenode #flocksjs` channel.

.

----

.

# What we learned

`... nothing `:D``

 * `* What is Flocks`
 * Why I `+ * prefer simple`
 * `+ * What makes Flocks different`
 * `+ * What Flocks does`
 * A `+ * Brief example`
 * and `+ * Where to find information`

.

----

.

`http://flocks.rocks` {make that colorful again}

I hope that was interesting.  Please enjoy your evening.