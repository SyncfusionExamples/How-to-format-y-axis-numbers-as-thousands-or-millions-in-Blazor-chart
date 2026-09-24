# Format Y-Axis Numbers as Thousands or Millions in Syncfusion Blazor Chart

## Overview

This sample demonstrates how to customize Y-axis label rendering in a Syncfusion [Blazor Charts](https://www.syncfusion.com/blazor-components/blazor-charts) component. The chart displays large numeric values and uses the `OnAxisLabelRender` event to intercept and modify axis labels before they are rendered. By converting raw values into abbreviated formats such as millions (`M`), the chart becomes easier to read and interpret, especially for financial, sales, and analytical datasets containing large numbers.

The implementation uses a column chart bound to a collection of date-based data points. During axis label rendering, the sample evaluates Y-axis labels and updates the displayed text dynamically, ensuring a clean and user-friendly presentation without changing the underlying data source.

## Key Features

- Uses the `SfChart` component to render chart data.
- Configures the X-axis using `ChartPrimaryXAxis`.
- Sets `ValueType.DateTime` for date-based horizontal axis rendering.
- Uses `IntervalType.Years` for yearly interval calculation.
- Displays data through a `ChartSeries` configured with `ChartSeriesType.Column`.
- Handles the `OnAxisLabelRender` event using the `LabelRender(AxisLabelRenderEventArgs args)` method.
- Accesses axis label information through `AxisLabelRenderEventArgs`.
- Identifies the primary Y-axis using `args.Axis.Name == "PrimaryYAxis"`.
- Converts rendered label text into numeric values using `Convert.ToDouble(args.Text)`.
- Updates `args.Text` with formatted values in millions by dividing the source value by `1000000` and appending the `"M"` suffix.

## Prerequisites

- [Visual Studio 2022](https://visualstudio.microsoft.com/vs/) or [Visual Studio Code](https://code.visualstudio.com/)
- [.NET SDK](https://dotnet.microsoft.com/en-us/download/dotnet) compatible with the project's target framework

## How to Run the Project

**Visual Studio 2022**

1. Clone or download the repository.
2. Open the project file located inside the `YaxisFormat` folder.
3. Restore NuGet packages when prompted.
4. Build the project.
5. Run the application using `Ctrl+F5`.

**Visual Studio Code**

1. Clone or download the repository.
2. Open the repository folder in Visual Studio Code.
3. Open the integrated terminal.
4. Navigate to the project directory.

```bash
cd YaxisFormat
dotnet restore
dotnet run
```

5. Open the local application URL displayed in the terminal after the application starts.

## Project Structure

`Pages/Index.razor` - Contains the `SfChart` component, chart configuration, sample data source, and the `LabelRender(AxisLabelRenderEventArgs args)` event handler used to format Y-axis labels into millions.

## Support and Feedback

- For general product questions, visit the [Syncfusion Community Forum](https://www.syncfusion.com/forums) or [Syncfusion Support](https://www.syncfusion.com/support).
- To report an issue specific to this sample, open a GitHub issue in this repository.
- Refer to the official Syncfusion chart documentation for axis label customization and rendering events: https://help.syncfusion.com/chart-sdk/blazor/charts/events

## License

This is a Syncfusion sample project provided to demonstrate product usage. Review the [Syncfusion license terms](https://www.syncfusion.com/sales/pricing?category=ui-components) before using Syncfusion components in your own applications.