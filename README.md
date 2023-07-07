# Construction_of_3D_graphs
Construction of 3D graphs. Working with the mplot3d Toolkit
import re
import matplotlib.pyplot as plt
text = re.sub('[^a-zA-Z]', '', open('data.txt',
              mode='r', encoding='utf8').read())

count = {}

for char in text:
    if count.get(char):
        count[char] += 1
    else:
        count[char] = 1

plt.bar(count.keys(), count.values(), width=0.5, color='g')
plt.show()
plt.bar(count.keys(), count.values(), width=0.5, color='g')
plt.savefig('bar.png')
from math import *
import matplotlib.pyplot as plt
import matplotlib.animation as animation

def data_gen(x=0.01):
    cnt = 0
    while cnt < 1000:
        cnt += 1
        x += 0.01
        yield x, (sin(10 ** x) * sin(3 * x)) / (x ** 2)

def init():
    ax.set_ylim(-4, 4)
    ax.set_xlim(0, 1)
    del xdata[:]
    del ydata[:]
    line.set_data(xdata, ydata)
    return line,

fig, ax = plt.subplots()
line, = ax.plot([], [], lw=2)
ax.grid()
xdata, ydata = [], []

def run(data):
    x, y = data
    xdata.append(x)
    ydata.append(y)
    xmin, xmax = ax.get_xlim()
    ymin, ymax = ax.get_ylim()
    if x >= xmax:
        ax.set_xlim(xmin, 2 * xmax)
        ax.figure.canvas.draw()
    if y >= ymax:
        ax.set_ylim(ymin, 2 * ymax)
        ax.figure.canvas.draw()
    line.set_data(xdata, ydata)
    return line,

ani = animation.FuncAnimation(
    fig, run, data_gen, interval=10, repeat=False, init_func=init)
plt.show()

