# Git. Как решить merge conflict? Что такое rebase, cherry-pick?

1. **Merge Conflict (конфликт слияния):** Он возникает, когда Git не может автоматически объединить изменения из разных веток в одной общей ветке. Для решения конфликта тебе потребуется вмешательство. Чтобы разрешить merge conflict, ты можешь вручную исправить файлы, помеченные как конфликтные, сливая изменения в соответствии с тем, как ты считаешь правильным. После этого добавь изменения, закоммить и заверши слияние.  
  
2. **Rebase (перебазирование):** Это процесс изменения истории коммитов в ветке, предполагая её начало с определённого коммита. При использовании rebase коммиты из твоей ветки применяются к последнему коммиту из целевой ветки. Это позволяет создать чистую и линейную историю коммитов без дополнительных слияний.  
  
3. **Cherry-pick (выборочное применение коммита):** Этот инструмент позволяет выбирать конкретные коммиты из одной ветки и применять их к другой. Это может быть полезно, если тебе нужно применить изменения из одного коммита в отдельную ветку без копирования всей ветки или слияния.  
  
Итак, решить merge conflict поможет внимательное внесение изменений, rebase - создание чистой истории коммитов, а cherry-pick - выборочное применение необходимых изменений.

---
# В чем разница между git merge и git rebase?

Разница между `git merge` и `git rebase` заключается в том, как происходит объединение изменений из разных веток.  
  
1. **Git Merge:**  
   - `git merge` объединяет изменения из одной ветки в другую. При слиянии Git создает специальный коммит, который объединяет изменения из всех веток. При этом история коммитов становится нелинейной, поскольку сохраняется информация о том, где и когда было произведено слияние. Эта команда хорошо подходит для командной работы и объединения разных рабочих потоков разработки.  
  
2. **Git Rebase:**  
   - `git rebase` перебазирует (переносит) коммиты из одной ветки в другую. В результате история коммитов становится линейной, так как изменения применяются к конечному коммиту целевой ветки. Это позволяет создать более чистую и упорядоченную историю коммитов. Основное преимущество заключается в том, что при перебазировании можно избежать создания лишних слияний и сохранить более легкую для понимания историю проекта.  
  
Итак, чтобы сделать выбор между `git merge` и `git rebase`, руководствуйся архитектурой проекта и наличием конфликтов. Если тебе нужно сохранить наличие специальных коммитов с информацией о слияниях разных веток, используй `git merge`. Если же тебе важна чистая история коммитов без лишних слияний, тогда `git rebase` может быть лучшим вариантом.

---
# Какие UI использовали?

GitHub Desktop, GitKraken, Sourcetree, SmartGit и GitAhead.

---
# Какая разница между GitLab/GitHub/Bitbucket?

  
GitLab, GitHub и Bitbucket - все они платформы для управления исходным кодом с использованием системы контроля версий Git, но у них есть свои особенности:  
  
1. **GitHub**:  
   - Наиболее популярная и распространенная платформа, особенно среди разработчиков open source проектов.  
   - Основной фокус на социальном взаимодействии и общих проектах.  
   - Хостинг открытого и закрытого кода.  
   - Имеет множество интеграций с другими сервисами и инструментами разработки.  
  
2. **GitLab**:  
   - Предоставляет возможности для DevOps и CI/CD.  
   - Можно развернуть GitLab на собственных серверах (self-hosted).  
   - Включает в себя инструменты для управления задачами, отслеживания ошибок и даже внутренних wiki-страниц.  
  
3. **Bitbucket**:  
   - Принадлежит корпорации Atlassian, которая предлагает также Jira и Confluence.  
   - Поддерживает Git и Mercurial.  
   - Хостинг закрытого кода бесплатен для небольших команд.  
  
Выбор между ними обычно зависит от того, какие инструменты и функции наиболее важны для вашего проекта или команды разработчиков.

---

# Какая разница между Git pull/Git fetch?

Команда **git pull** выполняет две операции сразу: **git fetch** и **git merge**.  
- **git fetch** забирает изменения с удаленного репозитория на локальную машину, но не применяет их к вашему текущему рабочему дереву.  
- **git pull**, с другой стороны, забирает изменения (git fetch) и автоматически сливает их в ваш текущий рабочий процесс (merge).  
  
Если вы хотите просто получить изменения и решить, когда и как их внести в свое рабочее дерево, лучше воспользоваться **git fetch**. Если уверены, что изменения из удаленного репозитория могут быть просто и быстро слиты в вашу текущую ветку, то используйте **git pull**.

