# EP2
import random

baralho = ['A♥', '2♥', '3♥', '4♥', '5♥', '6♥', '7♥', '8♥', '9♥', '10♥', 'J♥', 'Q♥', 'K♥', 'A♠', '2♠', '3♠', '4♠', '5♠', '6♠', '7♠', '8♠', '9♠', '10♠', 'J♠', 'Q♠', 'K♠', 'A♦', '2♦', '3♦', '4♦', '5♦', '6♦', '7♦', '8♦', '9♦', '10♦', 'J♦', 'Q♦', 'K♦', 'A♣', '2♣', '3♣', '4♣', '5♣', '6♣', '7♣', '8♣', '9♣', '10♣', 'J♣', 'Q♣', 'K♣']

random.suffle(baralho)

def lista_movimentos_possiveis (baralho, indice):
    carta = baralho [indice]
    naipe = carta[len(carta)-1]
    valor = carta.replace(carta[len(carta)-1], '')
    if indice > 0:
        carta_anterior = baralho[indice-1]
        naipe_anterior = carta_anterior[len(carta_anterior)-1]
        valor_anterior = carta_anterior.replace(carta_anterior[len(carta_anterior)-1], '')
    else:       
        naipe_anterior = None
        valor_anterior = None
    if indice > 2:
        carta_3anterior = baralho[indice-3]
        naipe_3anterior = carta_3anterior[len(carta_3anterior)-1]
        valor_3anterior = carta_3anterior.replace(carta_3anterior[len(carta_3anterior)-1], '')
    else:
        naipe_3anterior = None
        valor_3anterior = None 
    retorno = []
    if valor == valor_anterior:
        retorno.append(1)
    elif naipe == naipe_anterior:
        retorno.append(1)
    if valor == valor_3anterior:
        retorno.append(3)
    elif naipe == naipe_3anterior:
        retorno.append(3)
    return retorno
    
def empilha(baralho, o, d):
    baralho[d] = baralho[o]
    baralho.pop(o)
    return baralho
    
def possui_movimentos_possiveis (baralho):
    indice = 0
    while indice < len(baralho):
        carta = baralho [indice]
        naipe = carta[len(carta)-1]
        valor = carta.replace(carta[len(carta)-1], '')
        if indice > 0:
            carta_anterior = baralho[indice-1]
            naipe_anterior = carta_anterior[len(carta_anterior)-1]
            valor_anterior = carta_anterior.replace(carta_anterior[len(carta_anterior)-1], '')
        else:
            naipe_anterior = None
            valor_anterior = None
        if indice > 2:
            carta_3anterior = baralho[indice-3]
            naipe_3anterior = carta_3anterior[len(carta_3anterior)-1]
            valor_3anterior = carta_3anterior.replace(carta_3anterior[len(carta_3anterior)-1], '')
        else:
            naipe_3anterior = None
            valor_3anterior = None
        indice += 1
        if valor == valor_anterior:
            return True
        elif naipe == naipe_anterior:
            return True
        elif valor == valor_3anterior:
            return True
        elif naipe == naipe_3anterior:
            return True
    else:
        return False  
        
while possui_movimentos_possiveis(baralho):
    print('O estado atual do baralho é:')
    for carta in baralho:
        print('{}: {}'.format(baralho.index(carta)+1, carta))
    indice +1 = int(input('escolha uma carta (digite um numero entre 1 e {}):'.format(len(baralho))))
    if len(lista_movimentos_possiveis(baralho, indice)) > 1:
        d = int(input('Sobre qual carta você que empilhar o {} ? \n 1:{} \n2: {} \nDigite o número da sua escolha:'.format(baralho[indice], baralho[indice-1], baralho[indice-3])))
    else:
        if lista_movimentos_possiveis(baralho, indice) == 1:
            d = 1
        else:
            d = 2
    if d = 1:
        baralho = empilha(baralho, indice, indice-1)
    if d = 3:
        baralho = empilha(baralho, indice, indice-3)
    else:
        print('A carta escolhida não pode ser movida')
if len(baralho) > 1:
    print('Parabéns, você ganhou!')
else:
    print('Que pena, tente outra vez')

