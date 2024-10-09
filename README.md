# Cibersegurança

## Curvas Elípticas e o ECDH (II.3)
### (A)
>Alice e Bob fixam a curva elíptica $$y^2 = x^3 + x + 4$$, módulo 11, com ponto base G = (2, 5) e chaves públicas respetivas HA = (3, 1) e HB = (9, 4), para realizar uma troca de chaves usando o protocolo EC-Diffie-Hellmann.

---
#### -- I. Prove que G, HA e HB são efetivamente pontos da curva elíptica.

Para verificar se um ponto (x, y) está na curva, calculamos ( $$y^2$$ ) e ( $$x^3 + x + 4$$ ) e verificamos se ambos são congruentes módulo 11.
- <u>Para ( G = (2, 5) ):</u>
> $$y^2 = 5^2 = 25 \equiv 3$$ mod $$11$$  
> $$x^3 + x + 4 = 2^3 + 2 + 4 = 14 \equiv 3$$ mod $$11$$  
> Como ( $$y^2 \equiv x^3 + x + 4$$ mod $$11$$ )   G está na curva.

- <u>Para ( H<sub>A</sub> = (3, 1) ):</u>
> $$y^2 = 1^2 = 1 \equiv 1$$ mod $$11$$  
> $$x^3 + x + 4 = 3^3 + 3 + 4 = 34 \equiv 1$$ mod $$11$$  
> Como ( $$y^2 \equiv x^3 + x + 4$$ mod $$11$$ )   H<sub>A</sub> está na curva.

- <u>Para ( H<sub>B</sub> = (9, 4) ):</u>
> $$y^2 = 4^2 = 16 \equiv 5$$ mod $$11$$  
> $$x^3 + x + 4 = 9^3 + 9 + 4 = 742 \equiv 5$$ mod $$11$$  
> Como ( $$y^2 \equiv x^3 + x + 4$$ mod $$11$$ )   H<sub>B</sub> está na curva.

---
#### -- II.Assuma que 5HB é o simétrico, na curva elíptica, de M = (0, 9). Se dA = 5 é a chave privada da Alice, indique a chave secreta partilhada K por Alice e Bob.

Dado que $$5H_B$$ é o simétrico de $$M = (0, 9)$$ na curva elíptica, e $$d_A = 5$$ é a chave privada de Alice, podemos calcular a chave secreta compartilhada K.

Em uma curva elíptica, o simétrico de um ponto (x, y) é (x, -y). Então:

$$5H_B = (0, -9) \equiv (0, 2) (mod 11)$$

A chave secreta compartilhada K é calculada por Alice como: $$K = d_A * H_B = 5 * H_B$$

Já sabemos que $$5H_B = (0, 2)$$, então:

$$K = 5H_B = (0, 2)$$

Portanto, a chave secreta compartilhada $$K$$ por Alice e Bob é $$(0, 2)$$.

---

### (B)
>  Alice e Bob fixam a curva elíptica  $$y^2 = x^3 + 5$$, módulo 11, com ponto base G = (5, 8) e chaves públicas respetivas H<sub>A</sub> = (10, 9) e H<sub>B</sub> = (0, 7), para realizar uma troca de chaves usando o protocolo EC-Diffie-Hellmann.

#### --I. Prove que G, HA e HB são efetivamente pontos da curva elíptica

- <u>Para ( G = (5, 8) ): </u>
>$$y^2 = 8^2 = 64 \equiv 9$$ mod $$11$$   
>$$x^3 + 5 = 5^3 + 5 = 130 \equiv 9$$ mod $$11$$   
>Como  $$y^2 \equiv x^3 + 5 mod 11$$ , ( G ) está na curva.

- <u>Para ( H<sub>A</sub> = (10, 9) ):</u>
>$$y^2 = 9^2 = 81 \equiv 4$$ mod 11$$   
>$$x^3 + 5 = 10^3 + 5 = 1005 \equiv 4$$ mod $$11$$   
> Como  $$y^2 \equiv x^3 + 5$$ mod $$11$$ , ( H<sub>A</sub> ) está na curva.

- <u>Para ( H<sub>B</sub>= (0, 7) ): </u>
>$$y^2 = 7^2 = 49 \equiv 5$$ mod $$11 $$  
>$$x^3 + 5 = 0^3 + 5 = 5 \equiv 5$$ mod $$11 $$   
>Como  $$y^2 \equiv x^3 + 5$$ mod $$11$$ , ( H<sub>B</sub> ) está na curva.

#### --II. Indique a equação da reta tangente à curva elíptica em HA e verifique que dita reta interseta à curva nos pontos HA e M = (6, 1).

Primeiro, diferenciamos a equação da curva elíptica para obter a derivada da
curva num ponto (x, y). A derivada da curva elíptica é dada por:

