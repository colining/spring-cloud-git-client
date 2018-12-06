# git client
* 在client中只需要进行配置就可以直接从server上获取config，但是client并不可以自动刷新
* 通过引入refresh包，可以开发一个接口，访问时，即刷新页面
* 通过webhook，可以使每次push时，触发refresh接口，从而更新
* 在所需要config的客户端中，添加bus-amqp包，可以使得当bus收到更新消息时，及通知所有在消息总线下
的client，因此我们可以做到主动refresh某一个client，从而更新所有client，但并不优雅，因此实际上
我们会将server也拉进消息总线上，这样server被refresh时，所有client即被refresh
