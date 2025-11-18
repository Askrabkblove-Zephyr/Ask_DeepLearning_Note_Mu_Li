# 安装miniconda

```shell
sudo apt update
sudo apt install build-essential # 编译器
sudo apt install python3.12 # 安装python3.12

mkdir -p ~/miniconda3 # mkdir -p 创建目录时，同时创建所有不存在的父级目录。
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda3/miniconda.sh

bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
```

| 参数                            | 全称       | 作用                             |
| :------------------------------ | :--------- | :------------------------------- |
| **`bash`**                      | -          | 使用 Bash shell 执行安装脚本     |
| **`~/miniconda3/miniconda.sh`** | -          | Miniconda 安装脚本的路径         |
| **`-b`**                        | `--batch`  | **批处理模式**，自动接受许可协议 |
| **`-u`**                        | `--update` | 如果已存在则更新现有安装         |
| **`-p ~/miniconda3`**           | `--prefix` | **指定安装路径**                 |

```shell
rm ~/miniconda3/miniconda.sh #安装完成后删除
```

**激活conda**：

 `source ~/miniconda3/bin/activate`

**初始化conda**：

`conda init --all --dry-run`

**永久禁用自动激活（推荐）**：

`conda config --set auto_activate_base false`

**手动退出环境**：

`conda deactivate`

**删除环境**

`conda remove -n d2l --all` 

**切换镜像到清华源**

`pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple`

**切回官方源**

`pip config unset global.index-url`

**需要时手动激活 base 环境**：

`conda activate base`

#### **安装jupyter**：

`conda install jupyter`

**检验安装**

`which jupyter`

#### **安装d2l**：

- **去华为云镜像下载**：

`https://repo.huaweicloud.com/repository/pypi/simple/d2l/`

- **安装**：

 `pip install d2l-0.15.1.tar.gz`

- **检验安装**：

```
python
import d2l
print(d2l.__version__)
exit()
```

#### **安装pytorch**：

**nvcc --version 查看安装的CUDA版本号，根据版本号安装**

`pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121`



# windows下：

```
驱动API指的是显卡驱动支持的最高cuda版本
【nvidia-smi】
查看安装的CUDA版本
【nvcc --version】
```

首先miniconda是**环境管理工具**

- 参考<u>https://www.anaconda.com/docs/getting-started/miniconda/install#windows-powershell</u>下载miniconda

- 或者打开powershell输入：

  `Invoke-WebRequest -Uri "https://repo.anaconda.com/miniconda/Miniconda3-latest-Windows-x86_64.exe" -outfile ".\miniconda.exe" Start-Process -FilePath ".\miniconda.exe" -ArgumentList "/S" -Wait del .\miniconda.exe`

**安装好之后打开**`Anaconda PowerShell Prompt`输入：

**从Anaconda官方获取软件包：**

```shell
conda tos accept --override-channels --channel https://repo.anaconda.com/pkgs/main
conda tos accept --override-channels --channel https://repo.anaconda.com/pkgs/r
conda tos accept --override-channels --channel https://repo.anaconda.com/pkgs/msys2
```

**创建一个3.8环境**

`conda create --name d2l python=3.8 -y`   

**激活d2l环境**

`conda activate d2l` 

**去华为云镜像下载**：

`https://repo.huaweicloud.com/repository/pypi/simple/d2l/`

**安装**：

`pip install d2l-0.15.1.whl`

#### **安装pytorch**：

**nvcc --version 查看安装的CUDA版本号，根据版本号安装**

`pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu130`

或者下载之前的版本

`https://pytorch.org/get-started/previous-versions/`