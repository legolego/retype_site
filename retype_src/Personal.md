---
label: Personal Projects
layout: default
order: 99
---

# Personal Projects

These are links/descriptions to personal projects.

---

## This Retype site
```c++
input: ./retype_src
output: C:/gitProjects/legolego.github.io
url: https://legolego.github.io/
cname: false

```
You can make this site yourself with [Retype](https://retype.com/), code is [here](https://github.com/legolego/retype_site). The navigation is built-in and it's all done with markdown.


## Temperature Records over time
[![](static/TemperatureRecords02.png)](https://github.com/legolego/WeatherRecords)
This was my first real attempt at using Jupyter notebooks, and I decided to see if I could find how many new high and low temperature records were being set over time.


## Attempts at Advent of Code
```python
sum = 0
for group in Lines01[:]:    
    group = group.split('\n')   
    sets = [set(x) for x in group]    
    #print(set.intersection(*sets))
    sum += len(set.intersection(*sets))
```
Really good practice from a couple years ago, my attempts [here](https://github.com/legolego/adventofcode2020).

## PyWekaBayes

```python
# Choose trained Weka BIFXML file
xmlfile = "D:/weka/iris.xml"    # created with BayesNet, MaxNrParents=2, BIFXML file
bifreader = JavaObject(JavaObject.new_instance("weka.classifiers.bayes.net.BIFReader"))
editable = Classifier(jobject=javabridge.make_instance(
                "weka/classifiers/bayes/net/EditableBayesNet",
                "(Lweka/classifiers/bayes/net/BIFReader;)V",
                bifreader.jwrapper.processFile(xmlfile)))

# We need to calculate the margins of all the attributes
marginCalc = JavaObject(JavaObject.new_instance("weka.classifiers.bayes.net.MarginCalculator"))
marginCalc.jwrapper.calcMargins(editable.jobject)

marginCalcNoEvidence = Serial.deepcopy(marginCalc)    # could maybe get by without this, just use marginCalc()
```

This is a simple [project](https://github.com/legolego/PyWekaBayes) showing how in Python to call the BayesNet classifier provided by Weka. A relevant Google Groups discussion is [here](https://groups.google.com/g/python-weka-wrapper/c/qF4vw_6sqAA/m/EmqTph1NAAAJ)