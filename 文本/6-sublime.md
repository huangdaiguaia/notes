###Sublime

- **1.下载原安装包**
- **2.（汉化）**
- **3.注册码**

***
	—– BEGIN LICENSE —–
	Ryan Clark
	Single User License
	EA7E-812479
	2158A7DE B690A7A3 8EC04710 006A5EEB
	34E77CA3 9C82C81F 0DB6371B 79704E6F
	93F36655 B031503A 03257CCC 01B20F60
	D304FA8D B1B4F0AF 8A76C7BA 0FA94D55
	56D46BCE 5237A341 CD837F30 4D60772D
	349B1179 A996F826 90CDB73C 24D41245
	FD032C30 AD5E7241 4EAA66ED 167D91FB
	55896B16 EA125C81 F550AF6B A6820916
	—— END LICENSE ——

- **4.鼠标菜单右键**
    + win+R
    + regedit
    + HKEY_CLASSES_ROOT\*\shell\Sublime\command
    + "D:\Program Files (x86)\Sublime Text 3\Sublime Text 3.exe""%1"
    + "安装路径\Sublime Text 3.exe"//这个引号有时候不需要
    + "%1"使得打开的是编辑的文件 而不是只打开软件

- **5.安装Package Control**
    + https://packagecontrol.io/installation#st3
    复制代码
    + import urllib.request,os,hashlib; h = 'df21e130d211cfc94d9b0905775a7c0f' + '1e3d39e33b79698005270310898eea76'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
    + 在sublime中查看\开启控制台,黏贴代码
    + 重启sublime

- **6.命令**
    + ctrl+shift+p --打开命令面板
    + pci --Package Control: Install Package 缩写
    + remove --Package Control: Remove Package 缩写

- **7.插件**

	+ **主題**
		* Agila          [oceanic next][Markdown 正数第二 倒数第三]
		* Spacegray      [第三个]
		* Material Theme [第三 第四个]
		* Flatland

    + **emmet**代码补全等强大功能
    	+ 更強大的补全功能;sublime也自带了一些补全功能;

    - **vintageES**
    	+ 更強大的vi;Vintage插件是sublime自带的插件，默认是忽略掉的;

    - **SideBarEnhancements**
    	+ 使用浏览器快捷预览网页

    - **SublimeTmpl**
    	+ 新建模板
    	+ 在Preferences->Browse Packages找到SublimeTmpl
    	+ 修改templates文件夹下的文件html.tmpl
    	+ Open all with current extension as....HTML
        * ctrl+shift+p会跳出一个框，在框内输入html set syntax HTML 设置文件格式
    	+ ctrl+s时 写上后缀名 eg: test.md

***
	首选项\Package Settings\SublimeTmpl\Menu-User
    [
        {
            "id": "file",
            "children":
            [
                {
                    "id": "sublimetmpl",
                    "caption": "New File (SublimeTmpl)",
                    "children":
                    [
                        {
                            "id": "Markdown",
                            "caption": "Markdown",
                            "command": "sublime_tmpl",
                            "args": {
                                "type": "md"
                            }
                        }
                    ]
                }
            ]
        }
    ]

***
	首选项\Package Settings\SublimeTmpl\Settings-User
	{
	    "markdown": {
	        "syntax": "Packages/Markdown/Markdown.tmLanguage",
	        "extension": "md"
	    }
	}
   
*** 
- **7.插件**
    + **MarkdownEditing**
    	+ 必須在不打开Markdown的情况下再次安装。

    - **OmniMarkupPreviewer**
    	+ 关于OmniMarkupPreviewer 404
    	+ Sublime Text > Preferences > Package Settings > OmniMarkupPreviewer > Settings - User

    ```
    {
        "renderer_options-MarkdownRenderer": {
            "extensions": ["tables", "fenced_code", "codehilite"]
        }
    }
    ```

    - **ColorHighlighter**
    	* Color Highlighter有自带的Color Picker 故不用单独装colorPicker。
    	* 选中颜色，右键菜单中选择Choose Color

    ```
    {
      "ha_style": "none",
      "ha_icons": true,
      /*"ha_style": "default"//default Filled outlined none underlined colored text
      "ha_style": #000 本身填充
      "ha_icons": 序号前面的小圆点*/
    }
    ```

    - **Guttercolor**
    	* 需要安裝ImageMagick
    	* [配置系统环境变量Path: D:\Program Files\ImageMagick-7.0.6-Q16]
    	* "ha_icons": true, ColorHighlighter的这个设置很重要

    - **HTML-CSS-JS Prettify**
    	* 需要node.js *没装*
    	* 就不用单独装 JsFormat (javascript代码格式化)
    	* Alignment 选中要调整的行，然后按 Ctrl + Alt + A（代码对齐） *没装*

    - **Pretty JSON** *没用?*
    	* 格式化出漂亮的json
    	* 默认快捷键：ctrl + shift + f



