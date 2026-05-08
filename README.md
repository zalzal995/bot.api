# bot.api
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class GitReflogExecutor {
    public static void main(String[] args) {
        executeGitReflog();
    }

    public static void executeGitReflog() {
        try {
            ProcessBuilder processBuilder = new ProcessBuilder("git", "reflog");
            processBuilder.directory(new java.io.File("путь/к/твоему/git/репозиторию")); // Укажи путь к репозиторию
            processBuilder.redirectErrorStream(true);

            Process process = processBuilder.start();
            BufferedReader reader = new BufferedReader(new InputStreamReader(process.getInputStream()));

            String line;
            System.out.println("Вывод git reflog:");
            while ((line = reader.readLine()) != null) {
                System.out.println(line);
            }

            int exitCode = process.waitFor();
            System.out.println("Код завершения: " + exitCode);

        } catch (IOException | InterruptedException e) {
            e.printStackTrace();
        }
    }
}
