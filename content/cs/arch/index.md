---
title: "Computer architecture"
date: 2023-07-13T05:31:32+08:00
---

# The computer architecture

## 1. The von neumann architecture

It is a type of computer architecture that combine the program instruction memory and the data storage.

## 2. evaluate the computer architecture

### 2.1 non-time index

- The word length of the machine.
- The storage size of the machine
- The storage bandwidth of the machine
- The bus width of the machine

### 2.2 time 

- The main frequency of the machine
- CPI: clock cycles per instruction
- IPC: instructions per clock cycle
- MIPC: million instructions per second

## 3.The machine number

- real number: using + and - to describe the number
- machine number: using the 1 and 0 to describe the number
  - origin code: $2^n - x$
  - inverse code: 
  - 2's complement

原码是只使用第一位作为符号位，其他位来表示值，反码是在源码的基础上出了符号位置不变，其他位置全部取反

For the 2's complement, there is only one way to describle the 0.

### 3.1 data validation

code spaceing >= e + 1 can check e errors

code spaceing >= 2*t + 1 can repair t errors

parity checking: for parity checking, it use an addtional position to make it number begin even or old.


## 4. cpu


## 5. The microinstruction

### 5.1 Direct instructions format.

Each bits identify a signal. The instruction will be very long.

### 5.2 coded notation

Some signal can be given together, like add and sub. 3:8 decoder can use three bits to represent 8 signals.
