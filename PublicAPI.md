#Public API functionality

## Hooks ##
Visit [Hooks](Hooks.md) to view hooks which are currently available to extend and modify exsisting chart functionality.

## Chart Generation ##

  * chart\_render($chart, $attributes = array());
    * Returns image tag of the rendered chart, or FALSE on failure.
  * chart\_copy($chart, $name = NULL, $dest = 'files', $replace = FILE\_EXISTS\_REPLACE)
    * Copies a chart as a local png image.
  * chart\_build($chart);
    * Generates a Google API query string which is used to request the chart image.

## Utility Functions ##
The following functions are available to help build and modify chart array structures.

  * chart\_title($title, $color = '000000', $size = 14);
  * chart\_size($width, $height);
  * chart\_bar\_size($size = 40, $spacing = 20);
  * chart\_data\_colors($colors);
  * chart\_line\_style($line\_thickness = 1, $segment\_length = 1, $blank\_segment\_length = 0);
  * chart\_grid\_lines($x\_step, $y\_step, $segment\_length = 1, $blank\_segment\_length = 1);
  * chart\_shape\_marker($index = 0, $point = 1, $type = 'o', $size = 20, $color = '000000');
  * chart\_range\_marker($start, $end, $virtical = TRUE, $color = '000000');
  * chart\_fill($type = 'c', $color = '000000');
  * chart\_linear\_gradient($type = 'c', $color = '000000', $offset = 0);
  * chart\_linear\_stripes($type = 'c', $color = '000000', $angle = 0, $width = 0.25);
  * chart\_unique\_color($content\_id, $scheme = 'default');
    * Creates and returns a unique color per $content\_id. Making it easy to distingish between dynamic data sets where you may not manually enter colors.
    * When color is associated to the $content\_id passed, for example array('Error' => 'ff0000') then that color will be assigned.
  * chart\_mixed\_axis\_label($label, $position = NULL);
  * chart\_mixed\_axis\_range\_label($start, $end);
  * chart\_mixed\_axis\_style($index, $color, $font\_size = 12, $alignment = CHART\_ALIGN\_CENTER);

## Chart API Structure ##
The following describes parameters which can be entered manually or used along with the helper functions above to create what is the Chart API array structure.

#### Required ####
  * #chart\_id
    * unique id representing the chart.
  * #type
    * chart type. see chart type constants below.
  * #data
    * array of nested arrays or numeric values. Empty values are represented with the string 'NULL'.

#### Optional ####
  * #title
    * chart title and style. see chart\_title();
  * #size
    * chart dimensions. see chart\_size();
  * #legends
    * array of legends describing each dataset.
  * #labels
    * array of labels describing dataset series.
  * #adjust\_resolution
    * when TRUE data is adjusted to the resolution available which ensures that data is represented using the full range of values available.
    * when an array is passed rather than a bool, #adjust represents that the data should be adjusted, and #max indicates what value should be considered the maximum value to which all other values will resolve to.
    * Example: values of [5, 8, 12] will not be represented well when the chart has a range of 100 values, 12 will be represented at 100 (unless a max is specified) and other values are adjust appropriately.
  * #line\_styles
    * array of line styles which parallel datasets being displayed. see chart\_line\_style();
  * #grid\_lines
    * see chart\_grid\_lines();
  * #shape\_markers
    * array of shape markers. see chart\_shape\_marker();
  * #data\_colors
    * array of hex color values which parallel datasets.
    * use of chart\_unique\_color() is recommended.
    * NOTE: values must exclude #
  * #chart\_fill
    * chart fill color and styling. see chart\_fill()
  * #mixed\_axis\_labels
    * array of mixed axis labels. see chart\_mixed\_axis\_range\_label() and chart\_mixed\_axis\_label()
  * #mixed\_axis\_label\_styles
    * see chart\_mixed\_axis\_label\_styles()
  * #bar\_size
    * see chart\_bar\_size()

## Constants ##

#### Chart Types ####
  * CHART\_TYPE\_LINE
  * CHART\_TYPE\_LINE\_XY
  * CHART\_TYPE\_BAR\_H
  * CHART\_TYPE\_BAR\_V
  * CHART\_TYPE\_BAR\_H\_GROUPED
  * CHART\_TYPE\_BAR\_V\_GROUPED
  * CHART\_TYPE\_PIE
  * CHART\_TYPE\_PIE\_3D
  * CHART\_TYPE\_VENN
  * CHART\_TYPE\_SCATTER

#### Marker Types ####
  * CHART\_MARKER\_ARROW
  * CHART\_MARKER\_CROSS
  * CHART\_MARKER\_DIAMOND
  * CHART\_MARKER\_CIRCLE
  * CHART\_MARKER\_SQUARE
  * CHART\_MARKER\_VIRTICAL\_LINE\_X
  * CHART\_MARKER\_VIRTICAL\_LINE\_TOP
  * CHART\_MARKER\_HORIZONTAL\_LINE
  * CHART\_MARKER\_X

#### Axis ####
  * CHART\_AXIS\_X\_BOTTOM
  * CHART\_AXIS\_X\_TOP
  * CHART\_AXIS\_Y\_LEFT
  * CHART\_AXIS\_Y\_RIGHT

#### Alignment ####
  * CHART\_ALIGN\_LEFT
  * CHART\_ALIGN\_CENTER
  * CHART\_ALIGN\_RIGHT