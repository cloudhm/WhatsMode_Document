### App Web Browse Configuration

| Window Property | iOS  | Android |
|---|---|---|
|User-Agent|WhatsMode-iOS|WhatsMode-Android|

### JS call Native

| Event Name | Parameters | Remarks | 
|---|---|---|
| share | `title, img_url, description, share_url` | 分享 |
| pay | `order_id` | 支付|
| add_cartItem | `variant_id, quantity` | 加购 |
| buy_now | `variant_id, quantity` | 立即购买 |
| login | | 登录/注册|
| openURL | <pre>商品详情URL规则 {scheme}://{host}/.../product/{product_id}?uid={user_id}&i={influencer_id}&...{other_parameters}<br/>订单详情解析URL规则 {scheme}://{host}/.../order/detail/{order_id}<br/>活动商品列表URL规则 {scheme}://{host}/.../collection/list?collectionId={collection_id}</pre> |<pre>商品详情<br/>订单详情<br/>活动商品列表</pre>|

### Native call JS
`eval("callByApp({"event_name":${event_name}, ${other_parameters}})")`

| Event Name | Parameters |
|---|---|
|login_success|token, source|


### Native Embed Website
| Website | Remarks |
|---|---|
|{scheme}://{host}/.../message|消息列表|

<h5>需要手动嵌入Cookie进webview</h5>
<pre>
Set-Cookie: token=${token}; Domain=.socialeras.com; Path=/; language=${language}; currencyCode=${currencyCode}; countryCode=${countryCode}; clinetId=${UUID_String};
</pre>