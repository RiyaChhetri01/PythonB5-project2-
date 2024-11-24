# PythonB5-project2-
calculator making
# GUI Calculator 🧮

A simple calculator built with Python's `tkinter` library. Here's the main code:

## Calculator Code

```python
from tkinter import *

first_number = second_number = operator = None

def get_digit(digit):
    current = result_label['text']
    new = current + str(digit)
    result_label.config(text=new)

def clear():
    result_label.config(text='')

def get_operator(op):
    global first_number, operator
    first_number = int(result_label['text'])
    operator = op
    result_label.config(text='')

def get_result():
    global first_number, second_number, operator
    second_number = int(result_label['text'])
    if operator == '+':
        result_label.config(text=str(first_number + second_number))
    elif operator == '-':
        result_label.config(text=str(first_number - second_number))
    elif operator == '*':
        result_label.config(text=str(first_number * second_number))
    else:
        if second_number == 0:
            result_label.config(text='Error')
        else:
            result_label.config(text=str(round(first_number / second_number, 2)))

root = Tk()
root.title('Calculator')
root.geometry('300x380')
root.resizable(0, 0)
root.configure(background='black')

result_label = Label(root, text='', bg='black', fg='white')
result_label.grid(row=0, column=0, columnspan=5, pady=(50, 25), sticky='w')
result_label.config(font=('verdana', 30, 'bold'))

btn7 = Button(root, text='7', bg='#00a65a', fg='black', width=5, height=2, command=lambda: get_digit(7))
btn7.grid(row=1, column=0)
btn7.config(font=('verdana', 14))

# Add similar code for other buttons here

root.mainloop()

