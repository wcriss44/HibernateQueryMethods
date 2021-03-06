## Fork your Repository from [here](https://github.com/NOVA-Uncommon-Coders/HibernateQueryMethods).
Let's write a purchase history table! But first, enjoy this gif of two hamsters in a hamster wheel.

![screenshot](https://lh6.googleusercontent.com/-jziFd9qK9qM/UJKz-jQJ3NI/AAAAAAACYAE/1SF8WJOF52w/w506-h380/photo.jpg)

## Description

 [customers.csv](https://raw.githubusercontent.com/oakes/java-assignments/master/6.3-orm-omg/customers.csv) and [purchases.csv](https://raw.githubusercontent.com/oakes/java-assignments/master/6.3-orm-omg/purchases.csv) are already in the root of your project, parse them, and store them in PostgreSQL via Spring Data. Then display the purchases along with the name and email of the customer who made them using the entity joining capability of Spring Data.

## Requirements

* Create a database in PostgreSQL and add the appropriate settings to your `application.properties`
* Create an empty `home.html` template and a `/` route in your controller to serve it
* Create `Customer` and `Purchase` classes that can hold all the info from their respective CSVs, along with an id (add the appropriate annotations so it can be used with Spring Data)
  * The `Purchase` class should also have a `Customer` field which will serve to join the two tables together
  * You *don't* need to store the `customer_id` in your `Purchase` class, because the join system will create that column for you
* Create `CustomerRepository` and `PurchaseRepository` interfaces that can act as Spring Data repositories for the aforementioned classes
* In your controller, create a `@PostConstruct` method called `init` to parse the CSV files
  * For each CSV file, you should loop over each line, parse each column into a `Customer` or `Purchase` object, and add it to a repository
  * Make it so this *only* happens when the repositories are empty
* Edit `home.html` and the `/` route to make it display the purchases
  * It should display the results in an HTML table so the columns line up (see screenshot below)
  * You should be able to see the name and email from the customer table, and the category, credit card, cvv, and date fields from the purchase table
* Filter the table by category via a query parameter
  * In `PurchaseRepository`, add a method that finds `Purchase` objects by category
  * Modify your `/` route to take a `category` parameter
  * If the parameter isn't null, call the method you made instead of `findAll`
  * Displays links at the top that allow you to filter by each category

![screenshot](https://github.com/oakes/java-assignments/raw/master/6.3-orm-omg/screenshot2.png)