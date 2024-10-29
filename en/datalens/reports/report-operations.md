# Working with a report


{% include [business-note](../../_includes/datalens/datalens-functionality-available-business-note.md) %}


In this section, you will learn how to work with a report:

* [{#T}](#create-report)
* [{#T}](#report-pages)
* [{#T}](#report-widget-settings)
* [{#T}](#report-settings)
* [{#T}](#page-settings)
* [{#T}](#report-export)

## Creating a report {#create-report}



You can create a report in one of the following ways:

{% list tabs %}

- Workbook

  1. Go to the [page with workbooks and collections]({{ link-datalens-main }}/collections).
  1. Open the [workbook](../workbooks-collections/index.md) to create a report in.
  1. In the top-right corner, click **Create** and select **Report**.
  1. [Add pages](#report-pages) to your report.
  1. [Add](#add-widget) the [widgets](../dashboard/widget.md) you need to the pages.
  1. [Configure your report](#report-settings) and its individual [pages](#page-settings).
  1. In the top-right corner, click **Save**.
  1. In the window that opens, enter a name for the report and click **Create**.

- Navigation bar

  1. Go to the {{ datalens-short-name }} [home page]({{ link-datalens-main }}).
  1. In the left-hand panel, select ![image](../../_assets/console-icons/display-pulse.svg) **Reports** and click **Create report**.
  1. [Add pages](#report-pages) to your report.
  1. [Add](#add-widget) the [widgets](../dashboard/widget.md) you need to the pages.
  1. [Configure your report](#report-settings) and its individual [pages](#page-settings).
  1. In the top-right corner, click **Save**.
  1. In the window that opens, enter a name for the report and click **Create**.

{% endlist %}





You can [export](#report-export) the created report.

## Adding, moving, or deleting pages {#report-pages}

You can add multiple pages to a report, change their order, or delete them:

* To add a page, click ![image](../../_assets/console-icons/plus.svg) **Add Page** at the bottom left.
* To duplicate a page, in the preview area, click the ![image](../../_assets/console-icons/ellipsis.svg) icon next to the page and select ![icon](../../_assets/console-icons/copy.svg) **Duplicate**.
* To change the order of pages, drag them to a new location using your mouse.
* To delete a page, in the preview area, click the ![image](../../_assets/console-icons/ellipsis.svg) icon next the page and select ![icon](../../_assets/console-icons/trash-bin.svg) **Delete**.

## Configuring widgets {#report-widget-settings}

You can add, copy, or delete widgets in your report. When overlapping widgets, you can move them to the foreground or background.

### Adding a widget {#add-widget}

1. Select the report page you want to add the widget to.
1. Select a widget: [Chart](../concepts/chart/index.md), [Text](../dashboard/widget.md#text), [Title](../dashboard/widget.md#title), or Image. To immediately place the widget in the required location on the page, drag it with the left mouse button held down.
1. Configure your widget:

   {% list tabs group=widgets %}

   - Chart {#chart}

     * **Name**: Widget name. If the **Show** option is enabled (by default), the name is displayed at the top of the widget.
     * **Chart**: Select a chart from the list of items or provide a link to your chart.
     * (Optional) **Description**: Text displayed at the bottom of the widget.
     * (Optional) Under **Parameters**, list [chart parameters](../dashboard/dashboard_parameters.md#params-chart) and set their default values. If no default values are set, the report will display an error.
     * (Optional) Set a background.

   - Text {#text}

     * Enter the text of your link, clarifying caption, etc. The widget supports the [Markdown](../dashboard/markdown.md) markup language.

       {% note warning %}

       If you are inserting an image hosted in the {{ objstorage-full-name }} storage into a widget, set the [CORS](../../storage/operations/buckets/cors.md) settings for the bucket containing the image:

       {% include [datalens-cors-settings-note](../../_includes/datalens/datalens-cors-settings-note.md) %}

       {% endnote %}

     * (Optional) Set a background.

   - Title {#header}

     * Enter title text.
     * Select size.
     * (Optional) Set a background.

   - Image {#image}

     * Add a link to an [image](../dashboard/markdown.md#image) hosted in the [{{ objstorage-full-name }}](../../storage/quickstart.md) storage.

       {% note warning %}

       In {{ objstorage-full-name }} you must set the [CORS](../../storage/operations/buckets/cors.md) settings for the bucket with the image:

       {% include [datalens-cors-settings-note](../../_includes/datalens/datalens-cors-settings-note.md) %}

       {% endnote %}

     * (Optional) Specify an alternative text to display if the image fails to load.
     * (Optional) Disable the option to save the aspect ratio when resizing the widget. This option is enabled by default.
     * (Optional) Set a background.

   {% endlist %}

1. Click **Add**.
1. Resize the widget and move it to a convenient location on the page.
1. In the top-right corner, click **Save**.

You can copy and paste an already created widget onto the page:


* From any page of the current report.
* From the page of another report in the same workbook.
* From any dashboard in the same workbook.



To paste a copied widget onto a page:

1. Click the ![image](../../_assets/console-icons/ellipsis.svg) icon next to the widget you want to copy and select ![icon](../../_assets/console-icons/copy.svg) **Copy**. You can copy a widget from a dashboard in edit mode.
1. Select the report page you want to paste the widget into.
1. On the widget panel at the top, click ![icon](../../_assets/console-icons/copy-plus.svg) **Insert**.
1. Resize the widget and move it to a convenient location on the page.
1. In the top-right corner, click **Save**.

### Deleting a widget {#delete-widget}

1. Select the report page the widget is located on.
1. Click the ![image](../../_assets/console-icons/ellipsis.svg) icon next to the widget and select ![icon](../../_assets/console-icons/trash-bin.svg) **Delete**.
1. In the top-right corner, click **Save**.

### Moving a widget to the foreground or background {#move-widget-front-or-back}

Widgets on the page are arranged in layers that overlap each other. You can set the order of widgets on the page manually:

1. Select the report page the widget is located on.
1. Click the ![image](../../_assets/console-icons/ellipsis.svg) icon next to the widget and select:

   * ![icon](../../_assets/console-icons/arrow-up-to-line.svg) **Foreground** to move the widget to the foreground.
   * ![icon](../../_assets/console-icons/arrow-down-to-line.svg) **Background** to move the widget to the background.

1. In the top-right corner, click **Save**.

When you select or move a widget around the page, it is automatically overlaid on top of other widgets. Once you stop working with the widget, it will return to its layer.

## Configuring a report {#report-settings}

Report settings apply to all its pages:

1. At the top right, click ![icon](../../_assets/console-icons/gear.svg) **Report settings**.
1. Customize the appearance:

   * **Theme**: Select a page design theme: ![icon](../../_assets/console-icons/sun.svg) light or ![icon](../../_assets/console-icons/moon.svg) dark.
   * **Background color**: Specify a color in hexadecimal format or select a color from the color palette.
   * **Format**: Select a format: `A4` or `A3`.
   * **Orientation**: Select an orientation: `Album` or `Portrait`.

1. Set footer settings:

   * **{{ datalens-short-name }}** standard footer: Adds a footer: `Built in {{ datalens-full-name }}`.
   * **First page footer**: Repeats the footer on the first page. By default, the footer is not displayed on the first page.
   * **Page numbering**: Adds a page number to the footer.

## Configuring pages {#page-settings}

You can set individual settings for each page that differ from the general report settings. By default, the page is set to [report settings](#report-settings).

{% note info %}

Page settings have a higher priority than the same report settings. If the appropriate settings in the page settings have other values, they will be applied.

{% endnote %}

1. Select the report page you need to configure.
1. At the top right, click ![icon](../../_assets/console-icons/gear.svg) **Page settings** and enable the required settings:

   * **Theme**: Page design theme: ![icon](../../_assets/console-icons/sun.svg) light or ![icon](../../_assets/console-icons/moon.svg) dark.
   * **Background color**: Specify a color in hexadecimal format or select a color from the color palette.
   * **Format**: Page format: `A4` or `A3`.
   * **Orientation**: Page orientation: `Album` or `Portrait`.

1. In the top-right corner, click **Save**.

## Exporting a report {#report-export}

To export a report, click **Export**. The report is exported to a file in `.pdf`.
