---
title: "Joomla! 1.5模板升级至Joomla! 2.5 教程"
source: "http://www.joomla178.com/joomla-share/joomla-templates-tutorials/joomla15-template-upgrade-to-joomla25.html"
category: "JOOMLA模板开发"
author: ""
date: "2012-08-31"
archived_at: "2026-10-22T11:56:29.930671+08:00"
---

# Joomla! 1.5模板升级至Joomla! 2.5 教程

Multithumb found errors on this page:  
  
There was a problem loading image http://www.abokuo.com/images/stories/articles/20120628\_j15\_template\_covert2\_j25/01-folder-copy.png  
There was a problem loading image http://www.abokuo.com/images/stories/articles/20120628\_j15\_template\_covert2\_j25/02-folder-comparision.png  
There was a problem loading image http://www.abokuo.com/images/stories/articles/20120628\_j15\_template\_covert2\_j25/03-template-details-xml.png  
There was a problem loading image http://www.abokuo.com/images/stories/articles/20120628\_j15\_template\_covert2\_j25/04-template-details-xml-02.png  
There was a problem loading image http://www.abokuo.com/images/stories/articles/20120628\_j15\_template\_covert2\_j25/05-template-details-xml1.png  
There was a problem loading image http://www.abokuo.com/images/stories/articles/20120628\_j15\_template\_covert2\_j25/06-del-params-xml.png  
There was a problem loading image http://www.abokuo.com/images/stories/articles/20120628\_j15\_template\_covert2\_j25/07-template-details-xml-add.png  
There was a problem loading image http://www.abokuo.com/images/stories/articles/20120628\_j15\_template\_covert2\_j25/08-template-details-xml-params.png  
There was a problem loading image http://www.abokuo.com/images/stories/articles/20120628\_j15\_template\_covert2\_j25/09-mootools-index.png  
There was a problem loading image http://www.abokuo.com/images/stories/articles/20120628\_j15\_template\_covert2\_j25/10-rename-link-index.png  
There was a problem loading image http://www.abokuo.com/images/stories/articles/20120628\_j15\_template\_covert2\_j25/11-discover-admin.png  
There was a problem loading image http://www.abokuo.com/images/stories/articles/20120628\_j15\_template\_covert2\_j25/12-discover-icon-admin.png  
There was a problem loading image http://www.abokuo.com/images/stories/articles/20120628\_j15\_template\_covert2\_j25/13-install-template.png  
There was a problem loading image http://www.abokuo.com/images/stories/articles/20120628\_j15\_template\_covert2\_j25/14-make-default.png

先简单概括一下升级步骤

本文以JOOMLA！ 1.5前台布景模板“rhuk\_milkyway”作为升级示范。升级流程分为5个阶段：   
 第1步：复制Joomla! 1.5中的模板文件夹  
 第2步：编辑文件结构。   
 第3步：编辑“templateDetails.xml”文件  
 第4步：编辑“index.php”文件  
 第5步：安装，测试升级后的模板

#### 一、复制 Joomla! 1.5 模板所有文件。

请先在 Joomla! 2.5 前台模板文件夹中新建新文件夹（例如“rhuk\_milkyway25”），接着把要升级的 Joomla!1.5 模板中的所有文件╱文件夹复制过去。

