#### Explicación técnica

Para implementar nuestros ecosistemas, usamos como plantilla el ejemplo del repositorio [gym_examples](https://github.com/Farama-Foundation/gym-examples). Esta decisión nos facilitó la reutilización de los elementos gráficos de un entorno renderizado mediante pygame, permitiéndonos dedicar nuestra atención principalmente a la implementación de la lógica de cada ambiente.

Los entornos construidos son:

**PushBox**

- El entorno más sencillo y base para los demás.
- Sus características incluyen:
  - En su estado inicial, se dispone un *agente* y una caja o *target* de manera aleatoria.
  - El agente tiene cuatro acciones posibles: moverse hacia arriba, abajo, izquierda y derecha.
  - Si el agente se encuentra en una posición adyacente al target y se mueve en su dirección, lo empujará (es decir, el agente podrá mover la caja).
  - La caja permanece fija en el entorno a menos que el agente la desplace.
  - El objetivo del agente es empujar la caja hasta una región definida del entorno.
  - La política del agente es binaria y dispersa. Esto quiere decir que el agente obtendrá 0 como recompensa en cada paso que no consiga el objetivo, y obtendrá 1 cuando lo cumpla.

**PushBoxRand**

- Presenta las mismas características que `PushBoxBaseEnv` excepto por la característica 4. En este caso, el entorno cambia la caja de forma aleatoria cada cierta cantidad de pasos (definida por el tamaño del entorno). Adicionalmente, añade a la característica 2 una quinta acción: permanecer en la posición actual.

**PushBoxRandPol1**

- Comparte las características de `PushBoxRand` pero modifica las recompensas que recibe el agente en cada paso. Este entorno en particular recompensa los movimientos con 2 puntos, y penaliza quedarse en la misma posición con -1 puntos. Brinda 100 puntos al cumplir el objetivo.

**PushBoxRandPol2**

- Comparte las características de `PushBoxRand` pero modifica las recompensas que recibe el agente en cada paso. Este entorno en particular penaliza los desplazamientos con -1 puntos, y recompensa quedarse en la misma posición con 2 puntos. Brinda 100 puntos al cumplir el objetivo.

#### Modo de uso

Puedes ver el proyecto completo, así como el uso de los entornos, importando el archivo `.ipynb` en **Google Colaboratory**. Para conocer las instrucciones de uso local, deberás revisar los pasos realizados en el archivo anterior.

#### Notas adicionales

Debido a la falta de una forma práctica de enlazar commits desde el README de un repositorio, a continuación, se dejan los identificadores de cada commit involucrado en la creación de cada entorno, para poder ver qué modificaciones se hicieron a partir del fork original:

**PushBox (Entorno base)**

- Actualización en las importaciones, los módulos y los requerimientos del módulo: 03437e0
- Cambios gráficos: 224e778, 58b5b5a, 2fee43f, 926fb90
- Modificación en la lógica del método reset: a0220b6, 5366444
- Modificación en la lógica del método step: 509e425, 5366444

**PushBoxRand**

- Declaración en el módulo y creación del entorno: 10bb95a
- Cambios gráficos: 7e50435
- Cambio en la lógica del método step y en el inicializador del entorno: e998be4, 88f92d5, d647df3
