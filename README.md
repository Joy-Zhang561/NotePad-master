# NotePad
期中项目总结报告
=====
项目源码介绍<br>
-----
主要的类：<br>
NotesList类 应用程序的入口，笔记本的首页面会显示笔记的列表 <br>
NoteEditor类 编辑笔记内容的Activity <br>
TitleEditor类 编辑笔记标题的Activity <br>
NoteSearch类 编辑查询笔记内容的Activity <br>
NotePadProvider 这是笔记本应用的ContentProvider，也是整个应用的关键所在 <br>
主要的布局文件：<br>
note_editor.xml 笔记主页面布局<br>
note_search.xml 笔记内容查询布局<br>
notelist_item.xml 笔记主页面每个列表项布局<br>
title_editor.xml 修改笔记主题布局<br>
主要的菜单文件：<br>
editor_options_menu.xml 编辑笔记内容的菜单布局<br>
list_context_menu.xml 笔记内容编辑功能菜单布局<br>
list_options_menu.xml 笔记主页面的菜单布局<br>
功能设计介绍
-----
添加时间戳功能：<br>
添加时间戳的位置在主页面的每个列表项中添加，即

