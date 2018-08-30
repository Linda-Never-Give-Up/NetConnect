# SQLITE
			
		Class.forName("org.sqlite.JDBC");
		Connection connection = null;
		connection = DriverManager.getConnection("jdbc:sqlite:D:/222.db");
		Statement statement = connection.createStatement();
		statement.execute("create table userinfo (id integer primary key autoincrement,username varchar(20),password varchar(20) )");
		connection.close();


# xSTREAM （生成XML文件）
		XStream xstream = new XStream(new DomDriver());
		xstream.alias("person", Person.class);
		String xml = xstream.toXML(person);

# GSON
		Gson gson = new Gson();
		System.out.println(gson.toJson(persons));



### public class GenerateXML {

	public static void main(String[] args) {

		News news1 = new News("title1", "www.baidu.com/news1", "星期一");
		News news2 = new News("title2", "www.baidu.com/news2", "星期2");
		News news3 = new News("title3", "www.baidu.com/news3", "星期3");
		
		ArrayList<News> list=new ArrayList<>();
		list.add(news1);
		list.add(news2);
		list.add(news3);
		
		// 创建一个xml的生成器
		XStream xstream = new XStream(new DomDriver());
		xstream.alias("item", News.class); //xinwen就是根节点,自己取名。
		String xml = xstream.toXML(list);

		System.out.println(xml);
	}

		  <item>
		    <title>001</title>
		    <data>aaa</data>
		    <content>1</content>
		  </item>


		<list>
		  <item>
		    <title>001</title>
		    <data>aaa</data>
		    <content>1</content>
		  </item>
		  <item>
		    <title>002</title>
		    <data>bbb</data>
		    <content>2</content>
		  </item>
		</list>


###  Java对象和XML

	Stream对象相当Java对象和XML之间的转换器，转换过程是双向的。创建XSteam对象的方式很简单，只需要new XStream()即可。 
    Java到xml，用toXML()方法。 
    Xml到Java，用fromXML()方法。

利用sharedPreference生成xml文件保存用户数据 

				// 共享的参数项
				// MODE_PRIVATE: 私有化数据,只能自己访问,其他应用无法访问
				// MODE_WORLD_READABLE:全局可读,创建的文件其他应用也可以访问
				// MODE_WORLD_WRITEABLE:全局可读写,创建的文件其他应用也可以访问
				// 生成的文件的名字由自己指定
				SharedPreferences sp = getSharedPreferences("aa", MODE_PRIVATE);
				// 生成的文件的名字为当前类的类名
				// SharedPreferences sp = getPreferences(MODE_PRIVATE);
				// xml文件的编辑器
				Editor editor = sp.edit();
				// 设置要保存的数据
				editor.putBoolean("cb_status", isChecked);
				// 保存数据
				editor.commit();


# xml文件的序列化 

	public void generateXML2(View v) {
		try {
			// 创建一个xml生成器
			XmlSerializer serializer = Xml.newSerializer();
			//安卓应用程序保存文件的路径:data/data/pkg name/
			File file = new File("/data/data/com.itheima.generateXML/aa.xml"); 
			FileOutputStream fos = new FileOutputStream(file);
			// 设置输出流
			serializer.setOutput(fos, "utf-8");
			// 开始写文件
			serializer.startDocument("utf-8", true);

			// 开始写标签
			serializer.startTag(null, "map");
			serializer.startTag(null, "boolean");
			// 写属性
			serializer.attribute(null, "name", "cb_status");
			serializer.attribute(null, "value", "true");

			// 标签结束
			serializer.endTag(null, "boolean");
			serializer.endTag(null, "map");

			// 写文件结束
			serializer.endDocument();
			fos.close();
			Toast.makeText(this, "生成成功", Toast.LENGTH_SHORT).show();
		} catch (Exception e) {
			Toast.makeText(this, "生成失败", Toast.LENGTH_SHORT).show();
			e.printStackTrace();
		}
	}



# 利用pull解析器解析xml文件 

* 拷贝的文件一定拷贝到assets目录
	
	常见标签的类型:
	* START_DOCUMENT : 0. 文档开始
	* END_DOCUMENT   : 1. 文档结束
	* START_TAG      : 2. 标签开始
	* END_TAG        : 3. 标签结束
	* TEXT           : 4. 文本标签


	public void parseXML(View view) {
		try {
			// 打开了Assets目录里的文件,返回值是一个输入流
			InputStream inputStream = getAssets().open("person.xml");
			// 获取一个XML的解析器
			XmlPullParser pullParser = Xml.newPullParser();
			// 设置输入流
			pullParser.setInput(inputStream, "utf-8");
			int type;
			// 获取标签的类型
			type = pullParser.getEventType();
			while (type != XmlPullParser.END_DOCUMENT) {
				// 小心死循环
				type = pullParser.next();

				if (type == XmlPullParser.START_TAG) {
					if (pullParser.getName().equals("name")) {
						// 获取标签里的内容
						System.out.println("name:" + pullParser.nextText());
					} else if (pullParser.getName().equals("age")) {
						System.out.println("age:" + pullParser.nextText());
					} else if (pullParser.getName().equals("tel")) {
						System.out.println("tel:" + pullParser.nextText());
					} else if (pullParser.getName().equals("person")) {
						// 获取标签里的属性值
						System.out.println("person:" + pullParser.getAttributeValue(0));
					}
				}
			}
		} catch (Exception e) {
			e.printStackTrace();
		}
	}

# 手写web服务器

	熟悉服务器技术的核心
	用IE浏览器 http://127.0.0.1:9999/

		public static void main(String[] args) throws IOException {
			// 创建了一个ServerSocket
			ServerSocket serverSocket = new ServerSocket(9999);
			// 等待别人的连接
			Socket socket = serverSocket.accept();
			socket.getOutputStream().write("<h1>hello tomcat</h1>".getBytes());

			socket.close();
			serverSocket.close();
		}	