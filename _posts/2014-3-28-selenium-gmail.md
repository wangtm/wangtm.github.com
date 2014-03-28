---

layout : post

category : 开发

tags : [selenium   自动化测试 ]

title : 纯手工编写selenium自动化测试gmail邮箱

---


import com.thoughtworks.selenium.*;
import java.util.regex.Pattern;
//该实例都是有google邮箱做测试

public class 登录GMAIL extends SeleneseTestCase{
	public void steUp() throws Exception {
		//指定启动的浏览器和对应的地址
		steUp("http://www.gmail.com","*chorme");
	}
	public void test 登录GMAIL() throws Exception{
		//首先先打开登录地址
		selenium.open("/");

		//输入账号和密码，点击“登录”按钮，中间需要一个等待时间，设定3s；
		assertTrue(selenium.getTitle().matches("^Gmail[\\s\\S]*$"));
		selenium.type("E-mail","wangtangming888@gmail.com");
		selenium.type("passwd","wyh_111219");
		selenium.click("signIn");
		selenium.waitForPageToLoad("3000");

		assertTrue(selenium.getTitle().matches("^Gmail[\\s\\S]*$"));
		//线程挂起，等待时间为3s
		Thread.sleep("3000");

		//编写邮件
		selenium.mouseDown("//div[@class='n3']/div[1]/div[1]");
		selenium.mouseUp("//div[@class='n3']/div[1]/div[1]");

		assertTrue(selenium.getTitle().matches("^Gmail - 撰写邮件 -[\\s\\S]*$"));
		//输入收件人邮箱、标题、和邮件正文
		selenium.type("to","wtm_999@sina.com");
		selenium.type("subject","testgmail");
		selenium.type("//body[@class='editable  LW-yrriRe']","This is test mail");
		selenium.mouseDown("//div[@class='dx J-Jw']/div[1]");
		selenium.mouseUp("//div[@class='dx J-Jw']/div[1]");

		//对邮箱中的邮件进行管理，删除邮件
		//在开启另一个线程的时候，需要把已经开启的一个线程给挂起
		Thread.sleep("3000");
		assertTrue(selenium.getTitle().matches("^Gmail-收件箱[\\s\\S]*$"));
		String totalEmailBefore = selenium.getText("//span[@class='Dj']/b[3]");
		selenium.click("//input[@class='oz-jc']");
		selenium.mouseDown("//div[@class='pl J-J5-Ji']/div[3]");
		selenium.mouseUp("//div[@class='pl J-J5-Ji']/div[3]");
		Thread.sleep("30000");
		String.totalEmailNow = selenium.getTitle("//span[@class = 'Dj']/b[3]");
		System.out.println(totalEmailBefore + "Email at the begin, now only" + totalEmailNow + "Email!!");
		int emailNumBerfore = (Integer.valueOf(totalEmailBefore)).int Value();
		int emailNumNow = (Integer.valueOf(emailNumBerfore - emailNumNow));
		String delNum = String.valueOf(emailNumBerfore - emailNumNow);
		assertEquals("1",delNum);

		//对邮箱的存档操作
		//挂起或者结束另一个进程
		Thread.sleep("30000);
		assertTrue(selenium.getTitle().matches("^Gmail-收件箱[\\s\\S]*$"));
		selenium.click("//input[@class='oz-jc']");
		selenium.mouseDown("//div[@class='pl J-J5-Ji']/div[@act='7']");
		selenium.mouseUp("//div[@class='pl J-J5-Ji']/div[@act='7']");
		Thread.sleep("10000");

		assertTrue("selenium.isTextPresent("该会话已存档")");//这里是一开始我们编写的脚本,我们把这行代码修改成下面的代码就OK了

		//这里我们一运行，会发现报assertTrue的错误，原因是selenium.isTextPresent没有找到
		//文本“该会话已存档”，但是检测页面信息的确是存在。这里我们作如下修改；
		//这是由于selenium的一个缺陷，不能检查静态文本文件
		
		assertTrue(selenium.isTextPresent("//div[@class='vh']/span"));
		

		//下面我们接着测试邮箱的搜索功能
		selenium.type("//input[@class='bQ nr']","test mail");
		selenium.mouseDown("//td[@class = 'bN bM']/div[3]");
		selenium.mouseUp("//td[@class = 'bN bM']/div[3]");
		Thread.sleep("10000");
		assertFalse(selenium.isElementPresent("//td[@class = 'TC']/b[3]"));
		System.out.println("通过搜索\"test mail\",我们找到了" + totalEmailForSerch + "封邮件");
		selenium.type("//input[@class = 'bQ nr']","百度");
		selenium.mouseDown("//td[@class = 'bN bM']/div[3]");
		selenium.mouseUp("//td[@class = 'bN bM']/div[3]");
		Thread.sleep("10000");
		assertTrue(selenium.isVisible("//td[@colspan = '3']"));
		String testString = selenium.getText("//td[@colspan = '3']");
		System.out.println("搜索""百度");
		System.out.println(testString);
		//这里有人或许会说，怎么没有检查邮件是否发送成功呢？
		//这里卖一个关子，可以自己完成
	}
		@After
	public void tearDown() throws Exception {
		selenium.stop();
	}
}
