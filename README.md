import pandas as pd
import matplotlib.pyplot as plt
from scipy import stats
bank_data = pd.read_csv("bank_data.csv", header=0, sep=",")
x = bank_data["duration"]
y = bank_data["campaign"]
slope, intercept, r_value, p_value, std_err = stats.linregress(x, y)
def myfunc(x):
    return slope * x + intercept
mymodel = list(map(myfunc, x))
plt.scatter(x, y)
plt.plot(x, mymodel, color="red")
plt.ylim(ymin=0, ymax=10)
plt.xlim(xmin=0, xmax=1000)
plt.xlabel("Duration")
plt.ylabel("Campaign")
plt.title("Linear Regression: Duration vs Campaign")
plt.show()
