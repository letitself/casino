import random
import numpy as np


global coef_win

coef_win = {
    '10': 1,
    'J': 2,
    'Q': 3,
    'K': 4,
    'A': 5
}


def win_or_lose(lines):
  
    if (lines[0][0] == lines[1][1] and lines[0][0] == lines[2][2]) and (lines[2][0] == lines[1][1] and lines[2][0] == lines[0][2]):
      win.append(lines[1][1])
      win.append(lines[1][1])
    elif (lines[0][0] == lines[1][1] and lines[0][0] == lines[2][2]):
      win.append(lines[0][0])
    elif lines[2][0] == lines[1][1] and lines[2][0] == lines[0][2]:
      win.append(lines[2][0])
    else:
      pass

    for elem in lines:
      if elem[0] == elem[1] and elem[0] == elem[2]:
        win.append(elem[0])
      else:
        pass

    return win


def pay_out(symbols, bet, balance):
    balance -= bet
    symbols = dict((i, symbols.count(i)) for i in symbols)
    if not symbols:
        return balance
    else:
        for i in symbols.keys():
          balance += bet*int(symbols[i])*coef_win[i]
        return balance


balance_ = int(input('Enter your balance: '))
bet_ = int(input('Enter your bet: '))


print('Description of existing commands: \n y - next spin \n n - stop the game \n c - change the bet')
while balance_ > 0:
    if bet_ <= 0:
      print('Your bet can not be 0 $ or less, please enter correct bet')
      bet_ = int(input('Enter your new bet: '))
    else:
      values = ['10', 'J', 'Q', 'K', 'A']
      line1 = []
      win = []
      for i in range(3):
          line1.append(random.choices(values, weights=[0.4, 0.3, 0.2, 0.075, 0.025], k=3))
      yorn = input('Are you ready to play?(y/n/c) ')
      if yorn == 'y':
          win_or_lose(line1)
          balance_ = pay_out(win, bet_, balance_)
          print("-----------------------\nBalance: {} $, Bet: {} $\n-----------------------\n{}\n-----------------------".format(balance_, bet_, np.array(line1)))
      elif yorn == 'n':
          print('-----------------------\nThank you for the game, see you next time.\nYour balance: {}$\n-----------------------'.format(balance_))
          break
      elif bet_ <= 0 or yorn == 'c':
          bet_ = int(input('Enter your new bet: '))
      else:
          print('Incorrect answer, print existing command please(y - yes, n - no, c - change bet)')       
else:
  print('Refill your balance or leave')
