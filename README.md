# Домашнее задание к занятию "`Инструменты Git`" - `Шатый Константин`


### Инструкция по выполнению домашнего задания

   1. Сделайте `fork` данного репозитория к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/git-hw или  https://github.com/имя-вашего-репозитория/7-1-ansible-hw).
   2. Выполните клонирование данного репозитория к себе на ПК с помощью команды `git clone`.
   3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
      - впишите вверху название занятия и вашу фамилию и имя
      - в каждом задании добавьте решение в требуемом виде (текст/код/скриншоты/ссылка)
      - для корректного добавления скриншотов воспользуйтесь [инструкцией "Как вставить скриншот в шаблон с решением](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md)
      - при оформлении используйте возможности языка разметки md (коротко об этом можно посмотреть в [инструкции  по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md))
   4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`);
   5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
   6. Любые вопросы по выполнению заданий спрашивайте в чате учебной группы и/или в разделе “Вопросы по заданию” в личном кабинете.
   
Желаем успехов в выполнении домашнего задания!
   
### Дополнительные материалы, которые могут быть полезны для выполнения задания

1. [Руководство по оформлению Markdown файлов](https://gist.github.com/Jekins/2bf2d0638163f1294637#Code)

---

### Задания

### Найдите полный хеш и комментарий коммита, хеш которого начинается на aefea.

`Запрос:`
git log --oneline | grep '^aefea'

`Ответ:`
aefead2207 Update CHANGELOG.md

### Какому тегу соответствует коммит 85024d3?

`Запрос:`
git describe --tags 85024d3

`Ответ:`
v0.12.23

### Сколько родителей у коммита b8d720? Напишите их хеши.

`Запрос:`
git cat-file -p b8d720

`Ответ:`
tree cec002aab630c8bc701cb85bc94e55e751cd2d8f
parent 56cd7859e05c36c06b56d013b55a252d0bb7e158
parent 9ea88f22fc6269854151c571162c5bcf958bee2b
author Chris Griggs <cgriggs@hashicorp.com> 1579657548 -0800
committer GitHub <noreply@github.com> 1579657548 -0800
gpgsig -----BEGIN PGP SIGNATURE-----

 wsBcBAABCAAQBQJeJ6lMCRBK7hj4Ov3rIwAAdHIIAAWogFD+6nxgm7suNlJVqGv3
 iczwk1OySRvZiDhgJuaIEZMduudoIBnv7XStZsg5wQ7a0byh4iU6z7w6vVKPyj1e
 2KyTqwriHOYqDJ/pljIX92btLU+rXDP0DpnTg8WuMthqUJGh6q8OGorvlIHDwcdN
 DKZxKaLPaBYCD5nuYMyhuh9T6+4ayEN4zUbl5vLPN7XmvhSf4yDQ0H4UaR596qOo
 phaqODHglNLegdGwi+JaTtDSB/JO5zJNfn8OnuRgyhoplmKKlhBAEwS4muxjjkzD
 cUtFA+jkXaVpbfEh/dBRb3yB4W17jrxFDuDESjXKiU61bc8Fwa1JrfQAFlXczmY=
 =s9Hk
 -----END PGP SIGNATURE-----


Merge pull request #23916 from hashicorp/cgriggs01-stable

[Cherrypick] community linksroot@serv1:/home/kshatyy/Terraform/terraform#


### Перечислите хеши и комментарии всех коммитов, которые были сделаны между тегами v0.12.23 и v0.12.24.

`Запрос:`
git log v0.12.23..v0.12.24 --oneline

`Ответ:`
33ff1c03bb (tag: v0.12.24) v0.12.24
b14b74c493 [Website] vmc provider links
3f235065b9 Update CHANGELOG.md
6ae64e247b registry: Fix panic when server is unreachable
5c619ca1ba website: Remove links to the getting started guide's old location
06275647e2 Update CHANGELOG.md
d5f9411f51 command: Fix bug when using terraform login on Windows
4b6d06cc5d Update CHANGELOG.md
dd01a35078 Update CHANGELOG.md
225466bc3e Cleanup after v0.12.23 release

### Найдите коммит, в котором была создана функция func providerSource, её определение в коде выглядит так: func providerSource(...) (вместо троеточия перечислены аргументы).

`Запрос:`
git log -S'func providerSource('

`Ответ:`
commit 8c928e83589d90a031f811fae52a81be7153e82f
Author: Martin Atkins <mart@degeneration.co.uk>
Date:   Thu Apr 2 18:04:39 2020 -0700

    main: Consult local directories as potential mirrors of providers

    This restores some of the local search directories we used to include when
    searching for provider plugins in Terraform 0.12 and earlier. The
    directory structures we are expecting in these are different than before,
    so existing directory contents will not be compatible without
    restructuring, but we need to retain support for these local directories
    so that users can continue to sideload third-party provider plugins until
    the explicit, first-class provider mirrors configuration (in CLI config)
    is implemented, at which point users will be able to override these to
    whatever directories they want.

    This also includes some new search directories that are specific to the
    operating system where Terraform is running, following the documented
    layout conventions of that platform. In particular, this follows the
    XDG Base Directory specification on Unix systems, which has been a
    somewhat-common request to better support "sideloading" of packages via
    standard Linux distribution package managers and other similar mechanisms.
    While it isn't strictly necessary to add that now, it seems ideal to do
    all of the changes to our search directory layout at once so that our
    documentation about this can cleanly distinguish "0.12 and earlier" vs.
    "0.13 and later", rather than having to document a complex sequence of
    smaller changes.

    Because this behavior is a result of the integration of package main with
    package command, this behavior is verified using an e2etest rather than
    a unit test. That test, TestInitProvidersVendored, is also fixed here to
    create a suitable directory structure for the platform where the test is
    being run. This fixes TestInitProvidersVendored.

### Найдите все коммиты, в которых была изменена функция globalPluginDirs

`Запрос:`
git log -S'globalPluginDirs' --oneline

`Ответ:`
65c4ba7363 Remove terraform binary
125eb51dc4 Remove accidentally-committed binary
22c121df86 Bump compatibility version to 1.3.0 for terraform core release (#30988)
7c7e5d8f0a Don't show data while input if sensitive
35a058fb3d main: configure credentials from the CLI config file
c0b1761096 prevent log output during init
8364383c35 Push plugin discovery down into command package

### Кто автор функции synchronizedWriters?`

`Запрос:`
git log -S'synchronizedWriters'   

`Ответ:`
commit bdfea50cc85161dea41be0fe3381fd98731ff786
Author: James Bardin <j.bardin@gmail.com>
Date:   Mon Nov 30 18:02:04 2020 -0500

    remove unused

commit fd4f7eb0b935e5a838810564fd549afe710ae19a
Author: James Bardin <j.bardin@gmail.com>
Date:   Wed Oct 21 13:06:23 2020 -0400

    remove prefixed io

    The main process is now handling what output to print, so it doesn't do
    any good to try and run it through prefixedio, which is only adding
    extra coordination to echo the same data.

commit 5ac311e2a91e381e2f52234668b49ba670aa0fe5
Author: Martin Atkins <mart@degeneration.co.uk>
Date:   Wed May 3 16:25:41 2017 -0700

    main: synchronize writes to VT100-faker on Windows

    We use a third-party library "colorable" to translate VT100 color
    sequences into Windows console attribute-setting calls when Terraform is
    running on Windows.

    colorable is not concurrency-safe for multiple writes to the same console,
    because it writes to the console one character at a time and so two
    concurrent writers get their characters interleaved, creating unreadable
    garble.

    Here we wrap around it a synchronization mechanism to ensure that there
    can be only one Write call outstanding across both stderr and stdout,
    mimicking the usual behavior we expect (when stderr/stdout are a normal
    file handle) of each Write being completed atomically.

`Запрос:` 
git log -S'synchronizedWriters' --reverse --format="%an <%ae>"

`Ответ:`
Martin Atkins <mart@degeneration.co.uk>
James Bardin <j.bardin@gmail.com>
James Bardin <j.bardin@gmail.com>
root@serv1:/home/kshatyy/Terraform/terraform#

`Исходя из первого коммита, создал функцию synchronizedWriters  Martin Atkins, 
а последующие изменения вносил James Bardin`
