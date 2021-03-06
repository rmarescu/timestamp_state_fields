# TimestampStateFields

Treat timestamp columns as state fields in a model.

## Usage
Call timestamp_state_fields on timestamp columns that represents state of your model, e.g.

    Class Order < ActiveRecord::Base
      include TimestampStateFields
      timestamp_state_fields :processed_at, :canceled_at
    end

It will enable the following interactions on user model.

    order = Order.new

    # checks for presence of processed_at timestamp
    order.processed?

    # checks if canceled_at is nil
    order.not_canceled?

    # sets processed_at timestamp
    order.mark_as_processed unless order.processed?

    # unsets processed_at timestamp
    order.mark_as_not_processed

    # You can combine multiple scopes
    Order.processed.not_canceled.count

## Installation

Add this line to your application's Gemfile:

    gem 'timestamps_state_fields'

And then execute:

    $ bundle install

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
