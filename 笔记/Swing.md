GUI工具包——swing
1. GUI 设计步骤：
  * 创建组件
  * 指定布局
  * 响应事件
2. swing 组件分类:
  * 框架类JFrame：顶层容器
  * 面板类JPanel：没有标题栏、没有边框的中间层容器
  * 组件类：又称控件，控件类对象里不能再包含其他组件
    * 颜色类Color：java.awt
    * 字体类Font：java.awt
    * 图标类ImageIcon：大小固定的图像,javax.swing.ImageIcon
    * 标签 JLabel
    * 命令按钮 JButton
    * 复选框 JCheckBox
    * 单选按钮 JRadioButton
    * 单行文本编辑组件 JTextField
    * 密码文本组件 JpasswordField
    * 多行文本组件 JTextArea
    * 滚动窗格 JScrollPane
    * 选项卡窗格 JTabbedPane
3. 布局管理器：
  * 流式布局管理器 FlowLayout（是JPanel默认的布局管理方式）
    * 组件按照加入容器的先后顺序从左向右排列
    * 一行排满后自动转到下一行继续从左向右排列
    * 每一行中的组件默认设置为居中排列
  * 边界式布局管理器 BorderLayout （是 JFrame、JAapplet 和对话框组件 JDialog 默认使用的布局管理器）
    * 将显示区域按地理位置分为东、西、南、北、中5个区域。
    * 若未指定区域，则默认为中间，若将组件加入到已被其他组件占用的区域，将会取代原先的组件。
    * 若某区域未分配组件，则其他组件可以占据他的空间 。
    * 利用 add 方法向容器中添加组件时必须指出组件摆放区域。
  * 网格式布局管理器 GridLayout
    * 其构造方法中若表示行的参数rows为0，则表示可以是任意数目的行，若表示列的参数cols为0，则表示可以是2任意数目的列，但行数和列数不能同时为0。
  * 卡片式布局管理器 CardLayout
    * 把容器中所有组件堆叠起来，每次只显示最上面的一张，被显示的组件将占据容器的全部空间。
  * 网格包布局管理器 GridBagLayout
    * 与 GridLayout 类似，但更灵活，允许组件占用不同行或列的多个单元格。
    * 网格行数和列数不能在构造方法中指定，由添加到网格包布局策略的容器中的组件动态决定。
    * 网格包约束条件： GridBagConstraints 类对象，创建此对象后，就可以通过该对象的一些成员变量来设置网络包约束条件的具体数值。
  * 盒式布局管理器 BoxLayout （在一行或一列中摆放组件）
    * 沿水平方向排列组件时，当组件总宽度超出容器宽度时，组件不会换行（沿列排列相同），这时需要改变容器大小才能看见所有组件。
    * 该布局构造方法只有一种：'public BoxLayout(Contatiner target,int axis)'   参数：使用该布局的容器，组件排列方式。
  * 重叠布局管理器 OverLayout
    * 具有该布局策略的容器将加入该容器的所有组件叠放在一起，第一个被加入容器的组件会放在容器的最前面，后加入的会被覆盖，前面组件可使用 **JComponent.setOpaque(false)** 方法将其设置为透明的。
  * 弹簧布局管理器 SpringLayout
    * 在组件周围放置一个灵活的弹簧，这种弹簧可以压缩或伸长，把组件堆放到要求的位置。

[相关代码练习](file:///E:/JAVA workspace/Gui/src)
