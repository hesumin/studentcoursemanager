# studentcoursemanager
# 学生选课管理系统

## studentcoursemanager
## 学生选课管理系统

### studentcoursemanager
### 学生选课管理系统

# 目录
学生选课管理系统	4
一、项目设计目的和意义	4
二、项目设计背景	5
三、开发技术	5
四、数据库设计分析	5
  1、选课系统分析：	5
  2、角色需求描述：	9
    登录界面：	12
    管理员界面：	12
    学生界面：	13
    教师界面：	13
五、数据库设计内容：	14
  1、以管理员权限登录：	14
    1）首页展示信息：	14
    2）学生管理：	15
    3）教师管理：	17
    4）课程管理：	19
    5）分数区间统计：	21
    6）及格率统计：	23
    7）管理员信息：	24
  2、以教师权限登录：	24
    1）评分管理：	24
    2）查询统计：	26
  3、以学生权限登录：	26
    1）学生选课：	26
    2）统计查询：	27
六、后端项目功能实现	28
  1、项目搭建	28
  2、前端界面	29
  3、功能设置	29
  4、前端列表展示分页实现	30
  5、列表中组合条件查询	31
  6、查询统计	31
七、总结	32
八、参考文献	32
九、附录	33






 
学生选课管理系统
项目名称	基于javaweb开发的学生选课管理系统
负责人	班级	18级计算机科学与技术（人工智能方向）2班	姓名	何苏敏	学号	1825104007
	手机号码	18120782485	E-mail	1825104007@hqu.edu.cn
项目计划组成员	姓名	班级	学号	手机号码	主要分工	备注
	何苏敏	18计科2班	1825104007	18120782485	前端，后端，数据库设计	

一、项目设计目的和意义
  随着无纸化办公的广泛实现，信息自动处理和网络式信息的交互方法已经得到了广泛的应用。让计算机管理学生信息，是目前各大高校积极开展的工作之一，也是大学教育管理的重要工作内容之一。网上选课比传统选课更加节省资源，增加了学生的选课的自主权。
学生选课管理系统作为一种现代化的教学办公技术，越来越受到人们的重视，是一个学校非常重要的部分, 学生选课系统就是为了方便管理选课信息而设计的。学生选课管理系统将使选课管理工作变得更加规范化、系统化、程序化，避免选课管理的随意性，提高信息处理的速度和准确性，能够准确、及时、有效的查询和修改学生选课情况。在选课期间内，学生能够使用选课系统灵活的修改自己的选课情况，大大提高了学校选课工作的效率。学校教务处则可以通过选课系统的管理员权限来管理学生的选课情况，使得学生选课工作达到系统化和自动化，大大提高了学校的工作效率。
二、项目设计背景
数据库对于一个系统的应用具有十分重要的意义，一个设计良好的数据库系统一方面，能够给开发人员带来更便捷，更轻松的进行系统设计与编码；另一方面，对于系统后期的维护也非常重要，一个良好的数据库系统能够保证系统的可扩充性，以及系统的移植性等问题。
学生选课系统的出现使同学们能够更加自主、便捷、准确的进行选课。但是，由于一般高校中的学生都比较多，因此带来了诸多如信息管理等问题，鉴于需要将学生信息、选课信息等信息数字化以便于管理维护，我们便想到了利用数据库能够比较良好地解决此类问题，为此下面我将设计出一个学生选课管理系统。
三、开发技术
开发工具：IntelliJ IDEA + Navicat（MYSQL连接） + 前端浏览器
开发语言：java + JSP + MYSQL + 前端基础（Html、css、JavaScript、Jquery）
开发技术：Javaweb（SSM框架）+ Web容器（Tomcat）+ Tomcat后台服务技术
四、数据库设计分析
1、选课系统分析：
根据分析，我在数据库系统设计了10张表以上。本系统的实体主要有5类，管理员（教务处管理人员），学生、教师、课程和选课信息，其他表格如及格率和一些统计查询在后面详细说明，如下表示：
描述学生的属性有：学生编号ID、学生姓名、学生学号、学生密码。
student：E-R图
 
学生信息表：
字段	字段名	类型	可否为空	主键
stuId	学生id	int(11)	否	是
stuName	学生姓名	varchar(20)		
stuNo	学号	varchar(20)		
stuPwd	学生密码	varchar(50)		

