---
layout: default
title: 这条裙子好看吗？
parent: archive
nav_order: 2
---

最近导师问了我一个问题：“监督学习和强化学习有什么区别？”他想搞明白为什么最近大热的人工智能领域有那么多的学习（机器学习，深度学习，监督学习，非监督学习，强化学习……）？为什么教机器人擦桌子的学习方法是强化学习而不是监督学习？对于已经熟知机器学习知识的大神们来说，这个问题也许有些荒谬。不过从我的角度来看，一个门外汉确实会被这些以“学习”二字结尾的名词搞到晕头转向。正巧，我之前想到了一个好例子，用来解释监督学习和强化学习的区别再合适不过了。

## 监督学习
假设你~~是一个二五仔，今天准备在家冲击韩服天梯3000分。燃鹅你~~的无线鼠标没电了，而家里又没有备用电池。~~没有鼠标还怎么干死黃旭东？~~于是你火速跑下楼，准备去小区对面的超市批发一把电池回来。就在你出小区门的时候，迎面走来了一位穿裙子的小姐姐。你心想“这条裙子还挺好看的”。<br/><br/>
那么问题来了，为什么你会觉得这条裙子好看？其实这就是你进行**监督学习**的后果。所谓的监督学习其实就是有那么个权威告诉你，扶摔倒的老奶奶是对的不扶是错的，红色的裙子好看绿色的裙子不好看，1加1等于2而2加2等于4……也就是说每一个事件都有一个明确的评判标准，而你在涉世未深的时候往往你的父母老师会扮演这个绝对权威的角色，告诉你每个事件所对应的标签是什么。久而久之，你就会在此基础上形成自己的人生观价值观以及每件事情的评判标准。好了，~~既然你是个二五仔，那么~~大哥孙一峰是你最爱的主播也就是你的绝对权威。他每天直播的时候给你看一套半蔵森林的写真并且告诉你这就是好看的标准。久而久之，你就形成了一套自己的审美标准。但是很显然你的审美标准是受到了大哥的深远影响的。既然小区门口的这个小姐姐的穿衣风格和你每天看的写真很相近，那么你也自然而然的觉得她身上的裙子好看了。这是你长期受到审美训练的结果（当然你如果完全没受到过审美训练，你也会根据自己的直觉做出判断的）。

![xiaojiejie]({{ site.baseurl }}/images/supervlrn_vs_reinflrn/bzsl_in_skirt.jpeg)
> 来源见水印

## 强化学习
第二天，你刚交的初恋女朋友叫你跟她去上街买衣服，你们俩一同前往小区门口搭车，没想到又遇到了昨天那个小姐姐穿着一条跟昨天差不多的裙子。这时，你的女朋友问出了这个堪比“我和你妈同时掉水里先救谁”的世纪难题：“这条裙子好看吗？”当然你经过了~~大哥的~~审美训练，你内心是觉得这条裙子好看的。于是你脱口而出：“好看！”<br/><br/>
那么恭喜你，遭中了啊！你女朋友甩下一句：“你觉得好看是吧？那你以后别看我了，你就专门看她吧！”说完转身走了，留下一脸懵逼的你风中凌乱了一整个周末。后来你好不容易~~用你升级显卡的钱~~请她吃了一顿米其淋三星才把她哄回来，并且你答应她这周末再陪她去逛街。<br/><br/>
一转眼周末到了，你们又去小区门口搭车，碰巧又遇见那个小姐姐穿着一条裙子出现在了小区门口。你女朋友又抛来那个问题：“这条裙子好看吗？”这回你有经验了，肯定不能实话实说了。于是你答到：“不好看不好看！”<br/><br/>
那么恭喜你，又遭中了啊！女朋友回过头来就是一句：“我上周穿的裙子就是她那样的，我当时问你好不好看，你说好看，没想到你是敷演我！你说我顔值满分肯定也是骗我的！”说完又转身走了，留下二脸懵逼的你雨中凌乱了一个周末。当然你又只好~~用你买新游戏主机的钱~~给她买了个包才把她哄回来。<br/><br/>
后来同样的剧情反复上演，“这条裙子好看吗”已经不再是监督学习的问题了。因为即便是全世界所有人（甚至包括你女朋友）都觉得那条裙子好看，但问出这个问题的人是你女朋友的时候，这条裙子好不好看已经不是问题的本质了。这时后你面对的就是一个**强化学习**的问题。你发现，这个问题其实没有一个所谓的正确答案，甚至你女朋友自己都不知道她想要的是什么答案。<br/><br/>
但是好在你的目标其实很明确，那就是不要惹你女朋友生气甚至是要哄她开心。当然，因为你是第一次谈女朋友，你一开始当然不知道该如何应对这样的问题，所以一开始你的回答只是随便乱说的。每次都以你女朋友被惹毛而告终。不过，虽然都是惹毛，你注意到有时候她的反应更加歇斯底里一些，有时候会相对平和一些。于是你开始调整你回答的策略，你会尽量以让她相对平和的回答为蓝本并做稍许改动做为你下一次的答案。 这样一来，只要你的钱包够大，经过反复的尝试，你就能掌握哄女朋友开心的正确姿势了。

![xiaojiejie]({{ site.baseurl }}/images/supervlrn_vs_reinflrn/man_look_other_girl_.jpg)
> https://www.cheatsheet.com/health-fitness/men-relationships-normal-to-have-a-wandering-eye.html/?a=viewall