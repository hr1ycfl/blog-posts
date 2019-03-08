---
title: 'Flutter Widget 目录'
href: '2019-03-08-flutter-widget-menu'
categories: Flutter
date: 2019-03-08 20:45:36
tags:
  - Flutter
keywords: App, IOS, Android, Flutter
---

### AbsorbPointer
在命中测试期间吸收指针的小部件。当吸收为真时，此小部件通过终止命中测试来阻止其子树接收指针事件。它仍然会在布局过程中消耗空间并像往常一样对孩子进行绘画。它只是阻止它的子节点成为定位事件的目标，因为它从RenderBox.hitTest返回true。

### AlertDialog
警报是紧急中断，需要确认通知用户情况。AlertDialog小部件实现此组件。

### Align
一个小部件，它将其子项与其自身对齐，并根据子级的大小自行调整大小。

### AnimatedBuilder
用于构建动画的通用小部件。AnimatedBuilder对于希望将动画作为更大构建函数的一部分包含在内的更复杂的小部件非常有用。要使用AnimatedBuilder，只需构造窗口小部件并将其传递给构建器函数。

### AnimatedContainer
在一段时间内逐渐更改其值的容器。

### AnimatedCrossFade
一个小部件，它在两个给定的子节点之间交叉淡化，并在它们的大小之间设置动画。

### AnimatedDefaultTextStyle
DefaultTextStyle的动画版本，无论何时给定的样式发生更改，都会在给定的持续时间内自动转换默认文本样式（文本样式以应用于没有显式样式的后代Text小部件）。

### AnimatedListState
滚动容器的状态，在插入或移除项目时为其设置动画。

### AnimatedModalBarrier
一个小部件，阻止用户与自身后面的小部件交互。

### AnimatedOpacity
不透明度的动画版本，只要给定的不透明度发生变化，就会自动转换孩子在给定持续时间内的不透明度。

### AnimatedPhysicalModel
PhysicalModel的动画版本。

### AnimatedPositioned
定位的动画版本，可在给定位置发生变化时自动转换孩子在给定持续时间内的位置。

### AnimatedSize
动画小部件，只要给定孩子的大小发生变化，就会在给定的持续时间内自动转换大小。

### AnimatedWidget
在给定的Listenable更改值时重建的窗口小部件。

### AnimatedWidgetBaseState
具有隐式动画的小部件的基类。

### Appbar
Material Design应用栏。应用栏由工具栏和可能的其他小部件组成，例如TabBar和FlexibleSpaceBar。

### ASPECTRATIO
尝试将子项调整为特定宽高比的小部件。

### AssetBundle
资产包包含可由应用程序使用的资源，例如图像和字符串。对这些资源的访问是异步的，因此可以通过网络（例如，从NetworkAssetBundle）或从本地文件系统透明地加载它们，而不会阻塞应用程序的用户界面。

### BackdropFilter
一个小部件，它将过滤器应用于现有的绘制内容，然后绘制子项。这种效果相对昂贵，特别是如果滤镜是非局部的，例如模糊。

### Baseline
A widget that positions its child according to the child's baseline.

### BottomNavigationBar
底部导航栏使您可以轻松浏览并在单击中切换顶级视图。BottomNavigationBar小部件实现此组件。

### BottomSheet
底部工作表从屏幕底部向上滑动以显示更多内容。您可以调用showBottomSheet（）来实现持久底部工作表或showModalBottomSheet（）来实现模式底部工作表。

### ButtonBar
一组水平排列的按钮

### Card
A Material Design card. A card has slightly rounded corners and a shadow.

### Center
A widget that centers its child within itself.

### Checkbox
Checkboxes allow the user to select multiple options from a set. The Checkbox widget implements this component.

### Chip
A Material Design chip. Chips represent complex entities in small blocks, such as a contact.

### CircularProgressIndicator
A material design circular progress indicator, which spins to indicate that the application is busy.

### ClipOval
A widget that clips its child using an oval.

### ClipPath
A widget that clips its child using a path.

### ClipRect
A widget that clips its child using a rectangle.

### Column
Layout a list of child widgets in the vertical direction.

### ConstrainedBox
A widget that imposes additional constraints on its child.

### Container
A convenience widget that combines common painting, positioning, and sizing widgets.

### CupertinoActionSheet
An iOS-style modal bottom action sheet to choose an option among many.

### CupertinoActivityIndicator
An iOS-style activity indicator. Displays a circular 'spinner'.

### CupertinoAlertDialog
An iOS-style alert dialog.

### CupertinoButton
An iOS-style button.

### CupertinoDatePicker
An iOS-style date or date and time picker.

### CupertinoDialog
An iOS-style dialog.

### CupertinoDialogAction
A button typically used in a CupertinoAlertDialog.

### CupertinoFullscreenDialogTransition
An iOS-style transition used for summoning fullscreen dialogs.

### CupertinoNavigationBar
An iOS-style top navigation bar. Typically used with CupertinoPageScaffold.

### CupertinoPageScaffold
Basic iOS style page layout structure. Positions a navigation bar and content on a background.
















