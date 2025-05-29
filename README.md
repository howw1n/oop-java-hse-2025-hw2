
# 🔧 Домашнее задание 2: Расширение UniversitySystem

### 1. Очередь ожидания для полного курса (10 баллов)

* **В классе `Course`**:

    * Добавить поле

      ```java
      private Queue<Student> waitingList;
      ```

      реализованное через `new LinkedList<>()`.
    * В конструктор передавать также максимальную вместимость `int maxStudents`.
* **Поведение**:

    * Если при вызове `addStudent(...)` курс уже заполнен, помещать студента в `waitingList`.
    * Реализовать методы

      ```java
      public void processWaitingList();
      public int getWaitingListSize();
      ```

      — чтобы переводить студентов из очереди в основной список, когда появляются свободные места.

### 2. Лента объявлений через LinkedList (10 баллов)

* **Создать интерфейс `Publishable`**:

  ```java
  public interface Publishable {
      void publish(String message);
      List<String> getFeed();
  }
  ```
* **Реализовать в `Course`**:

    * Внутри хранить объявления в

      ```java
      private LinkedList<String> feed;
      ```
    * `publish(...)` добавляет сообщение в конец списка, `getFeed()` возвращает все записи.

### 3. Глобальный справочник студентов через HashMap (10 баллов)

* **В классе `University`** добавить:

  ```java
  private HashMap<Integer, Student> studentDirectory;
  ```
* **Новые методы**:

    * `public void registerStudent(Student s)` — регистрирует студента в `studentDirectory` (и опционально в каком-либо курсе).
    * `public Student findStudentById(int id)` — ищет студента по ключу; если не найден, бросает `StudentNotFoundException`.
* **Создать класс исключения** `StudentNotFoundException` (extends `Exception`).

### 4. Группировка курсов по кафедрам (10 баллов)

* **В `University`** хранить:

  ```java
  private HashMap<String, LinkedList<Course>> coursesByDept;
  ```
* **Новые методы**:

    * `public void addCourseToDept(String deptName, Course c)`
    * `public List<Course> getCoursesForDept(String deptName)`
* Это заставит использовать и `HashMap`, и `LinkedList`.

### 5. Новый класс: `GraduateStudent` (5 баллов)

* **Класс `GraduateStudent`** наследует `Student` (без abstract).
* **Добавляет** поле и метод:

  ```java
  private String thesisTitle;
  public String getThesisTitle();
  ```
* **Переопределить** `getDetails()` так, чтобы выводило также тему диссертации.

### 6. Интерфейс планировщика событий (15 баллов)

* **Определить интерфейс `Schedulable`**:

  ```java
  public interface Schedulable {
      void scheduleEvent(String description, String dateTime);
      List<Event> getSchedule();
  }
  ```
* **Создать класс `Event`** (POJO с полями `description` и `dateTime`).
* **Реализовать `Schedulable` в**:

    * **`Course`** (каждый курс хранит свой `LinkedList<Event>` для расписания).
    * **`Professor`** (каждый преподаватель хранит личное расписание аналогично).

### 7. Пользовательское исключение `CourseFullException` (5 баллов)

* **Когда** студент пытается записаться на курс, где и основной список, и очередь ожидания полны, бросать `CourseFullException`.
* **Конструктор** принимает сообщение вида

  ```
  "Course [название] is completely full"  
  ```

### 8. Класс управления кафедрой (10 баллов)

* **Создать класс `Department`**, реализующий интерфейс:

  ```java
  public interface Departmental {
      void addCourse(Course c);
      void removeCourse(Course c);
      List<Course> listCourses();
  }
  ```
* **Поля `Department`**:

    * `String name`
    * `Professor head`
    * `LinkedList<Course> courses`
* **Методы** управляют списком кафедры.

---

### 📊 Итого: 75 баллов

1. Очередь ожидания (10)
2. Лента объявлений (10)
3. Справочник студентов (10)
4. Группировка по кафедрам (10)
5. GraduateStudent (5)
6. Планировщик событий (15)
7. CourseFullException (5)
8. Department (10)

---

**Критерии оценки:**

* Правильное использование **интерфейсов** и **наследования**.
* Обязательное применение **LinkedList**, **Queue** и **HashMap**.
* Корректная работа с исключениями.
* Целостная интеграция в существующий проект.
* Чистый, задокументированный код.

Удачи!
