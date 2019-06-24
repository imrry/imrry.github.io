### 容器
容器是可以放置元素（文本，列表，表格等）的对象。有3个主要容器，即部分，页眉和页脚。有3个元素也可以作为容器，即Section、表格和脚注。

#### 节（Section）
* 单词中的每个可见元素都放在一个节内。要创建节，请使用以下代码：
```
$section = $phpWord->addSection($sectionStyle);
```

* 这`$sectionStyle`是一个可选的关联数组，用于设置内容样式。例：
```
$sectionStyle = [
    'orientation' => 'landscape',
    'marginTop' => 600,
    'colsNum' => 2,
];
```

#### 页码

* 您可以使用`pageNumberingStart`该部分的样式更改部分页码。
```
// 第一种方式
$section = $phpWord->addSection(['pageNumberingStart' => 1]);
// 第二种方式
$section = $phpWord->addSection();
$section->getStyle()->setPageNumberingStart(1);
```

#### 多列

* 您可以使用部分的样式`breakType`和`colsNum`样式将部分布局更改为多列（例如在报纸中）。
```
// 第一种方式
$section = $phpWord->addSection(array('breakType' => 'continuous', 'colsNum' => 2));
// 第二种方式
$section = $phpWord->addSection();
$section->getStyle()->setBreakType('continuous');
$section->getStyle()->setColsNum(2);
```

#### 行号

* 您可以使用该部分的`lineNumbering`样式将行编号应用于部分。
```
// 第一种方式
$section = $phpWord->addSection(array('lineNumbering' => array()));
// 第二种方式
$section = $phpWord->addSection();
$section->getStyle()->setLineNumbering(array());
```
* 以下是行编号样式的属性
  * `start` 行号起始值
  * `increment` 行号增量
  * `distance` 文本和行号之间的距离以缇为单位
  * `restart` 行编号重启设置连续| newPage | newSection

#### 页眉

* 每个部分都可以有自己的标题引用。要创建标头，请使用以下addHeader方法：
```
$header = $section->addHeader();
```
务必将结果保存在本地对象中。您可以使用页脚可用的所有元素。有关详细信息，请参阅“页脚”部分。此外，只有标题参考内部您可以添加水印或背景图片。请参阅“水印”部分。
您可以传递一个可选参数来指定应该应用页眉/页脚的位置，它可以是：
  * `Footer::AUTO` 默认情况下，所有页面除非被第一个或偶数覆盖。
  * `Footer::FIRST` 该部分的每个第一页。
  * `Footer::EVEN`该部分的每个偶数页面。只有在`phpWord->settings`中将`evenAndOddHeaders`设置为`true`时才会应用。

* 要更改`evenAndOddHeaders`，请使用该`getSettings`方法返回`Settings`对象，然后调用`setEvenAndOddHeaders`方法：

#### 页脚

* 每个部分都有自己的页脚引用。要创建页脚，请使用以下`addFooter`方法：
```
$footer = $section->addFooter();
```
* 确保将结果保存在本地对象中以向页脚添加元素。您可以将以下元素添加到页脚：
  * 文本 `addText` 和 `createTextrun`。
  * 文字中断
  * 图片
  * 表格
  * 页码文本
* 有关每个元素的详细信息，请参阅“元素”部分。

#### 其他容器
Textrns，表格单元格和脚注是也可以充当容器的元素。有关每个元素的详细信息，请参见相应的“元素”部分。
