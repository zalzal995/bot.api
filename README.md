# 1. Создайте папку и инициализируйте репозиторий
mkdir course-management
cd course-management
git init

# 2. Настройте имя и email (ваши настоящие!)
git config user.name "Ваша Фамилия Имя"
git config user.email "ваш@email.com"

# 3. Переименуйте ветку в main
git branch -m master main

# 4. Добавьте .gitignore
touch .gitignore
git add .gitignore
git commit -m "Initial commit: add .gitignore"

# 5. Создайте ветку для первого коммита (таблица 1)
git checkout -b feature/initial-structure

# 6. Разархивируйте приложенный архив в папку проекта

# 7. Добавьте файлы из таблицы 1
git add .mvn/ mvnw mvnw.cmd pom.xml .gitattributes
git add src/main/java/ru/mtuci/coursemanagement/CourseManagementApplication.java
git add src/main/java/ru/mtuci/coursemanagement/config/WebConfig.java
git add src/main/java/ru/mtuci/coursemanagement/controller/*.java
git add src/main/java/ru/mtuci/coursemanagement/service/PluginLoader.java
git add src/main/resources/application.yaml src/main/resources/data.sql
git add src/main/resources/templates/index.html
git commit -m "Add initial project structure and configuration"

# 8. Создайте ветку для второго коммита (таблица 2)
git checkout main
git checkout -b feature/auth-module
# Добавьте файлы AuthController, UserService, User, UserRepository, login.html
git add .
git commit -m "Add authentication module"

# 9. Ветка для третьего коммита (таблица 3)
git checkout main
git checkout -b feature/course-module
# Добавьте файлы CourseController, CourseService, Course, CourseRepository, courses.html
git add .
git commit -m "Add course management module"

# 10. Ветка для четвёртого коммита (таблица 4)
git checkout main
git checkout -b feature/students-module
# Добавьте файлы StudentsController, Student, StudentRepository, students.html
git add .
git commit -m "Add students management module"

# 11. Смерджите всё в main (сначала auth, потом course, потом students)
git checkout main
git merge feature/auth-module
git merge feature/course-module
git merge feature/students-module

# 12. Удалите ненужные файлы (test папку, Dockerfile, README.md)
rm -rf src/main/tests Dockerfile README.md
git commit -am "Remove unnecessary files"

# 13. Удалите ветки
git branch -d feature/auth-module feature/course-module feature/students-module
