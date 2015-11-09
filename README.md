# BI assignment 

The goal of this BI assignment is to find out if you could join our BI star-team to help us build a world-class data-driven startup.

We expect you to have not just lots of experience with building a data warehouse, but also hands-on experience with software development in other languages such as Python, Go, Nodejs, or PHP.

We will be evaluating the overall quality of your output, incl. the code quality & cleaness, SQL query optimisation, proper usage of a versioning tool and human-readable comments.

The assignment is split into 3 parts:

1. **Data warehouse & ETL load** => submission to a new GitHub repository
2. **Fix and clean the data** => submission via Evernote or whatever online note app
3. **API endpoint** => submission to a new GitHub repository

Please use `Readme.md` file in each repository to give us more info re. how did you approach the problem, why did you chose the solution you implemented etc.

### 1. Data warehouse & ETL

You can find these 3 tables in CSV files on AWS S3 (data storage):

* Table `offer` - offers from hotels
* Table `lst_currency` - list of all supported currencies
* Table `fx_rate` - currency exchange rates (rate from `prim_currency_id` to `scnd_currency_id`)

Please download the 3 files and create a simple ETL & data mart.

1. Create a new MySQL database & load the 3 tables (above) 1:1 to a new schema: `primary_data`
2. Create new schema: `bi_data` with the structure below
2. Create an ETL process to extract, transform and load the data from `primary_data` schema to `bi_data` schema


#### Data structure of `bi_data`

Please create new tables with the following structure. Add the SQL scripts to the repository.

* Table `valid_offers` (includes only active offers - `offer`.`valid_offer_flag` = 1)
	* `offer_id` `INT`
	* `hotel_id` `INT`
	* `hotel_name` `VARCHAR(255)`
	* `price` `FLOAT`
	* `currency_code` `VARCHAR(35)`
	* `valid_from_date` `DATETIME`
	* `valid_to_date` `DATETIME`
* Table `hotel_offers` (includes info about each hotel, for each day and each hour indicates if the hotel had at least one valid offer)
	* `hotel_id` `INT`
	* `date` `DATE`
	* `hour` `TINYINT`
	* `valid_offer_available_flag` `TINYINT`

#### ETLs

Please create scripts or procedures to transform the data from `primary_data` to the new tables in `bi_data`. Include the scripts to the repository.

The `valid_offers` table should show 

The `hotel_offers` table should indicate for each hotel if the hotel had offers for each day and hour. The days & hours when the hotel was not available should have indication `valid_offer_available_flag = 0`.

#### How to submit?

1. Create a new repository in GitHub, push the code and send us a link to the repository (see format below).
2. Write your notes to the `Readme.md` file in the repository.


### 2. Fix and clean the data




### 3. API endpoint

Please prepare a single API endpoint in whatever language you choose (Nodejs, PHP, Ruby, Python, ...). Pick a language you're most familiar with or the one you'd like to experiment with - in any case get ready for some follow-up questions.

The endpoint should expose some of the data from the newly created table `valid_offers` based on the request parameters. It should return a JSON response with the best deal (discount) for the hotel/checkin/checkout parameters. In other words - this API endpoint should return the offer with the best discount.

Request GET parameters:

* `hotelId`
* `checkinDate`
* `checkoutDate`

Endpoint `/offer/best-deal` with example GET params:

* `/offer/best-deal?hotelId=1234&checkinDate=2015-11-11&checkoutDate=2015-11-12`

JSON output:

```
{
	offerId: 12345678,
	hotelId: 1234,
	checkinDate: '2015-11-11',
	checkoutDate: '2015-11-12',
	sellingPrice: 234.34,
	currencyCode: 'USD'
}
```

#### How to submit?

1. Create a new repository in GitHub, push the code and send us a link to the repository.
2. Write your notes to the `Readme.md` file in the repository.

If you host this project on some publicly available IP, please send us the URL.

We should be able to run the project on localhost without any hassle (standard: no bugs, easy setup, documented Readme.md...).


## Example output

This is the output we expect to get from you. But feel free to over-deliver!

*****

*Dear BI Team,*

*It was lots of fun with the BI assignment and I'm happy I did it! The links are below:*

1. *DataMart & ETL*
	* URL to the repository: [GitHub link](http://www.github.com/example/repo2)
	* More info with screenshots & comments: See the `Readme.md` in the repository
2. *Fix and clean the data*
	* 
3. *API endpoint*
	* URL to the repository: [GitHub link](http://www.github.com/example/repo2)
	* More info: See the `Readme.md` in the repository

*Talk to you soon!*

*****

This will be enough for our team to jump on and evaluate. 

Good luck,
*~Your BI Team*




