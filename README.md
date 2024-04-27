# PintOs Alarm Clock

This project is part of COMP_7035_OS_Assignment1, where I've implemented an alarm clock functionality to enhance the Pintos Operating System. The aim was to create a more efficient timer sleep mechanism without busy waiting and ensure that threads sleep exactly the time they are supposed to.

## Preliminaries

The project has been guided by resources from S. Afrianto (2011) on avoiding busy waits in `timer_sleep` and a YouTube tutorial by J. Doe (2020).

- Afrianto, S. (2011). [Avoiding busy wait in timer_sleep on Pintos](https://souzanurafrianto.wordpress.com/2011/05/06/avoiding-busy-wait-in-timer_sleep-on-pintos/).
- Doe, J. (2020). [Pintos Tutorial Video](https://www.youtube.com/watch?v=myO2bs5LMak).

The tests for Alarm single, multiple, simultaneous, zero, and negative have passed, marking the assignment with a score of 100%.

## Installation

Clone the repository to get started:

```sh
git clone https://github.com/SAMi-Rn/Pintos-Alarm-Clock-Assingment-1.git
```
## Data Structures
In `threads.h`, I introduced `ticks_to_wakeup` to track the tick count for when a thread should wake up and  `sleeping_elem` to manage the sleeping threads efficiently.

```sh
struct thread {
  ...
  int64_t ticks_to_wakeup;
  struct list_elem sleeping_elem;
  ...
};
```
## Algorithms
I implemented `thread_sleep` and `wake_up_threads` to manage the sleeping and waking up of threads based on the system's tick count.

## Synchronization
Careful synchronization was achieved by disabling interrupts before manipulating shared data and ensuring the sleeping list was always sorted by wake-up ticks.

## Rationale
The new design brings efficiency and minimizes CPU wastage while maintaining precision in thread scheduling. However, there are complexities, such as managing the ordered insertion into the `sleeping_list` and ensuring accurate timing.

## Debugging Struggle Efforts
Our debugging process addressed issues such as maintaining the `sleeping_list` order and handling race conditions with interrupts. We had to ensure that all threads woke up at the correct times, even with simultaneous sleep/wake requests.

## YouTube Link
A detailed explanation of the implementation and a walk-through of the tests can be found on YouTube:
``` sh
https://youtu.be/RM0dMxRyE8k
```
