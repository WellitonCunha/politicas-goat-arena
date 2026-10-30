# Respostas do formulário "Segurança dos dados" do Play Console

Registro das respostas e do motivo de cada uma, para quando o formulário
precisar ser revisado — ele tem que ser atualizado sempre que o SDK de anúncios
subir de versão ou o app passar a tratar algum dado novo.

Base: **Google Mobile Ads SDK 25.5.0**, conforme a
[divulgação de dados do AdMob para o Google Play](https://developers.google.com/admob/android/privacy/play-data-disclosure).

> A Google deixa explícito naquela página que a responsabilidade pelas respostas
> é do desenvolvedor, não dela. O que está aqui é a leitura fiel do que o SDK
> declara coletar, cruzada com o que o app faz.

## O princípio que separa o que declarar

A Play considera um dado **coletado** quando o app o retira do aparelho. Os
dados da pelada — peladeiros, fotos, partidas, gols, cartões, valores — ficam
todos no armazenamento privado do app e nunca saem. Por isso **não** são
declarados, mesmo sendo dados pessoais: ninguém os coleta.

O mesmo vale para a exportação: o arquivo vai para onde o usuário escolher, por
ação dele, e não para nós.

O que sobra para declarar é o que o SDK de anúncios manda para o Google.

## Perguntas de abertura

| Pergunta | Resposta |
| --- | --- |
| O app coleta ou compartilha algum dos tipos de dados do usuário exigidos? | **Sim** |
| Todos os dados coletados são criptografados em trânsito? | **Sim** — o SDK usa TLS |
| Você oferece um meio de o usuário solicitar a exclusão dos dados? | **Não** |

Sobre a exclusão: não há servidor nem conta onde esses dados fiquem guardados
por nós. Os dados do app o usuário apaga no próprio aparelho, e o identificador
de publicidade ele redefine ou exclui nas configurações do Android. Não existe
pedido de exclusão a ser feito a nós, então "Não" é a resposta honesta.

## Tipos de dados a declarar

Para **todos** os quatro: coletado **Sim**, compartilhado **Sim**, processado
**não** efemeramente, e a coleta é **obrigatória** (o app não oferece um botão
para desligar o anúncio).

| Dado que o SDK coleta | Categoria no formulário | Finalidades |
| --- | --- | --- |
| Endereço IP, que pode estimar a localização geral | Localização → **Localização aproximada** | Publicidade ou marketing · Análise · Prevenção de fraudes, segurança e conformidade |
| Abertura do app, toques, visualizações de vídeo | Atividade no app → **Interações com o app** | Publicidade ou marketing · Análise · Prevenção de fraudes, segurança e conformidade |
| Tempo de abertura, travamentos, consumo de energia | Informações e desempenho do app → **Diagnóstico** | Análise · Prevenção de fraudes, segurança e conformidade |
| Ad ID, app set ID e identificadores de contas conectadas | **ID do dispositivo ou outros IDs** | Publicidade ou marketing · Análise · Prevenção de fraudes, segurança e conformidade |

**"Compartilhado" é Sim** porque o Google é terceiro em relação ao
desenvolvedor, e a própria página do AdMob usa a palavra "compartilha" para
descrever o que o SDK faz.

## O que NÃO declarar

Declarar demais é tão problemático quanto declarar de menos: a ficha passa a
dizer que o app coleta coisas que ele não coleta, e isso é uma declaração falsa.

| Não declarar | Por quê |
| --- | --- |
| Nome, telefone, data de nascimento dos peladeiros | ficam no aparelho, não são retirados dele |
| Fotos | copiadas para a área privada do app, nunca enviadas |
| Informações financeiras (mensalidades, caixa) | ficam no aparelho; não há pagamento no app |
| Arquivos e documentos | a exportação grava onde o usuário mandar, por ação dele |
| Localização precisa | o app não pede permissão de localização |
| Contatos, mensagens, áudio, agenda | o app não acessa nada disso |

## Quando isso precisa ser revisto

- quando o `play-services-ads` subir de versão — a página do AdMob muda junto
- se entrar qualquer SDK de análise, de relatório de falhas ou de login
- se o app passar a sincronizar dados em nuvem
- se for implementado o consentimento UMP para Europa e Reino Unido
