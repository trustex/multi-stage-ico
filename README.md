# MultiStageToken
### Writen by Jacky Gu 古千峰

`MultiStageToken`（`代币分期众筹合约`，简称`MST`）智能合约参照传统风投行业的对赌模式，将目前流行的代币众筹（ICO）分割成多期进行，每期众筹结束后，将投资人投的以太坊以及获取的代币锁定，锁定期过后，经投票决定是否继续下一轮。如果投资人对项目方的工作满意，则解冻以太坊以及代币；如果投资人投票结果决定终止众筹，则将以太坊返还给投资人，代币返还给项目方。

该合约基于ERC20标准开发，由项目方配置并部署到以太坊主网。分期期数，以及各期的参数均由项目方设定，一旦部署，不可更改。

#### 设定的参数分为两类，一类是全局参数，与传统的ERC20合约相同，包括：

* 代币名称
* 代码代号
* 总发行量
* 精度

#### 另一类是每期众筹的参数，包括：

* 每期募集ETH总额，即每期硬顶；
* 每期1ETH兑换的代币，即兑换价格；
* 每次投的最小与最大ETH金额；
* 每期众筹的时间段：包括开始众筹与结束时间；
* 每期众筹后冻结的时间段：包括开始冻结与结束时间；
* 每期冻结后投票时间段：包括开始投票和结束投票时间；
* 投票方式：可选择是按人头计票还是按所投的以太坊计票；
* 投票比率：如果当期投票人数超过投票率，则投票有效，否则视为不通过；
* 赞成票比率：如果当期投的赞成票比例超过此指标，则通过；
* 退款费用率：即如果投票没有通过，众筹停止，在返还投资人的以太坊中扣除多少比例，作为项目方的开支。

#### 投资人有以下行为：
* 打以太坊到合约参与众筹；
* 冻结期结束后投票，决定是否将以太坊解冻，并释放给项目方；
* 如果投票通过，则自行提取代币到钱包；
* 如果投票失败，则自行提取以太坊到钱包；

#### 项目方有以下行为：
* 一次性配置并部署合约；
* 如果阶段性投票通过，则提取以太坊；

#### 以上参数都由项目方设定，通过数值可准确考察该项目方的实力与诚信，投资人以此作为参考，比如：

* 有实力的项目方会将赞成票比率设得很高，比如80%，也就意味着必须要有80%的人支持，才能解冻ETH。
* 有实力的项目方会将冻结期设得较长，比如设定到承诺的二级市场上市后解冻，在此期间，项目方通过自身的研发与资金实力推动项目前行，这样一旦解冻，投资人出于对项目过去业绩的认可，会更看好项目的未来，从而降低二级市场抛压。
* 项目方可以采取限定投资额的方式，仅让私募等专业投资人参与，而不是小散参与，从而规避政策风险。
* 项目方可以通过设定不同的兑换价格，让先期投入者享有更低的折扣。而且因为这种折扣非常透明，且无法更改，避免了过去代投行业的乱象。
* 有实力的项目方可以将退款费用率设的很低。比如，为0的话，如果投票失败，投资人的以太坊将100%全部退还。如果为50%，则投资人即使投了反对票，也只能返回50%的投资款。
* 普通项目不会也不敢采取该方案，有实力项目，以及募集额度巨大的项目，会采取该方案。

#### 该合约完全开源，并不断完善，欢迎对此众筹模式有兴趣者参与探讨，更欢迎有实力的的项目方使用该模式

[获取源码 Contract Code](https://github.com/eoshackathon/multi-stage-ico/blob/mst-0.1.1/solidity/MultiStageToken.sol)
