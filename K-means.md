> K-means方法
> 2017-08-06
> Cheney
# 代码
    clear;
    data1=rand(30,2)*10;
    data2=rand(30,2)*10;
    data3=rand(30,2)*10;
    Data=[data1;data2;data3];
    Data_start=Data;
    start=[2,2;5,5;8,8];
    start1=start(1,:);
    start2=start(2,:);
    start3=start(3,:);
    Idx=zeros(length(Data),1);
    for k=1:10000
       for m=1:length(Data)
           distance1=norm((Data(m,:)-start1));
           distance2=norm((Data(m,:)-start2));
           distance3=norm((Data(m,:)-start3));
           distance=[distance1;distance2;distance3];
           [~,id]=min(distance);
           Idx(m)=id;
       end
       start1=mean(Data(Idx==1,:));
       start2=mean(Data(Idx==2,:));
       start3=mean(Data(Idx==3,:));
       start=[start1;start2;start3];
    end
    figure(1);
    hold on;
    plot(data1(:,1),data1(:,2),'r.');
    plot(data2(:,1),data2(:,2),'g.');
    plot(data3(:,1),data3(:,2),'b.');
    plot([2,2;5,5;8,8],'ko');
    hold off;
    figure(2);
    hold on;
    D1=Data(Idx==1,:);
    D2=Data(Idx==2,:);
    D3=Data(Idx==3,:);
    plot(D1(:,1),D1(:,2),'r.');
    plot(D2(:,1),D2(:,2),'g.');
    plot(D3(:,1),D3(:,2),'b.');
    plot(start(:,1),start(:,2),'ko');
    hold off;