DROP TABLE IF EXISTS `student`;
CREATE TABLE `student`  (
`stuId` int(11) NOT NULL AUTO_INCREMENT,
`stuName` varchar(20) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
`stuNo` varchar(20) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
`stuPwd` varchar(50) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
PRIMARY KEY (`stuId`) USING BTREE
) ENGINE = InnoDB AUTO_INCREMENT = 98 CHARACTER SET = utf8 COLLATE = utf8_general_ci ROW_FORMAT = Compact;

描述教师的属性有：教师编号ID、教师姓名、教师账号名、教师账号密码。
teacher：E-R图
 
教师信息表
字段	字段名	类型	可否为空	主键
tId	教师id	int(11)	否	是
tName	教师姓名	varchar(20)		
userName	用户名	varchar(20)		
pwd	密码	varchar(50)		


DROP TABLE IF EXISTS `teacher`;
CREATE TABLE `teacher`  (
`tId` int(11) NOT NULL AUTO_INCREMENT,
`tName` varchar(20) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
`userName` varchar(20) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
`pwd` varchar(50) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
PRIMARY KEY (`tId`) USING BTREE
) ENGINE = InnoDB AUTO_INCREMENT = 66 CHARACTER SET = utf8 COLLATE = utf8_general_ci ROW_FORMAT = Compact;

描述课程的属性有：课程编号ID、课程名称、授课老师编号、
course：E-R图
 
课程信息表：
字段	字段名	类型	可否为空	主键
cId	课程id	int(11)	否	是
cName	课程名	varchar(20)		
tId	课程教师id	int(11)		


DROP TABLE IF EXISTS `course`;
CREATE TABLE `course`  (
`cId` int(11) NOT NULL AUTO_INCREMENT,
`cName` varchar(20) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
`tId` int(11) NULL DEFAULT NULL,
PRIMARY KEY (`cId`) USING BTREE,
INDEX `FK_Reference_1`(`tId`) USING BTREE,
CONSTRAINT `FK_Reference_1` FOREIGN KEY (`tId`) REFERENCES `teacher` (`tId`) ON DELETE RESTRICT ON UPDATE RESTRICT
) ENGINE = InnoDB AUTO_INCREMENT = 12 CHARACTER SET = utf8 COLLATE = utf8_general_ci ROW_FORMAT = Compact;

描述选课信息的属性有：选课编号ID、学生编号、课程编号、课程分数。
sc：E-R图
 
选课信息表：
字段	字段名	类型	可否为空	主键
scId	选课id	int(11)	否	是
stuId	选课学生id	int(11)	否	
cId	选课课程id	int(11)	否	
score	分数	varchar(50)		


DROP TABLE IF EXISTS `sc`;
CREATE TABLE `sc`  (
`scId` int(11) NOT NULL AUTO_INCREMENT,
`stuId` int(11) NULL DEFAULT NULL,
`cId` int(11) NULL DEFAULT NULL,
`score` decimal(5, 2) NULL DEFAULT NULL,
PRIMARY KEY (`scId`) USING BTREE,
INDEX `FK_Reference_2`(`stuId`) USING BTREE,
INDEX `FK_Reference_3`(`cId`) USING BTREE,
CONSTRAINT `FK_Reference_2` FOREIGN KEY (`stuId`) REFERENCES `student` (`stuId`) ON DELETE RESTRICT ON UPDATE RESTRICT,
CONSTRAINT `FK_Reference_3` FOREIGN KEY (`cId`) REFERENCES `course` (`cId`) ON DELETE RESTRICT ON UPDATE RESTRICT
) ENGINE = InnoDB AUTO_INCREMENT = 182 CHARACTER SET = utf8 COLLATE = utf8_general_ci ROW_FORMAT = Compact;

描述管理员的属性有：管理员编号ID、管理员账号名、管理员账号密码、管理员姓名。
admin：E-R图
 
管理员信息表：
字段	字段名	类型	可否为空	主键
id	管理员id	int(11)	否	是
userName	管理员用户名	varchar(20)		
pwd	密码	varchar(50)		
name	管理员姓名	varchar(20)		


