#QT/QT5 #QT/QT控件 #QT/QChart #QT/QPieSlice/QPieSeries #QT/QChartView
# 如何在Qt5中实现一个饼状表格图控件

```c++
//![1]
    QPieSeries *series = new QPieSeries();
    series->append("Jane", 1);
    series->append("Joe", 2);
    series->append("Andy", 3);
    series->append("Barbara", 4);
    series->append("Axel", 5);
//![1]

//![2]
    QPieSlice *slice = series->slices().at(1);
    slice->setExploded();
    slice->setLabelVisible();
    slice->setPen(QPen(Qt::darkGreen, 2));
    slice->setBrush(Qt::green);
//![2]

//![3]
    QChart *chart = new QChart();
    chart->addSeries(series);
    chart->setTitle("Simple piechart example");
    chart->legend()->hide();
//![3]

//![4]
    QChartView *chartView = new QChartView(chart);
    chartView->setRenderHint(QPainter::Antialiasing);
//![4]
```
## 涉及到的qt类
1. QChart：qt表格数据类，用来存放表格中的数据
2. QpieSlice：饼状图中每一个元素所代表的扇形类
3. QPieSeries：整个图中所有扇形元素的集合
4. QChartView：qt表格图形控件


如何理解*QPieSeries->append("Jane", 1)* 这个方法中的**参数2** ？
> 当调用*append*方法为*QPieSeries*添加多个元素时，最终呈现出的效果，其中每个元素的比例是根据*append*方法传入的参数2来决定彼此的比例的。qt会计算各个对应传入的值的比例来为对应元素定下图内的比例。
> 比如，上面代码中，传入了5个元素，各自的值为1，2，3，4，5。则最终它们所占比为10%，20%，30%，40%，50%
> 注意：传入值并无具体要求，原则上说，只要是大于0的浮点数都可以，并且这个值可以通过*setValue*来随时改变