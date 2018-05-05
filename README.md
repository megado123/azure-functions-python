### Azure Python Function:

To provide an API end point, an Azure Function App was implemented to take advantage of Microsoft’s serverless compute functions.  Azure Function Apps are designed to scale based on demand, so our application is 

This tool was established to enable scientists to capture datasets in a variety of environments and enable scientists to work with developers to integrate into existing processes.  These processes are not limited to a scientists desk, but limitless through the extensibility provided through an API.  Current tools on the market use propriety software to make this information available on a sample by sample basis.  Given the RESTful API, new samples can be imported and integrated directly into the sampling process, rather than having to ship information of to a lab and wait for results.  These results are now stored in a central repository enabling scientists to not only compare the results against a known repository of known components, but also building out a new repository of samples to enable product and sample traceability and evolution that has not been possible with tools on the market today.
The first hurdle to address what the fact that Azure Function Apps by default use Python 2.7.  Given this solution was based on python, to be used and supported by a team that has standardized on Python 3.6, we needed to ensure that as this solution moves across cloud environments (development, QA, and production), that a stream-lined deployment strategy was enabled.  Within our repository that is linked to the Azure Function App, a *deploy.cmd* script was created that with ensure that Python 3.61 is moved to the default Python Folder for executing scripts within the Azure environment, and that a virtual environment is established and dependencies are automatically installed to support the python solution.  Given our API needed to send its input into our Cosmos database, we used decided to use the Microsoft Azure Cosmos DB Python SDK.  Implementing the API with Python, using a non trival library did result in a performance hit of the responsiveness of the API.  The API averages a response time of 9 seconds.  According to Microsoft’s issues lists posted on Github[1], this is to be expected.  Every time the API is called, it is run against a new instance of python.exe which means that all libraries have be be loaded per execution.
Given the enterprises commitment to Python, we decided not to update this function and replace with a c# implementation, however, for our Azure Databricks Function App, a c# implementation was preferred.

A checkin of code to the master branch will update the Azure Function and deploy any neccesarry dependencies associated with the function.




 
