jsondict
========
Dict with json file saving / restoring support

- datetime, date support
- readable formated json
- safely file write with file move os function
- auto-save support
- compression support

Install
-------
    pip install jsondict

Usage
-----
    >>> from datetime import datetime
    >>> from jsondict import JsonDict
    >>> db = JsonDict('var/test.json')
    >>> db.clear()
    >>> db.update({'b': 2, 'created': datetime(2013, 1, 27, 21, 14), 'a': 1})
    >>> db.save()
    >>> open(db.filename).read()
    '{\n  "a": 1,\n  "b": 2,\n  "created": "2013-01-27T21:14:00Z"\n}'

Auto-save and compression
-------------------------
    >>> import gzip
    >>> db = JsonDict('var/test.json.gz', compress=True, autosave=True)
    >>> db.clear()
    >>> db['x'] = 'y'
    >>> gzip.open(db.filename).read()
    '{\n  "x": "y"\n}'