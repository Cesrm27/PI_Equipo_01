# Taller 3: IA - Regresión LinealTaller 3: IA - Regresión LinealTaller 3: IA - Regresión Lineal

IntroducciónIntroducciónIntroducción

En este taller trabajamos con un modelo de regresión lineal, que es una técnica que sirve para predecir un valor numérico (en este caso, el consumo de energía) a partir de otras variables que lo pueden explicar (temperatura, horas de operación, carga y humedad).En este taller trabajamos con un modelo de En este taller trabajamos con un modelo de regresión linealregresión lineal, que es una técnica que sirve para predecir un valor numérico (en este caso, el consumo de energía) a partir de otras variables que lo pueden explicar (temperatura, horas de operación, carga y humedad)., que es una técnica que sirve para predecir un valor numérico (en este caso, el consumo de energía) a partir de otras variables que lo pueden explicar (temperatura, horas de operación, carga y humedad).

Primero exploramos los datos con gráficos y estadísticas para entender cómo se comportan. Luego entrenamos un modelo que aprende una fórmula matemática para predecir el consumo de energía, y revisamos qué tan bien funciona esa predicción. Finalmente, comparamos ese modelo con datos inventados y con otro tipo de modelo (un árbol de decisión), para confirmar si el modelo realmente detecta qué variables importan y cuáles no.Primero exploramos los datos con gráficos y estadísticas para entender cómo se comportan. Luego entrenamos un modelo que aprende una fórmula matemática para predecir el consumo de energía, y revisamos qué tan bien funciona esa predicción. Finalmente, comparamos ese modelo con datos inventados y con otro tipo de modelo (un árbol de decisión), para confirmar si el modelo realmente detecta qué variables importan y cuáles no.Primero exploramos los datos con gráficos y estadísticas para entender cómo se comportan. Luego entrenamos un modelo que aprende una fórmula matemática para predecir el consumo de energía, y revisamos qué tan bien funciona esa predicción. Finalmente, comparamos ese modelo con datos inventados y con otro tipo de modelo (un árbol de decisión), para confirmar si el modelo realmente detecta qué variables importan y cuáles no.

## Bloque 1: Importar herramientas y cargar los datosBloque 1: Importar herramientas y cargar los datosBloque 1: Importar herramientas y cargar los datos

```python
import numpy as npimport numpy as npimport numpy as np
import pandas as pdimport pandas as pdimport pandas as pd
import matplotlib.pyplot as pltimport matplotlib.pyplot as pltimport matplotlib.pyplot as plt
import seaborn as snsimport seaborn as snsimport seaborn as sns
%matplotlib inline%matplotlib inline%matplotlib inline
df = pd.read_csv("/Data_PI_regresion.csv")df = pd.read_csv("/Data_PI_regresion.csv")df = pd.read_csv("/Data_PI_regresion.csv")
df.head()df.head()df.head()
```

imagen:imagen:imagen:

![Imagen del taller](imagenes/imagen_4.png)

> **Aprendí:** Que antes de trabajar con datos hay que "traer" las herramientas necesarias: numpy y pandas para manejar números y tablas, y matplotlib/seaborn para hacer gráficos. Luego cargamos el archivo con los datos (temperatura, horas de operación, carga, humedad y consumo de energía) y vimos las primeras filas para saber cómo se ven.Aprendí:Aprendí: Que antes de trabajar con datos hay que "traer" las herramientas necesarias: numpy y pandas para manejar números y tablas, y matplotlib/seaborn para hacer gráficos. Luego cargamos el archivo con los datos (temperatura, horas de operación, carga, humedad y consumo de energía) y vimos las primeras filas para saber cómo se ven. Que antes de trabajar con datos hay que "traer" las herramientas necesarias: numpy y pandas para manejar números y tablas, y matplotlib/seaborn para hacer gráficos. Luego cargamos el archivo con los datos (temperatura, horas de operación, carga, humedad y consumo de energía) y vimos las primeras filas para saber cómo se ven.

## Bloque 2: Revisar la información general de los datosBloque 2: Revisar la información general de los datosBloque 2: Revisar la información general de los datos

```python
df.info(verbose=True)df.info(verbose=True)df.info(verbose=True)
df.describe().round(1)df.describe().round(1)df.describe().round(1)
df.columnsdf.columnsdf.columns
```

Imagen:Imagen:Imagen:

