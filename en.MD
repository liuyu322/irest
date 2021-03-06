# irest
<a href="https://github.com/Jon-Millent/irest/blob/master/README.md">中文</a>
|
<a href="https://github.com/Jon-Millent/irest/blob/master/en.MD">English</a>

Write the code to write tired? To relax, to check the weather with the command line,read the news, read a joke, browse pictures, looking for a romantic programmer ~

## Install

`npm install irest-cli -g` & `cnpm install irest-cli -g`


## Function list

* `irest news`  Check out the news
* `irest joke`  Come a joke
* `irest weather [city name]`  Look at the weather
* `irest image [Picture name(required)]`  Search for a picture to see

  
  
![image](https://github.com/Jon-Millent/irest/blob/master/show01.gif?raw=true)


## Question

*   `irest image xxx` wrong？ Please use the high version `nodejs > 8.0.x`
*   Image rendering misplaced? Please modify the resolution of the configuration file, see the following configuration file description
     `/config/index.js`
    ```javascript
        image: {
            size: 100 // Resolution
        }
    ```
*   Can not find the weather in my city? Please add city id in `/ config / city.js`

## Profile `/config/index.js`
```javascript
  let ErrorMessage = '): 获取数据失败'

  let baseConfig = {
    joke: { // joke config
      url: "http://www.walxh.com/pc/wicked/", // url
      page: {
        pageName: "page", // page key
        start: 1, // start page
        pageSize: 10, // How much data per page
        maxLength: 100, // The maximum number of pages

        listName: '.main-area', // parent element class name
        listTitle: '.main-title', // title class name
        listContent: '.main-content', // content class name
        listTime: '.main-time' // time class name
      },
      error: ErrorMessage
    },
    news: { // news config
      url: "http://sh.qihoo.com/",
      page: {
        listName: '.atom-editor',
        listTitle: '.title',
        listContent: '.subtitle'
      },
      error: ErrorMessage
    },
    weather: { // weather config
      url: "https://www.duba.com/static/weather_info/",
      data: {
        concatStr: '.html'
      },
      ipUrl: "http://int.dpool.sina.com.cn/iplookup/iplookup.php?format=json",
      page: {
        listName: '.atom-editor',
        listTitle: '.title',
        listContent: '.subtitle'
      },
      error: ErrorMessage
    },
    image: { // image config
      url: "https://cn.bing.com/images/search?FORM=HDRSC2&q=",
      imgClassName: '.mimg',
      error: ErrorMessage,
      size: 180 // Image output resolution, if the image shows a newline please modify this parameter to the appropriate value
    }
  }

```
