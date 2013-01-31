---

layout : post

category : manage

tags : [安全技巧 WordPress平板文件]

title : 十个实用的WordPress安全技巧

---


#十个实用的WordPress安全技巧

    8. 删除你的 WordPress版本号 
        问题 大家都知道，WordPress会自动在你的博客文件的头部显示版本号。如果你的博客一直都是最新版的话问题不大。但是如果由于某些原因你的WordPress版本并没有更新，却仍然显示出来的话，就会被黑客利用。 解决方法 在主题的functions.php文件里粘贴下面的代码，保存，然后刷新你的博客，这样你的WordPress版本号就不会出现了。 remove_action(‘wp_head’, ‘wp_generator’); 代码解释 要执行某个行动时， WordPress是用“hook”机制，也就是说可以让你将一个函数hook到 另一个函数里。显示WordPress版本号的 wp_generator函数被hook了。我们可以移除这 个 hook并通过使用 remove_action() 函数来阻止其执行。 
    9.更改默认的用户名“Admin” 
        问题 如果你使用的是默认的“admin”用户名，黑客只需要攻破你的密码即可入侵你的一切。这无疑 让黑客更容易得手，所以我们一直强调你应该更改默认的用户名 “admin” ，用个别人比较难猜 得出来的用户名。 不过还好WordPress 3.0安装时可以让你选择自己喜欢的用户名。 如果你还在使用旧版本并 且你的用户名还没有更改过，那么现在该动手了。 解决方法 如果你还没有更改“admin”用户名，只要在数据库中运行下面的SQL查询就可以更改。 UPDATE wp_users SET user_login = ‘你的新用户名’ WHERE user_login = ‘Admin’; 代码解释 用户名是保存在数据库中的。想要更改的话，只要一个简单的查询更新即可。注意：这个查询并 不会将你先前用“admin”账户发布的文章的用户名变成新的用户名 
    10.阻止浏览目录 
        问题 默认情况下，大多数主机允许显示目录列表。因此，如果你在浏览器地址栏输入 www.yourblog.com/wp-includes，你就看到所有在该目录下的文件，这无疑是一个很大的安 全隐患。 解决方法 只需在Apache配置里添加: Option -Indexes  
    1. 阻止透露不必要的信息 
        问题 当登录WordPress博客失败的时候，系统会显示错误提示信息。如果你忘记密码了，这个提示会对你有所帮助，可是这却也让那些想要攻击你博客的人有机可乘。因此，为何不阻止WordPress显示这个登录失败时的错误提示呢？ 解决办法 想要删除登录错误提示信息，只要打开你的functions.php文件，并粘贴下面的代码： add_filter(‘login_errors’,create_function(‘$a’, “return null;”));保存此文件，再次检查下你就会发现登录失败时就没有错误信息提示了。 代码解释 这段代码里，我们添加了一个简单的hook来覆盖login_errors()函数。由于创建的自定义函数返回null，因此就只会显示一个空白的字串。 代码解释
