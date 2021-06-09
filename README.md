## Homework

Вы продолжаете проходить стажировку в "Formatter Inc." (см [подробности](https://github.com/tp-labs/lab03#Homework)).

В прошлый раз ваше задание заключалось в настройке автоматизированной системы **CMake**.

Сейчас вам требуется настроить систему непрерывной интеграции для библиотек и приложений, с которыми вы работали в [прошлый раз](https://github.com/tp-labs/lab03#Homework). Настройте сборочные процедуры на различных платформах:
* используйте [TravisCI](https://travis-ci.com/) для сборки на операционной системе **Linux** с использованием компиляторов **gcc** и **clang**;
* используйте [AppVeyor](https://www.appveyor.com/) для сборки на операционной системе **Windows**.

```sh
#Классика жанра
$ export GITHUB_USERNAME=Lam0Rka
$ pushd .
~/Lam0Rka/workspace ~/Lam0Rka/workspace
#Клонируем
$ source scripts/activate
$ git clone https://github.com/Lam0Rla/lab033 projects/lab444_home
Клонирование в «projects/lab444_home»…
remote: Enumerating objects: 343, done.
remote: Counting objects: 100% (343/343), done.
remote: Compressing objects: 100% (163/163), done.
remote: Total 343 (delta 195), reused 313 (delta 165), pack-reused 0
Получение объектов: 100% (343/343), 1.10 MiB | 1.50 MiB/s, готово.
Определение изменений: 100% (195/195), готово.
$ cd projects/lab444_home
$ git remote remove origin
$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab444_home
#Создаём трэвис ямл
$ cat > .travis.yml <<EOF
> language: cpp
> 
> script:
> - cd solver_application
> - cmake .
> - make
> - cd ..
> - cd hello_world_application
> - cmake .
> - make
> 
> addons:
>   apt:
>     sources:
>       - george-edison55-precise-backports
>     packages:
>       - cmake
>       - cmake-data
>       - mingw-w64
> EOF
$ travis lint
Hooray, .travis.yml looks valid :)
#Пушим и добавляем всё
$ git add .
$ git commit -m"Hooray"
[master cb64b69] Hooray
 1 file changed, 19 insertions(+)
 create mode 100644 .travis.yml
git push origin main
```
