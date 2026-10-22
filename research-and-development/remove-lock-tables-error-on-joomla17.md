---
title: "Joomla1.7后台出现LOCK TABLES的解决方法"
source: "http://www.joomla178.com/joomla-share/research-and-development/remove-lock-tables-error-on-joomla17.html"
category: "研究开发"
author: "Jiang"
date: "2011-12-07"
archived_at: "2026-10-22T11:56:29.930671+08:00"
---

# Joomla1.7后台出现LOCK TABLES的解决方法

joomla在升级1.7以后加入了LOCK TABLES 机制，在后台操作一些编辑工作的时候会出现Access denied for user xxxxx SQL=LOCK TABLES xxx的相关提示。

如果主机是自己的，可以修改mysql的配置来进行权限分配解决这个问题。但大多数用户的主机都是租的虚拟空间，这个问题只能从“软件”入手了。我只想出了用去掉LOCK TABLES机制这个方法解决它。

解决方法：

找到\libraries\joomla\database\table.php文件，找到1401行 一直注释到1407行，即：

```
/*if ($this->_db->getErrorNum()) {
  $this->setError($this->_db->getErrorMsg());
  return false;
  }
```

然后找到1421一直注释掉1432行，即：

```
/*// Unlock the table.
  $this->_db->setQuery('UNLOCK TABLES');
$this->_db->query();

// Check for a database error.
  if ($this->_db->getErrorNum()) {
  $this->setError($this->_db->getErrorMsg());
  return false;
}

$this->_locked = false;*/
```

保存后在进后台编辑就不会出现LOCK TABLES提示了，不过这么做存在一定风险，目前还不清楚。

---

除特殊标明文章转自第三方网站，文章均由JOOMLASK.COM原创提供  
欢迎友情转载，请务必保留本文出处并引用本文链接： [Joomla1.7后台出现LOCK TABLES的解决方法](http://www.joomla178.com/joomla-share/research-and-development/remove-lock-tables-error-on-joomla17.html)
