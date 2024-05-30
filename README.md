# wallet_test
```
with debt as (
    select
        deal,
        sum(sum) as debt,
        min(date) as overdue_start_dt
    from pdcl
    group by deal
    having sum(sum) > 0
)

select
    deal,
    debt,
    overdue_start_dt,
    datediff(current_date, overdue_start_dt) as overdue_days
from debt
```
