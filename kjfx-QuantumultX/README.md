# Quantumult X 新手入门教程
Quantumult X 视频教程：▶ https://youtu.be/X1yna0CxfVo

## <a href="https://github.com/kjfx/QuantumultX/"><img width="40" src="https://raw.githubusercontent.com/kjfx/QuantumultX/main/country/qx.png" /></a>  一、Quantumult X 简介与下载
Quantumult X 简称“圈X”，是一款功能强大的网络工具，本文主要介绍它的代理功能。<br>
Quantumult X 目前支持的协议： SS/SSR、V2Ray、VLESS、Trojan、HTTP(S)<br>
Quantumult X 是一款付费APP，7.99美元，需要用美区等AppleID账号登录 Apple Store 下载。

注册美国AppleID教程：<a href="https://github.com/kjfx/AppleID" target="_blank">https://github.com/kjfx/AppleID</a><br><br>

## 二、Quantumult X 添加节点，订阅链接
#### 1、通过机场订阅链接导入
- Quantumult X 支持SS/SSR订阅链接、支持 Quantumult X 格式的 V2Ray和Trojan订阅链接。
- 机场网站有 Quantumult X 订阅链接的，直接复制订阅链接到 圈X的节点资源 - 资源路径里粘贴，或者点击导入到 Quantumult X 。
- 机场网站无 Quantumult X 订阅链接的，SS/SSR订阅链接可以使用，如果是V2Ray和Trojan订阅链接不能直接导入 Quantumult X ，<br>
需要添加一个 <code>资源解析器</code>，使用 <code>资源解析器</code> 后，可以将 Quantumult X 不识别的 节点或订阅链接 轻松的导入。
<span>
    
- :airplane: 如何添加资源解析器？<br>
打开Quantumult X 配置文件，找到 <code>[general]</code> 位置，添加以下代码：
</span>

    resource_parser_url=https://raw.githubusercontent.com/KOP-XIAO/QuantumultX/master/Scripts/resource-parser.js
备用：

    resource_parser_url=https://fastly.jsdelivr.net/gh/KOP-XIAO/QuantumultX@master/Scripts/resource-parser.js

#### 2、通过 URL 和 扫码 添加节点
Quantumult X 支持SS/SSR节点链接和扫码添加、支持 Quantumult X 格式的 V2Ray和Trojan节点链接和扫码添加，大部分机场的V2Ray和Trojan节点链接不能直接通过扫码添加。

#### 3、手动添加节点
<span>
    
- vmess节点格式（添加V2RAY节点）
</span>

    vmess=example.com:443, method=chacha20-poly1305, password=pwd, obfs=wss, obfs-host=example.com, obfs-uri=/ws, tls13=true, fast-open=false, udp-relay=false, tag=节点名称

<span>
    
- Trojan节点格式（添加Trojan节点）
</span>

    trojan=example.com:443, password=pwd, over-tls=true, tls-host=example.com, tls-verification=true, tls13=true, fast-open=false, udp-relay=false, tag=节点名称


#### 4、订阅链接转换
- 地址1（将节点链接转成订阅链接）：https://acl4ssr-sub.github.io/  (后端地址: 选择第二个)
- 地址2（将vmess节点链接转成订阅链接）：https://bianyuan.xyz/


## <h2><a href="https://github.com/kjfx/QuantumultX/"><img width="40" src="https://raw.githubusercontent.com/kjfx/QuantumultX/main/country/qx.png" /></a>  第二部分：Quantumult X 策略组和分流规则，添加使用教程</h2>
Quantumult X 视频教程：▶ https://youtu.be/XnLCigKhE9E
<h3>分流规则</h3>

#### 1、分流规则是什么？
- 分流规则可以实现不同的网站走不同的节点，自动让网站或APP走指定的节点或策略组，不需要人工操作。

