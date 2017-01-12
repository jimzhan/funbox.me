---
layout:     post
title:      "Programming Your Vim for Programming"
date:       2014-09-19 16:15:21 +0800
categories: technote, vim
---

最近開始把之前 [Python](//www.python.org/) 的各種 snippets 和 libraries 轉到 [Golang](//golang.org/), 試了幾個 plugins, 都不滿意，然後頭腦發熱又一次去試 [Sublime Text](//www.sublimetext.com/)。

平心而論這貨上手很順，編輯方面在熟悉了它的一些基本操作和快捷鍵後速度也並不慢。好吧，然後我假裝自己用得很開心的去找一些之前 Vim 下面用的順手的 plugins，最後卡在 file templates 上。找來找去只有 [FileHeader](//github.com/shiyanhui/FileHeader) 比較合適，可在 Vintagous 模式下用下來各種彆扭，加上 VI 模式下新建的文檔因為 paste off 問題会導致格式錯誤，這個問題以 [FileHeader](//github.com/shiyanhui/FileHeader) 的實現方式來說基本無解，要麼我就把自己所有的 templates 都改成有原生斷行的模式，要麼我自己去 hack Vintagous, 可兩樣我都不願意幹。後來又發現有個關於 *file_name* 獲取的小問題，我提了個 [Issue](//github.com/shiyanhui/FileHeader/issues/20)，可作者卻在還沒有解決的情況下就把它 closed 了，十二萬分汗, 這可不是做學問的態度啊親 (-__-")

咱還有 Vim 不是。認真想了想，發現我不爽的其實只是 [SPF13 Vim](//vim.spf13.com/) 而已。這貨入門很方便，如果你之前有過上千行的 *.vimrc*，你懂的。[SPF13 Vim](//vim.spf13.com/) 或 [Janus](//github.com/carlhuda/janus) 這類的 Vim Distributions, 有著一堆別人覺得好的 plugins、key mappings, color schemes, 嗯呐，這其實已經和學習一個新的 IDE 差不了多少了啊親。

想了一想，自己用 Vim 已經將近十年了，與其費力將其他工具打造得更像它，還不如好好的利用它。好吧，折騰吧，in short, 這是結果:

![dotvim with VimFiler & Tagbar](http://github.com/jimzhan/.vim/raw/master/previews/dotvim.png)


dotvim 所包含的 plugins
=======================

### 插件管理

* [Shougo/neobundle](//github.com/Shougo/neobundle.vim): 基於 [gmarik/vundle](//github.com/gmarik/vundle) 但加入了更多強大的功能，還有詳細的 logs.


### 文件管理

* [scrooloose/nerdtree](//github.com/scrooloose/nerdtree): Vim 下最強樹形文件管理器，沒有之一，已經加了 [NERDTreeTabs](//github.com/jistr/vim-nerdtree-tabs) 來解決 NERDTree 單獨啟用時可能產生的視窗混亂問題，toggle 的快捷鍵默認設定如下。

{% highlight shell %}
map <C-o>   <plug>NERDTreeTabsToggle<CR>
{% endhighlight %}

* [kien/ctrlp](//github.com/kien/ctrlp.vim): 文件查找，Sublime Text control-p 的 copycat，簡單好用，查找路徑已設定為 NERDTree 當前打開結點.


### GIT

* [tpope/vim-fugitive](//github.com/tpope/vim-fugitive): GIT 管理，常用的快捷鍵設定如下。

{% highlight vim linenos %}
nnoremap <silent> <leader>gs :Gstatus<CR>
nnoremap <silent> <leader>gd :Gdiff<CR>
nnoremap <silent> <leader>gc :Gcommit<CR>
nnoremap <silent> <leader>gb :Gblame<CR>
nnoremap <silent> <leader>gl :Glog<CR>
nnoremap <silent> <leader>gp :Git push<CR>
nnoremap <silent> <leader>gw :Gwrite<CR>
nnoremap <silent> <leader>gr :Gremove<CR>
{% endhighlight %}

### Autocomplete

* [Shougo/neocomplete](//github.com/Shougo/neocomplete.vim) + [Shougo/neosnippet](//github.com/Shougo/neosnippet.vim):
自動補全，靠譜的 plugin 中數它最輕量了, 需要 Vim 有 lua 支持 ([YCM](//github.com/Valloric/YouCompleteMe) 這貨在我機器上編譯完 175MB...)。


### File Editing

* [scrooloose/nerdcommenter](//github.com/scrooloose/nerdcommenter): 塊注釋/反注釋，自適應文件類型。
* [jiangmiao/auto-pairs](//github.com/jiangmiao/auto-pairs): 自動補全/刪除括號。
* [terryma/vim-multiple-cursors](//github.com/terryma/vim-multiple-cursors): 多行選擇/編輯，也是 Sublime Text 的 copycat。
* [aperezdc/vim-template](//github.com/aperezdc/vim-template): 文件模版, 可自定模版路徑，這貨必備！


### Programming

* [fatih/vim-go](//github.com/fatih/vim-go): Golang 支持，已包括 gofmt, gocode 等常用功能。
* [mattn/emmet-vim](//github.com/mattn/emmet-vim): Zen Coding, 編輯 HTML/CSS 的話，你懂的。
* [majutsushi/tagbar](//github.com/majutsushi/tagbar): 源碼 Tags 顯示，需要 ctags 支持。
* [scrooloose/syntastic](//github.com/scrooloose/syntastic): 靜態語法檢查。


### Status Bar

* [bling/vim-airline](//github.com/bling/vim-airline): 狀態欄顯示，已啟用 Buffers List, 結合下面設定的快捷鍵, 不再需要單獨的插件(如 [MiniBufExpl](//github.com/fholgado/minibufexpl.vim)) 來管理 Buffers, 如此也避免了視窗跳轉時可能產生的問題。

{% highlight vim linenos %}
:nmap <C-l>     :bnext<CR>
:nmap <C-h>     :bprevious<CR>
:nmap <C-k>     :bdelete<CR>
{% endhighlight %}

### Color Scheme

* [tomasr/molokai](//github.com/tomasr/molokai): 這是目前為止我測試過能同時在 iTerm 和 Gvim 不經設定就能表示良好並一致的配色方案，也是 Sublime Text 的默認配色。


安裝 dotvim:

{% highlight bash linenos %}
curl -s https://raw.githubusercontent.com/jimzhan/.vim/master/setup | sh
{% endhighlight %}

[dotvim on Github](//github.com/jimzhan/.vim)
