- import random

from forca import jogar


def jogar_adivinhacao():
    print('Bem vindo ao jogo de Adivinhação!')


numero_secreto = random.randrange(1, 101)
total_de_tentativas = 0
pontos = 1000

print('Qual nivel de difilculdade?', numero_secreto)
print('(1) facil (2) medio (3) dificil')

nivel = int(input('define o nivel:'))

if nivel == 1:
    total_de_tentativas = 20
elif nivel == 2:
    total_de_tentativas = 10
else:
    total_de_tentativas = 5

print(numero_secreto)

for rodada in range(1, total_de_tentativas + 1):
    print('tentativa', rodada, 'de', total_de_tentativas)
    chute_str = input('digite o seu número entre 1 e 100:')
    print('voce digitou ', chute_str)
    chute = int(chute_str)

    if chute < 1 or chute > 100:
        print('Voce deve digitar um número entre 1 e 100')
        continue

    acertou = chute == numero_secreto
    maior = chute > numero_secreto
    menor = chute < numero_secreto

    if acertou:
        print('Parabens! voce acertou e fez {} pontos! .format(pontos)')
        break
    else:
        if maior:
            print('voce errou! O seu numero foi maior do que o numero secreto.')
        elif menor:
            print('voce errou! O seu numero foi menor do que o numero secreto.')
            pontos_perdidos = abs(numero_secreto - chute)
            pontos = pontos - pontos_perdidos

    rodada = rodada + 1

print('fim de jogo')

if (__name__ == '__main__'):
    jogar()
