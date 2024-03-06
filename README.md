# Summary of Unit 2: Control Flow
This is a summary of the topics covered in Unit 2: Control Flow. 

## Booleans
A boolean is a value that can either be true or false. Booleans are a new data type, adding to your existing knowledge of integers, floats, and strings in Python. 

For example, here are two boolean variables:

```python
has_passport = True
has_drivers_license = False
```

Note the following about the above variable declaration:
- Booleans are special values that must begin with a capital letter, e.g. `True` and `False`.
- Booleans do not use quotes. 

## `if` / `elif` / `else` Statements
Thus far, we have been writing sequential programs. These are programs that run linearly, step-by-step, from start to finish. A sequential program might look something like this:

<img src="images/sequential.png" alt="sequential" height="280px" />

Programs often need to do different things based on circumstances. This leads us to a programming concept known as **selection**, which might look something like this: 

<img src="images/selection.png" alt="sequential" height="350px" />

In Python, the `if`, `elif`, and `else` statements are used for decision-making in your code. These statements allow you to execute certain blocks of code based on whether certain conditions are true or false.

When evaluating a single condition, you might use:

```python
if condition_is_true:
    # Code block to execute if condition is True
else:
    # Code block to execute if condition is False
```

If there are more conditions to evaluate, you can add use `elif` (often pronounced as "*else if*")to test these conditions:


```python
if condition1_is_true:
    # Code block to execute if condition1 is True
elif condition2_is_true:
    # Code block to execute if condition1 is False, but condition2 is True
else:
    # Code block to execute if both condition1 and condition2 are False
```

Note the use of **indentation** in the code blocks above. It's crucial to pay attention to the indentation in Python. Indentation determines which lines of code belong to which block. Incorrect indentation can lead to syntax errors or unintended behavior.

## Comparison Operators

Comparison operators are used to compare values. They return a boolean value — either `True` or `False` — depending on the comparison result. These operators are often used within if statements to evaluate conditions.

Operator | Definition
---|---
`==` | Equal to
`!=` | Not equal to
`<` | Less than
`>` | Greater than
`<=` | Less than or equal to
`>=` | Greater than or equal to

Note the use of `==` as a comparison operator for *equality*. There is an important distinction from the single `=` symbol used in variable assignment. They are **not interchangeable**.

Example:

```python
x = 5
y = 10

if x < y:
    print("x is less than y")
else:
    print("x is greater than or equal to y")
```

You can use variables or explicitly defined values around these comparison operators. For example:

```python
target_score = 15
user_score = 19

if user_score > target_score:
    print("Congratultions! You did it!")
else:
    print("Sorry, try again.")
```

The above program would function exactly the same as:

```python
user_score = 19

if user_score > 15:
    print("Congratultions! You did it!")
else:
    print("Sorry, try again.")
```

## Logical Operators

Logical operators are used to combine multiple conditional statements. They allow you to create more complex conditions by combining simpler conditions.

Operator | Definition
---|---
`and` | Returns `True` if both conditions are `True`
`or` | Returns `True` if at least one condition is `True`
`not` | Returns `True` if the condition is `False`, and vice versa

Example:

```python
has_passport = True
has_visa = False

if has_passport and has_visa:
    print("You may enter the country.")
elif has_passport and not has_visa:
    print("You need a visa to enter the country.")
elif has_visa and not has_passport:
    print("You need a passport to enter the country.")
else:
    print("You need a passport and visa to enter the country.")
```

### Order of Operations
You can combine logical operators with parentheses to force certain conditions to evaluate first. For example:

```python
customer_age = 67
has_membership = True

if (customer_age <= 18 or customer_age >= 65) and has_membership:
    print("Discount applies.")
else:
    print("No discount.")
```

The above code will evaluate the `customer_age` first with the logical `or` operator. The result is then evaluated with the next `and` expression.


## Style with Conditionals
There are a few notes for good programming style when using conditionals:
### Whitespace
- Leave whitespace around conditional operators, as you would arithmetic operators.
- Use logical paragraphs and keep code blocks together their respective conditions.

### Example: Whitespace around operators
#### Good
```python
if user_score > 15:
    print("Congratultions! You did it!")
```

#### Bad
```python
if user_score>15:
    print("Congratultions! You did it!")
```

### Example: Use logical paragraphs
#### Good
```python
if has_passport and has_visa:
    print("You may enter the country.")
elif has_passport and not has_visa:
    print("You need a visa to enter the country.")
elif has_visa and not has_passport:
    print("You need a passport to enter the country.")
else:
    print("You need a passport and visa to enter the country.")
```

#### Bad
```python
if has_passport and has_visa:


    print("You may enter the country.")
elif has_passport and not has_visa:
    print("You need a visa to enter the country.")

elif has_visa and not has_passport:
    print("You need a passport to enter the country.")
else:
    print("You need a passport and visa to enter the country.")
```

## `While` Loop
Programs often need to run a block of code repeatedly. This is done with a loop. One of the main loop constructs is called a `while` loop, which repeatedly executes a block of code as long as a specified condition is true. 

Here's the basic syntax:
```python
while condition:
    # code block to be executed
```

The condition is a boolean expression (see Comparison Operators section, above) that determines whether the loop should continue or stop. The code block under the while statement is executed repeatedly until the condition becomes `False`.

### Example
This code:

```python
num = 1
while num <= 5:
    print(num)
    num += 1
```

would result in the output:

```
1
2
3
4
5
```
The loop prints numbers from 1 to 5 because the condition `num <= 5` is true for those values of num.


## `For` Loop
A `for` loop in Python **iterates** over a sequence and executes a block of code for each item in the sequence. Here's the basic syntax:
```python
for item in sequence:
    # code block to be executed
```

`item` is a variable that represents the current item in the sequence being processed. `sequence` is any iterable object that contains multiple items. For our examples we used the `range()` function to give us a sequence o numbers.

## Using the `range()` Function
The `range()` function in Python generates a sequence of numbers based on the parameters provided. It's commonly used with for loops to execute a block of code a specific number of times.

Here's how the `range()` function works:

```python
range(start, stop, step)
```

* `start` (optional): The starting value of the sequence. If not provided, it defaults to 0.
* `stop`: The end value of the sequence. The sequence will stop before reaching this value.
* `step` (optional): The step size between each number in the sequence. If not provided, it defaults to 1.

### Generation of Sequence
When you call `range(start, stop, step)`, it generates a sequence of integers starting from `start` (inclusive) up to, but not including, `stop`. The numbers in the sequence are incremented by step.

#### Examples
* If you call `range(5)`, it generates a sequence from `0` to `4`.
* If you call `range(1, 6)`, it generates a sequence from `1` to `5`.
* If you call `range(1, 10, 2)`, it generates a sequence of odd numbers from `1` to `9`, i.e. `1`, `3`, `5`, `7`, `9`.

### Usage with `for` Loops
The `range()` function is commonly used with `for` loops to iterate a specific number of times. For example:
```python
for i in range(5):
    print(i)
```

This will print numbers from `0` to `4`, as the `range(5)` generates a sequence starting from `0` and ending before `5`.
