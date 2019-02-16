---
title: "Undo, Redo, and Scripts"
teaching: 10
exercises: 5
questions:
- "How can we undo steps?"
- "How can we redo steps?"
- "How can we apply steps we have completed to another dataset?"
objectives:
- "Undo some of our steps and then apply them again."
- "Save our expressions as JSON."
keypoints:
- "OpenRefine keeps track of your steps."
- "You can step back but you will lose everything you did after that."
- "You can save and apply your steps to other datasets."
---

## Using undo and redo.

It's common while exploring and cleaning a dataset to discover after you've made a change that you really should have done something else first. OpenRefine provides `Undo` and `Redo` operations to make this easy.

> ## Exercise
>
> 1. Click where it says `Undo / Redo` on the left side of the screen. All the changes you have made so far are listed here.
> 2. Click on the step that you want to go back to, in this case go back several steps to before you had done any text transformation.
> 3. Visually confirm that those columns now contain the special characters that we had removed previously.
> 3. Notice that you can still click on the later steps to `Redo` the actions. Before moving on to the next lesson, redo all the steps in your analysis so that all of the column you modified are lacking in square brackets, spaces, and single quotes.
{: .challenge}

## How OpenRefine records what you have done

As you conduct your data cleaning and preliminary analysis, OpenRefine saves every change you make to the dataset. These
changes are saved in a format known as JSON (JavaScript Object Notation). You can export this JSON script and apply it to other data files. If you had 20 files to clean, and they all had the same type of errors (e.g. misspellings, leading white spaces), and all
files had the same column names, you could save the JSON script, open a new file to clean in OpenRefine, paste in the script and run it.
This gives you a quick way to clean all of your related data.

## Saving your work as a script

1. In the `Undo / Redo` section, click `Extract...`, and select the steps that you want to apply to other datasets by clicking the check boxes.

![History](../fig/history.png)

2. Copy the code from the right hand panel and paste it into a text editor (like NotePad on Windows or TextEdit on Mac). Make sure it saves as a plain text file. In TextEdit, do this by selecting `Format` > `Make plain text` and save the file as a `.txt` file.

## Importing a script to use against another dataset

Let's practice running these steps on a new dataset. We'll test this on an uncleaned version of the dataset we've been working with.

1. Start a new project in OpenRefine using the messy dataset you downloaded before. Give the project a new name.  
2. Click the `Undo / Redo` tab > `Apply` and paste in the contents of `.txt` file with the JSON code.
3. Click `Perform operations`. The dataset should now be the same as your other cleaned dataset.

For convenience, we used the same dataset. In reality you could use this process to clean related datasets. For example, data that you had collected over different fieldwork periods or data that was collected by different researchers (provided everyone uses the same column headings). The data in this file was generated from an eSurvey system with the actual survey being delivered centrally to a smartphone, so the column headings are pretty much guaranteed to be the same.

{% include links.md %}


