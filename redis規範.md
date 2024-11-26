# Redis 規範

    
> ## DON'T
> 1. 不使用Keys
>

>      Keys 指令效率極低，屬於O(N)操作，會阻塞其他正常指令，在cluster 上，會是災難性的操作。生產環境嚴禁使用
> 2. 不使用Flush

>       flush 指令會清空所有數據，屬於高風險操作。嚴禁在生產環境使用
>      
> 3. 不將圖片檔放到Redis

>      不將超過50KB的單筆紀錄放到redis

> ## Key 命名
> 
> - 格式
> 1.   以 **":"** 區隔
> 2.   {系統scope}:{專案名}:{業務}:
> 3.   方便管理，用GUI介面查閱也方便
> 
> - 舉例:

>     mgt:tppoint:point:123
>     
>     {台北通後台}:{台北通健康點}:{點數}:{自定義}
>
>


> This is the first level of quoting.
>
> > This is nested blockquote.
>
> Back to the first level.

