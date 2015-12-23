# lab5

Согласно sched_getscheduler(2) для алгоритма планирования SCHED_BATCH определены относительные (динамические) приоритеты NICE, однако утилита ps их НЕ показывает:

user@ubuntu:~$ chrt -b 0 nice -19 ps fo pid,cls,ni,cmd

  PID CLS  NI CMD

 8284  TS   0 bash

 8492   B   -  \_ ps fo pid,cls,ni,cmd

Наеобходимо разобраться, починить. Оформить в виде патча и вложить процедуру сборки deb-пакета утилиты ps.

Результаты представить в виде git-репозитария на github.com



_________________________________________________

не компилируется без пары библиотек > sudo aptitude install libncurses5-dev libncursesw5-dev

нужно скачать исходные тексты
apt-get source procps

Проблема  в  функции (файл ps/output.c):

static int pr_nice(char *restrict const outbuf, const proc_t *restrict const pp){
if(pp->sched!=0 && pp->sched!=-1) return snprintf(outbuf, COLWID, "-");
return snprintf(outbuf, COLWID, "%ld", pp->nice);
+}


создаем patch.diff


создаем debian-патч ( необходимо иметь в соседнем каталоге оригинальный тарболл)  dpkg-source --commit





