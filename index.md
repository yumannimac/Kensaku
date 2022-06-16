# 検索備忘録

pythonを使ってpythonの中身あるいはターミナルコマンド（シェルコマンド）を使って実行するコードのうち検索で結構使えそうだけど忘れそうなものを書く。


`introspect`を使うと`import`して`getfile`したライブラリの場所と中身を表示できる。


```python
import inspect
import numpy

print(inspect.getfile(numpy))
print(dir(numpy))

```


```python
import inspect
from scipy import optimize

print(inspect.getfile(optimize))
print(dir(optimize))

```

    /Library/Frameworks/Python.framework/Versions/3.10/lib/python3.10/site-packages/scipy/optimize/__init__.py
    ['BFGS', 'Bounds', 'HessianUpdateStrategy', 'LbfgsInvHessProduct', 'LinearConstraint', 'NonlinearConstraint', 'OptimizeResult', 'OptimizeWarning', 'RootResults', 'SR1', '__all__', '__builtins__', '__cached__', '__doc__', '__file__', '__loader__', '__name__', '__nnls', '__package__', '__path__', '__spec__', '_basinhopping', '_bglu_dense', '_cobyla', '_cobyla_py', '_constraints', '_differentiable_functions', '_differentialevolution', '_dual_annealing', '_group_columns', '_hessian_update_strategy', '_highs', '_lbfgsb', '_lbfgsb_py', '_linesearch', '_linprog', '_linprog_doc', '_linprog_highs', '_linprog_ip', '_linprog_rs', '_linprog_simplex', '_linprog_util', '_lsap', '_lsap_module', '_lsq', '_minimize', '_minpack', '_minpack2', '_minpack_py', '_moduleTNC', '_nnls', '_nonlin', '_numdiff', '_optimize', '_qap', '_remove_redundancy', '_root', '_root_scalar', '_shgo', '_shgo_lib', '_slsqp', '_slsqp_py', '_spectral', '_tnc', '_trlib', '_trustregion', '_trustregion_constr', '_trustregion_dogleg', '_trustregion_exact', '_trustregion_krylov', '_trustregion_ncg', '_zeros', '_zeros_py', 'anderson', 'approx_fprime', 'basinhopping', 'bisect', 'bracket', 'brent', 'brenth', 'brentq', 'broyden1', 'broyden2', 'brute', 'check_grad', 'cobyla', 'curve_fit', 'diagbroyden', 'differential_evolution', 'dual_annealing', 'excitingmixing', 'fixed_point', 'fmin', 'fmin_bfgs', 'fmin_cg', 'fmin_cobyla', 'fmin_l_bfgs_b', 'fmin_ncg', 'fmin_powell', 'fmin_slsqp', 'fmin_tnc', 'fminbound', 'fsolve', 'golden', 'lbfgsb', 'least_squares', 'leastsq', 'line_search', 'linear_sum_assignment', 'linearmixing', 'linesearch', 'linprog', 'linprog_verbose_callback', 'lsq_linear', 'minimize', 'minimize_scalar', 'minpack', 'minpack2', 'moduleTNC', 'newton', 'newton_krylov', 'nnls', 'nonlin', 'optimize', 'quadratic_assignment', 'ridder', 'root', 'root_scalar', 'rosen', 'rosen_der', 'rosen_hess', 'rosen_hess_prod', 'shgo', 'show_options', 'slsqp', 'test', 'tnc', 'toms748', 'zeros']



```python
import inspect
import numpy

print(inspect.getfile(numpy))
```

    /Library/Frameworks/Python.framework/Versions/3.10/lib/python3.10/site-packages/numpy/__init__.py


`__path__`でも表示できる。`dir`で中身を表示。


```python
import ffmpeg

print(ffmpeg.__path__)
print(dir(ffmpeg))

```

    ['/Library/Frameworks/Python.framework/Versions/3.10/lib/python3.10/site-packages/ffmpeg']
    ['Error', 'Stream', '__all__', '__builtins__', '__cached__', '__doc__', '__file__', '__loader__', '__name__', '__package__', '__path__', '__spec__', '_ffmpeg', '_filters', '_probe', '_run', '_utils', '_view', 'colorchannelmixer', 'compile', 'concat', 'crop', 'dag', 'drawbox', 'drawtext', 'filter', 'filter_', 'filter_multi_output', 'get_args', 'hflip', 'hue', 'input', 'merge_outputs', 'nodes', 'output', 'overlay', 'overwrite_output', 'probe', 'run', 'run_async', 'setpts', 'trim', 'unicode_literals', 'vflip', 'view', 'zoompan']


