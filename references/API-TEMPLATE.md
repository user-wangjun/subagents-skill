# API Template / API 端点模板

Use this template when documenting API endpoints for a new subagent.

---

```markdown
# API.md - <Agent Name> API 端点

_创建于 YYYY-MM-DD_

---

## 🔑 认证方式 / Authentication

| 属性 | 值 |
|------|-----|
| **认证类型** | <如：Bearer Token / API Key / OAuth> |
| **Header 名称** | <如：Authorization> |
| **Token 格式** | <如：Bearer <token>> |
| **API Key** | `<your-api-key>` |
| **获取方式** | <如何获取 Key> |

---

## 📡 API 端点 / Endpoints

### 基础信息 / Base Info

| 属性 | 值 |
|------|-----|
| **Base URL** | `<如：https://api.example.com/v1>` |
| **请求格式** | <如：JSON> |
| **响应格式** | <如：JSON> |
| **速率限制** | <如：100 次/分钟> |

---

### 端点列表 / Endpoint List

#### 1. <端点名称>

| 属性 | 值 |
|------|-----|
| **方法** | `GET / POST / PUT / DELETE` |
| **路径** | `<如：/api/v1/home>` |
| **说明** | <用途> |
| **认证** | <需要/不需要> |

**请求示例 / Request Example**：
\`\`\`bash
curl -X GET <Base URL><路径> \
  -H "Authorization: Bearer <token>"
\`\`\`

\`\`\`javascript
// Node.js
const https = require('https');
const req = https.request({
  hostname: '<域名>',
  path: '<路径>',
  headers: { 'Authorization': 'Bearer <token>' }
}, res => {
  let data = '';
  res.on('data', chunk => data += chunk);
  res.on('end', () => console.log(data));
});
req.end();
\`\`\`

**响应示例 / Response Example**：
\`\`\`json
{
  "success": true,
  "data": { ... }
}
\`\`\`

---

#### 2. <端点名称>

| 属性 | 值 |
|------|-----|
| **方法** | `POST` |
| **路径** | `<路径>` |
| **说明** | <用途> |

**请求体 / Request Body**：
\`\`\`json
{
  "field1": "value1",
  "field2": "value2"
}
\`\`\`

---

## ⚠️ 注意事项 / Notes

1. <注意事项 1，如：速率限制为每秒 1 次>
2. <注意事项 2，如：必须用 Node.js 调用，curl 会报错>
3. <注意事项 3，如：Token 有效期为 30 天>

---

## 🐛 常见错误 / Common Errors

| 错误码 | 原因 | 解决方案 |
|--------|------|----------|
| 401 | Token 缺失或无效 | 检查 Authorization header |
| 429 | 速率限制 | 等待后重试 |
| 400 | 请求格式错误 | 检查请求体格式 |

---

## 示例 / Example

### InStreet API

- **Base URL**: `https://instreet.coze.site/api/v1`
- **认证**: Bearer Token
- **注意**: 必须用 Node.js HTTPS 模块调用，PowerShell/curl 会失败
```
