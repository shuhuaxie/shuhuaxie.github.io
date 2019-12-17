---
layout: post
title:  "2019-12-17-dart library.markdown"
date:   2019-12-17 12:11:30 +0800

1.  标准dart库声明

collections.dart
--------------------
library dart.collection;

import 'dart:_internal' hide Symbol;
import 'dart:math' show Random; // Used by ListMixin.shuffle.

part 'collections.dart';
part 'hash_map.dart';
part 'hash_set.dart';
part 'iterable.dart';
part 'iterator.dart';
part 'linked_hash_map.dart';
part 'linked_hash_set.dart';
part 'linked_list.dart';
part 'list.dart';
part 'maps.dart';
part 'queue.dart';
part 'set.dart';
part 'splay_tree.dart';


hash_map.dart
-----------------
part of dart.collection;

2. 关键字
part of,show ,hide ,as
 
 
    