---
title: conda list报错：TypeError：‘＜‘ not supported between instances of ‘str‘ and ‘NoneType‘
date: 2021-11-30 19:48:34
tags:
 - Python
 - Error Record
categories: Python
---

# 问题描述

安装mmcv之后,conda list就会报错:

```bash
	Traceback (most recent call last):
      File "/home/nercms/anaconda3/lib/python3.7/site-packages/conda/exceptions.py", line 1062, in __call__
        return func(*args, **kwargs)
      File "/home/nercms/anaconda3/lib/python3.7/site-packages/conda/cli/main.py", line 84, in _main
        exit_code = do_call(args, p)
      File "/home/nercms/anaconda3/lib/python3.7/site-packages/conda/cli/conda_argparse.py", line 82, in do_call
        exit_code = getattr(module, func_name)(args, parser)
      File "/home/nercms/anaconda3/lib/python3.7/site-packages/conda/cli/main_list.py", line 142, in execute
        show_channel_urls=context.show_channel_urls)
      File "/home/nercms/anaconda3/lib/python3.7/site-packages/conda/cli/main_list.py", line 80, in print_packages
        show_channel_urls=show_channel_urls)
      File "/home/nercms/anaconda3/lib/python3.7/site-packages/conda/cli/main_list.py", line 45, in list_packages
        installed = sorted(PrefixData(prefix, pip_interop_enabled=True).iter_records(),
      File "/home/nercms/anaconda3/lib/python3.7/site-packages/conda/core/prefix_data.py", line 130, in iter_records
        return itervalues(self._prefix_records)
      File "/home/nercms/anaconda3/lib/python3.7/site-packages/conda/core/prefix_data.py", line 159, in _prefix_records
        return self.__prefix_records or self.load() or self.__prefix_records
      File "/home/nercms/anaconda3/lib/python3.7/site-packages/conda/common/io.py", line 88, in decorated
        return f(*args, **kwds)
      File "/home/nercms/anaconda3/lib/python3.7/site-packages/conda/core/prefix_data.py", line 72, in load
        self._load_site_packages()
      File "/home/nercms/anaconda3/lib/python3.7/site-packages/conda/core/prefix_data.py", line 274, in _load_site_packages
        python_record = read_python_record(self.prefix_path, af, python_pkg_record.version)
      File "/home/nercms/anaconda3/lib/python3.7/site-packages/conda/gateways/disk/read.py", line 257, in read_python_record
        paths_tups = pydist.get_paths()
      File "/home/nercms/anaconda3/lib/python3.7/site-packages/conda/common/pkg_formats/python.py", line 268, in get_paths
        records = sorted(concatv(records, ((pf, None, None) for pf in missing_pyc_files)))
    TypeError: '<' not supported between instances of 'str' and 'NoneType'
```

<!-- more -->

# 解决方法

按照报错的路径去找，找最后一个报错的py文件: File "/home/nercms/anaconda3/lib/python3.7/site-packages/conda/common/pkg_formats/python.py", line 268

找到第268行, 改成下图所示, 把报错的地方加了个异常处理：

{%asset_img 1.png %}

之后，conda list就可以正常使用了。

