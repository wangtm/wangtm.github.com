---

layout : post

category : 技术

tags : [ThinkPHP Ajax表单提交]

title :ThinkPHP之Ajax表单提交

---

对提交的处理采用Ajax方式进行了改造。由于本示例使用了表单处理示例的数据表，
如果还不清楚的话可以先下载查看：表单处理示例。
和表单处理示例的区别之处，就是页面提示不再采用默认的跳转页面方式，
而是采用Ajax方式进行页面无刷新提示，并且比表单处理示例多了数据查询操作，如图所示：
默认的操作需要获取数据列表，关键代码：
    public function index() {
        $Form = M("Form");
        // 按照id排序显示前5条记录
        $list = $Form->order('id desc')->limit(5)->select();
        $this->list =   $list;
        $this->display();
    }
检测标题的Ajax响应操作是checkTitle操作方法：
    public function checkTitle($title='') {
        if (!empty($title)) {
            $Form = M("Form");
            if ($Form->getByTitle($title)) {
                $this->error('标题已经存在');
            } else {
                $this->success('标题可以使用!');
            }
        } else {
            $this->error('标题必须');
        }
    }
处理表单请求数据的方法稍作改进，采用AjaxReturn方法返回JSON数据到浏览器：
    public function insert() {
        $Form = D("Form");
        if ($vo = $Form->create()) {
            if (false !== $Form->add()) {
                $vo['create_time'] = date('Y-m-d H:i:s', $vo['create_time']);
                $vo['content'] = nl2br($vo['content']);
                $this->ajaxReturn($vo, '表单数据保存成功！', 1);
            } else {
                $this->error('数据写入错误！');
            }
        } else {
            $this->error($Form->getError());
        }
    }