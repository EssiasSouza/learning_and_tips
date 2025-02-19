### Python Websites and systems with Python

The library used for this is `Flet`

To execute the main function on Flet is necessary to define a main function and call using the line bellow:

````
flet.app(main_function_name)

````

To apply elements on the web page or UI, first declare the variable using a Flet function with the information as label.

````
def main(page):
  title = flet.Text("Text do show")
  page.add(title)

  button = flet.ElevatedButton("Click to begin"
  page.add(button)
````

# DATA MANAGEMENT

## List 
Is a ordered and mutable collection. Allows duplicated members.
list = ['car', True, 2, 3.5]

## Tuple
Is a ordered and unmutable collection. Allows duplicated members.
tuple = ("car", True, 2, 3.5)

## Dictionary
Is a ordered and mutable collection. Doesn't allow duplicated members.
dictionary = {"Name": "Car", "Logic": True, "Number": 2, "OtherNumber": 3.5}

## Set
Is a non ordered and non indexed collection. It doesn't allow duplicated members.
set = {"car", True, 2, 3.5}