# Software-Development-Portfolio-Projects
Here are some strong Software Development Portfolio Project ideas that look good on a GitHub profile and can help during internship applications
TaskFlowPro/
│
├── main.py
├── tasks.json
├── README.md

import json
import os
from datetime import datetime

FILE_NAME = "tasks.json"

def load_tasks():
    if os.path.exists(FILE_NAME):
        with open(FILE_NAME, "r") as file:
            return json.load(file)
    return []

def save_tasks(tasks):
    with open(FILE_NAME, "w") as file:
        json.dump(tasks, file, indent=4)

def add_task():
    tasks = load_tasks()

    title = input("Enter Task Title: ")
    description = input("Enter Description: ")
    priority = input("Priority (High/Medium/Low): ")
    deadline = input("Deadline (YYYY-MM-DD): ")

    task = {
        "id": len(tasks) + 1,
        "title": title,
        "description": description,
        "priority": priority,
        "deadline": deadline,
        "status": "Pending"
    }

    tasks.append(task)
    save_tasks(tasks)

    print("Task Added Successfully!")

def view_tasks():
    tasks = load_tasks()

    if not tasks:
        print("No tasks found.")
        return

    print("\n===== TASK LIST =====")

    for task in tasks:
        print(f"""
ID: {task['id']}
Title: {task['title']}
Description: {task['description']}
Priority: {task['priority']}
Deadline: {task['deadline']}
Status: {task['status']}
-------------------------
""")

def update_status():
    tasks = load_tasks()

    task_id = int(input("Enter Task ID: "))

    for task in tasks:
        if task["id"] == task_id:
            task["status"] = "Completed"
            save_tasks(tasks)
            print("Task Marked as Completed!")
            return

    print("Task Not Found!")

def delete_task():
    tasks = load_tasks()

    task_id = int(input("Enter Task ID to Delete: "))

    updated_tasks = [task for task in tasks if task["id"] != task_id]

    save_tasks(updated_tasks)

    print("Task Deleted Successfully!")

def task_statistics():
    tasks = load_tasks()

    total = len(tasks)
    completed = sum(1 for task in tasks if task["status"] == "Completed")
    pending = total - completed

    print("\n===== STATISTICS =====")
    print(f"Total Tasks: {total}")
    print(f"Completed Tasks: {completed}")
    print(f"Pending Tasks: {pending}")

def main():
    while True:
        print("""
===== TASKFLOW PRO =====

1. Add Task
2. View Tasks
3. Complete Task
4. Delete Task
5. Statistics
6. Exit
""")

        choice = input("Enter Choice: ")

        if choice == "1":
            add_task()
        elif choice == "2":
            view_tasks()
        elif choice == "3":
            update_status()
        elif choice == "4":
            delete_task()
        elif choice == "5":
            task_statistics()
        elif choice == "6":
            print("Goodbye!")
            break
        else:
            print("Invalid Choice!")

if __name__ == "__main__":
    main()
