---

layout : post

category : manage

tags : [selenium]

title : selenium核心代码

---

//设置浏览器driver

WebDriver driver; driver = new FirdfoxDriver(); driver.get(http://www.baidu.com);

//找到输入框，输入"selenium测试"并点击百度

driver.FindElement(By.id("kw"))clear(); driver.FindElement(By.id("kw")).sendkeys("selenium测试"); 
driver.FindElement(By.id("su"))clear(); //关闭浏览器 driver.close();

然后点击运行，即可在百度首页上看到输入框输入“selenium测试”的模拟效果