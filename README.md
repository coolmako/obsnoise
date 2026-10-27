# obsnoise

**检查智能体收到的观察里是否混入了无效信息。**

`obsnoise` —— 识别工具返回中的超时回退、空结果与错误混入，标出噪声比例

- 零依赖，Python 3.10+ 标准库即可运行
- 单文件，`obsnoise.py` 拷走就能用
- 不联网、不写文件

<!-- ipos:install -->
## 安装

零依赖，Python 3.10+ 即可：

```bash
pip install coolmako-obsnoise
```

装完直接用命令名调用：

```bash
obsnoise --help
```

也可以不用安装，直接把 `obsnoise.py` 拷走用——它只依赖标准库。

## 为什么需要它

工具返回被降级处理时最容易混进噪声，工具专门查这一点

它遵守下面几条自己定的规矩：

1. **只报告能定位到具体位置的结论**，不做语义猜测。
2. **规则表公开**，每条命中都能对应到 智能体观察噪声 领域的一条明示规则。
3. **输入为空或格式不对时明确报错**，不静默返回空结果。

## 用法

```bash
python obsnoise.py --file input.txt
python obsnoise.py --text "示例内容"
python obsnoise.py --file input.txt --json
```

加 `--json` 可以拿到机器可读的结果，便于接到流水线里。

## 已知局限

- 相似度按字符与词估算，不等于向量相似度。
- 不联网，不做语义检索。

## 跑测试

```bash
python test_obsnoise.py
```

测试用独立的断言与临时数据，不污染工作目录。

## 来源与参考

- Python 标准库文档：<https://docs.python.org/3/>
- GitHub 仓库：<https://github.com/coolmako/obsnoise>

---

## 关于作者

coolmako 做智能体观察噪声相关的问题。这个工具先替你回答一个具体问题，再谈别的。

- 个人主页：<https://coolmako.github.io>
- 仓库：<https://github.com/coolmako/obsnoise>

## 许可

MIT，见 [LICENSE](LICENSE)。
