## Case Scenario: Cleaning Bank Data
You have been asked to work with a bank to clean the data they collected as part of a recent marketing campaign, which aimed to get customers to take out a personal loan. They plan to conduct more marketing campaigns going forward so would like you to ensure it conforms to the specific structure and data types that they specify so that they can then use the cleaned data you provide to set up a PostgreSQL database, which will store this campaign's data and allow data from future campaigns to be easily imported.
They have supplied you with a csv file called "bank_marketing.csv", which you will need to clean, reformat, and split the data, saving three final csv files. Specifically, the three files should have the names and contents as outlined below:

## Expected outputs
### client.csv
|column        	|  data type	|      description	|      cleaning requirements|
|---------------|-------------|-------------------|---------------------------|
client_id	      |integer	    |Client ID	        |N/A
age	            |integer	    |Client's age in years	|N/A
job	            |object	      |Client's type of job	  |Change "." to "_"
marital         |	object	    |Client's marital status	                                  |N/A
education       |	object	    |Client's level of education	                              |Change "." to "_" and "unknown" to np.NaN
credit_default  |	bool	      |Whether the client's credit is in default	                |Convert to boolean data type:1 if "yes", otherwise 0
mortgage        |	bool	      |Whether the client has an existing mortgage (housing loan)	|Convert to boolean data type:1 if "yes", otherwise 0

### campaign.csv
|column        	       |  data type	|      description	|      cleaning requirements|
|----------------------|-------------|-------------------|---------------------------|
|client_id	           |integer	     |Client ID	          |N/A
|number_contacts	     |integer	     |Number of contact attempts to the client in the current campaign	|N/A
|contact_duration	     |integer	     |Last contact duration in seconds	|N/A
|previous_campaign_contacts	|integer |Number of contact attempts to the client in the previous campaign	|N/A
|previous_outcome	          |bool	   |Outcome of the previous campaign	|Convert to boolean data type:1 if "success", otherwise 0.
|campaign_outcome	          |bool	   |Outcome of the current campaign	  |Convert to boolean data type:1 if "yes", otherwise 0.
|last_contact_date          |datetime|Last date the client was contacted|Create from a combination of day, month, and a newly created year column (which should have a value of 2022);Format = "YYYY-MM-DD"

### economics.csv
|column        	|  data type	|      description	|      cleaning requirements|
|---------------|-------------|-------------------|---------------------------|
client_id	|integer	|Client ID	|N/A
cons_price_idx	|float	|Consumer price |index (monthly indicator)	|N/A
euribor_three_months	|float	|Euro |Interbank Offered Rate (euribor) three-month rate (daily indicator)	|N/A

## ----------- CODE -----------
```ruby
#Creating client, campaign, and economics datasets
# Verify columns exist  
print("Available Columns:", df.columns.tolist())

# Creating subsets  
client_columns = ["client_id", "age", "job", "marital_status", "education", "credit_default", "mortgage"]
campaign_columns = ["client_id", "campaign_contact", "days_since_last_contact", "previous_campaign_contacts", "previous_outcome", "campaign_outcome"]
economics_columns = ["client_id", "employment_variation_rate", "consumer_confidence_index", "euribor_three_months", "number_of_employees"]

# Ensure column names exist before selecting
for col_list in [client_columns, campaign_columns, economics_columns]:
    missing_cols = [col for col in col_list if col not in df.columns]
    if missing_cols:
        print(f"Missing columns: {missing_cols}")

# Create DataFrames
client = df[client_columns].copy()
campaign = df[campaign_columns].copy()
economics = df[economics_columns].copy()

# Verify dataset shapes
print(f"Client dataset shape: {client.shape}")
print(f"Campaign dataset shape: {campaign.shape}")
print(f"Economics dataset shape: {economics.shape}")

# Convert categorical columns to category type
client["job"] = client["job"].astype("category")
client["marital_status"] = client["marital_status"].astype("category")
client["education"] = client["education"].astype("category")
client["credit_default"] = client["credit_default"].astype("category")
client["mortgage"] = client["mortgage"].astype("category")

campaign["previous_outcome"] = campaign["previous_outcome"].astype("category")
campaign["campaign_outcome"] = campaign["campaign_outcome"].astype("category")

# Convert numerical columns
economics["employment_variation_rate"] = economics["employment_variation_rate"].astype(float)
economics["consumer_confidence_index"] = economics["consumer_confidence_index"].astype(float)
economics["euribor_three_months"] = economics["euribor_three_months"].astype(float)
economics["number_of_employees"] = economics["number_of_employees"].astype(int)

client.to_csv("client.csv", index=False)
campaign.to_csv("campaign.csv", index=False)
economics.to_csv("economics.csv", index=False)

```
