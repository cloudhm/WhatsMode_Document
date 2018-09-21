### App Web Browse Configuration

| Window Property | iOS  | Android |
|---|---|---|
|User-Agent|WhatsMode-iOS|WhatsMode-Android|
* 注意UA需要拼接，并不是简单设置。
`format: ${Origin UserAgent} ${New UserAgent}/${App Version}`
`eg: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_13_6) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/11.1.2 Safari/605.1.15 WhatsMode-iOS/1.0.0`

### JS call Native

| Event Name | Parameters | Remarks | 
|---|---|---|
| share | `title, img_url, description, share_url, product_id` | 分享 |
| pay | `order_id` | 支付|
| add_cartItem | `variant_id, quantity` | 加购 |
| buy_now | `variant_id, quantity` | 立即购买 |
| login | | 登录/注册|
| openURL | <pre>商品详情URL规则 {scheme}://{host}/.../product/{product_id}?uid={user_id}&i={influencer_id}&...{other_parameters}<br/>订单详情解析URL规则 {scheme}://{host}/.../order/detail/{order_id}<br/>活动商品列表URL规则 {scheme}://{host}/.../collection?collectionId={collection_id}</pre> |<pre>商品详情<br/>订单详情<br/>活动商品列表</pre>|

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

### 路由
`{scheme}://{host}/{path...}?{query}`

| 页面 | 基本规则 | |
|---|---|---|
|商品详情|<pre>path: /product/{product_id}<br/>query: 其他参数，i:网红id，uid:分享人id，等等</pre>||
|商品列表-活动|<pre>path: /collection<br/>query: colletionId 活动id</pre>||
|商品列表-搜索|<pre>path: /product<br/>query: q={search_key}</pre>||
|商品列表-标签|<pre>path: /product<br/>query: fq=work_tags:{tag}</pre>||
|商品列表-网红|<pre>path: /product<br/>query: fq=userId_ls:{influencerId}</pre>||
|商品列表-分类|<pre>path: /product<br/>query: fq=categoryId_l:{categoryId}</pre>|多分类<pre>eg:<br/>fq=categoryId_l:{categoryId_1},categoryId_l:{categoryId_2}</pre>|
|商品列表-自定义分类|<pre>path: /product<br/>query: categoriesId={id}</pre>||
|订单详情|<pre>path: /order/detail/{order_id}</pre>||