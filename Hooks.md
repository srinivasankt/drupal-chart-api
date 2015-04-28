#hooks allowing module developers to extend Chart API.

  * ## chart\_alter ##
    * Modify exsisting charts before they are created.
    * Implementation example:
    * 
```
 function modulename_chart_alter($chart_id, &$chart) {
   if ($chart_id == 'node_counts'){
     $chart['#size'] = chartapi_size(300, 200);  
   }
 }
```

  * ## chart\_color\_schemes ##
    * Extend and alter color schemes.
    * Implementation example:
```
function system_charts_chart_color_schemes(&$colors) {
  $colors['watchdog_severity'] = array(
      '0000FF',
      'FFFF00',
      'FF0000',
    );   
}

function system_charts_chart_color_schemes(&$colors) {
  $colors['watchdog_severity'] = array(
      'Notice'  => '0000FF',
      'Warning' => 'FFFF00',
      'Error'   => 'FF0000',
    );   
}
```
    * Assoc arrays can be used to pre-map colors to a specific $content\_id
    * NOTE: do not use the pound sign (#) for hex color values.