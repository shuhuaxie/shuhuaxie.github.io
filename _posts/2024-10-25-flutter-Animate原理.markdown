
- Animate典型运行代码
```
    _controller = AnimationController(
      duration: const Duration(seconds: 2),
      vsync: this,
    );

    _animation = Tween<Offset>(
      begin: Offset(0, 0), // 起始位置
      end: Offset(1, 0), // 结束位置
    ).animate(CurvedAnimation(
      parent: _controller,
      curve: Curves.easeInOut, // 使用缓动曲线
    ));

    child: AnimatedBuilder(
          animation: _animation,
          builder: (context, child) {
            return SlideTransition(
              position: _animation,
              child: Container(
                width: 100,
                height: 100,
                color: Colors.blue,
              ),
            );
          },
        ),
```
- 运行原理
    - Ticker触发数值变化，并触发stateChange，根据新的数值创建新的widget
    - Ticker
        - 由TickerCallback构造
        - 通过_startTime记录动画开始时间
        - 底层使用SchedulerBinding.instance.scheduleFrameCallback作为触发器
    - SingleTickerProviderStateMixin
        - 触发Ticker
    - 构造
        - AnimatedBuilder
            - Listenable - Animation
            ```
                // 为animation添加setState的监听
                widget.listenable.addListener(_handleChange);
                    setState(() {
                        // The listenable's state is our build state, and it changed already.
                    });
            ```
            - SlideTransition
                - Animation
        - Animation
            - Controller
                - SingleTickerProviderStateMixin
                    - Ticker      
    - 触发开始
        - _controller.forward();
            - _ticker!.start();
                - SchedulerBinding.instance.scheduleFrameCallback(_tick, rescheduling: - rescheduling);
    - 运行
        - Ticker : void _tick(Duration timeStamp)
            - AnimationController: void _tick(Duration elapsed)
                ```
                _value = clampDouble(_simulation!.x(elapsedInSeconds), lowerBound, upperBound);
                notifyListeners();
                _handleChange:setState
                ```
            - _animation: _AnimatedEvaluation
                ```
                _evaluatable.evaluate(parent); // Tween -> CurvedAnimation
                activeCurve.transform(t); // CurvedAnimation -> AnimationController|Animation<double>
                ```
            










 








    