![Imagen del taller](imagenes/imagen_1.png)

> **Aprendí:** Que antes de hacer cualquier modelo hay que revisar los datos: cuántas filas y columnas tiene la tabla, si falta información, y de qué tipo es cada dato. describe() me dio un resumen rápido (promedio, mínimo, máximo) de cada variable, y columns solo me mostró los nombres de las columnas.Aprendí:Aprendí: Que antes de hacer cualquier modelo hay que revisar los datos: cuántas filas y columnas tiene la tabla, si falta información, y de qué tipo es cada dato. Que antes de hacer cualquier modelo hay que revisar los datos: cuántas filas y columnas tiene la tabla, si falta información, y de qué tipo es cada dato. describe()describe() me dio un resumen rápido (promedio, mínimo, máximo) de cada variable, y me dio un resumen rápido (promedio, mínimo, máximo) de cada variable, y columnscolumns solo me mostró los nombres de las columnas. solo me mostró los nombres de las columnas.

## Bloque 3: Graficar y explorar visualmente los datosBloque 3: Graficar y explorar visualmente los datosBloque 3: Graficar y explorar visualmente los datos

```python
sns.pairplot(df)sns.pairplot(df)sns.pairplot(df)
df["Consumo_Energia"].plot.hist(bins=25, figsize=(8,4))df["Consumo_Energia"].plot.hist(bins=25, figsize=(8,4))df["Consumo_Energia"].plot.hist(bins=25, figsize=(8,4))
df["Consumo_Energia"].plot.density()df["Consumo_Energia"].plot.density()df["Consumo_Energia"].plot.density()
```

imagen:imagen:imagen:

![Imagen del taller](imagenes/imagen_6.png)

> **Aprendí:** Que los gráficos ayudan a "ver" los datos antes de modelarlos. El pairplot compara todas las variables entre sí para detectar relaciones a simple vista. El histograma me mostró cómo se distribuyen los valores de consumo de energía (si son bajos, altos o parejos), y el gráfico de densidad es una versión más suave de ese mismo histograma.Aprendí:Aprendí: Que los gráficos ayudan a "ver" los datos antes de modelarlos. El Que los gráficos ayudan a "ver" los datos antes de modelarlos. El pairplotpairplot compara todas las variables entre sí para detectar relaciones a simple vista. El histograma me mostró cómo se distribuyen los valores de consumo de energía (si son bajos, altos o parejos), y el gráfico de densidad es una versión más suave de ese mismo histograma. compara todas las variables entre sí para detectar relaciones a simple vista. El histograma me mostró cómo se distribuyen los valores de consumo de energía (si son bajos, altos o parejos), y el gráfico de densidad es una versión más suave de ese mismo histograma.

## Bloque 4: Ver qué tan relacionadas están las variables (correlación)Bloque 4: Ver qué tan relacionadas están las variables (correlación)Bloque 4: Ver qué tan relacionadas están las variables (correlación)

numeric_df = df.select_dtypes(include=[np.number])numeric_df = df.select_dtypes(include=[np.number])numeric_df = df.select_dtypes(include=[np.number])

numeric_df.corr().round(4)numeric_df.corr().round(4)numeric_df.corr().round(4)

```python
plt.figure(figsize=(10,7))plt.figure(figsize=(10,7))plt.figure(figsize=(10,7))
sns.heatmap(numeric_df.corr(), annot = True, linewidths=2)sns.heatmap(numeric_df.corr(), annot = True, linewidths=2)sns.heatmap(numeric_df.corr(), annot = True, linewidths=2)
```

imagen:imagen:imagen:

![Imagen del taller](imagenes/imagen_7.png)

> **Aprendí:** Que la correlación mide qué tan relacionadas están dos variables: un valor cercano a 1 significa que suben y bajan juntas, y uno cercano a 0 significa que no tienen relación. El heatmap convierte esos números en un mapa de colores, así es más fácil identificar de un vistazo qué variables están más conectadas con el consumo de energía.Aprendí:Aprendí: Que la correlación mide qué tan relacionadas están dos variables: un valor cercano a 1 significa que suben y bajan juntas, y uno cercano a 0 significa que no tienen relación. El Que la correlación mide qué tan relacionadas están dos variables: un valor cercano a 1 significa que suben y bajan juntas, y uno cercano a 0 significa que no tienen relación. El heatmapheatmap convierte esos números en un mapa de colores, así es más fácil identificar de un vistazo qué variables están más conectadas con el consumo de energía. convierte esos números en un mapa de colores, así es más fácil identificar de un vistazo qué variables están más conectadas con el consumo de energía.

