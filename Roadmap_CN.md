# 中文版Roadmap(Phase 1)

## Phase 1 目标：开发出基于Cairo V2的ZK BTC Light Client

### 1.用Cairo2(2.5.3~)开发可接受参数的读取用程序

- 由于Cairo1之后的版本，和Cairo0不同并无真正的hint（已和class lambda确认过），因此无法使用rust或者python调用Cairo代码的方式实现，需要采用将数据嵌入在代码中的方式来实现。参考用Cairo0实现的全节点：[ZeroSync](https://github.com/ZeroSync/ZeroSync)。
- 此阶段需要一个codegen用以进行代码生成。参考[Cairo-hints](https://github.com/reilabs/cairo-hints)。但无需使用此项目，因为每次重新从头生成Cairo代码会拖累效率，并且我们不需要它的通信架构。

### 2.基于上述程序进行试验性BTC区块的数据读取

- 开发出一个可以读取BTC区块的Cairo程序。
- 一些数据结构可能需要自行实现。参考[Cairo的数据结构库](https://github.com/keep-starknet-strange/alexandria)。
- 此阶段准备一些实验用数据即可，无需实时性。

### 3.实用性BTC区块数据读取

- 由于是轻节点，基于SPV机制实现即可。
- 用Rust（或其他语言）连接Node，并将区块数据传送给Cairo程序处理


### 4.Prover 和 Verifier
- Prover: https://github.com/lambdaclass/lambdaworks/tree/main/provers/cairo
- Verifier可能没必要