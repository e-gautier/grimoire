# Python timeout function
```python
import signal
import time
from contextlib import contextmanager


@contextmanager
def timeout(time):
    signal.signal(signal.SIGALRM, raise_timeout)
    signal.alarm(time)

    try:
        yield
    except TimeoutError:
        print('timeout')
    finally:
        signal.signal(signal.SIGALRM, signal.SIG_IGN)


def raise_timeout(signum, frame):
    raise TimeoutError


def main():
    with timeout(1):
        print('starting task')
        time.sleep(2)
        print('ending task')


if __name__ == '__main__':
    main()
```