---
title: "Filtering and Sorting with OpenRefine"
teaching: 10
exercises: 10
questions:
- "How can we select only a subset of our data to work with?"
- "How can we sort our data?"
objectives:
- "Filter to a subset of rows by text filter or include/exclude."
- "Sort table by a column."
- "Sort by multiple columns."
keypoints:
- "OpenRefine provides a way to sort and filter data without affecting the raw data."
---

## Using Facets

*Exploring data by creating facets and applying filters*

Facets are one of the most useful features of OpenRefine and can help you both get an overview of the data in a project as well as helping you bring more consistency to the data. OpenRefine supports faceted browsing as a mechanism for

* seeing a big picture of your data, and
* filtering down to just the subset of rows that you want to change in bulk.

A 'Facet' groups all the like values that appear in a column and then allows you to filter the data by these values. You can also edit values across many records at the same time.

There are different types of facets for different data types. We are going to start with a 'Text facet'. This groups all the identical text values in a column and lists the unique values with the number of records it appears in. The facet information always appears in the left hand panel in the OpenRefine interface. If you have numbers or dates in that they will show up in the facet in a group called **(number)** or **(date)**. If you want a number or date to appear as text in this kind of facet, you have to use a **custom text facet** and add **.toString()** after value in the Expression.

Here we will use faceting to look for potential errors in data entry in the `village` column.

1. Scroll over to the `village` column.
2. Click the down arrow and choose `Facet` > `Text facet`.
3. In the left panel, you'll now see a box containing every unique value in the `village` column
along with a number representing how many times that value occurs in the column.
4. Try sorting this facet by name and by count. Do you notice any problems with the data? What are they?
5. Hover the mouse over one of the names in the `Facet` list. You should see that you have an `edit` function available.
6. You could use this to fix an error immediately, and OpenRefine will ask whether you want to make the same correction to every value it finds like that one. But OpenRefine offers even better ways to find and fix these errors, which we'll use instead. We'll learn about these when we talk about clustering.

What errors do you see that we will need to clean up? We will talk about them as a group.

> ## Solution
> - `Chirdozo` is likely a mis-entry of `Chirodzo`.
> - `Ruca` is likely a mis-entry of `Ruaca`.
> - `Ruaca - Nhamuenda` and `Ruaca-Nhamuenda` refer to the same place (differ only by spaces around the hyphen). You might also wonder if both of these are the same as `Ruaca`. We will see how to correct these misspelled and mistyped entries in a later exercise.
> - The entry `49` is almost certainly an error but you will not be able to fix it by reference to other data.
{: .solution}

## Filtering

There are many entries in our data table. We can filter it to work on a subset of the data in the list for the next set of operations. Please ensure you perform this step to save time during the class.

1. Click the down arrow next to `respondent_roof_type` > `Text filter`. A `respondent_roof_type` facet will appear on the left margin.
2. Type in `mabat` and press return. There are 58 matching rows of the original 131 rows (and these rows are selected for the subsequent steps).
3. At the top, change the view to `Show` 50 `rows`. This way you will see most of the matching rows.

> ## Exercise
>
> 1. What roof types are selected by this procedure?  
> 2. How would you restrict this to only one of the roof types?  
>
> > ## Solution
> > 1. Do `Facet` > `Text facet` on the `respondent_roof_type` column after filtering. This will show that
> > two names match your filter criteria. They are `mabatipitched` and `mabatisloping`.   
> > 2. To restrict to only one of these two roof types, you could include more letters in your filter.
> >
> {: .solution}
{: .challenge}

### Excluding entries

In addition to the simple text filtering we used above, another way to narrow our filter is to `include` and/or `exclude` entries in a facet. You will see the `include` or `exclude` options if you hover over the name in the facet window.

If you still have your facet for `respondent_roof_type`, you can use it, or use drop-down menu > `Facet` > `Text facet` to create a new facet. Only the entries with names that agree with your `Text filter` will be included in this facet.

