# TDD Anti-Pattern Catalogue

Based on: [http://blog.james-carr.org/2006/11/03/tdd-anti-patterns/]

## The Liar

An entire unit test that passes all of the test cases it has and appears valid, but upon closer inspection it is discovered that it doesn’t really test the intended target at all.

## Excessive Setup

A test that requires a lot of work setting up in order to even begin testing. Sometimes several hundred lines of code is used to setup the environment for one test, with several objects involved, which can make it difficult to really ascertain what is tested due to the “noise” of all of the setup going on.

## The Giant

A unit test that, although it is validly testing the object under test, can span thousands of lines and contain many many test cases. This can be an indicator that the system under tests is a God Object

## The Mockery

Sometimes mocking can be good, and handy. But sometimes developers can lose themselves and in their effort to mock out what isn’t being tested. In this case, a unit test contains so many mocks, stubs, and/or fakes that the system under test isn’t even being tested at all, instead data returned from mocks is what is being tested.

## The Inspector

A unit test that violates encapsulation in an effort to achieve 100% code coverage, but knows so much about what is going on in the object that any attempt to refactor will break the existing test and require any change to be reflected in the unit test.

## Generous Leftovers

An instance where one unit test creates data that is persisted somewhere, and another test reuses the data for its own devious purposes. If the “generator” is ran afterward, or not at all, the test using that data will outright fail.

## The Local Hero

A test case that is dependent on something specific to the development environment it was written on in order to run. The result is the test passes on development boxes, but fails when someone attempts to run it elsewhere.

## The Nitpicker

A unit test which compares a complete output when it’s really only interested in small parts of it, so the test has to continually be kept in line with otherwise unimportant details. Endemic in web application testing.

## The Secret Catcher

A test that at first glance appears to be doing no testing due to the absence of assertions, but as they say, “the devil’s in the details.” The test is really relying on an exception to be thrown when a mishap occurs, and is expecting the testing framework to capture the exception and report it to the user as a failure.

## The Dodger

A unit test which has lots of tests for minor (and presumably easy to test) side effects, but never tests the core desired behavior. Sometimes you may find this in database access related tests, where a method is called, then the test selects from the database and runs assertions against the result.

## The Loudmouth

A unit test (or test suite) that clutters up the console with diagnostic messages, logging messages, and other miscellaneous chatter, even when tests are passing. Sometimes during test creation there was a desire to manually see output, but even though it’s no longer needed, it was left behind.

## The Greedy Catcher

A unit test which catches exceptions and swallows the stack trace, sometimes replacing it with a less informative failure message, but sometimes even just logging (c.f. Loudmouth) and letting the test pass.

## The Sequencer

A unit test that depends on items in an unordered list appearing in the same order during assertions.

## Hidden Dependency

A close cousin of The Local Hero, a unit test that requires some existing data to have been populated somewhere before the test runs. If that data wasn’t populated, the test will fail and leave little indication to the developer what it wanted, or why… forcing them to dig through acres of code to find out where the data it was using was supposed to come from.

## The Enumerator

A unit test with each test case method name is only an enumeration, i.e. test1, test2, test3. As a result, the intention of the test case is unclear, and the only way to be sure is to read the test case code and pray for clarity.

## The Stranger

A test case that doesn’t even belong in the unit test it is part of. it’s really testing a separate object, most likely an object that is used by the object under test, but the test case has gone and tested that object directly without relying on the output from the object under test making use of that object for its own behavior. Also known as TheDistantRelative.

## The Operating System Evangelist

A unit test that relies on a specific operation system environment to be in place in order to work. A good example would be a test case that uses the newline sequence for windows in an assertion, only to break when ran on Linux.

## Success Against All Odds

A test that was written pass first rather than fail first. As an unfortunate side effect, the test case happens to always pass even though the test should fail.

## The Free Ride

Rather than write a new test case method to test another feature or functionality, a new assertion rides along in an existing test case.

The One A combination of several patterns, particularly TheFreeRide and TheGiant, a unit test that contains only one test method which tests the entire set of functionality an object has. A common indicator is that the test method is often the same as the unit test name, and contains multiple lines of setup and assertions.

## The Peeping Tom

A test that, due to shared resources, can see the result data of another test, and may cause the test to fail even though the system under test is perfectly valid. This has been seen commonly in fitnesse, where the use of static member variables to hold collections aren’t properly cleaned after test execution, often popping up unexpectedly in other test runs. Also known as TheUninvitedGuests

## The Slow Poke

A unit test that runs incredibly slow. When developers kick it off, they have time to go to the bathroom, grab a smoke, or worse, kick the test off before they go home at the end of the day.
