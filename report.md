# Лабораторная работа 5

1.  **Задание 1**

Создаем файл ```pre-commit``` в директории ```.git/hooks```

  ```bash
  touch .git/hooks/pre-commit
  chmod +x .git/hooks/pre-commit  # Делаем файл исполняемым
   ```
Записываем в него Bash-скрипт для проверки .txt файлов перед коммитом

  ```bash
    #!/bin/bash

    FILES_TO_COMMIT=$(git diff --cached --name-only --diff-filter=ACM | grep '\>
    
    ERRORS=0
    
    for FILE in $FILES_TO_COMMIT; do
        if [[ -f "$FILE" ]]; then
            if ! grep -iq "author is" "$FILE"; then
                echo "Ошибка: В файле '$FILE' отсутствует строка 'author is'."
                ERRORS=1
            fi
        else
            echo "Предупреждение: Файл '$FILE' не найден. Возможно, он был удал>
        fi
    done
    
    if [[ $ERRORS -ne 0 ]]; then
        echo "Коммит отменён: файлы .txt должны содержать строку 'author is'."
        exit 1
    fi
    
    echo "Проверка пройдена: все .txt файлы содержат 'author is'."

    exit 0
   ```
![Снимок экрана 2024-12-17 144806](https://github.com/user-attachments/assets/5e8812e9-c48b-4843-9fbd-9d223951eda7)

Проверяем работу скрипта, создавая корректные и некорректные файлы.

![Снимок экрана 2024-12-17 145135](https://github.com/user-attachments/assets/93f72e87-f375-493d-b633-daf8aa8ccb6c)


2.  **Задание 2**

   Последовательно выполняем все шаги из задания 2 (лабораторная работа 5).
   
   ![Снимок экрана 2024-12-17 171032](https://github.com/user-attachments/assets/e187f71e-5f7c-450e-bccb-1de52ae11974)
    
   ![Снимок экрана 2024-12-17 172408](https://github.com/user-attachments/assets/eb2958b1-9b5c-455d-a48f-c91618ed410c)

   ![Снимок экрана 2024-12-17 173552](https://github.com/user-attachments/assets/557aae46-20fb-45ed-8b84-2fe6bc881afd)