## Bloque 5: Separar variables y preparar los datos para el modeloBloque 5: Separar variables y preparar los datos para el modeloBloque 5: Separar variables y preparar los datos para el modelo

```python
l_column= list(df.columns)l_column= list(df.columns)l_column= list(df.columns)
len_feature = len(l_column)len_feature = len(l_column)len_feature = len(l_column)
x = df[l_column[0:len_feature-1]]x = df[l_column[0:len_feature-1]]x = df[l_column[0:len_feature-1]]
y = df[l_column[len_feature-1]]y = df[l_column[len_feature-1]]y = df[l_column[len_feature-1]]
from sklearn.model_selection import train_test_splitfrom sklearn.model_selection import train_test_splitfrom sklearn.model_selection import train_test_split
x_train, x_test, y_train, y_test = train_test_split(x, y, test_size=0.3, random_state=123)x_train, x_test, y_train, y_test = train_test_split(x, y, test_size=0.3, random_state=123)x_train, x_test, y_train, y_test = train_test_split(x, y, test_size=0.3, random_state=123)
```

imagen:imagen:imagen:

![Imagen del taller](imagenes/imagen_3.png)

> **Aprendí:** Que para entrenar un modelo hay que separar los datos en dos partes: x son las variables que "explican" el resultado (temperatura, horas, carga, humedad) y y es lo que queremos predecir (consumo de energía). Además, hay que dividir los datos en un grupo para entrenar el modelo (70%) y otro para probarlo (30%) con datos que el modelo no vio antes, así se sabe si realmente aprendió o solo memorizó.Aprendí:Aprendí: Que para entrenar un modelo hay que separar los datos en dos partes: Que para entrenar un modelo hay que separar los datos en dos partes: xx son las variables que "explican" el resultado (temperatura, horas, carga, humedad) y son las variables que "explican" el resultado (temperatura, horas, carga, humedad) y yy es lo que queremos predecir (consumo de energía). Además, hay que dividir los datos en un grupo para entrenar el modelo (70%) y otro para probarlo (30%) con datos que el modelo no vio antes, así se sabe si realmente aprendió o solo memorizó. es lo que queremos predecir (consumo de energía). Además, hay que dividir los datos en un grupo para entrenar el modelo (70%) y otro para probarlo (30%) con datos que el modelo no vio antes, así se sabe si realmente aprendió o solo memorizó.

## Bloque 6: Entrenar el modelo de regresión linealBloque 6: Entrenar el modelo de regresión linealBloque 6: Entrenar el modelo de regresión lineal

```python
from sklearn.linear_model import LinearRegressionfrom sklearn.linear_model import LinearRegressionfrom sklearn.linear_model import LinearRegression
from sklearn import metricsfrom sklearn import metricsfrom sklearn import metrics
lm = LinearRegression()lm = LinearRegression()lm = LinearRegression()
lm.fit(x_train, y_train)lm.fit(x_train, y_train)lm.fit(x_train, y_train)
print("El termino de interseccion del modelo lineal", lm.intercept_)print("El termino de interseccion del modelo lineal", lm.intercept_)print("El termino de interseccion del modelo lineal", lm.intercept_)
print("Los coeficientes del modelo lineal:", lm.coef_)print("Los coeficientes del modelo lineal:", lm.coef_)print("Los coeficientes del modelo lineal:", lm.coef_)
cdf = pd.DataFrame(lm.coef_,x.columns,columns=["Coeficientes"])cdf = pd.DataFrame(lm.coef_,x.columns,columns=["Coeficientes"])cdf = pd.DataFrame(lm.coef_,x.columns,columns=["Coeficientes"])
cdfcdfcdf
```

