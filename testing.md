# Testing

<details>
<summary>What is the best way to unit test a function which uses external APIs, particularly DOM APIs? Mock / Stub window and document objects, or run your tests in those environments where they're available?</summary>

The best way to write unit tests for any external API's is to use mocks/Stubs. Mocks are effective as they mock the expected responses and rather than making the actual call, they simulate the call and return a response that you have already defined.  The mocked call ensures that the test would still pass even when the request is not necessarily made to the external API. Mocks ensure that the test execution time is reduced and that a situation where internet connectivity is not present your tests would still pass.

Running tests in the environment might lead to an increase in the execution time and situations where the api calls timeout hence causing your tests to fail. In worst case scenarios if at all an API call is required to call the base test class it could lead to a failure or an error while running all your tests that need the Base Test Class to be initialized before they run.
</details>

----

<details>
<summary>How do you write front-end integration tests </summary>
  
If you know the answer to this question, please submit a pull request with the answer.

</details>

_Waiting for response_


----

<details>
<summary> What are some of the frameworks/resources one can use to learn how to write front-end integration tests </summary>
  
If you know the answer to this question, please submit a pull request with the answer.

</details>

_Waiting for response_


----



