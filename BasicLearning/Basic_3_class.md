# Class

## What is Class in Python?

### Real-Life Example
There are list, dictionary in python we use to organise data, class provides a means of bundling data and funtionality together. In python class is a code template to create objects. 

For example, a school needs to collect all the personal information of all freshmen, the first thing to do is to create an information spreadsheet template. The student's attributes like student name, student ID, gender, nationality, telephone number ect., maybe included in the template, when the new semester begins, the school will prepare the spreadsheets to give out to the freshmen, when students receive the information spreadsheet, they will fill out with their own information. After finishing collecting information of all freshmen, school can use these information to manage all the students.

This process just exactly like how `class` works in python. Creating the information spreadsheet template is like calling the function `class` to define a class, the attributes like student name, student ID, gender, nationality, telephone number ect. is called `member variables`, this is also the constructor of class. Giving every student a spreasheet is called creating objects, also called instances in python, and filling out the information is called assigning attributes to the objects, we can define some functions to access and process the collected data, these functionalities is call `member methods`.

### How to Use Class in Python?

1. Creating class by calling the keyword `class`:
```py
class FreshmenTem: #The name of classes are best using the format of CamelCase, refer to this website: https://google.github.io/styleguide/pyguide.html
  pass
```
By the code above, we create an empty class.

2. Definition of member variables and member methods:
```py
class FreshmenTem:
    #Member variables aslo called constructor:
    '''
    The format of the constructor is like this:
    def __init__(self, variable_1, variable_2, variable_3, ...)
    self.m_name_1 = variable_1
    self.m_name_2 = variable_2
    self.m_name_3 = variable_3 ("m" means "member")
    Attention: The word "self" is always provided in the first argument.
    '''
    def __init__(self, name, ID, gender, nationality, telephone):
        self.m_name = name
        self.m_ID = ID
        self.m_gender = gender
        self.m_nationality = nationality
        self.m_tele = telephone
    """
    The format of the member method is pretty much the same with the member variables. But keep it in mind that when we want to call the member variables, we should use the keyword "self." following with the name of the variables.
    """
    def say_hi(self, message):
        print(f"I'm {self.m_name}, I come from {self.m_nationality}, my telephone number is {self.m_tele}, {message}")
```

3. Create objects:
```py
#Use the class
student_1 = FreshmenTem("fanfan", "1701", "female", "China", "123456")
student_2 = FreshmenTem("xixi", "1702", "Male", "China", "123789")

#When call the function in the class, we need to use the name of the object followed by a dot and the name of the function: object.function_name(parameter)
student1.say_hi("I'm so excited to meet everyone!")
student2.say_hi("Hope you guys have a nice day!")
```

Let's run the code:
```py
I'm fanfan, I come from China, my telephone number is 123456, I'm so excited to meet everyone!
I'm xixi, I come from China, my telephone number is 123789, Hope you guys have a nice day!
```

## Object-Oriented Programming

Python is an "object-oriented" programming language, this means that almost all the code is implemented using classed, programmers use classes to keep related things together. By using class in python, we can organise and structure data in a single unit, reduce duplication.
