# Example python code for quickly loading a tree

### Summary

This code shows a quick way to load a large tree in PNAV. 

The method used is to load the leaf nodes only (including tree filtering with an include_filter and an exclude_filter).  To minimize the amount of data returned from the query, I am only returning a select number of keys from the documents.  See the projection variable for details.  In particular, I am avoiding loading the tags or dropdowntags keys as they are in general the most memory intensive.  Because of the way I am doing the filtering with the include_filter and exclude_filter, I don't see much reason to load the tags data.

For my first example, I am loading the full Corteva CP portfolio from the pnavqa.phibred.com server ('Dave Large CP Test') without any tree filtering.  My results show I can load this data in about 2.4 seconds or so for the leaves and in about 0.77 seconds for the non-children nodes.  

Further down in the code, I turn on the tree filter for ProjectStatus:Approved and ProjectStatus:Planning.  Here I was able to load the leaf nodes in about 1.4 seconds and the non-children nodes in about 0.88 seconds or so.

