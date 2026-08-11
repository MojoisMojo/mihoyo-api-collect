# 游戏账号信息

- [获取游戏记录卡片信息](#获取游戏记录卡片信息)
- [通过LToken获取绑定游戏账号的基本信息](#通过ltoken获取绑定游戏账号的基本信息)
- [通过SToken获取绑定游戏账号的基本信息](#通过stoken获取绑定游戏账号的基本信息)
- [通过Action Ticket获取绑定游戏账号的基本信息](#通过action-ticket获取绑定游戏账号的基本信息)
- [原神](#原神)
  - [获取首页信息](#genshin-home)
  - [获取游戏账号基本信息](#genshin-role-basics)
  - [获取实时便笺信息](#genshin-dailynote)
  - [获取角色信息](#genshin-characters)
  - [获取深境螺旋信息](#genshin-spiral-abyss)
  - [获取祈愿记录](#genshin-wish)
- [崩坏：星穹铁道](#崩坏-星穹铁道)
  - [获取首页信息](#star-rail-home)
  - [获取角色信息](#star-rail-characters)
  - [获取忘却之庭信息](#star-rail-forgotten-hall)
  - [获取跃迁记录](#star-rail-warp)
  - [获取开拓月历](#star-rail-month-info)
- [绝区零](#绝区零)
  - [获取绑定游戏账号的基本信息](#zzz-roles)
  - [获取首页信息](#zzz-home)
  - [获取实时便笺信息](#zzz-dailynote)
  - [获取角色基础列表](#zzz-avatar-basic)
  - [获取角色详情](#zzz-avatar-info)
  - [获取式舆防卫战信息](#zzz-shiyu)
  - [获取危局强袭战信息](#zzz-deadly-assault)
  - [获取危局强袭战摘要](#zzz-deadly-assault-abstract)
  - [获取临界推演摘要](#zzz-threshold-abstract)
  - [获取临界推演详情](#zzz-threshold-detail)
  - [获取临界推演周期详情](#zzz-threshold-period)
  - [获取绳网月报](#zzz-month-info)
  - [获取绳网月报详情](#zzz-month-detail)
  - [获取调频记录](#zzz-gacha-record)
  - [获取当前调频信息](#zzz-cur-gacha)
  - [获取调频日历](#zzz-gacha-calendar)
  - [获取活动日历](#zzz-activity-calendar)
  - [获取拟境湮灭详情](#zzz-holo-boss)
  - [获取零号空洞摘要](#zzz-abyss-abstract)
  - [养成指南相关接口](#zzz-cultivate)

---

## 获取游戏记录卡片信息

**国服：**

_请求方式：GET_

> _需要验证请求头_
>
> `x-rpc-client_type`：`2`
> 
> K2`salt`
>
> `DS1`

> _需要验证Cookie_
> 
> SToken

`https://api-takumi-record.mihoyo.com/game_record/card/api/getGameRecordCard`

**参数：**

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| uid | str | 想要获取游戏记录卡片信息的米游社账号ID | |

**JSON返回：**

根对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| retcode | num | 返回码 | |
| message | str | 返回消息 | |
| data | obj | 该米游社账号的所有游戏记录卡片信息 | |

`data`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| list | arr | 所有游戏记录卡片信息 | |

`data`对象→`list`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| has_role | bool | 该账号是否已绑定该游戏的任何账号 | |
| game_id | num | 该游戏记录对应的游戏ID | |
| game_role_id | str | 该游戏记录展示的游戏账号ID | |
| nickname | str | 该游戏账号的昵称 | |
| region | str | 该游戏账号所属服务器的名称 | |
| level | num | 该游戏账号的等级 | 例如原神的冒险等级 |
| background_image | str | 该游戏记录卡片背景图片的URL | |
| is_public | bool | 该账号是否公开该游戏记录 | |
| data | arr | 该游戏记录的一些简略信息 | |
| region_name | str | 该游戏账号所属服务器的称呼 | |
| url | str | 该游戏记录卡片将跳转页面的URL | |
| data_switches | arr | 待调查 | |
| h5_data_switches | arr | 待调查 | |
| background_color | str | 该卡片背景颜色的16进制颜色值 | |

`data`对象→`list`数组→对象→`data`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| name | str | 该记录项的名称 | |
| type | num | 待调查 | |
| value | str | 该记录项的数据 | |

`data`对象→`list`数组→对象→`data_switches`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| switch_id | str | 待调查 | |
| is_public | bool | 待调查 | |
| switch_name | str | 待调查 | |

<details>
<summary>查看示例</summary>

```json
{
  "retcode": 0,
  "message": "OK",
  "data": {
    "list": [
      {
        "has_role": true,
        "game_id": 2,
        "game_role_id": "222681079",
        "nickname": "※青衫入雨※",
        "region": "cn_gf01",
        "level": 59,
        "background_image": "https://upload-bbs.mihoyo.com/upload/2020/09/22/0762ab7cc42ac5a760bb4d1ea87b2c42_1236712390449986860.png",
        "is_public": true,
        "data": [
          {
            "name": "活跃天数",
            "type": 1,
            "value": "524"
          },
          {
            "name": "获得角色数",
            "type": 1,
            "value": "53"
          },
          {
            "name": "成就达成数",
            "type": 1,
            "value": "795"
          },
          {
            "name": "深境螺旋",
            "type": 1,
            "value": "8-3"
          }
        ],
        "region_name": "天空岛",
        "url": "https://webstatic.mihoyo.com/app/community-game-records/?bbs_presentation_style=fullscreen&bbs_auth_required=true&v=101&gid=2&user_id=317832114",
        "data_switches": [
          {
            "switch_id": 1,
            "is_public": true,
            "switch_name": "个人主页卡片"
          },
          {
            "switch_id": 2,
            "is_public": true,
            "switch_name": "角色详情数据"
          }
        ],
        "h5_data_switches": [],
        "background_color": "D3BC8E"
      },
      ...
    ]
  }
}
```
</details>

## 通过LToken获取绑定游戏账号的基本信息

**国服：**

_请求方式：GET_

> _需要验证请求头_
>
> `x-rpc-client_type`：`5`
> 
> 4X`salt`
>
> `DS2`

> _需要验证Cookie_
> 
> LToken

`https://api-takumi.mihoyo.com/binding/api/getUserGameRolesByCookie`

**参数：**

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| game_biz | str | 游戏标识符 | 若该值为空，将返回所有绑定游戏账号的信息 |

**JSON返回：**

根对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| retcode | num | 返回码 | |
| message | str | 返回消息 | |
| data | obj | Cookie对应米游社账号绑定的游戏账号信息 | |

`data`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| list | arr | 游戏账号基本信息 | |

`data`对象→`list`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| game_biz | str | 该游戏账号所属游戏的标识符 | |
| region | str | 该游戏账号所在服务器的名称 | |
| game_uid | str | 该游戏账号的UID | |
| nickname | str | 该游戏账号的昵称 | |
| level | num | 该游戏账号的等级 | |
| is_chosen | bool | 是否已收藏该游戏账号 | |
| region_name | str | 该游戏账号所在服务器的称呼 | |
| is_official | bool | 该游戏账号所在服务器是否为官方服务器 | |

<details>
<summary>查看示例</summary>

```json
{
  "retcode": 0,
  "message": "OK",
  "data": {
    "list": [
      {
        "game_biz": "hk4e_cn",
        "region": "cn_qd01",
        "game_uid": "524923864",
        "nickname": "༽墨ᐒ染ᐓ月༼",
        "level": 22,
        "is_chosen": false,
        "region_name": "世界树",
        "is_official": false
      },
      ...
    ]
  }
}
```
</details>

## 通过SToken获取绑定游戏账号的基本信息

**国服：**

_请求方式：GET_

> _需要验证请求头_
>
> `x-rpc-client_type`：`2`
> 
> K2`salt`
>
> `DS1`

> _需要验证Cookie_
> 
> SToken

`https://api-takumi.miyoushe.com/binding/api/getUserGameRolesByStoken`

**JSON返回：**

根对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| retcode | num | 返回码 | |
| message | str | 返回消息 | |
| data | obj | Cookie对应米游社账号绑定的游戏账号信息 | |

`data`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| list | arr | 游戏账号基本信息 | |

`data`对象→`list`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| game_biz | str | 该游戏账号所属游戏的标识符 | |
| region | str | 该游戏账号所在服务器的名称 | |
| game_uid | str | 该游戏账号的UID | |
| nickname | str | 该游戏账号的昵称 | |
| level | num | 该游戏账号的等级 | |
| is_chosen | bool | 是否已收藏该游戏账号 | |
| region_name | str | 该游戏账号所在服务器的称呼 | |
| is_official | bool | 该游戏账号所在服务器是否为官方服务器 | |

<details>
<summary>查看示例</summary>

```json
{
  "retcode": 0,
  "message": "OK",
  "data": {
    "list": [
      {
        "game_biz": "hk4e_cn",
        "region": "cn_qd01",
        "game_uid": "524923864",
        "nickname": "༽墨ᐒ染ᐓ月༼",
        "level": 22,
        "is_chosen": false,
        "region_name": "世界树",
        "is_official": false
      },
      ...
    ]
  }
}
```
</details>

## 通过Action Ticket获取绑定游戏账号的基本信息

**国服：**

_请求方式：GET_

`https://api-takumi.miyoushe.com/binding/api/getUserGameRoles`

**参数：**

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| action_ticket | str | 用于获取绑定游戏账号信息的有效Action Ticket | |
| game_biz | str | 游戏标识符 | 若该值为空，将返回所有绑定游戏账号的信息 |

**JSON返回：**

根对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| retcode | num | 返回码 | |
| message | str | 返回消息 | |
| data | obj | Cookie对应米游社账号绑定的游戏账号信息 | |

`data`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| list | arr | 游戏账号基本信息 | |

`data`对象→`list`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| game_biz | str | 该游戏账号所属游戏的标识符 | |
| region | str | 该游戏账号所在服务器的名称 | |
| game_uid | str | 该游戏账号的UID | |
| nickname | str | 该游戏账号的昵称 | |
| level | num | 该游戏账号的等级 | |
| is_chosen | bool | 是否已收藏该游戏账号 | |
| region_name | str | 该游戏账号所在服务器的称呼 | |
| is_official | bool | 该游戏账号所在服务器是否为官方服务器 | |

<details>
<summary>查看示例</summary>

```json
{
  "retcode": 0,
  "message": "OK",
  "data": {
    "list": [
      {
        "game_biz": "hk4e_cn",
        "region": "cn_qd01",
        "game_uid": "524923864",
        "nickname": "༽墨ᐒ染ᐓ月༼",
        "level": 22,
        "is_chosen": false,
        "region_name": "世界树",
        "is_official": false
      },
      ...
    ]
  }
}
```
</details>

## 原神

> **鉴权（当前）**：本节接口 **不再需要** `DS` 请求头与 salt / DS 签名算法，只需携带有效 Cookie（国服多为 `ltoken` / `ltoken_v2` 等）。

<h3 id="genshin-home">获取首页信息</h3>

**国服：**

_请求方式：GET_

> _需要验证Cookie_
> 
> LToken

`https://api-takumi-record.mihoyo.com/game_record/app/genshin/api/index`

**参数：**

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| role_id | num | 原神UID | |
| server | str | 服务器名称 | |

**JSON返回：**

根对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| retcode | num | 返回码 | |
| message | str | 返回消息 | |
| data | obj | 玩家信息 | |

`data`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| role | obj | 玩家基础信息 | |
| avatars | arr | 玩家拥有的角色的信息 | 若Cookie对应的账号不是自己的，则只返回好感度最高的8个角色。 |
| stats | obj | 玩家世界信息 | |
| city_explorations | arr | 待调查 | 似乎没有用 |
| world_explorations | arr | 玩家的世界探索信息 | |
| homes | arr | 玩家的尘歌壶信息 | |

`data`对象→`role`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| AvatarUrl | str | 玩家头像 | 总是为空字符串 |
| nickname | str | 玩家昵称 | |
| region | str | 玩家账号的服务器名称 | |
| level | num | 玩家的冒险等级 | |

`data`对象→`avatars`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| id | num | 该角色的ID | |
| image | str | 该角色的头像 | |
| element | str | 该角色的元素 | 英文 |
| fetter | num | 该角色的好感度 | |
| level | num | 该角色的等级 | |
| rarity | num | 该角色的稀有度 | |
| actived_constellation_num | num | 该角色的已激活命之座数量 | |
| card_image | str | 该角色的角色卡 | |
| is_chosen | bool | 是否收藏了该角色 | |

`data`对象→`stats`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| active_day_number | num | 该玩家的游玩天数 | |
| achievement_number | num | 该玩家已达成的成就数量 | |
| anemoculus_number | num | 该玩家已供奉的风神瞳数量 | |
| geoculus_number | num | 该玩家已供奉的岩神瞳数量 | |
| avatar_number | num | 该玩家拥有的角色数量 | |
| way_point_number | num | 该玩家已激活的传送锚点数量 | |
| domain_number | num | 该玩家已激活的秘境入口数量 | |
| spiral_abyss | num | 该玩家当前的深境螺旋层级 | |
| precious_chest_number | num | 该玩家已开启的珍贵的宝箱数量 | |
| luxurious_chest_number | num | 该玩家已开启的华丽的宝箱数量 | |
| exquisite_chest_number | num | 该玩家已开启的精致的宝箱数量 | |
| common_chest_number | num | 该玩家已开启的普通的宝箱数量 | |
| electroculus_number | num | 该玩家已供奉的雷神瞳数量 | |
| magic_chest_number | num | 该玩家已开启的奇馈宝箱数量 | |
| dendroculus_number | num | 该玩家已供奉的草神瞳数量 | |

`data`对象→`world_explorations`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| level | num | 地区声望等级 | |
| exploration_percentage | num | 地区探索度 | 百分比×10，例如10%探索度则该字段为100 |
| icon | str | 地区图标 | |
| name | str | 地区名称 | |
| type | str | Reputation 声望<br/> | |
| offerings | arr | 该地区除神像以外的等级信息，例如须弥的梦之树、稻妻的神樱树等 | |
| id | num | 该地区的ID | |
| parent_id | num | 父地区的ID | |
| map_url | str | 该地区在米游社观测枢原神大地图的链接 | |
| strategy_url | str | 该地区在米游社攻略的链接 | |
| background_image | str | 该地区的背景图 | |
| inner_icon | str | 该地区的图标 | |
| cover | str | 该地区的覆盖图 | |

`data`对象→`world_explorations`数组→对象→`offerings`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| name | str | 名称 | |
| level | num | 等级 | |
| icon | str | 图标 | |

`data`对象→`homes`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| level | num | 该玩家的尘歌壶等级 | |
| visit_num | num | 该玩家的尘歌壶总造访人数 | |
| comfort_num | num | 尘歌壶该岛的洞天仙力 | |
| item_num | num | 该玩家的摆设图纸数量 | |
| name | str | 尘歌壶该岛的名称 | |
| icon | str | 尘歌壶该岛的图标 | |
| comfort_level_name | str | 尘歌壶该岛的洞天仙力的称号 | |
| comfort_level_icon | str | 尘歌壶该岛的洞天仙力的图标 | |

<details>
<summary>查看示例</summary>

```json
{
  "retcode": 0,
  "message": "OK",
  "data": {
    "role": {
      "AvatarUrl": "",
      "nickname": "※青衫入雨※",
      "region": "cn_gf01",
      "level": 57
    },
    "avatars": [
      {
        "id": 10000002,
        "image": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Ayaka.png",
        "name": "神里绫华",
        "element": "Cryo",
        "fetter": 10,
        "level": 90,
        "rarity": 5,
        "actived_constellation_num": 0,
        "card_image": "https://upload-bbs.mihoyo.com/game_record/genshin/character_card_icon/UI_AvatarIcon_Ayaka_Card.png",
        "is_chosen": false
      },
      ...
    ],
    "stats": {
      "active_day_number": 340,
      "achievement_number": 631,
      "anemoculus_number": 66,
      "geoculus_number": 130,
      "avatar_number": 46,
      "way_point_number": 285,
      "domain_number": 46,
      "spiral_abyss": "12-3",
      "precious_chest_number": 290,
      "luxurious_chest_number": 113,
      "exquisite_chest_number": 965,
      "common_chest_number": 1455,
      "electroculus_number": 128,
      "magic_chest_number": 80,
      "dendroculus_number": 182
    },
    "city_explorations": [],
    "world_explorations": [
      {
        "level": 5,
        "exploration_percentage": 560,
        "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/city_icon/UI_ChapterIcon_Xumi.png",
        "name": "须弥",
        "type": "Reputation",
        "offerings": [
          {
            "name": "梦之树",
            "level": 29,
            "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/city_icon/UI_ChapterOffering_DreamTree.png"
          }
        ],
        "id": 8,
        "parent_id": 0,
        "map_url": "https://webstatic.mihoyo.com/ys/app/interactive-map/index.html?bbs_presentation_style=no_header&utm_source=mys&utm_medium=ys&utm_campaign=gamerecord&lang=zh-cn&_markerFps=24#/map/2?center=3116.00,-3823.00&zoom=-2.00&shown_types=",
        "strategy_url": "https://bbs.mihoyo.com/ys/strategy/channel/map/45/251?bbs_presentation_style=no_header",
        "background_image": "https://upload-bbs.mihoyo.com/game_record/genshin/city_icon/UI_ChapterBackground_Xumi.png",
        "inner_icon": "https://upload-bbs.mihoyo.com/game_record/genshin/city_icon/UI_ChapterInnerIcon_Xumi.png",
        "cover": "https://upload-bbs.mihoyo.com/game_record/genshin/city_icon/UI_ChapterCover_Xumi.png"
      },
      ...
    ],
    "homes": [
      {
        "level": 8,
        "visit_num": 3,
        "comfort_num": 6500,
        "item_num": 466,
        "name": "罗浮洞",
        "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/home/UI_HomeworldModule_2_Pic.png",
        "comfort_level_name": "初显锦绣",
        "comfort_level_icon": "https://upload-bbs.mihoyo.com/game_record/genshin/home/UI_Homeworld_Comfort_5.png"
      },
      ...
    ]
  }
}
```

</details>

**国际服：**

_请求方式：GET_

> _需要验证Cookie_
> 
> LToken

`https://bbs-api-os.hoyolab.com/game_record/genshin/api/index`

参数：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| role_id | num | 原神UID | |
| server | str | 服务器名称 | |

<h3 id="genshin-role-basics">获取游戏账号基本信息</h3>

**国服：**

_请求方式：GET_

> _需要验证Cookie_
> 
> LToken

`https://api-takumi-record.mihoyo.com/game_record/app/genshin/api/roleBasicInfo`

**参数：**

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| server | str | 服务器名称 | |
| role_id | num | 原神UID | |

**JSON返回**

根对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| retcode | num | 返回码 | |
| message | str | 返回消息 | |
| data | obj | 该游戏账号的基本信息 | |

`data`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| AvatarUrl | str | 空字符串 | |
| nickname | str | 该游戏账号的昵称 | |
| region | str | 该游戏账号所属服务器的名称 | |
| level | num | 该游戏账号的冒险等级 | |
| card_play_level | num | 待调查 | |

<details>
<summary>查看示例</summary>

```json
{
  "retcode": 0,
  "message": "OK",
  "data": {
    "AvatarUrl": "",
    "nickname": "※青衫入雨※",
    "region": "cn_gf01",
    "level": 59,
    "card_play_level": 0
  }
}
```
</details>


<h3 id="genshin-dailynote">获取实时便笺信息</h3>

**国服：**

_请求方式：GET_

> _需要验证Cookie_
> 
> LToken

`https://api-takumi-record.mihoyo.com/game_record/app/genshin/api/dailyNote`

**参数：**

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| server | str | 服务器名称 | |
| role_id | num | 原神UID | |

**JSON返回**

根对象：

| 字段 | 类型 | 内容           | 备注 |
| ---- | ---- |--------------| ---- |
| retcode | num | 返回码          | |
| message | str | 返回消息         | |
| data | obj | 该游戏账号的实时便笺信息 | |

`data`对象：

| 字段 | 类型 | 内容       | 备注 |
| ---- | ---- |----------|-|
| current_resin | num | 当前树脂     | |
| max_resin | num | 树脂上限     | 恒为160 |
| resin_recovery_time | str | 树脂恢复时间   | 以秒为单位 |
| finished_task_num | num | 已完成任务数   | 为日常委托完成数 |
| total_task_num | num | 总任务数     | 为日常委托总数 |
| is_extra_task_reward_received | bool | 是否领取额外奖励 | |
| remain_resin_discount_num | num | 剩余周本折扣次数 | |
| resin_discount_num_limit | num | 周本折扣次数上限 | |
| current_expedition_num | num | 当前探索次数   | |
| max_expedition_num | num | 探索次数上限   | |
| expeditions | arr | 探索队伍信息   | |
| current_home_coin | num | 当前家园币    | |
| max_home_coin | num | 家园币上限    | |
| home_coin_recovery_time | str | 家园币恢复时间  | 以秒为单位 |
| calendar_url | str | 日历链接     | |
| transformer | obj | 转换器信息    | |
| daily_task | obj | 日常任务信息   | |
| archon_quest_progress | obj | 主线任务进度   | |

`data`对象→`expeditions`数组→对象：

| 字段 | 类型 | 内容 | 备注                          |
| ---- | ---- | ---- |-----------------------------|
| avatar_side_icon | str | 角色头像 |                             |
| status | str | 状态 | Ongoing-派遣中<br/>Finished-完成 |
| remained_time | str | 剩余时间 | 以秒为单位                       |

`data`对象→`transformer`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| obtained | bool | 是否获得 | |
| recovery_time | obj | 恢复时间 | |
| wiki | str | 百科链接 | |
| noticed | bool | 是否通知 | |
| latest_job_id | str | 最新任务ID | |

`data`对象→`transformer`对象→`recovery_time`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| Day | num | 天数 | |
| Hour | num | 小时 | |
| Minute | num | 分钟 | |
| Second | num | 秒数 | |
| reached | bool | 是否到达 | |

`data`对象→`daily_task`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| total_num | num | 总任务数 | |
| finished_num | num | 已完成任务数 | |
| is_extra_task_reward_received | bool | 是否领取额外奖励 | |
| task_rewards | arr | 任务奖励 | |
| attendance_rewards | arr | 签到奖励 | |
| attendance_visible | bool | 是否显示签到 | |

`data`对象→`daily_task`对象→`task_rewards`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- |----|
| status | str | 状态 |    |

> `task_rewards.status` 枚举类型如下：
> 
> + `TaskRewardStatusInvalid`：无效
> + `TaskRewardStatusTakenAward`：已领取
> + `TaskRewardStatusUnfinished`：未完成
> + `TaskRewardStatusFinished`：已完成

`data`对象→`daily_task`对象→`attendance_rewards`数组→对象：

| 字段 | 类型 | 内容 | 备注     |
| ---- | ---- | ---- |--------|
| status | str | 状态 |        |
| progress | num | 进度 | 最大2000 |

> `attendance_rewards.status` 枚举类型如下：
> 
> + `AttendanceRewardStatusInvalid`：无效
> + `AttendanceRewardStatusTakenAward`：已领取
> + `AttendanceRewardStatusWaitTaken`：等待领取
> + `AttendanceRewardStatusUnfinished`：未完成
> + `AttendanceRewardStatusFinishedNonReward`：已完成但无奖励
> + `AttendanceRewardStatusForbid`：禁止领取

`data`对象→`archon_quest_progress`对象：

| 字段 | 类型 | 内容         | 备注 |
| ---- | ---- |------------| ---- |
| list | arr | 任务列表       | |
| is_open_archon_quest | bool | 是否开启主线任务   | |
| is_finish_all_mainline | bool | 是否完成所有主线任务 | |
| is_finish_all_interchapter | bool | 是否完成所有间章任务 | |
| wiki_url | str | 百科链接       | |

`data`对象→`archon_quest_progress`对象→`list`数组→对象：

| 字段 | 类型  | 内容   | 备注 |
| ---- |-----|------| ---- |
| id | num | 任务ID | |
| chapter_title | str | 任务名称 | |
| chapter_num | str | 任务章节 | |
| status | str | 任务状态 | |

> `archon_quest_progress.list.status` 枚举类型如下：
> 
> + `StatusNotOpen`：未开启
> + `StatusOngoing`：进行中
> + `StatusFinished`：已完成

<details>
<summary>查看示例</summary>

```json
{
  "retcode": 0,
  "message": "OK",
  "data": {
    "current_resin": 160,
    "max_resin": 160,
    "resin_recovery_time": "0",
    "finished_task_num": 4,
    "total_task_num": 4,
    "is_extra_task_reward_received": true,
    "remain_resin_discount_num": 3,
    "resin_discount_num_limit": 3,
    "current_expedition_num": 5,
    "max_expedition_num": 5,
    "expeditions": [
      {
        "avatar_side_icon": "https://act-webstatic.mihoyo.com/hk4e/e20200928calculate/item_avatar_side_icon_u1536f/d06041afad12e786feec4bd91af88c47.png",
        "status": "Ongoing",
        "remained_time": "50850"
      },
      {
        "avatar_side_icon": "https://act-webstatic.mihoyo.com/hk4e/e20200928calculate/item_avatar_side_icon_u1536f/0a690548d7aa399313856434db3a43dc.png",
        "status": "Ongoing",
        "remained_time": "50850"
      },
      {
        "avatar_side_icon": "https://act-webstatic.mihoyo.com/hk4e/e20200928calculate/item_avatar_side_icon_u1536f/a4f153a2f89c05b83943c3cc51346c41.png",
        "status": "Ongoing",
        "remained_time": "50850"
      },
      {
        "avatar_side_icon": "https://act-webstatic.mihoyo.com/hk4e/e20200928calculate/item_avatar_side_icon_u1536f/2e2786b714207285c98e02f265dcc103.png",
        "status": "Ongoing",
        "remained_time": "1954"
      },
      {
        "avatar_side_icon": "https://act-webstatic.mihoyo.com/hk4e/e20200928calculate/item_avatar_side_icon_u1536f/3fddceeb1aac42fb6077446a007915c4.png",
        "status": "Ongoing",
        "remained_time": "1954"
      }
    ],
    "current_home_coin": 0,
    "max_home_coin": 2400,
    "home_coin_recovery_time": "284857",
    "calendar_url": "https://bbs.mihoyo.com/ys/obc/channel/map/193?bbs_presentation_style=no_header",
    "transformer": {
      "obtained": true,
      "recovery_time": {
        "Day": 0,
        "Hour": 0,
        "Minute": 0,
        "Second": 0,
        "reached": true
      },
      "wiki": "https://bbs.mihoyo.com/ys/obc/content/1562/detail?bbs_presentation_style=no_header",
      "noticed": false,
      "latest_job_id": "0"
    },
    "daily_task": {
      "total_num": 4,
      "finished_num": 4,
      "is_extra_task_reward_received": true,
      "task_rewards": [
        {
          "status": "TaskRewardStatusUnfinished"
        },
        {
          "status": "TaskRewardStatusUnfinished"
        },
        {
          "status": "TaskRewardStatusUnfinished"
        },
        {
          "status": "TaskRewardStatusUnfinished"
        }
      ],
      "attendance_rewards": [
        {
          "status": "AttendanceRewardStatusTakenAward",
          "progress": 2000
        },
        {
          "status": "AttendanceRewardStatusTakenAward",
          "progress": 2000
        },
        {
          "status": "AttendanceRewardStatusTakenAward",
          "progress": 2000
        },
        {
          "status": "AttendanceRewardStatusTakenAward",
          "progress": 2000
        }
      ],
      "attendance_visible": true
    },
    "archon_quest_progress": {
      "list": [],
      "is_open_archon_quest": true,
      "is_finish_all_mainline": true,
      "is_finish_all_interchapter": true,
      "wiki_url": ""
    }
  }
}
```

</details>

<h3 id="genshin-characters">获取角色信息</h3>

**国服：**

_请求方式：POST_

> _需要验证Cookie_
> 
> LToken

`https://api-takumi-record.mihoyo.com/game_record/app/genshin/api/character`

**参数：**

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| server | str | 服务器名称 | |
| role_id | num | 原神UID | |

**JSON返回**

根对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| retcode | num | 返回码 | |
| message | str | 返回消息 | |
| data | obj | 该游戏账号的角色信息 | |

`data`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| avatars | arr | 该账号拥有的角色的信息 | 若Cookie对应的账号不是自己的，则只返回好感度最高的8个角色。 |
| role | obj | 该账号的基本信息 | |

`data`对象→`avatars`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| id | num | 角色ID | |
| image | str | 角色的图像 | |
| icon | str | 角色的图标 | |
| name | str | 角色姓名 | |
| element | str | 角色的元素 | 英文 |
| fetter | num | 角色好感度 | |
| level | num | 角色等级 | |
| rarity | num | 角色稀有度 | |
| weapon | obj | 角色持有武器的信息 | |
| reliquaries | arr | 角色佩戴的圣遗物的信息 | |
| constellations | arr | 角色的命之座信息 | |
| actived_constellation_num | num | 该角色已点亮的命之座数量 | |
| costumes | arr | 该账号拥有的该角色衣装信息 | |
| external | | 待调查 | |

`data`对象→`avatars`数组→对象→`weapon`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| id | num | 该武器ID | |
| name | str | 该武器的名称 | |
| icon | str | 该武器的图标 | |
| type | num | 该武器的类型 | |
| rarity | num | 该武器的稀有度 | |
| level | num | 该武器的等级 | |
| promote_level | num | 该武器的精炼等级 | |
| type_name | str | 该武器所属类型的名称 | |
| desc | str | 该武器的描述 | |
| affix_level | num | 待调查 | |

`data`对象→`avatars`数组→对象→`reliquaries`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| id | num | 该圣遗物的ID | |
| name | str | 该圣遗物的名称 | |
| icon | str | 该圣遗物的图标 | |
| pos | num | 该圣遗物的位置<br/>1 生之花<br/>2 死之羽<br/>3 空之杯<br/>4 时之沙<br/>5 理之冠 | |
| rarity | num | 该圣遗物的稀有度 | |
| level | num | 该圣遗物的等级 | |
| set | obj | 该圣遗物所属的圣遗物套装的信息 | |
| pos_name | str | 该圣遗物的位置的名称 | |

`data`对象→`avatars`数组→对象→`reliquaries`数组→对象→`set`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| id | num | 该圣遗物套装的ID | |
| name | str | 该圣遗物套装的名称 | |
| affixes | arr | 该圣遗物套装的套装效果信息 | |

`data`对象→`avatars`数组→对象→`reliquaries`数组→对象→`set`对象→`affixes`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| activation_number | num | 需要装备多少该套装内的圣遗物才能激活该效果 | |
| effect | str | 该圣遗物套装效果的描述 | |

`data`对象→`avatars`数组→对象→`constellations`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| id | num | 该命之座的ID | |
| name | str | 该命之座的名称 | |
| icon | str | 该命之座的图标 | |
| effect | str | 该命之座的描述 | |
| is_actived | bool | 该账号是否已激活该命之座 | |
| pos | num | 该命之座的位置 | |

`data`对象→`avatars`数组→对象→`costumes`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| id | num | 该衣装的ID | |
| name | str | 该衣装的名称 | |
| icon | str | 该衣装的图标 | |

`data`对象→`role`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| AvatarUrl | str | 该账号的头像 | 似乎没有用 |
| nickname | str | 该账号的昵称 | |
| region | str | 该账号在的服务器的名称 | |
| level | num | 该账号的冒险等级 | |

<details>
<summary>查看示例</summary>

```json
{
  "retcode": 0,
  "message": "OK",
  "data": {
    "avatars": [
      {
        "id": 10000002,
        "image": "https://upload-bbs.mihoyo.com/game_record/genshin/character_image/UI_AvatarIcon_Ayaka@2x.png",
        "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Ayaka.png",
        "name": "神里绫华",
        "element": "Cryo",
        "fetter": 10,
        "level": 90,
        "rarity": 5,
        "weapon": {
          "id": 11505,
          "name": "磐岩结绿",
          "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/equip/UI_EquipIcon_Sword_Morax.png",
          "type": 1,
          "rarity": 5,
          "level": 90,
          "promote_level": 6,
          "type_name": "单手剑",
          "desc": "由纯净的翠玉精琢细雕而成的仪礼宝剑，挥舞时剑风中似有叹息之声。",
          "affix_level": 1
        },
        "reliquaries": [
          {
            "id": 71544,
            "name": "历经风雪的思念",
            "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/equip/UI_RelicIcon_14001_4.png",
            "pos": 1,
            "rarity": 5,
            "level": 20,
            "set": {
              "id": 2140011,
              "name": "冰风迷途的勇士",
              "affixes": [
                {
                  "activation_number": 2,
                  "effect": "获得15%冰元素伤害加成。"
                },
                ...
              ]
            },
            "pos_name": "生之花"
          },
          ...
        ],
        "constellations": [
          {
            "id": 21,
            "name": "霜杀墨染樱",
            "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/constellation_icon/UI_Talent_S_Ayaka_01.png",
            "effect": "神里绫华的普通攻击或重击对敌人造成<color=#99FFFFFF>冰元素伤害</color>时，有50%的几率使<color=#FFD780FF>神里流·冰华</color>的冷却时间缩减0.3秒。该效果每0.1秒只能触发一次。",
            "is_actived": false,
            "pos": 1
          },
          ...
        ],
        "actived_constellation_num": 0,
        "costumes": [],
        "external": null
      },
      ...
    ],
    "role": {
      "AvatarUrl": "",
      "nickname": "玄天",
      "region": "cn_gf01",
      "level": 56
    }
  }
}
```

</details>

**国际服：**

_请求方式：POST_

> _需要验证Cookie_
> 
> LToken

`未知`

**参数：**

**JSON返回**

<h3 id="genshin-spiral-abyss">获取深境螺旋信息</h3>

**国服：**

_请求方式：GET_

> _需要验证Cookie_
> 
> LToken

`https://api-takumi-record.mihoyo.com/game_record/app/genshin/api/spiralAbyss`

**参数：**

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| server | str | 服务器名称 | |
| role_id | num | 原神UID | |
| schedule_type | num | 要查询的是哪期深渊信息<br/>1 当期<br/>2 上期 | |

**JSON返回：**

根对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| retcode | num | 返回码<br/>10102 目标用户未公开数据 | |
| message | str | 返回消息 | |
| data | obj | 该游戏账号的深境螺旋信息 | |

`data`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| schedule_id | num | 这期深境螺旋的ID | |
| start_time | str | 这期深境螺旋开始时的Unix时间戳 | |
| end_time | str | 这期深境螺旋结束时间的Unix时间戳 | |
| total_battle_times | num | 该玩家在这期深境螺旋总共战斗的间数量 | |
| total_win_times | num | 该玩家在这期深境螺旋总共胜利的间数量 | |
| max_floor | str | 该玩家在这期最深抵达的间 | |
| reveal_rank | arr | 该玩家在这期深境螺旋使用次数最多的角色的信息 | |
| defeat_rank | arr | 该玩家在这期深境螺旋击破数量最多的角色的信息 | |
| damage_rank | arr | 该玩家在这期深境螺旋中伤害最大的角色的信息 | |
| take_damage_rank | arr | 该玩家在这期深境螺旋中承受伤害最多的角色的信息 | |
| normal_skill_rank | arr | 该玩家在这期深境螺旋中释放最多元素战技的角色的信息 | |
| energy_skill_rank | arr | 该玩家在这期深境螺旋中释放最多元素爆发的角色的信息 | |
| floors | arr | 该玩家在这期深境螺旋第8层及以上层的信息 | |
| total_star | num | 该玩家在这期深境螺旋得到的星的数量 | |
| is_unlock | bool | 该玩家是否已解锁渊月螺旋 | |

`data`对象→`reveal_rank`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| avatar_id | num | 该角色的ID | |
| avatar_icon | str | 该角色的图标 | |
| value | num | 该玩家在这期深境螺旋的使用该角色的次数 | |
| rarity | num | 该角色的稀有度 | |

`data`对象→`defeat_rank`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| avatar_id | num | 该角色的ID | |
| avatar_icon | str | 该角色的图标 | |
| value | num | 该玩家在这期深境螺旋中该角色击破的次数 | |
| rarity | num | 该角色的稀有度 | |

`data`对象→`damage_rank`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| avatar_id | num | 该角色的ID | |
| avatar_icon | str | 该角色的图标 | |
| value | num | 该玩家在这期深境螺旋中该角色输出的最大伤害 | |
| rarity | num | 该角色的稀有度 | |

`data`对象→`take_damage_rank`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| avatar_id | num | 该角色的ID | |
| avatar_icon | str | 该角色的图标 | |
| value | num | 该玩家在这期深境螺旋中该角色承受的伤害 | |
| rarity | num | 该角色的稀有度 | |

`data`对象→`take_damage_rank`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| avatar_id | num | 该角色的ID | |
| avatar_icon | str | 该角色的图标 | |
| value | num | 该玩家在这期深境螺旋中该角色承受的伤害 | |
| rarity | num | 该角色的稀有度 | |

`data`对象→`normal_skill_rank`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| avatar_id | num | 该角色的ID | |
| avatar_icon | str | 该角色的图标 | |
| value | num | 该玩家在这期深境螺旋中该角色释放的元素战技数量 | |
| rarity | num | 该角色的稀有度 | |

`data`对象→`energy_skill_rank`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| avatar_id | num | 该角色的ID | |
| avatar_icon | str | 该角色的图标 | |
| value | num | 该玩家在这期深境螺旋中该角色释放的元素爆发数量 | |
| rarity | num | 该角色的稀有度 | |

`data`对象→`floors`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| index | num | 该层的位置 | |
| icon | | 该层的图标，似乎没有用 | |
| is_unlock | bool | 该玩家是否已通过这层 | |
| settle_time | num | 该玩家通过这层的时间 | 总是为`0` |
| star | num | 该玩家在这层获得的星的数量 | |
| max_star | num | 该层最多可获得的星的数量 | |
| levels | arr | 该层的间的信息 | |

`data`对象→`floors`数组→对象→`levels`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| index | num | 该间的位置 | |
| star | num | 该玩家在这间获得的星的数量 | |
| max_star | num | 这间最多可获得的星的数量 | |
| battles | arr | 该玩家在这间的上半、下半的战斗信息 | |

`data`对象→`floors`数组→对象→`levels`数组→对象→`battles`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| index | num | 1 上半<br/>2 下半 | |
| timestamp | str | 该玩家开始战斗时的Unix时间戳 | |
| avatars | arr | 该玩家在该间的上半或下半战斗使用的角色的信息 | |

`data`对象→`floors`数组→对象→`levels`数组→对象→`battles`数组→对象→`avatars`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| id | num | 该角色的ID | |
| icon | str | 该角色的图标 | |
| level | num | 该角色的等级 | |
| rarity | num | 该角色的稀有度 | |

<details>
<summary>查看示例</summary>

```json
{
  "retcode": 0,
  "message": "OK",
  "data": {
    "schedule_id": 63,
    "start_time": "1675195200",
    "end_time": "1676491199",
    "total_battle_times": 32,
    "total_win_times": 20,
    "max_floor": "12-3",
    "reveal_rank": [
      {
        "avatar_id": 10000052,
        "avatar_icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Shougun.png",
        "value": 16,
        "rarity": 5
      },
      {
        "avatar_id": 10000030,
        "avatar_icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Zhongli.png",
        "value": 14,
        "rarity": 5
      },
      {
        "avatar_id": 10000025,
        "avatar_icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Xingqiu.png",
        "value": 14,
        "rarity": 4
      },
      {
        "avatar_id": 10000073,
        "avatar_icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Nahida.png",
        "value": 13,
        "rarity": 5
      }
    ],
    "defeat_rank": [
      {
        "avatar_id": 10000052,
        "avatar_icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_side_icon/UI_AvatarIcon_Side_Shougun.png",
        "value": 63,
        "rarity": 5
      }
    ],
    "damage_rank": [
      {
        "avatar_id": 10000052,
        "avatar_icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_side_icon/UI_AvatarIcon_Side_Shougun.png",
        "value": 127921,
        "rarity": 5
      }
    ],
    "take_damage_rank": [
      {
        "avatar_id": 10000052,
        "avatar_icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_side_icon/UI_AvatarIcon_Side_Shougun.png",
        "value": 175343,
        "rarity": 5
      }
    ],
    "normal_skill_rank": [
      {
        "avatar_id": 10000032,
        "avatar_icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_side_icon/UI_AvatarIcon_Side_Bennett.png",
        "value": 112,
        "rarity": 4
      }
    ],
    "energy_skill_rank": [
      {
        "avatar_id": 10000047,
        "avatar_icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_side_icon/UI_AvatarIcon_Side_Kazuha.png",
        "value": 62,
        "rarity": 5
      }
    ],
    "floors": [
      {
        "index": 8,
        "icon": "",
        "is_unlock": true,
        "settle_time": "0",
        "star": 9,
        "max_star": 9,
        "levels": [
          {
            "index": 1,
            "star": 3,
            "max_star": 3,
            "battles": [
              {
                "index": 1,
                "timestamp": "1675518215",
                "avatars": [
                  {
                    "id": 10000032,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Bennett.png",
                    "level": 90,
                    "rarity": 4
                  },
                  {
                    "id": 10000023,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Xiangling.png",
                    "level": 90,
                    "rarity": 4
                  },
                  {
                    "id": 10000047,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Kazuha.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000025,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Xingqiu.png",
                    "level": 90,
                    "rarity": 4
                  }
                ]
              },
              {
                "index": 2,
                "timestamp": "1675518263",
                "avatars": [
                  {
                    "id": 10000078,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Alhatham.png",
                    "level": 80,
                    "rarity": 5
                  },
                  {
                    "id": 10000031,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Fischl.png",
                    "level": 80,
                    "rarity": 4
                  },
                  {
                    "id": 10000030,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Zhongli.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000073,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Nahida.png",
                    "level": 90,
                    "rarity": 5
                  }
                ]
              }
            ]
          },
          {
            "index": 2,
            "star": 3,
            "max_star": 3,
            "battles": [
              {
                "index": 1,
                "timestamp": "1675518335",
                "avatars": [
                  {
                    "id": 10000032,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Bennett.png",
                    "level": 90,
                    "rarity": 4
                  },
                  {
                    "id": 10000023,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Xiangling.png",
                    "level": 90,
                    "rarity": 4
                  },
                  {
                    "id": 10000047,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Kazuha.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000025,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Xingqiu.png",
                    "level": 90,
                    "rarity": 4
                  }
                ]
              },
              {
                "index": 2,
                "timestamp": "1675518383",
                "avatars": [
                  {
                    "id": 10000078,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Alhatham.png",
                    "level": 80,
                    "rarity": 5
                  },
                  {
                    "id": 10000031,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Fischl.png",
                    "level": 80,
                    "rarity": 4
                  },
                  {
                    "id": 10000030,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Zhongli.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000073,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Nahida.png",
                    "level": 90,
                    "rarity": 5
                  }
                ]
              }
            ]
          },
          {
            "index": 3,
            "star": 3,
            "max_star": 3,
            "battles": [
              {
                "index": 1,
                "timestamp": "1675518455",
                "avatars": [
                  {
                    "id": 10000032,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Bennett.png",
                    "level": 90,
                    "rarity": 4
                  },
                  {
                    "id": 10000023,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Xiangling.png",
                    "level": 90,
                    "rarity": 4
                  },
                  {
                    "id": 10000047,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Kazuha.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000025,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Xingqiu.png",
                    "level": 90,
                    "rarity": 4
                  }
                ]
              },
              {
                "index": 2,
                "timestamp": "1675518507",
                "avatars": [
                  {
                    "id": 10000078,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Alhatham.png",
                    "level": 80,
                    "rarity": 5
                  },
                  {
                    "id": 10000031,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Fischl.png",
                    "level": 80,
                    "rarity": 4
                  },
                  {
                    "id": 10000030,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Zhongli.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000073,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Nahida.png",
                    "level": 90,
                    "rarity": 5
                  }
                ]
              }
            ]
          }
        ]
      },
      {
        "index": 9,
        "icon": "",
        "is_unlock": true,
        "settle_time": "0",
        "star": 9,
        "max_star": 9,
        "levels": [
          {
            "index": 1,
            "star": 3,
            "max_star": 3,
            "battles": [
              {
                "index": 1,
                "timestamp": "1675195660",
                "avatars": [
                  {
                    "id": 10000047,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Kazuha.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000032,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Bennett.png",
                    "level": 90,
                    "rarity": 4
                  },
                  {
                    "id": 10000039,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Diona.png",
                    "level": 73,
                    "rarity": 4
                  },
                  {
                    "id": 10000052,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Shougun.png",
                    "level": 90,
                    "rarity": 5
                  }
                ]
              },
              {
                "index": 2,
                "timestamp": "1675195715",
                "avatars": [
                  {
                    "id": 10000022,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Venti.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000075,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Wanderer.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000002,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Ayaka.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000030,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Zhongli.png",
                    "level": 90,
                    "rarity": 5
                  }
                ]
              }
            ]
          },
          {
            "index": 2,
            "star": 3,
            "max_star": 3,
            "battles": [
              {
                "index": 1,
                "timestamp": "1675195765",
                "avatars": [
                  {
                    "id": 10000047,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Kazuha.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000032,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Bennett.png",
                    "level": 90,
                    "rarity": 4
                  },
                  {
                    "id": 10000039,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Diona.png",
                    "level": 73,
                    "rarity": 4
                  },
                  {
                    "id": 10000052,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Shougun.png",
                    "level": 90,
                    "rarity": 5
                  }
                ]
              },
              {
                "index": 2,
                "timestamp": "1675195832",
                "avatars": [
                  {
                    "id": 10000022,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Venti.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000075,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Wanderer.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000002,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Ayaka.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000030,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Zhongli.png",
                    "level": 90,
                    "rarity": 5
                  }
                ]
              }
            ]
          },
          {
            "index": 3,
            "star": 3,
            "max_star": 3,
            "battles": [
              {
                "index": 1,
                "timestamp": "1675195880",
                "avatars": [
                  {
                    "id": 10000047,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Kazuha.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000032,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Bennett.png",
                    "level": 90,
                    "rarity": 4
                  },
                  {
                    "id": 10000039,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Diona.png",
                    "level": 73,
                    "rarity": 4
                  },
                  {
                    "id": 10000052,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Shougun.png",
                    "level": 90,
                    "rarity": 5
                  }
                ]
              },
              {
                "index": 2,
                "timestamp": "1675195929",
                "avatars": [
                  {
                    "id": 10000022,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Venti.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000075,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Wanderer.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000002,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Ayaka.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000030,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Zhongli.png",
                    "level": 90,
                    "rarity": 5
                  }
                ]
              }
            ]
          }
        ]
      },
      {
        "index": 10,
        "icon": "",
        "is_unlock": true,
        "settle_time": "0",
        "star": 9,
        "max_star": 9,
        "levels": [
          {
            "index": 1,
            "star": 3,
            "max_star": 3,
            "battles": [
              {
                "index": 1,
                "timestamp": "1675196184",
                "avatars": [
                  {
                    "id": 10000052,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Shougun.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000073,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Nahida.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000025,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Xingqiu.png",
                    "level": 90,
                    "rarity": 4
                  },
                  {
                    "id": 10000031,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Fischl.png",
                    "level": 80,
                    "rarity": 4
                  }
                ]
              },
              {
                "index": 2,
                "timestamp": "1675196243",
                "avatars": [
                  {
                    "id": 10000002,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Ayaka.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000022,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Venti.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000047,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Kazuha.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000030,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Zhongli.png",
                    "level": 90,
                    "rarity": 5
                  }
                ]
              }
            ]
          },
          {
            "index": 2,
            "star": 3,
            "max_star": 3,
            "battles": [
              {
                "index": 1,
                "timestamp": "1675196304",
                "avatars": [
                  {
                    "id": 10000052,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Shougun.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000073,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Nahida.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000025,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Xingqiu.png",
                    "level": 90,
                    "rarity": 4
                  },
                  {
                    "id": 10000031,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Fischl.png",
                    "level": 80,
                    "rarity": 4
                  }
                ]
              },
              {
                "index": 2,
                "timestamp": "1675196338",
                "avatars": [
                  {
                    "id": 10000002,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Ayaka.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000022,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Venti.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000047,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Kazuha.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000030,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Zhongli.png",
                    "level": 90,
                    "rarity": 5
                  }
                ]
              }
            ]
          },
          {
            "index": 3,
            "star": 3,
            "max_star": 3,
            "battles": [
              {
                "index": 1,
                "timestamp": "1675196375",
                "avatars": [
                  {
                    "id": 10000052,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Shougun.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000073,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Nahida.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000025,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Xingqiu.png",
                    "level": 90,
                    "rarity": 4
                  },
                  {
                    "id": 10000031,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Fischl.png",
                    "level": 80,
                    "rarity": 4
                  }
                ]
              },
              {
                "index": 2,
                "timestamp": "1675196405",
                "avatars": [
                  {
                    "id": 10000002,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Ayaka.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000022,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Venti.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000047,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Kazuha.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000030,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Zhongli.png",
                    "level": 90,
                    "rarity": 5
                  }
                ]
              }
            ]
          }
        ]
      },
      {
        "index": 11,
        "icon": "",
        "is_unlock": true,
        "settle_time": "0",
        "star": 9,
        "max_star": 9,
        "levels": [
          {
            "index": 1,
            "star": 3,
            "max_star": 3,
            "battles": [
              {
                "index": 1,
                "timestamp": "1675421955",
                "avatars": [
                  {
                    "id": 10000047,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Kazuha.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000022,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Venti.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000059,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Heizo.png",
                    "level": 70,
                    "rarity": 4
                  },
                  {
                    "id": 10000076,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Faruzan.png",
                    "level": 80,
                    "rarity": 4
                  }
                ]
              },
              {
                "index": 2,
                "timestamp": "1675422299",
                "avatars": [
                  {
                    "id": 10000002,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Ayaka.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000030,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Zhongli.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000073,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Nahida.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000025,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Xingqiu.png",
                    "level": 90,
                    "rarity": 4
                  }
                ]
              }
            ]
          },
          {
            "index": 2,
            "star": 3,
            "max_star": 3,
            "battles": [
              {
                "index": 1,
                "timestamp": "1675196645",
                "avatars": [
                  {
                    "id": 10000052,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Shougun.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000025,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Xingqiu.png",
                    "level": 90,
                    "rarity": 4
                  },
                  {
                    "id": 10000073,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Nahida.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000031,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Fischl.png",
                    "level": 80,
                    "rarity": 4
                  }
                ]
              },
              {
                "index": 2,
                "timestamp": "1675196706",
                "avatars": [
                  {
                    "id": 10000047,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Kazuha.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000032,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Bennett.png",
                    "level": 90,
                    "rarity": 4
                  },
                  {
                    "id": 10000023,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Xiangling.png",
                    "level": 90,
                    "rarity": 4
                  },
                  {
                    "id": 10000002,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Ayaka.png",
                    "level": 90,
                    "rarity": 5
                  }
                ]
              }
            ]
          },
          {
            "index": 3,
            "star": 3,
            "max_star": 3,
            "battles": [
              {
                "index": 1,
                "timestamp": "1675196815",
                "avatars": [
                  {
                    "id": 10000052,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Shougun.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000025,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Xingqiu.png",
                    "level": 90,
                    "rarity": 4
                  },
                  {
                    "id": 10000073,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Nahida.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000031,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Fischl.png",
                    "level": 80,
                    "rarity": 4
                  }
                ]
              },
              {
                "index": 2,
                "timestamp": "1675196863",
                "avatars": [
                  {
                    "id": 10000047,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Kazuha.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000032,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Bennett.png",
                    "level": 90,
                    "rarity": 4
                  },
                  {
                    "id": 10000023,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Xiangling.png",
                    "level": 90,
                    "rarity": 4
                  },
                  {
                    "id": 10000002,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Ayaka.png",
                    "level": 90,
                    "rarity": 5
                  }
                ]
              }
            ]
          }
        ]
      },
      {
        "index": 12,
        "icon": "",
        "is_unlock": true,
        "settle_time": "0",
        "star": 6,
        "max_star": 9,
        "levels": [
          {
            "index": 1,
            "star": 2,
            "max_star": 3,
            "battles": [
              {
                "index": 1,
                "timestamp": "1675560429",
                "avatars": [
                  {
                    "id": 10000078,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Alhatham.png",
                    "level": 80,
                    "rarity": 5
                  },
                  {
                    "id": 10000031,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Fischl.png",
                    "level": 80,
                    "rarity": 4
                  },
                  {
                    "id": 10000030,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Zhongli.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000073,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Nahida.png",
                    "level": 90,
                    "rarity": 5
                  }
                ]
              },
              {
                "index": 2,
                "timestamp": "1675560593",
                "avatars": [
                  {
                    "id": 10000052,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Shougun.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000025,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Xingqiu.png",
                    "level": 90,
                    "rarity": 4
                  },
                  {
                    "id": 10000032,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Bennett.png",
                    "level": 90,
                    "rarity": 4
                  },
                  {
                    "id": 10000023,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Xiangling.png",
                    "level": 90,
                    "rarity": 4
                  }
                ]
              }
            ]
          },
          {
            "index": 2,
            "star": 2,
            "max_star": 3,
            "battles": [
              {
                "index": 1,
                "timestamp": "1675561066",
                "avatars": [
                  {
                    "id": 10000078,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Alhatham.png",
                    "level": 80,
                    "rarity": 5
                  },
                  {
                    "id": 10000031,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Fischl.png",
                    "level": 80,
                    "rarity": 4
                  },
                  {
                    "id": 10000030,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Zhongli.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000073,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Nahida.png",
                    "level": 90,
                    "rarity": 5
                  }
                ]
              },
              {
                "index": 2,
                "timestamp": "1675561261",
                "avatars": [
                  {
                    "id": 10000052,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Shougun.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000025,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Xingqiu.png",
                    "level": 90,
                    "rarity": 4
                  },
                  {
                    "id": 10000032,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Bennett.png",
                    "level": 90,
                    "rarity": 4
                  },
                  {
                    "id": 10000023,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Xiangling.png",
                    "level": 90,
                    "rarity": 4
                  }
                ]
              }
            ]
          },
          {
            "index": 3,
            "star": 2,
            "max_star": 3,
            "battles": [
              {
                "index": 1,
                "timestamp": "1675197621",
                "avatars": [
                  {
                    "id": 10000073,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Nahida.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000052,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Shougun.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000025,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Xingqiu.png",
                    "level": 90,
                    "rarity": 4
                  },
                  {
                    "id": 10000032,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Bennett.png",
                    "level": 90,
                    "rarity": 4
                  }
                ]
              },
              {
                "index": 2,
                "timestamp": "1675197742",
                "avatars": [
                  {
                    "id": 10000002,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Ayaka.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000047,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Kazuha.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000030,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Zhongli.png",
                    "level": 90,
                    "rarity": 5
                  },
                  {
                    "id": 10000014,
                    "icon": "https://upload-bbs.mihoyo.com/game_record/genshin/character_icon/UI_AvatarIcon_Barbara.png",
                    "level": 52,
                    "rarity": 4
                  }
                ]
              }
            ]
          }
        ]
      }
    ],
    "total_star": 42,
    "is_unlock": true
  }
}
```

</details>

**国际服：**

_请求方式：GET_

> _需要验证Cookie_
> 
> LToken

`未知`

<h3 id="genshin-wish">获取祈愿记录</h3>

**国服：**

_请求方式：GET_

`https://hk4e-api.mihoyo.com/event/gacha_info/api/getGachaLog`

**参数：**

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| authkey_ver | num | 1 | |
| authkey | str | 用于标识游戏账号的Auth Key B | 获取方法：<br>1. 游戏内打开一次祈愿记录页面，然后在“游戏安装目录/YuanShen_Data/webCaches/Cache/Cache_Data/data_2”，寻找类似“<https://hk4e-api.mihoyo.com/event/gacha_info/api/getGachaLog……>”的链接，该参数的值在其中<br>2. [通过SToken获取账号Auth Key B](hoyolab/user/token.md#通过stoken获取账号auth-key-b)使请求体字段`auth_appid`为`webview_gacha` |
| lang | str | 语言，即返回数据中抽到的项目名称<br>zh-cn zh 简体中文<br>zh-tw 繁体中文<br>en-us en 英语<br>ru-ru ru 俄语<br>ja-jp ja 日语<br>以及其它国际语言代码 | |
| size | num | 返回数据中的最大数据数量。最小为0，最大为20。若小于0，则返回0个数据；若大于20，则返回最大20个数据 | |
| end_id | num | 见下文的说明 | |
| page | num | 页数，从1开始 | 若为负数返回则会是`-502`。若没有此参数，默认为第1页。该参数实际上没有用处，要实现翻页请使用`end_id`参数。见下文。 |
| gacha_type | num | 祈愿池<br>100 初行者推荐祈愿<br>200 常驻祈愿<br>301 角色活动祈愿<br>302 武器活动祈愿 | |

当需要获取超过20个记录时，需要使用到`end_id`参数。

具体步骤：

1. 当`page`为`1`（即第1页）时，需要指定`end_id`为`0`。则会返回最新的参数`size`个祈愿记录。
1. 当需要翻页（增加`page`）时，需要指定`end_id`为上页的`data`对象→`list`数组→最后一个元素→`id`字符串。
1. 重复第2步，直到获取完成想要获取的祈愿记录数量。

**JSON返回：**

根对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| retcode | num | 返回码<br>-100 请求参数`authkey`不正确<br>-108 未指定语言或不是支持的语言<br>-110 请求过快 | |
| message | str | 返回消息 | |
| data | obj | 该游戏账号的祈愿信息 | |

`data`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| page | num | 页数 | 与请求参数中的`page`参数的值相同 |
| size | num | 最大数据数量 | 与请求参数中的`size`参数的值相同 |
| total | num | 0 | |
| list | arr | 从新至旧排序的祈愿记录 | |
| region | str | 该账号所属服务器的标识 | |

`data`对象→`list`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| uid | str | 该玩家的UID | |
| gacha_type | str | 祈愿池 | 与请求参数中的`gacha_type`参数的值相同（角色活动祈愿-2除外，为`400`） |
| item_id | str | 似乎总是为空字符串 | |
| count | str | 1 | |
| time | str | 该玩家抽到该项目的日期 | |
| name | str | 抽到的项目名称 | 文本语言通过参数`lang`指定 |
| lang | str | 语言 | 与请求参数中的`lang`参数的值相同 |
| item_type | str | 该项目的类别 | 文本语言通过参数`lang`指定 |
| rank_type | str | 该项目的稀有度 | |
| id | str | 该祈愿记录的ID，可用于翻页获取祈愿记录。 | |

<details>
<summary>查看示例</summary>

```json
{
  "retcode": 0,
  "message": "OK",
  "data": {
    "page": "0",
    "size": "20",
    "total": "0",
    "list": [
      {
        "uid": "222681079",
        "gacha_type": "302",
        "item_id": "",
        "count": "1",
        "time": "2023-04-21 20:54:19",
        "name": "铁影阔剑",
        "lang": "zh-cn",
        "item_type": "武器",
        "rank_type": "3",
        "id": "1682078760003138679"
      }
    ],
    "region": "cn_gf01"
  }
}
```

</details>

**国际服：**

`未知`

## 崩坏：星穹铁道

> **鉴权（当前）**：本节接口 **不再需要** `DS` 请求头与 salt / DS 签名算法，只需携带有效 Cookie（国服多为 `ltoken` / `ltoken_v2` 等）。

<h3 id="star-rail-home">获取首页信息</h3>

**国服：**

_请求方式：GET_

> _需要验证Cookie_
> 
> LToken

`https://api-takumi-record.mihoyo.com/game_record/app/hkrpg/api/index`

**参数：**

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| role_id | num | 星穹铁道UID | |
| server | str | 服务器名称 | |

**JSON返回：**

根对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| retcode | num | 返回码 | |
| message | str | 返回消息 | |
| data | obj | 玩家信息 | |

`data`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| stats | obj | 玩家基础信息 | |
| avatar_list | arr | 该玩家拥有的角色的基本信息 | |

`data`对象→`stats`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| active_days | num | 该玩家的游玩天数 | |
| avatar_num | num | 该玩家拥有的角色数量 | |
| achievement_num | num | 该玩家已解锁的成就数量 | |
| chest_num | num | 该玩家已发现的战利品数量 | |
| abyss_process | str | 该玩家达成的忘却之庭层级 | |

`data`对象→`avatar_list`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| id | num | 该角色的ID | |
| name | str | 角色名称 | |
| element | str | 该角色的元素属性 | 英文 |
| icon | str | 该角色的头像 | |
| rarity | num | 该角色的稀有度 | |
| rank | num | 待调查 | |
| is_chosen | bool | 是否收藏了该角色 | |

<details>
<summary>查看示例</summary>

```json
{
  "retcode": 0,
  "message": "OK",
  "data": {
    "stats": {
      "active_days": 17,
      "avatar_num": 15,
      "achievement_num": 154,
      "chest_num": 209,
      "abyss_process": "回忆其六"
    },
    "avatar_list": [
      {
        "id": 1209,
        "level": 60,
        "name": "彦卿",
        "element": "ice",
        "icon": "https://uploadstatic.mihoyo.com/darkmatter/hkrpg/prod_gf_cn/item_icon_7a87fe/a5512decb10359dd6e1484085da105de.png",
        "rarity": 5,
        "rank": 0,
        "is_chosen": false
      },
      ...
    ]
  }
}
```

</details>

**国际服：**

`未知`

<h3 id="star-rail-characters">获取角色信息</h3>

<h3 id="star-rail-forgotten-hall">获取忘却之庭信息</h3>

<h3 id="star-rail-warp">获取跃迁记录</h3>

**国服：**

_请求方式：GET_

`https://api-takumi.mihoyo.com/common/gacha_record/api/getGachaLog`

**参数：**

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| authkey_ver | num | 1 | |
| authkey | str | 用于标识游戏账号的Auth Key B | 获取方法：<br>游戏内打开一次跃迁记录页面，然后在“游戏安装目录/StarRail_Data/webCaches/Cache/Cache_Data/data_2”，寻找类似“<https://api-takumi.mihoyo.com/common/gacha_record/api/getGachaLog……>”的链接，该参数的值在其中 |
| lang | str | 语言，即返回数据中抽到的项目名称<br>zh-cn zh 简体中文<br>zh-tw 繁体中文<br>en-us en 英语<br>ru-ru ru 俄语<br>ja-jp ja 日语<br>以及其它国际语言代码 | |
| size | num | 返回数据中的最大数据数量。最小为0，最大为20。若小于0，则返回0个数据；若大于20，则返回最大20个数据 | |
| end_id | num | 见下文的说明 | |
| page | num | 页数，从1开始 | 若为负数返回则会是`-502`。若没有此参数，默认为第1页。该参数实际上没有用处，要实现翻页请使用`end_id`参数。见下文。 |
| gacha_type | num | 跃迁池<br>1 常驻跃迁<br>2 新手跃迁<br>11 角色活动跃迁<br>12 光锥活动跃迁 | |
| game_biz | str | `authkey`对应账号所属服务器的服务器标识 | |

当需要获取超过20个记录时，需要使用到`end_id`参数。

具体步骤：

1. 当`page`为`1`（即第1页）时，需要指定`end_id`为`0`。则会返回最新的参数`size`个跃迁记录。
1. 当需要翻页（增加`page`）时，需要指定`end_id`为上页的`data`对象→`list`数组→最后一个元素→`id`字符串。
1. 重复第2步，直到获取完成想要获取的跃迁记录数量。

**JSON返回：**

根对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| retcode | num | 返回码<br>-100 请求参数`authkey`不正确<br>-111 请求参数`game_biz`不正确<br>-108 未指定语言或不是支持的语言<br>-110 请求过快 | |
| message | str | 返回消息 | |
| data | obj | 该游戏账号的祈愿信息 | |

`data`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| page | num | 页数 | 与请求参数中的`page`参数的值相同 |
| size | num | 该页的跃迁记录数量 | |
| list | arr | 跃迁记录 | |
| region | str | 该账号所属服务器的标识 | |
| region_time_zone | num | 该玩家的所在时区的UTC时间偏移量 | |

`data`对象→`list`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| uid | str | 该玩家的UID | |
| gacha_id | str | 该跃迁记录所在的跃迁池的ID | |
| gacha_type | str | 跃迁池 | 与请求参数中的`gacha_type`参数的值相同 |
| item_id | str | 该项目的ID | |
| count | str | 1 | |
| time | str | 该玩家抽到该项目的日期 | |
| name | str | 抽到的项目名称 | 文本语言通过参数`lang`指定 |
| lang | str | 语言 | 与请求参数中的`lang`参数的值相同 |
| item_type | str | 该项目的类别 | 文本语言通过参数`lang`指定 |
| rank_type | str | 该项目的稀有度 | |
| id | str | 该跃迁记录的ID，可用于翻页获取跃迁记录 | |

<details>
<summary>查看示例</summary>

```json
{
  "retcode": 0,
  "message": "OK",
  "data": {
    "page": "1",
    "size": "1",
    "list": [
      {
        "uid": "108976226",
        "gacha_id": "3003",
        "gacha_type": "12",
        "item_id": "20003",
        "count": "1",
        "time": "2023-05-07 15:15:27",
        "name": "琥珀",
        "lang": "zh-cn",
        "item_type": "光锥",
        "rank_type": "3",
        "id": "1683443400001878626"
      }
    ],
    "region": "prod_gf_cn",
    "region_time_zone": 8
  }
}
```

</details>

**国际服：**

`未知`


<h3 id="star-rail-month-info">获取开拓月历</h3>


**国服：**

_请求方式：GET_

> _需要验证Cookie_
> 
> Cookie Token：`cookie_token`

`https://api-takumi.mihoyo.com/event/srledger/month_info`

**参数：**

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| uid | num | 星穹铁道UID | |
| region | str | 服务器名称 | |
| month | str | 抽卡月份 | 指定查询月份，为空时查询当月数据，只能查询最近3个月数据，格式 `YYYYMM` |

**JSON返回：**

根对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| retcode | num | 返回码 | |
| message | str | 返回消息 | |
| data | obj | 玩家信息 | |

`data`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| data_month | str | 数据对应的月份 | 格式 `YYYYMM` |
| data_text | obj | 未知 | |
| day_data | obj | 当日数据 | |
| login_flag | bool | 登陆标识 | |
| month | str | 查询时的月份 | 格式 `YYYYMM` |
| month_data | obj | 月历数据 | |
| optional_month | arr | 可查询数据的月份 | 列表中为字符串，时间格式 `YYYYMM` |
| region | str | 服务器名称 | |
| start_month | str | 账号注册月份 | 格式 `YYYYMM` |
| uid | num | 星穹铁道UID | |
| version | num | 游戏版本 | 此字段内容待确认 |

`data`对象→`data_text`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| key | str | 未知 | |
| mi18n_key | num | 未知 | |
| type | str | 未知 | |

`data`对象→`day_data`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| current_hcoin | num | 当日星穹数量 | |
| current_rails_pass | num | 当日星轨通票与星轨专票数量 | |
| last_hcoin | num | 前日星穹数量 | |
| last_rails_pass | num | 前日星轨通票与星轨专票数量 | |


`data`对象→`month_data`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| current_hcoin | num | 当月星穹数量 | |
| current_rails_pass | num | 当月星轨通票与星轨专票数量 | |
| group_by | arr | 星穹数据来源详情 | |
| hcoin_rate | num | 星琼数量较上月的增长率 | |
| last_hcoin | num | 上月星穹数量 | |
| last_rails_pass | num | 上月星轨通票与星轨专票数量 | |
| rails_rate | num | 星轨通票与星轨专票数量较上月的增长率 | |


`month_data`对象→`group_by`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| action | str | 星穹来源 | |
| action_name | str | 星穹来源名称 | |
| num | num | 星穹数量 | |
| percent | num | 从该来源获取的星穹数量占总数的比例 | |

<details>
<summary>查看示例</summary>

```json
{
    "retcode": 0,
    "message": "OK",
    "data": {
        "uid": "123456789",
        "region": "prod_gf_cn",
        "login_flag": true,
        "optional_month": [
            "202308",
            "202307",
            "202306"
        ],
        "month": "202308",
        "data_month": "202308",
        "month_data": {
            "current_hcoin": 3245,
            "current_rails_pass": 17,
            "last_hcoin": 8916,
            "last_rails_pass": 35,
            "hcoin_rate": -63,
            "rails_rate": -51,
            "group_by": [
                {
                    "action": "daily_reward",
                    "num": 2025,
                    "percent": 62,
                    "action_name": "每日活跃"
                },
                {
                    "action": "adventure_reward",
                    "num": 375,
                    "percent": 11,
                    "action_name": "冒险奖励"
                },
                {
                    "action": "mail_reward",
                    "num": 340,
                    "percent": 10,
                    "action_name": "邮件奖励"
                },
                {
                    "action": "event_reward",
                    "num": 220,
                    "percent": 6,
                    "action_name": "活动奖励"
                },
                {
                    "action": "space_reward",
                    "num": 225,
                    "percent": 6,
                    "action_name": "模拟宇宙奖励"
                },
                {
                    "action": "other",
                    "num": 0,
                    "percent": 4,
                    "action_name": "其他"
                },
                {
                    "action": "abyss_reward",
                    "num": 60,
                    "percent": 1,
                    "action_name": "忘却之庭奖励"
                }
            ]
        },
        "day_data": {
            "current_hcoin": 0,
            "current_rails_pass": 0,
            "last_hcoin": 515,
            "last_rails_pass": 0
        },
        "version": "1.2",
        "start_month": "202304",
        "data_text": {
            "type": "TextDay",
            "key": "102_000",
            "mi18n_key": "2"
        }
    }
}
```

</details>

## 绝区零

**通用说明：**

1. **鉴权（当前）**：绝区零相关接口 **不再需要** `DS` 请求头，也 **不需要** salt / DS 签名算法。只需携带有效 Cookie（国服多为 `ltoken` / `ltoken_v2` + `ltuid` / `ltuid_v2` 等）。米游社 WebView 实际请求还会带 `x-rpc-app_version`、`x-rpc-device_id`、`x-rpc-device_fp`、`x-rpc-platform`、`Origin`/`Referer`（`https://act.mihoyo.com`）等字段，**均与 DS 无关**。
2. 大量接口返回的时间字段为对象（而非 Unix 时间戳），结构定义如下（「时间对象」）：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| year | num | 年 | |
| month | num | 月 | |
| day | num | 日 | |
| hour | num | 时 | |
| minute | num | 分 | |
| second | num | 秒 | |

3. 百分比排名类字段（如 `rank_percent`）以 **0.01%** 为单位，例如 `697` 表示约前 6.97%。
4. 角色稀有度 `rarity` 多为字符串 `S` / `A` / `B` 等。
5. 绝区零调频类型在战绩接口中常使用字符串枚举。

---

<h3 id="zzz-roles">获取绑定游戏账号的基本信息</h3>

通过 LToken 拉取绑定角色时，将 `game_biz` 设为绝区零即可。返回结构与通用接口相同，见上文 [通过LToken获取绑定游戏账号的基本信息](#通过ltoken获取绑定游戏账号的基本信息)。

**国服：**

_请求方式：GET_

> _需要验证Cookie_
>
> LToken

`https://api-takumi.mihoyo.com/binding/api/getUserGameRolesByCookie?game_biz=nap_cn`

**国际服：**

_请求方式：GET_

> _需要验证Cookie_
>
> CookieToken 等

`https://api-account-os.hoyolab.com/binding/api/getUserGameRolesByCookieToken?game_biz=nap_global`

**参数：**

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| game_biz | str | 游戏标识符 | 国服 `nap_cn`；国际服 `nap_global` |

<details>
<summary>查看示例</summary>

```json
{
  "retcode": 0,
  "message": "OK",
  "data": {
    "list": [
      {
        "game_biz": "nap_cn",
        "region": "prod_gf_cn",
        "game_uid": "100000001",
        "nickname": "示例昵称",
        "level": 60,
        "is_chosen": false,
        "region_name": "新艾利都",
        "is_official": true,
        "is_banned": false,
        "unmask": []
      }
    ]
  }
}
```

</details>

---

<h3 id="zzz-home">获取首页信息</h3>

对应米游社 / 战绩页「绝区零」首页：活跃天数、获得代理人/邦布、绳网声望、式舆/危局/临界推演等挑战数据、区域收集、「布连邦」等。

**国服：**

_请求方式：GET_

> _需要验证Cookie_
>
> LToken

`https://api-takumi-record.mihoyo.com/event/game_record_zzz/api/zzz/index`

**国际服：**

_请求方式：GET_

> _需要验证Cookie_
>
> LToken

`https://sg-public-api.hoyolab.com/event/game_record_zzz/api/zzz/index`

**参数：**

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| role_id | num | 绝区零 UID | |
| server | str | 服务器名称 | 如 `prod_gf_cn` |

**JSON返回：**

根对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| retcode | num | 返回码 | |
| message | str | 返回消息 | |
| data | obj | 玩家首页信息 | |

`data`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| stats | obj | 首页统计与各玩法数据 | |
| avatar_list | arr | 「我的代理人」展示列表 | |
| cur_head_icon_url | str | 当前头像 URL | |
| buddy_list | arr | 邦布列表 | |
| cat_notes_list | arr | 待调查 | 常为空数组 |
| award_state | str | 待调查 | |
| game_data_show | obj | 个人展示（称号、**勋章一览**、名片等） | |
| area_collections | arr | **区域收集**进度 | 城区 / 管制区 / 空洞等 |
| challenge_schedule_list | arr | 挑战期次时间表 | |

`data`对象→`stats`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| active_days | num | **活跃天数** | 首页主统计 |
| avatar_num | num | **获得代理人数** | |
| world_level_name | str | **绳网声望** | 如「传奇绳匠」 |
| cur_period_zone_layer_count | num | 当期式舆层数（旧字段） | 可为 0；新数据见 `hadal_brief` |
| buddy_num | num | **获得邦布数** | |
| commemorative_coins_list | arr | 调查协会纪念币等 | 如「调查协会纪念币」「协会纪念币·海港」 |
| achievement_count | num | **达成成就数** | |
| climbing_tower_layer | num | **拟真鏖战试炼**层数 | 首页「拟真鏖战试炼」 |
| next_hundred_layer | str | 下一目标层描述 | |
| memory_battlefield | obj | **危局强袭战** | 首页展示总分等 |
| stable_zone_layer_count | num | 稳定区层数 | |
| all_change_zone_layer_count | num | 变动区层数 | |
| climbing_tower_s2 | obj | 拟真鏖战试炼 S2 / 无边末路等 | 勋章类型 `MedalTypeClimbingTowerS2` |
| temple_data | obj | **百通宝**经营汇总 | 与便笺 `temple_running` 对应 |
| climbing_tower_s3 | obj | 拟真鏖战试炼 S3 / 荣耀所眷等 | |
| void_front_brief | obj | **临界推演** | 首页展示总分；结局名见 `ending_record_name` |
| challenge_full_s_times | num | 挑战满 S 次数 | |
| memory_battlefield_full_stars_times | num | 危局满星次数 | 与勋章「危局强袭·崩解」等相关 |
| hadal_brief | obj | **式舆防卫战** | 首页展示分数 |
| climbing_tower_s4 | obj | **运算中枢修复计划** | 见下表子字段 |
| rab_brief | obj | 其它玩法简报 | 待调查 |
| bangboo_micro_web_brief | obj | **「布连邦」账号** | 见下表子字段 |
| holo_boss_brief | obj | **拟境湮灭**简报 | 勋章「拟境湮灭·游刃」「湮灭·…」；接口字段名 `holo_boss_*` |
| zenkov_brief | obj | 待调查 | |

`data`对象→`stats`对象→`commemorative_coins_list`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| num | num | 数量 | |
| name | str | 名称 | |
| sort | num | 排序 | |
| url | str | 图标 | |
| wiki_url | str | 百科链接 | 可为空 |

`data`对象→`stats`对象→`memory_battlefield`对象（危局强袭战）：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| rank_percent | num | 全服排名百分比 | 0.01% 单位 |
| total_score | num | 总分 | 首页「危局强袭战」主数字 |
| total_star | num | 总星数 | 勋章「危局强袭·破阵」等 |
| zone_id | num | 期次 / 区域 ID | |
| has_hard | bool | 是否含绝境挑战 | |
| hard_rank_percent | num | 绝境排名百分比 | |
| hard_total_score | num | 绝境总分 | 勋章「危局强袭·肃清」等 |
| hard_total_star | num | 绝境总星 | |

`data`对象→`stats`对象→`void_front_brief`对象（临界推演）：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| void_front_id | num | 临界推演期次 ID | 拉详情时使用 |
| has_ending_record | bool | 是否完成结局 | |
| ending_record_name | str | 结局名称 | 如「结局一·侦探不止一个！」；勋章同名 |
| total_score | num | 总分 | 首页「临界推演」主数字 |
| rank_percent | num | 排名百分比 | |

`data`对象→`stats`对象→`hadal_brief`对象（式舆防卫战）：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| hadal_ver | str | 式舆数据版本 | 如 `v2` |
| hadal_brief_v2 | obj | v2 简报 | |

`data`对象→`stats`对象→`hadal_brief`对象→`hadal_brief_v2`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| cur_period_zone_layer_count | num | 当期通关层数 | |
| score | num | 分数 | 首页「式舆防卫战」主数字 |
| rank_percent | num | 排名百分比 | 0.01% 单位 |
| rating | str | 评级 | 如 `S+` |
| max_score | num | 满分 | |

`data`对象→`stats`对象→`climbing_tower_s4`对象（运算中枢修复计划）：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| layer_info | obj | 层数与高压测试分数 | |
| mvp_info | obj | 高压测试排行相关 | |

`layer_info`：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| climbing_tower_layer | num | **数域特训层数** | |
| total_score | num | **高压测试最高总分** | 勋章「狂澜勋冠」引用 |
| icon | str | 图标 | |

`mvp_info`：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| floor_mvp_num | num | MVP 次数 | |
| rank_percent | num | **高压测试排行** | 0.01% 单位；未上榜时数值偏大 |
| display_rank | bool | 是否展示排名 | |

`data`对象→`stats`对象→`bangboo_micro_web_brief`对象（「布连邦」账号）：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| level | num | **「布连邦」账号等级** | 首页主数字 |
| treasure_info | obj | **像素童话**进度 | `cur_progress` / `max_progress` |
| island_file | obj | **特区档案**进度 | 如 `10/33` |
| hot_event | obj | **邦圈热点**进度 | 如 `7/35` |

`data`对象→`stats`对象→`temple_data`对象（百通宝）：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| level | num | 百通宝等级 | 与便笺 `temple_running.level` 一致 |
| sell_days | num | 经营天数相关 | |
| total_sell_temple_coin | str | 累计经营货币 | 字符串数字 |

`data`对象→`stats`对象→`holo_boss_brief`对象（拟境湮灭）：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| unlock | bool | 是否解锁 | |
| no_injured_boss_num | num | 无伤通关 BOSS 数 | 勋章「湮灭·…」相关 |

`data`对象→`avatar_list`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| id | num | 代理人 ID | |
| level | num | 等级 | |
| name_mi18n | str | 名称 | |
| full_name_mi18n | str | 全名 | |
| element_type | num | 属性类型 | 数值枚举 |
| camp_name_mi18n | str | 阵营名称 | |
| avatar_profession | num | 职业 | 数值枚举 |
| rarity | str | 稀有度 | `S` / `A` 等 |
| group_icon_path | str | 阵营图标 | |
| hollow_icon_path | str | 头像（空洞风格） | |
| rank | num | 影画数量 | 代理人详情「影画」 |
| is_chosen | bool | 是否展示收藏 | |
| role_square_url | str | 方形头像 | |
| sub_element_type | num | 副属性类型 | |
| awaken_state | str | 觉醒状态 | 如 `AwakenStateNotVisible` |

`data`对象→`buddy_list`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| id | num | 邦布 ID | |
| name | str | 名称 | |
| rarity | str | 稀有度 | |
| level | num | 等级 | |
| star | num | 星级 | |
| bangboo_rectangle_url | str | 矩形图标 | |

`data`对象→`game_data_show`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| personal_title | str | 个人称号 | |
| title_main_color | str | 称号主色 | |
| title_bottom_color | str | 称号底色 | |
| title_bg_url | str | 称号背景 | |
| medal_list | arr | 勋章图标 URL 列表 | 字符串数组 |
| card_url | str | 名片 URL | |
| medal_item_list | arr | 待调查 | |
| all_medal_list | arr | 全部勋章详情 | |
| title_id | num | 称号 ID | |
| title_material | str | 称号素材 | |

`data`对象→`game_data_show`对象→`all_medal_list`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| medal_icon | str | 图标 | |
| number | num | 数值 | |
| medal_type | str | 类型 | |
| name | str | 名称 | |
| is_show | bool | 是否展示 | |
| medal_id | num | ID | |
| no_injured | bool | 是否无伤相关 | |
| number_str | str | 数值字符串 | |
| is_show_percent | bool | 是否以百分比展示 | |

`data`对象→`area_collections`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| urban_area_id | num | 城区 ID | |
| urban_area_group_id | num | 城区组 ID | |
| is_lock | bool | 是否锁定 | |
| name | str | 名称 | |
| icon | str | 图标 | |
| collection_progress | num | 收集进度 | |

`data`对象→`challenge_schedule_list`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| challenge_type | str | 挑战类型 | 字符串枚举 |
| start_ts | str | 开始时间戳 | 字符串形式的 Unix 秒 |
| end_ts | str | 结束时间戳 | 字符串形式的 Unix 秒 |

<details>
<summary>查看示例</summary>

```json
{
  "retcode": 0,
  "message": "OK",
  "data": {
    "stats": {
      "active_days": 489,
      "avatar_num": 46,
      "world_level_name": "传奇绳匠",
      "buddy_num": 30,
      "achievement_count": 341,
      "memory_battlefield": {
        "rank_percent": 697,
        "total_score": 144946,
        "total_star": 9,
        "zone_id": 690421,
        "has_hard": true,
        "hard_rank_percent": 1898,
        "hard_total_score": 31361,
        "hard_total_star": 3
      },
      "void_front_brief": {
        "void_front_id": 201,
        "has_ending_record": true,
        "ending_record_name": "结局一·侦探不止一个！",
        "total_score": 235828,
        "rank_percent": 4356
      },
      "hadal_brief": {
        "hadal_ver": "v2",
        "hadal_brief_v2": {
          "cur_period_zone_layer_count": 5,
          "score": 113656,
          "rank_percent": 2394,
          "rating": "S+",
          "max_score": 150000
        }
      },
      "holo_boss_brief": {
        "unlock": true,
        "no_injured_boss_num": 0
      }
    },
    "avatar_list": [
      {
        "id": 1581,
        "level": 60,
        "name_mi18n": "蕾米埃尔",
        "full_name_mi18n": "蕾米埃尔·丹",
        "element_type": 300,
        "camp_name_mi18n": "达识结社",
        "avatar_profession": 3,
        "rarity": "S",
        "rank": 2,
        "is_chosen": false,
        "role_square_url": "https://act-webstatic.mihoyo.com/game_record/zzzv2/role_square_avatar/role_square_avatar_1581.png",
        "sub_element_type": 0,
        "awaken_state": "AwakenStateNotVisible"
      }
    ],
    "cur_head_icon_url": "https://...",
    "buddy_list": [],
    "cat_notes_list": [],
    "award_state": "",
    "game_data_show": {
      "personal_title": "",
      "medal_list": [],
      "all_medal_list": []
    },
    "area_collections": [],
    "challenge_schedule_list": []
  }
}
```

</details>

---

<h3 id="zzz-dailynote">获取实时便笺信息</h3>

对应战绩页「实时便笺」：电量、今日活跃度、饼铺盲盒/刮刮卡/占卜、录像店经营、悬赏委托、丽都周纪、绳网会员、百通宝等。

**国服：**

_请求方式：GET_

> _需要验证Cookie_
>
> LToken

`https://api-takumi-record.mihoyo.com/event/game_record_zzz/api/zzz/note`

**国际服：**

_请求方式：GET_

`https://sg-public-api.hoyolab.com/event/game_record_zzz/api/zzz/note`

**参数：**

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| role_id | num | 绝区零 UID | |
| server | str | 服务器名称 | |

**JSON返回：**

根对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| retcode | num | 返回码 | |
| message | str | 返回消息 | |
| data | obj | 实时便笺 | |

`data`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| energy | obj | **电量** | 便笺顶部 `current/max`，如 `55/240` |
| vitality | obj | **今日活跃度** | 日任务分组 |
| vhs_sale | obj | **录像店经营** | 状态文案见枚举 |
| card_sign | str | **饼铺盲盒 / 刮刮卡 / 占卜** | 日任务一项；见枚举 |
| bounty_commission | obj | **悬赏委托进度** | 与零号空洞委托同源展示；可为 null |
| survey_points | null/obj | 待调查 | 可为 null |
| abyss_refresh | num | 周期玩法刷新剩余秒数 | 便笺「X 天 X 小时后刷新」类倒计时 |
| coffee | null/obj | 待调查 | 可为 null |
| weekly_task | obj | **丽都周纪获取积分** | |
| member_card | obj | **绳网会员** | |
| is_sub | bool | 是否订阅相关 | |
| is_other_sub | bool | 是否他人订阅视角 | |
| temple_running | obj | **百通宝** | 含「自动托管」等 |
| cafe_state | str | **菲林已领取**状态 | 如 `CafeStateDone` 对应便笺「菲林已领取 / 已完成」 |

`data`对象→`energy`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| progress | obj | 当前 / 上限 | 便笺「电量」 |
| restore | num | 回满所需秒数 | |
| day_type | num | 回满落在哪一天 | `1` 今日；`2` 明日（文案「明日 HH:MM 回满」） |
| hour | num | 回满时刻（时） | |
| minute | num | 回满时刻（分） | |

`data`对象→`energy`对象→`progress`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| max | num | 电量上限 | 如 240 |
| current | num | 当前电量 | |

`data`对象→`vitality`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| max | num | 今日活跃度上限 | 如 400 |
| current | num | 当前今日活跃度 | |

`data`对象→`vhs_sale`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| sale_state | str | 录像店经营状态 | 见枚举 |

> `vhs_sale.sale_state` 与便笺文案对照：
>
> * `SaleStateNo`：等待营业
> * `SaleStateDoing`：**正在营业**
> * `SaleStateDone`：**待结算**

> `card_sign` 枚举：
>
> * `CardSignNo`：未完成
> * `CardSignDone`：已完成

`data`对象→`bounty_commission`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| num | num | 悬赏委托当前进度 | |
| total | num | 目标总量 | 如 8000 |
| refresh_time | num | 刷新剩余秒数 | 文案「X 天 X 小时后刷新」 |
| unlock | bool | 是否解锁 | |
| hide | bool | 是否隐藏 | |

`data`对象→`weekly_task`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| refresh_time | num | 刷新剩余秒数 | |
| cur_point | num | 丽都周纪当前积分 | |
| max_point | num | 积分上限 | |
| unlock | bool | 是否解锁 | |

`data`对象→`member_card`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| is_open | bool | 是否开通绳网会员 | |
| member_card_state | str | 状态 | 如 `MemberCardStateACK` |
| exp_time | str | 剩余可领取天数对应的秒数（字符串） | 便笺「剩余领取 N 天」 |

`data`对象→`temple_running`对象（百通宝）：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| expedition_state | str | 派遣状态 | |
| bench_state | str | 工位状态 | |
| shelve_state | str | 货架状态 | |
| level | num | 百通宝等级 | |
| weekly_currency_max | str | 周货币上限 | 字符串数字 |
| currency_next_refresh_ts | str | 下次刷新时间戳 | |
| current_currency | str | 当前货币 | |
| auto_work | obj | **自动托管** | |

`data`对象→`temple_running`对象→`auto_work`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| is_auto_work_running | bool | 自动托管是否运行中 | |
| auto_work_ended | bool | 自动托管是否已完成 | 便笺「已完成」 |
| left_ts | num | 剩余秒数 | |

<details>
<summary>查看示例</summary>

```json
{
  "retcode": 0,
  "message": "OK",
  "data": {
    "energy": {
      "progress": { "max": 240, "current": 55 },
      "restore": 66538,
      "day_type": 2,
      "hour": 15,
      "minute": 10
    },
    "vitality": { "max": 400, "current": 400 },
    "vhs_sale": { "sale_state": "SaleStateDoing" },
    "card_sign": "CardSignDone",
    "bounty_commission": {
      "num": 0,
      "total": 8000,
      "refresh_time": 544731,
      "unlock": true,
      "hide": false
    },
    "survey_points": null,
    "abyss_refresh": 544731,
    "coffee": null,
    "weekly_task": {
      "refresh_time": 544731,
      "cur_point": 100,
      "max_point": 2100,
      "unlock": true
    },
    "member_card": {
      "is_open": true,
      "member_card_state": "MemberCardStateACK",
      "exp_time": "16355930"
    },
    "is_sub": false,
    "is_other_sub": false,
    "temple_running": {
      "expedition_state": "ExpeditionStateUnknown",
      "bench_state": "BenchStateUnknown",
      "shelve_state": "ShelveStateUnknown",
      "level": 45,
      "weekly_currency_max": "5000",
      "currency_next_refresh_ts": "0",
      "current_currency": "0",
      "auto_work": {
        "is_auto_work_running": true,
        "auto_work_ended": true,
        "left_ts": 0
      }
    },
    "cafe_state": "CafeStateDone"
  }
}
```

</details>

---

<h3 id="zzz-avatar-basic">获取角色基础列表</h3>

返回账号拥有的代理人简要信息（不含驱动盘 / 音擎详情）。

**国服：**

_请求方式：GET_

> _需要验证Cookie_
>
> LToken

`https://api-takumi-record.mihoyo.com/event/game_record_zzz/api/zzz/avatar/basic`

**国际服：**

`https://sg-public-api.hoyolab.com/event/game_record_zzz/api/zzz/avatar/basic`

**参数：**

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| role_id | num | 绝区零 UID | |
| server | str | 服务器名称 | |

**JSON返回：**

根对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| retcode | num | 返回码 | |
| message | str | 返回消息 | |
| data | obj | 角色列表 | |

`data`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| avatar_list | arr | 代理人基础信息 | 字段同首页 `avatar_list` 单项 |

<details>
<summary>查看示例</summary>

```json
{
  "retcode": 0,
  "message": "OK",
  "data": {
    "avatar_list": [
      {
        "id": 1581,
        "level": 60,
        "name_mi18n": "蕾米埃尔",
        "full_name_mi18n": "蕾米埃尔·丹",
        "element_type": 300,
        "camp_name_mi18n": "达识结社",
        "avatar_profession": 3,
        "rarity": "S",
        "group_icon_path": "https://...",
        "hollow_icon_path": "https://...",
        "rank": 2,
        "is_chosen": false,
        "role_square_url": "https://act-webstatic.mihoyo.com/game_record/zzzv2/role_square_avatar/role_square_avatar_1581.png",
        "sub_element_type": 0,
        "awaken_state": "AwakenStateNotVisible"
      }
    ]
  }
}
```

</details>

---

<h3 id="zzz-avatar-info">获取角色详情</h3>

按代理人 ID 查询驱动盘、音擎、技能、影画、皮肤与属性面板等。

**国服：**

_请求方式：GET_

> _需要验证Cookie_
>
> LToken

`https://api-takumi-record.mihoyo.com/event/game_record_zzz/api/zzz/avatar/info`

**国际服：**

`https://sg-public-api.hoyolab.com/event/game_record_zzz/api/zzz/avatar/info`

**参数：**

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| role_id | num | 绝区零 UID | |
| server | str | 服务器名称 | |
| id_list[] | num | 代理人 ID | 可重复传递多个；URL 形如 `id_list[]=1581` |
| need_wiki | bool | 是否返回 wiki 字典 | 如 `true` |

**JSON返回：**

根对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| retcode | num | 返回码 | |
| message | str | 返回消息 | |
| data | obj | 角色详情 | |

`data`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| avatar_list | arr | 代理人详情列表 | |
| equip_wiki | obj | 驱动盘 wiki 链接字典 | key 为装备 ID 字符串 |
| weapon_wiki | obj | 音擎 wiki 链接字典 | |
| avatar_wiki | obj | 代理人 wiki 链接字典 | |
| strategy_wiki | obj | 攻略 wiki | |
| cultivate_index | obj/任意 | 养成相关 | 待调查 |
| cultivate_equip | obj/任意 | 养成相关 | 待调查 |
| special_skill_icon | obj/任意 | 特殊技能图标 | |

`data`对象→`avatar_list`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| id | num | 代理人 ID | |
| level | num | 等级 | |
| name_mi18n | str | 名称 | |
| full_name_mi18n | str | 全名 | |
| element_type | num | 属性 | |
| camp_name_mi18n | str | 阵营 | |
| avatar_profession | num | 职业 | |
| rarity | str | 稀有度 | |
| group_icon_path | str | 阵营图标 | |
| hollow_icon_path | str | 头像 | |
| equip | arr | **驱动盘**列表 | 详情页「驱动盘」 |
| weapon | obj | **音擎** | 如「空羽复归之诗」 |
| properties | arr | **代理人属性** / 基础属性 | `property_name` 为中文属性名 |
| skills | arr | **技能** | |
| rank | num | 已解锁影画数 | |
| ranks | arr | 影画详情 | |
| role_vertical_painting_url | str | 立绘 | |
| equip_plan_info | obj | 驱动盘方案 / 评分 | 详情页「切换方案」；含有效副属性命中 |
| us_full_name | str | 英文全名等 | |
| vertical_painting_color | str | 立绘主色 | |
| sub_element_type | num | 副属性 | |
| skin_list | arr | 皮肤 | |
| role_square_url | str | 方形头像 | |
| awaken_state | str | 觉醒状态 | |
| skill_awaken | obj | 技能觉醒 | |

`data`对象→`avatar_list`数组→对象→`equip`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| id | num | 驱动盘 ID | |
| level | num | 等级 | |
| name | str | 名称 | |
| icon | str | 图标 | |
| rarity | str | 稀有度 | |
| properties | arr | 副词条 | |
| main_properties | arr | 主词条 | |
| equip_suit | obj | 套装信息 | |
| equipment_type | num | 部位 | |
| invalid_property_cnt | num | 未命中方案的副属性次数 | 详情文案「未命中 N 次」 |
| all_hit | bool | 是否全部命中方案 | |

`data`对象→`avatar_list`数组→对象→`equip`数组→对象→`properties`/`main_properties`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| property_name | str | 属性名 | |
| property_id | num | 属性 ID | |
| base | str | 数值 | 字符串 |
| level | num | 强化等级 | |
| valid | bool | 是否有效 | |
| system_id | num | 系统 ID | |
| add | num | 附加 | |

`data`对象→`avatar_list`数组→对象→`equip`数组→对象→`equip_suit`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| suit_id | num | 套装 ID | |
| name | str | 套装名 | |
| own | num | 已装备件数 | |
| desc1 | str | 2 件效果 | |
| desc2 | str | 4 件效果 | |

`data`对象→`avatar_list`数组→对象→`weapon`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| id | num | 音擎 ID | |
| level | num | 等级 | |
| name | str | 名称 | |
| star | num | 精炼 / 星级 | |
| icon | str | 图标 | |
| rarity | str | 稀有度 | |
| properties | arr | 属性 | 结构同驱动盘词条 |
| main_properties | arr | 主属性 | |
| talent_title | str | 天赋标题 | |
| talent_content | str | 天赋描述 | |
| profession | num | 职业限制 | |

`data`对象→`avatar_list`数组→对象→`properties`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| property_name | str | 属性名 | 如：生命值、攻击力、防御力、冲击力、暴击率、暴击伤害、异常掌控、异常精通、穿透率、能量自动回复 |
| property_id | num | 属性 ID | 如 `1`–`11` |
| base | str | 基础值 | |
| add | str | 加成值 | |
| final | str | 最终值 | 详情页展示 |

`data`对象→`avatar_list`数组→对象→`skills`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| level | num | 技能等级 | |
| skill_type | num | 技能类型 | |
| items | arr | 描述条目 | |
| awaken_state | str | 觉醒状态 | |

`data`对象→`avatar_list`数组→对象→`ranks`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| id | num | 影画 ID | |
| name | str | 名称 | |
| desc | str | 描述 | |
| pos | num | 位置 | |
| is_unlocked | bool | 是否解锁 | |

`data`对象→`avatar_list`数组→对象→`skin_list`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| skin_id | num | 皮肤 ID | |
| skin_name | str | 名称 | |
| skin_vertical_painting_url | str | 立绘 | |
| skin_square_url | str | 方图 | |
| skin_hollow_icon_path | str | 图标 | |
| skin_vertical_painting_color | str | 主色 | |
| unlocked | bool | 是否解锁 | |
| rarity | str | 稀有度 | |
| is_original | bool | 是否原皮 | |

---

<details>
<summary>查看示例（节选）</summary>

```json
{
  "retcode": 0,
  "message": "OK",
  "data": {
    "avatar_list": [
      {
        "id": 1581,
        "level": 60,
        "name_mi18n": "蕾米埃尔",
        "full_name_mi18n": "蕾米埃尔·丹",
        "element_type": 300,
        "camp_name_mi18n": "达识结社",
        "avatar_profession": 3,
        "rarity": "S",
        "rank": 2,
        "role_square_url": "https://act-webstatic.mihoyo.com/game_record/zzzv2/role_square_avatar/role_square_avatar_1581.png",
        "equip": [
          {
            "id": 34141,
            "level": 15,
            "name": "谶羽之誓[1]",
            "icon": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_u0f27d/4a03bec4f9762a883ee0e2e8784ed1b1.png",
            "rarity": "S",
            "properties": [
              {
                "property_name": "攻击力",
                "property_id": 12102,
                "base": "6%",
                "level": 2,
                "valid": true,
                "system_id": 121,
                "add": 1
              },
              {
                "property_name": "防御力",
                "property_id": 13102,
                "base": "9.6%",
                "level": 2,
                "valid": false,
                "system_id": 131,
                "add": 1
              }
            ],
            "main_properties": [
              {
                "property_name": "生命值",
                "property_id": 11103,
                "base": "2200",
                "level": 1,
                "valid": false,
                "system_id": 111,
                "add": 0
              }
            ],
            "equip_suit": {
              "suit_id": 34100,
              "name": "谶羽之誓",
              "own": 4,
              "desc1": "异常精通+30点。",
              "desc2": "装备者进入战场时，或被切换为当前操作中角色时，获得增益效果：异常精通提升50点，若装备者为<color=#FFA9DD>流明属性</color>，造成的属性异常伤害提升15%，持续15秒；\\n当装备者为非操作中角色时，则始终持有该增益效果。"
            },
            "equipment_type": 1,
            "invalid_property_cnt": 2,
            "all_hit": false
          },
          "... (3 total)"
        ],
        "weapon": {
          "id": 14158,
          "level": 60,
          "name": "空羽复归之诗",
          "star": 1,
          "icon": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_u0f27d/f1af9cffe1eced08be298670d2574948.png",
          "rarity": "S",
          "talent_title": "失乐园",
          "talent_content": "异常精通提升<color=#2BAD00>96</color>点；装备者触发<color=#FFA9DD>[异化]</color>反应时，自身获得属性异常伤害提升<color=#2BAD00>20%</color>的效果，并为全队角色施加造成的伤害提升<color=#2BAD00>30%</color>效果，效果均持续30秒，重复触发时刷新持续时间。",
          "profession": 3
        },
        "properties": [
          {
            "property_name": "生命值",
            "property_id": 1,
            "base": "7482",
            "add": "2872",
            "final": "10354"
          },
          {
            "property_name": "攻击力",
            "property_id": 2,
            "base": "1566",
            "add": "2393",
            "final": "3959"
          },
          {
            "property_name": "防御力",
            "property_id": 3,
            "base": "600",
            "add": "329",
            "final": "929"
          },
          {
            "property_name": "冲击力",
            "property_id": 4,
            "base": "",
            "add": "",
            "final": "83"
          },
          "... (5 total)"
        ],
        "skills": [
          {
            "level": 12,
            "skill_type": 0,
            "items": [
              {
                "title": "普通攻击：蹁跹",
                "text": "点按 <IconMap:Icon_Normal> 发动：\\n向前方进行至多四段攻击，造成<color=#FFA9DD>流明属性伤害</color>；\\n若普攻命中目标，招式结束后可为自身回复<span style=\"color: #fff\">[浮晖]</span></Term>；\\n第四段普攻结束后可为命中的敌人施加1个<color=#FFA9DD>[流明积蓄点]</color>。",
                "awaken": false
              },
              {
                "title": "普通攻击：独舞",
                "text": "长按 <IconMap:Icon_Normal> 发动：\\n向前方进行范围斩击，造成<color=#FFA9DD>流明属性伤害</color>；\\n若命中目标，招式结束后可为自身回复<color=#FFFFFF>[浮晖]</color>。",
                "awaken": false
              },
              {
                "title": "普通攻击：垂虹",
                "text": "当蕾米埃尔身上储存有<span style=\"color: #fff\">[虚曜]</span></Term>时，长按 <IconMap:Icon_Normal> 发动：\\n向前方发动大范围强力攻击，造成<color=#FFA9DD>流明属性伤害</color>；\\n招式结束后可为自身回复大量<color=#FFFFFF>[浮晖]</color>；\\n若命中目标，招式结束后可触发<span style=\"color: #fff\">[耀变]</span></Term>效果，倍率为<color=#2BAD00>160%</color>；\\n发动后会清空身上储存的所有<color=#FFFFFF>[虚曜]</color>。",
                "awaken": false
              },
              {
                "title": "普通攻击：惊鸿",
                "text": "当蕾米埃尔身上储存有<color=#FFFFFF>[虚曜]</color>，且自身处于<color=#FFFFFF>[映曜]</color>状态时，长按 <IconMap:Icon_Normal> 发动：\\n向前方发动大范围强力攻击，造成<color=#FFA9DD>流明属性伤害</color>；\\n招式结束后可为自身回复大量<color=#FFFFFF>[浮晖]</color>；\\n若命中目标，招式结束后可触发<color=#FFFFFF>[耀变]</color>效果，倍率为<color=#2BAD00>320%</color>；\\n发动后会清空身上储存的所有<color=#FFFFFF>[虚曜]</color>。",
                "awaken": false
              }
            ],
            "awaken_state": "AwakenStateNotVisible"
          },
          "... (3 total)"
        ],
        "ranks": [
          {
            "id": 1,
            "name": "青涩誓言",
            "desc": "进入战场时，蕾米埃尔获得3个特殊<span style=\"color: #fff\">[虚曜]</span></Term>，在勘域模式中此效果180秒内最多触发一次；\\n蕾米埃尔触发<span style=\"color: #fff\">[耀变]</span></Term>效果造成伤害时，无视目标50%的全属性伤害抗性；\\n发动<color=#FFFFFF>[支援技：花羽轮舞]</color>时，获得200点喧响值，18秒内最多触发1次此效果；\\n蕾米埃尔处于<span style=\"color: #fff\">[相变时流]</span></Term>状态下时，队伍中其他角色造成的属性异常伤害提升10%。",
            "pos": 1,
            "is_unlocked": true
          },
          "... (3 total)"
        ],
        "awaken_state": "AwakenStateNotVisible"
      }
    ],
    "equip_wiki": {
      "34141": "https://baike.mihoyo.com/zzz/wiki/content/2116/detail?bbs_presentation_style=fullscreen",
      "31342": "https://baike.mihoyo.com/zzz/wiki/content/191/detail?bbs_presentation_style=fullscreen"
    },
    "weapon_wiki": {
      "14158": "https://baike.mihoyo.com/zzz/wiki/content/2109/detail?bbs_presentation_style=fullscreen"
    },
    "avatar_wiki": {
      "1581": "https://baike.mihoyo.com/zzz/wiki/content/2076/detail?bbs_presentation_style=fullscreen"
    }
  }
}
```

</details>

<h3 id="zzz-shiyu">获取式舆防卫战信息</h3>

对应「式舆防卫战」（接口路径历史命名 `hadal`）。

**国服：**

_请求方式：GET_

> _需要验证Cookie_
>
> LToken

`https://api-takumi-record.mihoyo.com/event/game_record_zzz/api/zzz/hadal_info_v2`

**国际服：**

`https://sg-public-api.hoyolab.com/event/game_record_zzz/api/zzz/hadal_info_v2`

**参数：**

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| role_id | num | 绝区零 UID | |
| server | str | 服务器名称 | |
| schedule_type | num | 期次 | `1` 当期；`2` 上期 |
| need_all | bool | 是否需要完整数据 | 可选；示例为 `true` |
| without_v2_detail | bool | 是否省略 v2 层详情 | `true` 时省略层详情；`false` 返回完整明细 |

**JSON返回：**

根对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| retcode | num | 返回码 | |
| message | str | 返回消息 | |
| data | obj | 式舆数据 | |

`data`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| hadal_ver | str | 数据版本 | 如 `v2`；旧版可含 `hadal_info_v1` |
| hadal_info_v1 | obj | 旧版详情 | 可选 |
| hadal_info_v2 | obj | v2 详情 | |
| nick_name | str | 昵称 | |
| icon | str | 头像 | |

`data`对象→`hadal_info_v2`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| zone_id | num | 区域 / 期次 ID | |
| hadal_begin_time | obj | 开始时间 | 时间对象 |
| hadal_end_time | obj | 结束时间 | 时间对象 |
| pass_fifth_floor | bool | 是否通过第五层 | |
| brief | obj | 简报 | |
| fitfh_layer_detail | obj | 第五层详情 | 字段名字面量为 `fitfh` |
| fourth_layer_detail | obj | 第四层详情 | |
| begin_time | str | 开始时间戳字符串 | |
| end_time | str | 结束时间戳字符串 | |

`data`对象→`hadal_info_v2`对象→`brief`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| cur_period_zone_layer_count | num | 当期通关层数 | |
| score | num | 分数 | |
| rank_percent | num | 排名百分比 | 0.01% 单位 |
| rating | str | 评级 | |
| max_score | num | 满分 | |

`data`对象→`hadal_info_v2`对象→`fitfh_layer_detail`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| layer_challenge_info_list | arr | 第五层各节点挑战 | |

`data`对象→`hadal_info_v2`对象→`fitfh_layer_detail`对象→`layer_challenge_info_list`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| layer_id | num | 节点 ID | |
| rating | str | 评级 | |
| buffer | obj | Buff | `title` / `text` |
| score | num | 分数 | |
| avatar_list | arr | 出战代理人 | 简要字段 |
| buddy | obj | 出战邦布 | |
| monster_pic | str | 敌人图 | |
| max_score | num | 节点满分 | |
| challenge_time | obj | 挑战时间 | 时间对象 |

`data`对象→`hadal_info_v2`对象→`fourth_layer_detail`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| buffer | obj | Buff | |
| challenge_time | obj | 挑战时间 | |
| rating | str | 评级 | |
| layer_challenge_info_list | arr | 第四层节点 | 结构类似第五层 |

<details>
<summary>查看示例（节选）</summary>

```json
{
  "retcode": 0,
  "message": "OK",
  "data": {
    "hadal_ver": "v2",
    "hadal_info_v2": {
      "zone_id": 62053,
      "hadal_begin_time": {
        "year": 2026,
        "month": 7,
        "day": 24,
        "hour": 4,
        "minute": 0,
        "second": 0
      },
      "hadal_end_time": {
        "year": 2026,
        "month": 8,
        "day": 7,
        "hour": 3,
        "minute": 59,
        "second": 59
      },
      "pass_fifth_floor": true,
      "brief": {
        "cur_period_zone_layer_count": 5,
        "score": 107741,
        "rank_percent": 3284,
        "rating": "S+",
        "max_score": 150000
      },
      "fitfh_layer_detail": {
        "layer_challenge_info_list": [
          {
            "layer_id": 62053051,
            "rating": "S",
            "buffer": {
              "title": "终幕协奏",
              "text": "· 代理人的<color=#FFFFFF>[终结技]</color>、<color=#FFFFFF>[连携技]</color>造成的伤害提升40%。\\n· <color=#FFFFFF>[连携技]</color>命中敌人后，其失衡易伤倍率提升20%，失衡恢复速度降低15%，持续15秒，重复触发时刷新持续时间。"
            },
            "score": 42665,
            "avatar_list": [
              {
                "id": 1431,
                "level": 60,
                "rarity": "S",
                "element_type": 200,
                "avatar_profession": 1,
                "rank": 1,
                "role_square_url": "https://act-webstatic.mihoyo.com/game_record/zzzv2/role_square_avatar/role_square_avatar_1431.png",
                "sub_element_type": 4
              },
              "... (3 total)"
            ],
            "buddy": {
              "id": 54021,
              "rarity": "S",
              "level": 60,
              "bangboo_rectangle_url": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_ue005d/c233b63c6f02dd01c94725762feebc74.png"
            },
            "monster_pic": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_ue005d/5f369c40b2ea806b5271dd7b6117dae6.png",
            "max_score": 50000,
            "challenge_time": {
              "year": 2026,
              "month": 7,
              "day": 24,
              "hour": 23,
              "minute": 27,
              "second": 17
            }
          },
          "... (3 total)"
        ]
      },
      "fourth_layer_detail": {
        "buffer": {
          "title": "终幕协奏",
          "text": "· 代理人的<color=#FFFFFF>[终结技]</color>、<color=#FFFFFF>[连携技]</color>造成的伤害提升40%。\\n· <color=#FFFFFF>[连携技]</color>命中敌人后，其失衡易伤倍率提升20%，失衡恢复速度降低15%，持续15秒，重复触发时刷新持续时间。"
        },
        "challenge_time": {
          "year": 2026,
          "month": 7,
          "day": 24,
          "hour": 23,
          "minute": 23,
          "second": 39
        },
        "rating": "S",
        "layer_challenge_info_list": [
          {
            "layer_id": 62053041,
            "avatar_list": [
              {
                "id": 1431,
                "level": 60,
                "rarity": "S",
                "element_type": 200,
                "avatar_profession": 1,
                "rank": 1,
                "role_square_url": "https://act-webstatic.mihoyo.com/game_record/zzzv2/role_square_avatar/role_square_avatar_1431.png",
                "sub_element_type": 4
              },
              "... (3 total)"
            ],
            "buddy": {
              "id": 54021,
              "rarity": "S",
              "level": 60,
              "bangboo_rectangle_url": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_ue005d/c233b63c6f02dd01c94725762feebc74.png"
            },
            "challenge_time": {
              "year": 2026,
              "month": 7,
              "day": 24,
              "hour": 23,
              "minute": 23,
              "second": 39
            }
          },
          "... (2 total)"
        ]
      },
      "begin_time": "1784836800",
      "end_time": "1786046399"
    },
    "nick_name": "示例昵称",
    "icon": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_ue005d/a959c9810fc3a7b876451803d58d7f47.png"
  }
}
```

</details>

---

<h3 id="zzz-deadly-assault">获取危局强袭战信息</h3>

对应「危局强袭战」（接口路径 `hadal_mem_*`）。

**国服：**

_请求方式：GET_

> _需要验证Cookie_
>
> LToken

`https://api-takumi-record.mihoyo.com/event/game_record_zzz/api/zzz/hadal_mem_detail_v2`

**国际服：**

`https://sg-public-api.hoyolab.com/event/game_record_zzz/api/zzz/hadal_mem_detail_v2`

**参数：**

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| uid | num | 绝区零 UID | 参数名 `uid`（非 `role_id`） |
| region | str | 服务器名称 | 参数名 `region`（非 `server`） |
| schedule_type | num | 期次 | `1` 当期；`2` 上期 |

**JSON返回：**

根对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| retcode | num | 返回码 | |
| message | str | 返回消息 | |
| data | obj | 危局详情 | |

`data`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| start_time | obj | 开始时间 | 时间对象 |
| end_time | obj | 结束时间 | 时间对象 |
| rank_percent | num | 全服排名百分比 | 0.01% 单位 |
| list | arr | 普通节点记录 | |
| has_data | bool | 是否有数据 | |
| nick_name | str | 昵称 | |
| avatar_icon | str | 头像 | |
| total_score | num | 总分 | |
| total_star | num | 总星 | |
| zone_id | num | 期次 ID | |
| total_max_score | num | 本期满分 | |
| room_max_score | num | 单节点满分 | |
| has_hard | bool | 是否有绝境挑战 | |
| hard_list | arr | 绝境节点记录 | 结构同 `list` |
| hard_rank_percent | num | 绝境排名百分比 | |

`data`对象→`list`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| score | num | 分数 | |
| star | num | 星数 | |
| total_star | num | 该节点满星 | |
| challenge_time | obj | 挑战时间 | 时间对象 |
| boss | arr | BOSS 信息 | |
| buffer | arr | Buff 列表 | |
| avatar_list | arr | 出战代理人 | |
| buddy | obj | 出战邦布 | |

`data`对象→`list`数组→对象→`boss`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| icon | str | 图标 | |
| name | str | 名称 | |
| race_icon | str | 种族图标 | |
| bg_icon | str | 背景图 | |

`data`对象→`list`数组→对象→`buffer`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| icon | str | 图标 | |
| desc | str | 描述 | 可含 color 标签 |
| name | str | 名称 | |

`data`对象→`list`数组→对象→`avatar_list`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| id | num | 代理人 ID | |
| level | num | 等级 | |
| element_type | num | 属性 | |
| avatar_profession | num | 职业 | |
| rarity | str | 稀有度 | |
| rank | num | 影画 | |
| role_square_url | str | 方图 | |
| sub_element_type | num | 副属性 | |

`data`对象→`list`数组→对象→`buddy`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| id | num | 邦布 ID | |
| rarity | str | 稀有度 | |
| level | num | 等级 | |
| bangboo_rectangle_url | str | 图标 | |

<details>
<summary>查看示例（节选）</summary>

```json
{
  "retcode": 0,
  "message": "OK",
  "data": {
    "start_time": { "year": 2026, "month": 7, "day": 29, "hour": 4, "minute": 0, "second": 0 },
    "end_time": { "year": 2026, "month": 8, "day": 14, "hour": 3, "minute": 59, "second": 59 },
    "rank_percent": 697,
    "list": [
      {
        "score": 63025,
        "star": 3,
        "total_star": 3,
        "challenge_time": { "year": 2026, "month": 7, "day": 31, "hour": 19, "minute": 42, "second": 10 },
        "boss": [
          {
            "icon": "https://...",
            "name": "基塔布鲁·滞变畸兽",
            "race_icon": "https://...",
            "bg_icon": "https://..."
          }
        ],
        "buffer": [
          { "icon": "https://...", "desc": "...", "name": "勠力" }
        ],
        "avatar_list": [
          {
            "id": 1581,
            "level": 60,
            "element_type": 300,
            "avatar_profession": 3,
            "rarity": "S",
            "rank": 2,
            "role_square_url": "https://...",
            "sub_element_type": 0
          }
        ],
        "buddy": {
          "id": 54022,
          "rarity": "S",
          "level": 60,
          "bangboo_rectangle_url": "https://..."
        }
      }
    ],
    "has_data": true,
    "nick_name": "示例昵称",
    "avatar_icon": "https://...",
    "total_score": 144946,
    "total_star": 9,
    "zone_id": 690421,
    "total_max_score": 195000,
    "room_max_score": 65000,
    "has_hard": true,
    "hard_list": [],
    "hard_rank_percent": 1898
  }
}
```

</details>

---

<h3 id="zzz-deadly-assault-abstract">获取危局强袭战摘要</h3>

摘要信息（分数、星数、排名），不含完整出战明细。

**国服：**

_请求方式：GET_

> _需要验证Cookie_
>
> LToken

`https://api-takumi-record.mihoyo.com/event/game_record_zzz/api/zzz/hadal_mem_abstract_info`

**参数：**

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| uid | num | 绝区零 UID | |
| region | str | 服务器名称 | |
| schedule_type | num | 期次 | `1` 当期；`2` 上期 |

**JSON返回：**

`data`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| nick_name | str | 昵称 | |
| avatar_icon | str | 头像 | |
| list | arr | 摘要列表 | |
| start_time | obj | 开始时间 | 时间对象 |
| end_time | obj | 结束时间 | 时间对象 |
| total_max_score | num | 本期满分 | |
| room_max_score | num | 单节点满分 | |

`data`对象→`list`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| score | num | 分数 | |
| star | num | 星数 | |
| nest_type | str | 类型 | 如 `General` |
| rank | num | 排名相关 | |

<details>
<summary>查看示例</summary>

```json
{
  "retcode": 0,
  "message": "OK",
  "data": {
    "nick_name": "示例昵称",
    "avatar_icon": "https://...",
    "list": [
      { "score": 92919, "star": 9, "nest_type": "General", "rank": 2099 }
    ],
    "start_time": { "year": 2026, "month": 7, "day": 17, "hour": 4, "minute": 0, "second": 0 },
    "end_time": { "year": 2026, "month": 7, "day": 29, "hour": 3, "minute": 59, "second": 59 },
    "total_max_score": 195000,
    "room_max_score": 65000
  }
}
```

</details>

---

<h3 id="zzz-threshold-abstract">获取临界推演摘要</h3>

对应「临界推演」（接口路径 `void_front_*`）。

**国服：**

_请求方式：GET_

> _需要验证Cookie_
>
> LToken

`https://api-takumi-record.mihoyo.com/event/game_record_zzz/api/zzz/void_front_battle_abstract_info`

**国际服：**

`https://sg-public-api.hoyolab.com/event/game_record_zzz/api/zzz/void_front_battle_abstract_info`

**参数：**

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| uid | num | 绝区零 UID | |
| region | str | 服务器名称 | |

**JSON返回：**

`data`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| has_detail_record | bool | 是否有详情记录 | |
| void_front_battle_abstract_info_brief | obj | 简报 | |

`data`对象→`void_front_battle_abstract_info_brief`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| void_front_id | num | 期次 ID | 拉详情使用 |
| end_ts_over_42_days | bool | 结束是否超过约 42/43 天 | |
| end_ts | num | 结束 Unix 时间戳 | |
| has_ending_record | bool | 是否完成结局 | |
| ending_record_name | str | 结局名称 | |
| ending_record_bg_pic | str | 结局背景图 | |
| total_score | num | 总分 | |
| rank_percent | num | 排名百分比 | |
| max_score | num | 满分 | |
| left_ts | num | 剩余秒数 | |
| ending_record_id | num | 结局 ID | |

---


<details>
<summary>查看示例</summary>

```json
{
  "retcode": 0,
  "message": "OK",
  "data": {
    "has_detail_record": true,
    "void_front_battle_abstract_info_brief": {
      "void_front_id": 201,
      "end_ts_over_42_days": true,
      "end_ts": 0,
      "has_ending_record": true,
      "ending_record_name": "结局一·侦探不止一个！",
      "ending_record_bg_pic": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_ue005d/ef4e7b86d70766ce95a0b0faaf7fbad6.png",
      "total_score": 235828,
      "rank_percent": 4357,
      "max_score": 481000,
      "left_ts": 0,
      "ending_record_id": 4,
      "start_time": {
        "year": 2026,
        "month": 2,
        "day": 5,
        "hour": 4,
        "minute": 0,
        "second": 0
      },
      "end_time": null
    }
  }
}
```

</details>

<h3 id="zzz-threshold-detail">获取临界推演详情</h3>

**国服：**

_请求方式：GET_

> _需要验证Cookie_
>
> LToken

`https://api-takumi-record.mihoyo.com/event/game_record_zzz/api/zzz/void_front_battle_detail`

**国际服：**

`https://sg-public-api.hoyolab.com/event/game_record_zzz/api/zzz/void_front_battle_detail`

**参数：**

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| uid | num | 绝区零 UID | |
| region | str | 服务器名称 | |
| void_front_id | num | 临界推演期次 ID | 来自摘要 / 首页 `void_front_brief.void_front_id` |

**JSON返回：**

`data`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| void_front_battle_abstract_info_brief | obj | 简报 | 字段同摘要 brief |
| boss_challenge_record | obj | BOSS 节点记录 | |
| main_challenge_record_list | arr | 前置 / 主线节点记录 | |
| role_basic_info | obj | 账号展示信息 | |

节点记录字段（`main_challenge_record` / 列表项）：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| battle_id | num | 战斗 ID | |
| node_id | num | 节点 ID | |
| name | str | 节点名 | |
| score | num | 分数 | |
| star | str | 星级（字符串） | |
| score_ratio | str | 分数倍率等 | |
| challenge_time | obj | 挑战时间 | 时间对象 |
| buffer | obj | Buff | `icon` / `desc` / `name` |
| max_score | num | 满分 | |
| avatar_list | arr | 出战代理人 | |
| buddy | obj | 邦布 | |
| sub_challenge_record | arr | 子挑战 | 可选 |

---


<details>
<summary>查看示例（节选）</summary>

```json
{
  "retcode": 0,
  "message": "OK",
  "data": {
    "void_front_battle_abstract_info_brief": {
      "void_front_id": 201,
      "end_ts_over_42_days": true,
      "end_ts": 0,
      "has_ending_record": true,
      "ending_record_name": "结局一·侦探不止一个！",
      "ending_record_bg_pic": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_ue005d/ef4e7b86d70766ce95a0b0faaf7fbad6.png",
      "total_score": 235828,
      "rank_percent": 4357,
      "max_score": 481000,
      "left_ts": 0,
      "ending_record_id": 4,
      "start_time": {
        "year": 2026,
        "month": 2,
        "day": 5,
        "hour": 4,
        "minute": 0,
        "second": 0
      },
      "end_time": null
    },
    "boss_challenge_record": {
      "boss_info": {
        "icon": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_ue005d/99ce6d515edb42905414a1cfa05fee98.png",
        "name": "叛律孤歌·???",
        "race_icon": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_ue005d/4a0c564782a2084b9fe88abeadb913ba.png",
        "bg_icon": "https://act-webstatic.mihoyo.com/game_record/zzzv2/boss_bg/boss_bg_4.png"
      },
      "main_challenge_record": {
        "battle_id": 2010401,
        "node_id": 20104,
        "name": "LAST STAGE",
        "score": 62203,
        "star": "S",
        "score_ratio": "2.5",
        "challenge_time": {
          "year": 2026,
          "month": 3,
          "day": 11,
          "hour": 11,
          "minute": 46,
          "second": 36
        },
        "buffer": {
          "icon": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_ue005d/d3f4b45b9dda3de0094228efbe914551.png",
          "desc": "· 代理人的生命值上限<color=#2BAD00>提升30%</color>，终结技造成的伤害<color=#2BAD00>提升40%</color>。\\n· 代理人释放终结技后，能量和闪能获得效率 <color=#2BAD00>提升15%</color>，<color=#FE437E>以太属性伤害</color>和<color=#98EFF0>冰属性伤害</color><color=#2BAD00>提升40%</color>，持续20秒。",
          "name": "凝神"
        },
        "max_score": 182000,
        "avatar_list": [
          {
            "id": 1451,
            "level": 60,
            "element_type": 205,
            "avatar_profession": 4,
            "rarity": "S",
            "rank": 0,
            "role_square_url": "https://act-webstatic.mihoyo.com/game_record/zzzv2/role_square_avatar/role_square_avatar_1451.png",
            "sub_element_type": 0
          },
          "... (3 total)"
        ],
        "buddy": {
          "id": 54017,
          "rarity": "S",
          "level": 60,
          "bangboo_rectangle_url": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_ue005d/092e16be49985ad9551ac8d48851789b.png"
        },
        "sub_challenge_record": [
          {
            "battle_id": 2010403,
            "name": "3-1",
            "star": "S",
            "avatar_list": [
              {
                "id": 1091,
                "level": 60,
                "element_type": 202,
                "avatar_profession": 3,
                "rarity": "S",
                "rank": 0,
                "role_square_url": "https://act-webstatic.mihoyo.com/game_record/zzzv2/role_square_avatar/role_square_avatar_1091.png",
                "sub_element_type": 1
              },
              "... (3 total)"
            ],
            "buddy": {
              "id": 54001,
              "rarity": "S",
              "level": 60,
              "bangboo_rectangle_url": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_ue005d/f71b2752338a0dce92135950285b3cd7.png"
            },
            "buffer": {
              "icon": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_ue005d/a651daede18a66f047e809d57020dcac.png",
              "desc": "· 代理人的属性异常积蓄效率<color=#2BAD00>提升20%</color>。\\n· 对敌人施加<color=#FFFFFF>属性异常</color>效果时，全队<color=#2BAD00>提升60点异常精通</color>，<color=#FFFFFF>紊乱</color>造成的伤害<color=#2BAD00>提升40%</color>，持续15秒。",
              "name": "异象"
            }
          },
          "... (3 total)"
        ]
      }
    },
    "main_challenge_record_list": [
      {
        "battle_id": 2010201,
        "node_id": 20102,
        "name": "STAGE 02",
        "score": 96763,
        "star": "S",
        "score_ratio": "2.3",
        "challenge_time": {
          "year": 2026,
          "month": 3,
          "day": 11,
          "hour": 11,
          "minute": 20,
          "second": 9
        },
        "buffer": {
          "icon": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_ue005d/b5a0e3332e152e377984684296fb255d.png",
          "desc": "· 代理人的攻击力<color=#2BAD00>提升16%</color>，敌人的失衡易伤倍率<color=#2BAD00>提升30%</color>。\\n· 处于以太帷幕中的代理人，攻击命中敌人时无视其<color=#2BAD00>10%</color>的<color=#F0D12B>物理属性伤害抗性</color>和<color=#2BAD00>15%</color>的防御力。",
          "name": "聚气"
        },
        "max_score": 149500,
        "avatar_list": [
          {
            "id": 1431,
            "level": 60,
            "element_type": 200,
            "avatar_profession": 1,
            "rarity": "S",
            "rank": 1,
            "role_square_url": "https://act-webstatic.mihoyo.com/game_record/zzzv2/role_square_avatar/role_square_avatar_1431.png",
            "sub_element_type": 4
          },
          "... (3 total)"
        ],
        "buddy": {
          "id": 54021,
          "rarity": "S",
          "level": 60,
          "bangboo_rectangle_url": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_ue005d/c233b63c6f02dd01c94725762feebc74.png"
        },
        "sub_challenge_record": [
          {
            "battle_id": 2010202,
            "name": "2-1",
            "star": "S",
            "avatar_list": [
              {
                "id": 1451,
                "level": 60,
                "element_type": 205,
                "avatar_profession": 4,
                "rarity": "S",
                "rank": 0,
                "role_square_url": "https://act-webstatic.mihoyo.com/game_record/zzzv2/role_square_avatar/role_square_avatar_1451.png",
                "sub_element_type": 0
              },
              "... (3 total)"
            ],
            "buddy": {
              "id": 54017,
              "rarity": "S",
              "level": 60,
              "bangboo_rectangle_url": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_ue005d/092e16be49985ad9551ac8d48851789b.png"
            },
            "buffer": {
              "icon": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_ue005d/d3f4b45b9dda3de0094228efbe914551.png",
              "desc": "· 代理人的喧响值获取效率<color=#2BAD00>提升20%</color>。\\n·<color=#FFFFFF>[终结技]</color>和<color=#FFFFFF>[强化特殊技]</color>命中敌人时，无视其<color=#2BAD00>20%</color>的伤害抗性，<color=#FFFFFF>[终结技]</color>命中敌人后，代理人的<color=#FFFFFF>[终结技]</color>和<color=#FFFFFF>[强化特殊技]</color>造成的伤害<color=#2BAD00>提升50%</color>，持续30秒，重复触发时刷新持续时间。",
              "name": "奏鸣"
            }
          },
          "... (3 total)"
        ]
      },
      "... (2 total)"
    ],
    "role_basic_info": {
      "server": "prod_gf_cn",
      "nickname": "示例昵称",
      "icon": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_ue005d/a959c9810fc3a7b876451803d58d7f47.png"
    }
  }
}
```

</details>

<h3 id="zzz-threshold-period">获取临界推演周期详情</h3>

按 `schedule_type` 拉取某一周期的完整战斗详情。

**国服：**

_请求方式：GET_

> _需要验证Cookie_
>
> LToken

`https://api-takumi-record.mihoyo.com/event/game_record_zzz/api/zzz/void_front_battle_period_detail`

**参数：**

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| uid | num | 绝区零 UID | |
| region | str | 服务器名称 | |
| schedule_type | num | 期次 | `1` 当期等 |

**JSON返回：**

`data`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| void_front_id | num | 期次 ID | |
| void_front_battle_detail | obj | 详情 | 结构与 [获取临界推演详情](#zzz-threshold-detail) 的 `data` 相近 |

---

<details>
<summary>查看示例（节选）</summary>

```json
{
  "retcode": 0,
  "message": "OK",
  "data": {
    "void_front_id": 201,
    "void_front_battle_detail": {
      "void_front_battle_abstract_info_brief": {
        "void_front_id": 201,
        "end_ts_over_42_days": true,
        "end_ts": 0,
        "has_ending_record": true,
        "ending_record_name": "结局一·侦探不止一个！",
        "ending_record_bg_pic": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_ue005d/ef4e7b86d70766ce95a0b0faaf7fbad6.png",
        "total_score": 235828,
        "rank_percent": 4357,
        "max_score": 481000,
        "left_ts": 0,
        "ending_record_id": 4,
        "start_time": {
          "year": 2026,
          "month": 2,
          "day": 5,
          "hour": 4,
          "minute": 0,
          "second": 0
        },
        "end_time": null
      },
      "boss_challenge_record": {
        "boss_info": {
          "icon": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_ue005d/99ce6d515edb42905414a1cfa05fee98.png",
          "name": "叛律孤歌·???",
          "race_icon": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_ue005d/4a0c564782a2084b9fe88abeadb913ba.png",
          "bg_icon": "https://act-webstatic.mihoyo.com/game_record/zzzv2/boss_bg/boss_bg_4.png"
        },
        "main_challenge_record": {
          "battle_id": 2010401,
          "node_id": 20104,
          "name": "LAST STAGE",
          "score": 62203,
          "star": "S",
          "score_ratio": "2.5",
          "challenge_time": {
            "year": 2026,
            "month": 3,
            "day": 11,
            "hour": 11,
            "minute": 46,
            "second": 36
          },
          "buffer": {
            "icon": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_ue005d/d3f4b45b9dda3de0094228efbe914551.png",
            "desc": "· 代理人的生命值上限<color=#2BAD00>提升30%</color>，终结技造成的伤害<color=#2BAD00>提升40%</color>。\\n· 代理人释放终结技后，能量和闪能获得效率 <color=#2BAD00>提升15%</color>，<color=#FE437E>以太属性伤害</color>和<color=#98EFF0>冰属性伤害</color><color=#2BAD00>提升40%</color>，持续20秒。",
            "name": "凝神"
          },
          "max_score": 182000,
          "avatar_list": [
            {
              "id": 1451,
              "level": 60,
              "element_type": 205,
              "avatar_profession": 4,
              "rarity": "S",
              "rank": 0,
              "role_square_url": "https://act-webstatic.mihoyo.com/game_record/zzzv2/role_square_avatar/role_square_avatar_1451.png",
              "sub_element_type": 0
            },
            "... (3 total)"
          ],
          "buddy": {
            "id": 54017,
            "rarity": "S",
            "level": 60,
            "bangboo_rectangle_url": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_ue005d/092e16be49985ad9551ac8d48851789b.png"
          },
          "sub_challenge_record": [
            {
              "battle_id": 2010403,
              "name": "3-1",
              "star": "S",
              "avatar_list": [
                {
                  "id": 1091,
                  "level": 60,
                  "element_type": 202,
                  "avatar_profession": 3,
                  "rarity": "S",
                  "rank": 0,
                  "role_square_url": "https://act-webstatic.mihoyo.com/game_record/zzzv2/role_square_avatar/role_square_avatar_1091.png",
                  "sub_element_type": 1
                },
                "... (3 total)"
              ],
              "buddy": {
                "id": 54001,
                "rarity": "S",
                "level": 60,
                "bangboo_rectangle_url": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_ue005d/f71b2752338a0dce92135950285b3cd7.png"
              },
              "buffer": {
                "icon": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_ue005d/a651daede18a66f047e809d57020dcac.png",
                "desc": "· 代理人的属性异常积蓄效率<color=#2BAD00>提升20%</color>。\\n· 对敌人施加<color=#FFFFFF>属性异常</color>效果时，全队<color=#2BAD00>提升60点异常精通</color>，<color=#FFFFFF>紊乱</color>造成的伤害<color=#2BAD00>提升40%</color>，持续15秒。",
                "name": "异象"
              }
            },
            "... (3 total)"
          ]
        }
      },
      "main_challenge_record_list": [
        {
          "battle_id": 2010201,
          "node_id": 20102,
          "name": "STAGE 02",
          "score": 96763,
          "star": "S",
          "score_ratio": "2.3",
          "challenge_time": {
            "year": 2026,
            "month": 3,
            "day": 11,
            "hour": 11,
            "minute": 20,
            "second": 9
          },
          "buffer": {
            "icon": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_ue005d/b5a0e3332e152e377984684296fb255d.png",
            "desc": "· 代理人的攻击力<color=#2BAD00>提升16%</color>，敌人的失衡易伤倍率<color=#2BAD00>提升30%</color>。\\n· 处于以太帷幕中的代理人，攻击命中敌人时无视其<color=#2BAD00>10%</color>的<color=#F0D12B>物理属性伤害抗性</color>和<color=#2BAD00>15%</color>的防御力。",
            "name": "聚气"
          },
          "max_score": 149500,
          "avatar_list": [
            {
              "id": 1431,
              "level": 60,
              "element_type": 200,
              "avatar_profession": 1,
              "rarity": "S",
              "rank": 1,
              "role_square_url": "https://act-webstatic.mihoyo.com/game_record/zzzv2/role_square_avatar/role_square_avatar_1431.png",
              "sub_element_type": 4
            },
            "... (3 total)"
          ],
          "buddy": {
            "id": 54021,
            "rarity": "S",
            "level": 60,
            "bangboo_rectangle_url": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_ue005d/c233b63c6f02dd01c94725762feebc74.png"
          },
          "sub_challenge_record": [
            {
              "battle_id": 2010202,
              "name": "2-1",
              "star": "S",
              "avatar_list": [
                {
                  "id": 1451,
                  "level": 60,
                  "element_type": 205,
                  "avatar_profession": 4,
                  "rarity": "S",
                  "rank": 0,
                  "role_square_url": "https://act-webstatic.mihoyo.com/game_record/zzzv2/role_square_avatar/role_square_avatar_1451.png",
                  "sub_element_type": 0
                },
                "... (3 total)"
              ],
              "buddy": {
                "id": 54017,
                "rarity": "S",
                "level": 60,
                "bangboo_rectangle_url": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_ue005d/092e16be49985ad9551ac8d48851789b.png"
              },
              "buffer": {
                "icon": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_ue005d/d3f4b45b9dda3de0094228efbe914551.png",
                "desc": "· 代理人的喧响值获取效率<color=#2BAD00>提升20%</color>。\\n·<color=#FFFFFF>[终结技]</color>和<color=#FFFFFF>[强化特殊技]</color>命中敌人时，无视其<color=#2BAD00>20%</color>的伤害抗性，<color=#FFFFFF>[终结技]</color>命中敌人后，代理人的<color=#FFFFFF>[终结技]</color>和<color=#FFFFFF>[强化特殊技]</color>造成的伤害<color=#2BAD00>提升50%</color>，持续30秒，重复触发时刷新持续时间。",
                "name": "奏鸣"
              }
            },
            "... (3 total)"
          ]
        },
        "... (2 total)"
      ],
      "role_basic_info": {
        "server": "prod_gf_cn",
        "nickname": "示例昵称",
        "icon": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_ue005d/a959c9810fc3a7b876451803d58d7f47.png"
      }
    }
  }
}
```

</details>

<h3 id="zzz-month-info">获取绳网月报</h3>

对应「绳网月报 / 开拓月历」类收入总结（菲林、母带、邦布券等）。

**国服：**

_请求方式：GET_

> _需要验证Cookie_
>
> LToken

`https://api-takumi.mihoyo.com/event/nap_ledger/month_info`

**国际服：**

`https://sg-public-api.hoyolab.com/event/nap_ledger/month_info`

**参数：**

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| uid | num | 绝区零 UID | |
| region | str | 服务器名称 | |
| month | str | 月份 | 格式 `yyyyMM`，如 `202608`；空字符串表示当前月 |

**JSON返回：**

`data`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| uid | str | UID | 字符串 |
| region | str | 服务器 | |
| current_month | str | 当前月 | `yyyyMM` |
| data_month | str | 数据所属月 | |
| month_data | obj | 月数据 | |
| optional_month | arr | 可选月份列表 | 字符串数组 |
| role_info | obj | 角色展示 | |

`data`对象→`month_data`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| list | arr | 各资源类型合计 | |
| income_components | arr | 收入来源构成 | |

`data`对象→`month_data`对象→`list`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| data_type | str | 类型枚举 | 见下 |
| count | num | 数量 | |
| data_name | str | 显示名 | |

> `data_type` 取值：
>
> * `PolychromesData`：菲林
> * `MatserTapeData`：加密母带 & 原装母带（字面量为 `Matser`）
> * `BooponsData`：邦布券

`data`对象→`month_data`对象→`income_components`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| action | str | 来源动作 | 如 `daily_activity_rewards`、`shiyu_rewards` |
| num | num | 数量 | |
| percent | num | 占比 | |

`data`对象→`role_info`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| nickname | str | 昵称 | |
| avatar | str | 头像 | |

<details>
<summary>查看示例</summary>

```json
{
  "retcode": 0,
  "message": "OK",
  "data": {
    "uid": "100000001",
    "region": "prod_gf_cn",
    "current_month": "202608",
    "data_month": "202608",
    "month_data": {
      "list": [
        { "data_type": "PolychromesData", "count": 2935, "data_name": "菲林" },
        { "data_type": "MatserTapeData", "count": 20, "data_name": "加密母带 & 原装母带" },
        { "data_type": "BooponsData", "count": 0, "data_name": "邦布券" }
      ],
      "income_components": [
        { "action": "daily_activity_rewards", "num": 1600, "percent": 55 },
        { "action": "shiyu_rewards", "num": 780, "percent": 27 }
      ]
    },
    "optional_month": ["202608", "202607", "202606"],
    "role_info": {
      "nickname": "示例昵称",
      "avatar": "https://..."
    }
  }
}
```

</details>

---

<h3 id="zzz-month-detail">获取绳网月报详情</h3>

分页拉取某一资源类型的收入明细。

**国服：**

_请求方式：GET_

> _需要验证Cookie_
>
> LToken

`https://api-takumi.mihoyo.com/event/nap_ledger/month_detail`

**国际服：**

`https://sg-public-api.hoyolab.com/event/nap_ledger/month_detail`

**参数：**

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| uid | num | 绝区零 UID | |
| region | str | 服务器名称 | |
| month | str | 月份 | `yyyyMM` |
| type | str | 资源类型 | 同 `data_type`：`PolychromesData` / `MatserTapeData` / `BooponsData` |
| current_page | num | 页码 | 从 `1` 开始 |
| page_size | num | 每页条数 | 如 `20`；最大约 `100` |

**JSON返回：**

`data`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| uid | str | UID | |
| region | str | 服务器 | |
| data_month | str | 月份 | |
| current_page | num | 当前页 | |
| list | arr | 明细 | |
| total | num | 总条数 | |
| data_name | str | 资源显示名 | |
| data_type | str | 资源类型 | |

`data`对象→`list`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| id | str | 记录 ID | |
| action | str | 来源动作 | |
| time | str | Unix 时间戳（秒，字符串） | |
| num | num | 数量 | |

<details>
<summary>查看示例</summary>

```json
{
  "retcode": 0,
  "message": "OK",
  "data": {
    "uid": "100000001",
    "region": "prod_gf_cn",
    "data_month": "202608",
    "current_page": 1,
    "list": [
      {
        "id": "10000001",
        "action": "daily_activity_rewards",
        "time": "1700000000",
        "num": 20
      }
    ],
    "total": 95,
    "data_name": "菲林",
    "data_type": "PolychromesData"
  }
}
```

</details>

---

<h3 id="zzz-gacha-record">获取调频记录</h3>

战绩页「调频记录」。与游戏客户端 **public-operation** 抽卡接口（`common/gacha_record/api/getGachaLog`）不同：本接口使用 Cookie 鉴权，无需 authkey。

**国服：**

_请求方式：GET_

> _需要验证Cookie_
>
> LToken

`https://api-takumi-record.mihoyo.com/event/game_record_zzz/api/zzz/gacha_record`

**国际服：**

`https://sg-public-api.hoyolab.com/event/game_record_zzz/api/zzz/gacha_record`

**参数：**

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| uid | num | 绝区零 UID | |
| region | str | 服务器名称 | |
| gacha_type | str/num | 调频类型 | 字符串枚举或数字（见下表） |
| end_id | str/num | 分页游标 | 首次不传；下一页传上一页最后一条记录的 `id` |

> `gacha_type` 对照：
>
> | 字符串 | 数字 | 含义 |
> | --- | --- | --- |
> | `GACHA_TYPE_PERMANENT` | `1` | 常驻频段 |
> | `GACHA_TYPE_CHARACTER_UP` | `2` | 独家频段 |
> | `GACHA_TYPE_WEAPON_UP` | `3` | 音擎频段 |
> | `GACHA_TYPE_BANGBOO` | `5` | 邦布频段 |
> | `GACHA_TYPE_CHARACTER_RETURN` | `102` | 独家重映 |
> | `GACHA_TYPE_WEAPON_RETURN` | `103` | 音擎回响 |

**JSON返回：**

`data`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| gacha_item_list | arr | 记录列表 | 单页约 20 条 |
| has_more | bool | 是否还有下一页 | |

`data`对象→`gacha_item_list`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| id | str | 记录 ID | 用于 `end_id` 分页 |
| item_type | str | 物品类型 | 如 `ITEM_TYPE_WEAPON`、`ITEM_TYPE_AVATAR` 等 |
| item_id | num | 物品 ID | |
| item_name | str | 名称 | |
| rarity | str | 稀有度 | `S` / `A` / `B` 等 |
| date | obj | 获得时间 | 时间对象 |

<details>
<summary>查看示例</summary>

```json
{
  "retcode": 0,
  "message": "OK",
  "data": {
    "gacha_item_list": [
      {
        "id": "1700000000000000001",
        "item_type": "ITEM_TYPE_WEAPON",
        "item_id": 12003,
        "item_name": "「月相」-朔",
        "rarity": "B",
        "date": {
          "year": 2026,
          "month": 1,
          "day": 1,
          "hour": 12,
          "minute": 0,
          "second": 0
        }
      }
    ],
    "has_more": true
  }
}
```

</details>

---

<h3 id="zzz-cur-gacha">获取当前调频信息</h3>

当前卡池 UP、剩余抽数提示、可用票券数量等。

**国服：**

_请求方式：GET_

> _需要验证Cookie_
>
> LToken

`https://api-takumi-record.mihoyo.com/event/game_record_zzz/api/zzz/cur_gacha_detail`

**参数：**

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| uid | num | 绝区零 UID | |
| region | str | 服务器名称 | |

**JSON返回：**

`data`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| tickets | arr | 票券数量 | |
| gacha_info_list | arr | 各卡池摘要 | |
| record_show_gachas | arr | 记录页展示的卡池类型 | 字符串数组 |

`data`对象→`tickets`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| ticket_type | str | 票券类型 | 如 `GACHA_TICKET_TYPE_POLYCHROME` |
| ticket_cnt | num | 数量 | |

`data`对象→`gacha_info_list`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| gacha_type | str | 卡池类型 | |
| up_s_item_list | arr | 当期 UP 物品 | |
| sup_lock_show | bool | 是否展示锁定相关 | |
| more_s_need_cnt | num | 距离下一个 S 还需抽数 | 保底提示 |

`data`对象→`gacha_info_list`数组→对象→`up_s_item_list`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| item_type | str | `UP_S_ITEM_TYPE_AVATAR` / `UP_S_ITEM_TYPE_WEAPON` 等 | |
| avatar | obj | 代理人信息 | 角色 UP 时存在 |
| weapon | obj | 音擎信息 | 音擎 UP 时存在 |

---

<details>
<summary>查看示例</summary>

```json
{
  "retcode": 0,
  "message": "OK",
  "data": {
    "tickets": [
      {
        "ticket_type": "GACHA_TICKET_TYPE_RECHARGE_MONOCHROME",
        "ticket_cnt": 1380
      },
      {
        "ticket_type": "GACHA_TICKET_TYPE_POLYCHROME",
        "ticket_cnt": 45
      },
      "... (5 total)"
    ],
    "gacha_info_list": [
      {
        "gacha_type": "GACHA_TYPE_CHARACTER_UP",
        "up_s_item_list": [
          {
            "item_type": "UP_S_ITEM_TYPE_AVATAR",
            "avatar": {
              "avatar_id": 1581,
              "avatar_name": "蕾米埃尔",
              "rarity": "S",
              "icon": "https://act-webstatic.mihoyo.com/game_record/zzzv2/role_square_avatar/role_square_avatar_1581.png",
              "avatar_profession": 3,
              "avatar_element_type": 300,
              "avatar_sub_element_type": 0
            }
          },
          {
            "item_type": "UP_S_ITEM_TYPE_AVATAR",
            "avatar": {
              "avatar_id": 1501,
              "avatar_name": "爱芮",
              "rarity": "S",
              "icon": "https://act-webstatic.mihoyo.com/game_record/zzzv2/role_square_avatar/role_square_avatar_1501.png",
              "avatar_profession": 3,
              "avatar_element_type": 205,
              "avatar_sub_element_type": 0
            }
          }
        ],
        "sup_lock_show": false,
        "more_s_need_cnt": 64
      },
      {
        "gacha_type": "GACHA_TYPE_WEAPON_UP",
        "up_s_item_list": [
          {
            "item_type": "UP_S_ITEM_TYPE_WEAPON",
            "weapon": {
              "weapon_id": 14158,
              "weapon_name": "",
              "rarity": "S",
              "icon": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_ue005d/26892155360c9aee08d162f6a5a1f0c7.png",
              "profession": 3
            }
          },
          {
            "item_type": "UP_S_ITEM_TYPE_WEAPON",
            "weapon": {
              "weapon_id": 14150,
              "weapon_name": "",
              "rarity": "S",
              "icon": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_ue005d/d93801354ca47e0ee27f89f4d790d19d.png",
              "profession": 3
            }
          }
        ],
        "sup_lock_show": false,
        "more_s_need_cnt": 76
      },
      "... (4 total)"
    ],
    "record_show_gachas": [
      "GACHA_TYPE_CHARACTER_UP",
      "GACHA_TYPE_WEAPON_UP",
      "... (6 total)"
    ]
  }
}
```

</details>

<h3 id="zzz-gacha-calendar">获取调频日历</h3>

**国服：**

_请求方式：GET_

> _需要验证Cookie_
>
> LToken

`https://api-takumi-record.mihoyo.com/event/game_record_zzz/api/zzz/gacha_calendar`

**参数：**

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| uid | num | 绝区零 UID | |
| region | str | 服务器名称 | |

**JSON返回：**

`data`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| avatar_gacha_schedule_list | arr | 代理人卡池日程 | |
| weapon_gacha_schedule_list | arr | 音擎卡池日程 | |

日程对象字段：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| gacha_type | str | 卡池类型 | |
| gacha_state | str | 状态 | 如 `GACHA_STATE_IN_PROGRESS` |
| start_ts | num | 开始时间戳 | |
| end_ts | num | 结束时间戳 | |
| sup_lock_show | bool | 锁定展示 | |
| left_start_ts | num | 距开始剩余秒 | |
| left_end_ts | num | 距结束剩余秒 | |
| version | str | 版本号 | 如 `3.1` |
| avatar_list / weapon_list | arr | UP 列表 | |
| insurance_id | num | 待调查 | |
| idx | num | 序号 | 代理人日程可见 |

---

<details>
<summary>查看示例（节选）</summary>

```json
{
  "retcode": 0,
  "message": "OK",
  "data": {
    "avatar_gacha_schedule_list": [
      {
        "gacha_type": "GACHA_TYPE_CHARACTER_UP",
        "gacha_state": "GACHA_STATE_IN_PROGRESS",
        "start_ts": 1785290400,
        "end_ts": 1788850799,
        "sup_lock_show": false,
        "left_start_ts": 0,
        "left_end_ts": 2480266,
        "version": "3.1",
        "avatar_list": [
          {
            "avatar_id": 1581,
            "avatar_name": "蕾米埃尔",
            "rarity": "S",
            "icon": "https://act-webstatic.mihoyo.com/game_record/zzzv2/role_square_avatar/role_square_avatar_1581.png",
            "avatar_profession": 3,
            "avatar_element_type": 300,
            "avatar_sub_element_type": 0,
            "wiki_url": "https://baike.mihoyo.com/zzz/wiki/content/2076/detail?bbs_presentation_style=fullscreen",
            "jump_cultivate": true,
            "is_forward": false,
            "show_upon": true,
            "full_name": "蕾米埃尔·丹"
          },
          "... (3 total)"
        ],
        "insurance_id": 0,
        "idx": 2
      },
      "... (4 total)"
    ],
    "weapon_gacha_schedule_list": [
      {
        "gacha_type": "GACHA_TYPE_WEAPON_UP",
        "gacha_state": "GACHA_STATE_IN_PROGRESS",
        "start_ts": 1785290400,
        "end_ts": 1788850799,
        "sup_lock_show": false,
        "left_start_ts": 0,
        "left_end_ts": 2480266,
        "version": "3.1",
        "weapon_list": [
          {
            "weapon_id": 14158,
            "rarity": "S",
            "icon": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_ue005d/26892155360c9aee08d162f6a5a1f0c7.png",
            "talent_title": "失乐园",
            "talent_content": "异常精通提升<color=#2BAD00>96</color>点；装备者触发<color=#FFA9DD>[异化]</color>反应时，自身获得属性异常伤害提升<color=#2BAD00>20%</color>的效果，并为全队角色施加造成的伤害提升<color=#2BAD00>30%</color>效果，效果均持续30秒，重复触发时刷新持续时间。",
            "wiki_url": "https://baike.mihoyo.com/zzz/wiki/content/2109/detail?bbs_presentation_style=fullscreen",
            "show_upon": true,
            "profession": 3
          },
          "... (3 total)"
        ],
        "insurance_id": 0
      },
      "... (4 total)"
    ]
  }
}
```

</details>

<h3 id="zzz-activity-calendar">获取活动日历</h3>

**国服：**

_请求方式：GET_

> _需要验证Cookie_
>
> LToken

`https://api-takumi-record.mihoyo.com/event/game_record_zzz/api/zzz/activity_calendar`

**参数：**

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| uid | num | 绝区零 UID | |
| region | str | 服务器名称 | |

**JSON返回：**

`data`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| activity_list | arr | 活动列表 | |

`data`对象→`activity_list`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| activity_id | num | 活动 ID | |
| state | str | 状态 | 如 `STATE_IN_PROGRESS` |
| name | str | 活动名称 | |
| monochrome_cnt | num | 可获得菲林（单色胶片）总量 | 名称按活动奖励口径理解 |
| monochrome_got_cnt | num | 已获得数量 | |
| start_ts | num | 开始时间戳 | |
| end_ts | num | 结束时间戳 | |
| left_start_ts | num | 距开始剩余秒 | |
| left_end_ts | num | 距结束剩余秒 | |

<details>
<summary>查看示例</summary>

```json
{
  "retcode": 0,
  "message": "OK",
  "data": {
    "activity_list": [
      {
        "activity_id": 5000158,
        "state": "STATE_IN_PROGRESS",
        "name": "咔嚓！焦点对决！",
        "monochrome_cnt": 360,
        "monochrome_got_cnt": 60,
        "start_ts": 1786068000,
        "end_ts": 1787515199,
        "left_start_ts": 0,
        "left_end_ts": 1144666
      }
    ]
  }
}
```

</details>

---

<h3 id="zzz-holo-boss">获取拟境湮灭详情</h3>

接口路径为 `holo_boss_detail`。页面/勋章文案为 **拟境湮灭**（如「拟境湮灭·游刃」「湮灭·闪耀之誓」），与首页 `holo_boss_brief` 对应。

**国服：**

_请求方式：GET_

> _需要验证Cookie_
>
> LToken

`https://api-takumi-record.mihoyo.com/event/game_record_zzz/api/zzz/holo_boss_detail`

**参数：**

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| uid | num | 绝区零 UID | |
| region | str | 服务器名称 | |
| schedule_type | num | 期次 | `1` 当期等 |

**JSON返回：**

`data`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| start_time | obj | 开始时间 | 时间对象 |
| end_time | obj | 结束时间 | 时间对象 |
| list | arr | 各 BOSS 挑战记录 | |
| unlock | bool | 是否解锁 | |
| refresh_time | num | 刷新剩余秒数 | |

`data`对象→`list`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| rank | num | 排名 | |
| star | num | 星级 / 评级星 | |
| challenge_time | obj | 通关用时 | 时间对象；部分字段可为 0 |
| boss | obj | BOSS 信息 | |
| avatar_list | arr | 出战代理人 | |

`data`对象→`list`数组→对象→`boss`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| icon | str | 图标 | |
| name | str | BOSS 名称 | |
| medal | obj | 对应勋章 | `medal_icon` / `medal_id` / `is_no_injured`（无伤） |

---

<details>
<summary>查看示例（节选）</summary>

```json
{
  "retcode": 0,
  "message": "OK",
  "data": {
    "start_time": {
      "year": 2026,
      "month": 6,
      "day": 17,
      "hour": 6,
      "minute": 0,
      "second": 0
    },
    "end_time": {
      "year": 2026,
      "month": 10,
      "day": 21,
      "hour": 5,
      "minute": 59,
      "second": 59
    },
    "list": [
      {
        "rank": 6846,
        "star": 4,
        "challenge_time": {
          "year": 0,
          "month": 0,
          "day": 0,
          "hour": 0,
          "minute": 2,
          "second": 52
        },
        "boss": {
          "icon": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_ue005d/1db6475c70ef9bed960bd27f473ef98c.png",
          "name": "异构·太初梦魇·「始主」",
          "medal": {
            "medal_icon": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_ue005d/928f6519574070cb650a9483689622d9.png",
            "medal_id": 11001,
            "is_no_injured": false
          }
        },
        "avatar_list": [
          {
            "id": 1321,
            "level": 0,
            "element_type": 201,
            "avatar_profession": 1,
            "rarity": "S",
            "rank": 0,
            "role_square_url": "https://act-webstatic.mihoyo.com/game_record/zzzv2/role_square_avatar/role_square_avatar_1321.png",
            "sub_element_type": 0
          },
          "... (3 total)"
        ]
      },
      "... (3 total)"
    ],
    "unlock": true,
    "refresh_time": 6161039
  }
}
```

</details>

<h3 id="zzz-abyss-abstract">获取零号空洞摘要</h3>

对应战绩页「零号空洞」：执照等级、悬赏委托、探索任务、收集条目与最高难度记录等。

**国服：**

_请求方式：GET_

> _需要验证Cookie_
>
> LToken

`https://api-takumi-record.mihoyo.com/event/game_record_zzz/api/zzz/abysss2_abstract`

> 路径字面量为 `abysss2_abstract`（`abyss` 后为三个 `s`）。

**参数：**

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| uid | num | 绝区零 UID | |
| region | str | 服务器名称 | |

**JSON返回：**

`data`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| abyss_level | obj | **执照等级** | `cur_level` / `max_level` / `icon`；如 `260/260` |
| abyss_task | obj | **探索任务** | `cur_task` / `max_task`；如 `130/241` |
| abyss_duty | obj | **悬赏委托进度** | `cur_duty` / `max_duty`；如 `0/8000` |
| refresh_time | num | **周期剩余时间**（秒） | 展示为「周期剩余时间：X 天 X 时」 |
| abyss_max | obj | **已通关最高难度**相关 | 见下表 |
| abyss_collect | arr | 收集类图鉴进度 | `type` 与页面条目对照见下表 |
| unlock | bool | 是否解锁 | |
| abyss_task_force_investigation_max | obj | **特遣调查**最高记录 | 如「特遣调查 以太活性 N」 |
| special_mission | obj | **峰战**特殊任务最高记录 | 如「难度 N · 以太活性 M」 |
| hide_abyss_duty | bool | 是否隐藏悬赏委托 | |

`abyss_max` 字段与页面文案：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| max_name | str | **已通关最高难度**名称 | 如「战线肃清·难度六」 |
| heat_count | num | 相关热度 / 以太活性展示用 | 语义与下列特遣/峰战的 `heat_count` 类似，待统一 |
| max_count | num | **通关最高难度次数** | |
| best_time | num | **通关最高难度最短耗时**（秒） | 页格式化为 `HH:MM:SS` |
| has_data | bool | 是否有数据 | |

`abyss_task_force_investigation_max`（特遣调查）字段：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| max_name | str | 名称 | 固定类文案「特遣调查」 |
| heat_count | num | **以太活性**数值 | 如「特遣调查 以太活性 10」 |
| max_count | num | 通关 / 达成次数 | 如 `4` |
| best_time | num | 最短耗时（秒） | 例 `496` → `00:08:16` |
| has_data | bool | 是否有有效记录 | |

`special_mission`（峰战）字段：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| has_data | bool | 是否有有效记录 | |
| heat_count | num | **以太活性**数值 | 如「难度 1 · 以太活性 12」中的 `12` |
| high_difficulty | num | **难度**编号 | 如「难度 1」中的 `1` |
| max_count | num | 通关 / 达成次数 | |
| best_time | num | 最短耗时（秒） | 例 `592` → `00:09:52` |

`abyss_collect` 数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| type | num | 收集条目类型 | 与页面名称对照见下表 |
| cur_collect | num | 当前进度 | |
| max_collect | num | 目标进度 | |

> `abyss_collect.type` 与零号空洞「收集」列表对照：
>
> | type | 页面名称 | 示例进度 |
> | ---- | -------- | -------- |
> | 1 | 收集数据 | `6/12` |
> | 2 | 探究勋证 | `39/58` |
> | 3 | 战术棱镜方案 | `100/159` |
> | 4 | 武备图鉴 | `35/45` |
> | 5 | 协战武备图鉴 | `95/255` |
> | 6 | 鸣徽卡牌图鉴 | `2/5` |
> | 7 | 非正式指南 | `10/10` |
>
> 注：名称以客户端展示为准。

<details>
<summary>查看示例</summary>

```json
{
  "retcode": 0,
  "message": "OK",
  "data": {
    "abyss_level": {
      "cur_level": 260,
      "max_level": 260,
      "icon": "https://..."
    },
    "abyss_task": { "cur_task": 130, "max_task": 241 },
    "abyss_duty": { "cur_duty": 0, "max_duty": 8000 },
    "refresh_time": 537834,
    "abyss_max": {
      "max_name": "战线肃清·难度六",
      "heat_count": 9,
      "max_count": 2,
      "best_time": 462,
      "has_data": true
    },
    "abyss_collect": [
      { "type": 1, "cur_collect": 6, "max_collect": 12 },
      { "type": 2, "cur_collect": 39, "max_collect": 58 },
      { "type": 3, "cur_collect": 100, "max_collect": 159 },
      { "type": 4, "cur_collect": 35, "max_collect": 45 },
      { "type": 5, "cur_collect": 95, "max_collect": 255 },
      { "type": 6, "cur_collect": 2, "max_collect": 5 },
      { "type": 7, "cur_collect": 10, "max_collect": 10 }
    ],
    "unlock": true,
    "abyss_task_force_investigation_max": {
      "max_name": "特遣调查",
      "heat_count": 10,
      "max_count": 4,
      "best_time": 496,
      "has_data": false
    },
    "special_mission": {
      "has_data": false,
      "heat_count": 12,
      "high_difficulty": 1,
      "max_count": 1,
      "best_time": 592
    },
    "hide_abyss_duty": false
  }
}
```

</details>

---

<h3 id="zzz-cultivate">养成指南相关接口</h3>

| 路径 | 说明 |
| ---- | ---- |
| `GET /event/nap_cultivate_tool/icon_info` | 图标字典 |
| `GET /event/nap_cultivate_tool/avatar_basic_list` | 代理人基础列表 |

<h4 id="zzz-cultivate-icon">获取图标信息</h4>

**国服：**

_请求方式：GET_

> _需要验证Cookie_
>
> LToken / CookieToken 等账号 Cookie

`https://act-api-takumi.mihoyo.com/event/nap_cultivate_tool/icon_info`

**参数：**

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| uid | num | 绝区零 UID | |
| region | str | 服务器名称 | 如 `prod_gf_cn` |

**请求头（节选）：**

| 请求头 | 说明 |
| ---- | ---- |
| `Origin` | `https://act.mihoyo.com` |
| `Referer` | `https://act.mihoyo.com/` |
| `x-rpc-app_version` | 如 `2.112.0` |
| `x-rpc-cultivate_source` | `bbs` |
| `x-rpc-device_id` | 设备 ID |
| `x-rpc-device_fp` | 设备指纹 |
| `x-rpc-lang` | 如 `zh-cn` |
| `x-rpc-is_teaser` | 如 `1` |

**JSON返回：**

根对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| retcode | num | 返回码 | |
| message | str | 返回消息 | |
| data | obj | 图标数据 | |

`data`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| avatar_icon | obj | 代理人图标字典 | key 为代理人 ID 字符串 |
| buddy_icon | obj | 邦布图标字典 | key 为邦布 ID 字符串 |
| special_skill_icon | obj | 特殊技能图标字典 | key 为 ID 字符串 |

`data`对象→`avatar_icon`对象→（按 ID）对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| square_avatar | str | 方形头像 URL | |
| rectangle_avatar | str | 矩形头像 URL | |
| vertical_painting | str | 立绘 URL | |
| vertical_painting_color | str | 立绘主色 | 如 `#b92734` |
| avatar_us_full_name | str | 英文全名 | |
| teaser_avatar | str | 预告头像 URL | 可为空字符串 |

<h4 id="zzz-cultivate-avatar-list">获取代理人基础列表</h4>

**国服：**

_请求方式：GET_

> _需要验证Cookie_
>
> LToken / CookieToken 等账号 Cookie

`https://act-api-takumi.mihoyo.com/event/nap_cultivate_tool/avatar_basic_list`

**参数：**

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| uid | num | 绝区零 UID | |
| region | str | 服务器名称 | |

请求头与 `icon_info` 一致（含 `x-rpc-cultivate_source: bbs` 等）。

**JSON返回：**

`data`对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| list | arr | 代理人条目 | |

`data`对象→`list`数组→对象：

| 字段 | 类型 | 内容 | 备注 |
| ---- | ---- | ---- | ---- |
| avatar | obj | 代理人基础信息 | 字段类似战绩 `avatar_list` 单项 |
| unlocked | bool | 是否已解锁 | |
| is_up | bool | 是否 UP | |
| is_teaser | bool | 是否预告 | |
| is_top | bool | 是否置顶 | |

---

**备注：**

| 能力 | 国服主机 / 路径前缀 | 国际服主机 / 路径前缀 |
| ---- | ---- | ---- |
| 战绩 | `api-takumi-record.mihoyo.com/event/game_record_zzz/api/zzz/` | `sg-public-api.hoyolab.com/event/game_record_zzz/api/zzz/` |
| 绳网月报 | `api-takumi.mihoyo.com/event/nap_ledger/` | `sg-public-api.hoyolab.com/event/nap_ledger/` |
| 养成工具 | `act-api-takumi.mihoyo.com/event/nap_cultivate_tool/` | 未知 |
| 绑定角色 | `api-takumi.mihoyo.com/binding/api/getUserGameRolesByCookie` | `api-account-os.hoyolab.com/binding/api/getUserGameRolesByCookieToken` |

**`icon_info` 示例：**

<details>
<summary>查看示例（icon_info 节选）</summary>

```json
{
  "retcode": 0,
  "message": "OK",
  "data": {
    "avatar_icon": {
      "1411": {
        "square_avatar": "https://act-webstatic.mihoyo.com/game_record/zzzv2/role_square_avatar/role_square_avatar_1411.png",
        "rectangle_avatar": "https://act-webstatic.mihoyo.com/game_record/zzzv2/role_square_avatar/role_square_avatar_1411.png",
        "vertical_painting": "https://act-webstatic.mihoyo.com/game_record/zzzv2/role_vertical_painting/role_vertical_painting_1411.png",
        "vertical_painting_color": "#b92734",
        "avatar_us_full_name": "Ukinami Yuzuha",
        "teaser_avatar": ""
      },
      "1541": {
        "square_avatar": "https://act-webstatic.mihoyo.com/game_record/zzzv2/role_square_avatar/role_square_avatar_1541.png",
        "rectangle_avatar": "https://act-webstatic.mihoyo.com/game_record/zzzv2/role_square_avatar/role_square_avatar_1541.png",
        "vertical_painting": "https://act-webstatic.mihoyo.com/game_record/zzzv2/role_vertical_painting/role_vertical_painting_1541.png",
        "vertical_painting_color": "#6848f7",
        "avatar_us_full_name": "Promeia",
        "teaser_avatar": ""
      }
    },
    "buddy_icon": {
      "54004": {
        "square_avatar": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_u0f27d/1601781a2808352201728e4b965abc4b.png",
        "rectangle_avatar": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_u0f27d/1601781a2808352201728e4b965abc4b.png"
      }
    },
    "special_skill_icon": {
      "1051": {
        "special_skills": [
          {
            "skill_type": 1,
            "icon": "https://fastcdn.mihoyo.com/static-resource-v2/2025/12/16/4c0f24030dcbf14ba91505c60ced058a_8226905411985297866.png"
          }
        ]
      }
    }
  }
}
```

</details>

**`avatar_basic_list` 示例：**

<details>
<summary>查看示例（avatar_basic_list 节选）</summary>

```json
{
  "retcode": 0,
  "message": "OK",
  "data": {
    "list": [
      {
        "avatar": {
          "id": 1591,
          "level": 0,
          "name_mi18n": "希格莉德",
          "full_name_mi18n": "希格莉德·德拉叙尔",
          "element_type": 202,
          "camp_name_mi18n": "罗斯凯利法·空域巡戍局",
          "avatar_profession": 1,
          "rarity": "S",
          "group_icon_path": "https://act-webstatic.mihoyo.com/darkmatter/nap/live_webtool01_cn/item_icon_u0a0ae/59195faf1420775212a80ac27221e2df.png",
          "hollow_icon_path": "https://act-webstatic.mihoyo.com/darkmatter/nap/live_webtool01_cn/item_icon_u0a0ae/377f5ad3f1eb2d7dd4968c0d1b634be7.png",
          "rank": 0,
          "sub_element_type": 0,
          "awaken_state": "AwakenStateNotVisible"
        },
        "unlocked": false,
        "is_up": false,
        "is_teaser": true,
        "is_top": false
      },
      {
        "avatar": {
          "id": 1501,
          "level": 60,
          "name_mi18n": "爱芮",
          "full_name_mi18n": "爱芮",
          "element_type": 205,
          "camp_name_mi18n": "妄想天使",
          "avatar_profession": 3,
          "rarity": "S",
          "group_icon_path": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_u0f27d/fbe48ad2d135c7ba46e9a100f1e51e6d.png",
          "hollow_icon_path": "https://act-webstatic.mihoyo.com/darkmatter/nap/prod_gf_cn/item_icon_u0f27d/ca9120a6d3fe1b4284b54ad291fa0755.png",
          "rank": 0,
          "sub_element_type": 0,
          "awaken_state": "AwakenStateNotVisible"
        },
        "unlocked": true,
        "is_up": true,
        "is_teaser": false,
        "is_top": false
      },
      "... (58 total)"
    ]
  }
}
```

</details>
