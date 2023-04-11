[![C/C++ CI](https://github.com/edpfacom/libfacom/actions/workflows/c-cpp.yml/badge.svg)](https://github.com/edpfacom/libfacom/actions/workflows/c-cpp.yml)

# para atualizar as infos com o repositorio do professor

1. baixe seu repositorio
```
git clone <seu repositorio.git>
```
2. adicione o repositorio do professor na sua área
```
cd <seu diretorio>
git remote add professor git@github.com:edpfacom/libfacom.git
git config pull.rebase false
git pull professor main
git push origin main
```
 pronto agora basta fazer o seu código

# para clonar o repositório

## preparação da chave de acesso
1. crie um repositório novo (repositories -> new )
2. crie a chave no seu terminal local 
```
ssh-keygen -t ed25519
```
3. adicione a chave na maquina local 
```
exec ssh-agent bash
ssh-add ~/.ssh/id_ed25519
```

4. copie a chave (cat ~/.ssh/id_ed25519.pub)
5. adicione a chave no repositório novo (settings -> Deploy keys -> add deploy key). Coloque permissão de `writing` como verdadeiro

6. verifique se a conexão está funcional
```
ssh git@github.com 
```
caso apareceça `Hi <SEU REPOSITORIO>! You've successfully authenticated, but GitHub does not provide shell access.` sua chave esta funcionando

## comandos para clonar o repositório
```
git clone --bare git@github.com:edpfacom/libfacom.git
cd libfacom.git
git push --mirror <URL DO SSH DO NOVO REPOSITORIO. TEM QUE COMECAR COM GIT>
cd ..
rm -Rf libfacom.git
```


pronto! agora vc tem um novo repositório clonado no git. Para baixar o repositório 

```
git clone <URL DO SSH DO NOVO REPOSITORIO. TEM QUE COMECAR COM GIT>
```

# comandos para compilar

```
aclocal
autoreconf --install
./configure
make
make check
```

# para incluir um novo algoritmo

1. crie o teste dentro de tests/test_nova_funcionalidade.c
2. adicione o arquivo criado em tests/Makefile.am (somente caso seja criado um novo arquivo de teste)
3. adicione as interfaces das funções em src/facom.h
4. crie o código fonte da funcionalidade em src/nova_funcionalidade.c
5. adicione o arquivo criado em src/Makefile.am (somente caso seja criado um novo arquivo com funcionalidade)


Pronto! agora basta dar um make e make check para verificar se o código está funcional

# para incluir uma nova função dentro de um algoritmo

1. altere o caso de teste em testes/test_heap.c
2. adicione as interfaces em src/facom.c
3. crie o codigo fonte da função em src/heap.c
4. make
5. make check



