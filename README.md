# COINPAY SDK

## Introduction

COINPAY.ua - payment platform that provides: 
- deposit and withdrawal of funds to/from bank cards
- transfers within the platform free of commission fee
- currency and cryptocurrency exchange
## Requirements

This library requires Python version from 3.5 to 3.9.

Please note that this library also uses requests and certifi. These libraries' supported Python versions can differ from the versions supported by coinpay_sdk
## Installation
We recommend using [PyPI](https://pypi.org/project/coinpay_sdk/) to install the COINPAY Software Development Kit for Python.
```bash
$ pip install coinpay_sdk
```
## Usage
After the [registration](https://coinpay.ua/), api_key and api_secret will become available.
You can get them [here](https://coinpay.ua/settings/).
Please note that some features are fully available only after the [verification](https://coinpay.ua/verification/variants).

## Example
The [examples](examples) folder has basic and advanced examples.

Base api url - https://api.coinpay.ua/
```python
from coinpay.processing import CoinPay

api_key = ''
api_secret = ''
host = 'https://api.coinpay.ua/'

pay = CoinPay(api_key=api_key,
              api_secret=api_secret,
              host=host)


def get_total_balance(view_currency) -> float:
    """
    Shows total balance for account in chosen currency
    :param view_currency: currency for total balance
    :return: total balance amount for account
    """
    result = pay.get_balance()
    balance_dict = result.get('balance')
    total = 0
    for currency in balance_dict:
        total += ((balance_dict.get(currency).get(view_currency).get('total')) +
                  (balance_dict.get(currency).get(view_currency).get('reserved')))
    return total
print(get_total_balance('BTC'))
```

## Documentation

Please see the [Documentation](https://github.com/coinpay-com-ua/coinpay-official-api-docs) for more details.

## Contact Us

- Website: https://coinpay.ua
- Mail: support@coinpay.ua
- Telegram BOT: https://t.me/COINPAY_Bot
- Facebook: https://www.facebook.com/coinpay.com.ua

## License
COINPAY SDK for Python is licensed under MIT License.
