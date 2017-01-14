---
layout: post
title:  Alfred blogging workflow for farbox.com
date:   2014-07-08 13:15:56 +0800
tags: [technote]
---

最近需要記錄一些 tech notes (其實一直都需要)，只是因為自己的幾點小要求，一直沒有找到順手的工具:

* [Markdown](//daringfireball.net/projects/markdown/) based
* Platform independent, 最好是 GIT 或 Dropbox-based, 這樣我可以結合 [Alfred](//www.alfredapp.com) 簡化發佈的流程
* 作為 no zou no die 的死 tech 佬，整個 workflow 必須高大上
* 確定一定以及肯定必須得便宜得要死甚至免費

好吧，經過這些作死的 filters, Evernote, OneNote 還有 App Store 裏面那些死貴死貴的好貨爛貨們，都直接篩掉了。剩下 [GitHub Pages](//pages.github.com) 這類的 static blogging platform, 幾經周折和一些眾所周知你懂我懂的原因，決定上 [FarBox](//www.farbox.com), 作為一直崇洋媚外看不上國貨軟件的臭小資這次表示很驚訝，一個字：很好用！很強大！很方便！

小折騰完後，決定寫個 Alfred workflow 簡化整個 Blogging 流程，以後寫 tech notes 會方便很多。Blogging.alfredworkflow 主要做這些事兒:

* 在 $HOME/Dropbox/Apps/FarBox/${Your-Site-Folder}/ 下創建 date-based 的 post (格式為 %Y-%m-%d-${title}.md)
* 在新建的 blog post 中自動設定以下 meta data:
	* Title (通過 Alfred "post ${title}" 獲取, 已去除前後空格)
	* Date (默認設定為當前的日期、時間，格式為 %Y-%m-%d %H:%M:%S)
	* Tags (請自便...)
	* Url (默認為 /%Y/%m/%d/${title}, 這樣可以省去在 Dropbox 下硬性使用目錄映射 Url, 提高靈活性, 當然如果你不喜歡，也請自便...)
* 使用相應的編輯器打開剛才創建的 blog post，我的順序是:
	* /Applications/Byword.app
	* /Applications/MacVim.app
	* vim

好了，完事兒了。現在寫 tech notes 只需激活 [Alfred](//www.alfredapp.com), 鍵入:

	post 文章抬頭

Blogging.alfredworkflow 就會為你在 [FarBox](//www.farbox.com)/[Dropbox](//www.dropbox.com) 下建立新的 blog post 然後用你 (預先設定) 的編輯器打開它了。

NOTES:
* 關於 Blogging.alfredworkflow 你必須要更改的:
	* 導入 Blogging.alfredworkflow 後你必須在 Script 部分把 *Site* 更改為你自己的 *FarBox Site Folder*
* 關於 Blogging.alfredworkflow 你可以選擇更改的 (pretty much anything actually...):
	* Preferable editors
	* Meta data

Blogging.alfredworkflow 地址:
[https://github.com/jimzhan/alfred-workflows](https://github.com/jimzhan/alfred-workflows)
