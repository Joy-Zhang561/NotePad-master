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
    添加时间戳功能：
    1.添加时间戳的位置在主页面的每个列表项中添加，即在notelist_item.xml布局文件中添加一个<TextView><br>
       
  <TextView
        android:id="@android:id/text2"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:textAppearance="?android:attr/textAppearanceLarge"
        android:gravity="center_vertical"
        android:paddingLeft="5dp"
        android:singleLine="true"
        />
  
        
    2.在NoteList类的PROJECTION中添加COLUMN_NAME_MODIFICATION_DATE字段(该字段在NotePad中有说明)<br>
    
   private static final String[] PROJECTION = new String[] {  
            NotePad.Notes._ID, // 0  
            NotePad.Notes.COLUMN_NAME_TITLE, // 1  
            NotePad.Notes.COLUMN_NAME_MODIFICATION_DATE,//在这里加入了修改时间的显示  
    };  
   
    
    3.修改适配器内容，增加dataColumns中装配到ListView的内容，所以要同时增加一个ID标识来存放该时间参数。<br>
      
  String[] dataColumns = { NotePad.Notes.COLUMN_NAME_TITLE,  
        NotePad.Notes.COLUMN_NAME_MODIFICATION_DATE //增加时间参数} ;  
  int[] viewIDs = { android.R.id.text1 ,android.R.id.text2};  
  
    4.在NoteEditor文件的updateNote方法中获取当前系统的时间，并对时间进行格式化<br>
    
   // Sets up a map to contain values to be updated in the provider.   
      ContentValues values = new ContentValues();  
        Long now = Long.valueOf(System.currentTimeMillis());  
        SimpleDateFormat sf = new SimpleDateFormat("yy/MM/dd HH:mm");  
        Date d = new Date(now);  
        String format = sf.format(d);  
        values.put(NotePad.Notes.COLUMN_NAME_MODIFICATION_DATE, format);  
        
      5.显示结果为 
      
   ![](https://github.com/Joy-Zhang561/NotePad-master/row/master/Picture/1.1.png)
  
