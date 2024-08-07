# Tests

Testing is a process used to identify the correctness, completeness and quality of the code. It includes a set of activities conducted with intent of finding a set of errors in the code so that it could be corrected before the product is released to the users.

## Unit Test

Unit testing is a crucial step when coding, it aims to validate the functions or methods work as intended and produce the expected output.

Unit tests are designed to test the smallest units of code, typically individual functions or methods, in isolation from the rest of the code. This helps ensure that each unit of code behaves as expected.

Python offers several libraries, such as unittest, doctest and PyTest, to write and execute unit tests.

## How to Use Unit Test

In Python, use build-in `unittest` to test functions of mathematical operations as an example to show how to use unit test in Python:

```py
# Import unnittest
import unittest

# Functions need to be tested
def add(x, y):
    return x + y

def sub(x, y):
    return x - y

def mul(x, y):
    return x * y

def div(x, y):
    return x / y

def if_pos(x):
    if x > 0:
        return True
    else:
        return False

# Write the test class to test the functions
## The class should inherit from the TestCase of unittest
class TestMath(unittest.TestCase):
    def test_add(self):
        ## assertEqual can test whether two elements are equal
        ## Here it checks whether the result of add(1, 2) is equal to 3
        self.assertEqual(add(4, -2), 2)

    def test_sub(self):
        self.assertEqual(sub(4, -2), 6)

    def test_mul(self):
        self.assertEqual(mul(4, -2), -8)

    def test_div(self):
        self.assertEqual(div(4, -2), -2)

    def test_if_pos(self):
        self.assertTrue(if_pos(4))
        self.assertFalse(if_pos(-2))
        ## assertRaises is used to raise a specific exception, here means TypeError will raise under the condition of if_pos('4') 
        with self.assertRaises(TypeError):
            if_pos('4')

# When writing test code in the same file as functions, the block below should be included. This block tells Python to run the tests if the script is executed directly. This block is not required if the test code is in a separate '.py' file.
if __name__ == '__main__':
    unittest.main()

```

Run the code the output is:

<div align=center>
<img width="600" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/12955b04-9f79-4d0c-883d-b24ca0e1bbde">
</div>

`.` means one test is passed, and there are 5 `.`, means all tests are passed. If revise the `add` function to multiply the two elements, and run the code. Apparently, the test will fail:

<div align=center>
<img width="600" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/33f8f68d-8d0a-4a2b-b96c-02775eb99e30">
</div>

**Note**

These tests are not executed sequentially in the order they are listed within the class. Therefore, each test method must be independent, and the result of each test method must not affect other test methods.

## Integration Test
Integration tests focus on testing the interactions between different components and modules of a system. Unlike unit tests, which isolate individual units of code, integration tests verify that these units work together correctly when integrated into larger parts of the system. Integration tests help ensure that the various components of a system can communicate and collaborate effectively and achieve the desired functionality.

## White and Black Box Testing

White box testing is a testing technique where the tester has access to the internal structure of the code being tested.

In contrast, black box testing is a testing technique where the internal workings being tested are not known to the tester, tester only focuses on the inputs and outputs of the code without considering its internal implementation details. For example, the tester might be calling the API to do the test, the tester doesn't need to know the internals of the API, and just make requests to the data in it.

## Test-Driven Development (TDD)

TDD is a software development approach in which tests are written before the actual implementation code. TDD can provide rapid feedback when code changes and ensure the code is tested and reliable.




