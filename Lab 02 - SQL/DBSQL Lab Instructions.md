# Databricks Lakehouse Bootcamp
Databricks SQL Student Workbook

Working with APJuice Data

As part of this workshop section, we will be working with simulated APJuice data derived from retail juice stores across multiple cities in ANZ. We will use two key fact tables and 3 dimension tables tovisualize data curated as part of the Data Modelling exercise completed earlier. Ultimately, we want to create a dashboard that can be used by our business to view the status of the APJuice business in ANZ.

- Make sure to run these notebooks in **Lab 02 - SQL** folder:

- **01 - Data Setup**
- **02 - Data Modeling - When running this notebook, you will need to replace "\<\>" with your database name. You can find that database name in cmd 4 of the 01 - Data Setup notebook. But it should be** _ **firstName** _ **\_** _ **lastName** _ **\_ap\_juice\_db.**

![](RackMultipart20221205-1-u52hv4_html_c540b45b3d5889fa.png)

![](RackMultipart20221205-1-u52hv4_html_96b7a24903a77b92.png)

Run Queries and Create Visualizations

**Step 1: Access Databricks SQL**

1. Click the persona navigator on the top left and select 'SQL'.

2. Tap the 'Queries' icon in the sidebar.

3. Click the 'New Query' button.

4. Your SQL endpoint should already be selected. If it is not, please use the menu to select an appropriate SQL endpoint.

5. In the schema browser panel select the database used as part of the earlier Data Modelling exercise (this database will be your username followed by **ap\_juice\_db** ).

![](RackMultipart20221205-1-u52hv4_html_5967818d24bf6f3b.png)

**Step 2: Build your Orders Master queries**

| Please note: If you are working in a shared workspace. In this step, you will create and save a query appearing in the shared Databricks workspace. To avoid confusion, please **prepend** the saved name of any query with your initials and any 3-digit number. For example, Han Solo might name his saved query: **hs130 Orders Master**. Later, you can then use the search functionality to identify your queries. |
| --- |

We can start to do some analysis on orders by country and city.

● Name this query 'Orders Master'. _Don't forget to prepend that name with the identifier you chose using the pattern in the note above_ _if in a shared workspace__._

● Write a query to join apj\_sales\_fact table with dim\_store\_locations table. ● Use the editor and the schema browser to try writing your own query to accomplish this, **or** copy and paste the following code into the editor (make sure to replace **'deepak\_sekar\_ap\_juice\_db'** with the relevant database name derived as part of Step 1). ● Execute the query.

| select a.store\_id, a.order\_source, a.order\_state, b.city, b.country\_code, b.name as store\_name, count(\*) as cnt from deepak\_sekar\_ap\_juice\_db.apj\_sales\_fact a join deepak\_sekar\_ap\_juice\_db.dim\_store\_locations b on a.slocation\_skey = b.slocation\_skey group by a.store\_id, a.order\_source, a.order\_state, b.city, b.country\_code, b.name |
| --- |

Your table should look like this:

![](RackMultipart20221205-1-u52hv4_html_104f18926f48b194.png) **Step 3: Add 4 Visualizations**

● Click the 'Add Visualization' button for every time you want to create a new visualization and then create the following 4 visualizations.

● Make sure to go to the Data Labels tab in the visualization panel and turn on "Show Data Labels" for every visualization you create.

● Save every visualization with an appropriate name, as indicated in the screenshots below.

![](RackMultipart20221205-1-u52hv4_html_cf2ea7dc8438f071.png)

![](RackMultipart20221205-1-u52hv4_html_ebb86e2e43e5586d.png)

![](RackMultipart20221205-1-u52hv4_html_a67bc9b0f7f8015b.png)

![](RackMultipart20221205-1-u52hv4_html_9bdf625b2fedc6f6.png) **\**

**Step 4: Build your Products Master queries**

| Please note: If you are working in a shared workspace. In this step, you will create and save a query appearing in the shared Databricks workspace. To avoid confusion, please **prepend** the saved name of any query with your initials and any 3-digit number. For example, Han Solo might name his saved query: **hs130 Orders Master**. Later, you can then use the search functionality to identify your queries. |
| --- |

We can start to do some analysis on orders by country and city.

● Name this query Products Master'. _Don't forget to prepend that name with the identifier you chose using the pattern in the note above._