这段代码里，我们添加了一个简单的hook来覆盖login_errors()函数。由于创建的自定义函数返回null，因此就只会显示一个空白的字串。

    2. 强制使用SSL 
        问题 如果你担心数据被拦截，你完全可以使用SSL。SSL是什么？它是基于WEB应用的安全加密协议。你是否知道也可以给WordPress博客添加SSL加密？但是也并非是所有的主机都允许你使用SSL加密证书，如果你的博客是由IXWebhosting或美国主机Hostease托管的，那么就可以启用SSL，而且这两个主机都有中文站。 解决办法 一旦确定你的web服务器可以处理SSL，那问题就简单了，只要打开你的配置文件wp-config.php (在安装WordPress的根目录下)，然后粘贴下面的代码: define(‘FORCE_SSL_ADMIN’, true);保存文件即可。 代码解释 这个代码比较简单。 WordPress使用了很多常量来配置，在这里我们只是定义了FORCE_SSL_ADMIN 常量并将它的值设置为 true。这样一来，你的WordPress博客就实现SSL加密了。 
    3. 使用 .htaccess来保护配置文件wp-config 
        问题 作为一名 WordPress用户，你应该知道配置文件wp-config.php的重要性。 此文件包含了所有可访问数据库的信息:用户名、密码、服务器名称等。 保护 wp-config.php 配置文件是如此的关键，那么如何利用Apache来解决这个问题呢？ 解决办法 .htaccess文件位于WordPress安装目录下，首先要对它做个备份(如此重要的文件，任何改动之前一定要先备份)，打开它然后粘贴下面的代码： <files wp-config.php> order allow,deny deny from all </files>代码解释 .htaccess 文件非常强大，也是防止他人访问你的文件的最佳工具。这段代码里，我们只是创建了一个规则来阻止任何人访问 wp-admin.php文件，防止bots攻击。 
    4. 将不受欢迎用户和Bots列入黑名单 
        问题 这个是比较现实的问题:今天被某个人骚扰，他可能下一次还会继续骚扰你。你是否有注意到每天同个人/垃圾留言机器光顾你的博客无数次留下无数恼人的评论。处理这个问题的方法非常简单：直接禁止他们访问你的博客。 解决方法 在 .htaccess文件粘贴下面的代码，再次说明在修改之前，切记备份.htaccess文件。并记得将123.456.789 该成你想要禁止的IP地址。 <Limit GET POST PUT> order allow,deny allow from all deny from 123.456.789 </LIMIT>5. 防止WordPress博客的脚步侵入 问题 保护动态完全特别重要。大多数开发人员都只保护GET和POST的请求，但有时候这样并不够。我们应该注意防止脚步侵入以及任何试图修改PHP GLOBALS和 _REQUEST变量。 解决方法 下面的代码可以阻止脚步入侵以及任何试图修改PHP GLOBALS 和_REQUEST变量。将代码粘贴到你的 .htaccess文件 (WordPress安装目录下)。 Options +FollowSymLinks RewriteEngine On RewriteCond %{QUERY_STRING} (\<|%3C).*script.*(\>|%3E) [NC,OR] RewriteCond %{QUERY_STRING} GLOBALS(=|\[|\%[0-9A-Z]{0,2}) [OR] RewriteCond %{QUERY_STRING} _REQUEST(=|\[|\%[0-9A-Z]{0,2}) RewriteRule ^(.*)$ index.php [F,L] 代码解释 利用.htaccess文件，我们可以检查请求。在这里，我们检查该请求是否包含一个 <script> ， 它是否有试图修改PHP GLOBALS或_REQUEST的变量值。如果符合任何一个条件， 该请求就会被阻止，返回403错误到客户端浏览器。 
    6. 回击内容剽窃者 
        问题 如果你的博客有点知名度，很有可能就会有一些人在未经你的同意下直接使用你的内容。除了侵犯你的版权之外，由于盗用你的图片，对你服务器带宽也是一个很大的损耗。 解决办法 在 .htaccess文件里粘贴下面的代码： RewriteEngine On #Replace ?mysite\.com/ with your blog url RewriteCond %{HTTP_REFERER} !^http://(.+\.)?mysite\.com/ [NC] RewriteCond %{HTTP_REFERER} !^$ #Replace /images/nohotlink.jpg with your “don’t hotlink” image url RewriteRule .*\.(jpe?g|gif|bmp|png)$ /images/nohotlink.jpg [L] 保存之后， 只有你的网站网站才能链接到你的图片，而其它盗链网站就无法显示你的图片。 代码解释 在这段代码里，首先检查引荐人是否与自己博客的URL地址一致。如果不一致，那么以下扩展名 的文件，JPG, GIF, BMP或 PNG就不会显示而用 nohotlink图片代替。 
    7. 创建一个插件来阻止恶意URL的请求 
        问题 黑客通常通过恶意查询来找出并攻击一个博客的薄弱点。 解决办法 将下面的代码粘贴在一个文本文件里并命名为blockbadqueries.php。保存此文件并将它 上传到 wp-content/plugins 目录，然后像其他插件一样激活它。这样你的博客就不会 遭受恶意的查询。 <?php /* Plugin Name: Block Bad Queries Plugin URI: http://perishablepress.com/press/2009/12/22/protect-wor dpress-against-malicious-url-requests/ Description: Protect WordPress Against Malicious URL Requests Author URI: http://perishablepress.com/ Author: Perishable Press Version: 1.0 */  global $user_ID;  if($user_ID) {   if(!current_user_can(‘level_10′)) {     if (strlen($_SERVER['REQUEST_URI']) > 255 ||       strpos($_SERVER['REQUEST_URI'], “eval(“) ||       strpos($_SERVER['REQUEST_URI'], “CONCAT”) ||       strpos($_SERVER['REQUEST_URI'], “UNION+SELECT”) ||       strpos($_SERVER['REQUEST_URI'], “base64″)) {         @header(“HTTP/1.1 414 Request-URI Too Long”);     @header(“Status: 414 Request-URI Too Long”);     @header(“Connection: Close”);     @exit;     }   } } ?> 代码解释 这段代码非常简单，它检查特别长的请求字符串(超过255个字符) 以及URL中是否 存在eval或 base64 PHP 函数。如果符合其中的任何一个条件，该插件就会想客户端浏览器 发送414错误。  
