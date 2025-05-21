# README-M3.md

# Milestone 3 - JSON-java XML Providing interfaces with higher-order functions

## Overview
This milestone extends the functionality of the `XML.java` class by introducing a new overloaded method to support general modification of keys using a `JSONObject`:

- `public static JSONObject toJSONObject(Reader reader, Function<String, String> keyTransformer)`

The goal is to allow users to support general modification of keys without processing the entire structure unnecessarily.

## Changes Made

### Production Code
- Added a new overloaded method `toJSONObject(Reader reader, Function<String, String> keyTransformer)` to support general modification of keys.
- Introduced a private helper method `parse3(...)`, adapted from the original parser logic, to efficiently locate and replace the specific XML keys.

### Test Code
New test cases were added to `XMLTest.java` corresponding to the new method:

| Test Method                         | Description                                           |
|:------------------------------------|:------------------------------------------------------|
| `testKeyTransformation`             | Test to add a specified string to a key.              |
| `testKeyReversalTransformation`     | Test to reverse the key string.                       |
| `testUpperCaseKeyTransformation`    | Test to make key all uppercase letters.               |
| `testLowerCaseKeyTransformation`    | Test to make key all lowercase letters.               |
| `testEmptyXmlInputReturnsEmptyJson` | Test to ensure an empty XML input returns empty JSON. |
| `testEmptyRootTag`                  | Test to ensure an empty root tag is treated as empty. |
| `testWhitespaceOnlyTagContent`      | Test to ensure whitespace is treated as empty.        |


## Notes
- No existing production or test code was altered.
- The new tests are traceable and focus only on verifying the newly added methods.
- All tests, including pre-existing ones, pass successfully by running:
  ```bash
  mvn clean
  mvn compile
  mvn test
  ```

## Running New Individual Test Cases
To run individual new test cases:

```bash
mvn clean test -Dtest=XMLTest#testKeyTransformation
mvn clean test -Dtest=XMLTest#testKeyReversalTransformation
mvn clean test -Dtest=XMLTest#testUpperCaseKeyTransformation
mvn clean test -Dtest=XMLTest#testLowerCaseKeyTransformation
mvn clean test -Dtest=XMLTest#testEmptyXmlInputReturnsEmptyJson
mvn clean test -Dtest=XMLTest#testEmptyRootTag
mvn clean test -Dtest=XMLTest#testWhitespaceOnlyTagContent
```