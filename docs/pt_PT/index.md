
BLEA (anúncio em Bluetooth)
==============================

Description
-----------

Este plugin é um plugin que permite que você receba eventos de determinados dispositivos bluetooth (como NIUs da Nodon)

![blea icon](../images/blea_icon.png)

Configuration
-------------

Configuração do plugin
========================

a. Instalação / Criação

> **Tip**
>
> Para usar o plug-in, você precisa baixar, instalar e
> ativá-lo como qualquer plugin Jeedom.

- Depois disso, você chegará a esta página :

![gestion](../images/gestion.jpg)

Nesta página, você tem pouco a fazer. É altamente recomendável iniciar a instalação das dependências (mesmo que pareçam OK). Em seguida, ao final da atualização da página.

> **Important**
>
> A coisa mais importante aqui é selecionar seu controlador
> Bluetooth

A outra opção disponível nesta página é : **Excluir automaticamente dispositivos excluídos**. Isso remove o equipamento Jeedom quando é excluído.

Você também pode verificar o status das dependências e reiniciá-las. Em caso de problemas com o plug-in, sempre reinicie as dependências, mesmo se estiver bem em caso de dúvida.

O plugin
=========

Rendez vous dans le menu Plugins &gt; Protocole Domotique pour retrouver le plugin.

![blea screenshot1](../images/blea_screenshot1.jpg)

Nesta página você pode ver os módulos já incluídos.

Na parte superior desta página, você tem vários botões.

- Botão de inclusão : esse botão permite colocar o Jeedom na inclusão.
- Botão de exclusão : este botão permite colocar o Jeedom em exclusão.
- Botão de configuração : este botão abre a janela de configuração do plug-in.
- Botão de saúde : este botão permite que você tenha uma visão geral da saúde de todos os seus módulos.

![blea screenshot2](../images/blea_screenshot2.jpg)

Equipement
==========

Quando você clica em um de seus módulos, você chega na página de configuração deste módulo. Como em qualquer lugar em Jeedom, você pode aqui no lado esquerdo :

- Dê um nome ao módulo.
- Ative / torne visível ou não.
- Escolha seu objeto pai.
- Atribuir uma categoria.
- Definir um atraso de monitoramento de comunicação para determinados módulos.
- Publicar um comentário.

No lado direito, você encontrará :

- O perfil do equipamento (geralmente detectado automaticamente se o módulo permitir).
- Escolha um modelo se, para esse perfil, vários modelos estiverem disponíveis.
- Veja o visual.

Quais módulos
=============

No momento, apenas determinados módulos específicos são reconhecidos.

Caso NIU
-----------

O NIU é muito fácil de incluir, coloque o Jeedom em Inclusão e pressione o botão (simples assim).

Uma vez criado o NIU, você receberá este :

![blea screenshot3](../images/blea_screenshot3.jpg)

Você terá 4 pedidos :

![blea commands niu](../images/blea_commands_niu.jpg)

- ButtonId : fornece uma representação digital do tipo de suporte (ideal para cenários)
  - 01 : imprensa simples
  - 02 : suporte duplo
  - 03 : Pressão longa
  - 04 : relachement
- Botões : fornece uma representação textual do tipo de suporte
- Rssi : fornece o valor da força do sinal
- Bateria : dá o valor da bateria

Outros módulos
--------------------

Outros módulos podem ser incluídos, como farol NUT, pulseira fitbit, etc..

Eles permitirão a detecção de presença com detecção em um
Janela de 1 minuto.

Obviamente, muitos outros módulos serão adicionados.

Configuração de antena remota
================================

O Bluetooth tem um alcance relativamente limitado; é possível que parte da sua casa esteja fora do alcance da sua antena, dependendo da localização da sua caixa Jeedom.
Mas existe uma solução: é possível estender a rede instalando antenas adicionais.

A maneira mais fácil é usar um raspBerry pi (existente ou dedicado, dependendo do equipamento que você já possui). Vamos assumir aqui que o raspBerry já está instalado com um raspbian e que ssh e bluetooth estão ativados.

Criou a antena
--------------

Você deve ir para a página do plug-in (Plugins> Home Automation Protocol) e clicar em "Antenas"

1) clique em "Adicionar"
2) escolha um nome
3) Digite o ip e a porta (22 por padrão)
4) Digite o nome do usuário ("pi" por padrão) e a senha
5) Digite o equipamento bluetooth no pi ("hci0" em uma instalação padrão)
6) Salvar

Instalação do daemon
----------------------

Se não houve erro e sua antena foi criada no plug-in, você deve agora instalar as dependências necessárias e iniciar o daemon na antena, que cuidará de fazer o link entre os dispositivos bluetooth alcance da antena e do plugin (e, portanto, Jeedom).

1) Clique no botão "Enviar arquivos", pode demorar um pouco, aguarde. Uma faixa verde confirmando o sucesso aparecerá, vermelha se houver algum problema. Nesse caso, verifique o log "Blea", verifique a configuração (ip, usuário, senha, ...)
2) Clique no botão "Iniciar dependências"". Novamente, pode levar tempo, aguarde. Um banner verde confirmará o sucesso ou vermelho, se não (mesmo, verifique o registro Blea)
3) Opcional, você pode recuperar manualmente o log de instalação das dependências clicando em "Log de Dependências" e verificar o log, um arquivo de log específico estará disponível na configuração do plugin.
4) Se tudo correr bem, você pode clicar em "Iniciar o daemon", após um minuto no máximo a data da última comunicação deve ser atualizada, isso significa que o daemon está se comunicando corretamente com o plug-in BLEA.
5) Última etapa opcional, mas recomendada: ativar o gerenciamento automático do daemon clicando no botão correspondente. Isso fará com que o plug-in tente reiniciar automaticamente o daemon remoto no caso de uma perda de conexão (útil se o pi remoto tiver sido desconectado temporariamente da rede elétrica ou reiniciado após as atualizações).

Changelog
=========

Registro de alterações detalhado :
<https://github.com/jeedom/plugin-blea/commits/master>

Lista de equipamentos compatíveis
=================================

<https://jeedom.github.io/documentation/#equipment>