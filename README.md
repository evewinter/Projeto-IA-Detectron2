## Detecção Automática de Pessoas em Ambientes Universitários

Este projeto aplica técnicas de Inteligência Artificial utilizando Redes Neurais Convolucionais (CNN) para identificar a presença de pessoas em ambientes reais do Campus da UFC. O sistema foi desenvolvido como parte da disciplina de Inteligência Artificial 2025.2.


![WhatsApp Image 2026-01-21 at 15 02 17 (1)](https://github.com/user-attachments/assets/57a9e071-5b18-469f-a41f-caca2130652f)


## 📌 Descrição do Projeto
O objetivo principal é o desenvolvimento de um sistema de detecção automática com foco em aplicações de monitoramento e análise de ocupação de espaços. Utilizamos a técnica de Fine-Tuning em um modelo pré-treinado do framework Detectron2.

- Cenário Escolhido: Biblioteca do Campus.

- Aquisição de Dados: Fotos tiradas com o celular.

- Volume de Dados: 32 imagens rotuladas manualmente.



## 🛠️ Tecnologias e Ferramentas
- Linguagem: Python 3.11

- Framework Principal: Detectron2 (Facebook AI Research)

- Bibliotecas Auxiliares: PyTorch, OpenCV, NumPy

- Rotulagem: Roboflow (formato COCO-like)

- Ambiente de Execução: Google Colab (GPU T4)



## 📂 Estrutura do Repositório

projeto-deteccao-pessoas/

├── data/

│ ├── images/ # Imagens originais da biblioteca

│ └── annotations/ # Arquivos JSON no formato COCO

├── training/

│ └── train.py # Script para execução do fine-tuning

├── inference/

│ └── test_model.py # Script para teste em novas imagens

├── utils/

│ └── dataset_utils.py # Utilitários para conversão/ajuste do dataset

├── results/

│ ├── metrics/ # Gráficos de perda e precisão

│ └── images/ # Exemplos visuais das detecções

├── requirements.txt # Dependências do projeto

└── README.md



## 🚀 Como Executar
1. Preparação do Ambiente
Recomendamos o uso do Google Colab pela exigência do GPU. Instale as dependências necessárias:

pip install -r requirements.txt

O dataset deve estar organizado na estrutura: data/images (todas as fotos) e data/annotations (arquivos .json de treino e teste).

Caso utilize o arquivo ZIP gerado pelo Roboflow, o script de “Instalação e Organização” fará a distribuição automática das pastas.

2. Treinamento
O modelo foi adaptado para detectar exclusivamente a classe person. Para iniciar o treino:

python training/train.py

O script registrará o dataset no formato COCO e iniciará o fine-tuning do modelo COCO-Detection/faster_rcnn_R_50_FPN_3x.yaml por um número definido de iterações.

3. Teste e Inferência
Para validar o modelo com imagens que não foram usadas no treinamento:

python inference/test_model.py

Após o treino, o modelo final (model_final.pth) será salvo na pasta output.


## 📊 Resultados e Avaliação

### Configurações do Modelo

- Modelo Base: COCO-Detection/faster_rcnn_R_50_FPN_3x.yaml.

- Iterações: 800.

- Batch Size: 2.

- Taxa de Aprendizado (Base LR): 0.00025.

### Métricas de Desempenho

Os resultados obtidos após o processo de fine-tuning foram:

- mAP (mean Average Precision): 0.527

- Precision: 1.000

- Recall: 0,640

 ![WhatsApp Image 2026-01-21 at 15 02 18](https://github.com/user-attachments/assets/fea4d7a5-8459-434c-8e4b-65eec32bd2d8)

 ![WhatsApp Image 2026-01-21 at 15 02 17 (2)](https://github.com/user-attachments/assets/8958b08b-7fc1-4ea6-8e46-7a7aac2b4364)

 ![WhatsApp Image 2026-01-21 at 15 02 17](https://github.com/user-attachments/assets/786640b6-c8b6-4442-a975-f885fc550cb1)

 ![WhatsApp Image 2026-01-21 at 15 02 16](https://github.com/user-attachments/assets/5bb86b1b-4ff9-4ad4-ae5b-441d853cb326)


## ⚠️ Aplicação em Segurança da Informação
A detecção automática de pessoas é um componente crítico para a Segurança Física de Instalações, que é um dos domínios da Segurança da Informação. As aplicações práticas deste projeto incluem:

Controle de Acesso e Intrusão: O sistema pode ser integrado a câmeras de CFTV para alertar automaticamente a presença de pessoas em áreas restritas (como servidores ou laboratórios de pesquisa) fora do horário permitido.

Análise de Comportamento e Ocupação: Monitorar a lotação de ambientes em tempo real para garantir conformidade com normas de segurança.

Redução de Falha Humana: Automatizar a vigilância reduz a fadiga de operadores humanos que precisam monitorar múltiplas telas, garantindo que eventos críticos não passem despercebidos.

----------
Desenvolvido por: Calina Evelly Oliveira da Silva (571103) & Layna Gonçalves Clemente(565858).

Professor: Juan Sebastian Toquica Arenas

Instituição: Universidade Federal do Ceará (UFC)
----------


