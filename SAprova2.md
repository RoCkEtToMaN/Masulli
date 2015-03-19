# Masulli
#SAprova2
clear all
clc

x0=[0.5 0.5]';

x_corrente=x0; %è la x*
t0=2.0632; %   Valore iniziale di t0:valore abbastanza alto, ad esempio stimato
             % come la massima differenza tra i valori delle funzioni obiettivo di
             % due soluzioni nello stesso intorno
x_ran=x_corrente-0.1.*rand(2,1);
x_fin=zeros(2,1);
t=t0;
tfinale=0.001;
iter=1;
k=0;
dk=10;
itermax=20;
pr=rand(2,1);
b=rand(20,1);   %determino un valore casuale di alfa appartenente al range [0.8, 0.99]
b2=zeros(20,1);

for i=1:size(b,1)
%     b_new=b;
    if (b(i,1) > 0.88978)
%         fprintf('numeri di valori che rispettano la condizione: %d\n',i)
%         b2=b(i,1);
        b2(i,1)=b(i,1);
       
    end
    b2
        
end
    
c=unique(b2)

r=size(c,1);
alfa=zeros(r-1,1);

alfa([1:r-1],1)=c([2:r],1)
alfa=min(alfa)



% for i=1:size(b,1)
%     if (b(i,1) > 0.8)
%         [r c]=size(b);
%         a=zeros(r,1);
%         for j=1:r
%             a=b(r,1);
%         end
%     end
% end
            
%     if (b(i,1) >0.8) && (b(i,1) <= 0.99)

       
while (iter < itermax)
    k=k+1;
    if le(myfuns(x_ran),myfuns(x_corrente))
        x_corrente=x_ran;
        %x_fin=x_corrente;
        iter=0;
        x_ran=x_ran+0.1.*rand(2,1);
    elseif myfuns(x_ran) > myfuns(x_corrente)
            %x_fin=x_ran;
            esp=exp(-(myfuns(x_ran)-myfuns(x_corrente))/t);
            if (le(pr(1,1),esp(1,1)))||(le(pr(2,1),esp(2,1)))
                x_corrente=x_ran;
                x_ran=x_ran+0.1.*rand(2,1);
                iter=0;
            else
                 iter=iter+1;
%                  x_ran=x_ran-0.1.*rand(2,1);

            end
            
            
%     else
        %x_ran=rand(2,1);
%       iter=iter+1;
%       x_ran=rand(2,1)-[0.005;0.005];
    end
%     if (pr==exp(-(myfuns(x_ran)-myfuns(x_corrente))/t))
if k==dk
    t=alfa*t;
    k=0;
%     x_corrente=[0.5 0.5]';
%     x_ran=x_corrente+0.1.*rand(2,1);
end
if t<=tfinale
    break;
end
end
            
            
%     else %(sum(myfuns(x_ran)) > sum(myfuns(x_corrente)))
%             %x_fin=x_corrente;
%             if (le(pr,exp(-(myfuns(x_ran)-myfuns(x_corrente))/t)))
%                 x_corrente=x_ran;
%                 iter=0;
%             else
%                 x_ran=rand(2,1);
%                 iter=iter+1;
   % end
%      if k == dk
%          t=alfa*t;
%          k=0;
%     end
%     
% end
%    
%  



     
            
            
