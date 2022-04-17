    public class JvmComprehension {

        public static void main(String[] args) {
            int i = 1;                      // 1
            Object o = new Object();        // 2
            Integer ii = 2;                 // 3
            printAll(o, i, ii);             // 4
            System.out.println("finished"); // 7
        }

        private static void printAll(Object o, int i, Integer ii) {
            Integer uselessVar = 700;                   // 5
            System.out.println(o.toString() + i + ii);  // 6
        }
    }
    
# JVM

    public class JvmComprehension {
Загрузчик классов Application ClassLoader помещает информацию о классе JvmComprehension в Metaspace.

    public static void main(String[] args) {
Создаётся фрейм для метода main в стеке.

    int i = 1;                      // 1
Иницилизируемой пременной примитивного типа данных i присваивается значение, и она помещается в стек память во фрейм main.

    Object o = new Object();        // 2
Создаётся новый объект в куче. В стеке во фрейме main создаётся переменная o, которая содержит ссылку на этот объект.

    Integer ii = 2;                 // 3
В куче создаётся объект типа Integer, со значением 2. В стеке во фрейме main создаётся переменная ii, которая содержит ссылку на этот объект.

    printAll(o, i, ii);             // 4
    private static void printAll(Object o, int i, Integer ii) {
В стеке создаётся новый фрейм для метода printAll.
В нём будут созданы переменные o, i, ii. Значение i будет записано в стеке printAll, а ссылки на o и ii будут вести на существующие объекты в куче.

    Integer uselessVar = 700;                   // 5
В куче создаётся объект типа Integer, со значением 700. В стеке во фрейме main создаётся переменная uselessVar, которая содержит ссылку на этот объект.

    System.out.println(o.toString() + i + ii);  // 6
В стеке создастся новый фрейм для метода toString.
В куче создаётся объект String, куда кладётся строка результата метода toString над объектом o.
Фрейм toString удалится.
В куче создаётся ещё одна строка, получившаяся после слияния трёх строк. В стеке создастся новый фрейм для вывода на экран, куда передастся ссылка на эту строку.

    }
Фреймы println и printAll удалятся.

    System.out.println("finished"); // 7
В куче создастся строка, ссылка на которую передастся в новый фрейм println. После печати фрейм удалится.

    }
JVM завершает работу.

### Сборщик мусора
Во время работы программы в куче будет не связанная ни с чем переменная UselessVar и разные строки, ссылки на которые перестали быть нужными после операций над ними. Он их удалит. 

