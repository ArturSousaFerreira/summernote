<a name="TOP"> </a>
# Report 4 - Verification and Validation 

## Index
1. [Software Testability and Reviews](#SoftwareTestabilityandReviews)
2. [Test Statistics and analytics](#TestStatisticsandanalytics)
3. [Identify a new bug and/or correct a bug](#IdentifyCorrectBug)
4. [Group Members Identification](#Group)

<a name="SoftwareTestabilityandReviews"> </a>
## Software Testability and Reviews

##### 1. Controllability

Controllability is one of the most important factors of testability. Controllability is the ease of producing a specific output from a specific 
input—related to the effective coverage of the declared output domain from the input domain. In other words, it is the ability to control input and 
execution of a component/software under test as required for testing.

Analyzing Summernote, we can define controllability as the extent to which a component is constructed to provide component control capability to 
facilitate the control of components. Component control capability includes the following types:

- Component environment control: This refers to the built-in component capability that supports component environment installation, setup, and 
deployment.
- Component execution control: This refers to the built-in component execution control capability that enables executions of a component in different 
modes, such as test mode, normal function mode, and control mode. With this capability, users and testers can start, restart, stop, pause, and abort a program execution as they wish. 
- Component state-based behavior control: This refers to the built-in capability that facilitates the control of component state-based behavior, such 
as resetting component states, triggering a state transaction from one state to another. 
- Component test control: This refers to the built-in capability that facilitates the control of component tests through component interfaces. Setting 
up different input parameter data for component tests is a typical example. 
- Component function feature control: This refers to the built-in capability that facilitates the selection and configuration of component functional 
features. It is only applicable to software components with customizable functional features that allow component users to select and configure its 
features based on their needs.

Since these control capabilities are essential for supporting component testing and operations, component controllability is an important contributing 
factor for component testability. To increase component controllability, component developers need to learn how to construct software components with 
high controllability. The major challenge for them is that they are used to applying specific approaches to supporting program controllability at a 
certain level to meet the specific requirements for program control and test control. They need well-defined software controllability concepts and 
supporting methodology to help them address component controllability in all phases of a component-based software engineering process. 


##### 2. Observability

Software observability indicates how easy it is to observe a program based on its operational behaviors, input parameter values, and actual outputs for 
a test case. The same concept is also applicable to software components to check observability based on component interfaces to see the mapping 
relationships between the inputs and corresponding outputs. 
Software component is observable if distinct outputs are generated from distinct inputs so that, if a test input is repeated, the output is the same. 
If the outputs are not the same, then the component is dependent on hidden states not identified by the tester - input inconsistency. 
In our view, component observability refers to the degree to which components are designed to facilitate the monitoring and observation of component 
functions and behaviors of component tests. Component observability is twofold: 

- check the mapping relationships between inputs and corresponding outputs for each test. This could be done in two different stages. A test design 
review is the first stage, in which all component tests are verified to find the hidden inputs and missing outputs, and incorrect mapping relationships 
between inputs and outputs. Test result verification during component testing is the second stage, where an effective test tool could be an ideal 
solution to check this in a systematic manner. 
- track and monitor all component tests and test results. There are two ways to achieve this goal. An effective component test bed is a natural 
solution. To reduce the testing cost in setting up a specific component test bed for each component, we need to find effective methods to construct 
testable components with good observability.

##### 3. Isolateability
##### 4. Separation of concerns
##### 5. Understandability
##### 6. Heterogeneity


[Go to top](#TOP)
<a name="TestStatisticsandanalytics">
## Test Statistics and analytics

[Go to top](#TOP)
<a name="IdentifyCorrectBug"> </a>
## Identify a new bug and/or correct a bug
Reading the issues available at the git repository for the Summernote project and filtering the results using the `bug` tag allowed us to access a useful list of unresolved bugs already found and detailed by the community. After some time navigating through this list we decided to attempt to correct a bug disclosed at the beginning of November 2016 by the user `1002237913` concerning the text editor command for reseting the foreground text color. The referred #2125 issue is titled [ForeColor ResetToDefault](https://github.com/summernote/summernote/issues/2125) and explains the expected behaviour of the action of reseting the foreground color of a text involving the reversion of its color to the original one, while preserving any other text formatting previously applied like bold, italic, etc. In reality, Summernote's current build does not respect this and the `Reset to default` command actually also removes any extra text formatting along with reseting the its color. This was a bug acknowledged by the team developer [`lqez`](http://summernote.org/team/) and also tagged the issue as `pull-request-wanted`. The apparent simple nature of the bug and the fact that there was a deliberate request to get a fix by the community from a team developer made us attempt to fix the bug and open a [pull request](https://github.com/summernote/summernote/pull/2138). Our initial solution was mere line change that made the reset command only change the text color to black along the lines of a suggestion of the initial bug reporter. This was unfortunately not enough as `lqez` expressed that we should get the real reset color which in some cases could not be black, meaning we needed to figure the default text color defined somewhere in the program code. After some css style analysis we arrived at a possible solution that retrieves the original css color applied to the text and uses that value when issuing the reset color command. After each new commit amending the original pull-request, two checks are made: `coveralls` tests and displays the new code coverage status after the changes in the source code and `travis-ci` checks for integration errors including syntax and code formating errors. At the time of writing of this report, no new comments were added to that pull-request.

![Formatted-text-reset-color](resources/Formatted-text-reset-color.png?raw=true "Formatted-text-reset-color")
![Reset to default command](resources/reset-to-default-command.png?raw=true "Reset to default command")
![Formatted-text](resources/Formatted-text.png?raw=true "Formatted-text")

[Go to top](#TOP)
<a name="Group"> </a>
## Group Members Identification 

|               Name              |         Email        | Contribution |
|---------------------------------|:--------------------:|:------------:|
| Artur Sousa Ferreira            | ei12168@fe.up.pt     |      25%     |
| José Filipe de Monteiro Peixoto | ei12134@fe.up.pt     |      25%     |
| Nuno Miguel Rainho Valente      | up200204376@fe.up.pt |      25%     |
| Urvish Sanjay Desai                    | up201602683@fe.up.pt |      25%     |

[Go to top](#TOP)
