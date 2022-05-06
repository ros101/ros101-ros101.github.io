---
layout: notes
---
# Postcode

The UK postcode system consists of a string that contains a number of characters and numbers.

Create a python program that implements a regex that complies with the rules provided above – test it against the examples provided.

Examples:
* M1 1AA
* M60 1NW
* CR2 6XH
* DN55 1PT
* W1A 1HQ
* EC1A 1BB

How do you ensure your solution is not subject to an evil regex attack?

```python
import re

pattern = r'^(((([A-Z]{1,2})[0-9])[A-Z])|(([A-Z])[0-9])|(([A-Z]{1,2})[0-9]{1,2})) ([0-9]([A-Z]{2}))$'

def parse(post_code):
    '''parses the given postcode returning a dict with the fields'''
    match = re.match(pattern, post_code)

    if match is not None:
        # the regex tries to distinguish between different configurations
        # the presence of group 2 or 5 is used to separate the three cases
        if(match.group(2) is not None):
            return {
                'Valid': True,
                'Otutward Code': match.group(1),
                'Inward Code': match.group(9),
                'Postcode Area': match.group(4),
                'District Code': match.group(3),
                'Sub Discrict': match.group(1),
                'Unit': match.group(10)
            }
        elif(match.group(5) is not None):
            return {
                'Valid': True,
                'Otutward Code': match.group(1),
                'Inward Code': match.group(9),
                'Postcode Area': match.group(6),
                'District Code': match.group(5),
                'Sub Discrict': None,
                'Unit': match.group(10)
            }
        else:
            return {
                'Valid': True,
                'Otutward Code': match.group(1),
                'Inward Code': match.group(9),
                'Postcode Area': match.group(8),
                'District Code': match.group(7),
                'Sub Discrict': None,
                'Unit': match.group(10)
            }
    else:
        # the string is not a valid postcode
        return { 'Valid': False}

def test(parsed, outward, inward, area, district, sub, unit):
    '''compares the dict with the expected values''''
    if(parsed['Otutward Code'] != outward):
        raise Exception('error')
    if(parsed['Inward Code'] != inward):
        raise Exception('error')
    if(parsed['Postcode Area'] != area):
        raise Exception('error')
    if(parsed['District Code'] != district):
        raise Exception('error')
    if(parsed['Sub Discrict'] != sub):
        raise Exception('error')
    if(parsed['Unit'] != unit):
        raise Exception('error')

# values tested with https://ideal-postcodes.co.uk/guides/uk-postcode-format

# this covers all cases
# the postcode (first parameter) is split in the other parameters
test(parse('AB1C 2DE'), 'AB1C', '2DE', 'AB', 'AB1', 'AB1C', 'DE')
test(parse('B1C 2DE'), 'B1C', '2DE', 'B', 'B1', 'B1C', 'DE')
test(parse('B1 2DE'), 'B1', '2DE', 'B', 'B1', None, 'DE')
test(parse('B12 3DE'), 'B12', '3DE', 'B', 'B12', None, 'DE')
test(parse('AB1 2CD'), 'AB1', '2CD', 'AB', 'AB1', None, 'CD')
test(parse('AB12 3CD'), 'AB12', '3CD', 'AB', 'AB12', None, 'CD')

# some extra tests with the provided examples
test(parse('M1 1AA'), 'M1', '1AA', 'M', 'M1', None, 'AA')
test(parse('M60 1NW'), 'M60', '1NW', 'M', 'M60', None, 'NW')
test(parse('CR2 6XH'), 'CR2', '6XH', 'CR', 'CR2', None, 'XH')
test(parse('DN55 1PT'), 'DN55', '1PT', 'DN', 'DN55', None, 'PT')
test(parse('W1A 1HQ'), 'W1A', '1HQ', 'W', 'W1', 'W1A', 'HQ')
test(parse('EC1A 1BB'), 'EC1A', '1BB', 'EC', 'EC1', 'EC1A', 'BB')
```

The solution implements able to validate a postcode and extract 'Otutward Code', 'Inward Code', 'Postcode Area', 'District Code', 'Sub Discrict', and 'Unit'. It limits the risks of evil regex attack because it uses precise quantifiers (eg. `([A-Z]{1,2})`) to cap the number of possible patterns.
