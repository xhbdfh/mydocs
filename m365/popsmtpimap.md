## 需要使用到POP 或 IMAP SMTP 的客户

参考文档
https://techcommunity.microsoft.com/blog/exchange/new-opt-in-endpoint-for-pop3imap4-clients-that-need-legacy-tls/3710395

Exchange Online ended support for TLS1.0 and TLS1.1 in October 2020. This year, we plan to disable these older TLS versions for POP3/IMAP4 clients to secure our customers and meet compliance requirements. However, we know that there is still significant usage of POP3/IMAP4 clients that don’t support TLS 1.2, so we’ve created an opt-in endpoint for these clients so they can use TLS1.0 and TLS1.1. This way, an organization is secured with TLS1.2 unless they specifically decide to opt for a less secure posture.
Exchange Online 已于 2020 年 10 月终止了对 TLS 1.0 和 TLS 1.1 的支持。今年，我们计划为 POP3/IMAP4 客户端禁用这些旧版 TLS，以保障客户安全并满足合规性要求。然而，我们了解到仍有大量使用不支持 TLS 1.2 的 POP3/IMAP4 客户端，因此我们为这些客户端创建了一个可选端点，以便它们可以使用 TLS 1.0 和 TLS 1.1。这样，除非组织明确选择安全性较低的安全措施，否则他们仍可使用 TLS 1.2 进行安全保护。

Only WW tenants can use this new endpoint. Tenants in US government clouds have higher security standards and cannot use older versions of TLS.
只有 WW 租户可以使用这个新端点。美国政府云中的租户具有更高的安全标准，无法使用旧版本的 TLS。

To take advantage of this new endpoint, admins will have to:
要利用这个新端点，管理员必须：

Use Set-TransportConfig to set the AllowLegacyTLSClients parameter to True.
使用 Set-TransportConfig 将 AllowLegacyTLSClients 参数设置为 True。
Configure legacy POP3/IMAP4 clients and devices to use pop-legacy.office365.com / imap-legacy.office365.com as the new endpoint. Customers who use Microsoft 365 operated by 21 Vianet need to configure their clients to use pop-legacy.partner.outlook.cn / imap-legacy.partner.outlook.cn.
将旧版 POP3/IMAP4 客户端和设备配置为使用 pop-legacy.office365.com / imap-legacy.office365.com 作为新终结点。使用由世纪互联运营的 Microsoft 365 的客户需要将其客户端配置为使用 pop-legacy.partner.outlook.cn / imap-legacy.partner.outlook.cn 。
Starting in February 2023, we will reject a small percentage of connections that use TLS1.0 for POP3/IMAP4. Clients should retry as they do with any other temporary error that can occur when connecting. Over time we will increase the percentage of rejected connections, causing delays in connecting that should be more and more noticeable. The error will be:
自 2023 年 2 月起，我们将拒绝一小部分使用 TLS 1.0 协议进行 POP3/IMAP4 的连接。客户端应像处理连接过程中可能出现的任何其他临时错误一样进行重试。随着时间的推移，我们会增加被拒绝连接的百分比，从而导致连接延迟，并且延迟应该会越来越明显。错误信息如下：

TLS 1.0 and 1.1 are not supported. Please upgrade/update your client to support TLS 1.2. Visit https://aka.ms/popimap_tls.
TLS 1.0 和 1.1 不受支持。请升级/更新您的客户端以支持 TLS 1.2。请访问 https://aka.ms/popimap_tls 。

We intend to fully disable TLS 1.0 and TLS 1.1 for POP3/IMAP4 on the regular endpoint by the end of April 2023.  Affected customers will receive a Message Center post in a few days notifying them of this change.
我们计划在 2023 年 4 月底之前在常规端点上完全禁用 POP3/IMAP4 的 TLS 1.0 和 TLS 1.1。受影响的客户将在几天内收到消息中心帖子，通知他们此更改。

Additional documentation can be found here: Opt in to the Exchange Online endpoint for legacy TLS clients using POP3 or IMAP4.
其他文档可在此处找到： 使用 POP3 或 IMAP4 选择加入旧版 TLS 客户端的 Exchange Online 端点。

Exchange Team  交流团队

Updated Jan 06, 2023
更新于 2023 年 1 月 6 日
