
# Что такое GitFlow?

GitFlow - модель ветвления Git.

_Ключевые идеи_:

1. Данная модель отлично подходит для организации рабочего процесса на основе релизов,
2. Gitflow предлагает создание отдельной ветки для исправлений ошибок в продуктовой среде.

_Последовательность работы при использовании модели Gitflow_:

1. Из _master_ создается ветка _develop_.
2. Из _develop_ создаются ветки _feature_.
3. Когда разработка новой функциональности завершена, она объединяется с веткой _develop_.
4. Из _develop_ создается ветка _release_.
5. Когда ветка релиза готова, она объединяется с _develop_ и _master_.
6. Если в _master_ обнаружена проблема, из нее создается ветка _hotfix_.
7. Как только исправление на ветке _hotfix_ завершено, она объединяется с _develop_ и _master_.

---
# Чем `merge` отличается от `rebase`?

`git merge` - выполняет слияние коммитов из одной ветки в другую. В этом процессе изменяется только целевая ветка. История исходных веток остается неизменной.
![[Pasted image 20240226191031.png]]

- _Преимущества_:
    
    1. Простота,
    2. Сохраняет полную историю и хронологический порядок,
    3. Поддерживает контекст ветки.
    
    _Недостатки_:
    
    1. История коммитов может быть заполнена (загрязнена) множеством коммитов,
    2. Отладка с использованием git bisect может стать сложнее.
- `git rebase` - сжимает все изменения в один патч. Затем интегрирует патч в целевую ветку. В отличии от _merge_, _rebase_ перезаписывает историю, потому что она передаётся завершенную работу из одной ветки в другую. В процессе устраняется нежелательная история.

![[Pasted image 20240226191049.png]]

_Преимущества_:

1. Упрощает потенциально сложную историю,
2. Упрощение манипуляций с единственным коммитом,
3. Избежание слияния коммитов в занятых репозиториях и ветках,
4. Очищает промежуточные коммиты, делая их одним коммитом, что полезно для DevOps команд.

_Недостатки_:

1. Сжатие фич до нескольких коммитов может скрыть контекст
2. Перемещение публичных репозиториев может быть опасным при работе в команде,
3. Появляется больше работы,
4. Для восстановления с удаленными ветками требуется принудительный пуш. Это приводит к обновлению всех веток, имеющих одно и то же имя, как локально, так и удаленно.

---
# Чем `tag` отличается от `branch`?

И _tag_ и _branch_ представляют собой указатели на коммиты.

- Ветка представляет собой отдельный поток разработки, который может выполняться одновременно с другими разработками в той же кодовой базе. Коммит в ветке указывает на изменения, которые добавляются в новых коммитах
- Тег представляет собой версию определенной ветки в определенный момент времени.

_Tag_ представляет собой версию той или иной ветки в определенный момент времени. _Branch_ представляет собой отдельный поток разработки, который может выполнятся одновременно с другими разработками в той же кодовой базе.

---
# В ветке _develop_ есть коммит с изменениями, которые нужно перенести в ветку _master_. Как это сделать?

Необходимо найти хеш этого коммита и выполнить следующую комманду в ветке, в которую нужно перенести коммит.

```
git cherry-pick <commit_hash>
```
---
# Для чего нужна команда `git commit --amend`?

`commit --ammend` используется для исправления сообщения последнего коммита. Также возможно использовать, чтобы добавить файлы в индекс (`git add`), после добавить файлы в коммит `git commit --ammend`.

---
# Что такое Trunk-based development?

Trunk-based Development (TBD) - модель ветвления, в которой разработчики совместно работают над кодом в одной ветви, называемой "стволом" (trunk). При этом другие ветви имеют короткий срок жизни благодаря использованию документированных методов.

---
# Состояние репозитория ушло на много коммитов вперед. Как откатить весь репозиторий к определенному коммиту?

```
git reset --hard <tag/branch/commit hash>`
```

---
# В репозиторий запушен коммит с изменениями в двух файлах. Как откатить изменения этого коммита?

```
git revert
```
