---

layout : post

category : manage

tags : [Selenium-webdriver  自动化]

title : 如何捕获弹出窗口

---


在web自动化测试中点击一个链接然后弹出新窗口是比较司空见惯的事情。
webdriver中处理弹出窗口跟处理frame差不多，以下面的html代码为例

window.html

<html>

    <head><title>Popup Window</title></head>

    <body>

        <a id = "soso" href = "http://www.soso.com/" target = "_blank">click me</a>

    </body>

</html>


下面的代码演示了如何去捕获弹出窗口
require 'rubygems'

require 'pp'

require 'selenium-webdriver'



dr = Selenium::WebDriver.for :firefox

frame_file = 'file:///'.concat File.expand_path(File.join(File.dirname(__FILE__), 'window.html'))

dr.navigate.to frame_file

dr.find_element(:id =>'soso').click

# 所有的window handles

hs = dr.window_handles

# 当前的window handle

ch = dr.window_handle

pp hs

pp ch 

hs.each do |h|

    unless h == ch

        dr.switch_to.window(h)

        p dr.find_element(:id => 's_input')

    end

end

捕获或者说定位弹出窗口的关键在于获得弹出窗口的handle。
在上面的代码里，使用了window_handles方法获取所有弹出的浏览器窗口的句柄，然后使用window_handle方法来获取当前浏览器窗口的句柄，将这两个值的差值就是新弹出窗口的句柄。
在获取新弹出窗口的句柄后，使用switch_to.window(new_window_handle)方法，将新窗口的句柄作为参数传入既可捕获到新窗口了。
如果想回到以前的窗口定位元素，那么再调用1次switch_to.window方法，传入之前窗口的句柄既可达到目的。