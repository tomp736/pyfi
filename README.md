# PYFI

## Projects

### pyfi_core
 - Common classes for building transactionviews using transactions, filter rules, and transform rules. 

 ### pyfi_server
 - Sample app using flask and charts.js. 
 - Configs are currently hardcoded to `datasource.json` and `views.json` under `src/server`.

## Usage:

``` python

## Setup
transaction = <[transaction]>
start_date = <datetime>
end_date = <datetime>
time_delta_d = <int>
transaction_view_filters = [
    RegexFieldFilterStrategy('counterpart_data', ".*UBER.*")
]

# optionally create an exchange rate provider
exchange_rate_provider = ExchangeRateProvider()
transaction_transform_currency = CurrencyTranformStrategy("PLN", exchange_rate_provider)

## Extract View
transaction_view_builder = TransactionViewBuilder(transactions)
transaction_view_builder.set_duration(start_date, end_date, timedelta(days=time_delta_d))
transaction_view_builder.add_transform(transaction_transform_currency)
transaction_view_builder.add_filters(transaction_view_filters)
transaction_view_builder_views = transaction_view_builder.get_views()
```

## Web Interface

![Screenshot](screenshot.png)


## Progress

### pyfi_core - Exchange Rates

- [x] Hardcoded implementation
- [ ] UnitTests
- [ ] External data provider.

### pyfi_core - DataSource

- [x] ING CSV
- [ ] UnitTests
- [ ] Import/Export to pyfi native datastore
- [ ] ??

### pyfi_core - 

- [x] ING CSV
- [ ] UnitTests
- [ ] ??

### Frontend

- [x] Chart.js Bars
- [ ] UI Labels for Inputs
- [ ] Stacked Bar