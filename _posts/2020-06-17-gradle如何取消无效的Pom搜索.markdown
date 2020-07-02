---
layout: post
title:  "2020-06-17-gradle如何取消无效的Pom搜索.markdown"
date:   2020-06-17 12:11:30 +0800

1. 问题说明
项目中引入了BaiduLBS_Android.jar和faceplatform-ui-release.aar等第三方jar,
每次gradle都会试图找这些jar的unspecified.pom造成时间浪费

2. 问题拆解






