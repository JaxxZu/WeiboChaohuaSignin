# 微博超话自动签到-nodejs版本

---
## 部署方法
### 步骤 1：获取你的微博 Cookie

1. 浏览器打开https://m.weibo.cn/p/tabbar?containerid=100803_-_recentvisit  
2. 按F12打开开发者工具，登录-点击network-找到 **tabbar?containerid=100803_-_recentvisit** 查看请求的cookie  
3. 将 `SUB` `SUBP` `_T_WM`值，复制到脚本91~93行  

<img width="1854" height="957" alt="image" src="https://github.com/user-attachments/assets/a37972a3-e1f7-46c4-bad6-63df07d7920c" />

---


### 步骤 2：部署到vps上  
1. 上传weibo.js脚本到vps  
2. 安装nodejs、curl  
```
sudo apt install nodejs curl -y
```
3. 运行脚本 
```
node /path-to/weibo.js
```

### 步骤 3：设定定时任务
每天运行一次  
```
node /path-to/weibo.js
```
<img  src="https://github.com/user-attachments/assets/1a5c492f-5295-4904-9ff9-90b5fb04c683" />

---

## ✅ 完成！

你应该看到类似这样的输出：

```
[12:30:45] [成功] Cookie 验证成功，已登录
[12:30:48] [成功] 总共获取了 1 页数据，包含 2 个卡片

========== 开始处理超话签到 ==========

[12:30:49] [信息] ✓ 邓紫棋超话 - 今日已签到 (17级)
[12:30:50] [成功] ✓ 王心凌超话 - 签到成功 (13级)
...

========== 签到完成统计 ==========
总共关注超话: 2 个
之前已签到: 1 个
本次新签到: 1 个
签到失败: 0 个
总签到完成率: 100%
```

---

## ⚙️ 可选配置

### 启用微信通知（推荐）

想在签到完成后收到微信消息通知？

1. 访问 https://www.pushplus.plus/
2. 微信扫码登录
3. 复制你的 Token
4. 修改脚本：

```javascript
const PUSHPLUS_CONFIG = {
  enabled: true,  // 启用通知
  token: "粘贴你的Token",  // 这里填入 Token
}
```

签到完成后就会收到微信消息啦！📱

---

## 🔍 只想查看状态不签到？

修改脚本最后两行：

```javascript
// autoCheckin()        // 注释掉这行

analyzeOnly()           // 取消注释这行
```

---

## ❓ 遇到问题？

### Cookie 验证失败
- 检查 SUB 值是否完整复制（不要有多余空格）
- 重新登录微博后重新获取

### 未获取到数据
- 确保你已关注了一些超话
- 检查网络连接

---

## 📝 温馨提示

- ✅ 建议每天只运行一次
- ✅ Cookie 不要分享给他人
- ✅ 如果长时间不用，Cookie 会过期，需重新获取

---

**祝你使用愉快！** 🎉

