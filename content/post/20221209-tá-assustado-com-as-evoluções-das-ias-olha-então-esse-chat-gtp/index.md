---
title: Tá assustado com as evoluções das IAs? Olha então esse Chat GTP!
subtitle: Revisa código, escreve roteiro e conversa como se fosse uma pessoa.
description: Chat GTP da Open AI impressiona com o nível da conversa
date: 2022-12-09T16:09:35.686Z
authors:
  - Alexandre Alvaro
image: post/20221209-tá-assustado-com-as-evoluções-das-ias-olha-então-esse-chat-gtp/capa.jpg
thumbnail: post/20221209-tá-assustado-com-as-evoluções-das-ias-olha-então-esse-chat-gtp/thumb.jpg
categories:
  - IA
tags:
  - IA
  - Chat
  - Bot
  - ""
---
Quem tá acostumado a interagir com assistentes pessoais como Alexa, Google, Cortana e Siri, sabe que é impressionante sim, mas ainda tem muito pra melhorar, chatbots então, ainda mais.
Sempre que sai uma notícia sobre tecnologia de ponta de grandes nomes como a [Open AI](https://openai.com/), [Stability AI](https://stability.ai/), [Boston Dynamics](https://www.bostondynamics.com/) a gente já espera se surpreender, e acontece!

Mas confesso que desta vez fui pego de surpresa. Andei bastante empolgado com o Stable Diffusion da [Stability AI](https://stability.ai/), conforme podemos ver essa publicação que fiz [por aqui, no pedaço mais massa da internet](https://www.tabnews.com.br/xambitow/nao-use-o-app-lensa-crie-suas-proprias-imagens-com-i-a-no-seu-pc-ou-google-colab-com-stable-diffusion).
Mas quando estava trocando uma ideia sobre isso com meu amigo (e concunhado) [Luciano Clécio](https://www.linkedin.com/in/lucianoclecio/), ele me apresentou o [ChatGTP](https://openai.com/blog/chatgpt/) da [Open AI](https://openai.com/) eu desacreditei da qualidade do que vi.

O blog da própria [Open AI](https://openai.com/) descreve assim o [ChatGTP](https://openai.com/blog/chatgpt/) (tradução livre):
> ChatGPT: Otimizando modelos de linguagem para diálogo.
Treinamos um modelo chamado ChatGPT que interage de forma conversacional. O formato de diálogo permite que o ChatGPT responda a perguntas de acompanhamento, admita seus erros, conteste premissas incorretas e rejeite solicitações inadequadas. O ChatGPT é um modelo irmão do InstructGPT, que é treinado para seguir uma instrução em um prompt e fornecer uma resposta detalhada.

# Código fonte
Vi alguns exemplos por aí e testei algumas interações relacionadas a linhas de código, dá só uma olhada.
Importante ressaltar que fizemos toda conversa (e comentários em código) em português brasileiro!

## Aquele dev extra pra dar uma mão
Conversando com meu novo amigo, pedi uma mão pra fazer uma interface web com um campo pra converter código de cores.

### Segue o diálogo:
**Alexandre**: 
> Preciso de um código em python com uma interface web que converta uma entrada hexadecimal pra cores rgb  
> 
**ChatGTP**:
> Para criar uma interface web em Python para converter entradas hexadecimais em RGB, você pode usar o framework Flask. Ele permite criar facilmente uma aplicação web que lida com entradas do usuário e exibe resultados.
Primeiro, você precisará instalar o Flask usando o gerenciador de pacotes Python pip. Para fazer isso, abra o terminal e execute o seguinte comando:
```
pip install Flask
```
> Em seguida, você pode criar um arquivo Python com o seguinte código para criar sua aplicação:
```python
from flask import Flask, request

app = Flask(__name__)

@app.route('/convert', methods=['GET', 'POST'])
def convert():
    if request.method == 'POST':
        # Obter a entrada hexadecimal do usuário
        hex_input = request.form['hex']

        # Converter a entrada hexadecimal em RGB
   put[1:3], 16)
        g = int(hex_input[3:5], 16)
        b = int(hex_input[5:7], 16)

        # Exibir os valores RGB na página
        return 'Red: {}, Green: {}, Blue: {}'.format(r, g, b)

    return '''
        <form method="post">
            <input type="text" name="hex" placeholder="Hexadecimal" />
            <input type="submit" value="Convert" />
        </form>
    '''

if __name__ == '__main__':
    app.run()
```
> Este código cria uma aplicação Flask que lida com solicitações HTTP enviadas para o URL '/convert'. Se a solicitação for do tipo POST, o código extrai a entrada hexadecimal do formulário enviado pelo usuário e converte em valores RGB. Em seguida, exibe os valores RGB na página. Se a solicitação for do tipo GET, o código exibe um formulário HTML que permite que o usuário insira uma entrada hexadecimal.
Para executar a aplicação, basta executar o arquivo Python no terminal usando o seguinte comando:
```bash
python app.py
```

> Isso iniciará o servidor Flask na porta padrão (5000). Em seguida, você pode acessar a aplicação no seu navegador digitando o seguinte endereço:
```python
http://localhost:5000/convert
```
> Isso exibirá o formulário HTML que você criou. Depois de inserir uma entrada hexadecimal no formulário e enviá-lo, a aplicação converterá a entrada em valores

## Travei, ajuda a revisar o código aí meu camarada
Replicando um exemplo que vi em inglês, tentei pedir uma ajuda com um código em Go.
Perceba que fiz mais perguntas relacionadas a pergunta anterior e o ChatGTP dá conta de seguir o contexto.

### Segue o diálogo:
**Alexandre**: 
> este código não tá funcionando como eu espero, como resolver?
```go
resultWorkerErr := make(chan error)
defer close(resultWorkerErr)
go func() {
	defer cancel()
	resultWorkerErr <- b.resultWorker(ctx)
}()

err := b.worker(ctx)
cancel()
if err == nil {
	return <-resultWorkerErr
}
return multierror.Append(err, <-resultWorkerErr)
```

**ChatGTP**:
> Sem saber exatamente o que o seu código está fazendo, é difícil dar uma resposta precisa. No entanto, aqui estão algumas dicas gerais que podem ajudá-lo a encontrar o problema:
Adicione mais logs para ver o que está acontecendo no seu código. Isso pode ajudá-lo a identificar onde o problema está ocorrendo e o que está causando o erro.
Verifique se as suas funções estão sendo chamadas corretamente e se estão recebendo os argumentos corretos.
Verifique se as variáveis que você está usando estão sendo inicializadas corretamente e se possuem os valores que você espera.
Se você estiver trabalhando com concorrência, verifique se suas goroutines estão sendo sincronizadas corretamente para evitar problemas de race condition.
Essas dicas gerais podem ajudá-lo a encontrar o problema no seu código e corrigi-lo. Se você precisar de mais ajuda, é importante fornecer mais informações sobre o seu código e o que você está tentando fazer com ele.

**Alexandre**: 
> o erro nunca aparece. Acho que tem algo errado com o canal

**ChatGTP**:
> Se você está tendo problemas com o seu código e o erro nunca está sendo reportado, isso pode ser um sinal de que há algo errado com o seu canal. Algumas coisas a serem consideradas:
Verifique se o seu canal está sendo criado corretamente e se está sendo passado como argumento para as funções corretas.
Verifique se o seu canal está sendo utilizado corretamente em suas goroutines. Isso inclui a verificação de se ele está sendo lido e escrito corretamente e se as goroutines estão sendo sincronizadas corretamente para evitar problemas de deadlock.
Se você estiver utilizando o operador ***"defer"*** para fechar o canal, verifique se ele está sendo chamado corretamente e se está sendo chamado após todas as goroutines terem sido iniciadas.
Essas são algumas coisas a serem consideradas ao trabalhar com canais em Go. Se você ainda estiver tendo problemas, é importante fornecer mais informações sobre o seu código e o erro que você está enfrentando para que possamos ajudá-lo de maneira mais precisa.


## Faz aí um roteiro de vídeo pra mim
Resolvi desafiar um pouco a IA, e pedi pra criar um roteiro pra vídeo de Youtube sobre algo bem específico, relacionado a Internet das Coisas.
### Segue o diálogo:
**Alexandre**: 
> faz um roteiro para o canal de youtube "Inteligência das Coisas" explicando as vantagens de usar o ESP32 em relação ao ESP8266

**ChatGTP**:
> Oi! Aqui está um possível roteiro para um vídeo sobre as vantagens de usar o ESP32 em relação ao ESP8266 para o canal "Inteligência das Coisas":
    - Inicie o vídeo apresentando o tema e explicando por que é importante considerar as diferenças entre o ESP32 e o ESP8266 ao escolher uma placa de desenvolvimento para projetos de internet das coisas.
    - Em seguida, explique o que são o ESP32 e o ESP8266 e suas principais características. Mencione que ambos são microcontroladores Wi-Fi e que o ESP32 é a segunda geração do ESP8266.
    - Agora, vamos falar sobre as principais vantagens do ESP32 em relação ao ESP8266. Primeiro, mencione que o ESP32 possui dois processadores, o que o torna mais rápido e capaz de executar múltiplas tarefas ao mesmo tempo.
    - Em seguida, destaque a capacidade de conexão do ESP32 com outros dispositivos via Bluetooth, o que o torna mais versátil do que o ESP8266, que só suporta conexões Wi-Fi.
    - Também é importante mencionar que o ESP32 é mais eficiente em termos de consumo de energia do que o ESP8266, o que é importante para projetos que precisam de baixo consumo de energia, como dispositivos portáteis ou sensores de longo alcance.
    - Finalmente, apresente algumas das principais aplicações do ESP32, como controle de luzes inteligentes, monitoramento de temperatura e umidade, e até mesmo como um assistente de voz.
    - Conclua o vídeo resumindo as principais vantagens do ESP32 em relação ao ESP8266 e incentivando os telespectadores a experimentar o ESP32 em seus próprios projetos de internet das coisas.

## Pedi até dicas pro aniversário do meu sobrinho
Observe que escrevi errado as palavras ***festa*** e ***costuma***, e mesmo assim isso não foi problema.

### Segue o diálogo:
**Alexandre**: 
> me sugere um tema de ***feta*** infantil para um menino de 2 anos

**ChatGTP**:
> Um bom tema de festa infantil para um menino de 2 anos pode ser o tema de um personagem de desenho animado ou brinquedo que ele gosta. Algumas sugestões populares incluem o Mickey Mouse, Patrulha Canina, Super-Homem, Homem-Aranha, Thomas e seus amigos, ou até mesmo o tema de fazendinha. O importante é escolher algo que o pequeno vai gostar e se divertir.

**Alexandre**: 
> pensei em algo bem colorido, ***costua*** chamar a atenção dele quando passa na televisão

**ChatGTP**:
> Uma festa com tema colorido pode ser uma ótima opção para chamar a atenção de um menino de 2 anos. Você pode escolher um tema como arco-íris, frutas, ou até mesmo um monte de animais divertidos e coloridos. Outra ideia é criar um tema baseado em algum brinquedo ou personagem que o seu filho gosta e que tenha muitas cores vibrantes, como o Bob Esponja, o Coelho da Páscoa, ou até mesmo o tema de circo. Com certeza ele vai adorar!

# Conclusão
Estamos acompanhando apenas o início dessa nova fase. Tem muita polêmica envolvida no fóruns. Mas como eu falei no último post que fiz [por aqui, no pedaço mais massa da internet](https://www.tabnews.com.br/xambitow/nao-use-o-app-lensa-crie-suas-proprias-imagens-com-i-a-no-seu-pc-ou-google-colab-com-stable-diffusion):
> Muita gente está com medo da tecnologia e acredita que vai perder seu emprego. Provavelmente vai mesmo. Mas a gente precisa se adaptar e entender onde nos encaixamos nisso tudo, aprendendo a usar as ferramentas ao nosso favor. É assim toda vez que surge algo inovador no mundo, por exemplo a invenção da máquina de costura: https://www.maquinasuniao.com.br/conheca-a-historia-da-invencao-da-maquina-de-costura/

Lembrem dessa notícia: [IA do Google teria contratado advogado por conta própria](https://www.tabnews.com.br/gugadeschamps/ia-do-google-teria-contratado-advogado-por-conta-propria)

E [deste diálogo](https://www.aio.com.br/questions/content/texto-i-1-no-filme-eu-robo-um-policial-encarregado-de-investigar-o) na cena de interrogatório no filme **Eu robô**: 
```
[1] No filme Eu, Robô, um policial encarregado de
investigar o assassinato de um humano supostamente cometido
por uma máquina interroga um robô. Esse policial demonstra,
[4] desde o início do filme, uma atitude de reprovação em relação
ao desenvolvimento tecnológico dessas máquinas. Na cena do
interrogatório, ocorre o seguinte diálogo entre o policial e o robô.
[7] Policial: Por que se escondeu na cena do crime?
Robô: Eu tive medo.
Policial: Robôs não sentem medo. Eles não sentem nada. Não
[10] sentem fome, não sentem sono.
Robô: Eu tenho. E tenho até mesmo sonhos.
Policial: Seres humanos é que têm sonhos. Até cães têm
[13] sonhos. Você não. Você é só uma máquina. Uma imitação da
vida. Um robô consegue compor uma sinfonia? Um robô
consegue pintar uma bela obra-prima?
[16] Robô: Você consegue?
(O policial fica em silêncio, constrangido).
```


E aí? conta pra gente algo legal que você testou ou deixa a sua opinião sobre o futuro dos empregos de desenvolvimento, arte e outras áreas de criação, que sempre pensávamos que não seriam substituídas.

E faz teus testes lá: https://chat.openai.com/chat