> **Aprendí:** Que un modelo de regresión lineal básicamente arma una fórmula donde cada variable tiene un "peso" (coeficiente) que indica cuánto influye en el resultado. Al entrenarlo (fit), el modelo calcula esos pesos automáticamente. La tabla de coeficientes me permitió ver, por ejemplo, qué tanto influye la temperatura o la humedad en el consumo de energía.Aprendí:Aprendí: Que un modelo de regresión lineal básicamente arma una fórmula donde cada variable tiene un "peso" (coeficiente) que indica cuánto influye en el resultado. Al entrenarlo ( Que un modelo de regresión lineal básicamente arma una fórmula donde cada variable tiene un "peso" (coeficiente) que indica cuánto influye en el resultado. Al entrenarlo (fitfit), el modelo calcula esos pesos automáticamente. La tabla de coeficientes me permitió ver, por ejemplo, qué tanto influye la temperatura o la humedad en el consumo de energía.), el modelo calcula esos pesos automáticamente. La tabla de coeficientes me permitió ver, por ejemplo, qué tanto influye la temperatura o la humedad en el consumo de energía.

## Bloque 7: Revisar qué tan confiables son los coeficientesBloque 7: Revisar qué tan confiables son los coeficientesBloque 7: Revisar qué tan confiables son los coeficientes

```python
n = x_train.shape[0]n = x_train.shape[0]n = x_train.shape[0]
k = x_train.shape[1]k = x_train.shape[1]k = x_train.shape[1]
degrees_of_freedom = n - k - 1degrees_of_freedom = n - k - 1degrees_of_freedom = n - k - 1
train_pred = lm.predict(x_train)train_pred = lm.predict(x_train)train_pred = lm.predict(x_train)
train_error = np.square(train_pred - y_train)train_error = np.square(train_pred - y_train)train_error = np.square(train_pred - y_train)
sum_error = np.sum(train_error)sum_error = np.sum(train_error)sum_error = np.sum(train_error)
se = [0, 0, 0, 0]se = [0, 0, 0, 0]se = [0, 0, 0, 0]
for i in range(k):for i in range(k):for i in range(k):
r = sum_error / degrees_of_freedom r = sum_error / degrees_of_freedom r = sum_error / degrees_of_freedom
r = r / np.sum(np.square(x_train.iloc[:, i] - x_train.iloc[:, i].mean())) r = r / np.sum(np.square(x_train.iloc[:, i] - x_train.iloc[:, i].mean())) r = r / np.sum(np.square(x_train.iloc[:, i] - x_train.iloc[:, i].mean()))
```

se[i] = np.sqrt(r) se[i] = np.sqrt(r) se[i] = np.sqrt(r)

```python
cdf = pd.DataFrame({'Standard Error': se})cdf = pd.DataFrame({'Standard Error': se})cdf = pd.DataFrame({'Standard Error': se})
cdf['Coefficients'] = lm.coef_cdf['Coefficients'] = lm.coef_cdf['Coefficients'] = lm.coef_
cdf['t-statistic'] = cdf['Coefficients'] / cdf['Standard Error']cdf['t-statistic'] = cdf['Coefficients'] / cdf['Standard Error']cdf['t-statistic'] = cdf['Coefficients'] / cdf['Standard Error']
cdfcdfcdf
```

> **Aprendí:** Que no basta con tener los coeficientes, también hay que saber si son confiables. Calculando el "error estándar" y el "t-statistic" de cada variable pude ver cuáles realmente influyen de forma importante en el consumo de energía y cuáles podrían no aportar mucho.Aprendí:Aprendí: Que no basta con tener los coeficientes, también hay que saber si son confiables. Calculando el "error estándar" y el "t-statistic" de cada variable pude ver cuáles realmente influyen de forma importante en el consumo de energía y cuáles podrían no aportar mucho. Que no basta con tener los coeficientes, también hay que saber si son confiables. Calculando el "error estándar" y el "t-statistic" de cada variable pude ver cuáles realmente influyen de forma importante en el consumo de energía y cuáles podrían no aportar mucho.

## Bloque 8: Graficar cada variable contra el consumo de energíaBloque 8: Graficar cada variable contra el consumo de energíaBloque 8: Graficar cada variable contra el consumo de energía

l = list(x.columns)l = list(x.columns)l = list(x.columns)

```python
from matplotlib import gridspecfrom matplotlib import gridspecfrom matplotlib import gridspec
fig = plt.figure(figsize=(18, 10))fig = plt.figure(figsize=(18, 10))fig = plt.figure(figsize=(18, 10))
gs = gridspec.GridSpec(2, 2)gs = gridspec.GridSpec(2, 2)gs = gridspec.GridSpec(2, 2)
ax0 = plt.subplot(gs[0])ax0 = plt.subplot(gs[0])ax0 = plt.subplot(gs[0])
ax0.scatter(x[l[0]], y)ax0.scatter(x[l[0]], y)ax0.scatter(x[l[0]], y)
ax0.set_title(l[0] + " vs. Consumo_Energia", fontdict={'fontsize': 20})ax0.set_title(l[0] + " vs. Consumo_Energia", fontdict={'fontsize': 20})ax0.set_title(l[0] + " vs. Consumo_Energia", fontdict={'fontsize': 20})
```

