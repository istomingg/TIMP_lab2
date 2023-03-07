**Лабораторная работа 2**

**PART I**

1. Создайте пустой репозиторий на сервисе github.com (или gitlab.com, или bitbucket.com).

**Создал пустой репозиторий с названием TIMP_lab2**

2. Выполните инструкцию по созданию первого коммита на странице репозитория, созданного на предыдещем шаге.

**git init**

**echo "test" >> README.md**

**git add README.md**

**git commit -m "test"**

**git branch -M main**

**git remote add origin https://github.com/istomingg/TIMP_lab2.git**

**git push -u origin main**

3. Создайте файл hello_world.cpp в локальной копии репозитория (который должен был появиться на шаге 2). Реализуйте программу Hello world на языке C++ используя плохой стиль кода. Например, после заголовочных файлов вставьте строку using namespace std;.

**Создадим файл > hello_world.cpp и с помощью редактора nano (nano hello_world.cpp) реализуем код**

<img width="356" alt="image" src="https://user-images.githubusercontent.com/126329578/223393578-afe870bd-5d37-4856-9994-7893de777649.png">

4. Добавьте этот файл в локальную копию репозитория.

**git add hello_world.cpp**


5. Закоммитьте изменения с осмысленным сообщением.

**git commit -m "bad style of code"

6. Изменитьте исходный код так, чтобы программа через стандартный поток ввода запрашивалось имя пользователя. А в стандартный поток вывода печаталось сообщение Hello world from @name, где @name имя пользователя.

**Откроем код через редактор nano (nano hello_world.cpp) и внесем изменения**

<img width="471" alt="image" src="https://user-images.githubusercontent.com/126329578/223393929-20987485-c3d7-4ba7-8c6a-4093844f50af.png">

7. Закоммитьте новую версию программы. Почему не надо добавлять файл повторно git add?

**git commit -m "code style with string", без git add программа не даст этого сделать**

8. Запуште изменения в удалёный репозиторий.

**git push -f origin main**

9. Проверьте, что история коммитов доступна в удалёный репозитории.

**git log**

<img width="488" alt="image" src="https://user-images.githubusercontent.com/126329578/223394337-85e6dcd6-e82d-4e98-aaa0-d573aabe8d19.png">

**PART II**

1. В локальной копии репозитория создайте локальную ветку patch1:

**git branch patch1**

2. Внесите изменения в ветке patch1 по исправлению кода и избавления от using namespace std;:

**Перейдем в ветку patch1 (git checkout patch1) и с помощью редактора nano (nano hello_world.cpp) поменяем код**

<img width="533" alt="image" src="https://user-images.githubusercontent.com/126329578/223479711-e739418f-0adc-4dbe-99c2-cde51ee82940.png">

3. commit, push локальную ветку в удалённый репозиторий:

**git add. | git commit -m "code without namespace" | git push origin patch1**

4. Проверьте, что ветка patch1 доступна в удалёный репозитории:

<img width="196" alt="image" src="https://user-images.githubusercontent.com/126329578/223482599-ba6b6d4b-1bd3-450e-ab7d-ebe3fde610fe.png">

5. Создайте pull-request patch1 -> master:

**Сделал PR**

<img width="429" alt="image" src="https://user-images.githubusercontent.com/126329578/223485341-c670b247-c99a-459f-9e61-0ac7e46be30a.png">

6. В локальной копии в ветке patch1 добавьте в исходный код комментарии:

**Откроем файл через редактор nano и добавим коментарии**

<img width="553" alt="image" src="https://user-images.githubusercontent.com/126329578/223485999-b74b0534-cde8-4cf4-a4e6-9519bdb8fd05.png">

7. commit, push:

**git add . | git commit -m "code with //" | git push origin patch1

8. Проверьте, что новые изменения есть в созданном на шаге 5 pull-request:

<img width="317" alt="image" src="https://user-images.githubusercontent.com/126329578/223487270-bae02ff9-6756-4726-a1b6-23e65a3be4ab.png">

9. В удалённый репозитории выполните слияние PR patch1 -> master и удалите ветку patch1 в удаленном репозитории:

**git merge patch1**

<img width="692" alt="image" src="https://user-images.githubusercontent.com/126329578/223491714-02230686-3032-42e6-906a-eeb30d15b13c.png">

**Удалил ветку patch1**

10. Локально выполните pull:

**git push origin main**

11. С помощью команды git log просмотрите историю в локальной версии ветки master:

<img width="820" alt="image" src="https://user-images.githubusercontent.com/126329578/223492394-aae7128c-c0b9-4b79-ae86-1925eb152544.png">

12. Удалите локальную ветку patch1:

**git branch -d patch1**

**PART III**

1. Создайте новую локальную ветку patch2:

**git branch patch2**
2. Измените code style с помощью утилиты clang-format. Например, используя опцию -style=Mozilla:

**sudo apt install clang-format**

**clang-format -style="Mozilla" hello_world.cpp**

<img width="454" alt="image" src="https://user-images.githubusercontent.com/126329578/223496464-6d3672e8-fa26-4720-a8a2-2a2b3e2fdbd0.png">

3. commit, push, создайте pull-request patch2 -> master:

**git add hello_world.cpp | git commit -m "Mozilla style" | git push origin patch2 | Создал PR**

4. В ветке master в удаленном репозитории измените комментарии, например, расставьте знаки препинания, переведите комментарии на другой язык:

**Изменил комментарии**

5. Убедитесь, что в pull-request появились конфликтны:

<img width="638" alt="image" src="https://user-images.githubusercontent.com/126329578/223499130-4a4e94ec-aa0b-45f1-83be-22325bd69ea7.png">

6. Для этого локально выполните pull + rebase (точную последовательность команд, следует узнать самостоятельно). Исправьте конфликты.

**git pull --rebase origin main**

**Откроем файл cat hello_world.cpp и увидим конфликты**

7. Сделайте force push в ветку patch2:

**git push origin patch2 -f**

8. Убедитель, что в pull-request пропали конфликтны:

<img width="651" alt="image" src="https://user-images.githubusercontent.com/126329578/223507734-c3a42753-9042-4ad3-abf6-cf9ae6d4fbc2.png">

9. Вмержите pull-request patch2 -> maste:

**Вмержил patch2**
