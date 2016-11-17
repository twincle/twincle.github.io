[关爱八卦成长协会网站](http://www.guanba.com/)API接口说明（非官方）。

<!-- more -->

## 内容接口

### 文章列表（更新时间2016年8月18日）

GET http://api.guan.ba/index.php/mobileApp/article/list?UD=${}&contenttype=${}&count=${}&page=${}

#### 参数说明

##### UD

作用：未知

取值：留空

默认值：留空

##### contenttype

作用：定义八卦列表类型

取值：

- entertainment：娱乐八卦
- life：生活八卦

默认值：必填参数，无默认值

##### count

作用：定义列表文章数量

取值：number

默认值：10

##### page

作用：定义列表页数

取值：number

默认值：1

#### 返回值

```json
{
  data: [                         // 文章列表数组
    {
      article_id: string,         //
      audio: [any],               // 暂未确定数组元素类型
      author: {
        gender: string,           // 默认为unknow
        icon: string,             // 头像图片完整URL
        nickname: string,         //
        phone: string,            // 默认为空字符串
        uid: string               //
      },
      comment_count: number,      //
      coverimg: string,           // 默认为空字符串
      media: [any],               // 暂未确定数组元素类型
      pictures: [string],         // 图片完整URL
      source: string,             // 该字段未在页面显示
      summary: string,            //
      title: string,              //
      up_count: number|null,      // 该字段未在页面显示
      video: [any]                // 暂未确定数组元素类型
    },
    ...
  ],
  errCode: 0                      // 错误代码，目前仅返回0
}
```

### 文章内容（更新时间2016年8月18日）

GET http://api.guan.ba/index.php/mobileApp/article/detail?UD=${}&article_id=${}

#### 参数说明

##### UD

作用：未知

取值：留空

默认值：留空

##### article_id

作用：定义文章ID

取值：string

默认值：必填参数，无默认值

#### 返回值

```json
{
  data: {                         // 文章列表数组
    article_id: string,           //
    author: {
      gender: string,             // 默认为unknow
      icon: string,               // 头像图片完整URL
      nickname: string,           //
      phone: string,              // 默认为空字符串
      uid: string                 //
    },
    comment_count: number,        //
    content: string,              // 
    createtime: number,           // 毫秒数
    media: {
      audio: [any],               // 暂未确定数组元素类型
      pictures: [string],         // 图片完整URL
      video: [any]                // 暂未确定数组元素类型
    },
    source: string,               // 该字段未在页面显示
    summary: string,              //
    title: string,                //
    up_count: number|null         //
  },
  errCode: 0                      // 错误代码，目前仅返回0
}
```

### 文章评论（更新时间2016年8月18日）

GET http://api.guan.ba/index.php/mobileApp/comment/get_comment?UD=${}&article_id=${}&count=${}&page=${}

#### 参数说明

##### UD

作用：未知

取值：留空

默认值：留空

##### article_id

作用：定义文章ID

取值：string

默认值：必填参数，无默认值

##### count

作用：定义列表文章数量

取值：number

默认值：10

##### page

作用：定义列表页数

取值：number

默认值：1

#### 返回值

```json
{
  data: [                         // 文章列表数组
    {
      author: {
        gender: string,           // 默认为unknow
        icon: string,             // 头像图片完整URL
        nickname: string,         //
        phone: string,            // 默认为空字符串
        uid: string               //
      },
      comment_id: string,         //
      comment_to: {             // 该字段不一定存在
        gender: string,           // 默认为unknow
        icon: string,             // 头像图片完整URL
        nickname: string,         //
        phone: string,            // 默认为空字符串
        uid: string               //
      },
      content: string,            // 
      createtime: number,         // 毫秒数
      media: {
        audio: [any]              // 暂未确定数组元素类型
        pictures: [string]        // 图片完整URL
        video: [any]              // 暂未确定数组元素类型
      },
      up_count: number|null       // 
    },
    ...
  ],
  errCode: 0                      // 错误代码，目前仅返回0
}
```

### 评论对话

GET http://api.guan.ba/index.php/mobileApp/comment/get_dialogcomment?UD=&article_id=57b0588492cac5982e8b4577&count=30&page=1&commenter_id=57804aac92cac575268b4567&becommenter_id=57b2f49a92cac5a9238b4575

### 热门评论

GET http://api.guan.ba/index.php/mobileApp/comment/get_hotcomment?UD=&article_id=57b0588492cac5982e8b4577&count=30&page=1

### 作者评论

GET http://api.guan.ba/index.php/mobileApp/comment/get_authorcomment?UD=&article_id=57b0588492cac5982e8b4577&count=30&page=1&author_id=57804aac92cac575268b4567

（未完待续）