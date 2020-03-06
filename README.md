import os
totalmoves=["",'_','_','_','_','_','_','_','_','_']
def showscreen():
    print('\n',totalmoves[7], "|",totalmoves[8], "|",totalmoves[9], "\n",
          totalmoves[4], "|",totalmoves[5], "|",totalmoves[6], "\n",
          totalmoves[1], "|",totalmoves[2], "|",totalmoves[3], "\n",)

class player :
    
    def __init__(self, mark,nname):
        self.name=nname
        self.mark=mark
        self.playermoves=[self.mark,'_','_','_','_','_','_','_','_','_']

    def place (self,x):
        self.playermoves[x]=self.mark
        return x

    def wincheck(self):
        if (self.playermoves[1]==self.playermoves[2]==self.playermoves[3]==self.mark or
            self.playermoves[4]==self.playermoves[5]==self.playermoves[6]==self.mark or
            self.playermoves[7]==self.playermoves[8]==self.playermoves[9]==self.mark or
            self.playermoves[1]==self.playermoves[4]==self.playermoves[7]==self.mark or
            self.playermoves[2]==self.playermoves[5]==self.playermoves[8]==self.mark or
            self.playermoves[3]==self.playermoves[6]==self.playermoves[9]==self.mark or
            self.playermoves[1]==self.playermoves[5]==self.playermoves[9]==self.mark or
            self.playermoves[7]==self.playermoves[5]==self.playermoves[3]==self.mark):
            print ('>>>>>>>>>>>>>>>>>>>stop>>>>>>>>>>>>>>>>>>>>>',self.name, " won!")
            return True



def main():

    while True:
        os.system('cls')
        totalmoves=["",'_','_','_','_','_','_','_','_','_']
        print('-------------welcomeeeee toooooo dizzzzney landddddd-------------',"\n",
              "HERE IS YOUR GAME SCREEN:")
        showscreen()
        name1=input('player1 what is your name? ')
        name2=input('player2 what is your name? ')
        
        m=input(name1+'... what is your mark? X or O? ')
        if m.lower()=='x':
            m="X"
            n="O"
        elif m.lower()=="o":
            m="O"
            n="X"
        else:
            print('i said only x or o!!!!! you aparently cannot play this game... GET OUT OF HERE. SECURITY!!!')
            break

            
        print('ok.... ','\n',
              'then ',name1,' is: ',m,'\n',
              'and ',name2,' is:  ',n)
        player1=player(m, name1)
        player2=player(n, name2)
        i=0
        while True:
            showscreen()
            
            if i%2==0:
                x=int(input(name1+' make your move(enter from 1-9).you are '+m+' : '))
                if totalmoves[x]=="_":
                    os.system('cls')
                    player1.place(x)
                    totalmoves[x]=m
                    result=player1.wincheck()
                    if result==True:
                        break
                else:
                    print('wrong move... try again '+player1.name)
                    continue
            else:
                x=int(input(name2+' make your move(enter from 1-9).you are '+n+' : '))
                if totalmoves[x]=="_":
                    os.system('cls')
                    player2.place(x)
                    totalmoves[x]=n
                    result=player2.wincheck()
                    if result==True:
                        break
                else:
                    print('wrong move...try again '+player2.name)
                    continue
            i+=1
        showscreen()
        if result==True:
            playagain=input('Game Over. Do you wanna play again?? ')
            if playagain.lower()=='yes':
                continue
            else:
                break
        else:
            print('tie you are equally good')
            playagain=input('Game Over. Do you wanna play again?? ')
            if playagain.lower()=='yes':
                continue
            else:
                break



if __name__=="__main__":
    main()


    
