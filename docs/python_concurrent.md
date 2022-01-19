# Python concurrent
```python
from concurrent.futures import ThreadPoolExecutor
from typing import Tuple, Union

import requests
from faker import Faker

faker = Faker()
websites = [faker.domain_name() for _ in range(50)]


def response_time(domain: str) -> Union[None, Tuple[str, float]]:
    try:
        response = requests.get(f"https://{domain}")
    except requests.exceptions.RequestException:
        return
    return domain, response.elapsed.total_seconds()


with ThreadPoolExecutor() as executor:
    gen = executor.map(response_time, websites)
for result in gen:
    if result:
        print(result)

```