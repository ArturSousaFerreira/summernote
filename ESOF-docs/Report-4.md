<a name="TOP"> </a>
# Report 4 - Verification and Validation 

## Index
1. [Software Testability and Reviews](#SoftwareTestabilityandReviews)
2. [Test Statistics and analytics](#TestStatisticsandanalytics)
3. [Identify a new bug and/or correct a bug](#IdentifyCorrectBug)
4. [Group Members Identification](#Group)

<a name="SoftwareTestabilityandReviews"> </a>
## Software Testability and Reviews


[Go to top](#TOP)
<a name="TestStatisticsandanalytics">
## Test Statistics and analytics

[Go to top](#TOP)
<a name="IdentifyCorrectBug"> </a>
## Identify a new bug and/or correct a bug
Reading the issues available at the git repository for the Summernote project and filtering the results using the `bug` tag allowed us to access a useful list of unresolved bugs already found and detailed by the community. After some time navigating through this list we decided to attempt to correct a bug disclosed at the beginning of November 2016 by the user `1002237913` concerning the text editor command for reseting the foreground text color. The referred #2125 issue is titled [ForeColor ResetToDefault](https://github.com/summernote/summernote/issues/2125) and explains the expected behaviour of the action of reseting the foreground color of a text involving the reversion of its color to the original one, while preserving any other text formatting previously applied like bold, italic, etc. In reality, Summernote's current build does not respect this and the `Reset to default` command actually also removes any extra text formatting along with reseting the its color. This was a bug acknowledged by the team developer [`lqez`](http://summernote.org/team/) and also tagged the issue as `pull-request-wanted`. The apparent simple nature of the bug and the fact that there was a deliberate request to get a fix by the community from a team developer made us attempt to fix the bug and open a [pull request](https://github.com/summernote/summernote/pull/2138). Our initial solution was mere line change that made the reset command only change the text color to black along the lines of a suggestion of the initial bug reporter. This was unfortunately not enough as `lqez` expressed that we should get the real reset color which in some cases could not be black, meaning we needed to figure the default text color defined somewhere in the program code. After some css style analysis we arrived at a possible solution that retrieves the original css color applied to the text and uses that value when issuing the reset color command. After each new commit amending the original pull-request, two checks are made: `coveralls` tests and displays the new code coverage status after the changes in the source code and `travis-ci` checks for integration errors including syntax and code formating errors. At the time of writing of this report, no new comments were added to that pull-request.

![Reset to default command](resources/reset-to-default-command.png?raw=true "Reset to default command")

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
