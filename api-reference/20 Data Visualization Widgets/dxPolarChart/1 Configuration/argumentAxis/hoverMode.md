---
default: 'none'
acceptValues: 'allArgumentPoints' | 'none'
type: String
---
---
##### shortDescription
Specifies the elements that will be highlighted when the argument axis is hovered over.

---
The following values are accepted:

* **none**    
Nothing happens when the argument axis is hovered over.
* **allArgumentPoints**    
The points that correspond to the argument that is currently hovered over are highlighted. To change the way the points are highlighted, set the options within the **series**.**point**.[hoverStyle](/api-reference/20%20Data%20Visualization%20Widgets/dxPolarChart/5%20Series%20Types/CommonPolarChartSeries/point/hoverStyle '/Documentation/ApiReference/Data_Visualization_Widgets/dxPolarChart/Configuration/series/point/hoverStyle/') object.

When using the widget as an [ASP.NET MVC Control](/concepts/35%20ASP.NET%20MVC%20Controls/20%20Fundamentals '/Documentation/Guide/ASP.NET_MVC_Controls/Fundamentals/'), specify this option using the `ArgumentAxisHoverMode` enum. This enum accepts the following values: `AllArgumentPoints` and `None`.