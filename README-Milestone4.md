# README-M4
# Milestone 4 - stream-based styles

## Overview
This milestone extends the functionality of the `JSONObject.java` class.
The goal is to add streaming methods that allow the client code to chain operations on JSON nodes.

## Changes Made

### Production Code
We defined JSONNode, as an object with path and value. This is used by the method buildNodesFromJson and toStream.
We defined the method buildNodesFromJSON recursively travels the JSON tree and flattens the JSONNode objects into a list of key value pairs.
We defined the method toStream uses the output from buildNodesFromJSON and returns it as a stream to the client.

### Test Code
New test cases were added to `JSONObjectTest.java` corresponding to the new methods:

| Test Method                         | Description                                                   |
|:------------------------------------|:--------------------------------------------------------------|
| `testToStreamExtractTitles`         | Test to extract titles from XML and validate their values.    |
| `testToStreamPrintAllNodes`         | Test to print all the nodes of the XML in the stream.         |
| `testEmptyXML`                      | Test to ensure empty XML returns only the root node.          |
| `testSingleElementXML`              | Test to ensure single element XML is correctly handled.       |
| `testNestedEmptyElements`           | Test to ensure empty nested elements are handled.             |
| `testNestedElements`                | Test to ensure multiple nested elements are handled.          |
| `testNestedElementsWords`           | Test to ensure nested elements with text content are handled. |
| `testAttributesOnlyXML`             | Test to ensure XML with attributes is handled properly.       |
| `testMultipleNestedArrays`          | Test to ensure multiple nested arrays are handled properly.   |


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
mvn clean test -Dtest=JSONObjectTest#testToStreamExtractTitles
mvn clean test -Dtest=JSONObjectTest#testToStreamPrintAllNodes
mvn clean test -Dtest=JSONObjectTest#testEmptyXML
mvn clean test -Dtest=JSONObjectTest#testSingleElementXML
mvn clean test -Dtest=JSONObjectTest#testNestedEmptyElements
mvn clean test -Dtest=JSONObjectTest#testNestedElements
mvn clean test -Dtest=JSONObjectTest#testNestedElementsWords
mvn clean test -Dtest=JSONObjectTest#testAttributesOnlyXML
mvn clean test -Dtest=JSONObjectTest#testMultipleNestedArrays
```