# FUNK

A C continuation implementation inspired by Adam Dunkels' ProtoThread.

Only 7 C macros and 1 struct definition; less than 100 lines of code.

Simple yet POWERFUL.

Now you can write a coroutine (generator, to be exact) in the following way, quick, simple, and in a natural way.

Enjoy the power of YIELD();

```C
Continuation* add(Continuation* co,
    int a, int b, int * ret)
{
  struct timespec now;
  VAR_BEGIN
    struct timespec start;
  VAR_END

  if (!this || a < 0 || b < 0) { *ret = -1; EXIT(); }
  if (KILL_SIGNALLE()) EXIT();

  clock_gettime(CLOCK_REALTIME, &this->start);
  while(1)
  {
    clock_gettime(CLOCK_REALTIME, &now);
    if ((now.tv_sec - this->start.tv_sec) > 1)
      break;
    YIELD();
  }
  *ret = a + b;
  EXIT();
}
```
