import random

import numpy as np

def sigmoid(x):
    return 1 / (1 + np.exp(-x))

def d_sigmoid(x):
    return sigmoid(x)*(1-sigmoid(x))

class Person():

    def __init__(self, x, tr, name):
        self.x = x
        self.tr = tr
        self.name = name

def Data_study(dict):
    name = []
    x = []
    for i in dict:
        a = i[1:4]
        name.append(i[0])
        for j in range(len(a)):
            a[j] = float(a[j])

        x.append(a)

    tr = []
    for i in dict:
        v = []
        a = i[-1]
        for k in range(1):
            if k == 1:
                continue
            if k == a - 1:
                v.append(1)
            else:
                v.append(0)
        tr.append(v)
    return np.array(x), tr, name

def derivative(q):
    y = []
    D_w = [[]]
    D_b = []
    for i in range(len(w_o)):
        y.append(sigmoid(np.sum(q.x * w_o[i])) + b[i])

    for i in range(len(y)):
        for j in range(len(q.x)):
            d = 2*(q.tr[i] - y[i]) * d_sigmoid(y[i]) * q.x[j]
            D_w[i].insert(j, d)

    for i in range(len(y)):
        d = 2*(q.tr[i] - y[i]) * d_sigmoid(y[i])
        D_b.append(d)


    return D_w, D_b


def Why(q, w):
    y = []
    for i in range(len(w)):
        y.append(sigmoid(np.sum(q.x * w[i]) + b[i]))

    print(q.name)
    print(y)
    print(q.tr)

def Backprop(x, tr, name):
    D_w = []
    D_b = []
    for i in range(10):
        q = Person(x[i], tr[i], name[i])
        d_w, d_b = derivative(q)
        D_w.append(d_w)
        D_b.append(d_b)

    C_w = [[]]
    for i in range(len(D_w[0][0])):
        for j in range(len(D_w[0])):
            s = 0
            for k in range(len(D_w)):
                s += D_w[k][j][i]
            C_w[j].insert(i, s)

    for i in range(len(w_o)):
        for j in range(len(w_o[0])):
            if C_w[i][j] > 0:
                w_o[i][j] -= learn_w * C_w[i][j]
            elif C_w[i][j] < 0:
                w_o[i][j] += learn_w * C_w[i][j]

    C_b = []
    for i in range(len(D_b[0])):
        s = 0
        for j in range(len(D_b)):
            s += D_b[j][i]
        C_b.append((s))
    for i in range(len(b)):
            if C_b[i] > 0:
                b[i] -= learn_b * C_b[i]
            elif C_b[i] < 0:
                b[i] += learn_b * C_b[i]


def Study():
    x, tr, name = Data_study(Data_st)
    for i in range(1000):
        Backprop(x, tr, name)
    print('Смещение - ',b)
    print('Веса - ',w_o)

def a(q, w):
    y = []
    for i in range(len(w)):
        y.append(sigmoid(np.sum(q.x * w[i]) + b[i]))

    if np.sum(q.x) == 0:
        s = 'Неодобрено'

    elif y[0] < 0.483:
        s = 'Неодобрено'
    else:
        s = 'Одобрено '


    print(q.name, " - ", s)

Data_st =[['Петя', 1.0, 1.0, 0.0, 1.0], ['Вася', 1.0, 0.0, 1.0, 0.0], ['Катя', 1.0, 1.0, 0.0, 1.0], ['Ваня', 1.0, 1.0, 0.0, 1.0], ['Вика', 1.0, 0.0, 1.0, 0.0], ['Толя', 1.0, 1.0, 1.0, 0.0], ['Аня', 0.0, 0.0, 1.0, 0.0], ['Саша', 1.0, 1.0, 1.0, 0.0], ['Даша', 1.0, 1.0, 0.0, 1.0], ['Паша', 0.0, 1.0, 0.0, 1.0]]
x, tr, name= Data_study(Data_st)



w_o = [[0, 0, 0]]
learn_w = 0.00001
learn_b = 0.001
b = [0]

Study()


x_in = []
a1 = int(input('Стаж работы: '))
a2 = int(input('Возраст: '))
a3 = int(input('Cудимость: '))
x_in.append(a1)
x_in.append(a2)
x_in.append(a3)
x_in = np.array(x_in)
q = Person(x_in, None, 'Person')
a(q, w_o)
