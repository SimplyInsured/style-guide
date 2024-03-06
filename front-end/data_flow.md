# Passing Data between Back End and Front End

## Summary

The goal of this document is to outline where developers should look to make mutations to data when communicating between the front end and the back end.  The main two reasons for doing so are:

1. Keeps your mutations predictable.  Given that there are so many steps in the pipeline, if you run into trouble with your data, you can guess where the change to the data took place.
2. Makes the Back End independent of the Front End.  The two should have as little knowledge of each other as possible, so that changes can be made on either end independent of each other. 

## Sending Data to the Front End

![data-to-front-end](https://github.com/SimplyInsured/style-guide/assets/5034574/80e30de7-1147-4bd4-a0cd-30193e1a142c)

Serialize

There are two things you can do here:

1. Add any fields not present in your model schema that is required by the exposed back end schema.
2. Normalize any field into desired exposed format.
```ruby
class PlanSerializer < ApplicationSerializer
  attributes :price
  
  # bad
  # You don't need to format a value in a way that would be useful to display to the user.  This should
  # be done in the view.
  def price_as_string
    "$" + price
  end

  # ok
  # this is ok if the calculation is fairly heavy, or requires a ton of business logic.
  # but bad if you are just trying to average an array of prices that the front end already has access to.
  def average
    employees.map{|e| e.price}.average
  end

  # good
  def available_to_purchase
    on_market && !indemnity
  end

  # good
  # ok to format if the format is an expected standard of the backend.
  def price
    price.round(2)
  end
```
    