####写设置文件时注意命令之间的','[好像没关系了]

1. 首选项\用户设置

<!--  -->

    {
      "fade_fold_buttons":false,
      "auto_find_in_selection": true,
      "bold_folder_labels": true,
      "color_scheme": "Packages/Theme - Spacegray/base16-ocean.dark.tmTheme",
      "default_encoding": "UTF-8",
      "default_line_ending": "unix",
      "draw_minimap_border": true,
      "ensure_newline_at_eof_on_save": true,
      "font_size": 17,
      "highlight_modified_tabs": true,
      "ignored_packages":
      [
      ],
      "save_on_focus_lost": true,
      "trim_trailing_white_space_on_save": true,
      "update_check": false,
      "vintage_start_in_command_mode": true,
      "word_wrap": "true"
    }



2. 首选项\用户热键设置

<!--  -->

    [
      //vim esc jj
      { "keys": ["j","j"], "command": "exit_insert_mode",
        "context":
        [
          { "key": "setting.command_mode", "operand": false },
          { "key": "setting.is_widget", "operand": false }
        ]
      },

      { "keys": ["j","j"], "command": "hide_auto_complete", "context":
        [
          { "key": "auto_complete_visible", "operator": "equal", "operand": true }
        ]
      },

      { "keys": ["j","j"], "command": "vi_cancel_current_action", "context":
        [
          { "key": "setting.command_mode" },
          { "key": "selection_empty", "operator": "equal", "operand": true, "match_all": false },
          { "key": "vi_has_input_state" }
        ]
      },


      //SideBarEnhancements 浏览器快捷键打开(当用很多浏览器测试时)
      // {"keys": ["f12"],"command": "open_in_browser"}
      //chrome
      {"keys": ["f12"],
          "command": "side_bar_files_open_with",
          "args":{
                  "paths": [],
                  "application": "C:/Program Files (x86)/Google/Chrome/Application/chrome.exe",
                  "extensions": ".*"
                }
      },
      //ie
      {"keys": ["ctrl+alt+i"],
          "command": "side_bar_files_open_with",
          "args":{
                  "paths": [],
                  "application": "C:/Program Files/Internet Explorer/iexplore.exe",
                  "extensions": ".*"
                }
      },
      // firefox
      {"keys": ["ctrl+alt+f"],
        "command": "side_bar_files_open_with",
        "args":{
                  "paths": [],
                  "application": "D:/Program Files (x86)/Mozilla Firefox/firefox.exe",
                  "extensions":".*"
                }
      },

      //SublimeTmpl markdown
        {
            "keys": ["ctrl+alt+m"], "command": "sublime_tmpl",
            "args": {"type": "md"}, "context": [{"key": "sublime_tmpl.md"}]
        }
    ]



3. 首选项\更多设置\用户语法设置[Markdown.sublime-settings]
   首选项\Package Settings\Markdown Editing\Markdown GFM Settings-User

<!--  -->

    {
      "highlight_line": false,
      "color_scheme": "Packages/Monokai Extended/Monokai Extended.tmTheme",
    }


**注:**

    trim_trailing_white_space_on_save，自动移除行尾多余空格，处女座更安心了。

    ensure_newline_at_eof_on_save，文件末尾自动保留一个空行，懂的人自然知道它的用处。

    font_face 设置字体。Microsoft YaHei Mono 是一款混合字体，专为代码优化，看起来很舒服。当然你也可以使用你自己喜欢的字体，或者删掉本行，使用默认字体。

    disable_tab_abbreviations 设置为 true ，禁用 Emmet 的 tab 键功能（请使用 ctrl+e），系统自带的 tab 功能还是可圈可点的。当然你也可以不设置它，以完全使用 Emmet 的 tab 补全功能。

    translate_tabs_to_spaces 很明白就是把代码 tab 对齐转换为空格对齐，

    tab_size 配合设置空格数。这个需求因人而异了，不喜欢可以去掉。

    draw_minimap_border，用于右侧代码预览时给所在区域加上边框，方便识别。

    save_on_focus_lost，窗口失焦立即保存文件，嘛嘛再也不用担心你忘记保存了。

    highlight_line，当前行高亮。

    word_wrap，设置自动换行。

    fade_fold_buttons，默认显示行号右侧的代码段闭合展开三角号。

    bold_folder_labels，侧边栏文件夹显示加粗，区别于文件。

    highlight_modified_tabs，高亮未保存文件。

    default_line_ending: “unix”，使用 unix 风格的换行符。

    auto_find_in_selection: true ，开启选中范围内搜索（而不是整个文档

    translate_tabs_to_spaces :true，Tab转空格

    word_separators:true , 词的分符隔定义，加入中文符号

    "ignored_packages":
    [
    ]
    开启vi功能

    "vintage_start_in_command_mode": true    vi编辑器打开时为命令模式

    "default_encoding": "UTF-8",  设置默认编码格式为UTF-8

    "update_check": false,  禁止自动更新
