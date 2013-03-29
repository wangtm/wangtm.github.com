---

layout : post

category : 技术

tags : [提交表单后PHP不能获取提交内容]

title : 提交表单后PHP不能获取提交内容

---

	1. 修改php.ini，查找 register_globals，将其值修改为 On。这样就可以像原来一样，
	例如，提交的表单中包括一个名为"username"的变量，那么在php中就可以直接使用$username来访问该变量。
	但是，除非你要使用一段旧的代码而考虑到兼容性问题，否则不建议使用该方法。

　　2. 使用 $HTTP_GET_VARS、$HTTP_POST_VARS数组来访问，例如写成$HTTP_POST_VARS["username"]的形式。

　　3. 使用 $_POST、$_GET等数组来访问，例如写成 $_POST["username"]的形式。

　　4. 使用 import_request_variables 函数。该函数将提交内容导入到变量中。
       例如　import_request_variables("gp", "rvar_");第一个参数可以选择g,p,c，分别表示导入 GET,POST,COOKIE 变量；
	   第二个参数为导入后的变量前缀。执行上面的语句后即可使用 $rvar_username 来访问提交的 username 变量。
	   使用import_request_variables("gp", "");可以兼容以前的PHP程序。

