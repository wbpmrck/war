##what is this

this is a part-time project,it can be a funny game.

####DOING
* 开发
    * battle.go
        * 定义粗略的战斗流程
            * 战斗过程就是时间流逝的过程
            * 每个时间tick到之后，要执行：
                * 回复单位的行动力
                * 回复单位状态，重新计算状态
                * 根据最新状态判断行动顺序
                * 按照顺序先后，执行角色行动逻辑
        * 定义战斗判定阶段，考虑与技能、单位动作的衔接问题
    * character.go / warrior.go
        * 实现更多的战斗过程代码
        * 编写模拟战斗测试代码
    * skill.go
        * 技能包、技能项的设计
        * 技能项的实现
        * targetChooser的实现、丰富


####TODO
* 设计
    > 完成首批需求收集，确定0.1版本目标
* 装备系统
    > 装备的效果、和技能效果，如何区分和设计
* 效果和技能系统完善
    * 效果的排斥
        * 目前效果直接并没有直接关系，效果可以叠加。
        * 如果实现同一效果的叠加次数控制，以及不同效果的叠加互斥判断等，需要再考虑一下
* 沙箱和脚本

    > 建立基本的沙箱机制
    
    > 使用javascript来描述业务逻辑

####DONE
* 开发
    * skillBase.go
        * 定义技能基类的结构，里面应该分别包含技能项、技能类定义
        * 实现skill的接口
            * 注意技能接口的实现应该也是依赖effect接口的实现
    * effect.go
        * 添加效果字典集合
        * 在builtIn里添加几个内置的效果
    * eventEmitter.go
        * 支持通用的事件订阅、发布模型 (OK)
        * 在订阅事件的时候，对EventHandler进行构造和调用  (OK)
        * 让character内嵌Eventbase来提供事件发射、取消后续事件执行等功能  (OK)
        * 测试一下事件机制能否正常工作 (OK)
    * 规则的默认实现，以及实体的组合
        * 各种规则，如果有默认通用实现的，实现通用的版本
            * effectCarrier (OK)
            * attributeCarrier  (OK)
        * character对这些默认实现进行组合，从而实现自己的功能 (OK)
            * 定义一个角色 (OK)
            * 添加属性、效果 (OK)
            * 测试用例验证效果是否生效 (OK)