# Rails/Slim/Temple nested captures demo

This Rails repository replicates [this bug](https://github.com/slim-template/slim/issues/898) between Rails/Slim and Temple and then demonstrates that [this change to Temple](https://github.com/judofyr/temple/pull/112) will not reintroduce it.

## Setup

First visit the [`Gemfile`](Gemfile) and uncomment the gem versions under this line:

```ruby
# 🚫 Using releases or git refs as of 21 December 2022 replicates the bug:
```

Then `bundle` and `rails server` and then `curl -s http://localhost:3000/posts| grep microcopy`. This will replicate the bug:

```html
<divtestyes<divtestyes <divtestyes class="<divtestyes<divtestyes <divtestyes class="">awesome microcopy</div>
```

Next, revisit the Gemfile and uncomment the gem versions under this line:

```ruby
# ✅ Using the latest releases shows the bug is no longer present:
```

`bundle`, `rails server`, `curl -s http://localhost:3000/posts| grep microcopy`, and note that the bug is no longer present:

```html
<div class="test yes">awesome microcopy</div>
```

Finally, return to the Gemfile and uncomment the gem versions under this line:

```ruby
# ✅ Using latest slim plus a branch of temple with https://github.com/judofyr/temple/pull/112
# reintroduced does _not_ reintroduce the bug:
```

`bundle`, `rails server`, `curl -s http://localhost:3000/posts| grep microcopy`, and note that the bug is still absent:

```html
<div class="test yes">awesome microcopy</div>
```
