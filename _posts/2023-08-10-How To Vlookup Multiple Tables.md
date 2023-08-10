---
type: posts
layout: splash

title: How to Vlookup Multiple Tables
---

<!--author_profile: true
-->

In daily work with tables, expecially in excel, we usually apply the vlookup function to match values where the lookup area is just one array or one sheet. But, have you considered that how to vlookup value across multiple sheets?  I know that most people will suppose these areas have the same fields, so they can utilize Kutools for excel which can simplify the task of combining multiple sheets significantly. But here, I will introduce you some purely $excelish$ way to solve these problems.

Suppose I have the following worksheets:
<!---
https://stackoverflow.com/questions/24319505/how-can-one-display-images-side-by-side-in-a-github-readme-md
-->
<p float="left">
  <img src="/assets/images/doc-vlookup-from-multiple-sheets-1.png" width=20% />
  <img src="/assets/images/doc-vlookup-from-multiple-sheets-2.png" width=20% /> 
  <img src="/assets/images/doc-vlookup-from-multiple-sheets-3.png" width=20% />
  <!---&rarr;{:style="padding: 10px 0;"}
  -->
</p>
I want to get part of the corresponding values from these three worksheets, normally, there are two ways regarding formulas. 

<!---
https://stackoverflow.com/questions/24319505/how-can-one-display-images-side-by-side-in-a-github-readme-md
-->
![doc-vlookup-from-multiple-sheets-4](/assets/images/doc-vlookup-from-multiple-sheets-4.png){:style="display:block; margin-left:auto; margin-right:auto"}

<!---
![doc-vlookup-from-multiple-sheets-2](/assets/images/doc-vlookup-from-multiple-sheets-2.png){:style="display:inline; margin-left:auto; margin-right:auto"}
![doc-vlookup-from-multiple-sheets-3](/assets/images/doc-vlookup-from-multiple-sheets-3.png){:style="display:inline; margin-left:auto; margin-right:auto"}
-->

# Vlookup Values From Multiple Worksheets With Normal Formula
