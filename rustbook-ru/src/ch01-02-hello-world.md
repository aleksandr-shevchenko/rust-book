## Привет, мир!

Итак, когда Rust уже установлен, можно приступать к написанию вашей первой программы. Общая традиция при изучении нового языка программирования - писать маленькую программу, которая печатает в строке вывода `"Hello, world!"`. Давайте сделаем то же самое.

> Примечание. В этой книге предполагается базовое знакомство с командной строкой. Rust не предъявляет особых требований к вашему редактору кода или инструментам, поэтому, если вы предпочитаете использовать интегрированную среду разработки (IDE) вместо командной строки, не стесняйтесь использовать свою любимую IDE. Многие IDE имеют поддержку Rust; подробности можно найти в документации по IDE. В последнее время команда Rust сосредоточилась на обеспечении отличной поддержки IDE, и в этом направлении был достигнут большой прогресс!

### Создание папки проекта

Прежде всего начнём с создания директории, в которой будем сохранять наш код на языке Rust. На самом деле не важно, где сохранять наш код. Однако, для упражнений и проектов, обсуждаемых в данной книге, мы советуем создать директорию *projects* в вашем домашнем каталоге, там же и хранить в будущем код программ из книги.

Откройте терминал и введите следующие команды для того, чтобы создать директорию <em>projects</em> для хранения кода разных проектов, и, внутри неё, директорию <em>hello_world</em> для проекта “Hello, world!”.

Для Linux, macOS и PowerShell на Windows, введите:

```console
$ mkdir ~/projects
$ cd ~/projects
$ mkdir hello_world
$ cd hello_world
```

Для Windows в CMD, введите:

```cmd
> mkdir "%USERPROFILE%\projects"
> cd /d "%USERPROFILE%\projects"
> mkdir hello_world
> cd hello_world
```

### Написание и запуск первой Rust программы

Затем создайте новый исходный файл и назовите его *main.rs*. Файлы Rust всегда заканчиваются расширением *.rs*. Если вы используете более одного слова в имени файла, принято разделять их символом подчёркивания. Например, используйте *hello_world.rs* вместо *helloworld.rs*.

Теперь откроем файл *main.rs* для редактирования и введём следующие строки кода:

<span class="filename">Название файла: main.rs</span>

```rust
fn main() {
    println!("Hello, world!");
}
```

<span class="caption">Листинг 1-1: Программа которая печатает <code>Hello, world!</code></span>

Сохраните файл и вернитесь в окно терминала в каталог *~/projects/hello_world*. В Linux или macOS введите следующие команды для компиляции и запуска файла:

```console
$ rustc main.rs
$ ./main
Hello, world!
```

В Windows, введите команду `.\main.exe` вместо `./main`:

```powershell
> rustc main.rs
> .\main.exe
Hello, world!
```

Независимо от операционной системы, строка `Hello, world!` должна напечататься в окне вашего терминала. Если вы не увидели вывода, вернитесь в часть "Решение проблем" ["Troubleshooting"] раздела "Установка" для получения помощи.

Если напечаталось `Hello, world!`, то примите наши поздравления! Вы написали программу на Rust, что делает вас Rust программистом — добро пожаловать!

### Анатомия программы на Rust

Давайте рассмотрим «Hello, world!» программу в деталях. Вот первая часть головоломки:

```rust
fn main() {

}
```

Эти строки определяют функцию с именем `main`. Функция `main` особенная: это всегда первый код, который запускается в каждой исполняемой программе Rust. Первая строка объявляет функцию с именем `main`, которая не имеет параметров и ничего не возвращает. Если бы были параметры, они бы заключались в круглые скобки `()`.

Тело функции заключено в `{}`. Rust требует фигурных скобок вокруг всех тел функций. Хороший стиль — поместить открывающую фигурную скобку на ту же строку, что и объявление функции, добавив между ними один пробел.

