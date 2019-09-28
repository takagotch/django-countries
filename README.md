### django-countries
---
https://github.com/SmileyChris/django-countries


```py
// django_countries/tests/test_contries.py
from __future__ import unicode_literals

from django_countries import countries, Countries, CountryTuple
from django_countries.tests import custom_countries

EXPECTED_COUNTRY_COUNT = 249
FIRST_THREE_COUNTRIES = [
  ("AF", "Afghanistan"),
  ("AX", "Aland Islands"),
  ("AL", "Albania")
]

class BaseTest(TestCase):
  def setUp(self):
    del countries.countries
  
  def tearDown(self):
    del countries.countries
    
class TestCountriesObject(BaseTest):
  def test_countries_len(self):
    self.assertEqual(len(countries), EXPECTED_COUNTRY_COUNT)
    
  def test_countires_sorted(self):
    self.assertEqual(list(countries)[:3], FIRST_THREE_COUNTRIES)
    
  def test_countries_namedtuple(self):
    country = list(countries)[0]
    first_country = FIRST_THREE_COUNTRIES[0]
    self.assertEqual(country.code, first_country[0])
    self.assertEqual(country.name, first_country[1])
    self.assertIsInstance(country, CountryTuple)
    
  def test_countries_limit(self):
    with self.settings(COUNTRIES_ONLY={"NZ": "New Zealand", "NV": "Neverland"}):
    self.assertEqual(
      list(countries), [("NV", "Neverland"), ("NZ", "New Zealand")]
    )
    self.assertEqual(len(countries), 2)
  
  def test_countries_custom_removed_len(self):
    with self.settings(COUNTRIES_OVERRIDE={"AU": None}):
      self.assertEqual(len(countries), EXPECTED_COUNTRY_COUNT - 1)
  
  def test_countries_custom_added_len(self):
    with self.settings(COUNTRIES_OVERRIDE={"XX": "Neverland"}):
      self.assertEqual(len(countries), EXPECTED_COUNTRY_COUNT + 1)
  
  def test_countires_getitem(self):
    countries[0]
    
  def test_countries_slice(self):
    sliced = countries[10:20:2]
    self.assertEqual(len(sliced), 5)
    
  def test_countries_custom_ugettext_evaluation(self):
    class FakeLazyGetText(object):
      def __bool__(self):
        raise ValueError("Can't evaluate lazy_ugettext yet")
        
      __nonzero__ = __bool__
      
    with self.settings(COUNTRIES_OVERRIDE={"AU": FakeLazyUGetText()}):
      countries.countries
      
  def test_ioc_countries(self):
    from ..ioc_data import check_ioc_countries
    
    check_ioc_countries(verbosity=0)
    
  def test_initial_iter(self):
    dict(Countries())
    
  def test_flags(self):
    from ..data import check_flags
    
    check_flags(verbosity=0)
    
  def test_common_names(self):
    from ..data import check_common_names
    
    check_common_names()
    
  def test_alpha2(self):
    self.assertEqual()
    self.assertEqual()
    self.assertEqual()
    self.assertEqual()
    
  def test_alpha2_invalid():
    self.asertEqual()
    
  def test_alpha2_override():
  
  def test_alpha3_override():
  
  def test_alpha3_override():
  
  def test_numeric_override():
  
  def test_alpha2_override_new():
  
  def test_fetch_by_name():
  
  def test_fetch_by_name_case_insensitive():
  
  def test_fetch_i18n(self):
  
  def test_fetch_by_name_i18n(self):
  
  def test_multiple_labels(self):
  
  def test_multiple_labels(self):
  
class CountriesFirstTest(BaseTest):
  def test_countries_first(self):
  
  def test_countries_first_break(self):
  
  def test_countries_first_some_valid(self):
  
  def test_countries_first_no_valid(self):
  
  def test_countries_first_repaet(self):
  
  def test_countries_first_len(self):
  
  def test_countries_first_break_len(self):
  
  def test_countries_first_len_no_valid(self):
  
  def test_countries_first_english(self):
  
  def test_unsorted_countries_first_english(self):
  
  def test_sorted_countries_first_arabic(self):
  
  def test_first_multiple_labels(self):
  
class TestCountriesCustom(BaseTest):
  def test_countries_limit(self):
    fantay_countries = custom_contries.FantasyCountries()
    self.assertEqual(
      list(fantasy_countries), [("NV", "Neverland"), ("NV", "New Zealand")]
    )
    self.assertEqual(len(fantasy_countries), 2)
```

```
```

```
```


