import java.util.Scanner;
interface Plugin {
    void execute();
}


class TextPlugin implements Plugin {
    @Override
    public void execute() {
        System.out.println("TextPlugin executed.");
        // Add your text plugin logic here
    }
}


class ImagePlugin implements Plugin {
    @Override
    public void execute() {
        System.out.println("ImagePlugin executed.");
        // Add your image plugin logic here
    }
}


class AudioPlugin implements Plugin {
    @Override
    public void execute() {
        System.out.println("AudioPlugin executed.");
        // Add your audio plugin logic here
    }
}

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("Select a plugin to execute:");
            System.out.println("1. TextPlugin");
            System.out.println("2. ImagePlugin");
            System.out.println("3. AudioPlugin");
            System.out.println("4. Exit");
            System.out.print("Enter your choice: ");

            int choice = scanner.nextInt();
            Plugin selectedPlugin = null;

            switch (choice) {
                case 1:
                    selectedPlugin = new TextPlugin();
                    break;
                case 2:
                    selectedPlugin = new ImagePlugin();
                    break;
                case 3:
                    selectedPlugin = new AudioPlugin();
                    break;
                case 4:
                    System.out.println("Exiting...");
                    scanner.close();
                    return;
                default:
                    System.out.println("Invalid choice.");
            }

            if (selectedPlugin != null) {
                try {
                    selectedPlugin.execute();
                } catch (Exception e) {
                    System.out.println("Error executing plugin: " + e.getMessage());
                }
            }
        }
    }
}
