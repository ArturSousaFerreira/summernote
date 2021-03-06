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

Since [Summernote](http://summernote.org/) is a project still growing and evolving, there is still a large list of tasks and features to be developed and problems to be corrected. However, the project is open to the development of new features as long as it is of interest for the relevant project. Throughout this report will be described the process of identification, development and submission of a new feature of the [Summernote](http://summernote.org/) project.

<a name="DiscussSoftwareMaintainability"> </a>
## Discuss Software Maintainability

We have ran the [Better Codehub](https://bettercodehub.com/), later we call only [BC](https://bettercodehub.com/), tool to check ten guidelines for maintainable software in the [Summernote](http://summernote.org/) project.
Behind [BC](https://bettercodehub.com/) is the software improvement group, or [SIG](https://www.sig.eu/) for short. SIG is a management consultancy firm that has several clients, namely, 
KLM and Rabobank, for example. This gives us confidence in the tool we are using.  

The project achieved a compliance classification of 6 out of 10, in such a way that we've got a badge of [![BCH compliance](https://bettercodehub.com/edge/badge/ei12134/summernote)](https://bettercodehub.com) proving it.
To get more detailed information we provide a [link](resources/BetterCodeHub.pdf) to a pdf file that shows the ten guidelines in a list layout way.

Below are shown the results this tool generated in the same order presented to us. 

##### 1. :x: Write Short Units of Code

The [BC](https://bettercodehub.com/) rated this point as a failure and we confirm that, in [Summernote](http://summernote.org/), most of units above 15 lines of code, in our opinion, can't 
be splitted in smaller units. When writing new units, we shouldn't let them grow above 15 lines of code, when they pass this size we should split them, however 
in some cases it's impossible. 

##### 2. :x: Write Simple Units of Code

We read about writing simple units of code and we agree in one thing: it's very important to get things simple. Is it possible to achieve?
Our response is yes. Well, in this case we need to reduce complexity by extracting sub-branches to separate units of no more than 4 branchs (if, for, while, etc).

Of course, we are the opinion that the overall (McCabe) complexity of a system will not decrease by refactoring a method into several new methods. 
But from a maintainability perspective, a simple unit is easier to understand, and thus modify, than a complex one and simple units ease testing.

##### 3. :x: Write code once

[BC](https://bettercodehub.com/) rated the Write Code Once tests as a failure and by analyzing the list that contains the top 30 of units that violate this test 
guidelines, we confirm that [Summernote](http://summernote.org/) code has some duplicated code. That's a bad methodology for bugs because we need to fix in multiple places. This is both 
inefficient and error-prone. We should avoid duplication by never copy/pasting blocks of code.

##### 4. :heavy_check_mark: Keep unit interfaces small

We are happy to say all methods that are used in the project have small interfaces. A small interface is considered when we have at most 4 parameters per unit.
This implies interfaces changes easier to modify. 

Furthermore, it's important to reserve that large interfaces are not the problem, but rather are indicators of the actual problem. When some project hasn't pass this 
test we can predict some poor data model or ad hoc code modification. So, we `"can view interface size as a code smell, to see whether your data model needs improvement."`

##### 5. :heavy_check_mark: Separate concerns in modules
Like we analized in others reports, [Summernote](http://summernote.org/) is very well organized in modules. It is very important to minimize the consequences of 
changes and it's easier to understand the locations of functions to other developers don't get lost.

##### 6. :heavy_check_mark: Couple architecture components loosely
The tool positively classified the architecture as easy to maintain because changes made within a component have effects that are isolated within that component, also meaning there is a low number of incoming calls per component and there is little to no throughput code. The [BC](https://bettercodehub.com/) classified all the code as hidden code.

##### 7. :heavy_check_mark: Keep architecture components balanced
The tool acknowledges a correct balancing of the existing components size. It detected 7 components and classified their size uniformity as 0.61. This fits well with the recommendation of organizing the source code into 2 to 12 components with approximate sizes, so it is easier to locate the code and also helps when wanting to make isolated component maintenance.

##### 8. :heavy_check_mark: Keep your codebase small
The results show that the codebase is indeed kept small. This assessment is made by comparing the total project code lines into a Man-months effort measuring unit that represents the average productivity of a single programmer translated into lines of code. A possible reason for the good result might be the use of external libraries like Bootstrap and jQuery, which reduces codebase size, improving maintainability.

##### 9. :x: Automate tests
Although the [BC](https://bettercodehub.com/) classified the automation tests as a failure, in reality, as was discussed in the previous report, the PhantomJS test framework is being used and the code coverage is relatively higher than shown in this results (70% compared to 47%). It can be said that in this case the test code coverage seems to be directly comparing lines of code with testing code lines. As it detected the project had more than 10000 line of code, it expected the total lines of test code to be at least 50% of that which in this case it isn't.

##### 10. :heavy_check_mark: Write clean code
This is a passing test indicating that most source files comply with the good practices in keeping the code clean and maintainable, such as not leaving unit level code smells behind, no bad comments, no code in comments, no dead code, no long identifiers behind, no magic constants behind and no badly handled exceptions. Analysing a refactoring candidate like Summernote.js it is possible to quickly conclude that due to its line code size it is indeed the core of [Summernote](http://summernote.org/) and contains the most important functions and although has been kept relatively organized, it does indeed still present some code smells like bad comments and long identifiers.

##### Final note:
Although [BC](https://bettercodehub.com/) is a tool in the BETA version, it has very interesting features. Nowadays, a good organization according to the principles of software engineering is fundamental in the development of small, medium and large projects. As future computer engineers, it was important to have this first contact with this tool and we are sure that we will follow its growth in the future.

[Go to top](#TOP)
<a name="Reportevolutionprocess">
## Report evolution process

#### Feature decision

The [Summernote](http://summernote.org/) project repository provides a wide range of issues that are fed by the team members and by the community, as has been mentioned in previous reports. We wanted to chose a feature that was intended about a relatively short time and for that we search about date and with two labels: `feature-request` and `pull-request-wanted`.

After a careful analysis of this list, the group decided to evolve a feature that is based on issue [#1885](https://github.com/summernote/summernote/issues/1885), which is the most recent feature, at the date of this report. The feature-request primarily wants the editor to be able to input colors for its foreground and background by `hexadecimal` format. The feature seemed important and was yet lacking in the original software.

#### Identification of components implementing the feature  

While running the [Summernote](http://summernote.org/) in the browser, in this case we use Google Chrome, we detect some active components by using the code inspector on that browser. We followed the code inspector and found the code that implemented the current feature. The code is written in Javascript and the color can be applied through a color palette defined in the code. The color could be selected using function with event `click`. Hence, a few changes were required in this code.

#### Implementation of the feature

The feature required only to input color in hexadecimal format. But while searching, we found that we can implement an even better feature that implements html5 colorpicker which will take the input in hexadecimal as well as allow the user to input in the form of a gradient color map.  We observed that only a few additions were required to the code.

Thus, through a thorough analysis of the code, its syntax and indentation, we formulated the code and made it work after several attempts. And hence, the feature was implemented. A preview of the feature can be seen here:

![Feature html5 color input](resources/feature.png?raw=true "Feature html5 color input")

[Go to top](#TOP)
<a name="Linktopullrequest"> </a>
## Link to pull request

After the implementation of the new feature we've made a pull request in order to integrate it into the [Summernote](http://summernote.org/) library. It has passed all the tests and the coverage of tests has remained the same. The link to our pull request is available and is visible [here](https://github.com/summernote/summernote/pull/2159).

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
