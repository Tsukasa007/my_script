# 个人学习目的，请下载后24小时内删除下载的代码
#   fork  跑路  真的是branches dbk？
###### ql repo https:<span></span>//github.com/Tsukasa007/my_script.git "" "jdCookie|USER_AGENTS|sendNotify|backup" "" "master"


# 关于2.8 傻瓜智障版自动互助方法
##### 如果你是小白，又不知道2.8如何互助，何不尝试一下我这个不用动脑系列互助配置
# 1.根据上述拉取仓库后,青龙添加如下任务
#### task /ql/repo/Tsukasa007_my_script_master/code_tsukasa.sh	
![image](https://user-images.githubusercontent.com/28201662/128467629-6f9dd427-d4f3-4ef3-a364-a6a9511402c2.png)

# 2.配置文件--config
![img1](https://user-images.githubusercontent.com/28201662/128215529-bf9d1f70-48dd-45fa-8434-1830d6d4e68e.png)
#### 拉到文件的最下面，在最下面粘贴以下代码
```
env_name=(
  FRUITSHARECODES
  PETSHARECODES
  PLANT_BEAN_SHARECODES
  DREAM_FACTORY_SHARE_CODES
  DDFACTORY_SHARECODES
  JDZZ_SHARECODES
  JDJOY_SHARECODES
  JXNC_SHARECODES
  BOOKSHOP_SHARECODES
  JD_CASH_SHARECODES
  JDSGMH_SHARECODES
  JDCFD_SHARECODES
  JDHEALTH_SHARECODES
)
var_name=(
  ForOtherFruit
  ForOtherPet
  ForOtherBean
  ForOtherDreamFactory
  ForOtherJdFactory
  ForOtherJdzz
  ForOtherJoy
  ForOtherJxnc
  ForOtherBookShop
  ForOtherCash
  ForOtherSgmh
  ForOtherCfd
  ForOtherHealth
)

## name_js为脚本文件名，如果使用ql repo命令拉取，文件名含有作者名
## 所有有互助码的活动，把脚本名称列在 name_js 中，对应 config.sh 中互助码后缀列在 name_config 中，中文名称列在 name_chinese 中。
## name_js、name_config 和 name_chinese 中的三个名称必须一一对应。
name_js=(
  xxxxxxxx_jd_scripts_jd_fruit
  xxxxxxxx_jd_scripts_jd_pet
  xxxxxxxx_jd_scripts_jd_plantBean
  xxxxxxxx_jd_scripts_jd_dreamFactory
  xxxxxxxx_jd_scripts_jd_jdfactory
  xxxxxxxx_jd_scripts_jd_jdzz
  xxxxxxxx_jd_scripts_jd_crazy_joy
  xxxxxxxx_jd_scripts_jd_jxnc
  xxxxxxxx_jd_bookshop
  xxxxxxxx_jd_scripts_jd_cash
  xxxxxxxx_jd_scripts_jd_sgmh
  xxxxxxxx_jd_scripts_jd_cfd
  xxxxxxxx_jd_scripts_jd_health
)
name_config=(
  Fruit
  Pet
  Bean
  DreamFactory
  JdFactory
  Jdzz
  Joy
  Jxnc
  BookShop
  Cash
  Sgmh
  Cfd
  Health
)
name_chinese=(
  东东农场
  东东萌宠
  京东种豆得豆
  京喜工厂
  东东工厂
  京东赚赚
  crazyJoy任务
  京喜农场
  口袋书店
  签到领现金
  闪购盲盒
  京喜财富岛
  东东健康社区
)
```
# 3.粘贴后的xxxxx需要修改为你这些脚本js的仓库主的前缀
##### 比如种豆得豆得豆是这样的 ![img3](https://user-images.githubusercontent.com/28201662/128215559-e029028c-ea3f-449a-9556-94b91c6de730.png)
##### task JDHelloWorld_jd_scripts_jd_plantBean.js	
##### 那上面 xxxxxxxx_jd_scripts_jd_plantBean
##### 改成 JDHelloWorld_jd_scripts_jd_plantBean

#####请举一反三



# 4.配置文件--task_before.sh 修改为如下 直接覆盖！

```
#!/usr/bin/env bash

##helpStart
##helpEnd


combine_sub() {
    local what_combine=$1
    local combined_all=""
    local tmp1 tmp2
    local envs=$(eval echo "\$JD_COOKIE")
    local array=($(echo $envs | sed 's/&/ /g'))
    local user_sum=${#array[*]}
    for ((i = 1; i <= $user_sum; i++)); do
        local tmp1=$what_combine$i
        local tmp2=${!tmp1}
        combined_all="$combined_all&$tmp2"
    done
    echo $combined_all | perl -pe "{s|^&||; s|^@+||; s|&@|&|g; s|@+&|&|g; s|@+|@|g; s|@+$||}"
}

## 正常依次运行时，组合所有账号的Cookie与互助码
combine_all() {
    for ((i = 0; i < ${#env_name[*]}; i++)); do
        result=$(combine_sub ${var_name[i]})
        if [[ $result ]]; then
            export ${env_name[i]}="$result"
        fi
    done
}

combine_all
```

# 5.手动运行1.的定时任务 不动脑互助配置完成


# 如果有问题加入QQ群交流群554072417
