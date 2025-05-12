# python中的路径

## 工作目录
在Python中，文件路径的解析是相对于脚本执行时所在的目录（即工作目录）进行的。工作目录决定了Python如何查找和访问文件。
  
例如：在路径`/home/user/`下有一个文件`test.py`，执行如下命令
```bash
python test.py
```
则python会在`/home/user/`下寻找`test.py`文件。并且会将`/home/user/`设定为当前的工作目录（CWD, currentWorkDir）。

在 python 中可以通过 导入 pathlib 模块来获取当前的工作目录。
```python
from pathlib import Path

print(Path.cwd())    # /home/user
```

## 拼接路径
pathlib模块是在 python  3.4 中引入的，它提供了一种跨平台的方法来处理文件路径。通过 `/` 运算符可以合并路径，pathlib会自动将其转换为操作系统的正确路径分隔符。
例如：
```python
from pathlib import Path

p = Path("/home/user") / "test.py"
print(p)    # /home/user/test.py
```

## 绝对路径与相对路径
在 Python中的相对路径是基于当前的**工作目录(CWD)**来决定的。也就是说一个相对路径等价于当前工作目录与相对路径所组成的绝对路径。
例如：
```python
from pathlib import Path

p = Path("test.py")
equals(p, Path.cwd() / "test.py") # True

```
而获取绝对路径的方法是使用`Path.resolve()`方法。
```python
from pathlib import Path

print(Path.cwd())    # /home/user
p = Path("test.py")
print(p.resolve())    # /home/user/test.py
```

## pathlib模块的其他方法
- `Path.exists()`：检查路径是否存在。
- `Path.is_file()`：检查路径是否为文件。
- `Path.is_dir()`：检查路径是否为目录。
- `Path.parent`：获取路径的父目录。
  
### 获取脚本文件自身的路径
```python
from pathlib import Path
script_path_pl = Path(__file__).resolve()  #.resolve() 获取绝对路径并解析符号链接
print(f"脚本路径 (pathlib, 绝对路径): {script_path_pl}")
```

### 获取脚本所在的目录
```python
from pathlib import Path
script_directory_pl = Path(__file__).resolve().parent  # .resolve() 获取绝对路径并解析符号链接
print(f"脚本所在目录 (pathlib, 绝对路径): {script_directory_pl}")   
```