---
id: dxChart.Options.argumentAxis.argumentType
acceptValues: 'datetime' | 'numeric' | 'string'
type: String
default: undefined
---
---
##### shortDescription
Casts arguments to a specified data type.

---
If your data source stores, for example, numbers as strings, specify the proper data type using the **argumentType** option.

#include common-ref-enum with {
    enum: "`ChartDataType`",
    values: "`Numeric`, `DateTime`, and `String`"
}

#####See Also#####
- **valueAxis**.[valueType](/api-reference/20%20Data%20Visualization%20Widgets/dxChart/1%20Configuration/valueAxis/valueType.md '/Documentation/ApiReference/Data_Visualization_Widgets/dxChart/Configuration/valueAxis/#valueType') - casts values to a specified data type.
- **argumentAxis**.[type](/api-reference/20%20Data%20Visualization%20Widgets/dxChart/1%20Configuration/argumentAxis/type.md '/Documentation/ApiReference/Data_Visualization_Widgets/dxChart/Configuration/argumentAxis/#type') - specifies the axis type.
- **dataPrepareSettings**.[checkTypeForAllData](/api-reference/20%20Data%20Visualization%20Widgets/dxChart/1%20Configuration/dataPrepareSettings/checkTypeForAllData.md '/Documentation/ApiReference/Data_Visualization_Widgets/dxChart/Configuration/dataPrepareSettings/#checkTypeForAllData') - validates the type of each value coming from the data source.
- **dataPrepareSettings**.[convertToAxisDataType](/api-reference/20%20Data%20Visualization%20Widgets/dxChart/1%20Configuration/dataPrepareSettings/convertToAxisDataType.md '/Documentation/ApiReference/Data_Visualization_Widgets/dxChart/Configuration/dataPrepareSettings/#convertToAxisDataType') - allows you to disable the type cast in favour of the widget performance.