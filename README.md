# 务必要坚持的原则

# 项目目前状况
>项目目前分iPad和iPhone两个项目
# 产品层面
# 代码层面
## 通用方法，以及注意的事项
### 颜色和字体设置  相关文件`LesoStyle.h `
这里和之前的设计同学吕晶出过一套代码和设计方案的对应，在标注图中给出对应的颜色和字体方案，客户端根据给出方案设置对应的颜色和字体方案；这依赖于设计相关同事的支持，望推行，目前搜索设计负责人是**张志囡**
```objc

typedef enum {
    LesoFontStyle_Title_LV1 = 1,
    LesoFontStyle_Title_LV2,
    LesoFontStyle_Text_LV1,
    LesoFontStyle_Text_LV2,
    LesoFontStyle_Text_LV3,
    LesoFontStyle_Text_Float_Title,
    LesoFontStyle_Text_Float_Message,
    LesoFontStyle_Button_LV1,
    LesoFontStyle_Button_LV2,
}LesoFontStyle;

typedef enum {
    LesoColorStyle_Title_LV1 = 1,
    LesoColorStyle_Title_LV1_WEAK,
    LesoColorStyle_Text_LV1,
    LesoColorStyle_Text_LV2,
    LesoColorStyle_Text_LV3,
    LesoColorStyle_Text_Floating,
    LesoColorStyle_Button_LV1,
    LesoColorStyle_Button_LV2,
    LesoColorStyle_HL,
    LesoColorStyle_HL_2017,
    LesoColorStyle_Score,
    LesoColorStyle_DivView_LV1,
    LesoColorStyle_DivView_LV2,
    LesoColorStyle_DivView_LV3,
    LesoColorStyle_SearchBar_BG,
    LesoColorStyle_SearchBar_Text_BG,
    LesoColorStyle_SearchView_BG,           //灰色的分割线颜色
    LesoColorStyle_SearchView_Card_BG,       //cell白色背景
}LesoColorStyle;

```

### 角标设置 相关文件 ‘UIView+LesoVideoTypeBadge.h’
目前版本中涉及角标的设置是通过viewModel中对应的枚举进行设置的,目前分为左角标和右角标，

>规则为:


> * 左角标只可能是vip角标；右角标可以是全网、独播、自制、专题
> * 只要出现全网角标，则不可能出现vip角标
> * 左角标和右角标可以同时出现
相关逻辑参看[v6.7需求文档](http://wiki.letv.cn/display/search/IOS+SDK+v6.7)

```objc
typedef NS_ENUM(NSUInteger,LesoCornerType) {
    LesoCornerTypeNone,//没有角标
    LesoCornerTypeVip,//会员
    LesoCornerTypeHomeMade,//自制
    LesoCornerTypePlayMark,//独播
    LesoCornerTypeExternal,//全网
    LesoCornerTypeSubject,//专题
};
```

## 附录，常用case的query
| 情景/想要得到的数据	  | query
| ------------------- | :-----------: |
|直播数据获取playlist数据,type=6的娱乐数据 |剧场公演、演唱会、财经
|直播数据获取program数据,type=2的轮播台、卫视台数据 |足球、娱乐等，目前没有卫视台数据，轮播台匹配具体节目的title
|直播数据获取games数据,type=3的体育数据 |足球、体育
|只命中other_name，不命中title | 流氓大亨
|外网站点源很多的电视剧专辑 | 花千骨
|剧集为vip的综艺专辑 | 娱乐everyday
|自制剧专辑 | 我的老千生涯
|会员+自制 | 睡在我上铺的兄弟，女总裁的贴身高手
|会员+独播 | 甄嬛传，孤芳不自赏，超少年密码



