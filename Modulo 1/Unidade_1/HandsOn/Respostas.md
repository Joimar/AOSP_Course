## Configurando o ambiente

### Instalando a Ferramenta Repo

```
mkdir ~/bin

curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo

chmod a+x ~/bin/repo

Adicione o caminho do Repo ao PATH:

export PATH=~/bin:$PATH
```

O comando `curl` é uma ferramenta para transferência de dados, a url que vem seguida dele é o endereço para download da ferramenta Repo. O operador `>` indica para qual diretório o que foi baixado deve ir.
O comando `chmod a+x` é responsável por tornar executável o arquivo em `~/bin/repo`. Em seguida `export PATH=~/bin:$PATH` adiciona Repo às variáveis de ambiente, tornando possível ao shell do Linux operar os comandos e recursos da ferramenta Repo.
## Baixando o AOSP

Crie uma pasta para o código fonte:

```
mkdir aosp
cd aosp
```

Android tem diversas versões, para determinar qual você quer baixar e buildar vá em https://source.android.com/docs/setup/reference/build-numbers?hl=pt-br

Ao abrir a página vá até a tabela de **Builds e Tags**. Ao achar a versão do Android que deseja, use a sua respectiva **tag** no comando que você verá em seguida. 

![[Captura de tela de 2024-10-26 11-12-27.png]]

Uma vez dentro da pasta "aosp", utilize o **Repo** para inicializar o repositório com a branch (versão do Android) que você quer:

```
repo init -u https://android.googlesource.com/platform/manifest -b [tag-do-android]
```

No meu caso caso uma tag referente a uma versão do Android 12:

```
repo init -u https://android.googlesource.com/platform/manifest -b android-12.1.0_r27
```


Uma vez iniciado o repositório, vamos baixar o código fonte:

```
repo sync
```


Para otimizar o tempo você pode usar:

```
repo sync -j8
```

Nesse comando sinalizamos ao **repo** para fazer a sincronização será feita usando threads.

- a flag `-j`,é usada para indicar o número máximo de threads;
- o número que aparece a seguir representa o número de threads, no caso será 8.

Ao utilizar `-j8`, você está dizendo ao comando `repo sync` para utilizar 8 processos em paralelo para realizar a sincronização. Isso pode acelerar significativamente o processo de download, especialmente em máquinas com múltiplos núcleos de processador.


## Variáveis de Ambiente

Você deve setar o caminho para o sdk Android instalado no seu computador e suas ferramentas, como abaixo:

```
export ANDROID_HOME=/home/joimar/Android/Sdk
export PATH=$ANDROID_HOME/platform-tools:$ANDROID_HOME/tools:$PATH
```

## Build

Uma vez que o ambiente esteja todo pronto, o passo seguinte foi efetuar o *build*. O primeiro passo a ser dado é usar o comando `source` para executar os comandos dentro do script `envsetup.sh` dentro do diretório "build" no AOSP *source tree*.

```
source build/envsetup.sh
```

O conteúdo do `envsetup.sh` trata-se basicamente de uma série de comandos do *shell* Linux que vão configurar diversas variáveis de ambiente necessárias para buildar o AOSP, como por exemplo *paths* para recursos tais como ferramentas, bibliotecas e o código fonte Android.

Após a execução do script `envsetup.sh`, já tenho acesso à comandos aos comandos `lunch`, `make`, entre outros que iremos abordar mais adiante. 

O comando `lunch` é usado em seguida ao `source`. Esse comando é usado para identificar para qual tipo de dispositivo específico você gerar uma *build* do Android. 

```
lunch
```

Se o o comando for dado sem nenhum parâmetro, ele listará todas os *targets* disponíveis para diferentes tipos de dispositivos, como mostrado na imagem abaixo.

![[Captura de tela de 2024-11-24 21-06-47.png]]

A opção usada por mim foi a número 73, `sdk_car_x86_64-userdebug`, que uma *build* feita para funcionar em emulador. Então usei o comando `lunch` como descrito a seguir:

```
lunch 73
```

O próximo passo trata-se do processo de *build* propriamente dito. Com o ambiente devidamente configurado com o comando `source build/envsetup.sh`,o comando make torna-se capaz de "perceber" o *Android build system*, sendo assim possível compilar códigos e gerar imagens com ele.

```
make
```

Uma possibilidade de uso de parâmeros para o comando é `make -j[número_de_threads]`. A lógica é a mesma usada no comando `repo -j8`. No caso, eu fiz o processo de *build* ser dividido em 32 *threads*, exatamente como descrito abaixo:

```
make -j32
```

Uma vez com todo o projeto AOSP pronto para ser testado, eu apenas executei o comando para iniciar o emulador.

```
emulator
```

