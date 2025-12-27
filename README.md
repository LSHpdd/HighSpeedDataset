# 数据集分包合并指南（从GitHub下载后）

本文档用于指导从GitHub仓库下载完3.7GB数据集的25MB分包后，通过终端命令合并为完整压缩包。支持Windows（Git Bash/CMD）、Linux、macOS系统，所有命令可直接复制执行。

## 一、合并前准备

1. 确认所有分包已下载完成，且保存在**同一文件夹**（建议新建单独文件夹，如「HighSpeedDataset」，避免与其他文件混淆）。

2. 分包命名格式为：`HighSpeedDatasate_part_aa`、`HighSpeedDatasate_part_ab`...（从GitHub下载后默认保持该命名，无需修改）。

3. 确保分包完整无缺失（3.7GB总大小约148个分包，缺失会导致合并后压缩包损坏）。

## 二、按操作系统执行合并命令

核心逻辑：通过系统终端命令拼接所有分包，还原为原始3.7GB压缩包（`HighSpeedDatasate.zip`）。

### 场景1：Windows系统（推荐用Git Bash，与拆分命令配套）

若已安装Git for Windows，直接打开「Git Bash」，按以下步骤操作：

1. 进入分包所在文件夹（将命令中的路径替换为你实际的分包存放路径）：
        `# 示例：分包存放在桌面的「HighSpeedDataset」文件夹
cd /c/Users/你的Windows用户名/Desktop/HighSpeedDataset`路径说明：Windows路径（如 `C:\Users\Pepsi\Desktop\HighSpeedDataset`）需转换为Git Bash格式——将 `\` 改为 `/`，盘符 `C:` 改为 `/c`。

2. 执行合并命令（直接复制，无需修改）：
        `# 合并所有25MB分包为完整压缩包
cat HighSpeedDatasate_part_* > HighSpeedDatasate.zip`

3. 等待执行完成（耗时约1-5分钟，取决于电脑性能），文件夹中会生成 `HighSpeedDatasate.zip`（完整3.7GB压缩包）。

### 场景2：Windows系统（无Git Bash，用CMD）

若未安装Git，直接用Windows自带的「命令提示符（CMD）」，步骤如下：

1. 进入分包所在文件夹（替换为你的实际路径）：
        `:: 示例：分包存放在桌面的「HighSpeedDataset」文件夹
cd C:\Users\你的Windows用户名\Desktop\HighSpeedDataset`

2. 执行合并命令（**必须加 /b 参数**，表示二进制模式，否则压缩包损坏）：
        `:: 合并所有分包为完整压缩包（/b 是核心参数，不可省略）
copy /b HighSpeedDatasate_part_* HighSpeedDatasate.zip`

3. 等待完成，生成 `HighSpeedDatasate.zip` 即为完整压缩包。

### 场景3：Linux/macOS系统

打开系统自带的「终端」，直接执行以下命令：

1. 进入分包所在文件夹（替换为你的实际路径）：
        `# 示例：分包存放在下载文件夹的「HighSpeedDataset」目录
cd ~/Downloads/HighSpeedDataset`

2. 执行合并命令（直接复制）：
        `# 合并所有分包为完整压缩包
cat HighSpeedDatasate_part_* > HighSpeedDatasate.zip`

## 三、合并后验证（必做！确保压缩包可用）

合并后建议执行以下步骤，验证压缩包完整性，避免因分包缺失/损坏导致解压失败。

### 1. 检查压缩包大小

- Windows Git Bash/Linux/macOS终端：
       `# 查看合并后压缩包大小（应显示约3.7GB）
ls -lh HighSpeedDatasate.zip`预期输出（示例）：`-rw-r--r-- 1 user staff 3.7G 12月 28 10:00 HighSpeedDatasate.zip`

- Windows CMD：
        `:: 查看压缩包大小
dir HighSpeedDatasate.zip`预期输出（示例）：`2025/12/28  10:00        3972843520 HighSpeedDatasate.zip`（数值约等于3.7GB）

### 2. 解压验证

双击 `HighSpeedDatasate.zip` 或用命令解压，若无「压缩包损坏」「文件缺失」等报错，且能看到完整的数据集文件（如图片、标注文件），则合并成功。

命令行解压示例（可选）：

```bash

# 解压到当前文件夹下的「HighSpeedDataset」目录
unzip HighSpeedDatasate.zip -d HighSpeedDataset
```

## 四、常见问题解决（避坑指南）

### 问题1：合并后压缩包损坏/解压失败

- 原因：分包缺失、下载不完整；Windows CMD合并时未加 `/b` 参数；分包命名被修改。

- 解决：
        1.  检查所有分包是否齐全（确认无缺失 `aa/ab/ac...` 等后缀的文件）；
        2.  重新下载缺失/损坏的分包；
        3.  Windows CMD用户重新执行合并命令，确保加上 `/b` 参数；
        4.  确保分包命名与GitHub上一致（未修改前缀/后缀）。
      

### 问题2：终端提示「No such file or directory」（文件或目录不存在）

- 原因：进入的文件夹路径错误；分包不在当前目录。

- 解决：
        1.  重新确认分包存放路径，修正 `cd` 命令中的路径；
        2.  执行 `ls`（Git Bash/Linux/macOS）或`dir`（CMD），确认当前目录下有 `HighSpeedDatasate_part_*` 系列分包。
      

### 问题3：合并后压缩包大小远小于3.7GB

- 原因：仅合并了部分分包；命令中的分包前缀写错（如少写字母、拼写错误）。

- 解决：
        1.  执行 `ls HighSpeedDatasate_part_*`（Git Bash/Linux/macOS）或 `dir HighSpeedDatasate_part_*`（CMD），查看所有分包是否都被识别；
        2.  确认合并命令中的前缀 `HighSpeedDatasate_part_` 与分包实际命名完全一致（区分大小写）。
      

## 五、补充说明

1. 合并原理：拆分是将原始压缩包「按字节分段」，合并是「按顺序拼接分段文件」，未重新压缩，因此合并后的压缩包与原始文件完全一致。

2. 工具兼容性：该方法支持所有主流解压工具（WinRAR、7-Zip、macOS归档实用工具等），合并后的 `.zip` 文件可正常解压。

3. 耗时说明：合并耗时主要取决于硬盘读写速度，3.7GB数据合并通常需要1-5分钟，耐心等待即可（终端无额外输出表示正在执行，无需中断）。
> （注：文档部分内容可能由 AI 生成）