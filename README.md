
# toutiao

## 项目简介

通过抓取微信文章和今日头条新闻，仿照今日头条，打造一个自己的今日头条

![](images/toutiao.PNG)


## 基本思路

```
新闻下载 -> 新闻存储 -> 新闻展示
```

抓取源：

1. 今日头条app新闻

https://lf.snssdk.com/api/news/feed/v88/

2. 搜狗微信首页新闻

https://weixin.sogou.com/

备注

微信文章的图片地址会过期，所有抓取的时候直接保存到本地

```
static/images
```

## 项目使用模块

- 下载器使用了：requests
- 解析器使用了：scrapy.Selector
- 存储器使用了：peewee
- web框架使用了：Flask

## 启动运行
```
git clone git@github.com:mymikasa/toutiao.git
cd toutiao
pip install -r requirement.txt
python run.py

```
访问地址就可以打开：http://127.0.0.1:5000/


## 扩展
如果需要更多的新闻源，可以自己抓取新的新闻源，放在`spiders`文件夹下，按照如下字段解析

```python
item = {
    "title": title,   # 新闻标题
    "article_url": article_url,  # 新闻链接
    "source": source,   # 新闻发布者
    "source_url": source_url,  # 发布者链接
    "summary": summary,   # 新闻概要
    "tag": tag,  # 新闻标签
    "publish_time": publish_time,  # 新闻发布时间,datetime类型
    "image": image,  # 新闻图片
    }

```


```python
from models import ArticleModelUtils

ArticleModelUtils.insert(item)
```

这样前台就可以显示了


