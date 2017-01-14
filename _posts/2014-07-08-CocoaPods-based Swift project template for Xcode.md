---
layout: post
title:  CocoaPods-based Swift project template for Xcode
date:   2014-07-08 14:55:09 +0800
tags: [technote]
---

事情是這樣的, Apple 良心發現發佈了自已的 [Swift](//developer.apple.com/swift/ "Swift"), 而我需要在 [Swift](//developer.apple.com/swift/ "Swift") 中使用 [CocoaPods](//cocoapods.org/) (確切來說應該是在 [Swift](//developer.apple.com/swift/ "Swift") 中使用 Objective-C 和 C), 而據我所知目前只有兩種方法:

* Hack Podfile (通過 module.map)
* 使用官方推薦的 [Bridging-Header.h](//developer.apple.com/library/prerelease/ios/documentation/Swift/Conceptual/BuildingCocoaApps/MixandMatch.html)

第一種看似方便的 Hacking 用下來發現會出現一堆詭異且隨機的事情，更新 Pods 後還得經常手動刪除 ModuleCache, 而且也不被 [CocoaPods](//cocoapods.org/) 官方所推薦。於是俺決定做回良民使用第二種，但很快又發現每次新建一個 Project 都這麼幹的話，煩的要死不說，而且還容易出錯 (Typo 什麼的最討厭了)。作為 no zou no die 星人，只好祭出 customise 自己的 Project Template 這一大招一勞永逸的解決這煩人的問題，實際用下效果不錯而且一路順風順水，那些詭異又隨機的錯誤也再沒有出現過，實為居家旅行必備良藥。

CocoaPods Application.xctemplate 的說明:

* 繼承自 com.apple.dt.unit.emptyApplication, SDK platform 為 iphoneos
* 自動創建 *Podfile* 和 *Bridging-Header.h* 並加入 *Supporting Files* 組內
* 自動將 *Building Settings* 中 *SWFIT_OBJC_BRIDGING_HEADER* 指向 *Supporting Files* 下的 *Bridging-Header.h* 而無須再手動設定

CocoaPods Application.xctemplate 的使用:

* git clone 下來放到你認為合適方便的目錄, 如 $HOME/Dropbox/repos
* ln -s "$HOME/Library/Developer/Xcode/Templates/Project Templates/iOS/Application/CocoaPods Application.xctemplate" \<Your-cloned-location\>
* 新建 CocoaPods project 後照常 pod install 然後打開 *\<Your-Project\>.xcworkspace*
* 在 *Supporting Files/Bridging-Header.h* 中直接導入需要 expose 給 Swift 的 libraries 即可

CocoaPods Application.xctemplate 在這裏:  [github.com](//github.com/jimzhan/dotfiles/tree/master/Xcode/Templates/Project%20Templates/iOS/Application/CocoaPods%20Application.xctemplate)

That's it, 歡迎拍磚 :-)
