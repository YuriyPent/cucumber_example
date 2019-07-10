# Cucumber tutorial
[![CircleCI Build Status](https://circleci.com/gh/YuriyPent/cucumber_example.svg?style=shield)](https://circleci.com/gh/YuriyPent/cucumber_example)
### Create an empty Cucumber project
* Start by creating a new project directory with the `cucumber-archetype`
  ```powershell
  mvn archetype:generate                    \
   -DarchetypeGroupId=io.cucumber           \
   -DarchetypeArtifactId=cucumber-archetype \
   -DarchetypeVersion=4.2.6.1               \
   -DgroupId=hellocucumber                  \
   -DartifactId=hellocucumber               \
   -Dpackage=hellocucumber                  \
   -Dversion=1.0.0-SNAPSHOT                 \
   -DinteractiveMode=false
   ```
* Change into the directory `cd hellocucumber`
### Verify Cucumber installation
* run Cucumber `mvn test`. Cucumber’s output is telling us that it didn’t find anything to run.
### Write a Scenario
* Create an empty file called `src/test/resources/hellocucumber/is_it_friday_yet.feature` with the following content:
```cucumber
Feature: Is it Friday yet?
  Everybody wants to know when it's Friday

  Scenario: Sunday isn't Friday
    Given today is Sunday
    When I ask whether it's Friday yet
    Then I should be told "Nope"
```
*  Ask Cucumber to execute it `mvn test`.
*  Cucumber is telling us we have one undefined scenario and three undefined steps. It’s also suggesting some snippets of code that we can use to define these steps:
```cucumber
You can implement missing steps with the snippets below:

@Given("^today is Sunday$")
public void today_is_Sunday() {
    // Write code here that turns the phrase above into concrete actions
    throw new PendingException();
}
@When("^I ask whether it's Friday yet$")
public void i_ask_whether_it_s_Friday_yet() {
    // Write code here that turns the phrase above into concrete actions
    throw new PendingException();
}
@Then("^I should be told \"([^\"]*)\"$")
public void i_should_be_told(String arg1) {
    // Write code here that turns the phrase above into concrete actions
    throw new PendingException();
}
```
* Copy each of the three snippets for the undefined steps and paste them into `src/test/java/hellocucumber/Stepdefs.java`