# ... (se repite para las otras 3 variables)# ... (se repite para las otras 3 variables)# ... (se repite para las otras 3 variables)

imagen:imagen:imagen:

![Imagen del taller](imagenes/imagen_2.png)

> **Aprendí:** Que graficar cada variable por separado contra el resultado (consumo de energía) ayuda a ver visualmente si existe una relación clara (una tendencia) o si los puntos están totalmente dispersos sin ningún patrón.Aprendí:Aprendí: Que graficar cada variable por separado contra el resultado (consumo de energía) ayuda a ver visualmente si existe una relación clara (una tendencia) o si los puntos están totalmente dispersos sin ningún patrón. Que graficar cada variable por separado contra el resultado (consumo de energía) ayuda a ver visualmente si existe una relación clara (una tendencia) o si los puntos están totalmente dispersos sin ningún patrón.

## Bloque 9: Comparar lo predicho contra lo realBloque 9: Comparar lo predicho contra lo realBloque 9: Comparar lo predicho contra lo real

```python
predictions = lm.predict(x)predictions = lm.predict(x)predictions = lm.predict(x)
plt.figure(figsize=(10, 7))plt.figure(figsize=(10, 7))plt.figure(figsize=(10, 7))
plt.title("Consumo de energía real vs. el predicho", fontsize=25)plt.title("Consumo de energía real vs. el predicho", fontsize=25)plt.title("Consumo de energía real vs. el predicho", fontsize=25)
plt.xlabel("Consumo de energía real", fontsize=18)plt.xlabel("Consumo de energía real", fontsize=18)plt.xlabel("Consumo de energía real", fontsize=18)
plt.ylabel("Consumo de energía predicho", fontsize=18)plt.ylabel("Consumo de energía predicho", fontsize=18)plt.ylabel("Consumo de energía predicho", fontsize=18)
plt.scatter(x=y, y=predictions)plt.scatter(x=y, y=predictions)plt.scatter(x=y, y=predictions)
```

> **Aprendí:** Que una forma sencilla de evaluar un modelo es comparar lo que predijo contra el valor real en un gráfico. Si los puntos forman una línea diagonal de 45°, significa que el modelo predice bastante bien.Aprendí:Aprendí: Que una forma sencilla de evaluar un modelo es comparar lo que predijo contra el valor real en un gráfico. Si los puntos forman una línea diagonal de 45°, significa que el modelo predice bastante bien. Que una forma sencilla de evaluar un modelo es comparar lo que predijo contra el valor real en un gráfico. Si los puntos forman una línea diagonal de 45°, significa que el modelo predice bastante bien.

## Bloque 10: Revisar los errores del modelo (residuos)Bloque 10: Revisar los errores del modelo (residuos)Bloque 10: Revisar los errores del modelo (residuos)

```python
plt.figure(figsize=(10, 7))plt.figure(figsize=(10, 7))plt.figure(figsize=(10, 7))
plt.title("Histograma de residuos para verificar la normalidad", fontsize=25)plt.title("Histograma de residuos para verificar la normalidad", fontsize=25)plt.title("Histograma de residuos para verificar la normalidad", fontsize=25)
sns.histplot((y - predictions), kde=True)sns.histplot((y - predictions), kde=True)sns.histplot((y - predictions), kde=True)
plt.figure(figsize=(10, 7))plt.figure(figsize=(10, 7))plt.figure(figsize=(10, 7))
plt.title("Valores residuales vs. predichos\n", fontsize=25)plt.title("Valores residuales vs. predichos\n", fontsize=25)plt.title("Valores residuales vs. predichos\n", fontsize=25)
plt.scatter(x=predictions, y=y - predictions)plt.scatter(x=predictions, y=y - predictions)plt.scatter(x=predictions, y=y - predictions)
```

