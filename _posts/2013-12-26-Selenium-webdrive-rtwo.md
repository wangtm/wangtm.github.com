---

layout : post

category : manage

tags : [Selenium-webdriver  自动化]

title : 如何操作select下拉框

---

在selenium-webdriver中定位select list的方法比较简单，用id和name等属性可以很方便的将select给找出来，但是怎么去选择下拉框中的某一项呢？
思路是这样的，首先定位到select list元素，然后找出该select list下所有的option，点击该option element既可，以下面的html代码为例
<html>
    <head>
        <title>Select</title>
    </head>
    <body>
        <span>select demo</span>
        <select id = "s" name = "ns">
            <option value = "0">Op1</option>
            <option value = "1">Op2</option>
            <option value = "2">Op3</option>
            <option value = "3">Op4</option>
        </select>
    </body>
</html>
通过下面的代码可以选择到下拉框中的第2个option，也就是text为Op2的选项
require 'rubygems'
require 'selenium-webdriver'
 
dr = Selenium::WebDriver.for :firefox
select_file = 'file:///'.concat File.expand_path(File.join(File.dirname(__FILE__), 'select.html'))
dr.navigate.to select_file
dr.find_element(:id => 's').find_elements(:tag_name => 'option')[1].click
不难看出这样的代码还是不太直观的。为了能够更好的操作select元素，我们可以对其做一个简单的封装，示例代码如下：
easy_wrap.rb
 
require 'rubygems'
require 'selenium-webdriver'
module EasyWrap
    class Select
        def initialize e
            raise NotValidElementError unless e.is_a?(Selenium::WebDriver::Element) 
            @e = e
            child_options
        end 
 
        def select_by_value value
            @ops.each do |op|   
                op.click if op['value'] == value
            end
        end
 
        def select_by_index index
            @ops[index].click if valid_index? index
        end
 
        def select_by_text text
            @ops.each do |op|
                op.click if op['text'] == text
            end
        end
 
        def valid_index? index
            index.to_i < (@ops.size - 1)
        end
 
        def child_options
            begin
                @ops = @e.find_elements(:tag_name => 'option')
            rescue
                raise CanNotFindOptionError, "can not find options in #{@o}"
                exit
            end
        end
 
        def options
            @ops_text_arr = []
            @ops.each do |op|
                @ops_text_arr << op['text']
            end
            @ops_text_arr
        end
    end 
 
    class EasyWrapError < StandardError; end
    class NotValidElementError < EasyWrapError; end
    class CanNotFindOptionError < EasyWrapError; end
end #EasyWrap
通过引用该文件，我们的代码此时就应该是如下所示
select.rb
 
require './easy_wrap'
 
dr = Selenium::WebDriver.for :firefox
select_file = 'file:///'.concat File.expand_path(File.join(File.dirname(__FILE__), 'select.html'))
dr.navigate.to select_file
s = EasyWrap::Select.new dr.find_element(:id => 's')
# 选择value是1的option
s.select_by_value('1')
sleep 2
# 选择index是2的option,也就是第3个option
s.select_by_index(2)
sleep 2
# 选择text是Op4的option
s.select_by_text('Op4')
sleep 3
dr.close
上面的代码可以看出，在选择了下拉框的某1个option时，如果下拉框上绑定有onchange事件，那么onchange事件是不会被触发的，这应该是上面解决方案的一个缺陷。






