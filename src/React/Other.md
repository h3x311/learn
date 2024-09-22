# Others

## Date
> Javascript的时间戳都是以毫秒为单位,一天aka `24 * 60 * 60 * 1000`
- getFullYear() - year
- (getMonth() + 1).toString().padStart(2, '0') - month
- getDate().toString().padStart(2, '0') - day
- input的type是date的返回值是`YYYY-MM-DD`
- new Date() 返回当前的时间戳