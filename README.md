# Atividade-16-10-2024
Modelagem de Banco de Dados para FarmTech Solutions
##1) Informações Relevantes e Dados Necessários:

Para construir um sistema eficaz de armazenamento e análise de dados para a FarmTech Solutions, precisamos identificar as informações relevantes e os dados necessários para gerá-las. Com base no cenário apresentado, podemos destacar as seguintes informações e seus respectivos dados:

Informações:

Consumo de água:
Quantidade total de água aplicada por período (dia, semana, mês, etc.).
Quantidade de água aplicada por cultura e por área.
Variação do consumo de água ao longo do tempo.
Dados necessários:
Data e hora do ajuste de aplicação de água.
Quantidade de água aplicada.
Cultura.
Área da plantação.
Níveis de pH do solo:
Variação do pH do solo ao longo do tempo.
Níveis de pH por cultura e por área.
Dados necessários:
Data e hora das leituras do sensor de pH.
Valores de pH registrados.
Cultura.
Área da plantação.
Níveis de nutrientes do solo:
Níveis de fósforo (P) e potássio (K) no solo.
Variação dos níveis de nutrientes ao longo do tempo.
Níveis de nutrientes por cultura e por área.
Dados necessários:
Data e hora das leituras do sensor de nutrientes.
Valores de P e K registrados.
Cultura.
Área da plantação.
Previsão de necessidades:
Previsão da necessidade de água e nutrientes por cultura e por área.
Dados necessários:
Dados históricos de consumo de água e níveis de nutrientes.
Dados climáticos (temperatura, umidade, precipitação).
Otimização de recursos:
Identificação de áreas com consumo excessivo ou deficiente de água e nutrientes.
Recomendações para otimizar o uso de recursos.
Dados necessários:
Dados de consumo de água e níveis de nutrientes.
Dados de produção.

##2) Entidades e Atributos (MER):

Com base nas informações e dados identificados, podemos definir as seguintes entidades e atributos para o MER:

Entidade Sensor:

ID_Sensor (Chave Primária)
Tipo_Sensor (S1, S2 ou S3)
Localização (varchar) - Descrição da localização do sensor na plantação
Entidade Cultura:

ID_Cultura (Chave Primária)
Nome_Cultura (varchar)
Descricao (varchar) - Informações adicionais sobre a cultura
Entidade Área:

ID_Área (Chave Primária)
Tamanho (double) - em hectares
Localização (varchar) - Descrição da localização da área na plantação
ID_Cultura (Chave Estrangeira)
Entidade Leitura:

ID_Leitura (Chave Primária)
ID_Sensor (Chave Estrangeira)
ID_Área (Chave Estrangeira)
Data_Hora (datetime)
Valor (double) - Valor da leitura do sensor (umidade, pH, P ou K)
Entidade Irrigação:

ID_Irrigação (Chave Primária)
ID_Área (Chave Estrangeira)
Data_Hora (datetime)
Quantidade_Agua (double) - em litros
Entidade Nutriente:

ID_Nutriente (Chave Primária)
ID_Área (Chave Estrangeira)
Data_Hora (datetime)
Tipo_Nutriente (varchar) - (N, P ou K)
Quantidade (double) - em kg

##3) Cardinalidade dos Atributos:

A cardinalidade dos atributos indica a quantidade de valores que um atributo pode assumir para cada instância da entidade. No contexto do nosso MER, temos:

ID_Sensor, ID_Cultura, ID_Área, ID_Leitura, ID_Irrigação, ID_Nutriente: (1,1) - Cada entidade possui um único ID.
Tipo_Sensor: (1,1) - Cada sensor possui um único tipo.
Localização (Sensor e Área): (1,1) - Cada sensor e cada área possuem uma única localização.
Nome_Cultura: (1,1) - Cada cultura possui um único nome.
Descricao (Cultura): (0,1) - Uma cultura pode ou não ter uma descrição adicional.
Tamanho (Área): (1,1) - Cada área possui um único tamanho.
ID_Cultura (Área): (1,1) - Cada área está associada a uma única cultura.
ID_Sensor (Leitura): (1,1) - Cada leitura é realizada por um único sensor.
ID_Área (Leitura, Irrigação e Nutriente): (1,1) - Cada leitura, irrigação e aplicação de nutriente ocorre em uma única área.
Data_Hora (Leitura, Irrigação e Nutriente): (1,1) - Cada leitura, irrigação e aplicação de nutriente possui uma única data e hora.
Valor (Leitura): (1,1) - Cada leitura possui um único valor.
Quantidade_Agua (Irrigação): (1,1) - Cada irrigação possui uma única quantidade de água.
Tipo_Nutriente (Nutriente): (1,1) - Cada aplicação de nutriente possui um único tipo de nutriente.
Quantidade (Nutriente): (1,1) - Cada aplicação de nutriente possui uma única quantidade.


##4) Relacionamento entre Entidades (MER):

O relacionamento entre as entidades define como elas se conectam e interagem entre si. No nosso MER, temos os seguintes relacionamentos:

Sensor - Leitura: Um sensor realiza várias leituras (1:N).
Área - Leitura: Uma área possui várias leituras (1:N).
Área - Irrigação: Uma área recebe várias irrigações (1:N).
Área - Nutriente: Uma área recebe várias aplicações de nutrientes (1:N).
Cultura - Área: Uma cultura pode ser plantada em várias áreas (1:N).

##5) Tipo de Dado dos Atributos:

ID_Sensor, ID_Cultura, ID_Área, ID_Leitura, ID_Irrigação, ID_Nutriente: Inteiro (INT)
Tipo_Sensor: Texto (VARCHAR) - (S1, S2 ou S3)
Localização (Sensor e Área): Texto (VARCHAR)
Nome_Cultura: Texto (VARCHAR)
Descricao (Cultura): Texto (VARCHAR)
Tamanho (Área): Número decimal (DOUBLE)
Data_Hora (Leitura, Irrigação e Nutriente): Data e hora (DATETIME)
Valor (Leitura): Número decimal (DOUBLE)
Quantidade_Agua (Irrigação): Número decimal (DOUBLE)
Tipo_Nutriente (Nutriente): Texto (VARCHAR) - (N, P ou K)
Quantidade (Nutriente): Número decimal (DOUBLE)
