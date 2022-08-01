## Rust
- 迭代器使用不熟，迭代器有哪些方法、有什么用 不熟悉
- 错误处理不熟悉
- 
## lab1 还没过！
- 对需要的、能用的 类型和长度要求不清楚！
- 对裸指针能进行的操作不熟悉，如何通过裸指针获取指针指向的数据、可以通过裸指针干什么，只知道有个解引用裸指针和能通过裸指针和长度信息生成slice

对于试验本身，开始很长时间都没注意user这边发起的系统调用传递了参数， traphandler里还在找为什么收到的是这些参数类型

## 问题：

lab1 还没过！原本能通过的测试，做作业之后反而不能通过了，不知道为什么 
```
python3 check/ch3.py < stdout-ch3
[PASS] found <Hello, world from user mode program!>
[PASS] found <Test power_3 OK25719!>
[PASS] found <Test power_5 OK25719!>
[PASS] found <Test power_7 OK25719!>
[FAIL] not found <get_time OK25719! (\d+)>      <<< 这里
[FAIL] not found <Test sleep OK25719!>          <<< 这里
[PASS] found <current time_msec = (\d+)>
[FAIL] not found <time_msec = (\d+) after sleeping (\d+) ticks, delta = (\d+)ms!>        <<< 这里
[FAIL] not found <Test sleep1 passed25719!>     <<< 这里
[PASS] found <Test write A OK25719!>
[PASS] found <Test write B OK25719!>
[PASS] found <Test write C OK25719!>
[FAIL] not found <string from task info test>   <<< 这里原本就是作业需要通过的测试
[FAIL] not found <Test task info OK25719!>      <<< 这里原本就是作业需要通过的测试
[PASS] not found <FAIL: T.T> 
```
注释掉自己添加的所有方法，只留TCB里添加的两个字段，并在 TCB初始化时添加了两个字段 及 `run_next_task`方法里更新了`first_start_time`
```
first_start_time:0,
syscall_times: [0;MAX_SYSCALL_NUM]
```
这时 make test3 就已经边这样了，没有修改过sys_get_time()系统调用
