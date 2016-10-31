---
layout: page
title: Distribution
category: advanced
order: 8
lang: en
---

One big selling point of Elixir and Erlang is the ease with which you can distribute your application across many nodes.  In this lesson we'll look at just how to do that and how best to leverage this feature.

## Table of Contents

- [Node Basics](#quote)
- [Unquote](#unquote)
- [Distributed Tasks](#distributed-tasks)

## Quote

The first step to metaprogramming is understanding how expressions are represented.  In Elixir the abstract syntax tree (AST), the internal representation of our code, is comprised of tuples.  These tuples contain three parts: function name, metadata, and function arguments.

In order to see these internal structures, Elixir supplies us with the `quote/2` function.  Using `quote/2` we can convert Elixir code into their underlying representation:

```elixir
iex> quote do: 42
42
iex> quote do: "Hello"
"Hello"
iex> quote do: :world
:world
iex> quote do: 1 + 2
{:+, [context: Elixir, import: Kernel], [1, 2]}
iex> quote do: if value, do: "True", else: "False"
{:if, [context: Elixir, import: Kernel],
 [{:value, [], Elixir}, [do: "True", else: "False"]]}
iex(6)>
```