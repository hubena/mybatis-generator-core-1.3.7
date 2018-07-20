To get up and running quickly with MyBatis Generator (MBG), follow these steps:

Create and fill out a configuration file appropriately. At a minimum, you must specify:
A <jdbcConnection> element to specify how to connect to the target database
A <javaModelGenerator> element to specify target package and target project for generated Java model objects
A <sqlMapGenerator> element to specify target package and target project for generated SQL map files
(Optionally) A <javaClientGenerator> element to specify target package and target project for generated client interfaces and classes (you may omit the <javaClientGenerator> element if you don't wish to generate Java client code)
At least one database <table> element
See the XML Configuration File Reference page for an example of a configuration file.

Save the file in some convenient location (like \temp\generatorConfig.xml)
Run MBG from the command line with a command like this:

      java -jar mybatis-generator-core-x.x.x.jar -configfile \temp\generatorConfig.xml -overwrite
    
This will tell MBG to run using your configuration file. It will also tell MBG to overwrite any existing Java files with the same name. If you want to save any existing Java files, then omit the -overwrite parameter. If there is a conflict, MBG will save the newly generated file with a unique name (e.g. MyClass.java.1).

After running MBG, you will need to create or modify the standard MyBatis or iBATIS configuration files to make use of your newly generated code. See the Tasks After Running MyBatis Generator page for more information.
Important: Generated code for iBATIS2 requires that statement namespaces are enabled in your iBATIS configuration. See the Tasks After Running MyBatis Generator page for more information.


中文：
要使用MyBatis Generator（MBG）快速启动并运行，请按照下列步骤操作：

适当地创建并填写配置文件。至少，您必须指定：
<jdbcConnection>元素，用于指定如何连接到目标数据库
一个<javaModelGenerator>元素，用于为生成的Java模型对象指定目标包和目标项目
<sqlMapGenerator>元素，用于为生成的SQL映射文件指定目标包和目标项目
（可选）<javaClientGenerator>元素，用于为生成的客户端接口和类指定目标包和目标项目（如果不希望生成Java客户端代码，可以省略<javaClientGenerator>元素）
至少一个数据库<table>元素
有关配置文件的示例，请参阅XML配置文件参考页面。

将文件保存在一个方便的位置（如\ temp \ generatorConfig.xml）
使用如下命令从命令行运行MBG：

      java -jar mybatis-generator-core-x.x.x.jar -configfile \ temp \ generatorConfig.xml -overwrite
    
这将告诉MBG使用您的配置文件运行。它还将告诉MBG覆盖任何具有相同名称的现有Java文件。如果要保存任何现有Java文件，请省略-overwrite参数。如果存在冲突，MBG将使用唯一名称（例如MyClass.java.1）保存新生成的文件。

运行MBG后，您需要创建或修改标准MyBatis或iBATIS配置文件以使用新生成的代码。有关详细信息，请参阅运行MyBatis Generator页面后的任务。
要点：为iBATIS2生成的代码要求在iBATIS配置中启用语句名称空间。有关详细信息，请参阅运行MyBatis Generator页面后的任务。

注意：
	使用mysql时报：
	java.sql.SQLException: The server time zone value ‘XXXXXX’ is unrecognized or represents more than one time zone.
	出现这个的原因是因为 mysql返回的时间总是有问题，比实际时间要早8小时。
	在jdbc连接的url后面加上serverTimezone=GMT即可解决问题，如果需要使用gmt+8时区，需要写成GMT%2B8。
	或者使用低版本的驱动。

命令为：java -jar mybatis-generator-core-1.3.7.jar -configfile generatorConfig.xml -overwrite