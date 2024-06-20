---
title: Códigos
---
Códigos implementados em sala de aula com o apoio da professora Tânia. É possível acessar o link abaixo de cada script e fazer testes no Google Colab!

## Código | Método de Lagrange

``` bash
def metodoLagrange():
    pontos = int(input("Quantidades de pontos que serão utilizados: "))
    X, Y = [], []
    for i in range(pontos):
        x = float(input("x" + str(i) + " = "))
        X.append(x)
        y = float(input("y" + str(i) + " = "))
        Y.append(y)

    x = float(input("Valor que se deseja interpolar: "))
    coeficientes = []
    for indice in range(pontos):
        L = 1
        for j in range(pontos):
            if indice != j:
                L *= (x - X[j]) / (X[indice] - X[j])
        coeficientes.append(L)

    pn = 0
    for i in range(pontos):
        pn += Y[i] * coeficientes[i]

    print("p(" + str(x) + ") =", pn)

metodoLagrange()
```

Mais informações: [Código no Google Drive](https://colab.research.google.com/drive/1r6elwnrv4xSy8LPku_KdAWnlHs1roEcz?usp=sharing)

## Código | Método de Newton

``` bash
def metodoNewton():
    quant_pontos = int(input('Quantidade de pontos: '))
    pontos, f_pontos = [], []
    tabela = []

    for i in range(quant_pontos):
        ponto = float(input(f'x{i} = '))
        f_ponto = float(input(f'f(x{i}) = '))
        pontos.append(ponto)
        f_pontos.append(f_ponto)
    tabela.append(f_pontos)

    x = float(input('Ponto x a ser estimado: '))
    print()

    passo = 1
    for n in range(quant_pontos - 1):
        ordem = []
        for m in range(len(tabela[n]) - 1):
            dif_dividida = (tabela[n][m+1] - tabela[n][m]) / (pontos[m+passo] - pontos[m])
            ordem.append(dif_dividida)
        tabela.append(ordem)
        passo += 1

    for k in range(len(tabela)):
        print(f'Ordem {k}:', tabela[k])
    print()

    aprox = 0
    grau = 0
    for i in range(len(tabela)):
        fator = tabela[i][0]
        for j in range(grau):
            fator *= (x - pontos[j])
        grau += 1
        aprox += fator

    print(f'A aproximação encontrada para f({x}) = {aprox}')

metodoNewton()
```

Mais informações: [Código no Google Drive][def]

[def]: https://colab.research.google.com/drive/127d0vcANHwbpE7vJo_jQGfYR8UpufX6U?usp=sharing