> Примечание. Если вы хотите придерживаться стандартного стиля в проектах на Rust, вы можете использовать инструмент автоматического форматирования под названием `rustfmt` для форматирования кода в определённом стиле (подробнее о `rustfmt` в [Приложении D]).<!-- игнорировать --> ). Команда Rust включила этот инструмент в стандартный дистрибутив Rust, например, `rustc`, поэтому он уже должен быть установлен на вашем компьютере!

Тело функции `main` содержит следующий код:

```rust
    println!("Hello, world!");
```

Эта строка делает всю работу в этой маленькой программе: печатает текст на экран. Можно заметить четыре важных детали.

Первая, не столь заметная, - в стиле Rust для отступа используются четыре пробела, а не знак табуляции.

Во-вторых, `println!` вызывает макрос Rust. Если бы вместо этого была вызвана функция, она была бы введена как `println` (без `!`). Мы обсудим макросы Rust более подробно в Главе 19. Сейчас вам просто нужно знать, что использование `!` означает, что вы вызываете макрос вместо обычной функции, и что макросы не всегда следуют тем же правилам, что и функции.

В-третьих, вы видите строку `"Hello, world!"`. Мы передаём её в качестве аргумента функции `println!`, и она выводится на экран.

В-четвёртых, мы заканчиваем строку точкой с запятой (`;`), которая указывает на то, что это выражение закончилось и готово начаться следующее. Большинство строк кода на Rust заканчиваются точкой с запятой.

### Компиляция и выполнение кода являются отдельными шагами

Вы только что запустили только что созданную программу, так что давайте рассмотрим каждый шаг в этом процессе.

Перед запуском программы на Rust вы должны скомпилировать её с помощью компилятора Rust, введя команду `rustc` и передав ей имя вашего исходного файла, например:

```console
$ rustc main.rs
```

Если у вас есть опыт работы с C или C++, вы заметите, что это похоже на `gcc` или `clang`. После успешной компиляции Rust выводит двоичный исполняемый файл.

На Linux, macOS и с PowerShell на Windows вы можете увидеть исполняемый файл, введя команду `ls` в своём терминале. В Linux и macOS вы увидите два файла. С PowerShell в Windows вы увидите те же три файла, что и при использовании CMD.

```console
$ ls
main  main.rs
```

В CMD на Windows следует ввести следующие команды:

```cmd
> dir /B %= the /B option says to only show the file names =%
main.exe
main.pdb
main.rs
```

Это показывает исходный код файла с расширением *.rs*, исполняемый файл (*main.exe* на Windows, но *main* на всех других платформах) и, при использовании Windows, файл, содержащий отладочную информацию с расширением *.pdb*. Отсюда вы запускаете файлы *main* или *main.exe*, например:

```console
$ ./main # для Linux
> .\main.exe # для Windows
```

Если ваш *main.rs* — это ваша программа «Hello, world!», эта строка выведет в терминал `Hello, world!`.

Если вы лучше знакомы с динамическими языками, такими как Ruby, Python или JavaScript, возможно, вы не привыкли компилировать и запускать программу как отдельные шаги. Rust — это предварительно *скомпилированный* язык, то есть вы можете скомпилировать программу и передать исполняемый файл кому-то другому, и он сможет запустить его даже без установленного Rust. Если вы даёте кому-то файл *.rb* , *.py* или *.js*, у него должна быть установлена реализация Ruby, Python или JavaScript (соответственно). Но в этих языках вам нужна только одна команда для компиляции и запуска вашей программы. В дизайне языков программирования всё — компромисс.

Компиляция с помощью `rustc` подходит для простых программ, но по мере роста вашего проекта вы захотите управлять всеми параметрами и упростить передачу кода. Далее мы познакомим вас с инструментом Cargo, который поможет вам писать программы из реального мира на Rust.


["Troubleshooting"]: ch01-01-installation.html#troubleshooting
[Приложении D]: appendix-04-useful-development-tools.md