> **Aprendí:** Que el "residuo" es la diferencia entre el valor real y el predicho, es decir, el error del modelo. El histograma me sirvió para comprobar que esos errores se comportan como una campana (lo cual es buena señal), y el segundo gráfico me sirvió para verificar que el error no cambia de forma rara según el valor predicho, sino que se mantiene parejo.Aprendí:Aprendí: Que el "residuo" es la diferencia entre el valor real y el predicho, es decir, el error del modelo. El histograma me sirvió para comprobar que esos errores se comportan como una campana (lo cual es buena señal), y el segundo gráfico me sirvió para verificar que el error no cambia de forma rara según el valor predicho, sino que se mantiene parejo. Que el "residuo" es la diferencia entre el valor real y el predicho, es decir, el error del modelo. El histograma me sirvió para comprobar que esos errores se comportan como una campana (lo cual es buena señal), y el segundo gráfico me sirvió para verificar que el error no cambia de forma rara según el valor predicho, sino que se mantiene parejo.

## Bloque 11: Crear datos inventados para poner a prueba los modelosBloque 11: Crear datos inventados para poner a prueba los modelosBloque 11: Crear datos inventados para poner a prueba los modelos

```python
from sklearn.datasets import make_regressionfrom sklearn.datasets import make_regressionfrom sklearn.datasets import make_regression
n_samples = 100n_samples = 100n_samples = 100
n_features = 6n_features = 6n_features = 6
n_informative = 3n_informative = 3n_informative = 3
X, y, coef = make_regression(n_samples=n_samples, n_features=n_features, n_informative=n_informative,X, y, coef = make_regression(n_samples=n_samples, n_features=n_features, n_informative=n_informative,X, y, coef = make_regression(n_samples=n_samples, n_features=n_features, n_informative=n_informative,
```

random_state=20, shuffle=False, noise=20, coef=True) random_state=20, shuffle=False, noise=20, coef=True) random_state=20, shuffle=False, noise=20, coef=True)

print(coef)print(coef)print(coef)

```python
df1 = pd.DataFrame(data=X, columns=['X' + str(i) for i in range(1, n_features + 1)])df1 = pd.DataFrame(data=X, columns=['X' + str(i) for i in range(1, n_features + 1)])df1 = pd.DataFrame(data=X, columns=['X' + str(i) for i in range(1, n_features + 1)])
df2 = pd.DataFrame(data=y, columns=['y'])df2 = pd.DataFrame(data=y, columns=['y'])df2 = pd.DataFrame(data=y, columns=['y'])
df = pd.concat([df1, df2], axis=1)df = pd.concat([df1, df2], axis=1)df = pd.concat([df1, df2], axis=1)
df.head(10)df.head(10)df.head(10)
```

> **Aprendí:** Que se pueden crear datos falsos a propósito, donde ya sabemos de antemano la respuesta correcta. En este caso se generaron 6 variables, pero solo 3 de ellas realmente influyen en el resultado. Esto sirve para comprobar si un modelo es capaz de "descubrir" por sí solo cuáles variables importan y cuáles no.Aprendí:Aprendí: Que se pueden crear datos falsos a propósito, donde ya sabemos de antemano la respuesta correcta. En este caso se generaron 6 variables, pero solo 3 de ellas realmente influyen en el resultado. Esto sirve para comprobar si un modelo es capaz de "descubrir" por sí solo cuáles variables importan y cuáles no. Que se pueden crear datos falsos a propósito, donde ya sabemos de antemano la respuesta correcta. En este caso se generaron 6 variables, pero solo 3 de ellas realmente influyen en el resultado. Esto sirve para comprobar si un modelo es capaz de "descubrir" por sí solo cuáles variables importan y cuáles no.

## Bloque 12: Graficar las variables inventadasBloque 12: Graficar las variables inventadasBloque 12: Graficar las variables inventadas

```python
with plt.style.context(('Solarize_Light2')):with plt.style.context(('Solarize_Light2')):with plt.style.context(('Solarize_Light2')):
for i, col in enumerate(df.columns[:-1]): for i, col in enumerate(df.columns[:-1]): for i, col in enumerate(df.columns[:-1]):
plt.figure(figsize=(6, 4)) plt.figure(figsize=(6, 4)) plt.figure(figsize=(6, 4))
plt.grid(True) plt.grid(True) plt.grid(True)
plt.xlabel('Feature:' + col, fontsize=12) plt.xlabel('Feature:' + col, fontsize=12) plt.xlabel('Feature:' + col, fontsize=12)
plt.ylabel('Output: y', fontsize=12) plt.ylabel('Output: y', fontsize=12) plt.ylabel('Output: y', fontsize=12)
plt.scatter(df[col], df['y'], c='red', s=50, alpha=0.6) plt.scatter(df[col], df['y'], c='red', s=50, alpha=0.6) plt.scatter(df[col], df['y'], c='red', s=50, alpha=0.6)
```

