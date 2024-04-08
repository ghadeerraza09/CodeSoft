
class Task:
    def __init__(self, description, completed=False):
        self.description = description
        self.completed = completed

class TodoList:
    def __init__(self):
        self.tasks = []

    def add_task(self, task):
        self.tasks.append(task)

    def mark_completed(self, task_index):
        if 0 <= task_index < len(self.tasks):
            self.tasks[task_index].completed = True

    def display_tasks(self):
        for i, task in enumerate(self.tasks):
            status = '[x]' if task.completed else '[ ]'
            print(f"{i+1}. {status} {task.description}")

def main():
    todo_list = TodoList()
    while True:
        print("\nTo-Do List:")
        todo_list.display_tasks()
        print("\nCommands:")
        print("a - Add a task")
        print("c - Mark a task as completed")
        print("q - Quit")

        command = input("Enter a command: ").lower()
        if command == "a":
            description = input("Enter a task description: ")
            todo_list.add_task(Task(description))
        elif command == "c":
            index = int(input("Enter the task number to mark as completed: "))
            todo_list.mark_completed(index - 1)
        elif command == "q":
            break
        else:
            print("Invalid command. Please try again.")

if __name__ == "__main__":
    main()
```