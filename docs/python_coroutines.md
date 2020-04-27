# Python coroutines
```python
import asyncio
import time


async def manage_file_as_fake_task(delay, name):
    # await asyncio.sleep(delay)
    await asyncio.get_event_loop().run_in_executor(None, time.sleep, delay)
    print('task for file %s successfully ran' % name)


async def run_tasks(tasks):
    for task in tasks:
        try:
            await task
        except asyncio.TimeoutError:
            print('task expired')


def create_tasks():
    tasks = []
    files = [
        (1, 'file1'),
        (3, 'file2'),
        (4, 'file3'),
        (2, 'file4'),
        (1, 'file5'),
        (1, 'file6')
    ]

    for file in files:
        tasks.append(
            asyncio.create_task(manage_file_as_fake_task(*file))
            # asyncio.wait_for(manage_file_as_fake_task(*file), timeout=2)
        )

    return tasks


async def run_async():
    tasks = create_tasks()
    await run_tasks(tasks)


def main():
    asyncio.run(run_async())


if __name__ == '__main__':
    main()

```