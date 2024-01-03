# cf-sd-to-dalle3

## 项目介绍

这是一个`cloudflare`的ai worker,可以把`cloudflare`提供的`@cf/stabilityai/stable-diffusion-xl-base-1.0`
模型的输入和输出接口转换为`openai`的`dalle-3`接口的输入和输出。从而可以和目前支持openai格式的服务进行集成。

## 使用方法

1. 克隆本项目

```bash
git clone https://github.com/MagicalMadoka/cf-sd-to-dalle3.git

cd cf-sd-to-dalle3
```

2. 安装依赖
	 你需要保证你拥有nodejs的环境，然后执行

```bash
npm install
```

3. 部署到cloudflare

```bash
npm run deploy
```

如果是第一次部署他会自动打开浏览器，让你授权。

## 使用

假如你的worker被分配的路由是`cf-sd-to-dalle3.madokax.workers.dev`

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
