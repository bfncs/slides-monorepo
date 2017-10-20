# MAKE MONOREPO MONO AGAIN

----

![MAKE MONOREPO MONO AGAIN](./img/make_monorepo_mono_again.png)

---

## Status quo

----

The monorepo was created to solve two problems.

----

### DRY

Share code between multiple projects.

----

### Resilience

Do not destroy stuff you are not aware of.

*a.k.a.*: not be the pattern lib again.

----

### Technology

* Small, transpiled `npm`-compatible packages
* `lerna` to orchestrate linking and releasing (partly)
* shitload of roll-your-own-tooling

----

### Actually…

…this solved a lot of problems but created new ones.

---

## Monorepo Pain

----

`yarn link`

----

Versioning hell

![Whack a mole](./img/whack_a_mole.gif)

----

SemVer is hard to master and a false friend: if you do something wrong, stuff breaks.

----

### Poor Developer Experience

* No more hot reloading  <!-- .element: class="fragment" -->
* No more cmd+click to jump to imports <!-- .element: class="fragment" -->
* node_modules must be ignored in IntelliJ or it will crash <!-- .element: class="fragment" -->
* making changes in shared modules often means more than half of the time wrestling with the ecosystem <!-- .element: class="fragment" -->

----

### Poor outcome

* Webpack profile is fixed at dependency transpile time <!-- .element: class="fragment" -->
* No effective tree shaking <!-- .element: class="fragment" -->

Larger-than-needed artifacts sent to customers browser. This is needlessly giving away that free lunch.  <!-- .element: class="fragment" -->

----

Didn't we want to create a system that's:

* easy to change,
* ‎easy to maintain,
* easy to reason about,
* has a great DX and produces amazing UX?

---

![Let's do this!](./img/lets_do_this.gif)

----

![Doing what Dan Abramov says to do.](./img/doing_what_dan_abramov_says_to_do.jpg)


----

* Make monorepo mono again: move app-web to monorepo. Everything else is **stereo**.
* ‎Stop building npm packages, stop transpiling on the package level. It's just ES6 source code in files - you know what to do. <!-- .element: class="fragment" -->
* ‎Include shared code through Webpack's resolve config and Jest config for tests. It's easy. <!-- .element: class="fragment" -->
* ‎IntelliJ fully support's this. It's true. <!-- .element: class="fragment" -->
* ‎But what about versioning? <!-- .element: class="fragment" -->

----

##### Versioning vs. Testing

* Why did we want SemVer in the first place? To make sure nothing breaks! <!-- .element: class="fragment" -->
* Sounds like we should do testing, aye? <!-- .element: class="fragment" -->
* Snapshot tests are best-buy: cheap to write, good enough to have to opt in to changes willingly <!-- .element: class="fragment" -->

----

##### Pragmatic versioning

----

##### Patch or Minor change?

Just go ahead and do it!

----

##### Breaking change?

* If you can easily refactor ("find usages" ftw): just go ahead and do it.
* If this is too hard to do: copy-paste the module and add `-v2`.
* Yes, this might lead to versions piling up. Just like now, except we will see it and can react. But relax: there's no interest to pay!

----

##### Tooling

Stuff we already use every day:

ES6, Webpack, Babel, Jest, IntelliJ

----

[Madge](https://github.com/pahen/madge) is helpful to understand dependencies

----

If versions piling up will ever be a problem, we can add tooling that helps making outdated module usages more visible.

----

## Wanna try?

I made you a thing:

https://github.com/bfncs/js-monorepo-playground

----

## What's next?

1 - 2 week EE canvas!

----

### PROFIT!!!!!11111111111elf11

![Dilbert](./img/dilbert.gif)