# Laravel ฟังก์ชันที่ใช้งานบ่อย

## Syntax
### get Attribute
```bash
  get<attribute name/ camel case>Attribute($key){
    return $key;
  }
```
### set Attribute
```bash
  set<attribute name/ camel case>Attribute($key){
    $this->attributes['field_name'] = $value;
  }
```

## Example
### Ex.1 Override attribute ตอนดึงค่ามาแสดง
```php
public function getMemberDetailAttribute($key)
{
  if (isset($key))
    return json_decode($key);

  return null;
}
```

### Ex.2 Override attribute ตอนดึงค่ามาแสดง
```php
public function getPrevWaterMeterAttribute($key)
{
  if (is_null($key)) {
    return $this->member_detail->watermeter;
  }

  return $key;
}
```

### Ex.1 Override attribute ตอนเพิ่มค่าลงฐานข้อมูล
```php
public function setMemberDetailAttribute($value)
{
  $this->attributes['member_detail'] = _jsonUnescapedUnicode($value);
}
```

### Ex.1 Map values กรณีเรียกใช้งานฟังก์ชัน get()
```php
$result = $q->get();
$result->map(function ($item) use ($request) {
  return $item;
});
```

### Ex.2 Map values กรณีเรียกใช้งานฟังก์ชัน paginate(n)
```php
$result = $q->paginate(15);
$result->getCollection()->transform(function ($item) {
  return $item;
});
```

