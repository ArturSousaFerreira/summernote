<a name="TOP"> </a>
# Report 5 - Software Maintenance/Evolution 

## Index
1. [Introduction](#Introduction)
2. [Discuss Software Maintainability](#DiscussSoftwareMaintainability)
3. [Report evolution process](#Reportevolutionprocess)
4. [Link to pull request](#Linktopullrequest)
5. [Group Members Identification](#Group)

<a name="Introduction"> </a>
## Introduction

Since Summernote is a project still growing and evolving, there is still 
a large list of tasks and features to be developed and problems to be corrected. 
However, the project is open to the development of new features as long 
as it interest for the relevant project. Throughout this report will 
be described the process of identification, development and submission 
of a new feature of the Summernote project.

<a name="DiscussSoftwareMaintainability"> </a>
## Discuss Software Maintainability

We have ran the Better Codehub, later we call only BC, tool to check ten guidelines for maintainable software
in the Summernote project.

We present below the results this tool provided in the same order presented to us. 

1. :x: Write Short Units of Code
2. :x: Write Simple Units of Code
3. :x: Write Code Once
4. :heavy_check_mark: Keep unit interfaces small
5. :heavy_check_mark: Separate concerns in modules
6. :heavy_check_mark: Couple Architecture Components Loosely
7. :heavy_check_mark: Keep architecture components balanced
8. :heavy_check_mark: Keep your codebase small
9. :x: Automate Tests
10. :heavy_check_mark: Write clean code

We have notice a classification of compliance of 6 of 10, in such a way that we've got 
a badge of [![BCH compliance](https://bettercodehub.com/edge/badge/ei12134/summernote)](https://bettercodehub.com)
which proves the respective classification.

To get more detailed information we provide [here](resources/BetterCodeHub.pdf) a link to a pdf file that shows the
ten guidelines in a more evident and list layout way.

[Go to top](#TOP)
<a name="Reportevolutionprocess">
## Report evolution process

#### Feature decision

The Summernote project repository provides a wide range of issues that are fed by its
employees, as has been mentioned in previous reports. After a careful analysis of it, 
the group decided to evolve a feature that is based on issue #1885, which is the most recent 
feature , at the date of this report.

We wanted to chose a feature that was intended about a relatively short time and for that we
search about date and with two labels: `feature-request` and `pull-request-wanted`.

#### Identification of components implementing the feature  

While running the Summernote in the browser, in this case we use Google Chrome, we
detect some active components by using the code inspector on that browser. 

[Go to top](#TOP)
<a name="Linktopullrequest"> </a>
## Link to pull request

After the implementation of the new feature we've made a pull request in order
to integrate it into the Summernote library. It's available and it's visible here.

[Go to top](#TOP)
<a name="Group"> </a>
## Group Members Identification 

|               Name              |         Email        | Contribution |
|---------------------------------|:--------------------:|:------------:|
| Artur Sousa Ferreira            | ei12168@fe.up.pt     |      25%     |
| José Filipe de Monteiro Peixoto | ei12134@fe.up.pt     |      25%     |
| Nuno Miguel Rainho Valente      | up200204376@fe.up.pt |      25%     |
| Urvish Sanjay Desai             | up201602683@fe.up.pt |      25%     |

[Go to top](#TOP)
