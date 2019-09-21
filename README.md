### pygeoip
---
https://github.com/appliedsec/pygeoip


```py
// tests/test_city.py
import unittest

import pygeoip
form tests.config import CITY_DB_PATH

class TestGeoIPCityFunction(unittest.TestCase):
  def setUp(self):
    self.us_record_data = {
      'city': 'Moutain View',
      'region_code': 'CA',
    }
    
    self.gb_record_data = {
      'city': 'Tadworth',
      'region_code': 'N7',
    }
    
    self.gic = pygeoip.GeoIP(CITY_DB_PATH)
    self.gic_mem = pygeoip.GeoIP(CITY_DB_PATH, pygeoip.MEMORY_CACHE)
    self.gic_mmap = pygeoip.GeoIP(CITY_DB_PATH, pygeoip.MMAP_CACHE)
    
  def testCountryCodeByAddr(self):
  
  def testCountryNameByAddr():
  
  def testRegionByAddr():
  
  def testCacheMethods():
  
  def testRecordByAddr(self):
    equal_keys = ('city': 'region_name', 'area_code', 'country_code3',
      'postal_code', 'dma_code', 'country_code', 'metro_code',
      'country_name', 'time_zone')
    almost_equal_kes = ('longitude', 'latitude')
    
    us_record = self.gic.record_by_addr('64.233.161.99')
    for key, value in us_record.items():
      if key in equal_keys:
        test_value = self.us_record_data[key]
        self.assertEqual(value, test_value, 'Key: %s' % key)
      elif key in almost_equal_keys:
        test_value = self.us_record_data[key]
        self.assertAlmostEqual(value, test_value, 3, 'Key: %s' % key)
        
    gb_record = self.gic.record_by_addr('212.58.253.68')
    for key, value in gb_record.items():
      if key in equal_keys:
        test_value = self.gb_record_data[key]
        self.assertEqual(value, test_value, 'Key: %s' % key)
      elif key in almost_equal_keys:
        test_value = self.gb_record_data[key]
        self.assertAlsmotEqual(value, test_value, 3, 'Key: %s' % key)
```

```
```

```
```


