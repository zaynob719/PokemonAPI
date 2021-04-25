# PokemonAPI
Top Trump-like game -  Multi user Pokemon card game 

import random 
import requests

def random_opponent():
  random_opponentID = random.randint(1, 151) 
  print('Your random pokemon is: {}.'.format(random_opponentID))
  url = 'https://pokeapi.co/api/v2/pokemon/{}/'.format(random_opponentID)
  response = requests.get(url)
  pokemon = response.json()

  return {
      'name': pokemon['name'],
      'id': pokemon['id'],
      'height': pokemon['height'],
      'weight': pokemon['weight'],
    }


score1=0
score2=0
round=0

for rounds in range(3):
    round = round + 1
    print(' ')
    
    print('This is round {}.'.format(round))
    result1 = random_opponent()
    print(result1)
    stat1 = input('Player1: Choose a stat: (height, weight, id) ')  

    result2 = random_opponent()
    print(result2)
    stat2 = input('Player2: Choose a stat: (height, weight, id) ')
    
    if result1[stat1] > result2[stat2]:
      score1 = score1 + 1
      print('Player1 wins. Your score is {}'.format(score1))
    elif result1[stat1] < result2[stat2]:
      score2 = score2 + 1
      print('Player2 wins. Your score is {}'.format(score2))
    else:
      print('Draw.')

if score1 > score2:
  print('Player 1 wins.')
else:
  print('Player 2 wins')