DROP TABLE IF EXISTS `admin`;
CREATE TABLE `admin`  (
`id` int(11) NOT NULL AUTO_INCREMENT,
`userName` varchar(20) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
`pwd` varchar(50) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
`name` varchar(20) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
PRIMARY KEY (`id`) USING BTREE
) ENGINE = InnoDB AUTO_INCREMENT = 2 CHARACTER SET = utf8 COLLATE = utf8_general_ci ROW_FORMAT = Compact;

2、角色需求描述：
管理员、老师、学生
1、管理员：维护学生和老师信息、查询统计
1）管理员操作流程：
a) 登录系统
b) 实现对学生的CURD
c) 实现对老师的CURD
d) 实现各种查询、统计
2、老师：基本信息、所教课程
1)	老师操作流程：
a)	登录系统
b)	课程管理（实现对课程的CURD）
c)	考试成绩录入
d)	各种查询（学生的单科成绩、总成绩、排名）
e)	各种统计（统计及格率、统计>80分以上的同学等）
3、学生：基本信息、课程信息
1）学生操作流程：
1、	学生登录系统
2、	选择课程并提交确认（确认之后则不能修改了）
3、	考试系统
4、	各种查询（查询各科成绩、查询总成绩、查询排名等）
2)	学生查询功能
a)	各科成绩查询
b)	总成绩查询
c)	成绩排名、各科成绩排名
4、学生选课数据库系统——流程示意图
 
在选课系统中，，每个学生可选多门课程或者不选，每个教师教授多门课程。

1、用户登录时需要有一个用户名和密码，并选择相对应的身份即可以登录。
登录界面：
 

2、管理员可以查看选课系统中的整体信息，管理员权限包括学生管理，教师管理，课程管理，分数区间统计，课程及格率查询等，在下面有详细说明。
管理员界面：
 




3、学生进入选课系统后可以进行选课功能，修改并提交选课，课程分数查询统计。
学生界面：
 

4、教师进入选课系统后可以进行评分管理，对应教师选择自己教的那些课并进行相对应课程学生的分数评定，可以查询课程中学生们的总体分数段分类查询，学生课程分数及格率信息查询。
教师界面：
 
 

五、数据库设计内容：
我设计的学生选课管理系统，选课管理系统是学校教务系统中比较重要的一个数据库系统，在这里我将这个系统做了一个简化，选取了部分比较直观的关系模式。设计的数据库系统包括管理员信息，学生信息管理、教师信息管理、课程信息管理、分数统计信息，成绩及格率信息，教师评分管理，教师对课程的信息管理以及对学生的信息管理，学生选课信息、还有选课成绩查询。据此完成了一个学生选课管理系统。
设计目标：
所实现的功能有：
1、以管理员权限登录：
1）首页展示信息：
首页展示学生总体的成绩及格率可视化图表，包括及格率柱状图，及格率折线图，及格率饼图以及学生总分排行图表，可以清晰直观的看出总体学生的水平分布概况。
 
2）学生管理：
ID	姓名	学号	操作
78	张三	0001	修改  删除
79	李四	0002	修改  删除
80	王五	0003	修改  删除
81	张夏明	0004	修改  删除
82	李现	0005	修改  删除
83	王珍珍	0006	修改  删除
84	张珊珊	0007	修改  删除
85	米树	0008	修改  删除
86	欧哥	0009	修改  删除
87	张夏明	0010	修改  删除

 
可以新增学生信息，学生相关信息包括学号，姓名，登录密码，增加完成之后会提示增加成功并会展示在列表中。 
insert into student(stuName,stuNo,stuPwd) values(?,?,?)
 
可以查询学生信息，查询索引值可以是学生ID，学生姓名，学生学号中的一个或几个，查询信息输入再点击查询之后会将查询结果展示在列表中。 
select * from student
 
可以修改学生信息，由于学生ID是数据库中设置的唯一主键且是递增的，所以修改学生信息中可以修改学生学号，学生姓名，修改完成后点击提交会将新的学生信息展示在列表中。 
update  student set stuName = ?,stuNo = ? where stuId = ?
 
可以删除学生信息，点击删除按钮后将删除学生信息并会更新后展示在列表中。
delete from student where stuId = ?
 

