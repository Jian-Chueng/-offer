##### 机器人研发工程师 Robotic Research Engineer



岗位描述Job Description

人工智能实验室Robotics Lab致力于研发新一代物流/服务机器人；
其中涉及到机械结构, 电子工程, 软件系统, 自动控制, 动力系统, 嵌入式系统, 深度学习, 环境感知, SLAM, 避障与导航, 路径规划, 人机交互, 工业设计, 产品规划, 项目管理, 供应链管理等多个领域。

岗位要求Qualifications

\1. 计算机, 软件工程, 通信工程, 电子信息, 机械设计, 自动化, 精密仪器, 自动控制, 应用数学, 航天工程, 机器人学等相关专业背景；
\2. 在校期间有参加过各类机器人/无人机比赛并取得优异成绩者, 或在Robotics/Control/CV/HCI 等相关领域的顶级会议/期刊发表高水平论文者优先；
**\3. 系统软件岗位需熟悉Linux及开发环境, C++/Python/Java精通其一, 有多线程编程经验优先，有大型项目经验者优先；**
**\4. 算法研发岗位需熟悉机器人算法或者深度学习算法，以下领域精通其一：SLAM, path/motion planning, control, object detection, semantic segmentation, sensor fusion & calibration。**

同时，我们还希望你：
\1. 学习能力强，对新事物保有好奇心，并能快速适应新环境
\2. 良好的沟通能力和团队协同能力；能与他人合作，共同完成目标
\3. 对所在领域有热情，相信方法总比困难多，善于独立思考并反思总结

还在犹豫什么？我们期待着你的加入

工作地点Location

杭州市(Hangzhou)

参加面试的城市或地区Interview City or Region

远程(Remote Interviews)