![复制文件夹內容](http://www.abokuo.com/images/stories/articles/20120628_j15_template_covert2_j25/01-folder-copy.png "复制文件夹內容")

复制文件夹內容

#### 二、编辑文件结构。

由于Joomla! 2.5 在模板的结构有所修改，在文件结构做新增与删除动作。

![编辑文件结构以符合 Joomla! 2.5 規定](http://www.abokuo.com/images/stories/articles/20120628_j15_template_covert2_j25/02-folder-comparision.png "编辑文件结构以符合 Joomla! 2.5 規定")

编辑文件结构以符合 Joomla! 2.5 规定

Step 01：删掉“params.ini”文件：Joomla! 2.5 的参数都改在数据库中。

Step 02：在“atomic”模板文件夹中复制“error.php”：“error.php” 是 Joomla! 2.5 模板中用来作为错误展示页面，你可从“atomic”这个模板中复制过来。

Step 03：新建文件“template\_preview.png”：“template\_preview.png”是作为较大张模板预览图片，请准备尺寸为 640 x 480 像素的 PNG 格式图片并命名为“template\_preview.png”。

#### 三、编辑“templateDetails.xml”文件

编辑“templateDetails.xml”文件已符合 Joomla! 2.5 在模板上的要求。

Step 01：修改 <install> 标签及参数为 <extension> 标签。

![扩展描述格式更改](http://www.abokuo.com/images/stories/articles/20120628_j15_template_covert2_j25/03-template-details-xml.png "扩展描述格式更改")

扩展描述格式修改

|  |  |
| --- | --- |
| 原内容 | 新内容 |
| <install version="1.5"... | <extension version="2.5"... |
| </install> | </extension> |

Step 02：修改 <name> 标签内容，例如修改为“rhuk\_milkyway25”。

![修改模板名称](http://www.abokuo.com/images/stories/articles/20120628_j15_template_covert2_j25/04-template-details-xml-02.png "修改模板名称")

修改模板名称

Step 03：将多个标签编辑为单一标签：如果有多个文件位于同文件夹中，在 Joomla! 2.5 不用一一列举，用一个标签统一管理。

![簡化文件敘述](http://www.abokuo.com/images/stories/articles/20120628_j15_template_covert2_j25/05-template-details-xml1.png "簡化文件敘述")

简化文件解释

Step 04：删除“params.ini”文件，新增“error.php”与“template\_preview.png”文件。

![刪除“params.ini”敘述](http://www.abokuo.com/images/stories/articles/20120628_j15_template_covert2_j25/06-del-params-xml.png "刪除“params.ini”敘述")

刪除“params.ini”

![新增 error.php, template_preview.png 敘述](http://www.abokuo.com/images/stories/articles/20120628_j15_template_covert2_j25/07-template-details-xml-add.png "新增 error.php, template_preview.png 敘述")

新增 error.php, template\_preview.png

Setp 05：编辑 <params> 标签及内容

![修改 params 標籤內容](http://www.abokuo.com/images/stories/articles/20120628_j15_template_covert2_j25/08-template-details-xml-params.png "修改 params 標籤內容")

修改 params 标签

|  |  |
| --- | --- |
| 原内容 | 新内容 |
| <params> | <config>  <fields name="params">  <fieldset name="advanced"> |
| <param... | < field... |
| </param> | </ field> |
| </params> | </fieldset>  </fields>  </config> |

#### 四、编辑“index.php”文件

完成“templateDetails.xml”文件修改，需要再修改“index.php”文件。

Step 01：增加 PHP 程序代码，加载 Mootools 函式库：在如下图所示位置加入“JHtml::\_('behavior.framework', true);”程序代码。

![加入 mootools 函式庫支援](http://www.abokuo.com/images/stories/articles/20120628_j15_template_covert2_j25/09-mootools-index.png "加入 mootools 函式庫支援")

加入 mootools JS库

Step 02：以 PHP 程序代码取代模板名称：在 Joomla! 2.5 可以自“templateDetails.xml”文件取得模板名称，不需要在“index.php”文件中写模板名字了。

![更改模板名称表示方式](http://www.abokuo.com/images/stories/articles/20120628_j15_template_covert2_j25/10-rename-link-index.png "更改模板名称表示方式")

编辑模板名称

|  |  |
| --- | --- |
| 原内容 | 新内容 |
| rhuk\_milkyway. | <?php echo $this->template ?> |

#### 五、安装、测试升级后的模板。

到此已完成模板修改工作，但是 Joomla! 2.5 模板管理中还无法识别，继续以下步骤。

Step 01：进入 Joomla! 2.5 后台，点击“扩展管理”，选择“检测”分页。

![前往“检测”分頁](http://www.abokuo.com/images/stories/articles/20120628_j15_template_covert2_j25/11-discover-admin.png "前往“检测”分頁")

进入“检测”

Step 02：选择工具栏上的“检测”图标。

![选择检测”圖示](http://www.abokuo.com/images/stories/articles/20120628_j15_template_covert2_j25/12-discover-icon-admin.png "选择检测”圖示")

选择检测

Step 03：扩展管理中会显示“rhuk\_milkyway25”模板，选择该模板后选择工具栏“安装”图标。

![安裝](http://www.abokuo.com/images/stories/articles/20120628_j15_template_covert2_j25/13-install-template.png "安裝")

安裝模板

Step 04：到“模板管理”画面将升级过后的模板设为默认。

![设为默认模板](http://www.abokuo.com/images/stories/articles/20120628_j15_template_covert2_j25/14-make-default.png "设为默认模板")

设为默认模板

本文译自[How to convert Joomla 1.5 template to Joomla 2.5 template](http://magazine.joomla.org/issues/Issue-May-2012/item/740-How-to-convert-Joomla-15-template-to-Joomla-25)一文

**转载请标明出处，请引用本文地址：[Joomla! 1.5模板升级至Joomla! 2.5 教程](joomla15-template-upgrade-to-joomla25.md)**

---

除特殊标明文章转自第三方网站，文章均由JOOMLASK.COM原创提供  
欢迎友情转载，请务必保留本文出处并引用本文链接： [Joomla! 1.5模板升级至Joomla! 2.5 教程](http://www.joomla178.com/joomla-share/joomla-templates-tutorials/joomla15-template-upgrade-to-joomla25.html)
