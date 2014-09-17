## testJTopo ##

**JTopo** 示例, [JTopo官网: http://www.jtopo.com/](http://www.jtopo.com/)

本示例参照[JTopo](http://www.jtopo.com/demo/helloworld.html)官方示例。

本Project是使用 [Aptana Studio 3](http://www.aptana.com/products/studio3/) 创建的。

----------

由于JTopo官网尚在逐步完善，有很多API的使用还没有被整理出来，以下的API的用法是通过JTopo Demo中的代码整理出来的。

- **JTopo.Node (普通Node)**
	
	    node.setImage('./img/OS_Apple.png', true); //设置Node背景图片
    	node.borderRadius = 5; // 圆角Node


- **JTopo.CircleNode (圆角Node)**

		circleNode.fillColor = '0, 0, 0';//填充色
		circleNode.radius = 24; // 半径
		circleNode.alpha = 0.7; // 透明度


- **JTopo.TextNode (文本Node)**

		textNode.font = 'bold 16px 微软雅黑';//设置文本节点的字体


- **JTopo.LinkNode （超链接Node）**

        var linkNode = new JTopo.LinkNode('超链接：http://www.jtopo.com');
        linkNode.href = 'http://www.jtopo.com';
        linkNode.target = '_blank'; // 新窗口打开链接
        linkNode.font = 'italic bold 16px 微软雅黑';
        linkNode.visitedColor = '0,0,255'; // 访问过的链接为蓝色
        linkNode.shadowOffsetX = 5; // 阴影设置
        linkNode.shadowOffsetY = 16;


- **JTopo.Link （普通线段）**

        link.lineWidth = 3; // 线宽
        link.dashedPattern = 5; // 虚线 int值
        link.bundleOffset = 60; // 折线拐角处的长度
        link.bundleGap = 20; // 线条之间的间隔
        link.textOffsetY = 3; // 文本偏移量（向下3个像素）
        link.strokeColor = '0,200,255'; //连线的颜色

		
		var loop = newLink(from, from, 'loop');// Link的起始点和结束点相同，就画成一个圆


- **JTopo.FoldLink (折线)**

        link.direction = 'vertical'|| 'horizontal';
        link.arrowsRadius = 15; //箭头大小
        link.lineWidth = 3; // 线宽
        link.dashedPattern = 3; // 虚线 int值
        link.bundleOffset = 60; // 折线拐角处的长度
        link.bundleGap = 20; // 线条之间的间隔
        link.textOffsetY = 3; // 文本偏移量（向下3个像素）
        link.strokeColor = JTopo.util.randomColor(); // 线条颜色随机


- **JTopo.FlexionalLink (二次折线)**

	(属性同普通Link和FoldLink基本一样)


- **JTopo.CurveLink (曲线)**

	(属性同普通Link和FoldLink基本一样)


- **鹰眼**

        stage.wheelZoom = 0.85; // 设置鼠标缩放比例
        stage.eagleEye.visible = true; // 鹰眼


- **JTopo.Container (容器)**

		// 不指定布局的时候，容器的布局为自动(容器边界随元素变化）
        container.textPosition = 'Middle_Center';// 字体位置
        container.fontColor = '100,255,0';
        container.font = '18pt 微软雅黑';
        container.borderColor = '255,0,0';
        scene.add(container);


- **JTopo.layout.FlowLayout (流式布局)**
           
		var flowLayout = JTopo.layout.FlowLayout(10, 10); //（水平、垂直间隔均为10)


+ **JTopo.layout.GridLayout (网格布局)**

		var gridLayout = JTopo.layout.GridLayout(4, 3);//(4行3列)


* **JTopo.layout.TreeLayout (树形布局)**

		JTopo.layout.TreeLayout('down', 30, 107);


- **拓扑图形**

        // 圆形布局
        var cloudNode = new JTopo.Node('root');
        cloudNode.layout = {type: 'circle', radius: 150};

        // 树形布局
        var cloudNode = new JTopo.Node('root');
        cloudNode.layout = {type: 'tree', width:50, height: 100};
        
		// 树形布局（全自动）
        scene.doLayout(JTopo.layout.TreeLayout('down', 30, 107));// 树形布局


- **统计图表 -- 饼图**

        // 饼图
        var node = new JTopo.PieChartNode();
        node.radius = 100;           
		node.colors = ["#3666B0","#2CA8E0","#77D1F6"];
        node.datas = [0.3, 0.3, 0.4];
        node.titles = ['A', 'B', 'C'];


- **统计图表 -- 柱状图**

		var node = new JTopo.BarChartNode();     
        node.colors = ["#3666B0","#2CA8E0","#77D1F6","#12DFE5"];
        node.datas = [130, 200, 120, 180];
        node.titles = ['2010', '2012', '2013', '2014'];


- **计算a点和b点的距离**

		JTopo.util.getDistance(a, b);// 计算a点和b点的距离


- **动画 -- 弹性（简单）**

        // 弹性效果（引力、摩擦系数)
        var effect = JTopo.Effect.spring({
        	grivity: 10, // 引力 (可以为负值)
     		spring: 0.4, // 弹性系数
     		friction: 0.3 // 摩擦系数
     	})

     	// 效果作用对象(node节点以targetNode为目标，产生弹性效果)
     	effect.addNode(node, targetNode);
     	effect.play();// 播放


- **序列化和反序列化**

		var json = '{"version":"0.4.0","frames":24,"wheelZoom":null ...}';
		var stage = JTopo.createStageFromJson(json, canvas);// 反序列化
     
		var jsonStr = stage.toJson();// 序列化


+ **场景切换**

		scene.visible = true / false;


- **gif模拟**

		// 1行4列，1000毫秒播放一轮，行偏移量           
		var sprite = new JTopo.AnimateNode('./img/caizhu.png', 1, 4, 1000, 1); // caizhu.png是个sprite图
		sprite.setSize(90, 88);
		sprite.setLocation(300, 250);
		sprite.repeatPlay = true;
		sprite.play(); 
