todo_list = []

def show_menu():
    print("\n--- TO-DO LIST MENU ---")
    print("1. Add Task")
    print("2. View Tasks")
    print("3. Mark Task as Done")
    print("4. Delete Task")
    print("5. Exit")

def add_task():
    task = input("Enter a new task: ")
    todo_list.append({"task": task, "done": False})
    print("✅ Task added!")

def view_tasks():
    if not todo_list:
        print("📭 No tasks found.")
        return
    print("\n--- Your Tasks ---")
    for i, task in enumerate(todo_list):
        status = "✔" if task["done"] else "✘"
        print(f"{i+1}. [{status}] {task['task']}")

def mark_done():
    view_tasks()
    try:
        num = int(input("Enter task number to mark as done: "))
        todo_list[num - 1]["done"] = True
        print("✅ Task marked as done!")
    except:
        print("❌ Invalid task number.")

def delete_task():
    view_tasks()
    try:
        num = int(input("Enter task number to delete: "))
        removed = todo_list.pop(num - 1)
        print(f"🗑️ Deleted: {removed['task']}")
    except:
        print("❌ Invalid task number.")

while True:
    show_menu()
    choice = input("Choose an option (1-5): ")
    
    if choice == "1":
        add_task()
    elif choice == "2":
        view_tasks()
    elif choice == "3":
        mark_done()
    elif choice == "4":
        delete_task()
    elif choice == "5":
        print("👋 Goodbye!")
        break
    else:
        print("❌ Invalid choice. Try again.")