> **Aprendí:** Que graficando cada variable inventada contra el resultado se puede ver a simple vista cuáles muestran algún patrón (las que sí influyen) y cuáles se ven totalmente dispersas (las que no influyen).Aprendí:Aprendí: Que graficando cada variable inventada contra el resultado se puede ver a simple vista cuáles muestran algún patrón (las que sí influyen) y cuáles se ven totalmente dispersas (las que no influyen). Que graficando cada variable inventada contra el resultado se puede ver a simple vista cuáles muestran algún patrón (las que sí influyen) y cuáles se ven totalmente dispersas (las que no influyen).

## Bloque 13: Entrenar un árbol de decisiónBloque 13: Entrenar un árbol de decisiónBloque 13: Entrenar un árbol de decisión

```python
from sklearn import treefrom sklearn import treefrom sklearn import tree
from sklearn.model_selection import train_test_splitfrom sklearn.model_selection import train_test_splitfrom sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=123)X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=123)X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=123)
tree_model = tree.DecisionTreeRegressor(max_depth=5, random_state=10)tree_model = tree.DecisionTreeRegressor(max_depth=5, random_state=10)tree_model = tree.DecisionTreeRegressor(max_depth=5, random_state=10)
tree_model.fit(X_train, y_train)tree_model.fit(X_train, y_train)tree_model.fit(X_train, y_train)
from sklearn import metricsfrom sklearn import metricsfrom sklearn import metrics
test_pred = tree_model.predict(X_test)test_pred = tree_model.predict(X_test)test_pred = tree_model.predict(X_test)
plt.scatter(x=y_test, y=test_pred)plt.scatter(x=y_test, y=test_pred)plt.scatter(x=y_test, y=test_pred)
```

print("Mean square error (MSE):", metrics.mean_squared_error(y_test, test_pred))print("Mean square error (MSE):", metrics.mean_squared_error(y_test, test_pred))print("Mean square error (MSE):", metrics.mean_squared_error(y_test, test_pred))

> **Aprendí:** Que existe otro tipo de modelo, el árbol de decisión, que en vez de usar una fórmula lineal va haciendo preguntas tipo "sí o no" para llegar a una predicción. Lo entrené con los datos inventados, lo probé, y medí su error (MSE) para saber qué tan bien predice.Aprendí:Aprendí: Que existe otro tipo de modelo, el árbol de decisión, que en vez de usar una fórmula lineal va haciendo preguntas tipo "sí o no" para llegar a una predicción. Lo entrené con los datos inventados, lo probé, y medí su error (MSE) para saber qué tan bien predice. Que existe otro tipo de modelo, el árbol de decisión, que en vez de usar una fórmula lineal va haciendo preguntas tipo "sí o no" para llegar a una predicción. Lo entrené con los datos inventados, lo probé, y medí su error (MSE) para saber qué tan bien predice.

## Bloque 14: Ver qué tan importante fue cada variable para el árbolBloque 14: Ver qué tan importante fue cada variable para el árbolBloque 14: Ver qué tan importante fue cada variable para el árbol

```python
print("Importancia relativa de las características: ", tree_model.feature_importances_)print("Importancia relativa de las características: ", tree_model.feature_importances_)print("Importancia relativa de las características: ", tree_model.feature_importances_)
with plt.style.context('dark_background'):with plt.style.context('dark_background'):with plt.style.context('dark_background'):
plt.figure(figsize=(10, 7)) plt.figure(figsize=(10, 7)) plt.figure(figsize=(10, 7))
plt.grid(True) plt.grid(True) plt.grid(True)
plt.yticks(range(n_features, 0, -1), df.columns[:-1], fontsize=20) plt.yticks(range(n_features, 0, -1), df.columns[:-1], fontsize=20) plt.yticks(range(n_features, 0, -1), df.columns[:-1], fontsize=20)
plt.xlabel("Importancia relativa (normalizada) de los parámetros", fontsize=15) plt.xlabel("Importancia relativa (normalizada) de los parámetros", fontsize=15) plt.xlabel("Importancia relativa (normalizada) de los parámetros", fontsize=15)
plt.ylabel("Características\n", fontsize=20) plt.ylabel("Características\n", fontsize=20) plt.ylabel("Características\n", fontsize=20)
plt.barh(range(n_features, 0, -1), width=tree_model.feature_importances_, height=0.5) plt.barh(range(n_features, 0, -1), width=tree_model.feature_importances_, height=0.5) plt.barh(range(n_features, 0, -1), width=tree_model.feature_importances_, height=0.5)
```