$$\frac{dx}{dy} (y^2) = \frac{dx}{dy}(x^3 + 5) \equiv \frac{3x^2}{2y} $$
Para encontrar a equação da reta tangente à curva elíptica em H<sub>A</sub> = (10, 9),  calculamos a derivada da curva nesse ponto:
$$\frac{3x^2}{2y} = \frac{3 * 10^2}{2*9} = \frac{300}{18} = \frac{50}{3} mod 11$$

Para encontrar $$\frac{50}{3} mod 11$$, precisamos de encontrar o inverso de 3 modulo 11, que é o número $$b$$ tal que $$3b≡1(mod11)$$.
Calculando o inverso de 3 módulo 11:   
$$3 * 4 = 12 \equiv 1$$ mod $$11$$  
Portanto, o inverso de 3 módulo 11 é 4.  

Agora, podemos calcular a inclinação da reta tangente à curva elíptica em H<sub>A</sub>:  
$$m = 50 * 4 = 200 = 2 mod 11$$

A equação da reta tangente à curva elíptica em H<sub>A</sub> é dada por:  
$$r:(x,y) \equiv y-y_0 = m(x-x_0)$$  
$$r:(x,y) \equiv y-9 = 2(x-10)$$  
$$r:(x,y) \equiv y = 2x - 11$$  
$$r:(x,y) \equiv y = 2x$$ mod $$11$$  

Para verificar que a reta tangente à curva elíptica em H<sub>A</sub> intersecta a curva nos pontos H<sub>A</sub>
e M = (6, 1), substituímos as coordenadas de H<sub>A</sub> e M na equação da reta tangente:  
- Para H<sub>A</sub> = (10, 9):
- $$9 = 2 * 10$$ mod $$11$$
- $$9 = 20$$ mod $$11$$
  - $$9 = 9$$ mod $$11$$
    - A equação da reta tangente passa por H<sub>A</sub>.
- Para M = (6, 1):
- $$1 = 2 * 6$$ mod $$11$$
- $$1 = 12$$ mod $$11$$
  - $$1 = 1$$ mod $$11$$
    - A equação da reta tangente passa por M.


---

#### --III. Suponha que a chave privada do Bob é dB = 2. Qual é a chave secreta partilhada K por Alice e Bob?


- $$d_B = 2$$
- n é de ordem G
- 2 é raíz primitiva de 11
- $$d_B$$ pertence ao intervalo [2, n-2]  
  Bob calcula a sua chave pública:  
  $$H_B = d_B * G = 2 * (5, 8) = (5, 8) + (5, 8) = (10, 16) = (10, 5)$$  
  (10, 5) é a chave pública de Bob.

Alice escolhe o seu d_A (pertencente ao intervalo [2, n-2]) e calcula a sua chave pública:
- $$d_A = 7$$  
  $$H_A = d_A * G = 7 * (5, 8) = (35, 56) = (2,1) mod 11$$   
  (2, 1) é a chave pública de Alice.

Bob e Alice trocam as suas chaves públicas e calculam a chave secreta partilhada K:  
Bob calcula a chave secreta partilhada:  
$$K = d_B * H_A = 2 * (2, 1) = (4, 2)$$

Alice calcula a chave secreta partilhada:   
$$K = d_A * H_B = 7 * (10, 5) = (70, 35) = (4, 2)$$

Portanto, a chave secreta partilhada K por Alice e Bob é (4, 2).
---
### (C)
> Considere os seguintes parâmetros de domínio EC:
• p = 97		• G = (14, 18)
• a = 13		• n = 11
• b = 17		• h = 9

#### -- Indique a ordem da curva elíptica. A curva elíptica é cíclica? o ponto G é um gerador da curva?

A ordem da curva elíptica (N) é dada por n * h = 11 * 9 = 99

Uma curva elíptica é cíclica se a sua ordem for um número primo.
Neste caso, a ordem é 99 (não primo). Portanto, esta curva elíptica não é cíclica.

Para que G seja um gerador da curva, a sua ordem (n) deve ser igual à ordem da curva.
Neste caso, n (11) é diferente da ordem da curva (99), então G não é um gerador da curva, mas é um subgrupo de ordem 11.

---

### (D)
>Considere os seguintes parâmetros de domínio EC:
• p = 31		• G = (2, 5)
• a = 7			• n = 27
• b = 3			• h = 1

#### -- Indique a ordem da curva elíptica. A curva elíptica é cíclica? o ponto G é um gerador da curva?

A ordem da curva elíptica (N) é dada por n * h = 27 * 1 = 27

A ordem da curva é 27, que não é um número primo. Portanto, esta curva elíptica também não é cíclica.

Neste caso, a ordem de G (n = 27) é igual à ordem da curva (27). Isso significa que G é um gerador da curva elíptica.

