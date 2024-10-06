program SquidGame;

uses crt, graph, venbuton, mouse2, dos;
const lat=40;dx=30;dy=30;

var x,y,nrinc,ales,ales2,nr,gd, gm, xi, yi,i,j,cod:integer;
    sem:boolean;
    b:array[1..4,1..10] of button;
    a:array[1..3,1..2] of button;
    s:string;

{----------------------------------------------------------------------------}

procedure init;
begin
     gd:=detect;
     initgraph(gd,gm,'');
     setbkcolor(9);
end;

{----------------------------------------------------------------------------}

procedure drum;
var i,x,y,y1,t,y2:integer;
    s:string;
begin
     x:=20;
     y:=100;
     y1:=350;
     y2:=250;
     for i:=1 to 10  do
         begin
              t:=random(2);
              str(t,s);
              buton(b[1,i], x,y,x+lat,y+lat,yellow,14,s);
              t:=(1+t) mod 2;
              str(t,s);
              buton(b[2,i], x,y1,x+lat,y1+lat,yellow,14,s);
              x:=x+60;
         end;
end;

{----------------------------------------------------------------------------}

procedure meniu;
begin
     mouseon;
     buton(a[1,1],87,getmaxy-24,197,getmaxy-2,7,1,'EXIT');
     pune_buton(a[1,1]);
     buton(a[2,1],430,getmaxy-24,540,getmaxy-2,7,1,'RETRY');
     pune_buton(a[2,1]);
end;

{----------------------------------------------------------------------------}

procedure palpai(c:integer);
var i,j,cul:integer;
begin
     for i:=1 to 20 do
         begin
              cul:=1+random(15);
              b[1,c].bcolor:=cul;
              b[1,c].tcolor:=cul;
              pune_buton(b[1,c]);
              b[2,c].bcolor:=cul;
              b[2,c].tcolor:=cul;
              pune_buton(b[2,c]);
              delay(20);
         end;
     b[1,c].bcolor:=14;
     b[1,c].tcolor:=14;
     pune_buton(b[1,c]);
     b[2,c].bcolor:=14;
     b[2,c].tcolor:=14;
     pune_buton(b[2,c]);
end;

{----------------------------------------------------------------------------}

procedure linie;
begin
     setcolor(7);
     {sus}
     bar(20,100,570,102);
     bar(20,137,570,139);

     {jos}
     bar(20,350,570,352);
     bar(20,387,570,389);
end;

{-----------------------------PROGRAM PRINCIPAL------------------------------}

begin
     init; randomize;
     drum;meniu;mouseon;
     maximizemousewindow;
     nrinc:=9;
     x:=getmaxx div 2-110;
     y:=getmaxy div 2-20;
     STR(nrinc,s);
     linie;
     s:='Number of Attempts : '+s;
     buton(b[3,1],x,y,x+200,y+50,7,1,s);
     repeat
          pune_buton(a[1,1]); pune_buton(a[2,1]);
          for i:=1 to 10 do
             begin
                pune_buton(b[1,i]);
                pune_buton(b[2,i]);
             end;
          nr:=1;
          settextstyle(10,0,4);
          setcolor(yellow);
          outtextxy(172,0,'Squid Game');
          repeat
              palpai(nr);
              sem:=false;
              repeat
                  if buton_apasat(a[1,1]) then halt;
                  if buton_apasat(a[2,1]) then
                     begin
                          nr:=1;
                          nrinc:=9;
                          palpai(nr);
                          STR(nrinc,s);
                          s:='Number of Attempts : '+s;
                          buton(b[3,1],x,y,x+200,y+50,7,1,s);
                      end;
                  for i:=1 to 2 do
                      if buton_apasat(b[i,nr]) then
                         begin
                              sem:=true;
                              ales:=i;
                           end;
              until sem;
              if b[ales,nr].t='1' then nr:=nr+1
              else
                  begin
                       NRINC:=NRINC-1;
                       STR(nrinc,s);
                       s:='Number of Attempts : '+s;
                       buton(b[3,1],x,y,x+200,y+50,7,1,s);
                       nr:=1;
                  end;
          until (nr>10) or (nr=1);
          mouseon;
     until (nr>10) or (nrinc=0);


{-------------------------------ecrane final---------------------------------}

     if (nr>2) and (nrinc>0) then
        begin
             cleardevice;
             mouseoff;
             cleardevice;
             setbkcolor(2);
             repeat
                   settextstyle(10,0,4);
                   setcolor(1);
                   outtextxy(85,150,'CONGRATULATIONS');
                   delay(250);
                   settextstyle(1,0,3);
                   setcolor(white);
                   outtextxy(160,350,'Press any key to continue');
             until keypressed;
        end
     else if nrinc=0 then
         begin
              mouseoff;
              cleardevice;
              setbkcolor(red);
              repeat
                    mouseoff;
                    settextstyle(10,0,4);
                    setcolor(14);
                    outtextxy(225,150,'RETRY');
                    delay(250);
                    settextstyle(1,0,2);
                    setcolor(white);
                    outtextxy(172,350,'Press any key to continue');
              until keypressed;
         end;

end.