imagen:imagen:imagen:

![Imagen del taller](imagenes/imagen_5.png)

> **Aprendí:** Que el árbol de decisión puede decirnos qué tanto usó cada variable para hacer sus predicciones. Al ver el gráfico de barras, pude comprobar que el modelo sí detectó correctamente que solo 3 variables eran importantes, justo las mismas que se habían marcado como "informativas" al crear los datos inventados.Aprendí:Aprendí: Que el árbol de decisión puede decirnos qué tanto usó cada variable para hacer sus predicciones. Al ver el gráfico de barras, pude comprobar que el modelo sí detectó correctamente que solo 3 variables eran importantes, justo las mismas que se habían marcado como "informativas" al crear los datos inventados. Que el árbol de decisión puede decirnos qué tanto usó cada variable para hacer sus predicciones. Al ver el gráfico de barras, pude comprobar que el modelo sí detectó correctamente que solo 3 variables eran importantes, justo las mismas que se habían marcado como "informativas" al crear los datos inventados.

## Bloque 15: Confirmar todo con un reporte estadísticoBloque 15: Confirmar todo con un reporte estadísticoBloque 15: Confirmar todo con un reporte estadístico

```python
import statsmodels.api as smimport statsmodels.api as smimport statsmodels.api as sm
```

Xs = sm.add_constant(X)Xs = sm.add_constant(X)Xs = sm.add_constant(X)

```python
stat_model = sm.OLS(y, Xs)stat_model = sm.OLS(y, Xs)stat_model = sm.OLS(y, Xs)
stat_result = stat_model.fit()stat_result = stat_model.fit()stat_result = stat_model.fit()
```

print(stat_result.summary())print(stat_result.summary())print(stat_result.summary())

> **Aprendí:** Que existe una librería (statsmodels) que da un reporte más detallado y formal de una regresión lineal, mostrando qué tan bien explica el modelo los datos (R²) y si cada variable es estadísticamente significativa o no. El reporte confirmó que solo 3 de las 6 variables inventadas eran realmente importantes, coincidiendo con lo visto en el árbol de decisión.Aprendí:Aprendí: Que existe una librería (statsmodels) que da un reporte más detallado y formal de una regresión lineal, mostrando qué tan bien explica el modelo los datos (R²) y si cada variable es estadísticamente significativa o no. El reporte confirmó que solo 3 de las 6 variables inventadas eran realmente importantes, coincidiendo con lo visto en el árbol de decisión. Que existe una librería (statsmodels) que da un reporte más detallado y formal de una regresión lineal, mostrando qué tan bien explica el modelo los datos (R²) y si cada variable es estadísticamente significativa o no. El reporte confirmó que solo 3 de las 6 variables inventadas eran realmente importantes, coincidiendo con lo visto en el árbol de decisión.

Conclusión general

En este taller aprendí a explorar datos, entrenar un modelo de regresión lineal, evaluar qué tan bien predice (con gráficos de residuos y comparaciones real vs. predicho), y a comprobar con datos inventados si un modelo (lineal o árbol de decisión) es capaz de identificar correctamente qué variables realmente influyen en un resultado.En este taller aprendí a explorar datos, entrenar un modelo de regresión lineal, evaluar qué tan bien predice (con gráficos de residuos y comparaciones real vs. predicho), y a comprobar con datos inventados si un modelo (lineal o árbol de decisión) es capaz de identificar correctamente qué variables realmente influyen en un resultado.En este taller aprendí a explorar datos, entrenar un modelo de regresión lineal, evaluar qué tan bien predice (con gráficos de residuos y comparaciones real vs. predicho), y a comprobar con datos inventados si un modelo (lineal o árbol de decisión) es capaz de identificar correctamente qué variables realmente influyen en un resultado.