#### 2、Quantumult X 分流规则类型
- **HOST**           / 域名匹配  / 例如：www.google.com
- **HOST-SUFFIX**    / 域名后缀匹配  / 例如：google.com  
- **HOST-KEYWORD**   / 域名关键字匹配  / 例如：google  
- **USER-AGENT**     / 用户代理匹配  / 例如：*abc?
- **IP-CIDR**        / IP匹配       / 例如：192.168.0.1/24
- **IP6-CIDR**       / IPV6
- **GEOIP**          / IP数据库匹配  / 例如：US

#### 3、添加分流规则
- 打开Quantumult X 配置文件，找到 <code>[filter_remote]</code> 和 <code>[filter_local]</code> 位置可以添加<br>
点击 <code>分流规则</code> 按钮也可以添加和引用分流规则。
<span>
    
- 分流规则（引用）示例：
</span>

    https://raw.githubusercontent.com/kjfx/QuantumultX/main/country/filter.list


<br>
<h3>策略组</h3>

#### 1、策略组是什么？
- 策略组可以实现 自动切换节点、节点筛选、是否走代理等。
- 策略组 需要配合 分流规则 使用。
- 策略组 可包含多个节点和策略组。

#### 2、Quantumult X 自带 3 种策略。

- PROXY（代理）
- DIRECT（直连）
- REJECT（拒绝）

#### 3、Quantumult X 策略组类型
- static 静态策略-手动选择节点
- available 健康检查-自动选择节点，从第一个节点开始检查是否可用，直到选择可用节点。
- round-robin 负载均衡-轮询调度，轮流调用节点使用，IP可能会一直变。
- dest-hash 随机负载均衡，但相同域名走固定节点。
- url-latency-benchmark 自动测速-自动选择延迟低的节点

#### 4、添加策略组 （重点）
- 打开Quantumult X 配置文件，找到 <code>[policy]</code> 位置
<span>
    
- 默认策略
</span>

    static=default, proxy, direct, reject
    
<span>
    
- 筛选节点的策略组
</span>

    static=节点选择, 国际网络（自动选择节点）, proxy, direct, img-url=paperplane.fill.system
    static=HK 香港, server-tag-regex=香港|🇭🇰|HK, img-url=globe.system
    static=TW 台湾, server-tag-regex=台湾|🇹🇼|TW, img-url=globe.system
    static=US 美国, server-tag-regex=美国|🇺🇸|US, img-url=globe.system
    static=JP 日本, server-tag-regex=日本|🇯🇵|JP, img-url=globe.system
    static=KR 韩国, server-tag-regex=韩国|🇰🇷|KR, img-url=globe.system
    static=SG 新加坡, server-tag-regex=新加坡|🇸🇬|SG|狮城, img-url=globe.system
    url-latency-benchmark=国际网络（自动选择节点）, server-tag-regex=.*, check-interval=600, tolerance=0, img-url=globe.system
    static=Netflix, server-tag-regex=.*, img-url=play.circle.fill.system

- 需匹配的节点标签 - 正则<br>
美国|US ：节点名称中包含 美国或US 会被选中。<br>
IPLC.*香港：节点名称中需同时包含 IPLC和香港 会被选中。

#### 5、Quantumult X 懒人配置
- 分享几位大佬提供的配置规则<br>
<span>
    
    https://raw.githubusercontent.com/Orz-3/QuantumultX/master/Orz-3.conf
</span>

<span>
    
    https://raw.githubusercontent.com/w37fhy/QuantumultX/master/QuantumultX_diy.conf
</span>

    https://raw.githubusercontent.com/As-Lucky/Lucky/main/Lucky-qx.conf
    
## <h2><a href="https://github.com/kjfx/QuantumultX/"><img width="40" src="https://raw.githubusercontent.com/kjfx/QuantumultX/main/country/qx.png" /></a>  第三部分：Quantumult X 去广告规则和京东签到</h2>
Quantumult X 去广告和京东签到视频教程：▶ https://youtu.be/b3Gw-2QGciQ

