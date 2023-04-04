# java-chatgpt-api

**[中文](https://linweiyuan.github.io//2023/03/14/%E4%B8%80%E7%A7%8D%E5%8F%96%E5%B7%A7%E7%9A%84%E6%96%B9%E5%BC%8F%E7%BB%95%E8%BF%87Cloudflare-v2%E9%AA%8C%E8%AF%81.html)**

Unofficial API in Java (bypass Cloudflare v2 challenge CAPTCHA
using [undetected_chromedriver](https://github.com/ultrafunkamsterdam/undetected-chromedriver)).

---

Also support official API (the way which using API key):

- Chat completion

---

`compose.yaml`

```yaml
services:
  java-chatgpt-api:
    container_name: java-chatgpt-api
    image: linweiyuan/java-chatgpt-api
    ports:
      - 8080:8080
    environment:
      - CHATGPT_PROXY_SERVER=http://chatgpt-proxy-server:9515
#      - NETWORK_PROXY_SERVER=http://host:port
#      - NETWORK_PROXY_SERVER=socks5://host:port
    depends_on:
      - chatgpt-proxy-server
    restart: unless-stopped

  chatgpt-proxy-server:
    container_name: chatgpt-proxy-server
    image: linweiyuan/chatgpt-proxy-server
    restart: unless-stopped
```

### Client

Java Swing GUI application: [ChatGPT-Swing](https://github.com/linweiyuan/ChatGPT-Swing)

Golang TUI application: [go-chatgpt](https://github.com/linweiyuan/go-chatgpt)