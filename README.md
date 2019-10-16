# cmakelearn

```sh
$ cmake .	#get Makefile
$ make		#get executable file
$ sudo make install
$ make test
```

需要删除才能重新生成

```sh
$ sudo make install
[sudo] password for txcom-ubuntu64: 
[ 50%] Built target MathFunctions
[100%] Built target demo
Install the project...
-- Install configuration: ""
-- Installing: /usr/local/bin/demo
-- Installing: /usr/local/include/config.h
-- Installing: /usr/local/bin/libMathFunctions.a
-- Installing: /usr/local/include/MathFunctions.h
```

```sh
$ make test
Running tests...
Test project /home/txcom-ubuntu64/cmakelearn/demo5
    Start 1: test_run
1/5 Test #1: test_run .........................   Passed    0.00 sec
    Start 2: test_usage
2/5 Test #2: test_usage .......................   Passed    0.00 sec
    Start 3: test_5_2
3/5 Test #3: test_5_2 .........................   Passed    0.00 sec
    Start 4: test_10_5
4/5 Test #4: test_10_5 ........................   Passed    0.00 sec
    Start 5: test_2_10
5/5 Test #5: test_2_10 ........................   Passed    0.00 sec

100% tests passed, 0 tests failed out of 5

Total Test time (real) =   0.01 sec
```