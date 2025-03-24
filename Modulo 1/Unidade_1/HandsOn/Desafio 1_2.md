
# ORIENTAÇÕES GERAIS

- A atividade deve ser realizada em grupo e no momento assíncrono;  
- Informe os nomes de todas(os) as(os) componentes no trabalho;  
- A atividade deve ser entregue via Ambiente Virtual de Aprendizagem (AVA);  
- A data limite para a entrega da atividade será informada no AVA  
- Caso utilize referências bibliográficas, insira as fontes de acordo com a Associação Brasileira de Normas Técnicas (ABNT);  
 Leia atentamente as etapas para a realização da tarefa

# OBJETIVOS DE APRENDIZAGEM

- Descrever a arquitetura do sistema operacional Android;  
- Implementar um dispositivo com sistema operacional Android com funcionalidades emuladas.

# DESCRIÇÕES E PROCEDIMENTO

Olá, estudante!  

O Google mantém o repositório do Android Open Source Project (AOSP) e oferece as informações e o código-fonte necessários para criar variantes personalizadas do sistema operacional Android como dispositivos e acessórios, garantindo que atendam aos requisitos de compatibilidade e mantendo o ecossistema Android um ambiente saudável e estável para milhões de usuários.

Como um projeto de código aberto, o objetivo do Android é evitar que um fabricante possa restringir ou controlar as inovações de qualquer outro. Para esse fim, ele é um sistema operacional completo e com produção de qualidade para produtos com código-fonte personalizável que pode ser portado para praticamente qualquer dispositivo e com documentação pública disponível para todos.

# Ação 1 – 530 min.

Nesta atividade, você e sua equipe devem desenvolver um <span style="color:rgb(0, 176, 80)">roteiro de implementação de um dispositivo com sistema operacional Android</span>, descrevendo desde a configuração inicial da estação de trabalho no Linux até a emulação do sistema operacional Android. O roteiro deve conter a inserção de imagens (screenshots) e abranger os comandos utilizados no Linux.

Os conhecimentos desta atividade estão vinculados às Unidades de Aprendizagem (UA) 1 e 2. É indicado que na UA 1, sejam pesquisados os principais comandos utilizados (scripts), bem como a organização da estrutura e outros aspectos relacionados. Na UA 2, a indicação é executar a tarefa planejada anteriormente, realizando atividades como, por exemplo, configuração da estação de trabalho Linux, estrutura de versões dos códigos do AOSP, entre outras.  
Para obter uma compreensão abrangente, além do site oficial do Google, utilize artigos, relatórios, revistas e jornais especializados.

Leia as orientações a seguir para compreender os detalhes relacionados à atividade:

1. Configure a estação de trabalho Linux.

A documentação do Google sugere alguns requisitos mínimos de hardware para um bom  
desempenho, mas existem alguns processos de customização de “swap” para alcançar o mesmo  
objetivo. Caso necessário, consulte o link a seguir: https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-20-04-pt

2. Concentre-se na ferramenta “repo” criada pelo Google para controle de versionamento das versões do Android.
3. Identifique as versões do Android através do repositório de versionamento e do conteúdo que o compõe. Além disso, realize uma análise crítica das configurações dos repositórios dos projetos no arquivo de manifesto (default.xml) no diretório oculto “./repo”.
4. Pesquise sobre os principais comandos do Linux e realize uma análise sobre as principais funcionalidades dos comandos utilizados no Android e do processo de instalação dos pacotes necessários.
5. Elabore o roteiro, após analisar todas as informações reunidas durante a pesquisa, sintetize os principais pontos e identifique as lacunas e oportunidades de melhorias.

- Os comandos utilizados para sincronização do código do AOSP;<  
- A estrutura do arquivo de configuração do repo “default.xml”;<  
- Pelo menos dois exemplos de projetos que estão no arquivo .xml baixado junto com o AOSP;  
- A preparação e compilação do AOSP;  
- A emulação do AOSP.

6. Insira no roteiro capturas de telas imagens (screenshots) dos tópicos abordados.
7. Mantenha a clareza e a concisão em seu texto.

# Ação 2 – 10 min.

Realize o envio da atividade em um único documento no formato .pdf, através do espaço designado no Ambiente Virtual de Aprendizagem (AVA). Você e os demais integrantes da equipe devem enviar a atividade.

Boa sorte!

# Referências

Projeto Open Source do Android, Começar a desenvolver no Android. Disponível em: https://source.android.com/docs/setup?hl=pt-br. Acesso em: 15 jul. 2024.

DigitalOcean, Como adicionar espaço de swap no Ubuntu 20.04. Disponível em: https://  
www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-20-04-pt. Acesso em: 20 set. 2024.

# ___________________________


# Descrição
(Refazer, pois está parecendo o Hands On 3 e 4)
(para refazer, usar o link https://senaicimatec.instructure.com/courses/3897/assignments/37367)
Como customizar o Android para que seja capaz de  receber sinais de áudio e realizar equalização em  ambientes de engenharia automotiva?

O desafio tem como objetivo a implementação de um dispositivo com sistema operacional Android e com funcionalidades emuladas que sejam capazes de receber sinais do protocolo Controller Area Network (CAN). Esse dispositivo emulado servirá como uma plataforma de testes e validação, permitindo a verificação do correto funcionamento da equalização de áudio em cenários controlados.  
Para auxiliar o desenvolvimento, o desafio em questão está organizado em 2 (duas) entregas:

![[Captura de tela de 2024-10-26 12-37-10.png]]

Links citados no Hands On:
- https://developer.android.com/training/cars?hl=pt-br
- https://source.android.com/docs/automotive?hl=pt-br
# Conceitos 

## ECU

## CAN

## P2P

## Abordagem

Provavelmente vamos atuar no seguinte diretório:
hardware/libhardware/modules/audio