# Azure Data Factory
<h1 align="center">Hi 👋, I'm Tai</h1>
<h3 align="center"> Welcome to my Azure Data Factory Project </h3>
<br/>
<h4>  🌱 Check out my Microsoft Azure Data Factory Project using ETL process</h4>

<p>I started by using employee dataset stored in my Azure Data Lake. The data consisted of employee details and their sales. I then built a dataflow to load and transfrom the data of the sales products and product models data. I combined the two datasets in the dataflow and removed duplicate columns then filtered the row list price to filter out any list prices with thevalue of 0. When the transformations were complete I synced the final transfromations into a new dataset called 'ProductsFinal' where all the transformations were saved.</p>

<p>After completing my transfromations to satisfaction on the chosen datasets, I ran a pipeline with a copy activity to bring in some more data stored in my  Azure SQL databse, consisiting of employee data (ID, first name, last name) into the pipeline (Note: be sure to use a linked service that's compatible with SQL databases in azure for needed integrated runtime). I then run another pipeline using a 'Get Metadata' activity module to get the details of the last modified date using parameter arguments of last modified, size and item name. This was then attached to a 'stored procedure' activity module which facilitates native SQL code. From this stored procedure, I was then able to creat a 'lookup' activity module in a pipeline to get the metadata of the last execution date. Once this step was implemented, I created a pipeline to connect a 'If condition' activity which tested the last modified date and returned a true or false output. If true then the last execution date would be modified and if false, then there would be a wait activity. (Note: Azure timezone is in UTC so be sure to convert it to your timezone. I used "@convertFromUtc(pipeline().TriggerTime, 'Eastern Standard Time'" parameters in the expression builder for the correct execution date with DateTime type). Once I completed this to satisfaction, I run a pipeline with an 'execute' which is needed to execute the dataflow transfromations at pipeline level by debugging/running it here.</p>

Note: All activities can be run in a single pipeline but for demonstration purposes, you'll find I've seperated the activities into seperate pipelines in my repository.

<h3 align="left">Languages and Tools:</h3>
<p align="left"> <a href="https://azure.microsoft.com/en-in/" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/microsoft_azure/microsoft_azure-icon.svg" alt="azure" width="40" height="40"/> </a></p>
