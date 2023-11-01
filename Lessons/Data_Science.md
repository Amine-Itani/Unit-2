```.py
import matplotlib.pyplot as plt
plt.style.use('ggplot')
# we want to graph y = x^3 from x = [-15, 15]

x = []
y = []
for n in range(-15, 15, 1):
    x.append(n)
    y.append(n**3)

fig = plt.figure(figsize=(9,7))
plt.plot(x, y, linewidth=3)
plt.title("Graph of the equation $y=x^3$")
plt.xlabel("x", fontsize=18)
plt.ylabel("y", fontsize=18)
plt.show()


```
