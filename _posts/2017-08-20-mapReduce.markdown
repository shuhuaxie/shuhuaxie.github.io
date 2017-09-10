---
layout: post
title:  "mapReduce"
date:   2017-09-02 16:51:30 +0800

---
* mapReduce 是为了对现有的批量数据处理,进行分布式升级的算法,将1个任务拆分为数十数百个任务进行分布式计算后合并结果
         计算KV细化拆分                相同结果K值合并
              Map<K21,V21> -> Map<K31,V31>
Map<K1,V1> -> Map<K22,V22> -> Map<K31,V31>  ->Map<K41,V41>
              Map<K23,V23> -> Map<K31,V31>
* MapReduce的HelloWorld解析
    初始文本:                    分行 ->取小范围结果
    Hello World Bye World       Hello,1 World,1 Bye,1 World,1
    Hello Hadoop Bye Hadoop  -> Hello,1 Hadoop,1 Bye,1 Hadoop,1   ->合并结果 <Bye,3> <Hadoop,4> <Hello,3> <World,2>
    Bye Hadoop Hello Hadoop     Bye,1 Hadoop,1 Hello,1 Hadoop,1


