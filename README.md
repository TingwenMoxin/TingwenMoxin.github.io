# TingwenMoxin.github.io
理论部分，回答以下问题：
1）．试论述类与用例的区别。
答：类是具有一些相同特性的对象，用例是描述一个特定角色一系列的动作
2）．试比较边界类与实体类的异同。
答：边界类通常用来完成参与者和系统之间的交互的对象，实体类用来描述具体的实体
3）．试运用本节所学的静态建模技术找出用户管理模块中的所有的类。
答：实体类：Users（用户）类、Administrator（管理员）类、Userinfo（用户信息）类、
边界类：登录
控制类：数据操作
4）．请找出学生管理系统中学生注册用例的实体类，边界类，控制类。
答：实体类：ReportCard（报告）类、Grades（）类、Administrator（管理员）类、student（学生）类、teacher（教师）类
边界类：登录
控制类： 数据操作
5）．什么是依赖？它与关联有什么区别？
答：依赖表示两个或多个模型元素之间语义上的关系；关联是结构上的关系，描述了系统中对象或实例之间的离散连结。
6)．什么是泛化？泛化是否就是类的继承，如果不是请说明理由。
答：泛化是一种类型上的用于一般元素和特殊元素之间的分类关系；是一种子父类的继承关系的吧
7）．试论述聚合和组合的异同。
答：聚合不仅控制着成员对象的行为，而且控制着成员对象的创建和撤销，简单的聚合没有改变整体和部分之间跨越关联的导航含义，也不与整体和部分的生命周期相关；组合又叫强聚合，成员对象的生命周期取决于聚合的生命周期

2、学院公众号中，成绩查询模块可以很方便地使在校学生查询到期末考试成绩，特别是老师将期末成绩提交后，该模块会以弹窗的方式将信息通知到学生，问题：请根据滇池学院微信公众号中，学生成绩查询模块的功能，对该模块进行小组讨论分析，对该功能的类图中以
下元素进行必要说明：
1）该功能一共应该包含哪几个类
答：该功能应该包含学生类，考试科目类，教师类，公众号系统类。
2）每个类的属性，方法应该是什么，有什么作用，权限该是什么
答：学生类的属性应该有：①学号（int） ②姓名（string）  ③系别（string）；操作包括：成绩下载、学期筛选、查看成绩；学号是私有属性，姓名、专业、系别都是公有属性。

考试科目的属性应该有：①课程名（string）②成绩（int）③学分（int）；操作包括：获取课程信息、获取课程成绩；成绩是私有属性，课程名和学分都是公有属性。

教师类属性应该有：教师号（int）姓名（string）所属课程（string）；操作包括：成绩下载、学期筛选、查看成绩、成绩推送；教师号是私有属性，姓名、所属课程都是公有属性。

公众号系统类的属性应该有：①用户名（string）②密码（int）；操作包括：登陆系统、推送成绩。密码是私有属性，用户名是公有属性。
3）类之间分别有什么关系
答：学生类和考试科目类的关系应为依赖关系，学生类和教师类的关系应为依赖关系，学生类和公众号系统类的关系应为实现关系，考试科目类和教师类的关系应为依赖关系，考试科目类和公众号系统类应为关联关系，教师类和公众号系统类应为实现关系。
4）使用 staruml 画出该功能模块

3、网络的普及带给了人们更多的学习途径，随之而来的管理远程网络教学的“远程网络教学系统”诞生了。“远程网络教学系统”的功能需求如下：学生登录网站后，可以浏览课件、查找课件、下载课件、观看教学视频。教师登录网站后，可以上传课件、上传教学视频、发布教学心得、查看教学心得、修改教学心得。系统管理员负责对网站页面的维护、审核不合法课件和不合法教学信息、批准用户注册。
问题：老师需要登录“远程网络教学系统”后才能正常使用该系统的所有功能。如果忘记密码，可与通过“找回密码”功能恢复密码。请使用staruml 画出教师参与者的类图。
说明：由于题目中要求分析的是教师参与者的类图，固选取符合教师参与者的参与者，用例进行分析，对于学生参与者类，只进行简略的描述或者不描述；
在用户使用的时候，需要使用找回密码的累，找回密码选项中，假设使用手机确认用户，所以在注册和找回密码的时候需要用户提供手机号码（Tel）作为一个属性；
说明：根据类的划分划分，
实体类：课件(CourseWare），教学心得(TeachExperience），教学视频（TeachVideo），管理员（Administrator），教师（Teacher）

控制类：上传（upLoadOrNot）,登录（Login）

边界类：登陆页面(loginPage)，注册（Register），找回密码（Retrieve PassWord）
1初步分析以及用例图描述：
在该部分为两部分的分析：根据用例图，进行初步分析类之间的关系和多重度的分析
①教师（Teacher）和学生（Students）类应该是拥有一个公共的父类，即用户（User）类，是教师类的父类。有教师类继承于User类，但是管理员Adminstrtor不应属于用户，所以单独列出，作为一个单独的类；

②根据上述用例图分析，以及题目的描述，知道有：只有教师类才能上传教学视频（TeachVideo），课件(CourseWare），教学心得(TeachExperience），，而且，一门课程，可能有多名老师授课，至少一名老师上课，在上传课件，教学视频和教学心得的时候，可能上传0或者多个课件，教学视频和教学心得。固然，教师和教学视频（TeachVideo），课件(CourseWare），教学心得(TeachExperience），之间存在教师1..*和课件，教学心得，教学视频的0..*的多重度m描述；

③ 找回密码（Retrieeve PassWord）类，注册类（Register），都应该存在依赖于登录类（Login）,
而且注册类由于受管理员（Administrator）的管理，存在管理员（Administrator）1..*和注册（Register）1..*的多重度联系；


④  教师（Teacher）是用户（User）类的子类；用户的操作和管理员（Administrator）的操作都依赖于登录类（Login）；

