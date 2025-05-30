# README-M5
# Milestone 5 - asynchronous methods

## Overview
This milestone extends the functionality of the `XML.java` class.
The goal is to add asynchronous methods that allow the client code to proceed, and specifying what to do when the JSONObject becomes available. 

## Changes Made

### Production Code
We added an asynchronous method in the 'XML' class, which converts XML to JSON asynchronously in a new thread.

```bash
public static void toJSONObject(Reader reader,
                                Consumer<JSONObject> onSuccess,
                                Consumer<Exception> onError)
```  

### Test Code
New test cases were added to `XMLTest.java` corresponding to the new methods:

| Test Method             | Description                                                            |
|:------------------------|:-----------------------------------------------------------------------|
| `testWriteJsonToString` | Tests successful async parsing of simple XML and conversion to string. |
| `testExtractSubObject`  | Tests extracting a nested JSON object from parsed XML.                 |
| `testCheckKeyExists`    | Verifies that a specified key exists in the resulting JSON object.     |
| `testAddPrefixToKeys`   | Tests transforming keys of a JSON object by adding a prefix.           |
| `testReplaceSubObject`  | Tests modifying a sub-object within the JSON.                          |
| `testEmptyXmlInput`     | Tests behavior when input XML is empty (expects empty JSON).           |
| `testBadXml`            | Tests that bad XML triggers the error callback.                        |


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
mvn clean test -Dtest=XMLTest#testWriteJsonToString
mvn clean test -Dtest=XMLTest#testExtractSubObject
mvn clean test -Dtest=XMLTest#testCheckKeyExists
mvn clean test -Dtest=XMLTest#testAddPrefixToKeys
mvn clean test -Dtest=XMLTest#testReplaceSubObject
mvn clean test -Dtest=XMLTest#testEmptyXmlInput
mvn clean test -Dtest=XMLTest#testBadXml

```