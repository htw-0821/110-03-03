# 110-03-03
test

            if(cardempty(s-1))
                cout<<"         ";
            else if(!cardempty(s-1))
                cout<<"<  "<<(s<10 ? "0" :"")<<s<<"  > ";
            cout<<(x==cardsetX-1 ? "\n":"");
        }
    }
}
//是否配對成功
bool Game::match(int a,int b){
    if(ranks[cardset[a-1] % 13]==ranks[cardset[b-1] % 13]){//數字一樣
        if(level){//簡單(true)或困難(false)
            numOfPair++;
            cardset[a-1]=52;
            cardset[b-1]=52;
            return true;
        }
        else if((cardset[a-1]/13<2 && cardset[b-1]/13<2) || (cardset[a-1]/13>1 && cardset[b-1]/13>1)){//顏色相同
            numOfPair++;
            cardset[a-1]=52;
            cardset[b-1]=52;
            return true;
        }
        else return false;    
    }
    else return false;
}
char Game::grade(){
    if(turned<numOfCard*1.5)
        return 'S';
    else if (turned<numOfCard*1.9)
        return 'A';
    else if (turned<numOfCard*2.1)
        return 'B';
    else if (turned<numOfCard*2.4)
        return 'C';
    else
        return 'D';
}

//全部配對成功
void Game::end(){
    cout<<"\033[2J\033[1;1H"<<endl<<"    Mission Complete \n    You Got a "<<grade()<<" Star\n";
    backHome();
}

int main()
{
    Game a;
    a.home();
    
}
