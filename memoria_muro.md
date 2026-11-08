# MEMORIA DE CÁLCULO - MURO DE CONCRETO REFORZADO
NTC para Diseño y Construcción de Estructuras de Concreto, CDMX 2023

## 1. Datos de entrada
- Geometría: Hm = 350 cm, Lm = 670 cm, tm = 30 cm
- Elemento extremo izquierdo: hc2 = 70 cm, bc2 = 70 cm
- Elemento extremo derecho: hc1 = 70 cm, bc1 = 70 cm
- Materiales: f'c = 350 kg/cm2, fy = 4200 kg/cm2, Es = 2.1e+06 kg/cm2
- Cargas últimas: Pu = 620 t, Mu = 8990 t*m, Vu = 241 t
- Factores: FR flexión = 0.9, FR cortante = 0.75, εcu = 0.003

## 2. Propiedades de los materiales y de la sección
- β1 = 0.800  (β1 = 0.85 si f'c <= 300 kg/cm2; β1 = 1.05 - f'c/1400 >= 0.65 si f'c > 300)
- Ec = 261,916 kg/cm2  (Tabla 2.2.1, §2.2.8, concreto clase 1A, agregado calizo)
- Longitud del alma Lw = Lm - hc1 - hc2 = 530 cm
- Ag = 25,700 cm2;  centroide desde el borde izquierdo xg = 335.0 cm

## 3. Verificaciones geométricas (NTC-Concreto 2023, cap. 6.5, §6.5.3)
- Pu = 620.0 t <= 0.3 f'c Ag = 2698.5 t: el muro se diseña a flexión como viga en voladizo; L/t <= 70.
- Lm/tm = 22.3 <= 70 -> CUMPLE
- tm = 30 cm >= 14 cm (espesor mínimo muros de carga) -> CUMPLE
- Hm/Lm = 0.52: longitud mínima de concentración del refuerzo de borde = 132.5 cm
  hc1 = 70 cm < 132.5 cm -> REVISAR
  hc2 = 70 cm < 132.5 cm -> REVISAR

## 4. Flexocompresión - Paso 1: método T y C (acero concentrado al centro de los elementos extremos)
Equilibrio de Pu y Mu respecto al centroide de la sección, con las fuerzas en los centroides de los extremos:
  Fc = (Mu + Pu*at)/(ac + at);  Ft = Pu - Fc   (+ compresión, - tensión)
  Elemento en tensión:     As = T/(FR fy)
  Elemento en compresión:  As = (C/FR - 0.85 f'c Ae)/(fy - 0.85 f'c)
- Caso 1 (compresión en extremo derecho): ac = 300.0 cm, at = 300.0 cm
    Fc = 1808.3 t (compresión), Ft = -1188.3 t (tensión)
    As requerida: extremo der = 141.32 cm2;  extremo izq = 314.37 cm2
- Caso 2 (compresión en extremo izquierdo): ac = 300.0 cm, at = 300.0 cm
    Fc = 1808.3 t (compresión), Ft = -1188.3 t (tensión)
    As requerida: extremo izq = 141.32 cm2;  extremo der = 314.37 cm2

- Envolvente de ambos casos y cuantía mínima 20/fy = 0.0048: As_izq = 314.37 cm2, As_der = 314.37 cm2

## 5. Flexocompresión - Paso 2: bloque de esfuerzos, εcu = 0.003 y profundidad del eje neutro c
Con a = β1 c, concreto 0.85 f'c sobre el área comprimida (alma + elemento extremo), acero en el centro de los
elementos extremos con fs = Es*εs <= fy. Se resuelve c por bisección de  Pn(c) = Pu/FR  y se verifica FR*Mn >= Mu.
- Caso 1: As comp = 314.37 cm2, As tens = 314.37 cm2
    c = 68.28 cm,  a = β1 c = 54.62 cm,  εt = 0.0249
    Pn = 688.9 t (Pu/FR = 688.9 t),  FR*Mn = 9068.7 t*m >= Mu = 8990.0 t*m -> CUMPLE
- Caso 2: As comp = 314.37 cm2, As tens = 314.37 cm2
    c = 68.28 cm,  a = β1 c = 54.62 cm,  εt = 0.0249
    Pn = 688.9 t (Pu/FR = 688.9 t),  FR*Mn = 9068.7 t*m >= Mu = 8990.0 t*m -> CUMPLE

## 6. Acero vertical y transversal en los elementos extremos
- Extremo izquierdo (70 x 70 cm): As requerida = 314.37 cm2 -> 40 #10 (As = 317.60 cm2, ρ = 0.0648)
    Ash/s (ramas // longitud) = 0.6400 cm2/cm;  Ash/s (ramas // espesor) = 0.6400 cm2/cm
    Separación máx. contra pandeo: min(8 db = 25.4, 24 db_est = 22.8, tm/2 = 15.0) = 15.0 cm
- Extremo derecho (70 x 70 cm): As requerida = 314.37 cm2 -> 40 #10 (As = 317.60 cm2, ρ = 0.0648)
    Ash/s (ramas // longitud) = 0.6400 cm2/cm;  Ash/s (ramas // espesor) = 0.6400 cm2/cm
    Separación máx. contra pandeo: min(8 db = 25.4, 24 db_est = 22.8, tm/2 = 15.0) = 15.0 cm
  (Ash/s >= max[0.3 (Ag/Ac - 1) f'c/fyh ; 0.12 f'c/fyh] * h'',  h'' = dimensión del núcleo c-a-c de estribos)

## 7. Revisión por cortante (NTC-Concreto 2023, cap. 6.5/7.5/8.5)
- Acv = tm*Lm = 20,100 cm2;  Hm/Lm = 0.52 -> αc = 0.800
- VcR = FR αc λ √f'c Acv = 225.6 t
- Límite por aplastamiento del puntal: Vu <= 2 FR √f'c Acv = 564.1 t -> CUMPLE
- ρh requerida = (Vu/FR - αc λ √f'c Acv)/(fy Acv) = 0.00024;  ρh adoptada = max(·, 0.0025) = 0.00250
- ρv >= 0.0025 + 0.5 (2.5 - Hm/Lm)(ρh - 0.0025) = 0.00250
- VR = FR (αc λ √f'c + ρh fy) Acv = 383.9 t >= Vu = 241.0 t -> CUMPLE
- Malla en el alma (2 capa(s)): vertical #3 @ 17.5 cm (ρv = 0.00270, s máx = 45 cm); horizontal #3 @ 17.5 cm (ρh = 0.00270, s máx = 45 cm)
- Acero vertical en el alma: 43.01 cm2 totales en Lw = 530 cm (8.11 cm2/m)
- Acero horizontal en el alma: 0.0811 cm2/cm = 8.11 cm2/m de altura (28.4 cm2 en Hm = 350 cm)

## 8. Resumen de resultados
- Caso 1 (compresión derecha): c = 68.28 cm; εt = 0.0249; FR*Mn = 9068.7 t*m
- Caso 2 (compresión izquierda): c = 68.28 cm; εt = 0.0249; FR*Mn = 9068.7 t*m
- Extremo izquierdo: As vertical = 314.37 cm2 (40 #10); Ash/s = 0.6400 / 0.6400 cm2/cm
- Extremo derecho: As vertical = 314.37 cm2 (40 #10); Ash/s = 0.6400 / 0.6400 cm2/cm
- Alma: As vertical = 43.01 cm2 (#3 @ 17.5); As horizontal = 8.11 cm2/m (#3 @ 17.5)

### Avisos
- hc1 menor que la longitud de borde sugerida.
- hc2 menor que la longitud de borde sugerida.
- Extremo izq: ρ = 0.065 > 0.06; aumentar el elemento extremo.
- Extremo der: ρ = 0.065 > 0.06; aumentar el elemento extremo.

### Notas
- Las fórmulas se basan en las imágenes aportadas (β1, Tabla 2.2.1) y en el resumen de la NTC-Concreto 2023 de
  la tesis BUAP 2025 (muros). Confirmar numeración de apartados, cuantías mínimas del cap. 6.5/7.5/8.5, el límite
  de aplastamiento del puntal y el coeficiente de confinamiento contra el texto oficial antes de usar en proyecto.
- El acero distribuido del alma no se consideró en la flexión (criterio conservador).