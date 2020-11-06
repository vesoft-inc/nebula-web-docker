# 查询图数据

导入数据后，您可以开始使用 **控制台** 或者 **图探索** 查询图数据。

以查询代表“History of Chinese Women Through Time”课程的点的属性为例：

* 在 **控制台** 页面：运行 `FETCH PROP ON * hash("History of Chinese Women Through Time");`，数据库会返回这个点所有属性信息。返回结果后，点击 **导入图探索** 按钮，将点数据查询结果导入 **图探索** 进行可视化显示。  
![将控制台上查询得到的点数据信息导入到图探索进行可视化](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-012.png "将点数据查询结果导入图探索")

* 在 **图探索** 页面：点击 **开始探索** 按钮，在 **指定VID** 对话框中，输入 **"History of Chinese Women Through Time"**，在 **VID预处理** 选择 **Hash**，再点击 **添加** 按钮。**图探索** 画板里会显示这个点，将鼠标移到点上，您能看到这个点所有属性信息，如下图所示。  
![可视化显示 History of Chinese Women Through Time 课程的信息](https://docs-cdn.nebula-graph.com.cn/nebula-studio-docs/st-ug-013.png "按 VID 查询得到点的信息")
