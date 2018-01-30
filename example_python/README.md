# 用python调用百度OCR接口实例

* 本文主要针对Python开发者，描述百度文字识别接口服务的相关技术内容。
  OCR接口提供了自然场景下整图文字检测、定位、识别等功能。文字识别的结果可以用于翻译、搜索、验证码等代替用户输入的场景。
  
* 首先安装接口模块，在电脑终端里执行 pip install baidu-aip 即可。

* 调用代码：
  <br/>from aip import AipOcr  
  <br/>#你的 APPID AK SK """
  <br/>APP_ID = '你的 App ID'
  <br/>API_KEY = '你的 Api Key'
  <br/>SECRET_KEY = '你的 Secret Key'

  client = AipOcr(APP_ID, API_KEY, SECRET_KEY)

  上面代码块里APP_ID 、API_KEY、SECRET_KEY 三个值对应在http://console.bce.baidu.com/ai/#/ai/ocr/app/list 这里找到，需要用百度账号登录，然后创建一个应用，如下图：
  ![picture](https://github.com/MingQuanXu/python_interview/blob/master/example_python/ocr.jpg)

* #读取图片
```
 def get_file_content(filePath):
    with open(filePath, 'rb') as fp:
        return fp.read()

 image = get_file_content('ml.jpg')
```
  #调用通用文字识别, 图片为远程url图片
  <br/>#res=client.basicGeneralUrl(url)
  <br/>#调用通用文字识别, 图片为本地图片 
  <br/>res=client.general(image)
  
  这样就完成了调用，以下是调用图片识别结果案例：
  
  <img src="https://github.com/MingQuanXu/python_interview/blob/master/example_python/ml.jpg" alt="ml.jpg" align=left />
 
* #得到图片文字 
  ```
  for item in res['words_result']:
      print item['words']
  ```

  ![result](https://github.com/MingQuanXu/python_interview/blob/master/example_python/result.jpg)