`sys`を使うと`sys.path`から何かのパスを表示


```python
import numpy 
import sys
print(sys.path)

```

    ['/Users/home/Documents/VSCode用/kensaku', '/Users/home/.vscode/extensions/ms-toolsai.jupyter-2022.5.1001601848/pythonFiles', '/Users/home/.vscode/extensions/ms-toolsai.jupyter-2022.5.1001601848/pythonFiles/lib/python', '/Library/Frameworks/Python.framework/Versions/3.10/lib/python310.zip', '/Library/Frameworks/Python.framework/Versions/3.10/lib/python3.10', '/Library/Frameworks/Python.framework/Versions/3.10/lib/python3.10/lib-dynload', '', '/Library/Frameworks/Python.framework/Versions/3.10/lib/python3.10/site-packages']


ターミナルコマンド`pwd`はカレンとディレクトリを表示。


```python
!pwd
```

    /Users/home/Documents/VSCode用/kensaku


`pprint`は一行ずつ表示。地味に便利だが忘れやすい。シェルコマンドだと`ls-1`だった気がする。


```python
import sys
import pprint

pprint.pprint(sys.path)

```

    ['/Users/home/Documents/VSCode用/kensaku',
     '/Users/home/.vscode/extensions/ms-toolsai.jupyter-2022.5.1001601848/pythonFiles',
     '/Users/home/.vscode/extensions/ms-toolsai.jupyter-2022.5.1001601848/pythonFiles/lib/python',
     '/Library/Frameworks/Python.framework/Versions/3.10/lib/python310.zip',
     '/Library/Frameworks/Python.framework/Versions/3.10/lib/python3.10',
     '/Library/Frameworks/Python.framework/Versions/3.10/lib/python3.10/lib-dynload',
     '',
     '/Library/Frameworks/Python.framework/Versions/3.10/lib/python3.10/site-packages']


シェルコマンドでは`pprint`は使えないらしい。


```python
import pprint
a=!$PATH
pprint.pprint(a)
```

    ['zsh:1: no such file or directory: '
     '/usr/local/bin:/usr/local/bin:/usr/local/bin:/usr/local/bin:/usr/local/bin:/usr/local/bin:/usr/local/bin:/usr/local/bin:/usr/local/bin:/usr/local/bin:/usr/local/bin:/usr/local/bin:/usr/local/bin:/usr/local/bin:/usr/local/bin:/usr/local/bin:/usr/local/bin:/usr/local/bin:/usr/local/bin:/usr/local/bin:/usr/local/bin:/usr/local/bin:/usr/local/bin:/usr/local/bin:/usr/local/bin:/usr/local/bin:/usr/local/bin:/usr/local/texlive/2022/bin/universal-darwin:/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin']


シェルコマンド続く。`ls`はカレントディレクトリの中身を表示する。オプション`-a`で隠さず表示。


```python
!ls 
```

    kensaku.ipynb


macの設定


```python
!sw_vers
```

    ProductName:	macOS
    ProductVersion:	12.4
    BuildVersion:	21F79


以下がこのjupyterの実行環境


```python
import sys


sys.executable

```




    '/usr/local/bin/python3'



使用可能なkernelのリスト


```python
!/Library/Frameworks/Python.framework/Versions/3.10/bin/jupyter kernelspec list

```

    Available kernels:
      python3105jvsc74a57bd0aee8b7b246df8f9039afb4144a1f6fd8d2ca17a180786b69acc140d282b71a49    /Users/home/.vscode/extensions/ms-toolsai.jupyter-2022.5.1001601848/temp/jupyter/kernels/python3105jvsc74a57bd0aee8b7b246df8f9039afb4144a1f6fd8d2ca17a180786b69acc140d282b71a49
      python3                                                                                   /Library/Frameworks/Python.framework/Versions/3.10/share/jupyter/kernels/python3

