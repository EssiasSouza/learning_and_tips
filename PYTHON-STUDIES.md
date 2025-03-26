### Python compiler commands

Arquivo `version.txt`
````
# UTF-8 encoding
VSVersionInfo(
  ffi=FixedFileInfo(
    filevers=(1, 2, 1, 0),
    prodvers=(1, 2, 1, 0),
    mask=0x3f,
    flags=0x0,
    OS=0x40004,
    fileType=0x1,
    subtype=0x0,
    date=(0, 0)
  ),
  kids=[
    StringFileInfo(
      [
        StringTable(
          '040904b0',
          [
            StringStruct('CompanyName', 'Corpay'),
            StringStruct('FileDescription', 'TRX Inspector'),
            StringStruct('FileVersion', '1.2.1'),
            StringStruct('InternalName', 'TRX Inspector'),
            StringStruct('LegalCopyright', '© 2025 Corpay'),
            StringStruct('OriginalFilename', 'main_trx_inspector.exe'),
            StringStruct('ProductName', 'TRX Inspector'),
            StringStruct('ProductVersion', '1.2.1'),
            StringStruct('Comments', 'Compilado em 2024-03-25')
          ]
        )
      ]
    ),
    VarFileInfo([VarStruct('Translation', [1033, 1200])])
  ]
)
````


````
pyi-makespec --version-file version.txt .\main_trx_inspector.py
````
````
pyinstaller --onefile --windowed --version-file version.txt .\main_trx_inspector.py
````

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
