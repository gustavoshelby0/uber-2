# Análise de "No Driver Found" da Uber

# Problema de Negócio

Problema de Oferta vs. Demanda (Vazamento de Receita)
Os dados: Existem centenas de ocorrências de "No Driver Found" (Nenhum Motorista Encontrado) espalhadas por várias localidades e horários.

O problema de negócio: A plataforma está deixando dinheiro na mesa. Toda vez que um cliente não encontra motorista, a Uber perde 100% da receita daquela viagem.

Impacto: Perda de Market Share em regiões periféricas (ex.: Noida Extension, Greater Noida) e ineficiência na precificação dinâmica (surge pricing) para atrair motoristas para essas áreas no momento certo.

# Premissas da análise

Foi analisado o fenômeno "No Driver Found" (Nenhum Motorista Encontrado).
Foram analisadas 150.000 corridas da Uber. 
Os dados são referentes ao ano de 2024, e as corridas analisadas foram realizadas na Índia.


# Estratégia da solução

O método Fato-Dimensão foi usado para desenvolver a análise de dados.

# Passo 1: Resumir o contexto em uma pergunta aberta

As perguntas abertas são um tipo de demanda muito comum em análise de dados nas quais a demanda possui N possíveis soluções e cabe ao analista de dados avaliar as possibilidades e escolher a alternativa com o maior retorno e o menor esforço possível. Para essa análise, foi definida a seguinte pergunta aberta:

como a Uber pode resolver o problema de "No Driver Found" (Nenhum Motorista Encontrado)

# Passo 2: Transformar pergunta aberta em fechada

As perguntas fechadas são um tipo de demanda muito comum na área de análise de dados. Essa demanda contém todos os detalhes da análise de dados e direciona o analista exatamente para o que precisa ser feito. Geralmente, a pergunta fechada é a escolha de uma solução entre todas as alternativas possíveis, feita por um profissional mais sênior da área.

Para essa análise, foi definida a seguinte pergunta fechada:

Pergunta Fechada: Calcule a taxa de corridas perdidas pela Uber por causa do fenômeno "No Driver Found".

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

H1: A taxa de corridas perdidas pela Uber é de 2% quando olhado para o "No Driver Found".

H2: O "No Driver Found" só acontece quando o passageiro está no ponto de partida na cidade grande.

H3: O "No Driver Found" é alto quando o ponto de desembarque é na cidade grande.

H4: O "No Driver Found" tem a maior taxa quando é no Uber XL, porque esse veículo tem pouca disponibilidade.

H5: O "No Driver Found" acontece com maior frequência à noite, no período noturno (6 às 12pm).

Fiz no início apenas 4 Hipóteses para quebrar o gelo. Isso é uma análise exploratória do dataframe com base na pergunta fechada que o Analista de Dados Sr (Gustavo Shelby) me sugeriu.

**Hipótese Inicial → Rodar Excel/Análise → Obter Insight → Questionar o Insight → Gerar Nova Hipótese → Rodar Nova Análise.**

# Passo 6: Critérios de Priorização

- **Critério 1:** Dados disponíveis.
- **Critério 2:** Insights acionáveis.

# Passo 7: Priorização das Hipóteses Analíticas

H1: A taxa de corridas perdidas pela Uber é de 2% quando olhado para o "No Driver Found".

H2: O "No Driver Found" só acontece quando o passageiro está no ponto de partida na cidade grande.

H3: O "No Driver Found" é alto quando o ponto de desembarque é na cidade grande.

H4: O "No Driver Found" tem a maior taxa quando é no Uber XL, porque esse veículo tem pouca disponibilidade.

H5: O "No Driver Found" acontece com maior frequência à noite, no período noturno (6 às 12pm).

# Insights da análise

# Resultados

**📥 Baixe a apresentação em PowerPoint (clique no link e, em seguida, em "Download" ou "View raw"):**  
  [https://docs.google.com/presentation/d/1jrQ17n-un9UXdU5uls8ValpbZDV1kk1F/edit?usp=sharing&ouid=114029927907630112086&rtpof=true&sd=true](https://docs.google.com/presentation/d/1jrQ17n-un9UXdU5uls8ValpbZDV1kk1F/edit?usp=sharing&ouid=114029927907630112086&rtpof=true&sd=true)

# Próximos passos

Fazer o acompanhamento das futuras mudanças que a diretoria poderá implementar na cidade de Delhi (Índia).

Este é o retrato do sintoma. Na próxima fase, precisamos responder: isso acontece porque as corridas têm baixo valor monetário para o motorista? Ou porque a distância até o embarque é muito grande?

Para isso, será necessário cruzar os 7% de perdas por "No Driver Found" com o tempo médio de espera dos motoristas por região, e com o valor médio recebido por corrida, a fim de identificar a principal causa do problema.
