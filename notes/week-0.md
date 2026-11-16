# 第 0 周｜环境准备

记录日期：2026-11-16。

## 已完成与验证记录

- [x] Foundry 已安装在 WSL Ubuntu；`forge --version` 和 `cast --version` 均输出 1.9.0。
- [x] 官方模板已克隆到本地，执行 `forge test -vv`，8 个测试通过，0 个失败。
- [x] 已领取 Sepolia ETH。水龙头页面显示领取 0.05 ETH，钱包到账已由本人确认。
- [x] Lasna 测试币已到账。钱包截图显示网络为 Reactive Lasna，余额为 1.05 lREACT。
- [x] 已使用 Codex 辅助学习。
- [x] 已建立本公开学习仓库，包含 `README.md` 与 `notes/`。

余额是当时的截图记录，可能随交易变化；本文不据此推断额外 0.05 lREACT 的来源。本人已使用钱包，但是否为新建的测试专用账户仍需自行确认。

## 仍需确认或完成

- [ ] 确认课程使用的是测试专用账户，而非存有资产的主账户。
- [ ] 按课程任务表单要求补充必要的环境证明、余额截图或交易哈希并提交。
- [ ] 后续部署源链、Reactive 和回调合约，记录完整链路的合约地址与交易哈希。

截至本次记录，尚未完成合约链上部署；本地测试通过不等于链上部署成功，也不代表平台任务已经提交。

## 本地测试复现

先安装 Foundry，再执行：

```bash
git clone --recurse-submodules https://github.com/ethpanda-org/reactive-builder-camp.git
cd reactive-builder-camp/starter
forge test -vv
```

以上测试在本地使用 MockSystem 和 MockProxy，不需要测试币，也不能替代真实跨链执行验证。

## 给 AI 的 Omni 版本上下文

使用 Reactive Network Omni 新版本。优先参考以下官方资料：

- https://dev.reactive.network/reactive-contracts
- https://dev.reactive.network/callback-contracts
- https://dev.reactive.network/economy
- https://github.com/Reactive-Network/reactive-smart-contract-demos/tree/omni/src/micro-demos

不要混用旧版 ReactVM、`vm` 修饰符或 `emit Callback`。Omni 的 `react()` 使用 `onlySystem`，通过 `requestCallbackV_1_0` 请求回调。系统合约为 `0x8888888888888888888888888888888888888888`；`0x...fffFfF` 仅用于 Cron 事件源。部署前重新核对当前官方文档与目标链 Proxy 地址。
