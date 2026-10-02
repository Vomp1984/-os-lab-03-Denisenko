Первый вывод top:
<img width="1196" height="745" alt="image" src="https://github.com/user-attachments/assets/07e89cb5-859c-45fd-bd92-4e44f21ec767" />  

<img width="729" height="400" alt="image" src="https://github.com/user-attachments/assets/a3bfb0fe-bf42-4da4-9fb9-292043fa7e20" />  

Команда renice -n 0 -p выполняется только с sudo из-за всторенной системы безопасности, ведь изменение приоритета задачи в ручную может привести к негативным последствиям.  
Изначальное распределение между процессами с приоритетами 0 и 19 было 97.7 и 1.7  
taskset -c 0 необходима для  привязки процесса к определенному ядру процессора. 


