# 📈📉&nbsp;&nbsp;simple-back
![PyPI](https://img.shields.io/pypi/v/simple-back)
## Why another python backtester?
There are many backtesters out there, so inevitably, this is just another one of them.

This utility is not built for intra-day trading strategies, as most free data sources only give access to open and close prices.

Other things that make this backtester different are:
### Speed over Accuracy
``simple-back`` offers multiprocessing out of the box, making it blazingly fast, for a slight accuracy trade-off.
In my tests, multiprocessing has only ever led to small changes in results.

Once you have settled on a strategy, you can always run the backtester with multiprocessing disabled.

### Defaults over Configuration
Many backtesters need a great deal of configuration and setup before they can be used. 
Not so this one. 
At it's core you only need one loop, as this backtester can be used like any iterator.
````python
from simple_back import Backtester

for day, event, b in tqdm(Backtester(10_000, cal='NYSE', start='2019-4-1', end='today-1')):
  if event == 'open':
    # do stuff on open
  if event == 'close':
    # do stuff on close
````
I'm currently trying to figure out if I can make this iterator use multiprocessing, but until then you will have to use a [strategy object](https://render.githubusercontent.com/view/ipynb?commit=503b7c54ed188028d3ed4abd60c72b724b034d70&enc_url=68747470733a2f2f7261772e67697468756275736572636f6e74656e742e636f6d2f4d696e6958432f73696d706c652d6261636b2f353033623763353465643138383032386433656434616264363063373262373234623033346437302f6578616d706c65732f75736167655f6578616d706c65732e6970796e62&nwo=MiniXC%2Fsimple-back&path=examples%2Fusage_examples.ipynb&repository_id=265216728&repository_type=Repository#Strategy-Class) if you want faster backtests.

### Exensibilty over Trying-to-do-it-all
This is inteded to be a lean framework where, e.g. adding crypto data is as easy as extending the ``DailyPriceProvider`` class.

### Prototyping over Production
This should go without saying, beware before using this in any production systems. This is intended for rapid prototyping of strategies and nothing more.

## 
