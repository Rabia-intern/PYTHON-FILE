# PYTHON-FILE
import tkinter as tk
from tkinter import messagebox

tasks = []

#Add task function
def add_task():
    task = task_entry.get()
    if task:
        tasks.append(task)
        update_task_list()
        task_entry.delete(0,tk.END)
    else:
        messagebox.showwarning("Input Error", "Please enter a task")

#Update the task display
def update_task_list():
    task_listbox.delete(0,tk.END)
    for task in tasks:
        task_listbox.insert(tk.END, task)

#Delete a selected task
def delete_task():
    selected_task = task_listbox.curselection()
    if selected_task:
        tasks.pop(selected_task[0])
        update_task_list()
    else:
        messagebox.showwarning("Selection Error", "Please select a task to delete:")

#main application window
root = tk.Tk()
root.title("To-Do List")

#Task input field
task_entry = tk.Entry(root, width=40)
task_entry.pack(pady=10)

#Add task button
add_button = tk.Button(root, text="Add task", width=40, command=add_task)
add_button.pack(pady=10)

#listbox to display tasks
task_listbox = tk.Listbox(root, height=10, width=40)
task_listbox.pack(pady=10)

#Delete task button 
delete_button = tk.Button(root, text="Delete Task", width=40, command=delete_task)
delete_button.pack(pady=10)

#run the application
root.mainloop()
