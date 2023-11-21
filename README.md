# Pytest-Python-Testing-Framework


## Introduction

As a backend engineer or a QA/test Engineer, ensuring the quality and reliability of your code is important. One way to achieve this is by using Python testing frameworks to automate the testing process and identify bugs or issues in your code before the piece of software is released or deployed.



They offer the following benefits:

- Testing frameworks improve code quality.

- Automated testing saves time and effort.

- Code reusability optimises testing efforts and reduces duplication.

- Python testing frameworks integrate seamlessly with other tools, modules and libraries.



In this step-by-step guide, you will learn how to implement PyTest - one of Python's most popular Python testing frameworks.



## Prerequisites


Before diving into the details of Python testing frameworks, let's first focus on the prerequisites for implementing PyTest.


-   **Python Installation**: Please ensure you have Python installed on your system. One can download the latest version of Python from the official [Python website](https://www.python.org/downloads/).

-   **Pip Installation**: Pip(package installer for Python) is a tool used to manage packages, libraries and dependencies in Python. It allows us to install and manage Python packages. Make sure you have pip installed on your system.

You can check if pip is installed by running the following command in your command prompt/terminal:


```line_numbers,python
python -m pip --version
```
or

```line_numbers,python
python3 -m pip --version
```
You can check out this official Python website to [install packages](https://packaging.python.org/en/latest/tutorials/installing-packages/).



## What is a Python Testing Framework

Python Testing framework is a set of tools and libraries that provide a structure and guidelines to write and execute tests in Python for Test automation. It makes sure that the code meets the desired quality standards. It is essential and useful for every Backend developer, software engineer, DevOps and QA/Test engineer.  A few famous and widely used Python testing frameworks are Pytest, PyUnit, DocTest, Testify, Robot and many more.


## Implementing PyTest

### Installing PyTest


To get started with PyTest, you need to install it on your system. Open your terminal and run the following command:

```line_numbers,python
pip install pytest
```

This command will download and install the latest PyTest version and its dependencies.


### Writing Test Cases

Now that PyTest is installed let's start writing basic unit test cases.

Please create a new Python file and name it ```test_backend.py```. This file will define our test cases using PyTest's syntax.

<$>[note]
**Note**:  By default, PyTest will discover and run all the test cases in files with names starting with **"test_"** or ending with **"_test"**.The pytest discovery process will recursively scan the current folder and its subfolders for files starting with names either **"test_"** or ending with **"_test"**. Tests located in those files are then executed.
<$>



```line_numbers,python
import pytest

def test_addition():

    assert 3 + 3 == 6

def test_subtraction():

    assert 5 - 4 == 1

def test_multiplication():

    assert 4 * 4 == 16

def test_division():

    assert 10 / 2 == 5

```

In the above example, we have defined four basic unit test cases as functions: **test_addition**, **test_subtraction**, **test_multiplication**, and **test_division**. The ```assert``` keyword is used when debugging code and lets you test if a certain condition in your code returns True; if not, it will return an **AssertionError**.


### Running Test Cases, Running Specific tests

To run the tests, go to the folder where you saved the test_backend.py file and then execute the below command in your terminal or command prompt:

```line_numbers,python
pytest
```

Or,

```line_numbers,python
python -m pytest
```

Output:

```
[secondary_label Output]

test session starts
==================================================

platform darwin -- Python 3.9.6, pytest-7.4.3, pluggy-1.3.0

rootdir: ~/Python Testing Frameworks

collected 4 items

test_backend.py ....
==================================================

4 passed in 0.01s                                                                                                                                                                 [100%]
```

When using PyTest, you don't have to manually run each test case in your file. The tool will automatically find and execute all the defined test cases. If everything goes well and all the assertions are true, you'll get a nice summary of test results along with the number of passed tests as shown above.


Let’s assume that one of the tests fails then, we would notice the following output:

```
[secondary_label Output]

test session starts
==================================================

platform darwin -- Python 3.9.6, pytest-7.4.3, pluggy-1.3.0

rootdir: ~/Python Testing Frameworks

collected 4 items

test_backend.py ...F  
==================================================                                                                                                                                                                 [100%]

FAILURES
==================================================

test_division 

    def test_division():

>       assert 10 / 2 == 6

E       assert (10 / 2) == 6

test_backend.py:13: AssertionError

short test summary info
==================================================

FAILED test_backend.py::**test_division** - assert (10 / 2) == 6

1 failed, 3 passed in 0.01s 

```

### Test Discovery


PyTest provides powerful test discovery capabilities that allow you to organize your test cases in a structured manner. **By default, PyTest will discover and run all the test cases in files with names starting with "test_" or ending with "_test".** However, you can customise the test discovery process using various command-line options or by configuring a  ```pytest.ini``` file.

For example, one can specify a specific directory to search for test modules by running the following command:

```line_numbers,python
pytest tests/
```

This command will only run the test cases inside the **"tests"** directory.


### Test Fixtures

Test Fixtures in Pytest are amazing components that can be reused to set a fixed baseline for your test cases. They come in handy when you need to create preconditions for your tests and when you want to clean up any resources once your tests are done. PyTest makes it easy to define and use test fixtures elegantly.

To define a test fixture, you need to use the ```@pytest.fixture``` decorator. For example, a fixture called ```db``` defined below,  sets up a database connection and then closes the connection after operating. We can define this fixture as follows:

```line_numbers,python

import pytest

@pytest.fixture

def db():

    # Set up the database connection

    db = create_db()

    yield db

    # Clean up the database connection

    db.close()

```

In this example, the ```yield``` statement defines the code executed after running the test cases. The yield keyword is used to control the flow of a generator function, which is similar to a return statement used for returning values in Python.

To use a fixture in a test case, you must include it as an argument in the test function.

For example:

```line_numbers,python
def query_test(db):
    results = db.query("SELECT * FROM users")
    assert len(result) == 12
```

In this test case, the ```db``` fixture will be automatically injected into the ```query_test()``` function, allowing you to use it to perform database operations. Fixtures are handy for developers to prepare a specific testing environment, such as database connections, API clients, or mock objects. By using fixtures, developers can ensure that tests are isolated and repeatable.

Test engineers can also use fixtures to prepare the system under test, manage test data, or simulate complex scenarios.

Moreover, fixtures can be utilised to handle resource cleanup after tests, improving test suite reliability and maintainability.


## Conclusion

In this tutorial, we learned to implement and use PyTest, one of the most popular and feature-rich Python testing frameworks and provided a step-by-step guide on implementing it in Python.

It is essential to continuously write and update test cases as your codebase evolves. By investing time and effort in testing, you can catch bugs early, improve code quality, and deliver more robust and reliable software.






