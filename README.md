hello flink
http://wuchong.me/blog/2018/11/07/5-minutes-build-first-flink-application/

当我们说“统计过去一小时内点击量”，这里的“一小时”是指什么呢？ 在 Flink 中它可以是指 ProcessingTime ，也可以是 EventTime，由用户决定。
ProcessingTime：事件被处理的时间。也就是由机器的系统时间来决定。
EventTime：事件发生的时间。一般就是数据本身携带的时间。
在本案例中，我们需要统计业务时间上的每小时的点击量，所以要基于 EventTime 来处理。那么如果让 Flink 按照我们想要的业务时间来处理呢？这里主要有两件事情要做。
第一件是告诉 Flink 我们现在按照 EventTime 模式进行处理，Flink 默认使用 ProcessingTime 处理，所以我们要显式设置下。
env.setStreamTimeCharacteristic(TimeCharacteristic.EventTime);


