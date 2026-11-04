# 游乐园 ♥ 调查表

线上地址：**https://wat3onxrniu.github.io/park-date/**

两个人各开一个页面，勾各自那一栏，实时对在一起看。

## 怎么用

1. 打开网页，右上角点「复制邀请链接」。
2. 把链接发给对方。
3. 各自勾选，页面上的方框会实时变成三种状态：
   - 深灰：只有你勾了
   - 粉红：只有 TA 勾了
   - 对角双色：两个人都勾了
4. 拉到最下面，「你们的对照」会算默契度，并列出两个人重合的项目。

答案同时存在浏览器本地（localStorage），关掉页面再打开还在。

## 怎么放到网上（GitHub Pages，免费）

1. 登录 GitHub，点右上角 `+` → **New repository**。
2. 仓库名随便起，比如 `park-date`，选 **Public**，点 Create。
3. 在仓库页点 **uploading an existing file**，把本文件夹里的 `index.html` 拖进去，Commit。
4. 仓库上方的 **Settings** → 左侧 **Pages** → Branch 选 `main`、目录选 `/ (root)` → **Save**。
5. 等一分钟，地址是 `https://<你的用户名>.github.io/park-date/`。

之后把这个地址发给对方就行。房间号会自动带在链接的 `#r=xxxxxx` 里，两个人用同一条链接就进了同一间。

## 数据是怎么同步的

没有后端服务器，用的是公共 MQTT 服务器（浏览器直连 WebSocket）：

- `wss://broker.emqx.io:8084/mqtt`
- `wss://broker.hivemq.com:8884/mqtt`
- `wss://test.mosquitto.org:8081/mqtt`

按顺序试，连上哪个用哪个。每个人的答案发到自己房间的一个独立主题上，并设成保留消息，所以后进来的人也能立刻看到对方已经勾了什么。

连不上的时候页面会提示，勾选内容照旧存在本地，可以点「复制我的答案」把结果发给对方手工对照。

## 一台电脑上测两个人

在地址后面加 `?as=随便一个名字`，比如：

```
index.html?as=aaa#r=test01
index.html?as=bbb#r=test01
```

两个标签页就是两个独立的人。
