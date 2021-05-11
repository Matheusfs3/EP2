# EP2
def cria_baralho ():
    lista_e = ['2♠', '3♠', '4♠', '5♠', '6♠', '7♠', '8♠', '9♠', '10♠', 'J♠', 'Q♠', 'K♠', 'A♠']
    lista_c = ['2♥', '3♥', '4♥', '5♥', '6♥', '7♥', '8♥', '9♥', '10♥', 'J♥', 'Q♥', 'K♥', 'A♥']
    lista_o = ['2♦', '3♦', '4♦', '5♦', '6♦', '7♦', '8♦', '9♦', '10♦', 'J♦', 'Q♦', 'K♦', 'A♦']
    lista_p = ['2♣', '3♣', '4♣', '5♣', '6♣', '7♣', '8♣', '9♣', '10♣', 'J♣', 'Q♣', 'K♣', 'A♣']
    baralho = lista_c + lista_e + lista_o + lista_p
    return baralho
    
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
