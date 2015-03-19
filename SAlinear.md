# Masulli
#SAprova2

clear all
clc

x0=[0.76541,1.76]';

x_corrente=x0; %è la x*
t0=0.06; %   Valore iniziale di t0:valore abbastanza alto, ad esempio stimato
             % come la massima differenza tra i valori delle funzioni obiettivo di
             % due soluzioni nello stesso intorno
n=randi([1:2],1);       
x_ran=x_corrente+0.1*rand(2,1);
x_fin=x0;
t=t0;
tfinale=0.01;
iter=0;
k=0;
dk=5;
itermax=25;
pr=rand(2,1);
b=rand(20,1);   %determino un valore casuale di alfa appartenente al range [0.8, 0.99]
b2=zeros(20,1);
esp=zeros(2,1);
p=0;

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





       
while (iter < itermax)
     k=k+1;
   

     fx_ran=myfuns(x_ran);
     fx0=myfuns(x0);
     final=myfuns(x_fin);
     m1=myfuns(x_ran(:,1));
     m2=myfuns(x_corrente(:,1));      
     esp=exp(-(m1-m2)/t);

    if ((fx_ran(1,1) <= fx0(1,1)))&&((fx_ran(2,1)) <= fx0(2,1))
        x_corrente=x_ran;
        
        iter=0;
%          if x_ran(1,1)<x_ran(2,1)
%              x_ran(1,1)= x_ran(1,1)+rand(1,1);
%          end
         if ((fx_ran(1,1) < final(1,1)))&&((fx_ran(2,1)) < final(2,1))
            x_fin=x_ran;
         end
    else

        if (le(pr(1,1),esp(1,1)))&&(le(pr(2,1),esp(2,1)))
            x_corrente=x_ran;
%             t=alfa*t;
%             k=0;
            iter=0;
        else
            iter=iter+1;
        end
    end
    if (k==dk)
            t=alfa*t;
            k=0;
            iter=iter+1;
    end  
    

    
    
if t<=tfinale
        break;        
end
% n=randi([1:2],1);       
x_ran=x_ran+0.01*rand(2,1);

    
end

            
            
  

x_fin=x_ran

funzioneFINALE=myfuns(x_fin)

     
            
            
%questo dovrebbere essere il quanto
