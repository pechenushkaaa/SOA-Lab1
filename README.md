# SOA-Lab1

Разработать веб-сервис на базе сервлета, реализующий управление коллекцией объектов, и клиентское веб-приложение, предоставляющее интерфейс к разработанному веб-сервису. В коллекции необходимо хранить объекты класса `StudyGroup`, описание которого приведено ниже:

```java
public class StudyGroup {
    private long id; //Значение поля должно быть больше 0, Значение этого поля должно быть уникальным, Значение этого поля должно генерироваться автоматически
    private String name; //Поле не может быть null, Строка не может быть пустой
    private Coordinates coordinates; //Поле не может быть null
    private java.time.LocalDate creationDate; //Поле не может быть null, Значение это-го поля должно генерироваться автоматически
    private Long studentsCount; //Значение поля должно быть больше 0, Поле не может быть null
    private long expelledStudents; //Значение поля должно быть больше 0
    private Integer shouldBeExpelled; //Значение поля должно быть больше 0, Поле не может быть null
    private FormOfEducation formOfEducation; //Поле не может быть null
    private Person groupAdmin; //Поле может быть null
}
public class Coordinates {
    private Float x; //Значение поля должно быть больше -406, Поле не может быть null
    private Float y; //Значение поля должно быть больше -345, Поле не может быть null
}
public class Person {
    private String name; //Поле не может быть null, Строка не может быть пустой
    private int weight; //Значение поля должно быть больше 0
    private Color hairColor; //Поле может быть null
    private Country nationality; //Поле не может быть null
    private Location location; //Поле может быть null
}
public class Location {
    private long x;
    private Float y; //Поле не может быть null
    private Integer z; //Поле не может быть null
}
public enum FormOfEducation {
    DISTANCE_EDUCATION,
    FULL_TIME_EDUCATION,
    EVENING_CLASSES;
}
public enum Color {
    GREEN,
    RED,
    YELLOW;
}
public enum Country {
    RUSSIA,
    FRANCE,
    SOUTH_KOREA;
}
```


Веб-сервис должен удовлетворять следующим требованиям:
- API, реализуемый сервисом, должен соответствовать рекомендациям подхода RESTful.
-	Необходимо реализовать следующий базовый набор операций с объектами коллекции: добавление нового элемента, получение элемента по ИД, обновление элемента, удаление элемента, получение массива элементов.
-	Операция, выполняемая над объектом коллекции, должна определяться методом HTTP-запроса.
-	Операция получения массива элементов должна поддерживать возможность сортировки и фильтрации по любой комбинации полей класса, а также возможность постраничного вывода результатов выборки с указанием размера и порядкового номера выводимой страницы.
-	Все параметры, необходимые для выполнения операции, должны передаваться в URL запроса.
-	Данные коллекции, которыми управляет веб-сервис, должны храниться в реляционной базе данных.
-	Информация об объектах коллекции должна передаваться в формате xml.
-	В случае передачи сервису данных, нарушающих заданные на уровне класса ограничения целостности, сервис должен возвращать код ответа http, соответствующий произошедшей ошибке.
-	Веб-сервис должен быть "упакован" в веб-приложение, которое необходимо развернуть на сервере приложений Tomcat.


Помимо базового набора, веб-сервис должен поддерживать следующие операции над объектами коллекции:
-	Удалить все объекты, значение поля studentsCount которого эквивалентно заданному.
-	Вернуть количество объектов, значение поля groupAdmin которых равно заданному.
-	Вернуть массив объектов, значение поля groupAdmin которых больше заданного.


Эти операции должны размещаться на отдельных URL.


Требования к клиентскому приложению:
-	Клиентское приложение может быть написано на любом веб-фреймворке, который можно запустить на сервере helios.
-	Клиентское приложение должно обеспечить полный набор возможностей по управлению объектами коллекции, предоставляемых веб-сервисом -- включая сортировку, фильтрацию и постраничный вывод.
-	Клиентское приложение должно преобразовывать передаваемые сервисом данные в человеко-читаемый вид -- параграф текста, таблицу и т.д.
-	Клиентское приложение должно информировать пользователя об ошибках, возникающих на стороне сервиса, в частности, о том, что сервису были отправлены невалиданые данные.