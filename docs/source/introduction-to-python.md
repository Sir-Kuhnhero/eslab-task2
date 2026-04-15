# Introduction to Python

Python is a high-level programming language that focuses on readable code and fast development. In this course context, it is useful because you can model ideas quickly, test them with small scripts and connect them to backend services without a heavy setup. Compared to lower-level languages, Python often lets you express the same logic in fewer lines, which is especially helpful when you are experimenting with algorithms and data processing.

## Table of Contents
1. [Loose Typing and Dynamic Behavior](#loose-typing-and-dynamic-behavior)
2. [Interpreter vs. Compiler](#interpreter-vs-compiler)
3. [Lists and Dictionaries](#lists-and-dictionaries)
4. [Immutable Types](#immutable-types)
5. [Python for Web Data: JSON and Schemas](#python-for-web-data-json-and-schemas)
6. [Useful Python Shortcuts](#useful-python-shortcuts)

## Loose Typing and Dynamic Behavior

Python is often described as dynamically typed. This means variables do not have a fixed type declaration in your source code. A name can point to an integer in one line and later point to a string in another line. This is convenient for rapid development, but it also means type mistakes can appear at runtime if values are used in unexpected ways.

```python
x = 10
# or
x = "ten"  # Same variable name, different type
```

People sometimes call this "loose typing" in everyday discussion, although the more precise term is dynamic typing. Python still has strong type rules during execution. For example, adding a number and a string directly will raise an error.

Python also supports implicit type conversion. For example, if you add an integer to a floating-point number, the interpreter automatically converts the integer to a float. However this only works for compatible types.

## Interpreter vs. Compiler

In C++, code is usually compiled ahead of time into machine code. The compiler performs many checks and optimizations before the program runs. The result is typically fast execution, but the build step can be longer and development changes often require recompilation.

Python is interpreted at runtime (technically compiled to bytecode and executed by the Python virtual machine). In practice, this gives a shorter edit-run cycle, which is great for prototyping and scripting. You can test small changes quickly, inspect values interactively and iterate faster during algorithm design. This difference is one reason Python is common in teaching, data processing and backend tooling, while C++ is often preferred when strict performance or low-level control is required.


An important consequence is that many type-related errors are discovered only when the relevant code path actually runs. For example, if one branch tries to add a string to an integer, Python will raise an error only when execution reaches that branch. If that branch is never executed during your tests, the problem can remain hidden.


## Lists and Dictionaries

Two of the most important Python data structures are lists and dictionaries. A list stores an ordered sequence of values, while a dictionary stores key-value mappings. Together they are enough to represent many real-world models such as schedules, graph nodes, configuration data and API payloads.

```python
tasks = ["T1", "T2", "T3"]
node_info = {"id": 1, "type": "compute", "available": True}

print(tasks[0])          # prints: T1
print(node_info["type"]) # prints: compute
```

Lists are useful when order matters or when you iterate over elements. Dictionaries are useful when you need fast lookup by a meaningful key. In backend code, dictionaries also map naturally to JSON objects, which makes data exchange straightforward.

## Python for Web Data: JSON and Schemas

Web APIs commonly exchange data in JSON format. JSON is a text format for structured data and maps naturally to Python types: objects become dictionaries, arrays become lists, numbers become int or float, booleans stay booleans and null becomes None.

In backend development, you usually parse input JSON, validate it, process it and return output JSON. Schema files define what valid input and output should look like. A schema can specify required fields, data types, ranges and nested structures. This helps catch errors early and makes API behavior more reliable.

```python
import json

payload = '{"job_id": 1, "wcet": 4}'
data = json.loads(payload)  # data is now a Python dict
print(data["wcet"])  # 4
```

When teams share schema definitions, frontend and backend developers can work consistently against the same contract.

## Useful Python Shortcuts

Python includes many built-in tools that reduce manual coding. Instead of writing long loops for common tasks, you can use expressive built-in functions and language patterns. This often improves readability and reduces mistakes.

- `max(<list>, key=<function>)`: returns the largest element. With `key`, you can choose what "largest" means.
- `min(<list>, key=<function>)`: returns the smallest element. With `key`, you can compare by a specific field.
- `len(<list>)`: returns how many elements are in the list.
- `sum(<list>)`: returns the sum of all numeric elements.
- `<list>[-1]`: accesses the last item in the list.
- `<list>.append(<item>)`: adds one item to the end of the list.
- `<list>.remove(<item>)`: removes the first matching item from the list.
- `all(<condition> for <item> in <iterable>)`: returns `True` only if every element satisfies the condition.