[网址](https://campus.alibaba.com/traineePositions.htm?spm=a1z3e1.11874847.0.0.5d8d4928aOxyxa&refno=12412)



# **基础测评**

**40道选择题+评估性格的97题**

2020春招的测评内容分为4个部分。前3个部分为单选，每道题都有好像90秒的时间限制，每个部分结束可以休息一下。第4部分是三选二，无时间限制。

1. （11道）给出一段话，然后据此选择正确的表述选项（阅读理解）。
2. （11道）根据图表总结信息，需要估算之类的:观察能力与数学，大概是给你一张图求一些净利润，月增长率
3. （11道）找规律。
4. （98道）从3个正面的选项里选出最符合自己和最不符合自己的2项。



# **笔试流程：**

大概你可能要提前10分钟进行调试，调试摄像头，屏幕录制，还有手机监控。**纪律**可以用自己的编译器**，其他跟常规一样。**

**1.有且只有2个编程题，没有选择题，时间1个小时。**

总的来说这次题目对我而言题目还是比较难，时间只有1个小时，平时都是面向百度的编程......

第一题，这有一点斗地主知识可能会理解的更快一点，**题目大概意思就是我们给你一副牌（无论几张），计算出你打光他的最少步数。**

鄙人思路就是分情况讨论，首先如果牌少于4则不可能成顺子，那么他的情况只能是对子，或者无对子，无对子的情况，出牌数是数组本身的长度。若牌的数大于4则有可能成顺子（完成度大概是这一步）。把顺子找出来，摘去顺子，计数加1。如果还有就再摘去，计数加1，直到没有顺子。然后如果有对子就摘去计数在＋1，若对子连续3个，计数-2。代码就不放了，粗糙......

**第二题是关于一个ASCALL的题**，题目没怎么看。第一题都来不及呢。





我感觉第一题是真的陷进去了:

当时主要是考虑的是顺子和对子冲突的情况，如果对子把顺子拆散了，那还要不要出对子

这种情况下:56778899，出对子，只用出三次牌; 出顺子，4次牌;这种情况下:45667788910,出顺子，只用出两次牌;出对子，5次牌;

然后就想用dfs搜索，分别搜索出对子和出顺子的情况，结果没时间;



第二题，给定一些非递减的字符串，然后问拼接成最长的字符的长度(保持非递减性质):

我的思路是，求出所有起始字母的集合，做成一个字典;每个起始字母，对应一个装了很多字符串的列表

如果你随机选择了一个字符串后，你当前的字母就这个字符串最后的字符，然后在字典去找下个字符所对应的列表，再随便选择一个

然后可以利用bfs去搜索这件事情

要用很多数据结构就换了python,结果还是没时间 = =







---

作者：十柒201911151658203
链接：https://www.nowcoder.com/discuss/389676?type=1
来源：牛客网



### 第一题

> 输入一个整数n 1<n<10^9
> 输出一个整数
> 找出其所有非空子集中所有元素个数之和，然后对10^9+7取模，输出结果
> 例如输入2，有{1}，{2}，{1，2}3个非空子集，所有元素个数之和为4
> 输出结果为4

#### 思路

用int肯定会超，需要用到BigInteger

对于输入n，求得所有元素之和为n*2^(n-1)

然后再对10^7+7取模即可

### 代码

```c++
作者：十柒201911151658203
链接：https://www.nowcoder.com/discuss/389676?type=1
来源：牛客网

public class Solution1 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String n = sc.next();
        BigInteger in = BigInteger.valueOf(Long.parseLong(n));
        BigInteger num = f(in);//种数
        BigInteger x = BigInteger.valueOf(10).pow(9).add(BigInteger.valueOf(7));
        System.out.println(num.mod(x));
    }
 
    private static BigInteger f(BigInteger n) {
        return n.multiply(BigInteger.valueOf(2).pow(n.intValue()-1));
    }
}
```

### 第二题

> 输入n,m两个整数代表n行m列
> 下面输入n行字符串，每个字符串都包含m个字符（只含有'.','#','E','S'）
> 其中S代表起点，E代表终点，#代表无法通过
> 从起点出发，可向左，向右，向上，向下移动一步
> 也可按如下中心对称移动，也只算移动一步
> X（i,j）→  X‘（n+1-i,m+1-j）
> 求从起点到终点最少需要移动几步

示例输入

```
4 4
#S..
E#..
#...
....
```

输出

```
4
```

说明
先中心对称到达（4，3），然后向上一步，向右一步，中心对称到达终点





作者：红枫归尘
链接：https://www.nowcoder.com/discuss/390915?type=1
来源：牛客网



1、从n个人中选择任意数量的人员组成一支队伍，然后从一支队伍中选出一位队长，不同的队长算不同的组合，问这样的组合的数量对10^9+7取模 。 



```python
作者：红枫归尘
链接：https://www.nowcoder.com/discuss/390915?type=1
来源：牛客网

def quick_power_mod(x, n, mod):
    res = 1
    while n:
        if n & 1:
            res = res * x % mod
        n = n >> 1
        x = (x ** 2) % mod
    return res
 
n = 2
mod = 10 ** 9 + 7
mod1 = quick_power_mod(2, n-1, mod)
mod2 = n % mod
result = (mod1 * mod2) % mod
 
print(result)
```

快速幂算法，递推公式为S=n*(2^n-1)

  笔试时递推公式没进一步优化，先去做第二题了，导致时间不太够，递推公式没推好的话会超时。 

```python
作者：红枫归尘
链接：https://www.nowcoder.com/discuss/390915?type=1
来源：牛客网

def dfs(pos_x, pos_y, road, fly_time, time, min_time):
    if time >= min_time:
        return min_time
    if sum([road[i][j] == 0 for i in range(n) for j in range(m)]) == 0:
        return min_time
 
    # down
    if (0 <= pos_x + 1 < n) and road[pos_x+1][pos_y] != 1:
        if road[pos_x+1][pos_y] == 2:
            return time+1
        else:
            road[pos_x+1][pos_y] = 1
        min_time = min(dfs(pos_x+1, pos_y, road, fly_time, time+1, min_time), min_time)
        road[pos_x+1][pos_y] = 0
    # up
    if (0 <= pos_x - 1 < n) and road[pos_x-1][pos_y] != 1:
        # print('up')
        if road[pos_x-1][pos_y] == 2:
            return time+1
        else:
            road[pos_x-1][pos_y] = 1
        min_time = min(dfs(pos_x-1, pos_y, road, fly_time, time+1, min_time), min_time)
        road[pos_x-1][pos_y] = 0
    # left
    if (0 <= pos_y - 1 < m) and road[pos_x][pos_y-1] != 1:
        road[pos_x][pos_y-1] = 1
        min_time = min(dfs(pos_x, pos_y-1, road, fly_time, time+1, min_time), min_time)
        road[pos_x][pos_y-1] = 0
    # right
    if (0 <= pos_y + 1 < m) and road[pos_x][pos_y+1] != 1:
        # print('right')
        if road[pos_x][pos_y+1] == 2:
            return time+1
        else:
            road[pos_x][pos_y+1] = 1
        min_time = min(dfs(pos_x, pos_y+1, road, fly_time, time+1, min_time), min_time)
        road[pos_x][pos_y+1] = 0
    # fly machine
    if (0 <= n - 1 - pos_x < n) and (0 <= m - 1 - pos_y < m) and road[n-1-pos_x][m-1-pos_y] != 1 and fly_time > 0:
        # print('fly')
        if road[n-1-pos_x][m-1-pos_y] == 2:
            return time+1
        else:
            road[n-1-pos_x][m-1-pos_y] = 1
        min_time = min(dfs(n-1-pos_x, m-1-pos_y, road, fly_time-1, time+1, min_time), min_time)
        road[n-1-pos_x][m-1-pos_y] = 0
 
    return min_time
 
 
n, m = [4, 4]
road = [[1, 1, 0, 0], [2, 1, 0, 0], [1, 0, 0, 0], [0, 0, 0, 0]]
born_x = 0
born_y = 1
fly_time = 5
min_time = 1000000000000000000000
time = dfs(born_x, born_y, road, fly_time, 0, min_time)
if time == 1000000000000000000000:
    time = -1
print(time)
```

用了dp来做，笔试时也没做出来orz 后来发现问题在于每一次搜索的时候设置了步进的点为1，导致初始设定2为终点的判定始终未找到，以及时间不太够，摔

  用惯了台式机再用笔记本写感觉屏幕和键盘用着好难受😂 

  难受，希望面试时能顺利些，预祝大家都能有好结果♥

