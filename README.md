# Data-Structures-and-Algorithms-in-Python
Data Structures and Algorithms by Python Google Colab

**Recursion in Python**

"Of all ideas I have introduced to children, recursion stands out as the one idea that is particularly able to evoke an excited response."

![68747470733a2f2f7468656275726e696e676d6f6e6b2e636f6d2f77702d636f6e74656e742f75706c6f6164732f323031372f30382f726563757273696f6e2d30312e706e67](https://user-images.githubusercontent.com/89307294/164760776-9bb710b4-2433-4fba-ab32-d251261e101c.png)
Image: theburningmonk.com

**1.Iterative Products Delivery**

<img width="1097" alt="Screen Shot 2565-04-23 at 00 04 15" src="https://user-images.githubusercontent.com/89307294/164761333-26a40597-fb76-44c9-9b26-d3ae73fda558.png">

Image: realpython.com

#Recursive Exercise 1 Iterative Products Delivery
```
houses = ["Nadech's House","Yaya's Houses","frank's Houses","Mario's Houses"]
def deliver_products_iteratively():
  for house in houses:
    print("Delivering product to",house)
#call function
deliver_products_iteratively()
```
**2.The Structure of a Recursive Algorithm**

Divide it into subproblems and apply the same strategy

<img width="1090" alt="Screen Shot 2565-04-23 at 00 06 50" src="https://user-images.githubusercontent.com/89307294/164761830-77a5b5b1-4263-4fcf-84f9-0ebcc8ba5cff.png">

Image: realpython.com

All Recursive Functions share a common structure made up of 2 parts:
1) Base Case
2) Recursive Case


#Recursive Exercise 2 Recursive Products Delivery
```
houses = ["nadach's house","yaya's house","frank's house","mario's house"]
def deliver_products_recursively(houses):
  #worker doing his work --> base case == 1
  if len(houses) == 1:
    house = houses[0]
    print("Delivering products to",house)
  #manager doing his work --> recursive case
  else:
    mid = len(houses) // 2
    first_half = houses[:mid]
    second_half = houses[mid:]
    #divides his work among two workers
    deliver_products_recursively(first_half)
    deliver_products_recursively(second_half)
#call recursive function
deliver_products_recursively(houses)
```
**3.Calculating Factorial**

<img width="437" alt="Screen Shot 2565-04-23 at 00 12 09" src="https://user-images.githubusercontent.com/89307294/164762469-6ae8112b-001c-4e1e-a29f-42fb4eba66cb.png">


#Recursive Exercise 3 Calculating Factorial
```
def factorial_recursive(n):
  # base case 1! = 1
  if n == 1:
    return 1
  # recursive case: n! = n * (n-1)!
  else:
    return n * factorial_recursive(n-1)
#call function recursive function
factorial_recursive(6)
```
**4.Maintaining State --> Sum Recursive**

<img width="1079" alt="Screen Shot 2565-04-23 at 00 15 46" src="https://user-images.githubusercontent.com/89307294/164762967-c755b099-1578-4dc0-a969-b48afa9b518c.png">


#Recursive Exercise 4.1 Assign Arguments
```
def sum_recursive(current_number, accumulated_sum):
  #base case
  #return the final state
  if current_number == 11:
    return accumulated_sum
  #recursive case
  #thread the state through the recursive call
  else:
    print(accumulated_sum)
    return sum_recursive(current_number + 1, accumulated_sum + current_number)
#call sum recursive function
#1+2+3+4+5+6+7+8+9+10
sum_recursive(1,0)
```

#Recursive Exercise 4.2 Global Mutable State
```
current_number = 1
accumulated_sum = 0
def sum_recursive():
  global current_number
  global accumulated_sum
  #base case
  if current_number == 11:
    return accumulated_sum
  #recursive case
  else:
    accumulated_sum = accumulated_sum + current_number
    current_number = current_number + 1
    print(accumulated_sum)
    return sum_recursive()
#call sum recursive function
sum_recursive()
```

#Recursive Exercise 4.3 A List is an example of a Recursive Data Structure
```
def list_sum_recursive(input_list):
  #base case
  if input_list == []:
    return 0
  #recursive case
  else:
    head = input_list[0]
    smaller_list = input_list[1:]
    print("this is data of smaller_list ->",smaller_list)
    print("this is data of head ->",head)
    return head + list_sum_recursive(smaller_list)
#call list sum recursive function
list_sum_recursive([1,2,3,4,5,6,7,8,9,10])
```

**5.List Input of a Recursive Data Structure**

https://user-images.githubusercontent.com/89307294/164764009-ca64c5aa-8574-497e-a1ae-0dac7f71189b.mov

Image: realpython.com

```
#Recursive Exercise 5.1 
def attach_head(element, input_list):
  return [element] + input_list
#Call List of recursive function
#attach_head("i", attach_head("Love", attach_head("Recursion", attach_head(555, []))))
attach_head('I',                                            #(4) will return [I, Love, Recurtion, 555]
            attach_head('Love',                             #(3) will return [Love, Recursion, 555]
                        attach_head('Recursion',            #(2) will return [Recursion, 555]
                                    attach_head(555, [])))) #(1) will return [555]
```
```
#Recursive Exercise 5.2
Line = [1,2,3,4,5,6]
def howmanyin(lst):
  if lst[1:]:
    print("me and the guys behind")
    # print(lst[1:])
    return 1 + howmanyin(lst[1:])
  else:
    print("just me")
    return 1
#call recursive function
howmanyin(Line)
```
**6.Fibonacci**

https://user-images.githubusercontent.com/89307294/164764285-c093ecb5-6e95-4b25-9b47-c9a27dfe0fdb.mov

```
#Recursive Exercise 6
def fibonacci_recursive(n):
  #Base case
  if n <= 1:
    return n
  #Recursive case
  else:
    return (fibonacci_recursive(n-1) + fibonacci_recursive(n-2))
#Take input from the user
nterms = int(input("How many terms? "))
#Check if the number of terms is valid
if nterms <= 0:
  print("Please enter a positive integer")
else:
  print("Fibonacci sequence: ")
  for i in range(nterms):
    print("This data values: ",i)
    print(fibonacci_recursive(i))
```
