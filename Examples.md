#Charting examples

## Simple chart ##
![http://chart.apis.google.com/chart?chd=t%3A5%2C4%2C6&cht=p3&chs=300x150&chtt=Servings&chf=bg%2Cs%2CFFFFFF.png](http://chart.apis.google.com/chart?chd=t%3A5%2C4%2C6&cht=p3&chs=300x150&chtt=Servings&chf=bg%2Cs%2CFFFFFF.png)

```
  $chart = array(
      '#chart_id' => 'test_chart',
      '#title' => t('Servings'),
      '#type' => CHART_TYPE_PIE_3D,
    );
    
  $chart['#data']['fruits'] = 3;
  $chart['#data']['meats']  = 2;
  $chart['#data']['dairy']  = 5;

  echo chart_render($chart);
```



## Labels, title styling, and chart size ##
![http://chart.apis.google.com/chart?chd=t%3A3%2C2%2C5&cht=p&chs=400x200&chtt=Servings&chts=cc0000%2C15&chl=Fruits%7CMeats%7CDairy&chf=bg%2Cs%2CFFFFFF.png](http://chart.apis.google.com/chart?chd=t%3A3%2C2%2C5&cht=p&chs=400x200&chtt=Servings&chts=cc0000%2C15&chl=Fruits%7CMeats%7CDairy&chf=bg%2Cs%2CFFFFFF.png)

```
  $chart = array(
      '#chart_id' => 'test_chart',
      '#title' => chart_title(t('Servings'), 'cc0000', 15),
      '#type' => CHART_TYPE_PIE,
      '#size' => chart_size(400, 200),
    );
    
  $chart['#data']['fruits'] = 3;
  $chart['#data']['meats']  = 2;
  $chart['#data']['dairy']  = 5;

  $chart['#labels'][] = t('Fruits');
  $chart['#labels'][] = t('Meats');
  $chart['#labels'][] = t('Dairy');

  echo chart_render($chart);
```



## Custom data colors ##
Alternatively use the the [Color Schemes Hook](http://code.google.com/p/drupal-chart-api/wiki/Hooks) which can be then associated to multiple charts containing some or all of the same content. You may want to consider chart\_unique\_color();

![http://chart.apis.google.com/chart?chd=t%3A3%2C2%2C5&cht=p&chs=400x200&chtt=Servings&chts=cc0000%2C15&chl=Fruits%7CMeats%7CDairy&chco=00ff00%2Cff0000%2C0000ff&chf=bg%2Cs%2CFFFFFF.png](http://chart.apis.google.com/chart?chd=t%3A3%2C2%2C5&cht=p&chs=400x200&chtt=Servings&chts=cc0000%2C15&chl=Fruits%7CMeats%7CDairy&chco=00ff00%2Cff0000%2C0000ff&chf=bg%2Cs%2CFFFFFF.png)

```
  $chart = array(
      '#chart_id' => 'test_chart',
      '#title' => chart_title(t('Servings'), 'cc0000', 15),
      '#type' => CHART_TYPE_PIE,
      '#size' => chart_size(400, 200),
    );
    
  $chart['#data']['fruits'] = 3;
  $chart['#data']['meats']  = 2;
  $chart['#data']['dairy']  = 5;

  $chart['#labels'][] = t('Fruits');
  $chart['#labels'][] = t('Meats');
  $chart['#labels'][] = t('Dairy');
  
  $chart['#data_colors'][] = '00ff00';
  $chart['#data_colors'][] = 'ff0000';
  $chart['#data_colors'][] = '0000ff';

  echo chart_render($chart);
```

## Line chart, legends, resolution adjustment, and label positioning ##

As you can see in the chart below, the resolution of the encoding type chosen does not reflect well with the data provided. So in the chart below it, we set "'#adjust\_resolution' => TRUE,".

![http://chart.apis.google.com/chart?chd=t%3A1%2C3%2C5%2C4%2C2%7C2%2C2%2C4%2C3%2C1%7C5%2C2%2C3%2C1%2C2&cht=lc&chs=400x200&chtt=Servings&chts=cc0000%2C15&chdl=Fruits%7CMeats%7CDairy&chco=00ff00%2Cff0000%2C0000ff&chf=bg%2Cs%2C&chxr=0%2C0%2C5&chxl=1%3A%7CCount%7C2%3A%7CMon%7CTue%7CWed%7CThu%7CFri%7C3%3A%7CDays+of+the+week&chxt=y%2Cy%2Cx%2Cx&chxp=1%2C95%7C3%2C50.png](http://chart.apis.google.com/chart?chd=t%3A1%2C3%2C5%2C4%2C2%7C2%2C2%2C4%2C3%2C1%7C5%2C2%2C3%2C1%2C2&cht=lc&chs=400x200&chtt=Servings&chts=cc0000%2C15&chdl=Fruits%7CMeats%7CDairy&chco=00ff00%2Cff0000%2C0000ff&chf=bg%2Cs%2C&chxr=0%2C0%2C5&chxl=1%3A%7CCount%7C2%3A%7CMon%7CTue%7CWed%7CThu%7CFri%7C3%3A%7CDays+of+the+week&chxt=y%2Cy%2Cx%2Cx&chxp=1%2C95%7C3%2C50.png)

![http://chart.apis.google.com/chart?chd=t%3A20%2C60%2C100%2C80%2C40%7C40%2C40%2C80%2C60%2C20%7C100%2C40%2C60%2C20%2C40&cht=lc&chs=400x200&chtt=Servings&chts=cc0000%2C15&chdl=Fruits%7CMeats%7CDairy&chco=00ff00%2Cff0000%2C0000ff&chf=bg%2Cs%2C&chxr=0%2C0%2C5&chxl=1%3A%7CCount%7C2%3A%7CMon%7CTue%7CWed%7CThu%7CFri%7C3%3A%7CDays+of+the+week&chxp=1%2C95%7C3%2C50&chxt=y%2Cy%2Cx%2Cx&chxs=2%2C0000ff%2C12%2C0.png](http://chart.apis.google.com/chart?chd=t%3A20%2C60%2C100%2C80%2C40%7C40%2C40%2C80%2C60%2C20%7C100%2C40%2C60%2C20%2C40&cht=lc&chs=400x200&chtt=Servings&chts=cc0000%2C15&chdl=Fruits%7CMeats%7CDairy&chco=00ff00%2Cff0000%2C0000ff&chf=bg%2Cs%2C&chxr=0%2C0%2C5&chxl=1%3A%7CCount%7C2%3A%7CMon%7CTue%7CWed%7CThu%7CFri%7C3%3A%7CDays+of+the+week&chxp=1%2C95%7C3%2C50&chxt=y%2Cy%2Cx%2Cx&chxs=2%2C0000ff%2C12%2C0.png)

```
 $chart = array(
      '#chart_id' => 'test_chart',
      '#title' => chart_title(t('Servings'), 'cc0000', 15),
      '#type' => CHART_TYPE_LINE,
      '#size' => chart_size(400, 200),
      '#adjust_resolution' => TRUE,
    );
    
  $chart['#data']['fruits'] = array(1, 3, 5, 4, 2);
  $chart['#data']['meats']  = array(2, 2, 4, 3, 1);
  $chart['#data']['dairy']  = array(5, 2, 3, 1, 2);

  $chart['#legends'][] = t('Fruits');
  $chart['#legends'][] = t('Meats');
  $chart['#legends'][] = t('Dairy');

  $chart['#data_colors'][] = '00ff00';
  $chart['#data_colors'][] = 'ff0000';
  $chart['#data_colors'][] = '0000ff';

  $chart['#mixed_axis_labels'][CHART_AXIS_Y_LEFT][0][] = chart_mixed_axis_range_label(0, 5);
  $chart['#mixed_axis_labels'][CHART_AXIS_Y_LEFT][1][] = chart_mixed_axis_label(t('Count'), 95);
  
  $chart['#mixed_axis_labels'][CHART_AXIS_X_BOTTOM][1][] = chart_mixed_axis_label(t('Mon'));
  $chart['#mixed_axis_labels'][CHART_AXIS_X_BOTTOM][1][] = chart_mixed_axis_label(t('Tue'));
  $chart['#mixed_axis_labels'][CHART_AXIS_X_BOTTOM][1][] = chart_mixed_axis_label(t('Wed'));
  $chart['#mixed_axis_labels'][CHART_AXIS_X_BOTTOM][1][] = chart_mixed_axis_label(t('Thu'));  
  $chart['#mixed_axis_labels'][CHART_AXIS_X_BOTTOM][1][] = chart_mixed_axis_label(t('Fri'));
  $chart['#mixed_axis_labels'][CHART_AXIS_X_BOTTOM][2][] = chart_mixed_axis_label(t('Days of the week'), 50);

  echo chart_render($chart);
```

## Grid lines and chart fill ##

![http://chart.apis.google.com/chart?chd=t%3A-1%2C2%2C4%2C5%2C5%2C10%2C9%2C9%2C12%2C12%2C20%2C20%2C17%2C16%2C17%2C18%2C30%2C27%2C36%2C26%2C22%2C37%2C28%2C35%2C24%2C47%2C47%2C35%2C56%2C37%2C46%2C61%2C58%2C33%2C38%2C44%2C66%2C56%2C64%2C53%2C76%2C73%2C74%2C43%2C60%2C56%2C67%2C67%2C52%2C95%2C69%2C68%2C72%2C66%2C89%2C107%2C62%2C67%2C105%2C116%2C96%2C74%2C123%2C102%2C110%2C85%2C115%2C110%2C122%2C134%2C84%2C87%2C120%2C77%2C145%2C84%2C128%2C88%2C84%2C121&cht=lc&chs=400x200&chtt=Servings&chts=cc0000%2C15&chg=20%2C20%2C1%2C5&chf=c%2Cs%2Ceeeeee.png](http://chart.apis.google.com/chart?chd=t%3A-1%2C2%2C4%2C5%2C5%2C10%2C9%2C9%2C12%2C12%2C20%2C20%2C17%2C16%2C17%2C18%2C30%2C27%2C36%2C26%2C22%2C37%2C28%2C35%2C24%2C47%2C47%2C35%2C56%2C37%2C46%2C61%2C58%2C33%2C38%2C44%2C66%2C56%2C64%2C53%2C76%2C73%2C74%2C43%2C60%2C56%2C67%2C67%2C52%2C95%2C69%2C68%2C72%2C66%2C89%2C107%2C62%2C67%2C105%2C116%2C96%2C74%2C123%2C102%2C110%2C85%2C115%2C110%2C122%2C134%2C84%2C87%2C120%2C77%2C145%2C84%2C128%2C88%2C84%2C121&cht=lc&chs=400x200&chtt=Servings&chts=cc0000%2C15&chg=20%2C20%2C1%2C5&chf=c%2Cs%2Ceeeeee.png)

```
  $chart = array(
      '#chart_id' => 'test_chart',
      '#title' => chart_title(t('Servings'), 'cc0000', 15),
      '#type' => CHART_TYPE_LINE,
      '#size' => chart_size(400, 200),
      '#chart_fill' => chart_fill('c', 'eeeeee'),          
      '#grid_lines' => chart_grid_lines(20, 20, 1, 5),          
    );
    
  for ($i = 0; $i < 80; $i++){
    $chart['#data'][] = $i + rand(0, $i);
  }

  echo chart_render($chart);
```

## Bar sizing & color mapping ##
Spacing and sizing of bars can be adjusted using the #bar\_size attribute. Colors are mapped to content id's with chart\_unique\_color(id), no matter how many charts on the page use test\_a, test\_b, or test\_c, they will always have the same corrosponding color.

![http://chart.apis.google.com/chart?chd=t%3A40%2C50%2C70%7C60%2C50%2C30%7C40%2C60%2C20&cht=bvg&chs=400x200&chtt=Bar+Chart&chts=0000ee%2C15&chg=30%2C15%2C1%2C3&chco=FFE500%2CFFF9BF%2C78c0e9&chf=bg%2Cs%2CFFFFFF&chbh=15%2C5.png](http://chart.apis.google.com/chart?chd=t%3A40%2C50%2C70%7C60%2C50%2C30%7C40%2C60%2C20&cht=bvg&chs=400x200&chtt=Bar+Chart&chts=0000ee%2C15&chg=30%2C15%2C1%2C3&chco=FFE500%2CFFF9BF%2C78c0e9&chf=bg%2Cs%2CFFFFFF&chbh=15%2C5.png)

```
  $chart = array(
      '#chart_id' => 'test_chart',
      '#title' => chart_title(t('Bar Chart'), '0000ee', 15),
      '#type' => CHART_TYPE_BAR_V_GROUPED,
      '#size' => chart_size(400, 200),
      '#grid_lines' => chart_grid_lines(30, 15),
      '#bar_size' => chart_bar_size(15, 5), 
    );
    
  $chart['#data'][] = array(40, 50, 70);
  $chart['#data'][] = array(60, 50, 30);
  $chart['#data'][] = array(40, 60, 20);
  
  $chart['#data_colors'][] = chart_unique_color('test_a');
  $chart['#data_colors'][] = chart_unique_color('test_b');
  $chart['#data_colors'][] = chart_unique_color('test_c');

  echo chart_render($chart);
```