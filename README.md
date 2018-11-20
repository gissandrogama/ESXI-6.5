# RECUREPAR SENHA VMware ESXI 6.5

Você que trabalha na área já se deparou com a situação parecida. 

Isso aconteceu comigo a poucos dias, no servidor está instalado o VMware ESXI 6.5, e para fazer o reparo no sistema da máquina virtual que tinha parado precisava acessar o "VMware", só que a empresa não possuía a senha, pesquisando encontrei basicamente que a solução era reinstalar o `ESXI`, mais corria o risco de perder as máquinas. Nas pesquisas que fiz geralmente o pessoal falava que não tinha como recupera ou quebrar a senha, mas encontrei algumas dicas e a solução que obtive êxito foi a seguinte: 

As ferramentas que usei foi um pendrive bootavel do Ubuntu 18.04 LTS.

Nas pesquisas que fiz fiquei sabendo que os arquivos fundamentais para o sistema da VMware, tais como: /bin, /usr, ficam "compactados" em uma partição específica do VMware.

Vamos a ação!

Coloque o Ubuntu para rodar como experimental, abra o terminal com o comando `crt+alt+t`, acesse o root com o comando. 

```shell
$ sudo su
```

liste as partições;

```shell
fdisk -l
```

Agora terá que montar a partição `sda5` no `/mnt`, nessa partição vamos encontrar o arquivo `state.gtz` e ao descompactar esse arquivo, iremos ter um `/etc` e dentro dele o `shadow` que é onde faremos nossas alterações.

### Montar a partição no `/mnt`.

```shell
$ mount /dev/sda5 /mnt
$ cd /mnt  
```

**Copiar o arquivo `state.tgz` para um diretoiro de sua preferencia, no meu caso copiei em `/root`.**

```shell
$ cp state.tgz /root
$ cd /root
```

Agora decompactar o arquivo que acabamos de copiar, os comandos abaixo foram os melhores que achei para fazer a decompactação.

### comando para descompactar

```shell
$ gzip -d state.tgz
$ tar xvf state.tar
```

Ao descompactar o arquivo `state.tar` ira aparecer no seu diretorio um arquivo chamado `local.tgz`, descompacte o mesmo com os comando usado anteriormente.

```shell
$ gzip -d local.tgz
$ tar xvf local.tar
```

Agora se executar o comando `ls -l`, irá verificar que apareceu o diretorio `/etc`, 





