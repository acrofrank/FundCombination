# FundCombination
基金组合研究: 利用python，抓取天天基金网、晨星网数据，分析组合持仓、行业分布、基金参数特征，辅助基金组合投资策略制定


1 组合分析工具用途
组合分析，晨星网也有组合透视工具，对应该项功能。但是晨星网的组合透视功能存在3项不足，其一、只能分析前十重仓，实际应用中，前十不够，依靠前十重仓进行判断容易入坑(亲身体验)；其二、行业分析太多粗略，无法为投资策略提供参考；其三、当组合内含有QDII或者港股时，晨星网的组合透视计算可能有误。当时发现该点时，我根据晨星网提供的数据，自己用计算器算了几遍，发现晨星网计算的组合持仓确实有误。怀疑晨星网无法有效及时获取QDII、港股的持仓信息。
基于此，本工具主要有三个特点：
第一：重仓股分析
根据天天基金网、晨星网公布的基金前十重仓，结合组合内基金的比例，算出所有前十股票在组合内的持仓比例；
第二：一二级行业分级
行业分布，细化到一二级行业，分类更细，方便投资分析
第三、针对单个基金，提供工具抓取晨星网上的标准差、风险系统、夏普比、阿尔法、贝塔、R平方、回撤、规模、股票集中度等参数。


2 软件输入
在./input文件夹下，其中group_fund.json里面填入基金组合的比例，stock_info.json里面填入股票的一二级行业(暂时手动添加)，chenxingcode.json填入基金在晨星网的特殊编码(例如https://cn.morningstar.com/quicktake/F0000004AI中的F0000004AI)


3 软件输出
在./output里面，有两类，一类是Fund_info.csv，存储单独基金的信息；一类是group_position.csv，存储组合透视分析结果。

4 软件大概逻辑
acquire_group_fund.py用于获取组合分析结果；export_fund_info.py用于获取基金具体参数；FundParameterInfo.py基金类，里面有具体的抓取信息实现，从天天网上抓取时，首先获取网页保存为本地html文件，再进行解析，从晨星网上抓取时，利用selinum+webdriver进行信息抓取。