3）教师管理：
ID	姓名	账号	操作
1	张平	zhangping	修改  删除
2	欧阳锋	ouyangfeng	修改  删除
3	杨过	yangguo	修改  删除
4	洪七公	hongqigong	修改  删除
5	郭靖	guojing	修改  删除
6	黄蓉	huangrong	修改  删除
7	欧阳克	ouyangke	修改  删除
8	杨铁心	yangtiexin	修改  删除
65	黄药师	huangyaoshi	修改  删除

 
可以新增老师信息，老师相关信息包括老师姓名，老师账号，登录密码，增加完成之后会提示增加成功并会展示在列表中。 
insert into teacher(tName,userName,pwd) values(?,?,?)
 
可以查询教师信息，查询索引值可以是教师ID，教师姓名，教师账号中的一个或几个，查询信息输入再点击查询之后会将查询结果展示在列表中。 
select * from teacher
 
可以修改教师信息，由于教师ID是数据库中设置的唯一主键且是递增的，所以修改教师信息中可以教师姓名，教师账号，修改完成后点击提交会将新的教师信息展示在列表中。 
update teacher set  tName = ?,USERNAME = ? where tid = ?
 
可以删除教师信息，点击删除按钮后将删除教师信息并会更新后展示在列表中。
delete from teacher where tid = ?
 

4）课程管理：
ID	课程名	老师	操作
1	Java	张平	修改  删除
2	html	张平	修改  删除
3	javascript	张平	修改  删除
4	python	欧阳锋	修改  删除
5	spark	欧阳锋	修改  删除
6	hadoop	杨过	修改  删除
7	ruby	杨过	修改  删除
8	jdbc	黄蓉	修改  删除
9	css	黄蓉	修改  删除
10	Hibernate	黄蓉	修改  删除

 
可以新增课程信息，课程信息中包括课程名称，课程所属老师，而且课程老师在教师管理中已经准备好了所以以下拉框提示选择，选择相对应的老师之后点击提交，增加完成之后会提示增加成功并会展示在列表中。 
insert into course(cname,tid) values(?,?)
 
可以查询课程信息，查询索引值可以是课程ID，课程名，教师姓名，教师账号等相对应课程信息可以查找对应的课程，查询信息输入再点击查询之后会将查询结果展示在列表中。 
select course.*,teacher.tname,teacher.userName from course,teacher where course.tid = teacher.tId
 
可以修改课程信息，由于课程ID是数据库中设置的唯一主键且是递增的，所以修改课程信息中可以课程名称，重新选择课程对应的老师，修改完成后点击提交会将新的课程信息展示在列表中。 
update course set cname = ?,tid = ? where cid = ?
 
可以删除课程信息，点击删除按钮后将删除课程信息并会更新后展示在列表中。
delete from course where cid = ?
 

5）分数区间统计：
ID	课程名	(0,60)	[60,70]	(70,85]	(85,100]
1	Java	3	2	7	1
2	html	3	3	2	3
3	javascript	2	3	3	2
4	python	3	3	4	3
5	spark	2	1	6	4
6	hadoop	2	2	2	5
7	ruby	2	1	5	4
8	jdbc	1	1	6	3
9	css	0	0	0	0
10	Hibernate	0	0	0	0

 
	分数区间统计中展示的信息包括课程ID，课程名，分数区间分为(0,60)，[60,70]，(70,85]，(85,100]，将学生的得分信息分成这四类计数统计在列表中。

"select course.cid,cname,ifnull(bad,0) bad,ifnull(common,0) common,ifnull(good,0) good,ifnull(best,0) best" + 
      " from course" + 
      " left join (" + 
      " select cid,count(*) bad from sc where score<60 group by cid" + 
      " ) A on course.cid = A.cid" + 
      " left join (" + 
      " select cid,count(*) common from sc where score>=60 and score<=70 group by cid" + 
      " ) B on  course.cid = B.cid" + 
      " left join(" + 
      " select cid,count(*) good from sc where score>70 and score<=85 group by cid" + 
      " ) C on course.cid = C.cid" + 
      " left join (" + 
      " select cid,count(*) best from sc where score>85 and score<=100 group by cid" + 
      " ) D on course.cid =D.cid "

	
