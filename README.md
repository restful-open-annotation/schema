# Schema for RESTful OA
A schema is a programmatically parsable description of a specificiation. It support independant validation without being restricted to any programming languages.

This directory stores the schemas for validating RESTful OA. The schemas are independant from language/format.

# json-schema.org
This is the first effort to define a parsable despcrition of RESTful OA specification.

## Files
json-schema-basic.json - The JSON Schema supports the core spec of OA.

json-schema.json - The Standard Schema is under development and will support the full spec of OA.

## Validation
Json-schema.org community has developed a number of tool to either validate a json-schema instance or validate a file against the instance [1]. They are available in different languages.

## Test examples
The following examples could be tested on [2], an online validator.

Example 1:
Correct:

	{
	    "target": "http://example.org",
	    "serializedAt": "2015-03-08T09:55:51",
	    "annotatedAt": "2015-03-08T09:55:51",
	    "@id": "54fc1ca77580581a828e0fa3"
	}

Wrong:

	{
	    "body": "http://example.org",
	    "serializedAt": "2015-03-08T09:55:51",
	    "annotatedAt": "2015-03-08T09:55:51",
	    "@id": "54fc1ca77580581a828e0fa3"
	}

A "target" is mandatory according OA specs.

Example 2:
Correct:

	{
	    "target": "http://example.org",
	    "body": {"@id": "http://xmlns.com/foaf/0.1/Person"},
	    "serializedAt": "2015-03-08T09:55:51",
	    "annotatedAt": "2015-03-08T09:55:51",
	    "@id": "54fc1ca77580581a828e0fa3"
	}

Wrong:

	{
	    "target": "http://example.org",
	    "body": 12345,
	    "serializedAt": "2015-03-08T09:55:51",
	    "annotatedAt": "2015-03-08T09:55:51",
	    "@id": "54fc1ca77580581a828e0fa3"
	}

A "body" has to be a URI or following Web Annotation WG context [3].

Example 3:
Correct:

	{
	    "target": "http://example.org",
	    "serializedAt": "2015-03-08T09:55:51",
	    "annotatedAt": "2015-03-08T09:55:51",
	    "@id": "54fc1ca77580581a828e0fa3"
	}

Wrong:

	{
	    "target": "http://example.org",
	    "serializedAt": "3 Aug 2015, 09:55:51",
	    "annotatedAt": "3 Aug 2015, 09:55:51",
	    "@id": "54fc1ca77580581a828e0fa3"
	}

The above example is because that an OA timestamp must be expressed in xsd:dateTime.


# References
[1] http://json-schema.org/implementations.html
[2] http://json-schema-validator.herokuapp.com/index.jsp
[3] http://www.w3.org/TR/2014/WD-annotation-model-20141211/#json-ld-context
