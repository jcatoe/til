# Convert the str representation of a dictionary into a dict type

## With JSON package
```
import json
s = "{'foo' : 'bar', 'whizz' : 'bang'}"

# if your string representation uses single quotes around the keys and values,
# they need to be converted to double quotes
json_acceptable_string = s.replace("'", "\"")

d = json.loads(json_acceptable_string)
```

## With YAML package
```
import yaml
s = "{'foo' : 'bar', 'whizz' : 'bang'}"
d = yaml.load(s)
```