6）及格率统计：
ID	课程名	及格人数	总人数	及格率
1	Java	10	14	71.00%
2	html	8	12	67.00%
3	javascript	8	11	73.00%
4	python	10	14	71.00%
5	spark	11	14	79.00%
6	hadoop	9	12	75.00%
7	ruby	10	13	77.00%
8	jdbc	10	12	83.00%

 
及格率统计中将展示相对应的课程及格人数及及格率的统计，展示信息包括课程ID，课程名，及格人数，所选课程总人数，课程及格率。
// 课程及格人数
sql1= "select A.cid,(" + 
      " select cname from course where A.cid = course.cid " + 
      " ) cname,jgnum,allnum,round(jgnum/allnum,2)*100 jgl from (" + 
      " select cid, count(*) jgnum from sc where score>=60 group by cid " + 
      " ) A,(" + 
      " select cid, count(*) allnum from sc group by cid " + 
      " ) B where A.cid = B.cid ";

// 课程及格率
sql2 = "select * from course,(" + 
      " select A.cid,jgnum,allnum,round(jgnum/allnum,2)*100 jgl from (" + 
      " select cid, count(*) jgnum from sc where score>=60 group by cid " + 
      " ) A,(" + 
      " select cid, count(*) allnum from sc group by cid " + 
      " ) B where A.cid = B.cid" + 
      " ) C where course.cid = C.cid " + 
      " and tid = ?";


7）管理员信息：
	ID	1
用户名	admin
姓名	管理员
管理员除了可以查看这些信息以及完成这些功能之外，当管理员需要更换的时候，还可以修改自己的密码：
 

2、以教师权限登录：
1）评分管理：
	以教师张平为例，
 
ID	课程名	老师	操作
1	Java	张平	评分
2	html	张平	评分
3	javascript	张平	评分

 
ID	学生姓名	评分
80	王五	74
81	张夏明	78
82	李现	79
83	王珍珍	99
84	张珊珊	68
85	米树	66
86	欧哥	47
87	张夏明	84
88	香加皮	39
89	程咬金	85
90	丽水	75
91	实施	73
92	伸缩缝	55
78	张三	98

2）查询统计：
 
分数区间统计
ID	课程名	(0,60)	[60,70]	(70,85]	(85,100]
1	Java	3	2	7	2
2	html	3	3	2	3
3	javascript	2	3	3	2

及格率统计
ID	课程名	及格人数	总人数	及格率
1	Java	11	14	79.00%
2	html	8	12	67.00%
3	javascript	8	11	73.00%
3、以学生权限登录：
1）学生选课：
	以学生张三为例：
 
是否选择	课程名	教师
 
Java	张平
 
html	张平
 
javascript	张平
 
python	欧阳锋
 
spark	欧阳锋
 
hadoop	杨过
 
ruby	杨过
 
jdbc	黄蓉
 
css	黄蓉
 
Hibernate	黄蓉

2）统计查询：
 

课程名	分数
Java	78.0
html	87.0
javascript	68.0
python	98.0
spark	87.0
hadoop	51.0
ruby	76.0
jdbc	86.0
六、后端项目功能实现
1、项目搭建
1)	创建项目（dynamic Web project）studentcoursemanager
2)	建包
a)	com.entity(model)：student实体、teacher实体、课程实体等
b)	com.dao（Data Access Object 数据访问对象）操作数据库
c)	com.utils:工具包
d)	com.servlet(web\action\controller)：存放servlet项目的文件
e)	com.service(biz)：存放业务逻辑的
3)	编码
配置数据库连接文件db.properties （JDBC连接数据库）
driverClassName=com.mysql.jdbc.Driver
url=jdbc:mysql://127.0.0.1:3306/studentcoursemanager?useUnicode=true&characterEncoding=UTF-8&serverTimezone=Asia/Shanghai
username=root
password=root

