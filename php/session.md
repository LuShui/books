session
	PHP会话管理，为用户分配唯一的身份标识，使用 $_SESSION 保存，在PHP脚本结束后，PHP会自动序列化并将其保存为文件

	传送会话ID
		1、通过cookie传送
		2、URL参数
			当用户禁用cookie后可以通过URL参数进行传送
			当启用了 session.use_trans_sid 选项， PHP 将会自动在相对 URI 中包含会话 ID

	自定义会话保存机制
		1、通过 session_set_save_handler()
		2、通过 SessionHandlerInterface 类 或者通过继承 SessionHandler 类来扩展内置的管理器


	session 内置函数
		session_abort()   		结束会话且不保存sessionid
		

