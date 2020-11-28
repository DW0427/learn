# 概念 #

## DevOps ##

DevOps = Development + Operations   开发&运维

DevOps是一组过程、方法与系统的统称，用于促进开发（应用程序/软件工程）、技术运营和质量保障（QA）部门之间的沟通、协作与整合。

![img](https://bkimg.cdn.bcebos.com/pic/0b55b319ebc4b745dfdcdd5acdfc1e178a821535?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2U4MA==,g_7,xp_5,yp_5)

![img](https://img2018.cnblogs.com/blog/1283669/201910/1283669-20191012104743427-979298839.png)



## CI/CD ##

核心概念：持续集成，持续交付，持续部署

面向开发和运营团队，主要针对在集成新代码时所引发的问题 **“集成地狱”**

具体含义取决于**CI/CD 管道**的自动化程度

本地修改代码并保存 => CI/CD自动化工具 => 应用更新（比如Android / IOS开发？）

开发阶段：编码 => 构建 => 集成 =>测试 => 交付 => 部署

![img](https://user-gold-cdn.xitu.io/2019/5/24/16ae580b279b80aa?imageslim)

![CI/CD 流程](https://www.redhat.com/cms/managed-files/ci-cd-flow-desktop_1.png)

### 持续集成（Continuous Integration, CI） ###

代码变更 => 触发自动化工具执行代码检测 => 及早暴露问题

在持续集成中，开发人员将会频繁地向主干提交代码，经过编译和自动化测试流进行验证后，才把新提交代码最终合并到主干上

持续集成是在源代码变更后自动检测、拉取、构建和（在大多数情况下）进行单元测试的过程。持续集成的目标是快速确保开发人员新提交的变更是好的，并且适合在代码库中进一步使用

CI的流程执行和理论实践让我们可以确定新代码和原有代码能否**正确地集成**在一起

![img](https://img2018.cnblogs.com/blog/1283669/201910/1283669-20191018120400821-1892663756.png)

### 持续交付（Continuous Delivery, CD） ###

通常是指开发人员对应用的更改会自动进行错误测试并上传到存储库（如 [GitHub](https://redhatofficial.github.io/#!/main) 或容器注册表），然后由运维团队将其部署到实时生产环境中 **MANUAL**

持续交付的目的就是确保尽可能减少部署新代码时所需的工作量

![img](https://img2018.cnblogs.com/blog/1283669/201910/1283669-20191018120739237-1487958277.png)

### 持续部署（Continuous Deployment, CD） ###

指的是自动将开发人员的更改从存储库发布到生产环境，以供客户使用 **AUTO**

持续部署以持续交付的优势为根基，实现了管道后续阶段的自动化

![img](https://img2018.cnblogs.com/blog/1283669/201910/1283669-20191018120910138-1707880496.png)

## DevOps & CI/CD ##

![img](https://img2018.cnblogs.com/blog/1283669/201910/1283669-20191018121053900-160882122.png)