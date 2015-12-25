---
layout: post
title: 用数组为表单字段命名
tags: html form 
categories: CODE小习惯
---

为表单中字段命名时，选择数组方式，而不是简单字符串，以便后台分组处理。

html:
```html
<form>
    <input name="input1['name']" type="text">
    <input name="input1['passwd']" type="password">
    <input name="input2['name']" type="text">
    <input name="input2['passwd']" type="password">
    <input type="submit" value="submit">
</form>
```
php:
```php
$data1 = $_POST['input1'];
$data2 = $_POST['input2'];
```