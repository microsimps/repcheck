# repcheck

**检查评测集是否覆盖了真实流量的分布。**

`repcheck` —— 比较评测集与线上流量在长度、类别、难度上的分布差异，量化覆盖缺口

- 零依赖，Python 3.10+ 标准库即可运行
- 单文件，`repcheck.py` 拷走就能用
- 不联网、不写文件

<!-- ipos:install -->
## 安装

零依赖，Python 3.10+ 即可：

```bash
pip install microsimps-repcheck
```

装完直接用命令名调用：

```bash
repcheck --help
```

也可以不用安装，直接把 `repcheck.py` 拷走用——它只依赖标准库。

## 为什么需要它

把「分布差异」量化成单一覆盖率指标，而不是人工比对

它遵守下面几条自己定的规矩：

1. **只报告能定位到具体位置的结论**，不做语义猜测。
2. **规则表公开**，每条命中都能对应到 评测样本代表性 领域的一条明示规则。
3. **输入为空或格式不对时明确报错**，不静默返回空结果。

## 用法

```bash
python repcheck.py --file input.txt
python repcheck.py --text "示例内容"
python repcheck.py --file input.txt --json
```

加 `--json` 可以拿到机器可读的结果，便于接到流水线里。

## 已知局限

- 分箱是等宽或等频，样本太少时结论不稳。
- 不做显著性检验。

## 跑测试

```bash
python test_repcheck.py
```

测试用独立的断言与临时数据，不污染工作目录。

## 来源与参考

- Python 标准库文档：<https://docs.python.org/3/>
- GitHub 仓库：<https://github.com/microsimps/repcheck>

---

## 关于作者

microsimps 做评测样本代表性相关的问题。这个工具先替你回答一个具体问题，再谈别的。

- 个人主页：<https://microsimps.github.io>
- 仓库：<https://github.com/microsimps/repcheck>

## 许可

MIT，见 [LICENSE](LICENSE)。
