# 1st slide

Olá a toda a gente, obrigado por estarem presentes. Vou começar a minha a apresentação sobre o que ando a fazer desde setembro até aqui.

# 2nd Slide

Antes de começar, quero trazer-vos à atenção que o meu trabalho recente tem andado à volta de estudar e aprender conceitos novos,e apresentação vai refletir isso. Ou seja, vai ser mais à volta dos conceitos que ando a trabalhar do que em trabalho feito e resultados.

# 3rd Slide

Vamos começar com uma pequena introdução

# 4/5th Slide

Este é o meu titulo "Meta-Reinforcement Learning and Causality for Multi-tasking in Robots with Redundant Kinematics". Na verdade, o que eu quero dizer com isto é que (transition) eu vou explorar diferentes metodos the learning para criar sistemas que controlem robôs.

E, na verdade, é impossivel atacar todos estes tópicos ao mesmo tempo, (transition) então escolhi começar pelo Reinforcement Learning e a Causalidade.

# 6th Slide

Antes demais, queria enquadrar o contexto do mundo da robotica. Estes dados foram fornecidos pela Federação Internacional de Robotica em 2023, e demonstram um crescimento nos últimos anos de robôs industriais, com especial foco em robôs colaborativos.

# 7th Slide

No lado da robotica de serviços, vemos um crescimento significativo na produção dos mesmo, e a Federação Internacional de Robotica argumenta que deve-se ao facto da falta de mão-de-obra especializada para estes cargos. 

# 8th Slide

O que os robôs colaborativos e de serviços têm em comum é que precisam de interagir em ambientes complexos por causa de terem de interagir com seres humanos, ou terem de existir em ambientes criados para seres humanos. (transition)

E por isso, estes robôs têm que ser mais flexiveis e adaptaveis. Durante o resto da apresentação, quero que mantenham estes requerimentos em mente.

# 9th Slide

Vamos começar por falar no porquê de utilizar Reinforcement Learning

# 10th Slide

Muito resumidamente, Reinforcement Learning é uma metodologia de aprendizagem que permite a um agente aprender como cumprir um objetivo interagindo com o mundo para adquirir informação. Estas interações são normalmente denominadas de ações. Cada vez que o robô interage com o mundo, ele recebe uma recompensa que avalia a sua performance face ao objetivo. Quero salientar esta component de interação, visto que Reinforcement Learning é a única metologia de aprendizagem que permite à inteligencia artificial fazer isto. Isto traz outro tipo de dificuldades, mas também abre portas para outras de oportunidades.

# 11th Slide

Queria salientar que Reinforcement Learning não é a única solução de controlo para a robótica, e precisamos de estar cientes que outros metodos existem. Um dos métodos estado-da-arte é este Model Predictive Control. Eles claramente possuem similiaridades, com o tipico processo de malha fechada que encontramos em problemas de controlo. 

No entanto uma grande diferença é que nos metodos mais tradicionais, o mundo fisico é preciso ser modelado por equações dinamicas diferenciais, enquanto em Reinforcement Learning o agente aprende como o mundo funciona pela experiencia. Modelar o mundo por equações é possivel em problemas de locomoção em que apenas preocupamos com o corpo do robô e o plano estático em que ele caminha, mas quando começamos a introduzir objetos ou pessoas que são mais dinamicas e imprevisiveis, os metodos tradicionais não escalam tão bem.

# 12th Slide

Dito isto, temos aqui um exemplo de controlo tradicional a funcinonar muito melhor que Reinforcement Learning!

Como já tinha dito, para tarefas de locomoção, os métodos de controlo tradicional parecem melhores, pois parecem ser ter mais precisão de movimento.

# 13th Slide

Por outro lado, temos aqui um resultado das minhas experiencias em Reiforcement Learning. Vou vos mostrar um típico problema de PickAndPlace, em que o robô precisa de apanhar um cubo numa posição aleatoria e trazê-lo para uma posição objetivo também aleatoria. Não estou a dizer que robotica tradicional não consegue fazer isto, mas de facto tornou-se um problema muito mais simples por causa do Reinforcement Learning. Neste cenário, não tivemos que especificar nenhuma dinamica do mundo, como é que o braço interage com o bloco, pontos de aproximação, forças de contacto, pontos de contacto, entre outras grandezas roboticas, que normlamente seriam necessárias. No final de tudo, acho que o agente conseguiu fazer esta tarefa com uma taxa de sucesso elevada com 3h de treino penso eu.