加载db.properties配置文件
建立数据库连接，返回数据源
2、前端界面
1)	登录页面login.html
2)	首页：index.html
3)	列表页面：list.html
4)	新增或修改页面：add.html/edit.html
3、功能设置
管理员：
1）学生管理：CURD
2）老师管理：CURD、（老师课程设置）
3）课程管理：CURD
4）统计查询：（及格率、每个科目等等统计）
老师：
5）登录
6）录入分数
a)	先查询自己所教的课程(管理员已经设置过了)
b)	查询所教课程下的学生（学生角色选课的过程，学生登录后做选课）
c)	最后录入评分,提交即可（老师角色评分即可）
7）查询统计（统计及格率、所教科目统计等等）
学生：
8）登录
a)	登录操作
9）选课
a)	查询所有的课程
b)	选课其实就是选择老师（因为课程关联老师）
10）考试（考试系统…），老师录入分数之后。（6b步骤）
11）查询考试成绩、查询排名等
示意流程图：
 

4、前端列表展示分页实现
分页：数据库分页查询语句+掌握jsp+java等综合技术
常见第一种
 
常见第二种
 

常用分页技术：
内存分页：一次性将数据查询出来放入内存，然后进行分页，每页的数据都是在内存中存储，所以查询效率高。适用于小数据量，要求查询效率较高。
数据库分页：每次从数据库中查询出来一次的数据，然后放入内存，如果点击下一页，则重新从数据库查询下一页数据放入内存，上一页内存数据就被GC回收。适用于数据量较大的，查询效率较低。
分页技术点
 
页面大小(PageSize)：已知设置的10；
总记录条数（TotalCount）数据库查询而来；
总页数(totalPage)：TotalCount /pageSize = 85; 
如果：totalCount%pageSize!=0  +1
如果：totalCount%pageSize==0  +0
页码数（PageNo）：默认为1，
下一页 pageNo+1（尾页的时候，不加1了），
上一页pageNo-1（首页的时候不减1）
尾页：pageNo = totalPage
首页：pageNo = 1
5、列表中组合条件查询
组合条件：一个条件、两个条件、三个及其以上
输入几个条件，按照条件查询结果（满足查询的条件与）。
组合条件查询出来的结果是&&的关系
-- 按照ID查询
select * from student  where stuId = 1
-- 当前端录入学生姓名的时候
select * from student  where stuName like '%2%'
-- 当前端录入姓名与学号的时候 ，执行的如下SQL
select * from student  where stuName like '%2%' and stuNO like '%1%'
-- 通常情况下：字符串都按照like 模糊查询较多，数字：（=或者范围居多）
6、查询统计
1）	数据库数据录入
2）	查询统计
a)管理员-成绩区间统计
科目	<60）	[60-70]	(70-85]	(85-100]
Java	1	10	5	6
Html	1	10	5	6
Javascript	1	10	5	6
b)管理员-及格率
科目	及格率	参加考试人数
Java	72%	10
Html	75%	10
Javascript	84%	10
c)老师-成绩区间统计(所教科目)
科目	<60）	[60-70]	(70-85)	(85-100]
Java	1	10	5	6
d)老师-及格率
科目	及格率	参加考试人数
Java	72%	10
e)老师/学生-排名（查询）
f)学生-自己分数

七、总结
上面部分大体上测试了学生选课管理系统的可行性，并且介绍了对本系统的测试方式，描述了一些简单的测试实例，由上面的结果可以知道，整个系统的设计都比较符合要求，大体上符合一开始在设计中提出的各种要求。
经过这一个学期对Javaweb的学习，以及对SSM后台管理项目的练习，我对主流的java后台项目的搭建使用更加顺手了。在设计这个java学生选课后台管理系统的时候我学到了许多新知识，如使用PowerDesign数据模工具对数据库逻辑结构的建立，转换为物理模型，然后连接到MYSQL，再进行视图、触发器和存储过程的设计等。在使用过程中，查阅了不少资料，包括网上和书籍等，锻炼了我的自学能力！

八、参考文献
[1]张磊，丁香乾.Java Wbe程序设计.电子工业出版社，2015 581-121. 
[2]李兴华.Java开发实战经典，2014 108-180.  
[3]李兴华.Java Web开发实战经典基础篇，2016  124-220. 
[4]Java学习路线图.Java经典编程300例，明日科技 2018 56-78. 
[5]侯天超 Web编程基础，2018 52-78.  
[6]范春晓.JSP动态网站开发技术[J].中国科技博览, 2016 58-92.
