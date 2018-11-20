# RECUREPAR SENHA VMware ESXI 6.5

Você que trabalha na área já se deparou com a situação parecida. 

Isso aconteceu comigo a poucos dias, no servidor está instalado o VMware ESXI 6.5, e para fazer o reparo no sistema da máquina virtual que tinha parado precisava acessar o "VMware", só que a empresa não possuía a senha, pesquisando encontrei basicamente que a solução era reinstalar o `ESXI`, mais corria o risco de perder as máquinas. Nas pesquisas que fiz geralmente o pessoal falava que não tinha como recupera ou quebrar a senha, mas encontrei algumas dicas e a solução que obtive êxito foi a seguinte: 

As ferramentas que usei foi um pendrive bootavel do Ubuntu 18.04 LTS.

Nas pesquisas que fiz fiquei sabendo que os arquivos fundamentais para o sistema da VMware, tais como: /bin, /usr, ficam "compactados" em uma partição especifica do VMware.

Vamos a ação.

Coloque o Ubuntu rodar como experimental, abra o terminal com o comando `crt+alt+t`, acesse o root com o comando 

```shell
$ sudo su
```

