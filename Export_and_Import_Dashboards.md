# Export and Import Dashboards

Performance Analyzer Dashboards are easily exported and imported

## Exporting a dashboard

Dashboards export in the JSON format, and contain everything you need
(layout, variables, styles, data sources, queries, etc) to import the
dashboard at a later time.

1.  The export feature is accessed from the share menu. Click
    **Export**.  
    ![](attachments/85229574/85852161.png?height=250)
2.  Click the **Save to File** button or **View JSON** button.  
    ![](attachments/85229574/85262363.png?height=250)
3.  Save to your desired location.

### Making a dashboard portable

If you want to export a dashboard for others to use then it could be a
good idea to add template variables for things like a metric prefix (use
constant variable) and server name.

A template variable of the type `Constant` will automatically be hidden
in the dashboard, and will also be added as an required input when the
dashboard is imported.

## Importing a dashboard

To import a dashboard,

1.  Click the current dashboard view in the top menu.  
    ![](attachments/85229574/85917697.png?height=400)
2.  Click the **Import** button. The **Import Dashboard** dialog
    opens.  
    ![](attachments/85229574/85950468.png?height=400)
3.  You can:
    1.  Upload a JSON file by clicking the **Upload .json File** button.
    2.  Provide a Grafana.net dashboard url or id.
    3.  Paste the JSON text into the text box and click **Load**.

