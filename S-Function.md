**S-Function模板调用**

matlab2022以前的版本：`edit sfuntmpl`

matlab2022以后的版本：`edit sfundsc2`

>注：用以上命令打开的都是level1的模板。2022以后版本弃用level1，使用level2，可以打开模板sfundsc2_level2.m或msfuntmpl.m。使用level1模板编写也可以运行。

**S-Function level1模板使用方法**

- 修改初始化函数`mdlInitializeSizes`参数

```Matlab
sizes.NumContStates = 1; %连续时间状态的个数

sizes.NumDiscStates = 0; %离散时间状态的个数

sizes.NumOutputs = 1; %输出的个数

sizes.NumInputs = 1; %输入的个数

sizes.DirFeedthrough = 0; %系统输入是否直接馈入输出，例如y=x为0，而y=x+u为1。控制器中也为1。

sizes.NumSampleTimes = 1; %设置采样时间的个数，最少是1

x0 = 0; # 初始状态

str = []; # 不用改一直为空矩阵

ts = [0 0]; % 采样时间设置，连续时间设置为[0 0]
%ts = [.1 0]; % Sample period of 0.1 seconds (10Hz)
```

采样时间`ts=[离散采样周期   偏移量]`,必须为mx2维度，其中m为上面参数NumSampleTimes的值，填写形式如下：
![[Pasted image 20240625171609.png]]
![[Pasted image 20240625170526.png]]

采样时间可以理解为采样周期，真正的`采样时刻=n*周期+偏移量`。
对于连续系统，采样时间应设为0，matlab也提供CONTINUOUS_SAMPLE_TIME，该宏的值=0;
对于固定步长的离散系统，可以直接设置采样间隔和偏移，形如：[0.1  0.02];
对于变步长的离散系统，可以设置为：[-2,  0.0]，这种参数需要同时simulink求解器solver设置成变步长的。
继承前一模块的采样点，可以设置为：[-1, 0]。

- 编写函数`function sys=mdlDerivatives(t,x,u)`

这部分编写连续系统方程
`sys = []`中的状态表示连续状态的导数。

- 编写函数`function sys=mdlUpdate(t,x,u)`

在此描述离散状态方程和其他每个仿真步长必须执行的过程。
`sys = []`表示 $x(k+1)$

- 编写函数`function sys=mdlOutputs(t,x,u)`

描述输出方程

- 编写函数`function sys=mdlGetTimeOfNextVarHit(t,x,u)`

计算下一个采样点的绝对时间，只有当在mdlInitializeSizes中指定了变步长离散采样时间时，才使用该程序。

**s-function level1模板**
```Matlab
function [sys,x0,str,ts,simStateCompliance] = sfuntmpl(t,x,u,flag)

% 主函数

switch flag,

% Initialization %

case 0,

[sys,x0,str,ts,simStateCompliance]=mdlInitializeSizes;

% Derivatives %

case 1,

sys=mdlDerivatives(t,x,u);

% Update %

case 2,

sys=mdlUpdate(t,x,u);

% Outputs %

case 3,

sys=mdlOutputs(t,x,u);

% GetTimeOfNextVarHit %

case 4,

sys=mdlGetTimeOfNextVarHit(t,x,u);

% Terminate %

case 9,

sys=mdlTerminate(t,x,u);

% Unexpected flags %

otherwise

DAStudio.error('Simulink:blocks:unhandledFlag', num2str(flag));

end

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

%%%%% 以下为子函数定义 %%%%%

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

function [sys,x0,str,ts,simStateCompliance]=mdlInitializeSizes

sizes = simsizes;% 必须首先调用且必须存在

sizes.NumContStates = 0;% 连续状态数

sizes.NumDiscStates = 0;% 离散状态数

sizes.NumOutputs = 0;% 输出个数

sizes.NumInputs = 0;% 输入个数

sizes.DirFeedthrough = 1;% 1为存在直接馈通，0为不存在

sizes.NumSampleTimes = 1;% 采样时间个数，至少是1

sys = simsizes(sizes);

x0 = [];% 初始状态

str = [];% str 置空

ts = [0 0];% 初始化采样时间数组

simStateCompliance = 'DefaultSimState';

function sys=mdlDerivatives(t,x,u)

%该函数可无

sys = [];%表示状态导数，即dx

function sys=mdlUpdate(t,x,u)

%每个仿真步都会调用该函数，在此描述离散状态方程和其他每个仿真步长必须执行的过程

sys = [];

function sys=mdlOutputs(t,x,u)

%该函数必须存在

sys = [];

function sys=mdlGetTimeOfNextVarHit(t,x,u)

%计算下一个采样时间，仅在系统为变采样时间系统时调用

sampleTime = 1; % 设置下一个采样时间为1s以后

sys = t + sampleTime;%

function sys=mdlTerminate(t,x,u)

%仿真结束时调用，在此完成仿真结束的收尾工作

sys = [];
```


