# DETECÇÃO DE FRAUDES EM CARTÕES DE CRÉDITO
Exercício de detecção de fraudes em cartões de crédito usando machine learning com a Prof. Isadora Ferrão

<strong>Introdução </strong>

O projeto de detecção de fraudes em cartões de crédito visa identificar transações fraudulentas para proteger os consumidores e as instituições financeiras. A fraude é uma ação deliberada que causa prejuízo a terceiros, e a análise de dados é fundamental para detectar comportamentos atípicos em grandes volumes de transações.

<strong>Conjunto de Dados</strong>

O conjunto de dados utilizado contém transações de cartões de crédito realizadas em setembro de 2013 por titulares de cartões europeus. Com 284.807 transações, apenas 492 são fraudes, resultando em uma proporção de 0,172% de fraudes, o que caracteriza um problema de desbalanceamento de classes.

<strong>Objetivo</strong>

O objetivo é aplicar técnicas de aprendizado de máquina para identificar transações fraudulentas, minimizando perdas financeiras e aumentando a segurança.

<strong>Análise e Pré-processamento</strong>

<strong>Importação de Bibliotecas</strong>

O código começa importando as bibliotecas necessárias:

<img width="639" alt="Screenshot_96" src="https://github.com/user-attachments/assets/3f0e005b-8939-47f4-9643-f74ee88b9cd1" />



O dataset é carregado e informações básicas são exibidas:


<img width="600" alt="Screenshot_97" src="https://github.com/user-attachments/assets/8c8b620d-0a77-43e6-b713-3facab84ff7c" />

<img width="867" alt="Screenshot_98" src="https://github.com/user-attachments/assets/64c92166-79f6-45a8-a99c-216bc7c374f6" />

<img width="163" alt="Screenshot_99" src="https://github.com/user-attachments/assets/a1a95b52-5fc2-4cba-b21e-9478d6c134f8" />


<strong>Análise da Distribuição</strong>

A distribuição das classes (fraudes vs. não fraudes) é analisada:

<img width="295" alt="Screenshot_100" src="https://github.com/user-attachments/assets/5bc12a0d-b6ff-462c-aa72-b8e47bf188ae" />

A análise mostra que a maioria das transações é legítima, com um pequeno número de fraudes.
A coluna "Amount" mostra a "quantia" , demonstrando o pico de valor no caso de fraude:

<img width="345" alt="Screenshot_101" src="https://github.com/user-attachments/assets/e9a46c6c-f412-4d25-a957-dec1c844493d" />

<strong>Normalização dos Dados</strong>

A coluna "Amount" é normalizada para melhorar a performance do modelo:

<img width="515" alt="Screenshot_108" src="https://github.com/user-attachments/assets/47e6f3ba-def2-408d-b01b-20f1873cdf50" />

<strong>Detecção de Anomalias com Isolation Forest</strong>

Um modelo de Isolation Forest é utilizado para detectar fraudes. 
Isso gera uma nova coluna no DataFrame de nome IF_Pred que indica se uma transação é considerada uma fraude.

<img width="828" alt="Screenshot_103" src="https://github.com/user-attachments/assets/0d628128-370a-48df-96d5-5992ada54fdc" />

Visualizando valores preditos:

<img width="401" alt="Screenshot_104" src="https://github.com/user-attachments/assets/d5908bf2-7ac3-4ec0-92b6-0629b49726d8" />

<strong>Avaliação do Modelo</strong>

A matriz de confusão é calculada para avaliar o desempenho do modelo:

<img width="403" alt="Screenshot_105" src="https://github.com/user-attachments/assets/b3d2e022-8c45-4204-8178-fd49e573f9b2" />

Verdadeiros Negativos (TN): 283969

Falsos Positivos (FP): 346

Falsos Negativos (FN): 353

Verdadeiros Positivos (TP): 139

Métricas de Desempenho:

Acurácia: 1.00

Precisão: 0.29

Recall: 0.28

<strong>Modelagem com Random Forest</strong> 

Um pipeline é criado para aplicar SMOTE e treinar um classificador Random Forest:

<img width="582" alt="Screenshot_106" src="https://github.com/user-attachments/assets/3f2422bc-c05d-4741-a70d-c3d62fff03bf" />

<strong>Validação Cruzada</strong>

A validação cruzada é realizada para avaliar a robustez do modelo. Os resultados da validação cruzada mostram a média das métricas:

Acurácia média: 1.00
Precisão média: 0.49
Recall médio: 0.84

<strong>Conclusões</strong>

<ul>
<li>Desbalanceamento de Dados: O conjunto de dados é altamente desbalanceado, o que torna a detecção de fraudes um desafio.</li>
<li>>Eficácia do Isolation Forest: O modelo Isolation Forest mostrou-se eficaz na identificação de fraudes, embora a precisão e o recall devam ser monitorados.</li>
<li>Uso de SMOTE: O uso de SMOTE ajudou a melhorar o desempenho do modelo Random Forest, aumentando a representação da classe minoritária.</li>
</ul>

<strong>Importância do Projeto</strong>
A detecção de fraudes em cartões de crédito é crucial para a segurança financeira. Este projeto não só ajuda a reduzir perdas financeiras, mas também melhora a confiança dos consumidores nas instituições financeiras, promovendo um ambiente de transações mais seguro.

<strong>Referência</strong>
Os dados utilizados estão disponíveis em: Kaggle - Credit Card Fraud Detection.

