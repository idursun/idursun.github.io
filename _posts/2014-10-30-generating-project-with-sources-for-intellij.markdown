---
layout: post
title:  "Generating a Scala project with sources for Intellij IDEA"
date:   2014-10-30 11:00:00
tags: scala sbt intellij
comments: true
---
I don't know exactly why but when I make a new scala project with intellij idea I cannot get scala sources attached. Here what I do in such case:

run `sbt` and the following commands:

   * `update-classifiers update-sbt-classifiers`
   * `gen-idea sbt-classifiers`

`gen-idea` here is a sbt plugin that generates intellij projects. You can activate it either by adding the following line to your `build.sbt` file in your project folder or the global `build.sbt` file which is located in under `~/.sbt/0.13/plugins/`

   * `addSbtPlugin("com.github.mpeltonen" % "sbt-idea" % "1.6.0")`


Everything should work fine.
