### 1. Importing
```ruby
import re
```

### 2. Main Functions
```ruby
re.search()	#Search for pattern anywhere in string (returns match or None)
re.match()	#Match pattern at beginning of string (returns match or None)
re.fullmatch()	#Match entire string
re.findall()	#Return all non-overlapping matches in a list
re.finditer()	#Return iterator yielding match objects
re.sub()	#Replace pattern with string
re.split()	#Split string by pattern
re.compile()	#Compile regex pattern for reuse
```

### 3. Common Patterns
```ruby
.	#Any character except newline
^	#Start of string
$	#End of string
*	#0 or more
+	#1 or more
?	#0 or 1
{n}	#Exactly n
{n,}	#n or more
{n,m}	#Between n and m
[]	#Character set
()	#Group
\d	#Digit
\D	#Non-digit
\w	#Word char
\W	#Non-word char
\s	#Whitespace
\S	#Non-whitespace
```

### 4. Examples
```ruby
# Search for 'cat' anywhere
re.search('cat', 'A cat and a dog.')     # Match object

# Match at start
re.match('cat', 'cat dog')               # Match object

# Find all numbers
re.findall(r'\d+', 'abc 123 def 456')    # ['123', '456']

# Substitute
re.sub(r'\s+', '-', 'a b   c')           # 'a-b-c'

# Split by commas or spaces
re.split(r'[,\s]+', 'a, b c')            # ['a', 'b', 'c']

# Compile and reuse
pattern = re.compile(r'\w+')
pattern.findall('Hello world!')           # ['Hello', 'world']
```

### 5. Match Object Methods
```ruby
.group()	Return matched string
.groups()	Return all groups as tuple
.start()	Start index of match
.end()	End index of match
```

### 6. Flags
```ruby
re.I	Ignore case
re.M	Multiline ^ $
re.S	Dot matches newline
re.findall(r'cat', 'Cat cat', re.I)      # ['Cat', 'cat']
```
