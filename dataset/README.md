# #**高速路数据集（HighSpeedDatasate）使用说明** 

##### ##数据集说明 

##### 本仓库包含 4GB 高速路场景目标检测数据集，因单文件上传限制（≤25MB），已拆分为多个 25MB 分包存储。

##### -分包命名：`HighSpeedDatasate_part_aa`、`HighSpeedDatasate_part_ab`、`HighSpeedDatasate_part_ac`... 

##### -总大小：4GB 

#### -格式：ZIP 压缩包（包含标注文件、图片文件） 

## ## 一、合并分包为完整压缩包 

## ### 方式 1：使用 Git Bash（推荐，和拆分指令配套） 

## #### 步骤 1：打开 Git Bash 

##### - 双击桌面「Git Bash」快捷方式（安装 Git for Windows 后自动生成）； 

##### - 或在文件夹空白处右键 → 选择「Git Bash Here」。 

## #### 步骤 2：进入分包所在文件夹 

##### 将仓库克隆到本地后，执行以下命令进入数据集分包目录（替换为你的实际路径）： ```bash 

## # 示例路径：桌面 HighSpeed 仓库的 dataset 文件夹 

##### cd /c/Users/Pepsi/Desktop/HighSpeed/dataset
