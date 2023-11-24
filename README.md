# How-to-format-y-axis-numbers-as-thousands-or-millions-in-Blazor-chart

This article explains how to format y-axis numbers into thousands or millions in Blazor chart.

**Formatting Y axis labels into Thousands or Millions:**

Blazor chart provides us support to format axis label using [OnAxisLabelRender ](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.ChartEvents.html#Syncfusion_Blazor_Charts_ChartEvents_OnAxisLabelRender)event. This event triggers before each axis label is rendered.

The following properties are available in the [AxisLabelRenderEventArgs](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.AxisLabelRenderEventArgs.html).

- [LabelStyle ](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.AxisLabelRenderEventArgs.html#Syncfusion_Blazor_Charts_AxisLabelRenderEventArgs_LabelStyle)- Specifies the font information of the axis label.
- [Text ](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.AxisLabelRenderEventArgs.html#Syncfusion_Blazor_Charts_AxisLabelRenderEventArgs_Text)- Specifies the text to be displayed in the axis label.
- [Value](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.AxisLabelRenderEventArgs.html#Syncfusion_Blazor_Charts_AxisLabelRenderEventArgs_Value) - Specifies the ﻿﻿value of the axis label.

The following code example, we can see how to format the y-axis label into millions using [OnAxisLabelRender](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.ChartEvents.html#Syncfusion_Blazor_Charts_ChartEvents_OnAxisLabelRender) event.

**C#**

```cshtml

@using Syncfusion.Blazor.Charts

<SfChart Title="Sales Comparison">

    <ChartPrimaryXAxis IntervalType="IntervalType.Years" ValueType="Syncfusion.Blazor.Charts.ValueType.DateTime" LabelPlacement="LabelPlacement.BetweenTicks"/>

    <ChartEvents OnAxisLabelRender="@LabelRender"></ChartEvents>

    <ChartSeriesCollection>
        <ChartSeries DataSource="@Data" XName="X" YName="Y" Type="ChartSeriesType.Column" />
    </ChartSeriesCollection>

</SfChart>

@code {

    public class ChartData
    {
        public DateTime X { get; set; }
        public double Y { get; set; }
    }

    public List<ChartData> Data = new List<ChartData>
    {
          new ChartData{ X = new DateTime(2005, 01, 01), Y= 7000000 },
          new ChartData{ X = new DateTime(2006, 01, 01), Y= 5000000 },
          new ChartData{ X = new DateTime(2007, 01, 01), Y= 3000000 },
          new ChartData{ X = new DateTime(2008, 01, 01), Y= 4000000 },
          new ChartData{ X = new DateTime(2009, 01, 01), Y= 8000000 },
          new ChartData{ X = new DateTime(2010, 01, 01), Y= 5000000 },
          new ChartData{ X = new DateTime(2011, 01, 01), Y= 7300000 },
          new ChartData{ X = new DateTime(2012, 01, 01), Y= 9000000 },           
    };

    public void LabelRender(AxisLabelRenderEventArgs args)
    {
        if(args.Axis.Name == "PrimaryYAxis")
        {
            double temp = Convert.ToDouble(args.Text);
            args.Text = (temp / 1000000).ToString() + "M";
        }

    }
}

```


The following image screenshot illustrate the output of the above code snippet.

**Output:**

![](/Y-axis-format-to-Millions.png)

**Conclusion**

I hope you enjoyed learning how to format y-axis label into thousands and millions in Blazor Chart Component.

You can refer to our [Blazor Chart feature tour](https://www.syncfusion.com/blazor-components/blazor-charts) page to know about its other groundbreaking feature representations and [documentation](https://blazor.syncfusion.com/documentation/chart/getting-started), and how to quickly get started for configuration specifications. You can also explore our [Blazor Chart example](https://blazor.syncfusion.com/demos/chart/line?theme=bootstrap5) to understand how to create and manipulate data.

For current customers, you can check out our components from the [License and Downloads](https://www.syncfusion.com/sales/teamlicense) page. If you are new to Syncfusion, you can try our 30-day [free trial](https://www.syncfusion.com/downloads/blazor) to check out our other controls.

If you have any queries or require clarifications, please let us know in the comments section below. You can also contact us through our [support forums](https://www.syncfusion.com/forums), [support portal](https://support.syncfusion.com/create), or [feedback portal](https://www.syncfusion.com/feedback/blazor-components?control=charts). We are always happy to assist you!
