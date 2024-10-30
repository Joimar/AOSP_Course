compilação (JIT -_Just In Time_)

rodar arquivos de bytecode **.dex** (Dalvik _Executable_), que são versões compactadas dos arquivos **.class** do Java

O projeto do Android não se baseia na linguagem Java para o isolamento entre aplicativos e o sistema, mas, em vez disso, assume que cada aplicação está executando em seu próprio processo Linux com o seu próprio ambiente Dalvik, assim como o _system_server_ e outras partes centrais da plataforma que são escritos em Java.

O uso de processos do _Linux_ e segurança simplifica muito o ambiente de Dalvik, tendo em vista que ele não é mais responsável por aqueles aspectos críticos da estabilidade e robustez do sistema.

Misturar processos e a linguagem Java dessa maneira introduz alguns desafios. Levantar um novo ambiente de linguagem Java pode ser demorado, mesmo em _hardwares_ móveis modernos. A solução para esse problema é o **daemon nativo zygote.**

O Dalvik introduziu o conceito de Zygote, um processo que pré-carrega bibliotecas comuns e configurações que podem ser compartilhadas entre diferentes aplicativos, economizando memória e melhorando o desempenho geral. (Isso já não era comum no Linux?)

O fork() desempenha um papel importante na otimização

![[Pasted image 20241029084323.png]]

A partir do **Android 5.0 Lollipop**, a **Android Runtime (ART)** substituiu a Dalvik VM como a máquina virtual padrão

# ART

compilação antecipada AOT (Ahead Of Time), código dos aplicativos é compilado no momento da instalação, resultando em um código nativo otimizado que pode ser executado diretamente pela CPU do dispositivo

No Android 8.0 e versões mais recentes, a ART TI (ART - Tooling Interface) expõe alguns componentes internos em tempo de execução e permite que desenvolvedores influenciem o comportamento de execução dos aplicativos. Isso pode ser usado para implementar ferramentas de desempenho de última geração fornecidas para implementar agentes nativos em outras plataformas.

-Revisar as medidas de segurança para o ART TI-

Ao comparar Dalvik e ART, as principais diferenças estão na forma como o código é compilado e executado.

# Dalvik vs ART

**Dalvik**: na Dalvik, a compilação ocorre durante a execução do aplicativo (JIT), o que pode aumentar o tempo de inicialização de aplicativos e exigir mais processamento durante a execução. Isso resulta em maior uso de CPU e bateria.

**ART**: na ART, a compilação ocorre no momento da instalação do aplicativo (AOT), o que significa que o aplicativo já está otimizado para a execução, resultando em tempos de inicialização mais rápidos e menor uso de CPU durante a execução.

**Dalvik**: a Dalvik era eficiente para dispositivos com memória limitada e CPUs mais lentas, mas o seu uso de JIT introduzia algum impacto de desempenho, especialmente em processos que envolviam muitas traduções de _bytecode._

**ART**: a ART melhora significativamente o desempenho geral dos aplicativos. Como o código já está pré-compilado, o tempo de inicialização dos aplicativos é menor, e há menos necessidade de usar a CPU para compilar o código durante a execução, resultando em uma experiência de usuário mais fluida.

**Dalvik**: a Dalvik era projetada para ser eficiente no uso de memória, mas como a compilação era feita dinamicamente, o uso de memória aumentava durante a execução dos aplicativos.

**ART**: a ART consome mais espaço de armazenamento, pois o código é pré-compilado e armazenado no dispositivo, mas esse _trade-off_ resulta em uma execução mais eficiente, com menor consumo de memória RAM durante a execução dos aplicativos.
(A substituição já ocorreu? O fato de ART demandar maior armazenamento por conta do código pré-compilado, ao se tornar um problema, o Dalvik assume de alguma forma?)

**Dalvik**: como a Dalvik compila o código dinamicamente, os tempos de instalação de aplicativos eram rápidos.

**ART**: com a ART, os tempos de instalação são mais longos, pois o código do aplicativo precisa ser compilado para código nativo durante a instalação. No entanto, esse aumento no tempo de instalação é compensado por um melhor desempenho durante a execução do aplicativo.

**Dalvik**: devido ao uso de JIT, a Dalvik exigia mais CPU durante a execução de aplicativos, o que resultava em maior consumo de energia, especialmente em aplicativos que faziam uso intenso de CPU.

**ART**: como a ART já pré-compila o código, a CPU não precisa trabalhar tanto durante a execução do aplicativo, resultando em um menor consumo de bateria.

# JIT e AOT

Se um aplicativo for atualizado, o código recém-adicionado pode ser compilado em tempo de execução usando JIT até que uma nova compilação AOT ocorra.

O **perfilamento dinâmico** também pode ser usado para monitorar o comportamento do aplicativo e ajustar o código, usando JIT para melhorar partes do aplicativo que são executadas frequentemente.

Se o arquivo `.oat`, o binário AOT para `.dex`,  estiver disponível, o ART o usará diretamente. Embora os ficheiros .oat sejam gerados regularmente, nem sempre contêm código compilado (binário AOT).

- O JIT é ativado para qualquer aplicativo que não seja compilado de acordo com a filtro de compilação `speed`, que diz “compile o máximo que puder a partir da aplicação”;
- Os dados do perfil JIT são despejados em um arquivo em um diretório do sistema que apenas a aplicação pode acessar.
- O daemon de compilação AOT (`dex2oat`) analisa esse arquivo para orientar a sua compilação. O comando **dex2oat** é o responsável por realizar a compilação AOT no _Android_. Ele é invocado durante a instalação ou atualização de um aplicativo e converte os arquivos DEX em arquivos OAT (o formato otimizado para ART).

Isso permite que o código Java do aplicativo seja executado diretamente como código nativo no processador do dispositivo. Logo, o **dex2oat** é executado no momento da instalação e também pode ser acionado após atualizações do sistema ou do próprio aplicativo.

![[Pasted image 20241029094048.png]]
