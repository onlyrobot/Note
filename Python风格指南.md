# Python风格指南

## Python导入格式

```python
import module_name [as mn]
from module_name import xxx
```

## Python命名规范

>package_name, module_name, ClassName, instance_var_name, method_name, ExceptionName, function_name, GLOBAL_VAR_NAME, function_parameter_name, local_var_name

## Python注释规范

```python
'''
Author: xxx
Date: xxx
Description: xxx
'''

class C:
    '''short decription

    long description

    Attributes:
        attr1: desctiption
        attr2: description
    '''

    def __init__(self):
        '''short description'''
        example = 1

    def fun(slef, param : type) -> type:
        '''short description

        long description.

        Args:
            arg1: description
            arg2: description

        Returns/Yields:
            description

        Raises:
            Error1: description
            Error2: description
        '''
        # single line annotation
        # single line annotation
        example = 1    # single line short annotation
        # TODO(your contact): what to do
```

## Python空行规范

* 顶级定义之间空两行
* 成员函数定义之间空一行
* 其他有必要的地方空一行

## 其他

* 每一行的长度尽量不超过80个字符
* 用4个空格来缩进
* 括号内不加空格，分号、逗号、冒号前面不加空格后面加空格（除了行尾）
* 尽量不要用#!作为文件开始
* 所有python模块都应该是可导入的，意味着作为脚本执行的语句要放在`main`函数里，用`if __name__ == '__main__'`来判断当前是否为`main`函数
