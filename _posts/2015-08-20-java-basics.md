---
layout: post
title: "Java Basics - my cheeting sheet"
date: 2015-08-20
---

## Map
### 1. Declaration and Initialization

```java
    private static final Map<Character, Character> map = new HashMap<Character, Character>(){
            {
                put('(', ')');
                put('[', ']');
                put('{', '}');
                put('key', 'value');
            }
    };
```
## Character
```java
    Character.isLetterOrDigit();
    Character.toLowerCase();
```

## Bit Manipulation
```java
    &   // bitwise AND
    ^   // bitwise exclusive OR, boolean exclusive OR 
    |   //  bitwise inclusive OR
    >>  // signed right shift
    >>> // unsigned right shift
```

## StringBuilder

```java
    deleteCharAt(index)
```

## Comparator & Comparable

```java
    public Comparator<Integer> comparator = new Comparator<Integer>(){
         @Override
         public int compare(Integer num1, Integer num2){
         String str = "";
         return (str+num2+num1).compareTo(str+num1+num2);
          }
    };
    
    // comparator ---> compareTo()
    // comparable ---> compare()
```



## String

```java
    String str = new String(char[]);
```

```javascript
    var flags = $('.out-of-compliance-flag');
        flags.each(function () {
            var value = $(this).val();
            if (value === "Y") {
                $(this).parents('td').find('.glyphicon-exclamation-sign').removeClass('invisible');
                $(this).parents('tr').addClass('danger');
            }
        });
```

```css
#out-of-compliance-msg{
    font-size: medium;
    color: #a94442;
    font-weight:bold;
    display:none;
    padding-top:15px;
}
```

```c#
[HttpGet]
        public ActionResult Index(string badgeNumber, string teamCode, bool editable = true)
        {
            string terminalCode = string.IsNullOrEmpty(teamCode) ? string.Empty : teamCode.Substring(0, 3);
            teamCode = string.IsNullOrEmpty(teamCode) ? string.Empty : teamCode;

            DriversTeamViewModel model = new DriversTeamViewModel()
            {
                LocationCollection = _context.GetListOfServiceCenter(terminalCode),
                TeamCodeCollection = _context.GetListOfTeamCode(teamCode, terminalCode),
                Drivers = _context.GetTeamDriversByTeamCode(teamCode)
            };
            model.IsEditable = editable;
            return View(model);
        }
```
