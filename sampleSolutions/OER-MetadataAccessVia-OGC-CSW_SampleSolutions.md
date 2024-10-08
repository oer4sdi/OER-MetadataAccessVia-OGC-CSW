[OER-MetadataAccessVia-OGC-CSW](https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/tree/main) 

# Sample Solutions



## Task 3.4.5 (Python Notebook)

```python
# Define filter constraints
# Tip 1: use 'And' constraint: combined_filter = And([filter1, filter2, filter3])
# Tip 2: use 'csw:Title', 'csw:AnyText' or 'csw:subject' (aka Keywords) for filtering

filter1 = PropertyIsLike('csw:Title', '%Naturschutzgebiete%')
filter2 = PropertyIsLike('csw:Subject', 'INSPIRE')
filter3 = PropertyIsLike('csw:Anytext', '%Niedersachsen%')

combined_filter = And([filter1, filter2, filter3])


# GetRecords() method
csw.getrecords2(constraints=[combined_filter], maxrecords=20)

# If there are results print the titles of them
if csw.records is not None:
    # Show results
    for rec in csw.records.values():  # assuming response.records is a dictionary
        print(rec.title)
else:
    print("There are no results found. Please try to work out your filters")
```

 