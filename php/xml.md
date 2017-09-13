php中xml数据的处理
1、XML Expat 解析器
	基本使用
		//创建xml解析器
		$parser=xml_parser_create();
		//发现开始节点
		function start($parser,$element_name,$element_attrs){
			switch($element_name){
				case "NOTE":
						echo "-- Note --<br>";
					break;
				case "TO":
						echo "To: ";
					break;
				case "FROM":
						echo "From: ";
					break;
				case "HEADING":
						echo "Heading: ";
					break;
				case "BODY":
						echo "Message: ";
					break;
			}
		}
		//xml解析结束
		function stop($parser,$element_name){
		echo "<br>";
		}
		//xml解析找到数据
		function char($parser,$data){
		echo $data;
		}
		//设置遇到节点调用的函数
		xml_set_element_handler($parser,"start","stop");
		//设置遇到数据调用的函数
		xml_set_character_data_handler($parser,"char");
		//打开xml文件
		$fp=fopen("base.xml","r");
		//读取xml文件数据
		while ($data=fread($fp,4096)){
		//开始解析xml数据	
		xml_parse($parser,$data,feof($fp)) or die (sprintf("XML Error: %s at line %d", xml_error_string(xml_get_error_code($parser)),xml_get_current_line_number($parser)));
		}
		//释放xml解析器
		xml_parser_free($parser);


2、