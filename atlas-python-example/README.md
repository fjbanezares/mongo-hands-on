# Atlas Python hands-on

First, let's create an account in Atlas the online database that Mongo offers for free with small scale and training purposes.

Once created get the access URL, will look something like this:
```python
mongodb+srv://fjbanezares:<password>@cluster0.h5kauwo.mongodb.net/?retryWrites=true&w=majority
```

With this we cane instantiate a client, choose a database and within a namespace:
```python
import pymongo
import math
client = pymongo.MongoClient('mongodb+srv://user:password@cluster0.h5kauwo.mongodb.net/?retryWrites=true&w=majority')
mydb = client["test"]
sinfun = mydb["sin"]
```

Here we generate a dataset based on a sinusoid,we take little more than 2 pi radians.
```python
data = []
for i in range(100):
    x = i/10.
    y = math.sin(x)
    data.append({'x':x,'y':y})
# the list of records is written to the database in one go:
sinfun.insert_many(data)
print('done')
```


now see the entries in Mongo
```python
client.sinfun.find()
sinfun = client.test.sin
sinfun.find_one()
```

```python
df = pd.DataFrame(entries)
df.head()
```

visualize
```python
import matplotlib.pyplot as plot
df.plot('x')
plot.show()
```