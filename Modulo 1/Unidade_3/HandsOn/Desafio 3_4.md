https://senaicimatec.instructure.com/courses/3897/assignments/37367

# ORIENTAÇÕES GERAIS

- A atividade deve ser realizada em grupo e no momento assíncrono;  
- Informe os nomes de todas(os) as(os) componentes no trabalho;  
- A atividade deve ser entregue via Ambiente Virtual de Aprendizagem (AVA);  
- A data limite para a entrega da atividade será informada no AVA;  
- Caso utilize referências bibliográficas, insira as fontes de acordo com a Associação Brasileira de Normas Técnicas (ABNT);  
- Leia atentamente as etapas para a realização da tarefa.

# OBJETIVOS DE APRENDIZAGEM

UA 3 e 4

- Customizar o sistema operacional Android com funcionalidades emuladas para que seja  
capaz de receber sinais da Controller Area Network (CAN);
- Reproduzir o fluxo de áudio de acordo com as configurações de equalização no sistema.  
# DESCRIÇÕES E PROCEDIMENTOS

Olá, estudante!  

O Google mantém o repositório do Android Open Source Project (AOSP) e oferece as informações e o código-fonte necessários para criar variantes personalizadas do sistema operacional Android. Os fabricantes de hardware e desenvolvedores devem integrar suas customizações respeitando as diretrizes do AOSP, ao invés de criar soluções alternativas que possam ser menos seguras.

Para habilitar o suporte ao protocolo de Rede de Área do Controlador (CAN - Controller Area Network) no kernel do AOSP, é necessário configurar o kernel para incluir os módulos e drivers de rede CAN. Esse processo envolve a modificação da configuração do kernel para ativar o suporte CAN e, se necessário, compilar drivers adicionais. A ferramenta can-utils é utilizada para o desenvolvimento e debug, pois com elas é possível enviar mensagens e monitorar a rede CAN.

# Ação 1 – 530 min.

Nesta atividade, você e sua equipe devem desenvolver um desenvolver um vídeo (.mp4) explicando em cada passo desde a configuração do kernel para habilitar o suporte ao protocolo Controller Area Network (CAN) no Android até a customização e ferramentas utilizadas para simular o envio de áudio e monitoramento da rede CAN. O vídeo deve compor uma explicação detalhada de cada passo e dos comandos utilizados no linux.

Os conhecimentos desta atividade estão vinculados às Unidades de Aprendizagem (UA) 3 e 4. É indicado que na UA 3, execute a tarefa planejada anteriormente, realizando atividades como, por exemplo, baixar uma versão do kernel do Android e habilitar o suporte ao protocolo CAN. Na UA 4, você precisará de um componente no sistema Android que ouça a rede CAN e intérprete as mensagens CAN relacionadas ao áudio. O Android oferece a Equalizer API para manipular configurações de equalização.

Para obter uma compreensão abrangente, além do site oficial da Google, utilize artigos, relatórios, revistas e jornais especializados.

Leia as orientações a seguir para compreender os detalhes relacionados a atividade:

1. Baixe os códigos-fontes do kernel Android utilizando a ferramenta “repo”;
2. Em seguida, adicione o suporte ao protocolo CAN. Cada mensagem CAN conterá informações específicas, como volume, balanço ou ajustes de equalização;

O kernel padrão do Linux e do Android não suporta o barramento CAN, sendo necessário adicionar esse suporte manualmente no arquivo de configuração “/common/build.config” e compilar o kernel com essas configurações.

3. Prossiga com a elaboração e adicione o conjunto de ferramentas “can-utils” e os módulos do kernel no AOSP;
4. Compile o AOSP novamente para gerar uma nova imagem do Android customizado com o protocolo CAN;
5. Emule a imagem do AOSP gerada e habilite a interface CAN;
6. Simule o envio de áudio e crie um script em JAVA para realizar a equalização do áudio;
7. Elabore o vídeo, após coletar e analisar todas as informações reunidas durante a pesquisa;
8. Sintetize os principais pontos, identifique as lacunas e oportunidades de melhorias, de acordo com os itens abaixo:
- Os comandos utilizados para instalação e customização do kernel;  
- A estrutura dos arquivos de configuração do kernel após a compilação;  
- A integração do kernel junto com o AOSP; 
- A preparação e compilação do AOSP; 
- A emulação do AOSP;  
- A simulação do envio de áudio e monitoramento da rede CAN com os comandos “candump” e “cangen”;  
- A equalização do áudio utilizando a API do Android "Equalizer”.

9. Mantenha a clareza e a concisão em seu vídeo.

# Ação 2 – 10 min.

Realize o envio da atividade em um único documento no formato PDF, através do espaço designado no Ambiente Virtual de Aprendizagem (AVA). Para o recurso audiovisual incorpore o link no documento enviado.

Boa sorte!

# Referências

Projeto Open Source do Android. Começar a desenvolver no Android. Disponível em: https://source.android.com/docs/setup?hl=pt-br. Acesso em: 15 jul. 2024.


# Abordagens

Usar os arquivos **bazel**?

