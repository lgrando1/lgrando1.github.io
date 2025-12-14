---
abstract: Veículos Aéreos Não Tripulados (VANT), ou drones, estão sendo aplicados em diversas áreas, como na agricultura de precisão, na recuperação de desastres e no combate ao mosquito da dengue. No entanto sua baixa autonomia de voo (entre 20 e 30 minutos) limita sua aplicação nestas atividades. Para mitigar este problema, pode ser realizado a substituição da fonte de energia, otimizar o planejamento da rota/missão destes dispositivos e coordenar a decisão de recargas das baterias. Este trabalho propõe um modelo de simulação baseado em agentes para estudar o comportamento de coordenar a decisão interna de dispositivos IoT, utilizando neste exemplo drones, de seu processo de decisão de recarga. Foram desenvolvidos dois cenários de políticas de decisão internas, sendo a primeira política, chamada de política base (BL) direciona os drones para recarga quando a bateria atinge um nível crítico e a segunda política é baseada em um modelo da teoria dos jogos, chamado El Farol Bar (CT), cujo modelo possui um histórico de utilização em problemas de congestão e a natureza deste modelo considera que os agentes não se comunicam entre si, reduzindo o consumo de energia devido à transmissão de dados. A simulação foi implementada no software Netlogo, nela ocorre a simulação da carga e descarga da bateria dos agentes ao executar uma determinada missão e a possibilidade de que eles parem de funcionar caso o processo de recarga não seja suficiente para manter um nível mínimo de energia. A simulação é interrompida quando resta pelo menos um drone com bateria ou após 1.500 unidades de tempo. A performance do modelo é avaliada por dois indicadores de confiabilidade deste sistema, definido como os valores médios de simulações finalizadas em relação ao total e a quantidade de drones que finalizaram estas simulações. Foram considerados 15 níveis de consumo média de energia, as duas políticas e dois tamanho de estação de recargas resultando em 60 casos e cada um destes repetidos 100 vezes, resultando em 6000 rodadas de simulação. Como resultados observamos que o modelo CT supera o modelo BL em condições em que o sistema exige maior consumo médio de bateria pelos drones, nesta condição, o sistema BL falha em manter um número mínimo de drones operacionais para completar suas missões. Na condição de um menor consumo de energia média do sistema ambos os modelos se comportaram da mesma forma, onde todos os drones conseguem terminar a simulação. Espera-se que esta abordagem possa ser expandida para outras áreas como a gestão de recarga de carros autônomos, contribuindo para a otimização de sistemas distribuídos.
address:
  #city: Limeira
  country: Brazil
  # postcode: "94305"
  # region: SP
  # street: 450 Serra Mall
all_day: false
authors: []
date: "2024-09-11T13:30:00Z"
date_end: "2024-09-11T14:30:00Z"
event: XV Workshop da Pós Graduação da Faculdade de Tecnologia - UNICAMP  
event_url: https://wordpress.ft.unicamp.br/workshoppos/edicao-2024/
featured: false
eventAttendanceMode: Presential
eventStatus: EventScheduled
location: Limeira-SP
organizer: Faculdade de Tecnologia - Unicamp
projects:
- example
publishDate: "2024-11-19T13:30:00Z"
summary: "I presented the status of my September 2024 Ph.D. research **Análise de consumo de bateria de dispositivos usados em IoT (Internet das Coisas)** at the XV FT Unicamp Workshop."
tags: ["Agent-Based", "Simulation", "presentation", "Drones", "Farm" ]
title: "XV Workshop da Pós Graduação da Faculdade de Tecnologia - UNICAMP"
#url_code: ""
url_pdf: "https://lgrando1.github.io/uploads/workshoppos2024.png"
#url_slides: https://lgrando1.github.io/uploads/workshoppos2024.png
#url_video: ""
---

