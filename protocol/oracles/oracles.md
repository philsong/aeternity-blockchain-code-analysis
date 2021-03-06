# ORACLES  预言机

## 概述和定义

 -  **oracle **是区块链上的一个实体(entity)，位于完整节点(full node)的**oracle状态树**中。
 -  oracle由**oracle 操作者（operate）** 操作。
 -  oracle运算符通过在链上发布**oracle 注册事务（register transaction）**来创建oracle。
 -  oracle注册事务将一个帐户注册为oracle。 （一个帐户 - 一个oracle）
 - 任何用户都可以通过在链上发布**oracle查询事务（query transaction）**来查询oracle。
 -  oracle查询事务在oracle状态树中创建一个**oracle查询对象**。
 -  oracle 操作者(operator)扫描区块链上的交易
    oracle通过任何方式查询事务。可能在操作者（operator）自己的节点上。
 -  oracle operator通过在链上发布**oracle响应事务(oracle response transaction)**来响应oracle查询。
 -  oracle响应事务通过添加响应来修改oracle查询对象。
 - 添加响应后，oracle查询对象将关闭，然后变为不可变的。

## Oracle生命周期示例

## Oracle state trees

## Oracle transactions

## Oracle操作的技术方面

### Oracles有一个已发布的API

 -  API定义查询应具有的格式。 （query_format）
 -  API定义应答将具有的格式。 （response_format）
 -  API定义应在其下解释格式的VM版本。
   - 如果VM版本为0（？AEVM_NO_VM）：
     - 查询和响应格式是未解释的字符串（字节数组）。
     - 从sophia合同调用时，查询和响应被视为字符串。
   - 对于sophia对应的VM版本：
     - 查询和响应格式必须是类型表示，根据ABI编码。
     - 查询和响应被解释为格式规范中的类型

### Oracle响应有一个类型声明
 - 类型应与智能合约语言中的类型相对应。
 - 应该有动机在oracle答案中使用简单类型（布尔值，整数）。
   - 例如，通过智能合约中的访问成本。

### oracle应答是否应该限制使用？
 - 例如，只有查询的创建者能够在智能合约中使用答案吗？
 - 框架是否应该支持加密/解密答案？

### oracle查询/响应有一个TTL
 - 实际响应将保留在链上。
 - 在一定数量的块之后，将从状态树中修剪响应。
 - 发布答案的成本应反映TTL。