Faceting and filtering look very similar. A good distinction is that faceting gives you an overview description of all of the data that
is currently selected, while filtering allows you to select a subset of your data for analysis.

> ## Exercise
>
> Use `include / exclude` to select only entries from one of these two roof types.
>
> > ## Solution
> >
> > 1. In the facet (left margin), click on one of the names, such as `mabatisloping`. Notice that when you click on the name, or hover
> > over it, there are entries to the right for `edit` and `include`.
> > 2. Click `include`. This will explicitly include this roof type, and exclude others that are not explicitly included. Notice that the
> option now changes to `exclude`.
> > 3. Click `include` and `exclude` on the other roof type and notice how the two entries appear and disappear
> >  from the table.
> >
> {: .solution}
{: .challenge}

Remove the filter before moving on so that you again have the full dataset of 131 records.


> ## More on Facets
> [OpenRefine Wiki: Faceting](https://github.com/OpenRefine/OpenRefine/wiki/Faceting)
>
> As well as 'Text facets' Refine also supports a range of other types of facet. These include:
>
> * Numeric facets
> * Timeline facets (for dates)
> * Custom facets
> * Scatterplot facets
>
> **Numeric and Scatterplot facets** display graphs instead of lists of values. The numeric facet graph includes 'drag and drop' controls you can use to set a start and end range to filter the data displayed. These facets are explored further in [Examining Numbers in OpenRefine](http://www.datacarpentry.org/OpenRefine-ecology-lesson/03-numbers/)
>
> **Custom facets** are a range of different types of facets. Some of the default custom facets are:
>
> * Word facet - this breaks down text into words and counts the number of records each word appears in
> * Duplicates facet - this results in a binary facet of 'true' or 'false'. Rows appear in the 'true' facet if the value in the selected column is an exact match for a value in the same column in another row
> * Text length facet - creates a numeric facet based on the length (number of characters) of the text in each row for the selected column. This can be useful for spotting incorrect or unusual data in a field where specific lengths are expected (e.g. if the values are expected to be years, any row with a text length more than 4 for that column is likely to be incorrect)
> * Facet by blank - a binary facet of 'true' or 'false'. Rows appear in the 'true' facet if they have no data present in that column. This is useful when looking for rows missing key data.
{: .callout}

## Using clustering to detect possible typing errors

In OpenRefine, clustering means "finding groups of different values that might be alternative representations of the same thing". For example, the two strings `New York` and `new york` are very likely to refer to the same concept and just have capitalization differences. Likewise, `Gödel` and `Godel` probably refer to the same person. Clustering is a very powerful tool for cleaning datasets which contain misspelled or mistyped entries. OpenRefine has several clustering algorithms built in. Experiment with them, and learn more about these algorithms and how they work.

1. In the `village` Text Facet we created in the step above, click the `Cluster` button.
2. In the resulting pop-up window, you can change the `Method` and the `Keying Function`. Try different combinations to
 see what different mergers of values are suggested.
3. Select the `key collision` method and `metaphone3` keying function. It should identify two clusters.
4. Click the `Merge?` box beside each cluster, then click `Merge Selected and Recluster` to apply the corrections to the dataset.
4. Try selecting different `Methods` and `Keying Functions` again, to see what new merges are suggested.
5. You should find no more clusters are found. None of the available methods offered to cluster `Ruaca-Nhamuenda` with `Ruaca` or `Chirdozo` with `Chirodzo`.  To merge these values we need to hover over them in the village text facet, select edit, and manually change the names.
6. Change `Chirdozo` to `Chirodzo` and `Ruaca-Nhamuenda` to `Ruaca`. You should now have four clusters: `Chirodzo`, `God`, `Ruaca` and `49`.

Important: If you `Merge` using a different method or keying function, or more times than described in the instructions above,
your solutions for later exercises will not be the same as shown in those exercise solutions.

## Different clustering algorithms

The technical details of how the different clustering algorithm work can be found at the link below.

[More on clustering](https://github.com/OpenRefine/OpenRefine/wiki/Clustering-In-Depth)