<h3>Quantumult X 去广告</h3>

- Quantumult X 支持 youtube 去广告以及一些常用的网站和APP去广告。
- 分享几位大佬提供的配置规则。
- 第一步：在圈X配置文件里找到 <code>[filter_remote]</code> 添加<br>
<span>
    
    http://limbopro.xyz/Adblock4limbo.list, tag=毒奶特供, force-policy=reject, enabled=true
    https://raw.githubusercontent.com/w37fhy/QuantumultX/master/Rules/Advertising.list, tag=🛑轻量广告拦截, force-policy=reject, update-interval=172800, opt-parser=true, enabled=true
    https://raw.githubusercontent.com/NobyDa/Script/master/QuantumultX/AdRule.list, tag=🛑重度广告拦截, force-policy=reject, update-interval=172800, opt-parser=false, enabled=false
</span>

- 第二步：在圈X配置文件里找到 <code>[rewrite_remote]</code> 添加<br>
<span>
    
    http://limbopro.xyz/Adblock4limbo.conf, tag=毒奶特供, enabled=true
    https://raw.githubusercontent.com/NobyDa/Script/master/QuantumultX/Rewrite_lhie1.conf, tag=NoByDa（lhie1 Rewrite）, enabled=true
    https://raw.githubusercontent.com/NobyDa/Script/master/QuantumultX/Js.conf, tag=NoByDa（NoByDa Rewrite）, enabled=true
    https://raw.githubusercontent.com/ConnersHua/RuleGo/master/Surge/Module/Block/YouTubeAds.sgmodule, tag=油管去广告, update-interval=172800, opt-parser=true, enabled=true
    https://raw.githubusercontent.com/Orz-3/QuantumultX/master/YouTube.conf, tag=油管去广告, update-interval=86400, opt-parser=true, enabled=true
</span>

- 第三步：开启 <code>重写</code> 和 <code>MitM</code> 并生成证书、配置证书。<br>

<h3>Quantumult X 京东签到</h3>

- 分享野比大佬提供的配置规则。
<span>
    
    https://raw.githubusercontent.com/NobyDa/Script/master/JD-DailyBonus/JD_DailyBonus.js
</span>


<br>
<h2>常见问题：</h2>

#### 1、关于 Quantumult X 网页响应测试，测试延迟后的两个数值<br>
- 第一项为节点 TCP 握手，第二项为通过对应节点访问测试网页获得 HTTP 响应所需要的时间，来确认节点的可用性。

<h2>免责声明：</h2>

- 以上分享的内容中涉及的任何解锁和解密分析脚本仅供资源共享和学习研究，不能保证合法性、准确性、完整性和有效性，请根据实际情况自行判断。
- 以上分享的内容来源网络，请大家自行判断使用，包括但不限于由任何内容错误导致的任何损失或损害, 不承担任何责任。
- 您必须在下载后24小时内从您的计算机或手机中彻底删除以上所分享的全部内容。
- 如果任何单位或个人认为以上分享的内容可能涉嫌侵犯其权利，则应及时通知并提供身份证明，所有权证明，我们将在收到认证文件后删除相关脚本。
- 使用者都应仔细阅读此声明，保留随时更改或补充此免责声明的权利。您一旦使用并复制了本项目分享的任何内容，则视为您已接受此免责声明。

<h2>特别感谢（排名不分先后）：</h2>

- <a href="https://github.com/Orz-3/QuantumultX" target="_blank">@Orz-3</a><br>
- <a href="https://github.com/w37fhy" target="_blank">@w37fhy</a><br>
- <a href="https://github.com/NobyDa/Script/blob/master/JD-DailyBonus/JD_DailyBonus.js" target="_blank">@NobyDa</a><br>
- <a href="https://github.com/limbopro/Adblock4limbo" target="_blank">@limbopro</a><br>
- <a href="https://github.com/DivineEngine/Profiles/tree/master" target="_blank">@DivineEngine </a>

