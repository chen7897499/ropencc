
ropencc
=======
ropencc is a project for conversion between Traditional and Simplified Chinese, wrapper in ruby.

繁简转换的程序，看似简单，但一研究起来，却真的不简单。其中一个难点是繁简汉字之间往往不能一一对应

例如：瞭解 -> 了解 瞭望 -> 瞭望；“標準”繁換簡是“标准”，但“标准”簡換繁卻是“標准”

还有若干语言习惯的问题，例如同一个地名的称呼就不一样，就不一一列举了

而 Open Chinese Convert（OpenCC）「开放中文转换」，是一个致力于中
文简繁转换的项目，由清华大学的 [BYVoid](http://www.byvoid.com/blog/about/) 提供高质量词库和函数库(libopencc)。<a href='https://github.com/BYVoid/OpenCC'>更多介紹</a>。

Install
-------
1. 先安装 libopencc

    Ubuntu

    如果你正在使用Ubuntu 10.10 (Maverick) 以上的版本，opencc已經被加入到了官方源中，使用

        sudo apt-get install opencc
        sudo apt-get install libopencc-dev

    如果你更願意體驗最新的版本，請使用ppa：

        sudo add-apt-repository ppa:byvoid-kcp/ppa
        sudo apt-get update
        sudo apt-get install opencc
        sudo apt-get install libopencc-dev


    Mac OS X

    使用 brew 安装

        brew install opencc

    更多 libopencc 安装介绍请查看： <https://github.com/BYVoid/OpenCC>

2. 安装 ropencc

        gem install ropencc

预设配置文件
-----

* `s2t.json` Simplified Chinese to Traditional Chinese 簡體到繁體
* `t2s.json` Traditional Chinese to Simplified Chinese 繁體到簡體
* `s2tw.json` Simplified Chinese to Traditional Chinese (Taiwan Standard) 簡體到臺灣正體
* `tw2s.json` Traditional Chinese (Taiwan Standard) to Simplified Chinese 臺灣正體到簡體
* `s2hk.json` Simplified Chinese to Traditional Chinese (Hong Kong Standard) 簡體到香港繁體（香港小學學習字詞表標準）
* `hk2s.json` Traditional Chinese (Hong Kong Standard) to Simplified Chinese 香港繁體（香港小學學習字詞表標準）到簡體
* `s2twp.json` Simplified Chinese to Traditional Chinese (Taiwan Standard) with Taiwanese idiom 簡體到繁體（臺灣正體標準）並轉換爲臺灣常用詞彙
* `tw2sp.json` Traditional Chinese (Taiwan Standard) to Simplified Chinese with Mainland Chinese idiom 繁體（臺灣正體標準）到簡體並轉換爲中國大陸常用詞彙

Usage
-----

简转繁 (Simple Interface)

    Ropencc.conv('s2t.json', str)

繁转简 (Simple Interface)

    Ropencc.conv('t2s.json', str)

简转繁 (File-Class like Interface)

    Ropencc.open 's2t.json' do |cc|
        rs = cc.convert '新年快乐'
        assert_equal '新年快樂', rs
    end

繁转简 (File-Class like Interface)

    Ropencc.open 't2s.json' do |cc|
        rs = cc.convert '新年快樂'
        assert_equal '新年快乐', rs
    end


附：libopencc 作者简介
--------------------
BYVoid，清華大學計算機系二零一零級本科生，清華大學學生網絡管理委員會副會長，現於微軟亞洲研究院系統組實習。

出生於1991年末，年十九歲，河南安陽人。熱愛計算機科學、語言學、漢語音韻學。能說有入聲的老派安陽話，會用簡繁體流暢地閱讀書寫，能夠辨析漢字簡繁正異用法。認爲「正體字」不等於「臺灣正體字」，支持傳統正體字回歸主流，主張廢除簡體字， 希望陸、港、澳、臺、日、韓、越早日實現漢字統一。
