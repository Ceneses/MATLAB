> 画分形树
> 2017-08-07
> Cheney
# 代码
   function [x,y]=frac_tree(x0,y0,v)
   %This is a Frac_tree function
   %x0 is init(x)；
   %y0 is init(y)；
   %v is a rand number
   %maker：Cheney
   %date：2016/8/3
   if nargin==0
      v=10000;x0=0;y0=0;
   end
   if nargin==1
      v=x0;x0=0;y0=0;
   end
   if nargin==2
       v=10000;
   end
   if nargin>3
       error('你输入的参数个数有误！输入参数可以是0个1个2个或着3个！');
   end
   if (abs(x0-round(x0))>eps||x0<0)||(abs(y0-round(y0))>eps||y0<0)
       error('输入参数x0,y0必须为非负整数！');
   end
   if abs(v-round(v))>eps||v<=0
       error('输入参数v必须为正整数！');
   end
   v=rand(v,1);
   N=length(v);
   x=[x0;zeros(N-1,1)];y=[y0;zeros(N-1,1)];
   for k=2:N
       vv=v(k);
       if vv<0.05,y(k)=0.5*y(k-1);
       elseif vv<0.45
           x(k)=0.42*(x(k-1)-y(k-1));y(k)=0.2+0.42*(x(k-1)+y(k-1));
       elseif vv<0.85
           x(k)=0.42*(x(k-1)+y(k-1));y(k)=0.2-0.42*(x(k-1)-y(k-1));
       else
           x(k)=0.1*x(k-1);y(k)=0.1*y(k-1)+0.2;
       end
   end
   h=plot(x,y,'.g');axis('square',[-0.26 0.26 0 0.52]);
   set(h,'MarkerSize',4);
   legend('分形树/Frac_tree');title('本函数由恒成立制作/Made by Cheney');disp('分形树如图所示：');
    
