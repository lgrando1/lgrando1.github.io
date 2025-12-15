---
title: 'Procedimento de recarga de baterias de drones utilizando simulação por agentes e equilíbrio de Nash'

# Authors
# If you created a profile for a user (e.g. the default `admin` user), write the username (folder name) here
# and it will be replaced with their full name and linked to their profile.
authors:
  - admin

# Author notes (optional)

date: '2020-08-21T00:00:00Z'
# doi: 'https://doi.org/10.47749/T/UNICAMP.2020.1149276' # <--- REMOVIDO

# Schedule page publish date (NOT publication's date).
#publishDate: '2017-01-01T00:00:00Z'

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ['7']

# Publication name and optional abbreviated publication name.
publication: My Master Thesis
publication_short:  Universidade Estadual de Campinas (UNICAMP)

abstract: This work seeks to solve one of the most critical problems of the Flying AdHoc (FANET) networks, which is the issue of coordinating the recharging of drones that fly in the form of Swarms. For recharging to be done in the best possible way, it is desirable that the number of charging devices (base stations) did not be excessively high due to the high implementation cost. Conversely, it is also necessary that, when drones want to recharge, they must have a source of energy available. In other words, we search for a balance between the economically viable number of charging stations and the adequate energy supply for the drones when necessary. For this, we propose agents (drones) equipped with internal intelligence, that is, with internal predictors that provide intelligence to attempt to predict the next attendance rate in the charging device and thus be able to decide whether go or not go to the recharging. Ideally, the forecast should be as best as possible. Therefore, the drone should go when it predicts it should go and it shouldn't go when it predicts not to go. The Nash equilibrium usage for this problem is made possible by the modeling via the El Farol Bar Problem (EFBP), which allows the development of this analogy without the collusion of agents in coordinating the simulation of the recharge of this set of drones. In other words, there will be no energy expenditure on communication about the drones' battery recharging coordination, although the communication will continue in the other tasks inherent to the swarm of drones. The verification of the suitability of the proposal is done through Agent-Based Simulation and are used three different policies for the best predictor decision by each drone. This will allow us to verify the performance in the operation of the system through a Nash Equilibrium. In the current state of this analogy is considered that if the drones go to the charging station and it is full, there will be no possible charging because the system is overloaded. This study includes microscopic and macroscopic analysis. Microscopic analysis is the evaluation of the performance of the rewards of each predictor concerning a set of simulation parameters, aiming at a microscopic behavior performance improvement. A macroscopic analysis is the evaluation of the performance of the global service of the system with three types of policies. This latter analysis is used as a basis for evaluating the drone's recharge analogy. In this way, the performance of the best simulation sets for the recharge of drones is evaluated, which allows supplying below the control threshold (attendance below than the number of recharge positions), but which are relatively close to the threshold.

# Summary. An optional shortened abstract.
#summary: Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis posuere tellus ac convallis placerat. Proin tincidunt magna sed ex sollicitudin condimentum.

tags: [Drones, Simulation, Agent-Based, Nash Equilibrium]

# Display this page in the Featured widget?
featured: true

# Custom links (substituindo url_pdf)
links:
  - name: PDF (UNICAMP Repositório)
    url: 'http://repositorio.unicamp.br/Acervo/Detalhe/1149276'
    icon: hero/document-text
    
# Os campos abaixo foram removidos ou são redundantes com a nova estrutura de `links`:
# url_pdf: 'http://repositorio.unicamp.br/Acervo/Detalhe/1149276' # <--- REMOVIDO
# url_code: 'https://github.com/wowchemy/wowchemy-hugo-themes'
# url_dataset: 'https://github.com/wowchemy/wowchemy-hugo-themes'
# url_poster: ''
# url_project: ''
# url_slides: ''
# url_source: 'https://github.com/wowchemy/wowchemy-hugo-themes'
# url_video: 'https://youtube.com'

# Novo bloco para DOI (Identificadores)
hugoblox:
  ids:
    doi: 'https://doi.org/10.47749/T/UNICAMP.2020.1149276'

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
#image:
#  caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/pLCdAaMFLTE)'
#  focal_point: ''
#  preview_only: false

# Associated Projects (optional).
#   Associate this publication with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `internal-project` references `content/project/internal-project/index.md`.
#   Otherwise, set `projects: []`.
#projects:
#  - example

# Slides (optional).
#   Associate this publication with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides: "example"` references `content/slides/example/index.md`.
#   Otherwise, set `slides: ""`.
#slides: example
---