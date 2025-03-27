# computer_renju_c
make renju c program play with computer

You can play gomoku with computer to execute renju.c file. 
I will do optimized later to make gomoku online game to make an apk make by unity.

This is my first game which made in SNU_programmin practice class assignment.
Different with class assignment is playing with computer.
Now i will show my computer algorithm which in my renju.c

my algorithm ::
need :
25x25 board that get int number
25x25 board dir_1
25x25 board dir_1 defend
25x25 board dir_2
25x25 board dir_2 attack
5 integer 25x25 board

do :
1. first add in board dir_1 defend
   for(check stone line = 4, check stone line = 1, --check stone line)
     for(check all of 25x25 points)
       1 point :
         for(4 dir that dir=0,1,2,3)     // dir=0 dir=1 dir=2 dir=3 mean(1,1) (1,0) (0,1) (1,-1) 4 direction
           if(board dir_1 % 2^(dir+1) < 2^dir && player stone == check stone line)
   // if board dir_1 is 1101(2) this means i add dir0,dir2,dir3 add in board dir_1 defend
   // see in example if dir = 0 board dir_1 % 2^1 = 1 (when 1101(2)) It isnt certify if condition. becuz 1 < 1
   // but when you see 1100(2) example It certify if condition. 0 < 1
   // so this mean if I calculate one direction like dir=2 it isnt need add another line of count.
   // lets see example
   // i add . O O O 300 points in . board
   // but in my algorithm . O O also add points less than 300 in . board
   // it made computer foolish, so i add this dir_1 dir_2 board to check is it already add it. lets see other algorithm
             board dir_1 += defend points //it is depend by check stone line
             board dir_1 += 2^dir
           end
         end
       end

2. second add in board dir_2 attack // It is maybe same as 1 only different player stone to my stone
   for(check stone line = 4,check stone line = 1,--check stone line)
     for(check all 25x25 points)
       1 point :
         for(4 dir, dir=0,1,2,3)
           if(board dir_2 % 2^(dir+1) < 2^dir && Computer stone == check stone line)
