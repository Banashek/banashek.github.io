---
layout: post
title: "How to loop over user input in clojure"
date: 2015-08-15
date-day: 15th
date-month: August
date-year: 2015
categories: clojure
---
So I picked a programming challenge as a way to start learning clojure the other day. Most programming challenges take an input, and produce some output ("calculate x whatever numbers").

So I started of with `lein new app derp` to set up my derp project.

Being new to functional programming and clojure, my next step was to google, but nothing really seemed to work out the way I wanted.

What I had wanted was a solution where I could loop over user input and return relevant results until the user entered 'q' to quit the application.

After trying a few things, here is my solution:

{% highlight clojure %}
(ns derp.core
  (:gen-class))

(defn validate-input [in] (if (not= in "q") in))

(defn input []
  (if-let [v (validate-input (read-line))]
    (do
      (println v)
      (recur))
    "Exiting"))

(defn -main []
  (input))
{% endhighlight %}

The input function loops over the user input (which is validated by the validate-input function to check that it is not 'q').

If the input is not 'q', then it is bound to the variable v and printed back out (but you most likely will want to do something else with the data).

This will work either in a `lein repl` or a `lein run` or a `lein trampoline run`.

Figure I would share this for anyone else going through the same issue.

-Jon
