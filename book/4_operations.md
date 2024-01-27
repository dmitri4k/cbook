Операции

Над объектами в языке Си могут выполняться различные операции:

операции присваивания;
операции отношения;
арифметические;
логические;
сдвиговые операции.
Результатом выполнения операции является число.

Операции могут быть бинарными или унарными. Бинарные операции выполняются над двумя объектами, унарные — над одним.

Операция присваивания
Операция присваивания обозначается символом = и выполняется в 2 этапа:

вычисляется выражение в правой части;
результат присваивается операнду, стоящему в левой части:
объект = выражение;

Пример:


int a = 4; // переменной a присваивается значение 4
int b;
b = a + 2;   // переменной b присваивается значение 6, вычисленное в правой части
В случае если объекты в левой и правой части операции присваивания имеют разные типы используется операция явного приведения типа.

объект = (тип)выражение;

Пример:


float a = 241.5;
// Перед вычислением остатка от деления a приводится к целому типу
int b = (int)a % 2;  // b = 1
Операции отношения
Основные операции отношения:

== эквивалентно — проверка на равенство;
!= не равно — проверка на неравенство;
< меньше;
> больше;
<=меньше или равно;
>= больше или равно.
Операции отношения используются при организации условий и ветвлений. Результатом этих операций является 1 бит, значение которого равно 1, если результат выполнения операции — истина, и равно 0, если результат выполнения операции — ложь.

Арифметические операции
Основные бинарные операции, расположенные в порядке уменьшения приоритета:

* — умножение;
/ — деление;
+ — сложение;
— — вычитание;
% — остаток от целочисленного деления.
Основные унарные операции:

++ — инкрементирование (увеличение на 1);
–– — декрементирование (уменьшение на 1);
— — изменение знака.
Результат вычисления выражения, содержащего операции инкрементирования или декрементирования, зависит от того, где расположен знак операции (до объекта или после него). Если операция расположена до объекта, то сначала происходит изменение значения переменной на 1, а потом это значение используется для выполнения следующих операций. Если операция ++ или — расположена после переменной, то сначала выполняется операция, а потом значение переменной изменяется на 1.

Пример:



int a = 2;
int b = 3;
int c;
c = a * ++b;
// c=8, поскольку в операции умножения уже b=4


int a = 2;
int b = 3;
int d;
d = a * b++;
// d=6, поскольку в операции умножения b=3, следующим действием будет b=4
Бинарные арифметические операции могут быть объединены с операцией присваивания:

объект *= выражение; // объект = объект * выражение
объект /= выражение; // объект = объект / выражение
объект += выражение; // объект = объект + выражение
объект -= выражение; // объект = объект — выражение
объект %= выражение; // объект = объект % выражение
Логические операции
Логические операции делятся на две группы:

условные;
побитовые.
Условные логические операции чаще всего используются в операциях проверки условия if и могут выполняться над любыми объектами. Результат условной логической операции:

1 если выражение истинно;
0 если выражение ложно.
Вообще, все значения, отличные от нуля, интерпретируются условными логическими операциями как истинные.

Основные условные логические операции:

&& — И (бинарная) — требуется одновременное выполнение всех операций отношения;
|| — ИЛИ (бинарная) — требуется выполнение хотя бы одной операции отношения;
! — НЕ (унарная) — требуется невыполнение операции отношения.
Побитовые логические операции оперируют с битами, каждый из которых может принимать только два значения: 0 или 1.

Основные побитовые логические операции в языке Си:

& конъюнкция (логическое И) — бинарная операция, результат которой равен 1 только когда оба операнда единичны (в общем случае — когда все операнды единичны);
| дизъюнкция (логическое ИЛИ) — бинарная операция, результат которой равен 1 когда хотя бы один из операндов равен 1;
~ инверсия (логическое НЕ) — унарная операция, результат которой равен 0 если операнд единичный, и равен 1, если операнд нулевой;
^ исключающее ИЛИ — бинарная операция, результат которой равен 1, если только один из двух операндов равен 1 (в общем случае если во входном наборе операндов нечетное число единиц).
Для каждого бита результат выполнения операции будет получен в соответствии с таблицей.

a	b	a & b	a | b	~a	a ^ b
0	0	0	0	1	0
0	1	0	1	1	1
1	0	0	1	0	1
1	1	1	1	0	0
Пример:


unsigned char a = 14;    // a = 0000 1110
unsigned char b = 9;     // b = 0000 1001
unsigned char c, d, e, f;
c = a & b;               // c = 8 = 0000 1000
d = a | b;               // d = 15 = 0000 1111
e = ~a;                  // e = 241 = 1111 0001
f = a ^ b;               // f = 7 = 0000 0111
Побитовые операции позволяют осуществлять установку и сброс отдельных битов числа. С этой целью используется маскирование битов. Маски, соответствующие установке каждого бита в байте, представлены в таблице

Бит	Маска
0	0x01
1	0x02
2	0x04
3	0x08
4	0x10
5	0x20
6	0x40
7	0x80

Для установки определенного бита необходимо соответствующий бит маски установить в 1 и произвести операцию побитового логического ИЛИ с константой, представляющей собой маску:
1
2unsigned char a = 3;
a = a | 0x04;  // a = 7, бит 2 установлен
Для сброса определенного бита необходимо соответствующий бит маски сбросить в 0 и произвести операцию побитового логического И с константой, представляющей собой инверсную маску:
1
2unsigned char a = 3;
a = a & (~0x02);  // a = 1, бит 1 сброшен
Бинарные побитовые логические операции могут быть объединены с операцией присваивания:

объект &= выражение; // объект = объект & выражение
объект |= выражение; // объект = объект | выражение
объект ^= выражение; // объект = объект ^ выражение
Сдвиговые операции
Операции арифметического сдвига применяются в целочисленной арифметике и обозначаются как:

>> — сдвиг вправо;
<< — сдвиг влево.
Общий синтаксис осуществления операции сдвига:

объект = выражение сдвиг КоличествоРазрядов;

Пример:


unsigned char a=6;  // a = 0000 0110
unsigned char b;
b = a >> 1; // b = 0000 0110 >> 1 = 0000 0011 = 3
Арифметический сдвиг целого числа вправо >> на 1 разряд соответствует делению числа на 2.

Арифметический сдвиг целого числа влево << на 1 разряд соответствует умножению числа на 2.