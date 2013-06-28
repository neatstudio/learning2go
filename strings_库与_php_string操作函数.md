#####strings 库与 php string操作函数

* 字符串查找
    * Contains类的函数，基本上都是Index函数与0的比较值
        * strings.Contains("abc","a") 与  ( strpos() === false) 基本类似 ，
            * Contains 返回true和false 
            * 空字符串与空字符串 查找返回 true
        * strings.ContainsAny 与 strpos 空字符串返回false , 空字符串与空字符串返回false
        * strings.ContainsRune 与 strpos       
    * Index / IndexAny /IndexRune /IndexFunc 这些才是基本上与 strpos类似  
        * Index 函数返回 -1 ，代表找不到，其他均为能够找到（与javascript类似）
        * strpos 如果找不到是返回 === false，其他都为 int ，因为可能为 0
        * IndexFunc 根据条件进行查找并返回所在的位置，找不到为-1
    * LastIndex / LastIndexAny /LastIndexFunc 类似 strrpos    
    * HasPrefix 等同于 `strpos("string","str") === 0`
    * HasSuffix 等同于 `strrpos("string","str") == strlen(string)-strlen(str)    `             
* Count 与 substr_count 基本类似，返回原字符串指定字符串的个数
* EqualFold 忽略字符串大小写的对比，因为PHP可以直接对比，所以类似于 $a == $b
    * PHP中有strncmp /strncasecmp 等与EqualFold不一致。     
* Map 类似于。。。。`array_map(explode("",$str),'自定义函数') ,处理完后，对数据再joi(n"")`
* Repeat == str_repeat
* 字符串切分和合并：
    * Split / SplitAfter / SplitAfterN /Sp    litN ，类似HPP的：`explode,split,str_pslit`
    * SplitAfter，是在分割的时候，将分割字符也带上了
    * SplitAfterN ，是在SplitAfter的基础上，参考explode的num参数，即允许切分几次
    * SplitN 在Split的基础上，参考explode的num参数
    * Fields 将字符串按空格分割成数组（list数组），类P似HP:`array_filter(explode(" ",$tsr))`
        * 新的数组中，不含任何空字符（空白会被去除干净）
    * FieldsFunc 
        * 根据指定逻辑条件进行分割，当条件结果返回true时开始切割    
    * Join 等同于： join ,implode 函数
* 大小写相关
    * Title ，批量首字符大写。。几乎等于Ucwords
    * ToLower / ToTitle / ToUpper  == strtolower /strtoupper
    * ToLowerSpecial / ToTitleSpecial / ToUpperSpecial 
* Trim 相关
    * Trim == trim ,TrimLeft = ltrim ,TrimRight = rtrim , 
    * TrimFunc,TrimLeftFunc,TrimRightFunc
    * TrimPrefix , TrimSuffix
    * TrimSpace去掉不可见字符，
* 字符串替换
    * Replace 几乎等同于 str_replace
        * 不支持数组
        * 第三个参数一定要传，如果<0，则全部替换，如果>=0，则代表替换的次数。为0。。。这不蛋疼吗
        * php的str_replace最后一个num参数其实是引用，是计算你替换了几次。与这里的num参数不一样
    * Replacer 感觉就是str_replace的数组版。不过它的参数要能够一一对应，即参数是偶数个    
* Reader 
    * 通过读取一个字符串之后返回Reader对象
    * PHP中无类似函数，不过PHP可以直接 $str{0} , $str{1} 之类的操作
---        
####php中与strings不太一样的地方
* 字符串长度
    * Go:len / PHP:str_len strings包中没有，这是Go的全局函数 
    * 字符串表达方法
        * `` 与 PHP的HEREDOC 类似
        * go的字符串是双引号：""，单引号字符常量表⽰示⼀一个Unicode字符 (rune),支持\uFFFF、\UFFFFFFFF和\xFF格式字符。
        * PHP的字符串其实是单引号，双引号的话，可以解析其中的变量
        * 多个字符串连接用“+”号，与java(javascript)类似，PHP中用“.”
    * php的str_rot13，在string中没有，不过string.Map的例子就是rot13，可以借鉴
    * printf/sprintf等，可以参考 fmt中的相应 函数，函数名一致
        * Go 没有vsprintf。这是PHP特有的偷懒函数
    
* 参考：[neatstudio.com](http://neatstudio.com)    

        
    
    
