### Python Websites and systems with Python

The library used to this is `Flet`

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
