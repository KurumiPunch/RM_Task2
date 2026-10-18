### NMOS低侧开关
- 信号发生器输出低电平时,Vgs=0v,NMOS截止,R1两端无电压
- 信号发生器输出高电平时,Vgs=3.3v,NMOS导通,R1两端电压为24v-Q2处压降
----
### PMOS高侧开关
- 信号发生器输出低电平时,Q3 Vbe=0v,NPN截止,Q4的base极被上拉到24V,Q4的Veb=0v,Q4截止,Q1的gate极与R8分压被下拉,Vgs<阈值,PMOS导通,R2两端电压为24V-PMOS导通压降
- 信号发生器输出高电平时,Q3 Vbe>阈值,NPN导通,Q4的base极与R5分压被下拉,使
  Q4的Veb>阈值,PNP导通,Q1的gate极被上拉到24V,Vgs=0v,PMOS截止,R2两端
  电压为0V