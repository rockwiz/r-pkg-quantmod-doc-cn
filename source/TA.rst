TA
==

描述
    一组往图形上添加技术指标的函数

详细
    往用chartSeries创建的金融图表上添加技术分析研究或叠加的一般机制

    标注“\*”的功能通过TTR包实现

    一般TA绘图工具

    :addTA:         add data as custom indicator
    :dropTA:        remove technical indicator
    :moveTA:        move a technical indicator
    :swapTA:        swap two technical indicators

    目前技术指标包括

    :addADXadd:     Welles Wilder’s Directional Movement Indicator \*
    :addATRadd:     Average True Range \*
    :addAroon:      add Aroon Indicator \*
    :addAroonOsc:   add Aroon Oscillator \*
    :addBBands:     add Bollinger Bands \*
    :addCCI:        add Commodity Channel Index \*
    :addCMF:        add Chaiken Money Flow \*
    :addChAD:       add Chaiken Accumulation Distribution Line \*
    :addChVol:      add Chaiken Volatility \*
    :addCMO:        add Chande Momentum Oscillator \*
    :addDEMA:       add Double Exponential Moving Average \*
    :addDPO:        add Detrended Price Oscillator \*
    :addEMA:        add Exponential Moving Average \*
    :addEMV:        add Arm’s Ease of Movement \*
    :addEnvelope:   add Moving Average Envelope
    :addEVWMA:      add Exponential Volume Weighted Moving Average \*
    :addExpiry:     add options or futures expiration lines
    :addKST:        add Know Sure Thing \*
    :addLines:      add line(s)
    :addMACD:       add Moving Average Convergence Divergence \*
    :addMFI:        add Money Flow Index \*
    :addMomentum:   add Momentum \*
    :addOBV:        add On-Balance Volume \*
    :addPoints:     add point(s)
    :addROC:        add Rate of Change \*
    :addRSI:        add Relative Strength Indicator \*
    :addSAR:        add Parabolic SAR \*
    :addSMA:        add Simple Moving Average \*
    :addSMI:        add Stochastic Momentum Index \*
    :addTDI:        add Trend Direction Index \*
    :addTRIX:       add Triple Smoothed Exponential Oscillator \*
    :addVo:         add Volume if available
    :addVolatility: add volatility \*
    :addWMA:        add Weighted Moving Average \*
    :addWPR:        add Williams Percent R \*
    :addZigZag:     add Zig Zag \*
    :addZLEMA:      add ZLEMA \*

    参阅单个函数以获取特定实现和参数细节。基本的TTR实现细节可从TTR包找到。

    技术指标的add\*\*\*版本和TTR基础函数间的主要改变是前者没有data参数。

    值得注意的增加包括on, with.col。

返回值
    利用它运行产生的效果，一个chobTA类对象将静默返回。如果从R命令行调用，该方法在当前图表上绘制适当的技术指标。

备注
    从函数或脚本中调用任何上述方法通常需要将其包装在一个plot调用中，因为它们依赖调用初始化实际图表附加物的上下文（context）。

参考
    Josh Ulrich编写的TTR包

范例
::

    ## Not run:
    addADX()
    ## End(Not run)


