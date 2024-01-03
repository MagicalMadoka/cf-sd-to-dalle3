# cf-sd-to-dalle3

## 项目介绍

这是一个`cloudflare`的ai worker,可以把`cloudflare`提供的`@cf/stabilityai/stable-diffusion-xl-base-1.0`
模型的输入和输出接口转换为`openai`的`dalle-3`接口的输入和输出。从而可以和目前支持openai格式的服务进行集成。

## 部署方法
以下的部署方式任选一种即可
### npm部署

1. 克隆本项目

```bash
git clone https://github.com/MagicalMadoka/cf-sd-to-dalle3.git

cd cf-sd-to-dalle3
```

2. 安装依赖（你需要保证你拥有nodejs的环境，然后执行）

```bash
npm install
```

3. 部署到cloudflare

```bash
npm run deploy
```

如果是第一次部署他会自动打开浏览器，让你授权。

### 直接部署（感谢[MrDgbot](https://github.com/MrDgbot/)提供）
1. 进入https://dash.cloudflare.com/ 找到AI => Workers AI
<img width="100%" height="10%" alt="image" src="https://github.com/MagicalMadoka/cf-sd-to-dalle3/assets/148524140/93657f8f-22fa-40ce-b0f8-aa7183082ad6">
  
2. 选择一个AI可以绑定的模板
<img width="100%" height="10%" alt="image" src="https://github.com/MagicalMadoka/cf-sd-to-dalle3/assets/148524140/b9fdd35b-f067-4fe9-86c0-6fe1c602d5ea">

3. 确认AI绑定
  <img width="100%" height="10%" alt="image" src="https://github.com/MagicalMadoka/cf-sd-to-dalle3/assets/148524140/86de0bca-9827-481f-a6d9-1331424061a5">

5. **复制项目中[index.js](https://github.com/MagicalMadoka/cf-sd-to-dalle3/blob/master/src/index.js)文件**
   
6. 点击编辑代码，然后粘贴index.js，
  <img width="100%" height="10%" src="https://github.com/MagicalMadoka/cf-sd-to-dalle3/assets/148524140/9eef8965-6e2b-4923-b37d-384f187df2d4">

7. 保存部署即可
   <img width="1418" alt="image" src="https://github.com/MagicalMadoka/cf-sd-to-dalle3/assets/148524140/49781fa1-e916-4031-adf7-86eb56331c23">

## 使用

登陆到控制台，看一下你刚才部署的worker的路由是什么。假如你的worker被分配的路由是`cf-sd-to-dalle3.madokax.workers.dev`

### curl

```bash
curl https://cf-sd-to-dalle3.madokax.workers.dev \
  -H "Content-Type: application/json" \
  -d '{
    "model": "dall-e-3",
    "prompt": "A cute cat",
    "n": 1,
    "size": "1024x1024"
  }'
```

### oneapi

- 渠道：自定义
- Base URL：https://cf-sd-to-dalle3.madokax.workers.dev
- 模型：dall-e-3
- 密钥：随便填点啥

## 致谢

- https://cdn.ipfsscan.io
