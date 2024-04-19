---

# Celestia(tia) 公链铭文 Mint 脚本使用指南

本文档详细介绍了如何使用 Celestia(tia) 公链上的铭文 Mint 脚本。请严格按照以下步骤操作。

### 步骤 1: 安装依赖

首先，克隆仓库并安装必要的依赖：
```bash
git clone https://github.com/poyntersuresh/tiav1-mint
yarn install
cp .env.example .env
```

### 步骤 2: 配置环境变量

请在 `.env` 文件中设置环境变量。必须正确配置以下参数：

- `NODE_URL`：RPC 节点 URL，可从 [Atomscan Celestia Directory](https://atomscan.com/directory/celestia) 选择。
- `PRIVATE_KEY`：主钱包（资金钱包）私钥，用于向 Mint 钱包转账。
- `NUM_OF_WALLETS`：需要生成的 Mint 钱包数量。
- `WALLET_JSON_FILE`：生成的所有 Mint 钱包的存储文件。
- `TOKEN_TRANSFER_AMOUNT`、`GAS_PRICE`、`GAS_LIMIT`：转账和 gas 相关配置。
- `MINT_AMOUNT`、`TICK`、`PROTOCOL`、`MINT_TIMES`：Mint 操作的相关配置。

### 步骤 3: 批量生成 Mint 钱包

运行以下命令生成 Mint 钱包：
```bash
node wallet_gen.js
```

### 步骤 4: 批量转账到 Mint 钱包

从主钱包向所有 Mint 钱包批量转账：
```bash
node transfer.js
```

### 步骤 5: 执行 Mint 操作

开始 Mint 过程：
```bash
node mint.js
```

### 特别说明

如果无法从 Keplr 钱包导出私钥，请按照以下方法操作：

1. 配置 `.env` 文件，将 `PRIVATE_KEY` 留空。
2. 使用 `node wallet_gen.js` 生成钱包。
3. 在 `wallets.json` 中选择任意一个钱包作为主钱包。
4. 通过 Keplr 钱包向选定的钱包地址转账 TIA。
5. 将该钱包地址的私钥填写到 `.env` 文件的 `PRIVATE_KEY` 字段。
6. 执行 `node transfer.js` 批量转账。
7. 执行 `node mint.js` 开始批量 Mint 操作。

请确保所有步骤按照指南执行，以保证 Mint 过程的顺利进行。
