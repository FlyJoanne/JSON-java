# README-M2.md

# Milestone 2 - JSON-java XML Partial Extraction and Replacement

## Overview
This milestone extends the functionality of the `XML.java` class by introducing two new overloaded methods to support partial extraction and replacement of XML content using a `JSONPointer`:

- `public static JSONObject toJSONObject(Reader reader, JSONPointer path)`
- `public static JSONObject toJSONObject(Reader reader, JSONPointer path, JSONObject replacement)`

The goal is to allow users to efficiently extract or replace a specific part of an XML document without processing the entire structure unnecessarily.

## Changes Made

### Production Code
- Added a new overloaded method `toJSONObject(Reader, JSONPointer)` to extract the target XML segment corresponding to a given JSONPointer path and convert it into a JSONObject.
- Added another overloaded method `toJSONObject(Reader, JSONPointer, JSONObject)` to replace a specific target in the XML with a given JSONObject during the parsing process.
- Introduced a private helper method `parse2(...)`, adapted from the original parser logic, to efficiently locate, extract, and optionally replace the specific XML path.

### Test Code
New test cases were added to `XMLTest.java` corresponding to the new methods:

| Production Method | Test Method | Description |
|:---|:---|:---|
| `toJSONObject(Reader, JSONPointer)` | `toJSONObjectPointerExtractTest` | Tests extracting a single-level object using JSONPointer. |
| `toJSONObject(Reader, JSONPointer)` | `toJSONObjectPointerDeepExtractTest` | Tests extracting a deeply nested object using JSONPointer. |
| `toJSONObject(Reader, JSONPointer, JSONObject)` | `toJSONObjectPointerReplaceTest` | Tests replacing a single-level object using JSONPointer. |
| `toJSONObject(Reader, JSONPointer, JSONObject)` | `toJSONObjectPointerDeepReplaceTest` | Tests replacing a deeply nested object using JSONPointer. |
| `toJSONObject(Reader, JSONPointer)` | `toJSONObjectPointerExtractErrorTest` | Tests extracting a non-existing path and expects a JSONException. |
| `toJSONObject(Reader, JSONPointer, JSONObject)` | `toJSONObjectPointerReplaceErrorTest` | Tests replacing a non-existing path and expects a JSONException. |

All new tests follow the required naming conventions (`methodNameTest()`) and are located in `src/test/java/org/json/junit/XMLTest.java`.

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
mvn clean test -Dtest=XMLTest#toJSONObjectPointerExtractTest
mvn clean test -Dtest=XMLTest#toJSONObjectPointerDeepExtractTest
mvn clean test -Dtest=XMLTest#toJSONObjectPointerReplaceTest
mvn clean test -Dtest=XMLTest#toJSONObjectPointerDeepReplaceTest
mvn clean test -Dtest=XMLTest#toJSONObjectPointerExtractErrorTest
mvn clean test -Dtest=XMLTest#toJSONObjectPointerReplaceErrorTest
```