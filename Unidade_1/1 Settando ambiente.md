## Instalando a Ferramenta Repo

```
mkdir ~/bin

curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo

chmod a+x ~/bin/repo

Adicione o caminho do Repo ao PATH:

export PATH=~/bin:$PATH
```


## Baixando o AOSP

Crie uma pasta para o código fonte:

mkdir aosp
cd aosp

Android tem diversas versões, para determinar qual você quer baixar e buildar vá em https://source.android.com/docs/setup/reference/build-numbers?hl=pt-br

Ao abrir a página vá até a tabela de **Builds e Tags**. Ao achar a versão do Android que deseja, use a sua respectiva **tag** no comando que você verá em seguida. 

![[Captura de tela de 2024-10-26 11-12-27.png]]

Uma vez dentro da pasta "aosp", utilize o **Repo** para inicializar o repositório com a branch (versão do Android) que você quer:

```
repo init -u https://android.googlesource.com/platform/manifest -b [tag-do-android]
```

No meu exemplo com a minha versão do Android:

```
repo init -u https://android.googlesource.com/platform/manifest -b android-12.1.0_r27
```

Em segui deve-se fazer baixar o código fonte usando **Repo**:

```
repo sync
```

Para otimizar o tempo você pode usar:

```
repo sync -j8
```

Onde o número representa quantos repositórios podem ser sincronizados ao mesmo tempo

## Variáveis de Ambiente

Você deve setar o caminho para o sdk Android  e suas ferramentas, como abaixo

_____________________________
```
export ANDROID_HOME=/home/joimar/Android/Sdk
export PATH=$ANDROID_HOME/platform-tools:$ANDROID_HOME/tools:$PATH
```

______________________________________________________________