---


# Что такое Git-Flow?

Git-Flow - это модель ветвления и работы с ветками в Git, разработанная для более удобного управления рабочим процессом в больших проектах. Она определяет строгие правила и набор названий веток, основанный на типе изменений, что помогает лучше организовать работу команды над проектом.  
  
Git-Flow включает в себя основные типы веток, такие как:  
- **master** - в этой ветке находится стабильная версия проекта.  
- **develop** - ветка, в которую сливаются все изменения из других веток для тестирования перед объединением с **master**.  
- **feature** - ветки для добавления нового функционала.  
- **release** - ветки для подготовки нового релиза.  
- **hotfix** - ветки для исправления критических ошибок в продакшене.  
  
Использование Git-Flow помогает структурировать работу над проектом, минимизирует конфликты при слиянии изменений и упрощает управление версиями.

---

# Версионирование. Какая разница между SemVer и CalVer?

SemVer и CalVer - это два разных подхода к версионированию программного обеспечения.  
  
**SemVer (Semantic Versioning)** - это семантическое версионирование, которое предполагает использование трех числовых компонентов в формате X.Y.Z, где X - мажорная версия (совместимость нарушена), Y - минорная версия (новый функционал без нарушения совместимости), Z - патч версия (исправление ошибок без изменения API).  
  
**CalVer (Calendar Versioning)** - это версионирование, основанное на календаре. В CalVer версия программного обеспечения определяется датой или временем, когда была выпущена новая версия. Например, YYYY.MM.DD или год.месяц.день. Этот метод облегчает понимание последовательности релизов, а также прост в использовании.  
  
Разница между SemVer и CalVer заключается в том, что SemVer использует числовые компоненты для обозначения версий на основе изменений в API, в то время как CalVer опирается на календарь для определения версий. Выбор между ними зависит от предпочтений команды разработчиков и специфики проекта.

---
# Тестирование. Какие существуют виды? Как писать тесты, TDD?

1. **Модульное тестирование (Unit Testing)**: Проверка отдельных модулей (функций, классов) на корректность их работы.  
    
2. **Интеграционное тестирование (Integration Testing)**: Проверка взаимодействия между модулями или системами.  
  
3. **Приемочное тестирование (Acceptance Testing)**: Проверка соответствия продукта требованиям заказчика.  
  
4. **Функциональное тестирование (Functional Testing)**: Проверка функциональности программы.  
  
5. **Нагрузочное тестирование (Load Testing)**: Проверка, как система работает при больших нагрузках.  
  
Теперь про TDD (Test-Driven Development) - это методология разработки, при которой сначала пишутся тесты, затем код, который делает эти тесты проходящими, и только потом переходят к следующему шагу.  
  
Шаги TDD:  
1. **Написание теста (RED)**: Сначала пишется тест, который описывает необходимое поведение.  
2. **Прохождение теста (GREEN)**: Затем пишется минимальный код, который позволяет пройти написанный тест.  
3. **Рефакторинг (REFACTOR)**: После прохождения теста код улучшается без изменения функциональности.  
  
TDD помогает создавать более надежный и стабильный код, так как каждое изменение контролируется тестами. Начни с написания теста для требуемой функциональности, затем пиши код, который делает этот тест успешным. 

---
# В чем разница между компилируемыми и интерпретационными языками программирования?

Разница между компилируемыми и интерпретируемыми языками программирования связана с тем, как программный код преобразуется в машинный код для выполнения компьютером:  
  
1. **Компилируемые языки (Compiled Languages)**:  
   - Код программы преобразуется в машинный код однократно компилятором перед выполнением.  
   - Полученный исполняемый файл выполняется на целевой платформе независимо от исходного кода.  
   - Примеры: C, C++, Rust.  
  
2. **Интерпретируемые языки (Interpreted Languages)**:  
   - Код программы выполняется построчно (инструкция за инструкцией) интерпретатором во время выполнения.  
   - Интерпретатор анализирует и исполняет код одновременно, без необходимости компиляции.  
   - Примеры: Python, Ruby, JavaScript.  
  
Оба типа языков имеют свои преимущества и недостатки. Компилируемые языки обычно работают быстрее, так как код уже скомпилирован в машинный код, но они требуют компиляции перед запуском. Интерпретируемые языки более гибкие и обычно проще для начинающих программистов, но могут иметь более низкую производительность из-за интерпретации в реальном времени.
