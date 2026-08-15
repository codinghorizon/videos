---
layout: default
title: "Your Frontend State Is Confusing Your Coding Agent"
permalink: /htmx-is-back-because-ai-agents-hate-frontend-state/
date: 2026-08-15
---

# Your Frontend State Is Confusing Your Coding Agent

Everything the finished picture puts on screen as code, syntax or a named behaviour,
chased to the project that publishes it. The video states no statistics, benchmarks,
prices or version numbers, so what needed sourcing here is the code itself: an attribute
that does not exist, or a template tag written in the wrong dialect, is the one factual
error a video like this can make.

## What htmx is, and what it does to a page

htmx describes itself as "a library that allows you to access modern browser features
directly from HTML, rather than using javascript". Its stated generalisation of HTML is
that any element can issue an HTTP request, any event can trigger one, any HTTP verb can
be used, and any element can be the target of the update rather than the whole window.

A request returns HTML, normally a fragment rather than a whole document, and htmx swaps
that fragment into the target element. The project frames this as keeping the developer
"firmly within the original web programming model".

This is the claim the whole video rests on, and it is the project's own description of
itself rather than an inference.

Source: htmx documentation, https://htmx.org/docs/

## The attributes shown on screen

Every `hx-` attribute rendered in a shot is in the published attribute reference.

| On screen | What the reference says it does | Beats |
|---|---|---|
| `hx-get` | issues a `GET` to the specified URL | 029 |
| `hx-post` | issues a `POST` to the specified URL | 008, 022, 060 |
| `hx-target` | specifies the target element to be swapped | 008, 022 |
| `hx-swap` | controls how content will swap in | 008, 022 |

`hx-target` takes a CSS selector, which is why `hx-target="#row-1"` addresses the row with
that id. `hx-swap` defaults to replacing the target's `innerHTML`; `outerHTML`, as used in
beats 008 and 022, replaces the target element itself, which is what makes a returned
`<tr id="row-1">` stand in for the row it replaces. Other documented strategies include
`beforebegin`, `beforeend`, `afterend` and `afterbegin`.

Source: htmx attribute reference, https://htmx.org/reference/

## The four server rendered stacks in beat 063

The video names Go templates, Django templates, Rails views and Phoenix templates, and the
shot renders one line of each. Each line is the dialect that project publishes.

**Go.** The range action is documented as `{{range pipeline}} T1 {{end}}`, so
`{{range .Items}}` is the correct opening form. `html/template` is documented as having
"the same interface" as `text/template` with automatic escaping added, so the syntax on
screen is right for HTML output as well as text.
Source: Go text/template package documentation, https://pkg.go.dev/text/template

**Django.** The built in `for` tag is `{% for item in iterable %} … {% endfor %}`, shown in
the documentation as `{% for athlete in athlete_list %}`. The form on screen matches.
Source: Django built in template tags, https://docs.djangoproject.com/en/stable/ref/templates/builtins/

**Rails.** `<%= render item %>` is valid shorthand. Passing a single model instance makes
Rails derive the partial from the model name, and the same shorthand renders a collection.
Source: Rails layouts and rendering guide, https://guides.rubyonrails.org/layouts_and_rendering.html

**Phoenix.** `<%= for item <- @items do %> … <% end %>` is a valid comprehension in HEEx.
The documentation also gives a newer attribute form, `:for={post <- @posts}`, which it
describes as the recommended approach for new code. The shot uses the comprehension form
because it is the one that reads as a template loop alongside the other three.
Source: Phoenix LiveView assigns and HEEx documentation, https://phoenix-live-view.hexdocs.pm/assigns-eex.html

## The HTTP status codes on screen

`200`, `403` and `500` appear in beats 021, 049 and 050 as ordinary response statuses:
success, forbidden, and server error. These are the standard registered meanings and are
used on screen with those meanings and no others.

## What is argument rather than fact

The video's five reasons are an argument about how coding agents behave, not a set of
measured results, and the shots are built so that none of them renders a figure that would
imply otherwise. Nothing on screen states a benchmark, a percentage, a survey result or a
count of anything beyond what the script itself enumerates.

Two on screen counts do appear, and both are counts of the video's own list rather than
external data: the ten files in beats 005 and 006 are the ten steps the script names one
by one, and the seven layers in beat 058 are the seven the script names in a single
sentence. Both are legible in the narration as it is spoken.

The following are the script's position and are carried as such:

- that coding agents struggle more than people do when a feature's true behaviour is
  spread across several files
- that agents reach for the largest pattern they have seen when given a blank frontend task
- that the amount of overbuilt frontend code in public repositories shapes what agents
  produce
- that server response assertions give an agent stronger feedback than mocked component
  tests
- that keeping a route, its validation, its database call and its template near each other
  reduces how much context an agent needs

These are stated as a view in the narration and are listed under **Not checked** in the
upload sheet rather than presented as findings.
