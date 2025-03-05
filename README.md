# 亚马逊 CAPTCHA 解决方案

[![宣传图](https://github.com/bright-cn/LinkedIn-Scraper/raw/main/Proxies%20and%20scrapers%20GitHub%20bonus%20banner.png)](https://www.bright.cn/products/web-unlocker/captcha-solver/amazon)

借助 Bright Data 先进的 CAPTCHA 解决技术，轻松绕过亚马逊的验证码。通过机器学习算法、[自动化 IP 轮换](https://www.bright.cn/solutions/rotating-proxies)和强大的代理基础设施，确保对目标站点的顺畅且持续的访问。

Bright Data 的 CAPTCHA Solver 是 [**抓取浏览器**](https://www.bright.cn/products/scraping-browser) 和 [**网络解锁器 API**](https://www.bright.cn/products/web-unlocker) 的内置功能，为处理最复杂的验证码挑战提供完整解决方案。

## 功能
- **快速解决验证码**：以高准确率和速度自动解决亚马逊验证码。  
- **IP 轮换**：通过自动重试和动态 IP 调整来避免封禁。  
- **浏览器指纹**：模拟真实用户活动来[绕过复杂的机器人检测](https://www.bright.cn/blog/web-data/anti-scraping-techniques)。  
- **JavaScript 渲染**：可应对大量使用 JavaScript 的动态网站内容。  
- **全球地理覆盖**：精准定位，解除任何区域的内容限制。  
- **无缝集成**：与 Puppeteer、Playwright 和 Selenium 等工具完美结合。  
- **事件监控**：跟踪验证码识别、成功或失败等事件。

## 为什么选择亚马逊 CAPTCHA 解决方案

### **全球 20,000+ 客户的信赖**
Bright Data 的 CAPTCHA Solver 在开发者、企业以及大型公司中以其卓越的可靠性和性能而备受信赖。

### **强大的高级代理网络支持**
拥有超过 1 亿个 IP 并具备高级地理定位功能，我们的代理基础设施能够顺畅且不中断地解决验证码。

### **AI 驱动的验证码解决**
我们的 CAPTCHA Solver 利用先进的 AI 逻辑来自动识别、分析并解决验证码。它还可处理重试、指纹识别和请求头等，以绕过最复杂的反机器人措施。

### **专为开发者打造**
- 轻松与 Puppeteer、Playwright、Selenium 集成。  
- 可完全自定义验证码解决策略。  
- 自动重试和动态 IP 调整以保证采集过程不中断。

> **小贴士 💡**  
>> 已经有验证码解决方案？结合我们为 [Puppeteer](https://www.bright.cn/integration/puppeteer)、[Playwright](https://www.bright.cn/integration/playwright) 和 [Selenium](https://www.bright.cn/integration/selenium) 提供的代理服务，减少验证码的出现率。

## 工作原理

Bright Data 的 CAPTCHA Solver 集成在 **Scraping Browser** 和 **Web Unlocker** 中，让解决验证码变得轻而易举。

### **自动化验证码解决**
CAPTCHA Solver 会自动实时检测并解决验证码。只需启用此功能，即可从验证码检测到最终解决全程自动处理。

### **针对亚马逊验证码的自定义选项**
```javascript
// 为不同的验证码类型定义默认选项
function getCaptchaOptions(captchaType, customOptions = {}) {
  const defaultOptions = {
    timeout: 30000, // 最长等待验证码解决的时间（毫秒）
    check_timeout: 500, // 间隔（毫秒），用于检查验证码的状态
    wait_networkidle: { timeout: 1000 }, // 网络空闲等待 1 秒
    debug: false // 调试模式（默认关闭）
  };

  // 定义不同验证码类型的选择器
  const captchaSelectors = {
    DataDome: { selector: '#datadome-captcha', success_selector: '#captcha-success' },
    reCAPTCHA: { selector: '.g-recaptcha', success_selector: '.recaptcha-success' },
    ClickCaptcha: { selector: '.click-captcha', success_selector: '.captcha-passed' },
    hCaptcha: { selector: '.h-captcha', success_selector: '.hcaptcha-success' },
    PerimeterX: { selector: '#px-captcha', success_selector: '#px-success' },
    SimpleCaptcha: { selector: '.simple-captcha', success_selector: '.captcha-done' },
    FunCaptcha: { selector: '.funcaptcha', success_selector: '.funcaptcha-success' },
    CloudflareTurnstile: { selector: '.cf-turnstile', success_selector: '.cf-success' },
    AWSWAF: { selector: '#aws-waf-captcha', success_selector: '#aws-waf-success' },
    GeeTest: { selector: '.geetest-captcha', success_selector: '.geetest-success' },
    KeyCAPTCHA: { selector: '#keycaptcha', success_selector: '#keycaptcha-success' },
    PuzzleCAPTCHA: { selector: '.puzzle-captcha', success_selector: '.puzzle-solved' },
    YandexCAPTCHA: { selector: '#yandex-captcha', success_selector: '#yandex-success' },
    ImageCAPTCHA: { selector: '.image-captcha', success_selector: '.image-captcha-success' },
    TextCAPTCHA: { selector: '.text-captcha', success_selector: '.text-captcha-success' }
  };

  // 获取对应验证码类型的选择器
  const selectedOptions = captchaSelectors[captchaType] || {};

  // 合并默认选项、验证码特定选项和用户自定义配置
  return { ...defaultOptions, ...selectedOptions, ...customOptions };
}

// 针对不同验证码类型的示例用法
const ddOptions = getCaptchaOptions('DataDome', { timeout: 40000, debug: true });
const recaptchaOptions = getCaptchaOptions('reCAPTCHA', { debug: true });
const hcaptchaOptions = getCaptchaOptions('hCaptcha');

console.log(ddOptions);
console.log(recaptchaOptions);
console.log(hcaptchaOptions);

// 错误处理示例
try {
  if (!document.querySelector(ddOptions.selector)) {
    throw new Error(`无法使用选择器找到验证码元素: ${ddOptions.selector}`);
  }

  // 在此处实现你的验证码解决逻辑
  solveCaptcha(ddOptions);
} catch (error) {
  console.error('解决验证码失败:', error.message);
}
```

#### 示例工作流程：
1. **检测验证码**：系统检测验证码类型（例如 PerimeterX）。  
2. **解决验证码**：使用 AI 逻辑自动完成验证码解决。  
3. **失败重试**：如果解决失败，系统会自动使用新 IP 重试。  
4. **返回结果**：一旦成功解决，即可无缝访问目标站点。

## 支持的验证码类型

Bright Data 的 CAPTCHA Solver 支持多种验证码类型，包括：

- [**DataDome**](https://www.bright.cn/products/web-unlocker/captcha-solver/datadome)  
- [**reCAPTCHA**](https://www.bright.cn/products/web-unlocker/captcha-solver/recaptcha)  
- [**Click Captcha**](https://www.bright.cn/products/web-unlocker/captcha-solver/click-captcha)  
- [**Cloudflare**](https://www.bright.cn/products/web-unlocker/captcha-solver/Cloudflare)  
- [**PerimeterX**](https://www.bright.cn/products/web-unlocker/captcha-solver/perimeterx)  
- [**SimpleCaptcha**](https://www.bright.cn/products/web-unlocker/captcha-solver/simplecaptcha)  
- [**FunCaptcha**](https://www.bright.cn/products/web-unlocker/captcha-solver/funcaptcha)  
- [**Cloudflare Turnstile**](https://www.bright.cn/products/web-unlocker/captcha-solver/cloudflare-turnstile)  
- [**AWS WAF Captcha**](https://www.bright.cn/products/web-unlocker/captcha-solver/aws-waf-captcha)  
- [**GeeTest CAPTCHA**](https://www.bright.cn/products/web-unlocker/captcha-solver/geetest-captcha)  
- [**KeyCAPTCHA**](https://www.bright.cn/products/web-unlocker/captcha-solver/keycaptcha)  
- [**Puzzle CAPTCHA**](https://www.bright.cn/products/web-unlocker/captcha-solver/puzzle-captcha)  
- [**Yandex CAPTCHA**](https://www.bright.cn/products/web-unlocker/captcha-solver/yandex-captcha)  
- [**Image CAPTCHA**](https://www.bright.cn/products/web-unlocker/captcha-solver/image-captcha)  
- [**Text CAPTCHA**](https://www.bright.cn/products/web-unlocker/captcha-solver/text-captcha)

## 高级自定义

[Bright Data 的 CAPTCHA Solver](https://github.com/bright-cn/Captcha-solver) 支持高级自定义，可用于为特定场景微调解决逻辑。

## **事件监控**
跟踪验证码解决的事件，用于处理更高级的需求：  
- `Captcha.detected`：已检测到验证码并开始解决。  
- `Captcha.solveFinished`：验证码已成功解决。  
- `Captcha.solveFailed`：验证码解决失败。

## **价格**

| **套餐**               | **价格（每1K 结果）** | **月度成本**    | **说明**                            |  
|------------------------|-----------------------|----------------|-------------------------------------|  
| **按量付费 (Pay-as-you-go)** | $1.50                | 无需承诺         | 适合临时或小规模的抓取需求。          |  
| **Growth**             | $1.27                | $499           | 面向成长型团队的优化方案。           |  
| **Business**           | $1.12                | $999           | 适用于大规模数据采集需求。           |  
| **Premium**            | $1.05                | $1,999         | 提供高级功能和优先支持。             |  
| **Enterprise**         | 定制报价             | 联系我们        | 为大型企业定制的顶级服务包。         |  

🚀 **特别优惠**：首次充值最高可享受与相同金额的匹配奖励，最高可达 **$500**！

## **开发者为何青睐亚马逊 CAPTCHA 解决方案**
- **易于集成**：可无缝对接 Puppeteer、Playwright、Selenium 等常用工具。  
- **先进的 AI 逻辑**：自动处理重试、验证码解决、指纹识别、IP 轮换以及高级请求头等。  
- **内置浏览器**：无需额外管理外部浏览器即可完成 JavaScript 渲染。  
- **实时监控**：在可视化面板上查看网络性能的实时数据。  
- **卓越支持**：24/7 全天候全球客服，并不断推出新功能。

## **常见问题**

### **亚马逊 CAPTCHA Solver 的工作原理是什么？**  
此解决方案利用高级 AI 逻辑自动检测并解决亚马逊验证码。

### **它可以同时解决多个验证码吗？**  
可以，该方案支持同时处理多种验证码类型，确保访问不中断。

### **如果验证码解决失败怎么办？**  
系统会自动进行重试。如仍有问题，可随时联系我们 24/7 的客服团队进行排查。

---

## **告别亚马逊验证码**
立即开始免费试用，体验 Bright Data 无缝的 [亚马逊验证码解决方案](https://www.bright.cn/products/web-unlocker/captcha-solver/amazon)！  
