---
title: "Introduction"
teaching: 10
exercises: 0
questions:
- "What is messy data?"
- "What is OpenRefine?"
- "Why use OpenRefine as part of your workflow?"
objectives:
- "Describe OpenRefine’s uses and applications."
- "Differentiate data cleaning from data organization."
- "Experiment with OpenRefine’s user interface."
- "Locate helpful resources to learn more about OpenRefine."
keypoints:
- "OpenRefine is a powerful, free and open source tool that can be used for data cleaning."
- "OpenRefine will automatically track any steps allowing you to backtrack as needed and providing a record of all work done"
---
# Lesson

## "Messy data"

Data needs to be consistent in a lot of ways so that you can work with it. The most obvious way to create consistency is by 
formatting your data so that columns contain data for one variable of one data type and rows contain data for one observation (see the 
lesson on [Spreadsheets](https://nesclic.github.io/spreadsheets-socsci-update/). But even if you have carefully structured your 
spreadsheet, errors can creep in that will cause you issues during analysis.

Today we are going to talk about some of the common things that make data "messy". These can include:
* Typos and different spellings
* Codes mixed in with full words
* Different people entering things in different ways
* Combining sources that use different codes that need to be reconciled
* Updating codes or names from an older data set

Most data is at least a little messy. You will probably spend a lot of time cleaning data, and it is an iterative process. Everyone who 
works with data has to deal with this; you are not alone!

## OpenRefine

OpenRefine is an open-source tool that was built to help people clean data. It provides functions that let you investigate your
data and then apply fixes to groups of data at the same time. You can also write short scripts to transform columns of data. 

While at first glance it may look like using spreadsheet software like Excel there are a few key things that make OpenRefine a good
data cleaning tool:
* You work with a new version of your data in OpenRefine, leaving your original untouched.
* OpenRefine lets you work with data as rows or records and columns, not just cells.
* OpenRefine keeps track of the steps you go through from import to export.
* You can "Undo" steps if you want to go back to an earlier version of the data.
* You can copy the steps and apply them to another dataset with the same structure.
* OpenRefine has features that let you cluster data that *looks* the same, simplifying clean up.
* You can use open refine to get data from other sources through APIs.

## Features

* Open source ([source on GitHub](https://github.com/OpenRefine/OpenRefine)).
* A large growing community, from novice to expert, ready to help. See Getting
  Help section below.
* Works with large-ish datasets (100,000 rows). Can adjust memory allocation to
  accommodate larger datasets.

## Before we get started

Note: this is a Java program that runs on your machine (not in the cloud). It runs inside your browser, but no web connection is needed.

Follow the [Setup]({{ site.baseurl }}/setup.html) instructions to install OpenRefine.

If after installation and running OpenRefine, it does not automatically open for you, point your browser at http://127.0.0.1:3333/ or http://localhost:3333 to launch the program.


## Getting help for OpenRefine.

[GREL Functions Wiki](https://github.com/OpenRefine/OpenRefine/wiki/GREL-Functions)
[OpenRefine documentation](http://openrefine.org/documentation.html)


