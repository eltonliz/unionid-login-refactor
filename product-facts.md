# 微信账号身份事实基线

> 核对日期：2026-09-23。本文件只保留影响产品决策的官方事实，不记录任何密钥或实现凭据。

## 已核对事实

1. 同一微信用户只有在多个应用绑定于同一微信开放平台账号时，才能通过 UnionID 在多个 AppID 之间识别。
2. 已绑定开放平台账号的小程序，可通过 `wx.login` + 服务端 `code2Session` 获取 UnionID，不需要用户先授权手机号。
3. OpenID 是用户在特定 AppID 下的标识；APP 与小程序跨 AppID 不能直接比较裸 OpenID。
4. 小程序手机号能力必须经用户同意，回调中的手机号 `code` 由后端换取手机号。
5. 手机号 `code` 与 `wx.login` 的登录 `code` 作用不同，不能混用；获取手机号不等于建立微信登录身份。
6. 手机号快速验证组件提供经平台验证的号码，但官方说明不保证每次实时验证；高风险账号处理需根据业务增加其他校验。
7. 官方提醒开发者合理使用手机号能力；不合理地要求用户提供手机号、中断正常使用流程，可能影响体验并触发平台处理。

## 官方来源

- UnionID 机制说明：https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/union-id.html
- 小程序登录：https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/login.html
- 手机号快速验证组件：https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/getPhoneNumber.html
- 移动应用微信登录：https://developers.weixin.qq.com/doc/oplatform/Mobile_App/WeChat_Login/Development_Guide.html
