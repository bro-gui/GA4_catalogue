<h1></a>Add your catalog to GA4 without modifying your data layer, thanks to GA4 item data import.</h1>
<h2>Implent extra items data with no cost, easy and fast to update.</h2>
Importing item data into GA4 simplifies and reduces the amount of e-commerce data you need to send with events (good for your speed and TMS implementation) : a single item ID will be sent to GA4 at the time of collection, and can be associated with your imported item data to feed e-commerce dimensions and metrics into your reports.

<h2>What's the point? I've already spent time and money to get the perfect datalayer.</h2>
Yes but I'm sure you already get plenty of question as : 

<li>What is the conversion rate for the new collection?</li>
<li>Are plain products more popular than multicolored ones?</li>
<li>To what extent has the rate of additions to the basket increased for sold-out products?</li>
<li>What is the conversion rate for packshot products?</li>

Or, even more brilliantly, the styling department decides to stop using black and white because it's too obvious. Suddenly, sales plummet. What's the impact on the product to be added to the basket? Or better still, the brand has just decided that colors should have brand names. For example, blue is no longer called blue but Figueroles, red is now Ricin and grey is dead long live Slate. How do you compare the change? And I'm not telling you everything I've seen!
Anyway there is always a solution to get the answer. You therefore need to implement the data directly in your datalayer to obtain the new item dimensions. And use GA4's custom dimensions like category1, 2, … This is a good idea but the data will be update only for the new collect and your dev team will ask you many days to do it. If you're using Looker Studio, you could  blend data with your catalog. OK, only if you're looking for simple data. Or you could mix it with a google spreadsheet from your catalogue. If you're using BigQuery, you might already have a table with all the requirements, so you'll just do a join. But it's best to get the data without any lookup.
All theses solutions work, but making to much noise. Fortunately, we have GA4, and as everyone knows, it's both a frustrating and brilliant solution. And thankfully, the UA import option is still there.
Import item data allows you to integrate your entire product catalogue, enabling you to measure user behaviour, site traffic, sales and conversions using item-specific data such as size, colour, style or any other item dimension.

And for those who don't know, it is possible to create calculated measures in GA4. For example, the margin, the personalised COGS measure. But you simply need to find the add-to-cart/view item, which is not visible in GA4 reports. And then have it in the report as shown in the screenshot below. Link to GA4 google support

![image](https://github.com/bro-gui/GA4_ImportItemData/assets/159245204/69f752c1-0f87-4f97-a979-4df128173791)

<h2>So start to custom and pimp your Item data </h2>
Datas you are about to import will be attached to the GA4 data. So when you go to a report Analytics will issue a request for the report data. What's interesting here is that this type of join is temporary.
In this way, GA4 combines the imported data with its internal data to create a unified view when you generate a report. If you delete your imported data in GA4, you won't be able to create new reports or access the joined data created before.
You can upload data via the same data source multiple times as long as you are just adding values to existing fields. If you want to add fields to a data source, you need to delete the existing data source and then create a new one - once you save a data source, you can't change the mapping of Analytics fields to the fields in your CSV.
<h3>]> Create a CSV file</h3>
Create a CSV file of item dimensions upload the google exmple file for Item data template . Beaware to use commas rather than semicolons. 
To give an example, I'm only going to change part of my catalogue and I'm going to try and find out which items can get the best add to cart ratio. So I will put for some ID a Brand dimension Brand_foo and some others IDs brand_bar. Balance items will not be mapped in my new catalogue.

<h3>]> Upload the data</h3>
When you import data, you create a data source. A data source is the combination of the CSV file you want to upload and a mapping of existing Analytics fields to the fields in your CSV. 
The SFTP server method also allows you to connect the GA4 to your server and schedule periodic data downloads. This method is best suited to large-scale or automated data imports.
<li>Click Create data source.</li>
<li>Enter a name for your data source.</li>
<li>Select the data type</li>

![image](https://cdn-images-1.medium.com/max/1200/1*sdpLibMNB-td1gQYmc55Rw.png)

Then click import and ok then 
Click Review terms if prompted. This prompt is displayed if you are importing device or user data.
Select Manual CSV upload, select the CSV file on your computer, then click Open.

![image](https://cdn-images-1.medium.com/max/1200/1*jW4DKG990qJuDOPo7NzUpA.png)

By mistake, when I did the mapping, I used the item_cat2 dimension for the Brand dimension. So if I look at the brand I now have 2 other categories cat2w and cat2b imported on the Item ID data. The other items that I haven't mapped still have the UK brand.
![image](https://cdn-images-1.medium.com/max/1200/1*oE2GrdylEofueTqCzJRVZw.png)

<h3>]> To import new data:</h3>
If the mapping is the same you just have to click Import now and choose the relevant CSV file on your computer. 

But for my example I need to change my mapping. So I need first to delete the datas (see next step below). once it's done you could upload the new data with the new mapping and I now have the correct dimension in my report. 

*⁀➷And I got my answer, and I could say that items with Brand_foo is 6% add_to_cart when the brand_bar is 2 times less!
![image](https://cdn-images-1.medium.com/max/1200/1*3K2pZNMEiN5oNob1--37HA.png)
Don't forget that it can take up to 24 hours for this data to be included in your studio looker reporting.
<h3>]> delete the data</h3>
If you want to delete the data source:
<li>Click > Delete data source.</li>
<li>Read the deletion notice, then click Delete data source.</li>

Then you will come back to the original data collected from your TMS and datalayer.
![image](https://cdn-images-1.medium.com/max/1200/1*suhkrtOjLNriMuSwoDsGig.png)
I hope that's been clear and that you'll now find lots of ways to use these tips. If not I'm sure I could find some for you ≽^•⩊•^≼
