### php获取N个自然月后的日期

```php
function next_months($date, $months = 1) {
    if (is_numeric($date)) {
        $date = date('Y-m-d', $date);
    }
    $next_month = date('Y-m-d', strtotime('+' . $months . ' month', strtotime($date)));
    list($d_y, $d_m, $d_d) = explode('-', $date);
    list($n_y, $n_m, $n_d) = explode('-', $next_month);

    $diff = ($n_y - $d_y) * 12 + ($n_m - $d_m);

    if ($diff > $months) {
        $next_month = date('Y-m-d', strtotime('last day of next month', strtotime($date)));
    }

    return $next_month;
}
```

来源: :link:https://yian.me/blog/php/get-the-date-of-next-month-in-php.html

