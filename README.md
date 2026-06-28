# Análise de  "No Driver Found" da Uber

# Problema de Negócio

Problema de Oferta vs. Demanda (Vazamento de Receita
O dado: Existem centenas de ocorrências de "No Driver Found" (Nenhum Motorista Encontrado) espalhadas por várias localidades e horários.

O problema de negócio: A plataforma está deixando dinheiro na mesa. Toda vez que um cliente não encontra motorista, a Uber perde 100% da receita daquela viagem.

Impacto: Perda de Market Share em regiões periféricas (ex: Noida Extension, Greater Noida) e ineficiência na precificação dinâmica (surge pricing) para atrair motoristas para essas áreas no momento certo.

# Premissas da análise

Foi analisado o fenômeno "No Driver Found" (Nenhum Motorista Encontrado).
Foram analisadas 150.000 corridas da Uber. 
Os dados são referentes ao ano de 2024, e as corridas analisadas foram realizadas na Índia.


# Estratégia da solução

O método Fato-Dimensão foi usado para desenvolver a análise de dados.

# Passo 1: Resumir o contexto em uma pergunta aberta

As perguntas abertas são um tipo de demanda muito comum em análise de dados nas quais a demanda possui N possíveis soluções e cabe ao analista de dados avaliar as possibilidades e escolher a alternativa com o maior retorno e o menor esforço possível. Para essa análise, foi definida a seguinte pergunta aberta:

**como a Uber pode resolver o problema de "No Driver Found" (Nenhum Motorista Encontrado)**

# Passo 2: Transformar pergunta aberta em fechada

As perguntas fechadas são um tipo de demanda muito comum na área de análise de dados. Essa demanda contém todos os detalhes da análise de dados e direciona o analista exatamente para o que precisa ser feito. Geralmente, a pergunta fechada é a escolha de uma solução entre todas as alternativas possíveis, feita por um profissional mais sênior da área.

Para essa análise, foi definida a seguinte pergunta fechada:

**Pergunta Fechada: **Calcule a taxa de cancelamento dos motoristas em comparação com a dos clientes nos últimos 30 dias, considerando todo o país.**

**Como se trata de uma comparação entre motoristas e clientes, considero aceitável que as taxas percentuais sejam semelhantes. Caso exista uma discrepância significativa entre as taxas de cancelamento, medidas mais diretas devem ser adotadas.**

# Passo 3: Definição da Coluna Fato

O Fato é a coluna de interesse que representa o ponto focal da análise. Nesse caso, a coluna "Booking Status" mostra se a corrida foi concluída ou não.

# Passo 4: Identificação das Dimensões

As colunas foram agrupadas em dimensões comuns que fornecem mais detalhes sobre o Fato que será analisado. Foram organizadas as seguintes dimensões:

Tempo e Data (Contexto Temporal): Date, Time. (Fornece a base cronológica para análise de sazonalidade, picos de demanda e horários de pico).

Localização e Veículo (Logística e Percurso): Vehicle Type, Pickup Location, Drop Location. (Detalha a estrutura operacional da viagem, incluindo o modal utilizado e os pontos de origem e destino).

Valores e Distância (Métricas Quantitativas da Corrida): Avg VTAT, Avg CTAT, Booking Value, Ride Distance. (Reúne as principais medidas numéricas que servirão como base para os cálculos de performance, faturamento e eficiência de tempo).

Avaliações e Pagamento (Experiência e Quitação): Driver Ratings, Customer Rating, Payment Method. (Agrupa as percepções de qualidade tanto do motorista quanto do cliente, além da forma de pagamento utilizada).

Cancelamentos e Incompletude (Motivos de Falha): Reason for cancelling by Customer, Driver Cancellation Reason, Incomplete Rides Reason. (Centraliza os fatores qualitativos e categóricos que explicam as interrupções e insucessos na operação).

Controle e Identificação do Registro: Booking ID, Customer ID, Booking Status, Cancelled Rides by Customer, Cancelled Rides by Driver, Incomplete Rides. (Aqui estão os identificadores únicos para rastreabilidade, as contagens de eventos críticos e o Booking Status, que funciona como a variável de desfecho (alvo) para classificação do resultado final da reserva).


# Passo 5: Hipóteses Analíticas

H1: Cliente tem uma taxa de cancelamento de corrida de 4%

H2: Motoristas têm uma taxa de cancelamento na corrida de 20%

H3: Os motoristas que têm a maior taxa de cancelamento trabalham de carro

H4: Os passageiros de moto têm maior taxa de cancelamento em comparação com os que pedem carro

H5: Os clientes que mais cancelam é porque mudaram de ideia

H6: Os clientes que menos cancelam é porque o motorista forçou o cancelamento

H7: As corridas que têm mais cancelamentos são as mais baratas

H8: Os motoristas cancelam porque a corrida é longa e o retorno é baixo para eles

H9: Motoristas com baixa avaliação cancelam mais

Fiz no início apenas 4 Hipóteses para quebrar o gelo. Isso é uma análise exploratória do dataframe com base na pergunta fechada que o Analista de Dados Sr (Gustavo Shelby) me sugeriu.

**Hipótese Inicial → Rodar Excel/Análise → Obter Insight → Questionar o Insight → Gerar Nova Hipótese → Rodar Nova Análise.**

# Passo 6: Critérios de Priorização

- **Critério 1:** Dados disponíveis.
- **Critério 2:** Insights acionáveis.

# Passo 7: Priorização das Hipóteses Analíticas

H1: Cliente tem uma taxa de cancelamento de corrida de 4%

H2: Motoristas têm uma taxa de cancelamento na corrida de 20%

H3: Os motoristas que têm a maior taxa de cancelamento trabalham de carro

H4: Os passageiros de moto têm maior taxa de cancelamento em comparação com os que pedem carro

H5: Os clientes que mais cancelam é porque mudaram de ideia

H6: Os clientes que menos cancelam é porque o motorista forçou o cancelamento

H7: As corridas que têm mais cancelamentos são as mais baratas

H8: Os motoristas cancelam porque a corrida é longa e o retorno é baixo para eles

H9: Motoristas com baixa avaliação cancelam mais

# Insights da análise

# Resultados

**📥 Baixe a apresentação em PowerPoint (clique no link e, em seguida, em "Download" ou "View raw"):**  
  [https://docs.google.com/presentation/d/1XHxmh7erL-NnA13BMChkJsRH5zSv07E2/edit?usp=drive_link&ouid=114029927907630112086&rtpof=true&sd=true](https://docs.google.com/presentation/d/1XHxmh7erL-NnA13BMChkJsRH5zSv07E2)

# Próximos passos

Fazer o acompanhamento das futuras correções no sistema de punição dos motoristas para verificar se houve redução na taxa de cancelamento por parte de clientes e motoristas.

Este é o retrato do sintoma. Na próxima fase, precisamos responder: isso acontece porque as corridas têm baixo valor? Porque a distância até o embarque é grande? Ou trata-se apenas de má-fé?

Vamos cruzar os 25% de cancelamentos dos clientes e dos motoristas com o tempo de espera e o valor da corrida para identificar a causa principal e definir se a solução deve ser punitiva ou baseada em reajustes no repasse aos motoristas.
