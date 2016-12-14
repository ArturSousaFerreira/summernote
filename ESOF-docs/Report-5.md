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

Since Summernote is a project still growing and evolving, there is still a large list of tasks and features to be developed and problems to be corrected. However, the project is open to the development of new features as long as it is of interest for the relevant project. Throughout this report will be described the process of identification, development and submission of a new feature of the Summernote project.

<a name="DiscussSoftwareMaintainability"> </a>
## Discuss Software Maintainability

We have ran the Better Codehub, later we call only BC, tool to check ten guidelines for maintainable software in the Summernote project.

Below are shown the results this tool generated in the same order presented to us. 

1. :x: Write Short Units of Code
2. :x: Write Simple Units of Code
3. :x: Write Code Once
4. :heavy_check_mark: Keep unit interfaces small
5. :heavy_check_mark: Separate concerns in modules
6. :heavy_check_mark: Couple Architecture Components Loosely
7. :heavy_check_mark: Keep architecture components balanced
##### 8. :heavy_check_mark: Keep your codebase small
The results show that the codebase is indeed kept small. This assessment is made by comparing the total project code lines into a Man-months effort measuring unit that represents the average productivity of a single programmer translated into lines of code. A possible reason for the good result might be the use of external libraries like Bootstrap and jQuery, which reduces codebase size, improving maintainability.

##### 9. :x: Automate Tests
Although the Better Code Hub classified the automation tests as a failure, in reality, as was discussed in the previous report, the PhantomJS test framework is being used and the code coverage is relatively higher than shown in this results (70% compared to 47%). It can be said that in this case the test code coverage seems to be directly comparing lines of code with testing code lines. As it detected the project had more than 10000 line of code, it expected the total lines of test code to be at least 50% of that which in this case it is not.

##### 10. :heavy_check_mark: Write clean code
This is a passing test indicating that most source files comply with the good practices in keeping the code clean and maintainable, such as not leaving unit level code smells behind, no bad comments, no code in comments, no dead code, no long identifiers behind, no magic constants behind and no badly handled exceptions. Analysing a refactoring candidate like summernote.js it is possible to quickly conclude that due to its line code size it is indeed the core of summernote and contains the most important functions and although has been kept relatively organized, it does indeed still present some code smells like bad comments and long identifiers.

The project achieved a compliance classification of 6 out of 10, in such a way that we've got a badge of [![BCH compliance](https://bettercodehub.com/edge/badge/ei12134/summernote)](https://bettercodehub.com) proving it.

To get more detailed information we provide a [link](resources/BetterCodeHub.pdf) to a pdf file that shows the ten guidelines in a list layout way.

[Go to top](#TOP)
<a name="Reportevolutionprocess">
## Report evolution process

#### Feature decision

The Summernote project repository provides a wide range of issues that are fed by its team members and also by its users community. After a careful analysis of this list, the group decided to evolve a feature that is based on the issue [#1885](https://github.com/summernote/summernote/issues/1885), which is, at the date of this report, the most recently commented feature, also tagged both as `feature-request` and `pull-request-wanted`. The feature selected appeared to us to be relatively simple of interpretation and consequent implementation.

#### Identification of components implementing the feature  

While running the Summernote in the browser, in this case we use Google Chrome, we detected the relevant active components by using the code inspector tool. 

[Go to top](#TOP)
<a name="Linktopullrequest"> </a>
## Link to pull request

After the implementation of the new feature we've made a pull request in order to integrate it into the Summernote library. It's available and it's visible here.

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
