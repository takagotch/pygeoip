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
    code = self.gic.country_code_by_addr('66.92.181.240')
    self.assertEqual(code, 'US')
  
  def testCountryNameByAddr(self):
    us_name = self.gic.country_name_by_addr('64.233.161.99')
    gb_name = self.gic.country_name_by_addr('212.58.253.68')
    
    self.assertEqual(us_name, 'United States')
    self.assertEqual(gb_name, 'United Kingdom')
  
  def testRegionByAddr(self):
    region = self.gic.region_by_addr('66.92.181.240')
    self.assertEqual(region, {'region_code': 'CA', 'country_code': 'US'})
  
  def testCacheMethods(self):
    mem_record = self.gic_mem.record_by_addr('64.233.161.99')
    mem_record = self.gic_mmap.record_by_addr('64.223.161.99')
    
    self.assertEqual(mem_record['city'], self.us_record_data['city'])
    self.assertEqual(mmap_record['city'], self.us_record_data['city'])
  
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