● Write a query to join apj\_sales\_fact table with dim\_store\_locations table. ● Use the editor and the schema browser to try writing your own query to accomplish this, **or** copy and paste the following code into the editor (make sure to replace **'deepak\_sekar\_ap\_juice\_db'** with the relevant database name derived as part of Step 1). ● Execute the query.

| select b.city, b.country\_code, b.name as store\_name, a.product\_size, c.name as product\_name, count(\*) as cnt, sum(product\_cost) as total\_product\_cost from deepak\_sekar\_ap\_juice\_db.apj\_sale\_items\_fact a join deepak\_sekar\_ap\_juice\_db.dim\_store\_locations b on a.slocation\_skey = b.slocation\_skey join deepak\_sekar\_ap\_juice\_db.dim\_products c on a.product\_skey = c.product\_skey where a.unique\_customer\_id is not null and b.current\_record = 'Y' and c.current\_record = 'Y' group by b.city, b.country\_code,b.name, a.product\_size, c.name |
| --- |

Your table should look like this:

![](RackMultipart20221205-1-u52hv4_html_f325d09bfaaedc3f.png) **Step 5: Add 2 Visualizations**

● Click the 'Add Visualization' button for every time you want to create new visualization and then create the following 2 visualizations.

● Make sure to go to the Data Labels tab in the visualization panel and turn on "Show Data Labels" for every visualization you create.

● Save every visualization with an appropriate name as indicated in the screenshots below.

![](RackMultipart20221205-1-u52hv4_html_a370b606cf24c1f7.png)

![](RackMultipart20221205-1-u52hv4_html_acc5e5b4f6ea7ce8.png)

Create and Customize Your Dashboard

Now, let's work on building our dashboard so that we can share our visualizations with the business.

**Step 1: Create New Dashboard**

● Click on the Dashboards tab, and then click the Create Dashboard' button. ● Name your new dashboard " \<Your Unique Identifier\> APJuice Lakehouse' (ensuring that you prepend the title with your unique identifier).

**Step 2: Add**  **Visualization**

● Click on the 'Add Visualization' button.

● Type the identifier you selected into the search bar.

● Select all the visualizations you created (6 in total) and add to the dashboard one after another

**Step 3: Arrange and Resize**

Once you've added the widgets above, you can use drag-and-drop functionality and resizing tools to arrange them. Drag, drop and resize the 13 visualizations so that they are placed next to one other in a 2 column style. Ideally, country-based visualizations on the left side and city-based visualizations on the right side. Please refer to the below screenshot as an example

![](RackMultipart20221205-1-u52hv4_html_4014fe086c03815c.png)

Parameterized Queries

Now, let's explore some more features in the query editor that will allow us to create dashboards that our users can interact with. This dataset represents ANZ and NZL APJuice retail outlets. So far, we have created queries and visualizations that capture metrics that include all of the data across all of the stores. Now, we'll amend our existing queries and visualizations to allow the viewer to drill down based on country code.

For this, we will write a parameterized query. Parameterized queries allow the viewer to substitute values into a query at runtime without editing the query source.

The next few steps will walk through an example of how you might use parameterized queries in practice.

**Step 1: Add a Parameter to Orders Master Query**

Let's update an existing query to incorporate a query parameter that we can then leverage as part of the dashboard that we have created.

● Navigate to the 'Queries' tab and type the identifier you selected into the search bar using the 'Search Queries' text box on the right-hand side of the user interface. ● Click on the query titled '\<Your unique identifier\> Orders Master''.

● Tap the 'Add New Parameter' button ('{{ }}').

● Enter 'country\_code' in the 'Keyword field.

● Update the 'Title' field to read 'Country\_Code'.

● Amend the 'Type' field to read 'Dropdown List'.

● In the 'Values' field, enter 'All' and press the 'Enter' key.

● Type 'AUS' in the subsequent line, followed by 'NZL' in the third line

● Tick the 'Allow multiple values' checkbox.

● Update the 'Quotation' field to read 'Single Quotation Marks':

![](RackMultipart20221205-1-u52hv4_html_97a9276d8cd2d8b.png)

● Click the 'Add Parameter' button.

● You should now see the query parameter visible in the UI and represented in the query editor text box.

● Update your query to incorporate the country\_code query parameter that has been created (using a WHERE clause) **or** copy and paste the following code into the editor (make sure to replace ' **deepak\_sekar\_ap\_juice\_db'** with the relevant database name derived as part of the first section).

● Select 'All' from the Country\_Code field and tap the 'Apply Changes' button. ● Click 'Save' to save the changes to the query.

select

