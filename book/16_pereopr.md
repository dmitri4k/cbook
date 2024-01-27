Переопределение типов

Оператор переопределения типов typedef вводит синоним для существующего типа, например

 typedef unsigned char BYTE;
BYTE b;  // b – типа unsigned char
Использование typedef для переопределения типов аналогично директиве #define, но

#define является директивой препроцессора и обрабатывается перед компиляцией путем простой замены всех вхождений:
 
 
 
 #define P_INT int*
typedef int* p_integer;
P_INT p1, p2; // int* p1, int p2;
p_integer p3, p4; // int* p3, int* p4;
с помощью #define нельзя объявить имя функции или массива, но можно используя typedef
 
 typedef unsigned char name[30];
name my;  // my – строка из 30 символов
typedef широко применяются в Windows API для описания типов функций, применяемых в программировании оконных приложений Windows.


```
#include <stdio.h>
#include <stdlib.h>
typedef struct Books
{
  char  title[50], author[50], subject[100];
  int   book_id;
} Book;
int main() 
{
  Book book;
  strcpy_s(book.title, "C Programming");
  strcpy_s(book.author, "Nuha Ali");
  strcpy_s(book.subject, "C Programming Tutorial");
  book.book_id = 6495407;
  printf("book title : %s\n", book.title);
  printf("book author : %s\n", book.author);
  printf("book subject : %s\n", book.subject);
  printf("book book_id : %d\n", book.book_id);
  getchar(); getchar();
  return 0;
}
```
Результат выполнения: