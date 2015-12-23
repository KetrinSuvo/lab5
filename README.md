# lab5

Согласно sched_getscheduler(2) для алгоритма планирования SCHED_BATCH определены относительные (динамические) приоритеты NICE, однако утилита ps их НЕ показывает:

user@ubuntu:~$ chrt -b 0 nice -19 ps fo pid,cls,ni,cmd

  PID CLS  NI CMD

 8284  TS   0 bash

 8492   B   -  \_ ps fo pid,cls,ni,cmd

Наеобходимо разобраться, починить. Оформить в виде патча и вложить процедуру сборки deb-пакета утилиты ps.

Результаты представить в виде git-репозитария на github.com