# 14/15th Slide

Concluindo esta secção, a única idea que quero passar é que o controlo tradicional é robusto e previsivel, mas não é escalavél,

 (transition)

enquanto reinforcement learning é escalavel e flexivel. Como o obejtivo falado anteriormente era desenvolver sistemas que interajam em ambientes mais complexos, reinforcement learning parece uma melhor escolha. Salientando que parece-me que nenhum dos metodos é melhor que outro, simplesmente parecem me que têm casos de estudo diferentes.

# 16th Slide

Vamos entrar agora no porquê da causalidade?


# 17th Slide

Primeiro vamos a uma intuição. Não se já leram o livro de Thinking Fast and Slow, este livro é sempre falado quando se fala de Causalidade em Machine Learning. Basicamente, o livro divide o pensamento humano em 2 sistemas, o pensamento rapido, que é mais à base da correlação e do reconhecimento de padrões, e o pensamento lento, com base na logica e no planeamento. O argumento principal é que os poderosos modelos de Deep Learning de hoje em dia estão presos a maximizar o sistema 1, e para atingir inteligencia e performance ao nível do ser humano, precisamos de tentar trabalhar no sistema 2, utilizando os conceitos de causalidade.

# 18th Slide

 Mas então, qual é a diferença entre correlação e causalidade, e porque é que correlação pode nãos ser suficiente? Bem, temos aqui dados reais que correlacionam afogamentos e consumo de gelado. Mas o que está aqui a acontecer? O consumo de gelados causa afogamentos? Ou os afogamentos aumentam a vontade o publico em geral de comer gelados?
 Bem, nenhum dos dois, estas variaveis claramente não têm nenhuma relação de causa-efeito apesar 
 de estarem estatisticamente realacionadas.

 (transition)
 
E elas estão relacionadas porque têm uma terceira variavel que causa as duas: os meses do ano, meses mais quentes implicam mais ativididade que provocam os dois eventos.

O perigo disto é que se eu usar esta correlação para tentar prever afogamentos baseado no consumo de gelado, se por acaso o mercadona tiver uma promoção nos gelados em dezembro e toda agente começar a comer gelados, o modelo vai alertar-nos que os afogamentos também vão aumentar

# 19th Slide

Mas então, como é que conseguimos descobrir se duas varaiveis correlacionadas têm ou não uma relação de causa-efeito? 
Como diz o título,

(transitions)

por intervenções!

Por exemplo, se forçassemos pessoas a comer gelado numa altura aleatoria, iriamos ver que o numero de afogamentos não mudaria, e podiamos dizer que o primeiro evento não causa o segundo. 

Talvez os mais atentos devem ter notado que já é a segunda vez que menciono intervenções nesta apresentação!

# 20th Slide

Por último vamos falar de Causal Reinforcement Learning

# 21st Slide

Já vimos que Reinforcement Learning aprende a atingir um objetivo por interações, e falamos agora que em Causal Learning aprendemos como o mundo funciona por interaçẽos. 

(transition)

Ou seja, ambas estas metodologias usam este mesmo tipo de dados de intervenção, e por isso acabam por fazer o mesmo tipo suposições sobre o problema de aprendizagem, tornando apelativo juntar as duas. Também pode-se arguentar que aprender como o mundo funciona de uma maneira mais representativa, de uma maneira causal, pode ajudar a aprendizagem de Reinforcement Learning.

# 22nd Slide

Juntar estas duas metologias chama-se Causal Reinforcement Learning, e claramente não foi uma ideia minha. Temos aqui um investigador, Elias Bareinboim, que trabalha num laboratorio que produz bastante material cientifico à volta deste tópico

# 24th Slide

Concluido, neste momento eu sei mais ou menos que metodologias quero usar e porquê, e falta-me explorar como implementa-las e pensar num caso de estudo de robotica para validar os meus metodos.

Dado a natureza desta apresentação, tive de ser muito breve com os conceitos, no entanto deixo aqui o meu blog do doutoramento que vou resumindo os meus estudos e os meus resultados para quem estiver mais interessado em saber mais.

Obrigado pela atenção, espero que tenham gostado!