---
layout: post
title:  "2019-12-22-Flutter Widget.markdown"
date:   2019-12-22 12:11:30 +0800

1. StatelessWidget
对RenderObjectWidget和StatefulWidget的简单封装.
1) Container
将一个Widget分解成多个串联的Widget, Align/Padding/LimitedBox
2) GestureDetector
RawGestureDetector的封装
3) SingleChildScrollView
_SingleChildViewport,Scrollable,
2. StatefulWidget
拥有更多生命周期,通过更新来提高效率,由于会对包含的Widget造成影响,应该
将Widget尽量放低
3. RenderObjectWidget
RenderPositionedBox createRenderObject(BuildContext context) 
void updateRenderObject(BuildContext context, RenderPositionedBox renderObject)
SingleChildRenderObjectWidget
Align
// 使用performLayout(),修饰child的位置和尺寸


// TODO 关系
 
 
RenderObject //layout    