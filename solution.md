# HW01

## Дедлайн 23:59 14.09

### Валерий Васильевич Мацкевич

#### Задание 1

Привести грамматику для языка палиндромов `{ w w^r | w \in {0, 1}* }`. Привести дерево вывода какой-нибудь строки длины не меньше 7 в предложенной грамматике. 

#### Решение

Грамматика:
```
G = <V_T, V_N, P, S>

V_T = {0; 1}
V_N = {W}
P = {S -> 0S0 | 1S1 | ε}
```

Дерево вывода для `11000011`:
```
      1   1   0   0
       \   \   \   \
root->  S - S - S - S - ε
       /   /   /   /
      1   1   0   0
```

#### Задание 2

Описать язык, порождаемый грамматикой 
  ``` 
  S -> aSA | aT 
  TA -> bTa
  aA -> Aa
  T -> ba
  ```
  
#### Решение

```
S ->^{n} ... -> a^n S A^n -> a^n b Ta A^{n - 1} -> a^{n + 1} b TA a A^{n - 2} -> 
-> a^{n + 1} b^2 T a^2 A^{n - 2} -> ... -> a^{n + 1} b^{n} T a^{n} -> a^{n + 1} b^{n + 1} a^{n + 1}
```
  
Таким образом, язык выглядит как `a^k b^k a^k` для любых натуральных `k`.
  
#### Задание 3

Изучить спецификацию синтаксиса вашего второго самого любимого языка, в отчете привести ссылку на документ, который вы изучали, и отметить 3 новые для вас особенности синтаксиса. 

#### Решение

GLSL — OpenGL Shading Language 😳💀

1. [input- и output- блоки для аггрегации данных между различными построениями шейдеров](https://www.khronos.org/opengl/wiki/Interface_Block_(GLSL)#Input_and_output):
```
// Vertex Shader
out VertexData
{
  vec3 color;
  vec2 texCoord;
} outData;

// Geometry Shader
in VertexData
{
  vec3 color;
  vec2 texCoord;
} inData[];
```

2. [Существование атомарного счётчика](https://www.khronos.org/opengl/wiki/Atomic_Counter)

```
atomic_uint
```

3. [Порядок квалификаторов](https://www.khronos.org/opengl/wiki/Type_Qualifier_(GLSL)#Qualifier_order)

```
invariant-qualifier interpolation-qualifier layout-qualifier other-storage-qualifier precision-qualifier
```
