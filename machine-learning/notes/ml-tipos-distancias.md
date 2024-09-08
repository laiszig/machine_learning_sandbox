### Distancia Euclidiana
Medir distancia entre dois pontos em um espaco multidimensional. Calcula a linha reta (ou a menor distancia) entre dois pontos.
- **`Aplicacao no k-NN`**: o algoritmo identifica os k vizinhos mais proximos de um ponto de consulta.
- **`Geometria`**: em um espaco 2D, ela define regioes circulares ao redor de um ponto de consulta.
- **`Uso pratico`**: util quando todas as dimensoes tem escalas semelhantes e a relacao entre elas e linear. Sensivel a diferencas proporcionais em todas as dimencoes.

### Distancia de Manhattan
Calcula medindo a soma das distancias absolutas ao longo de cada dimensao. 
- **`Geometria`**: a distancia de Manhattan forma regioes de vizinhanca em forma de losangos ou diamantes 
- **`Uso pratico`**: util em cenarios onde se movem apenas em direcoes ortogonais (como em um sistema de grade, por isso o nome "taxista", ja que a distancia e medida como se fosse percorrida por ruas retas).

### Distancia supremum (ou distancia de Chebyshev)
Definida como a maior diferenca absoluta entre as coordenadas correspondentes dos dois pontos. Usada em cenarios onde as variacoes em uma unica dimensao dominam a decisao de proximidade. Nesse caso, o k-NN considera apenas a maior diferenca em uma dimensao entre os pontos, em vez de somar todas as distancias entre as dimensoes.
- **`Robustez`**: A distancia supremum e sensivel apenas a maior variacao entre os pontos, ignorando variacoes menores em outras dimensoes.
- **`Geometria`**: Em um espaco 2D, a distancia supremum define regioes quadradas, em contraste com a distancia Euclidiana (circular) e Manhattan (diamante).

### Quando usar cada distancia
- **`Distancia Euclidiana`**:
Quando todas as dimensoes (ou atributos) dos dados tem escalas semelhantes e sao continuas.
Quando a relacao entre os atributos e linear e voce quer capturar a menor distancia direta entre dois pontos.
Em espacos de baixa ou moderada dimensionalidade, onde os dados nao sao muito esparsos.

- **`Distancia de Manhattan`**:
Quando as variaveis ou dimensoes tem escalas diferentes ou quando as mudancas ao longo de cada dimensao sao independentes entre si.
Para problemas onde o movimento se da de forma ortogonal, como em grades ou sistemas urbanos (da o nome "distancia do taxista").
Quando os atributos sao discretos e as diferencas absolutas sao mais relevantes do que a menor linha reta.

- **`Distancia Supremum`**:
Quando o que importa e a maior diferenca em qualquer uma das dimensoes, sem considerar a soma das distancias nas outras.
Em problemas onde voce precisa monitorar a variacao maxima em uma unica dimensao, como controle de qualidade ou monitoramento de sistemas.
Quando a prioridade e dada ao atributo com a maior discrepancia, como em certos problemas de logistica ou controle.