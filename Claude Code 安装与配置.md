# Claude Code 安装与配置

分三步:安装node.js、安装git，安装配置claude

##  安装node.js

**下载安装：**

1. 打开浏览器，访问 Node.js 官网：https://nodejs.org/
2. 你会看到两个版本按钮，选择左边的 **LTS（长期支持版）**，这是最稳定的版本
3. 下载完成后，双击安装包
4. 安装过程中一路点 **"Next"**（下一步），保持默认选项即可
5. 最后点 **"Install"** 完成安装![image-20260621110539420](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20260621110539420.png)

**验证安装：**

安装完成后，**关闭并重新打开终端**（这一步很重要，否则新安装的命令可能找不到），然后输入：

```bash
# 检查 Node.js 版本
$ node -v
```

预期输出：

```
v24.15.0
```

（版本号可能不完全一致。建议安装官网当前 LTS 版本；如果用 npm 安装 Claude Code，需要 Node.js `v18` 或更高版本。）

```bash
# 检查 npm 版本（npm 是 Node.js 自带的包管理器）
$ npm -v
```

预期输出：

```
22.23.0
```

>  **验证**：如果两条命令都能输出版本号，恭喜，Node.js 安装成功！

![image-20260621110720933](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20260621110720933.png)



## git安装

Git 是一个"版本控制"工具。什么是版本控制？想象你在写一篇文章，每写一个版本你都存一份副本：`论文_v1.doc`、`论文_v2.doc`、`论文_最终版.doc`、`论文_最终最终版.doc`…… Git 就是帮你优雅地管理这些版本的工具。

在AI编程中，Git 尤其重要 —— 因为**AI有时候会改错代码**。有了 Git，你可以随时"时光倒流"回到之前正确的版本。这是你的"后悔药"。

**下载安装：**

**Windows 用户：**

1. 访问 https://git-scm.com/download/win
2. 下载 64-bit 版本的安装包
3. 双击安装，安装过程中保持所有默认选项即可（会有很多页配置，不用改，一直点 Next）
4. 安装完成

**验证安装：**

```bash
$ git --version
```

预期输出：

```
git version 2.43.0
```

**首次配置（必须）：**

安装完成后，需要告诉 Git 你是谁（这些信息会记录在每次代码提交中）：

```bash
# 设置你的名字（用英文，可以是昵称）
$ git config --global user.name "Your Name"

# 设置你的邮箱
$ git config --global user.email "your.email@example.com"
```

> **提示**：这里的名字和邮箱不需要是真实的，但建议和你将来注册 GitHub 的邮箱保持一致。

Git 最小生存技能（6条命令走天下）：**

你现在不需要精通 Git，只要记住这6条命令就够了（后面遇到会详细解释）：

```bash
# 1. 在项目文件夹中初始化 Git 仓库（只需要做一次）
$ git init

# 2. 查看当前文件状态（哪些文件被修改了）
$ git status

# 3. 把修改的文件添加到"暂存区"（准备提交）
$ git add .

# 4. 提交一个版本（附带说明信息）
$ git commit -m "描述这次修改做了什么"

# 5. 将代码推送到远程仓库（如GitHub）
$ git push

# 6. 从远程仓库拉取最新代码
$ git pull
```

>  **避坑**：使用AI编程工具时，养成一个好习惯 —— **在让AI做大的修改之前，先 `git add . && git commit -m "保存当前进度"`**。这样即使AI改坏了，你也能用 `git checkout .` 恢复到之前的状态。这是无数开发者总结出的血泪经验。



## Claude Code 安装与配置

**npm 安装：**

```bash
npm install -g @anthropic-ai/claude-code
```

**验证安装：**

```bash
$ claude --version
```

预期输出：

```
claude-code v1.x.x
```

>  **验证**：如果能看到版本号，说明安装成功！

![image-20260621111919032](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20260621111919032.png)

**配置settings.json**

打开claude所在文件位置

```bash
explorer.exe "$env:USERPROFILE\.claude"
```

![image-20260621112132187](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20260621112132187.png)

找到settings.json,如果没有的话就自己创建

![image-20260621112317498](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20260621112317498.png)

必须是在.claude下的文件夹

做好配置

```bash
{
  "env": {
    "ANTHROPIC_AUTH_TOKEN": "sk-你自己的key",
    "ANTHROPIC_BASE_URL": "https://api.deepseek.com/anthropic",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "deepseek-v4-pro",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "deepseek-v4-pro",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "deepseek-v4-flash",
    "CLAUDE_CODE_SUBAGENT_MODEL": "deepseek-v4-flash",
    "CLAUDE_CODE_MAX_OUTPUT_TOKENS": "32000"
  },
  "theme": "dark"
}

```

![image-20260621112659115](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20260621112659115.png)

启动成功