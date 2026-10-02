Таблица: Древо от оболочки до pid1  
| команда | вывод | PPID |  
| ps -o pid,ppid,user,cmd -p $$ | PID    PPID USER     CMD  
3706    3646 user1    /usr/bin/bash | 3646 |  
| ps -o pid,ppid,user,cmd -p 3646 | PID    PPID USER     CMD  
3646    3632 user1    /usr/libexec/ptyxis-agent --socket-fd=3 --rlimit-nofile | 3632 |  
| ps -o pid,ppid,user,cmd -p 3632 | PID    PPID USER     CMD  
3632    2166 user1    /usr/bin/ptyxis --gapplication-service | 2166 |  
| ps -o pid,ppid,user,cmd -p 2166 | PID    PPID USER     CMD  
2166       1 user1    /usr/lib/systemd/systemd --user | 1 |  


