<img width="813" height="436" alt="image" src="https://github.com/user-attachments/assets/027cd4cc-4824-4bed-a0f9-67f322d37821" />  

Таблица: Древо от оболочки до pid1  
| Команда | Вывод | PPID |
| :--- | :--- | :--- |
| `ps -o pid,ppid,user,cmd -p $$` | PID PPID USER CMD<br>3706 3646 user1 /usr/bin/bash | 3646 |
| `ps -o pid,ppid,user,cmd -p 3646` | PID PPID USER CMD<br>3646 3632 user1 /usr/libexec/ptyxis-agent --socket-fd=3 --rlimit-nofile | 3632 |
| `ps -o pid,ppid,user,cmd -p 3632` | PID PPID USER CMD<br>3632 2166 user1 /usr/bin/ptyxis --gapplication-service | 2166 |
| `ps -o pid,ppid,user,cmd -p 2166` | PID PPID USER CMD<br>2166 1 user1 /usr/lib/systemd/systemd --user | 1 |  
И так, мы дошли до PID 1, им является  является менеджер пользовательских служб у которого не родителя, так как процесс запусткается на прямую ядром.  
<img width="338" height="71" alt="image" src="https://github.com/user-attachments/assets/65159225-ef8c-43c8-b8e8-36fe3d0bf04f" />  
Благодаря команде ps -e | wc -l мы можем увидеть общее число процессов в системе.  
<img width="461" height="63" alt="image" src="https://github.com/user-attachments/assets/f3bad7e5-8e6d-49e7-8228-149edbd55116" />  
Благодаря команде ps -eo state | grep -c "S" мы можем увидеть количество наших S процессов(спящих). Таких процессов множество по нескольким причинам:  
1) Процессы ожидающие определенных условий.
2) Процессы которые активны небольшой промежуток времени на фоне работы системы(менеджеры сети к примеру).
Такой принцип работы процессов необходим для оптимизации работы системы.


