> Preisach模型
> 2017-08-06
> Cheney
# 代码
    close all;clear all;clc;% clear the workplace
    [a,b]=meshgrid(-0.5:1/N:0.5,0.5:-1/N:-0.5);
    x=-0.5:0.01:0.5;
    y=zeros(1,length(x));
    x_old=-0.6;
    counter=1;
    w=1/(1000*(1000-1))/2;
    %the voltage raise
    for i=1:1:length(x)，
        for j=1:N-1
            for k=1:N-j
                if x(i)>=b(j,k)
                    temp=1;
                elseif x(i)<=a(j,k)
                     temp=-1;
                else
                    if x_old<=a(j,k)
                        temp=-1;
                    elseif x_old>=b(j,k)
                        temp=1;
                    end
                end
                y(counter)=y(counter)+temp*w;
            end
        end
        counter=counter+1;
    end
    x=0.5:-0.01:-0.5;
    y=zeros(1,length(x));
    x_old=0.6;
    counter=1;
    %the voltage decrease
    for i=1:1:length(x)
        for j=1:N-1
            for k=1:N-j
                if x(i)>=b(j,k)
                    temp=1;
                elseif x(i)<=a(j,k)
                     temp=-1;
                else
                    if x_old<=a(j,k)
                        temp=-1;
                    elseif x_old>=b(j,k)
                        temp=1;
                    end
                end
                y(counter)=y(counter)+temp*w;
            end
        end
        counter=counter+1;
    end
    figure
    plot([x1 x],[y1 y],'r');
    axis([-0.5 0.5 -0.25 0.25]);
