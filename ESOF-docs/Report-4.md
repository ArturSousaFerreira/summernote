<a name="TOP"> </a>
# Report 4 - Verification and Validation 

## Index
1. [Introduction](#Introduction)
2. [Software Testability and Reviews](#SoftwareTestabilityandReviews)
3. [Test Statistics and analytics](#TestStatisticsandanalytics)
4. [Identify a new bug and/or correct a bug](#IdentifyCorrectBug)
5. [Group Members Identification](#Group)

<a name="Introduction"> </a>
## Introduction

In this report we will look at Summernote with concern to software testing. In the first section we will analyze the testability of the project, see the level of difficulty in testing the different components of the text editor and the scope for improvement of these test methods. Next, the test statistics of the project will be presented including the number of tests, project coverage and other aspects. Finally, the process of correcting a bug report in the project will be presented.

Software testing is used with verification and validation to check if the software meets the specifications and fulfills its purpose. We can define the terms as: 

* Verification: Have we built the software right? (i.e., does it implement the requirements).

* Validation: Have we built the right software? (i.e., do the deliverables satisfy the customer).

<a name="SoftwareTestabilityandReviews"> </a>
## Software Testability and Reviews

There are many definitions of the software testability and different papers have given
different types of software testability factors and metrics on different perspective. 

We are the opinion that software testability is the degree to which a software artifact facilitates testing in a given test context. It is directly related to test effort reduction. A lack of testability, like other design faults, is expensive
to repair when detected late during software development. Therefore, testability should be addressed already during reviews of early development artifacts.

It is really difficult task to get all the clear view of factors that can affect the software testability with their dominating degree on the software system. Even though, we collected six of the factors that affect the software
testability, presented below.


##### 1. Controllability

Controllability is one of the most important factors of testability.
Controllability is the ease of producing a specific output from a specific input—related to the effective coverage of the declared output domain from the input domain. In other words, it is the ability to control input and 
execution of a component/software under test as required for testing.

Summernote is composed of several functionalities that are divided into well-defined and separate functions and modules. Its controllability depends on the module itself, but overall it is large, and it is easy to predict for most cases all possible situations.

To increase component controllability, component developers need to learn how to construct software components with high controllability. The major challenge for them is that they are used to applying specific approaches to supporting program controllability at a certain level to meet the specific requirements for program control and test control. They need well-defined software controllability concepts and supporting methodology to help them address component controllability in all phases of a component-based software engineering process. 

##### 2. Observability

Software observability indicates how easy it is to observe a program based on its operational behaviors, input parameter values, and actual outputs for a test case. The same concept is also applicable to software components to check observability based on component interfaces to see the mapping relationships between the inputs and corresponding outputs. 

Software component is observable if distinct outputs are generated from distinct inputs so that, if a test input is repeated, the output is the same. 

If the outputs are not the same, then the component is dependent on hidden states not identified by the tester - input inconsistency. 

In the case of Summernote, we conclude that the observability of test results when applied to these "core" modules of the project is excellent because it is easy to interpret. In the case of modules developed by external contributors, the tests seem to be somewhat optional, so their observability depends on the technique used to implement them.

##### 3. Isolateability

Isolateablity is the degree to which the component under test can be tested in isolation.

Building and testing each function in isolation gives a more accurate idea in case of error. If we just hope to see everything work out at the end, we will see that in case of error, testing and debugging will be a painful process. When problems are encountered, it can be difficult to figure out where in the hierarchy of functions that originated.

It is much better if each routine or class can be exercised as soon as it is written, and before being combined with other parts. If we can control the inputs and observe the outputs of a single function, it is relatively easy to find out what this function did. If we can only observe the operation of the entire program, it can be very difficult to find out where an incorrect result came from.

There may be some components that can not be tested in perfect isolation but if there is a partial ordering of functionality tests that allows us to test all other subcomponents first, we can be sure that new problems are in the new code.

Determining an overall degree of isolateability for Summernote would be complicated because it is difficult to predict in which cases isolateability is ideal or not, but the insulation of the various components under test seems good.

##### 4. Separation of concerns

The separation of concerns is keeping the code for each of these concerns separate. Changing the interface should not require changing the business logic code, and vice versa. 

One of the most important principle in Software Engineering is the Separation of Concerns (SoC): the idea that a software system must be decomposed into parts that overlap in functionality as little as possible. It is so central that it appears in many different forms in the evolution of all methodologies, programming languages and best practices.

It is interesting to note that Dijkstra mentions the importance of SoC in 1974: `separation of concerns ... even if not perfectly possible is yet the only available technique for effective ordering of one's thoughts`.

As we already said in [previous report](Report-3.md/#architecturel-pattern) this project seems to follow an architectural design named the Model-View-Controller, MVC, and this design pattern is an excellent example of separating these concerns for better software maintainability.

##### 5. Understandability

Software systems tend to depart more and more from the principle of simplicity and become increasingly complex.

The increase in size and complexity of software drastically affects several quality attributes, especially maintainability and understandability. Here 
we'll focus in understandability.

Software developers and maintainers need to read and understand source programs and other documents of software. The significance of understandability is very obvious that can be perceived as `If we can't learn something, we won't understand it. If we can't understand something, we can't use it - at least not well enough to avoid creating a money pit. We can't maintain a system that we don't understand - at least not easily. And we can't make changes to our system if we can't understand how the system as a whole will work once the changes are made`. Understandability of software documents is thus 
important as `the better we know what the thing is supposed to do, the better we can test for it`.

Software understandability is vital and one of the most significant components of the software development. The lack of understandability aspect often leads to false interpretation that may in turn lead to ambiguities, misunderstanding and hence to faulty development results. It plays an important role as far as the issue of delivering quality software is concerned. Therefore, understandability is obviously relevant and significant in the context of software testability. In Summernote's project we verify that this project continues to maintain clean code, keep architecture components balanced but
exists some possible refactoring to do due to duplication of code. 

##### 6. Heterogeneity

Summernote is an open-source library under the MIT license as had been said previously, and have some contributions on github from various developers.

It represent a risk of embedding the modified code submitted in a pull request, and made the integration with the existent code so is necessary to ensure that it remains globally functional.

By one side, the unit tests allows the owners and the contributors of Summernote's project guarantee the correct operation of library components and the right flow of development. On the other hand, it is important to verify if the integration of the various components is done correctly through integration tests. As already mentioned, the Grunt tool is used to automate Unit tests and the Travis-CI tool is used to automate Integration tests. In the chapter 2 we'll show the results obtained with this tools. 

It is verified by us that the use of a public GitHub repository open to any collaborator encourages a greater heterogeneity of the test tools used.

[Go to top](#TOP)
<a name="TestStatisticsandanalytics">
## Test Statistics and analytics

We ran the default build, dist and test configurations of grunt to obtain some information regarding the test cases provided by the Summernote team. After running, we detected the presence of [147](https://travis-ci.org/summernote/summernote/builds/178270739) successfully passing unit tests. The unit tests can be found in the `test` folder of the git repository. A screenshot of the log is given below to get a view of the same.

![Unit-tests](resources/unit-tests.png?raw=true "Unit tests")

The testing solution uses PhantomJS javascript testing framework and Karma to run the tests against selected web browsers. The results are then sent to the Coveralls website where the test results are presented in a user friendly manner including the code coverage, which at the chosen commit was approximately [70%](https://coveralls.io/builds/8964163). We also noted the [![Coverage Status](https://coveralls.io/repos/summernote/summernote/badge.svg?branch=develop&service=github)](https://coveralls.io/github/summernote/summernote?branch=develop) badge provided by the team in the `README.md` file of the summernote repository linked to the Coveralls website. It is also possible to check the code coverage in a per file basis and compare the global coverage back in time.

![Code-coverage](resources/code-coverage.png?raw=true "Code coverage")

The coverage report of the code in testing can be found using the grunt test command in the node modules of the project and also by using the istanbul code coverage tool made for javascript codes and also written in javascript. The report gives a detatiled description of the number of lines of code used along with the functions and is compressed into folders giving a better view of the overall coverage of the code. The resulting report is a graphical front-end webpage made using LCOV and can be found here. A screenshot of the same is given below. However, the entire [LCOV report](http://htmlpreview.github.com/?https://github.com/ei12134/summernote/blob/doc/verification-and-validation/test/coverage/PhantomJS%201.9.8%20(Linux%200.0.0)/lcov-report/index.html) can be found in a graphical format at `test\coverage\PhantomJS 1.9.8 (Linux 0.0.0)`.

![LCOV-report](resources/coverage.png?raw=true "Coverage Report")

[Go to top](#TOP)
<a name="IdentifyCorrectBug"> </a>
## Identify a new bug and/or correct a bug

#### Bug identification
Reading the issues available at the git repository for the Summernote project and filtering the results using the `bug` tag allowed us to access a useful list of unresolved bugs already found and detailed by the community. After some time navigating through this list we decided to attempt to correct a bug disclosed at the beginning of November 2016 by the user `1002237913` concerning the text editor command for reseting the foreground text color. The referred issue numbered #2125 and titled [ForeColor ResetToDefault](https://github.com/summernote/summernote/issues/2125) explains the expected behaviour of the action of reseting the foreground color of a text involving the reversion of its color to the original one, while preserving any other text formatting previously applied like bold, italic, etc. In reality, Summernote's current build does not respect this and the `Reset to default` command actually also removes any extra text formatting along with reseting the its color. This was a bug acknowledged by the team developer [`lqez`](http://summernote.org/team/) and also tagged as `pull-request-wanted`. 

![Formatted-text-reset-color](resources/Formatted-text-reset-color.png?raw=true "Formatted-text-reset-color")
![Reset to default command](resources/reset-to-default-command.png?raw=true "Reset to default command")
![Formatted-text](resources/Formatted-text.png?raw=true "Formatted-text")

#### Bug correction
The simple apparent nature of the bug and the fact that there was a deliberate request to get a fix from the community by a team developer encouraged us in attempting to fix the bug and open a [pull request](https://github.com/summernote/summernote/pull/2134). Our initial solution was mere line change that made the reset command only change the text color to black along the lines of a suggestion of the initial bug reporter. This was unfortunately not enough as `lqez` expressed that we should get the real reset color which in some cases could not be black, meaning we needed to figure the default text color defined somewhere in the program code. After some css style analysis we arrived at a possible solution that retrieves the original css color applied to the text and uses that value when issuing the reset color command. After each new commit amending the original pull-request, two checks are made: `coveralls` tests and displays the new code coverage status after the changes in the source code and `travis-ci` checks for integration errors including syntax and code formating errors. At the time of writing of this report, no new comments were added to that pull-request.

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
