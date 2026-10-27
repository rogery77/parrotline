# parrotline

**比对提示词原文与它的复述版本，标出被漏掉或走样的部分。**

`parrotline` —— 逐条比对原文与复述，找出遗漏的约束、弱化的语气与新增的不存在的限制

- 零依赖，Python 3.10+ 标准库即可运行
- 单文件，`parrotline.py` 拷走就能用
- 不联网、不写文件

<!-- ipos:install -->
## 安装

零依赖，Python 3.10+ 即可：

```bash
pip install rogery77-parrotline
```

装完直接用命令名调用：

```bash
parrotline --help
```

也可以不用安装，直接把 `parrotline.py` 拷走用——它只依赖标准库。

## 为什么需要它

复述偏差是评测数据构造时的常见污染源，工具专门盯这个

它遵守下面几条自己定的规矩：

1. **只报告能定位到具体位置的结论**，不做语义猜测。
2. **规则表公开**，每条命中都能对应到 提示词复述偏差 领域的一条明示规则。
3. **输入为空或格式不对时明确报错**，不静默返回空结果。

## 用法

```bash
python parrotline.py --file input.txt
python parrotline.py --text "示例内容"
python parrotline.py --file input.txt --json
```

加 `--json` 可以拿到机器可读的结果，便于接到流水线里。

## 已知局限

- 一致性靠字面差异判定，语义等价但写法不同会误报。
- 不解析跨文档的引用关系。

## 跑测试

```bash
python test_parrotline.py
```

测试用独立的断言与临时数据，不污染工作目录。

## 来源与参考

- Python 标准库文档：<https://docs.python.org/3/>
- GitHub 仓库：<https://github.com/rogery77/parrotline>

---

## 关于作者

rogery77 做提示词复述偏差相关的问题。这个工具先替你回答一个具体问题，再谈别的。

- 个人主页：<https://rogery77.github.io>
- 仓库：<https://github.com/rogery77/parrotline>

## 许可

MIT，见 [LICENSE](LICENSE)。
