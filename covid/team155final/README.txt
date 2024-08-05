DESCRIPTION
This file contains the COVID Severity and Mortality Analysis dashboard, which has a TabPy connection. The Jupyter Notebook file included will produce and deploy the model, this notebook needs the Covid Data.csv as an input. The outputs are the model deployed to tableau and the two Covid_Clean_Sankey.csv and Covid_Clean.csv. 
The tableau dashboard will allow analysis of the trends in COVID outcomes, as well as real time predictions of COVID severity. Alink to the partial dashboard is available at: https://public.tableau.com/app/profile/maria.tariq/viz/group155visualization_NoTabpy/PatientAnalysis?publish=yes.  However, the full dashboard must be launched locally due to the TabPy Connection, instructions are included.  

INSTALLATION
Instructions here
1. Open Terminal and run:
pip install tabpy
pip install tabpy client
tabpy

Once this runs successfully you will see a line in the terminal with ”Web service listening on port 9004”, Note the port number displayed in the terminal once installation is successful.

2. In Tableau, navigate to Help > Settings and Performance > Manage Analytics Extension Connection.

3. Select TabPy and set the Hostname as localhost and the Port as the noted port number. Test the connection.

4. Open the Jupyter notebook and execute the entire file.

5. Go to Tableau and start using the notebook. If there are errors related to Datasource you can replace them with the same datasets in the folder.

EXECUTION
Open the dashboard and navigate to the desired pages. 

DEMO VIDEO 
https://youtu.be/OaDONF8AoAw