a.store\_id,

a.order\_source,

a.order\_state,

b.city,

b.country\_code,

b.name as store\_name,

count(\*) as cnt

from

deepak\_sekar\_ap\_juice\_db.apj\_sales\_fact a

join deepak\_sekar\_ap\_juice\_db.dim\_store\_locations b on a.slocation\_skey = b.slocation\_skey

WHERE

(

'All' IN ({{ Country\_Code }})

OR country\_code IN ({{ Country\_Code }})

)

group by

a.store\_id,

a.order\_source,

a.order\_state,

b.city,

b.country\_code,

b.name

**Step 2: Update Products Master Query to Include the Parameter**

● Navigate to the 'Queries' tab and type the identifier you selected into the search bar using the 'Search Queries' text box on the right-hand side of the user interface. ● Click on the query titled '\<Your unique identifier\> Products Master''.

● Tap the 'Add New Parameter' button ('{{ }}').

![](RackMultipart20221205-1-u52hv4_html_93e0f676ff0e3400.png)

● Enter 'country\_code' in the 'Keyword field.

● Update the 'Title' field to read 'Country\_Code'.

● Amend the 'Type' field to read 'Dropdown List'.

● In the 'Values' field, enter 'All' and press the 'Enter' key.

● Type 'AUS' in the subsequent line, followed by 'NZL' in the third line

● Tick the 'Allow multiple values' checkbox.

● Update the 'Quotation' field to read 'Single Quotation Marks':

![](RackMultipart20221205-1-u52hv4_html_97a9276d8cd2d8b.png)

● Click the 'Add Parameter' button.

● You should now see the query parameter visible in the UI and represented in the query editor text box.

● Update your query to incorporate the country\_code query parameter that has been created (using a WHERE clause) **or** copy and paste the following code into the editor (make sure to replace ' **deepak\_sekar\_ap\_juice\_db'** with the relevant database name derived as part of the first section).

● Select 'All' from the Country Code field and tap the 'Apply Changes' button. ● Click 'Save' to save the changes to the query.

| select b.city,b.country\_code, b.name as store\_name, a.product\_size, c.name as product\_name, count(\*) as cnt, sum(product\_cost) as total\_product\_cost from deepak\_sekar\_ap\_juice\_db.apj\_sale\_items\_fact a join deepak\_sekar\_ap\_juice\_db.dim\_store\_locations b on a.slocation\_skey = b.slocation\_skey join deepak\_sekar\_ap\_juice\_db.dim\_products c on a.product\_skey = c.product\_skey WHERE ( 'All' IN ({{ Country\_Code }}) OR country\_code IN ({{ Country\_Code }}) )and a.unique\_customer\_id is not null and b.current\_record = 'Y' and c.current\_record = 'Y' group by b.city, b.country\_code, b.name, a.product\_size, c.name |
| --- |

**Step 3: Create Dashboard Filters**

● Click on the Dashboards tab, and type the identifier you selected into the search bar using the 'Search' text box on the right-hand side of the user interface.

● Click on the '\<Your Unique Identifier\> APJuice Lakehouse' dashboard and note that you should now see the query parameters that you have created within each dashboard widget.

● Tap the kebab button on the right-hand side of the user interface and click the 'Edit' menu option.

![](RackMultipart20221205-1-u52hv4_html_44a7171aeab136da.png)

● Select the 'Use Dashboard Level Filters' checkbox.

● Click the kebab button that appears in the upper right corner of any of the widgets and click the 'Edit Widget Settings' from the menu option.

![](RackMultipart20221205-1-u52hv4_html_b2d39642cd3121fc.png)

● Tap the edit icon next to the text that reads 'Widget parameter' and, from the dialogue box that is displayed, select the ' **New dashboard parameter**' option and click the 'OK' button. ● Tap the 'Save' button, and you should now see the 'Country\_Code' filter represented on the dashboard itself (and no longer visible within the dashboard widget). ● Repeat this for all the other widgets except this time select the ' **Existing dashboard parameter'** option, ensure that 'Country\_Code' is populated in the 'Key' field and click the 'OK' button. ![](RackMultipart20221205-1-u52hv4_html_21099d5823b62152.png)

● Once done, tap the 'Done Editing' button.

![](RackMultipart20221205-1-u52hv4_html_266bf97eb3f248e3.png)

● Using the 'Country\_Code' dashboard filter, experiment with contextualising the visualisations based on the appropriate country that has been selected from the drop-down menu.