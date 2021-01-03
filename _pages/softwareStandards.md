---
layout: single
author_profile: false
permalink: /softwareStandards/
title: "Software standards"
excerpt: "Summary of the coding standards and best practices used for our projects."
toc: true
toc_label: "The software standards applied to all of the code residing in The Aging Apprentice Github repositories"

---
<img src="/assets/images/vaccumTubes.jpg" alt="vaccum tubes" width="100%" height="50%"> 
When contributing to VA3WAM repositories please follow these standards. With luck we will be able to jump between projects
with minimal effort.

## C++
This <a href="http://www.edparrish.net/common/cppdoc.html">link</a> points to a set of standards used for coding in C++. 
In addition to these standards comments should be markdown compliant using /// followed by XML tags. Source code tags are 
parsed using <a href="https://en.wikipedia.org/wiki/Doxygen">DoxyGen</a> to produce documentation.

## Versioning
We use <a href="http://semver.org/">SemVer</a> for versioning. We use the Github release process to package up known working 
code configuraitons.

## Naming Variables and Files
We use <a href="https://en.wikipedia.org/wiki/Camel_case">camelCase</a> for naming variables in our code as well as when naming files. 

## Readme Files
Our Github respositories must contain a readme file that is based on this 
<a href="https://github.com/va3wam/TWIPe/blob/Andrew/README.md">template</a>.
