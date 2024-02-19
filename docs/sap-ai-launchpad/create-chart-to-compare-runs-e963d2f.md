<!-- loioe963d2fdf9d44280b94aca73aa43f4fb -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Create Chart to Compare Runs

You can create charts for runs to visually compare quality criteria and values.



<a name="loioe963d2fdf9d44280b94aca73aa43f4fb__context_env_mq2_ytb"/>

## Context

You can create multiple charts and view them in the *Chart View*.

> ### Note:  
> Each chart can include data for up to five runs.



## Procedure

1.  In the *Functions Explorer* app, choose *All Runs*.

2.  **Optional:** If you have a large list of runs, you can filter the list by choosing <span class="SAP-icons-V5"></span> \(Filter\). The *Filter* dialog appears.

    1.  Enter the run ID or select a status.

    2.  Choose *Apply* to apply the filter to the list.


3.  Select the runs for comparison and choose *View Metrics*.

    ![All Runs screen with four runs selected for metrics comparison.](images/Image_AIL_FE_All_All_Runs_Compare_Metrics_fbaf644.png)

    The *Metrics Overview* appears for the selected runs. The run IDs and descriptions are listed in the *My Selection* pane. The *Metrics Comparison* pane defaults to the chart view.

    ![Metrics comparison screen with selected runs in the My Selection pane and an empty chart view in the right pane.](images/Image_AIL_FE_All_Vis_Board_9ffa073.png)

4.  Choose *Add Chart* to create a chart based on your selected runs.

    The *Add Chart* dialog appears.

5.  Enter the chart settings:

    -   Enter a name and description for the chart.
    -   In *Chart Settings*, choose `Runs` as the metrics source.
    -   In *Comparison Type*, choose your preferred comparison. You can compare metrics to parameters, to the source, or to steps or time. Based on your selection, you'll be prompted to select the metrics and values for comparison.

6.  Choose *Preview* to continue to the preview settings.

    > ### Caution:  
    > If *Preview* is not enabled, review your settings and selections. Some settings are mandatory, and you can't proceed until specified. Some settings and data combinations don't correspond to a valid chart type.

7.  In the *Chart Selection* pane, select the chart type \(such as column or bar chart\). Note, the chart types available depend on the chart settings you defined.

8.  Choose *Data Selection* from the dropdown menu to confirm the runs selected for the chart.

    You can show or hide runs from the data selection, and see the impact on the preview chart.

9.  Choose *OK* to create the chart. The chart appears in your chart view.

10. **Optional:** Check the chart. Note, if you have multiple charts, you may need to scroll.

    1.  To display a chart in full-screen mode, choose <span class="SAP-icons-V5"></span> \(Open Full Screen\).

    2.  To edit a chart, choose :pencil2:.

    3.  To delete a chart from your chart view choose :pencil2:



