# TechnicalIndicators

A javascript technical indicators written in javascript. 

# Installation

For nodejs install using npm

``` 
npm install --save technicalindicators
```

```
const SMA = require('technicalindicators').SMA;
```
For browser install using bower

```
bower install --save technicalindicators
```
```
<script src="bower_components/technicalindicators/browser.js"></script>
```

All indicators will be available in window object. So you can just use

```
SMA.calculate({period : 5, values : [1,2,3,4,5,6,7,8,9]});
```
or

```
sma({period : 5, values : [1,2,3,4,5,6,7,8,9], reversedInput : true});
```

#Available Indicators

1. [Simple Moving Average](https://tonicdev.com/anandaravindan/sma "SMA").
2. [Exponential Moving Average](https://tonicdev.com/anandaravindan/ema "EMA").
3. [Weighted Moving Average](https://tonicdev.com/anandaravindan/wma "WMA").
4. [Moving Average Convergence Divergence](https://tonicdev.com/anandaravindan/macd "MACD").
5. [MACD Histogram](https://tonicdev.com/anandaravindan/macd "MACD").
6. [Bollinger Bands](https://tonicdev.com/anandaravindan/bb "BB").
7. [Average True Range](https://tonicdev.com/anandaravindan/atr "ATR").
8. [Relative Strength Index](https://tonicdev.com/anandaravindan/rsi "RSI").
9. [Wilder’s Smoothing (Smoothed Moving Average)](https://tonicdev.com/anandaravindan/wema "WEMA").
10. [Rate of Change (ROC)](https://tonicdev.com/anandaravindan/roc "ROC").
11. [Know Sure Thing (KST)](https://tonicdev.com/anandaravindan/kst "KST").
12. [Stochastic (Stochastic)](https://tonicdev.com/anandaravindan/stochastic "Stochastic").
13. [WilliamsR (WilliamsR)](https://tonicdev.com/anandaravindan/williamsr "WilliamsR").
14. [Accumulation Distribution Line (ADL)](https://tonicdev.com/anandaravindan/adl "adl").
15. [On Balance Volume (OBV)](https://tonicdev.com/anandaravindan/obv "obv").
16. [TRIX (TRIX)](https://tonicdev.com/anandaravindan/trix "trix").

# API

There are three ways you can use to get the indicator results.

##calculate 

Every indicator has a static method ```calculate``` which can be used to calculate the indicator without creating an object.

```javascript
const SMA = require('technicalindicators').SMA;
var prices = [1,2,3,4,5,6,7,8,9,10,12,13,15];
var period = 10;
SMA.calculate({period : period, values : prices})
```

##nextValue

```nextValue``` method is used to get the next indicator value.

```javascript
var sma = new SMA({period : period, values : []});
var results = [];
prices.forEach(price => {
  var result = sma.nextValue(price);
  if(result)
    results.push(result)
});
```

##getResult

This a merge of calculate and nextValue. The usual use case would be

1.Initialize indicator with available price value

2.Get results for initialized values 

3.Use nextValue to get next indicator values for further tick.
    
```javascript
var sma = new SMA({period : period, values : prices});
sma.getResult(); // [5.5, 6.6, 7.7, 8.9]
sma.nextValue(16); // 10.1
```

Note:  Calling nextValue will not update getResult() value. 

#Running tests and getting coverage

```
npm test
```

```
npm run cover
```
# Contribute

Create issues about anything you want to report, change of API's, or request for adding new indicators. You can also create pull request with new indicators.

## Adding new indicators.

1. Fork the project, clone it, run

```
npm install
```
```
gulp watch-test
```

2. Add tests for the indicator. Make it pass. It would be better if a sample of the stockcharts excel is used for the test case.
3. Add the indicator to the index.js
4. Run ```npm run build``` so it adds the indicator to the browser.js
5. Add it to read me, with the link to the tonicdev url containing the sample.
6. Add indicator it to keywords in package.json and bower.json
7. Send a pull request.


