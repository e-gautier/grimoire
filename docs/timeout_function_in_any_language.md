# timeout a function

<!-- tabs:start -->

#### ** Python **

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

#### ** Java **

```java
final Future<?> handler = executor.submit(() -> {
    try {
        System.out.println("starting task");
        Thread.sleep(2000);
        System.out.println("ending task");
    } catch (InterruptedException exception) {
        System.out.println("timeout");
    }
});

ScheduledFuture<?> scheduledFuture = executor.schedule(() -> {
    if (!handler.isDone()) {
        handler.cancel(true);
    } else {
        // TODO if task is done on time
    }
}, 1000, TimeUnit.MILLISECONDS);
```

<!-- tabs:end -->
