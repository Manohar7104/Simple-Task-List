import java.util.ArrayList;
import java.util.Scanner;
public class TaskList {
    private ArrayList<String> tasks;
    public TaskList() {
        tasks = new ArrayList<>();
    }
    public void addTask(String task) {
        tasks.add(task);
        System.out.println("Task added successfully.");
    }
    public void removeTask(int index) {
        if (index >= 0 && index < tasks.size()) {
            tasks.remove(index);
            System.out.println("Task removed successfully.");
        } else {
            System.out.println("Invalid task index.");
        }
    }
    public void listTasks() {
        if (tasks.isEmpty()) {
            System.out.println("Task list is empty.");
        } else {
            System.out.println("Task List:");
            for (int i = 0; i < tasks.size(); i++) {
                System.out.println((i + 1) + ". " + tasks.get(i));
            }
        }
    }
    public static void main(String[] args) {
        TaskList taskList = new TaskList();
        Scanner scanner = new Scanner(System.in);
        while (true) {
            System.out.println("\nChoose an option:");
            System.out.println("1. Add Task");
            System.out.println("2. Remove Task");
            System.out.println("3. List Tasks");
            System.out.println("4. Exit");
            System.out.print("Enter your choice: ");
            int choice = scanner.nextInt();
            scanner.nextLine(); // consume newline
            switch (choice) {
                case 1:
                    System.out.print("Enter task to add: ");
                    String taskToAdd = scanner.nextLine();
                    taskList.addTask(taskToAdd);
                    break;
                case 2:
                    System.out.print("Enter task index to remove: ");
                    int indexToRemove = scanner.nextInt();
                    taskList.removeTask(indexToRemove - 1); // Adjusting index for user input
                    break;
                case 3:
                    taskList.listTasks();
                    break;
                case 4:
                    System.out.println("Exiting program.");
                    System.exit(0);
                default:
                    System.out.println("Invalid choice. Please choose again.");
            }
        }
    }
}
