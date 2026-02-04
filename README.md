# 🤖 EcoTrack - Robot Inteligente de Monitorização Ambiental

**Universidade:** IADE – Universidade Europeia  
**Faculdade:** Faculdade de Design, Tecnologia e Comunicação  

## 🏫 Identificação do Projeto
**Curso:** Engenharia Informática  
**Unidade Curricular:** PBL – Sistemas Distribuídos, IoT, IA e Engenharia de Software  
**Ano letivo:** 2025/2026  
**Grupo:** 1  
**Título do Projeto:** EcoTrack - Robot Inteligente de Monitorização Ambiental
**Palavras-chave:** IoT, ESP32, Inteligência Artificial, Robótica, Sensores

**Repositório GitHub:** https://github.com/Rubenmpff/Robo-inteligente-monitorizacao-ambiental  

---

## 🧠 Problema Identificado

Em muitos espaços interiores, **não existe um sistema acessível e autónomo que permita acompanhar a qualidade do ambiente em tempo real**, nomeadamente os níveis de **temperatura, humidade, ruído**.  
Esta falta de monitorização pode afetar o **conforto e bem-estar das pessoas**, especialmente em **ambientes domésticos e escolares**, onde a qualidade ambiental influencia a concentração, o desempenho e a saúde.

Além disso, as soluções existentes no mercado são geralmente **fixas, caras e pouco interativas**, não permitindo mobilidade nem integração com sistemas inteligentes.  
Assim, torna-se relevante desenvolver uma solução **móvel, acessível e inteligente** que recolha, processe e apresente informações ambientais de forma **dinâmica e interativa**.

---


## 🎯 Público-Alvo

O projeto **Robô Inteligente de Monitorização Ambiental** é direcionado a **utilizadores e organizações que necessitam de acompanhar e otimizar as condições ambientais em espaços interiores**.  
O sistema destina-se a **habitações, escolas, escritórios, laboratórios e espaços públicos**, onde a monitorização de fatores como **temperatura, humidade e ruído** é essencial para garantir o **conforto, a produtividade e o bem-estar das pessoas**.  

Este tipo de solução é particularmente útil em **ambientes onde o controlo climático e acústico influencia o desempenho das atividades**, como salas de aula, bibliotecas, centros de trabalho colaborativo ou áreas comerciais.  
O robô permite recolher dados, processá-los localmente e comunicar alertas ou recomendações, promovendo uma **gestão mais eficiente e inteligente do ambiente**.  


---

## 🎯 Objetivo do Projeto

O projeto tem como objetivo desenvolver um **robô inteligente de monitorização ambiental**, baseado na plataforma **ESP32**, que seja capaz de:

- 📡 **Recolher dados ambientais** em tempo real (temperatura, humidade, som);  
- 🚗 **Deslocar-se** pelo espaço, detetando obstáculos;  
- 🧠 **Processar localmente as informações** e reagir de forma inteligente;
- 🗣️ **Comunicar com o utilizador** e apresentar dados no ecrã e em LEDs;
- 💾 **Armazenar dados** para análise posterior e possíveis previsões.  

Este sistema pretende demonstrar a integração entre **IoT (Internet of Things)**, **Inteligência Artificial** e **Engenharia de Software**, aplicadas ao contexto de **monitorização ambiental**.

---


## 🔧 Levantamento de Hardware e Software

### 🧩 Hardware

| Componente | Quantidade | Função |
|-------------|-------------|--------|
| ESP32 DevKit | 1 | Microcontrolador principal |
| DHT22 | 1 | Sensor de temperatura e humidade |
| HC-SR04 | 2 | Detectar obstáculos e distância |
| INMP441 | 1 | Microfone digital (nível de som) |
| LM2596  | 1 | Regulador de tensão |
| OLED 0.96” | 1 | Mostrar expressões e dados |
| 1 LED RGB (KY-016) | 1 | Feedback visual (cor por nível de som/estado) |
| L298N | 1 | Ponte H para controlo dos motores | 
| Motores DC + rodas | 4 | Locomoção do robot |
| Pilhas | 1 | Alimentação |
| Breadboard e jumpers | — | Ligações e prototipagem |
| Chassis robótico 4WD | 1 | Estrutura física do robot |


---

### 💻 Software

| Software / Tecnologia | Função |
|------------------------|--------|
| Arduino IDE  | Programação do ESP32 |
| Python | Processamento de dados e IA |
| Flask | Servidor local e API REST |
| SQLite | Armazenamento de dados |
| GitHub | Controlo de versões e documentação |
| Draw.io / Canva | Criação de diagramas |
| Wokwi | Simulação de circuitos e sensores |

---


## ⚙️ Desenho da Infraestrutura Computacional

O sistema é composto por dois módulos principais:  
- **Módulo físico (robô inteligente)** — responsável pela recolha de dados, movimento e interação.  
- **Módulo lógico (servidor local)** — responsável por processar, armazenar e visualizar as informações recolhidas pelo robot.

O robot utiliza o **ESP32** como controlador central, comunicando com sensores, atuadores e periféricos através de ligações digitais e analógicas.  
Os dados recolhidos são processados localmente e, quando disponível uma ligação Wi-Fi, são enviados para o **servidor local**, onde são armazenados numa **base de dados SQLite** e apresentados numa **interface web** desenvolvida em **Python**.

---

### 🧭 Arquitetura geral do sistema

    +-------------------------------------------+
    |               Servidor Local              |
    |-------------------------------------------|
    |  • Python                                 |
    |  • Base de Dados (SQLite)                 |
    |  • Interface Web de Monitorização         |
    +--------------------^----------------------+
                         |
                  Wi-Fi (Local Network)
                         |
    +--------------------v----------------------+
    |                Robot ESP32                 |
    |-------------------------------------------|
    |  • ESP32 DevKit                          |
    |  • Sensores: DHT22, HC-SR04              |
    |  • LM2596                                |
    |  • OLED Display + LED RGB (KY-016)       |
    |  • Ponte H L298N + Motores DC            |
    |  • Pilhas                                |
    |-------------------------------------------|
    |  • Recolhe dados ambientais              |
    |  • Reage a som e obstáculos              |
    |  • Envia dados para o servidor           |
    +-------------------------------------------+


---

### 🛰️ Comunicação entre módulos

| Canal | Direção | Função |
|--------|----------|--------|
| **Wi-Fi (MQTT / HTTP)** | ESP32 ↔ Servidor | Envio de dados e controlo remoto |
| **I2C** | ESP32 → OLED / DHT22 | Comunicação com sensores e ecrã |
| **I2S** | INMP441 → ESP32 | Transmissão de áudio digital |
| **GPIO / PWM** | ESP32 ↔ Motores / LED RGB | Controlo de movimento e feedback visual |

---

## 🤖 Esboço do Artefacto Físico

O artefacto físico é composto por uma base robótica 4WD com:
- Estrutura em plástico;
- Sensores (DHT22, HC-SR04, INMP441);
- Ecrã OLED representando o “rosto” do robot;
- LEDs WS2812B para feedback visual e reação a som;
- Microfone integrado (INMP441);
- LM2596 Regulador de tensão;
- Ponte H L298N;
- Alimentação por Pilhas;

![WhatsApp Image 2025-12-15 at 16 18 04](https://github.com/user-attachments/assets/4ef5c40a-4118-428f-b5c8-6cd4a571f7f6)
![WhatsApp Image 2025-12-15 at 16 18 05](https://github.com/user-attachments/assets/8914ecf7-702d-4fb0-a970-c5c8bdb74529)


---


## 📋 Lista Preliminar de Materiais

| Categoria | Elemento | Quantidade | Observações |
|------------|-----------|-------------|-------------|
| 🧠 Microcontrolador | ESP32 DevKit | 1 | Controlador principal do robô |
| 🌡️ Sensores | DHT22, HC-SR04, INMP441 | — | Recolha de dados ambientais (temperatura, humidade, distância, som) |
| 🚗 Movimento | L298N + Motores DC | 1 + 4 | Ponte H e motores para locomoção |
| 💡 Feedback | OLED 0.96" + LED RGB (KY-016) | 1 + 1 | Ecrã e LED RGB para expressões e reação a som |
| 🔋 Energia | Pilhas | 1  | Alimentação |
| 🧱 Estrutura | Chassis robótico 4WD | 1 | Base física com rodas e suporte |
| 🔌 Ligações | Breadboard, jumpers, resistências 220 Ω | — | Montagem e prototipagem dos circuitos |

---
## 🧪 Guiões de Teste (Versão Preliminar)

### 🧩 Guião 1 – Monitorização Ambiental
1. Ligar o robot e aguardar a inicialização do sistema.  
2. O robot ativa automaticamente os sensores DHT22, INMP441.  
3. Os valores de temperatura, humidade e nível de som são apresentados no ecrã OLED.
4. Os dados são enviados para o servidor local e registados na base de dados.

### 🎧 Guião 2 – Reação a Som
1. Colocar o robot num ambiente com diferentes níveis de ruído.  
2. O microfone (INMP441) deteta o volume ambiente.  
3. O LED RGB muda de cor conforme o nível de som (verde → azul → vermelho).
4. Quando o som diminui, o LED regressa a verde.

---

## 🧱 Diagrama de Circuitos

<img width="338" height="495" alt="image" src="https://github.com/user-attachments/assets/393c4b65-1b91-4b01-9b0e-2d23687a1dd1" />

---

## 📅 Plano de Trabalho e Distribuição de Tarefas

<img width="950" height="492" alt="image" src="https://github.com/user-attachments/assets/86a857b7-e4ef-437e-a0f6-b6e686bc91d7" />

![WhatsApp Image 2025-12-15 at 18 06 56](https://github.com/user-attachments/assets/4c1d5296-eb26-40e1-820e-d6f29cb4900e)

---

## 🧩 Fases do Projeto

| Fase | Descrição | Estado |
|------|------------|--------|
| 1️⃣ Protótipo base | Movimento, sensores, LEDs e leitura de dados | 🔄 Em desenvolvimento |
| 2️⃣ Integração energética | Alimentação a Pilhas | ⏳ Próxima fase |
| 3️⃣ Inteligência artificial | Predição | 🔜 Planeada |
| 4️⃣ Versão final | Testes, relatório e apresentação | 🟢 Fase final |

---

## 📘 Enquadramento nas Unidades Curriculares

| Unidade Curricular | Contributo do Projeto |
|--------------------|-----------------------|
| **Sistemas Distribuídos** | Implementação da comunicação entre o robô (cliente) e o servidor local (servidor) através de Wi-Fi, com troca de dados em tempo real. |
| **Computação Física e Internet of Things (IoT)** | Integração de múltiplos sensores e atuadores conectados à rede, recolha e envio de dados ambientais. |
| **Inteligência Artificial (IA)** | Processamento de dados ambientais .|
| **Engenharia de Software** | Estruturação modular do código, definição de requisitos, testes, validação e documentação no GitHub. |

---

## 💬 Conclusão

O **Robô Inteligente de Monitorização Ambiental** é uma proposta inovadora que combina **IoT, IA e Engenharia de Software** num sistema físico e interativo.  
O projeto permitirá recolher e analisar dados ambientais, promovendo a eficiência energética e a interação homem–máquina num contexto acessível, educativo e prático.  

O desenvolvimento segue uma abordagem incremental, começando por um protótipo funcional e evoluindo para uma versão inteligente com autonomia, reconhecimento e comunicação.

---

📄 **Autores:**  

Ruben Ferreira

Sofia Leandro

Catarina Cardoso	

📅 **Data:** Novembro 2025  
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# 🧩 Milestone 2 – Desenvolvimento e Prototipagem

## 🧠 1. Descrição da Funcionalidade do Protótipo

Durante esta segunda fase foi desenvolvido e testado o **protótipo funcional RoboESP32 - EcoTrack**, um robot móvel baseado em **ESP32**, capaz de monitorizar o ambiente e interagir com o utilizador.

### ⚙️ Funcionalidades Implementadas

- 🌡️ Leitura de **temperatura e humidade** com **DHT22**
- 📏 **Deteção de obstáculos** com dois **HC-SR04** (frente e trás)
- 🚗 **Controlo de movimento** manual e automático com **L298N**
- 💡 **Visualização de dados** no **ecrã OLED**
- 🔊 **Buzzer** para alertas de proximidade
- 📶 **Comunicação Wi-Fi** com **servidor Flask**
- 💬 **Envio de alertas automáticos** via **Telegram**
- 🧠 **Funções de IA preditiva** *(em desenvolvimento)*

![WhatsApp Image 2025-12-15 at 16 18 03](https://github.com/user-attachments/assets/9db5526d-d877-4317-928e-0888b3b538cb)


https://github.com/user-attachments/assets/05524280-6da5-4680-9f27-0fcea9c01019


---

## ⚙️ 2. Descrição da Solução e Arquitetura Implementada

O sistema segue um **modelo cliente–servidor**, comunicando via **REST API**.

### 🧩 Módulo Físico (ESP32 – Robot IoT)

- Leitura dos sensores (**DHT22**, **HC-SR04**)
- Controlo dos motores (**L298N**)
- Exibição dos dados (**OLED**)
- Envio de dados (**POST /dados**) para o servidor Flask
- Receção de comandos (**GET /api/controlo_robo**)
- Modo automático com lógica de navegação e segurança (Em Desenvolvimento)
- Regulador de tensão (**LM2596**);

### 🖥️ Módulo Lógico (Servidor Flask + Dashboard)

- **Endpoints REST:** `/dados`, `/api/leituras`, `/api/controlo_robo`
- **Base de dados:** SQLite
- **Dashboard web:** HTML + Chart.js
- **Sistema de alertas:** Telegram
- **Módulo de IA:** previsões futuras *(em desenvolvimento)*

---

### 🔄 Fluxo de Comunicação

ESP32 → POST /dados → Servidor Flask
Flask → guarda dados → atualiza Dashboard
Dashboard → POST /api/controlo_robo → Flask → GET no ESP32

<img width="933" height="575" alt="image" src="https://github.com/user-attachments/assets/aabb4d6d-1b8f-4722-94e9-90c3037a54c0" />

---

### 🧱 Arquitetura Geral


![WhatsApp Image 2025-12-15 at 15 31 32](https://github.com/user-attachments/assets/2aae111c-39b7-4c2a-aa1a-cf4ffd649450)


---

## 🔌 3. Diagramas de Circuitos Necessários

### 📍 Ligações Principais

| Componente           | Pinos ESP32                              |
|----------------------|------------------------------------------|
| DHT22                | GPIO 15                                 |
| HC-SR04 (frente)     | TRIG 4 / ECHO 18                        |
| HC-SR04 (trás)       | TRIG 5 / ECHO 19                        |
| L298N                | IN1 13 / IN2 12 / IN3 14 / IN4 27       |
| OLED                 | SDA 21 / SCL 22                         |
| Buzzer               | GPIO 26                                 |
| LM2596               | Regulador de tensão (Em Desenvolvimento)|
| Alimentação          | VIN / GND                               |


### 🔧 Esquema Simplificado


<img width="298" height="159" alt="image" src="https://github.com/user-attachments/assets/c7ae8949-2035-452f-90e7-f0d6d6920476" />


🧰 O diagrama elétrico foi criado no **Wokwi**, com todas as ligações simuladas.  


<img width="343" height="495" alt="image" src="https://github.com/user-attachments/assets/ed34a30a-dfcb-4de3-88b4-41b4dd0767b5" />


---

## 🧪 4. Descrição de Atividades Realizadas

### 🔩 Montagem e Testes de Hardware

- Montagem do **ESP32** com sensores e atuadores
- Testes de funcionamento do **DHT22**, **HC-SR04** e **OLED**
- Integração da **ponte H L298N** e calibração dos motores
- Ligação do **buzzer** e validação do alerta sonoro

![WhatsApp Image 2025-12-15 at 16 17 57 (1)](https://github.com/user-attachments/assets/275ab5b9-78b7-4527-811c-bf27f0f440db)
![WhatsApp Image 2025-12-15 at 16 17 57 (2)](https://github.com/user-attachments/assets/a57d78c1-6050-47af-92a3-b3878482f588)
![WhatsApp Image 2025-12-15 at 16 17 57](https://github.com/user-attachments/assets/36d1fab6-2182-48ea-b1a5-3190527f3a51)
![WhatsApp Image 2025-12-15 at 16 17 58](https://github.com/user-attachments/assets/37bb7fb4-ca44-4854-b470-360029b65844)
![WhatsApp Image 2025-12-15 at 16 17 59](https://github.com/user-attachments/assets/b176666b-fe2d-440c-9b20-984220fe4ef1)
---

## Plataforma Modular

### O foco central é a flexibilidade e a escalabilidade do sistema.

- Expansibilidade de Hardware: O sistema permite a integração de novos sensores de forma simples, facilitando a coleta de diferentes tipos de dados conforme a necessidade.
- Arquitetura de Software: O código do servidor, desenvolvido em Flask (um framework Python), é estruturado de forma modular. Isso torna a manutenção e a inclusão de novas funcionalidades muito mais eficientes.
- Escalabilidade: O sistema possui a capacidade de ser replicado, o que sugere que pode ser expandido para diferentes unidades ou instâncias sem a necessidade de criar um novo código do zero.
- Versatilidade de Aplicação: Devido à sua natureza modular, a plataforma pode ser facilmente adaptada para monitorar diversos tipos de ambientes (industriais, residenciais, agrícolas)

---

### 💻 Desenvolvimento de Firmware

- Programação da **recolha e envio de dados via Wi-Fi**
- Implementação do **modo automático inteligente**
- Lógica de **controlo remoto e atualização OLED**
- Gestão de **reconexão Wi-Fi automática**

![WhatsApp Image 2025-12-15 at 15 31 32](https://github.com/user-attachments/assets/6607a7fe-3c4a-4ccf-9a9c-c777d5939a41)

---

### 🌐 Servidor e Dashboard

- Desenvolvimento da **API REST** em Flask
- Base de dados **SQLite** funcional
- Dashboard interativo com **gráficos e botões de controlo**
- Sistema de **alertas Telegram** funcional

  
<img width="654" height="558" alt="image" src="https://github.com/user-attachments/assets/7d40e7f5-adb3-4c75-a4b3-008a76110781" />
<img width="1900" height="922" alt="image" src="https://github.com/user-attachments/assets/69f4a27b-3e56-4a6e-b81e-3c12115047df" />
<img width="1891" height="943" alt="image" src="https://github.com/user-attachments/assets/ae34ed8a-6647-4a93-9f3c-371203938356" />


---

### ✅ Testes e Resultados

- Comunicação **ESP32 ↔ Flask** validada
- Dados armazenados e exibidos em **tempo real**
- Alertas **Telegram** e **comandos de movimento** testados com sucesso

---

## 🚀 Próximas Etapas

- Integração do **módulo de IA** (previsões ambientais) *(em desenvolvimento)*
- Otimização do **modo automático** e do **servidor**
- Melhorias na **interface web** e documentação final
- Integração de **mais sensores**
- Fase de testes

---


📄 **Autores:**  
Ruben Ferreira

Sofia Leandro

Catarina Cardoso

📅 **Data:** Dezembro 2025  

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Milestone 3 – Integração de IA, Interação Natural e Sistema Completo

## 🧠 1. Objetivo do Milestone 3

Nesta terceira fase foi concluída a integração do sistema **RoboESP32 – EcoTrack** com módulos de **Inteligência Artificial** e **interação natural**, elevando o projeto de um sistema IoT reativo para uma plataforma inteligente, preditiva e interativa.

Foram integrados:

- **IA preditiva**, através de Regressão Linear, para estimar valores futuros de temperatura e humidade;
- **Interação conversacional**, recorrendo a um **LLM local (Ollama)**, ativado por um evento sonoro (“clap”);
- **Resposta por voz (TTS)**, onde o servidor gera áudio e o ESP32 reproduz o som através de uma coluna via **I2S**.

Com estas funcionalidades, o sistema passa a ser capaz de:

- recolher dados ambientais;
- armazenar e visualizar informação num dashboard web;
- gerar previsões ambientais;
- emitir alertas automáticos;
- interagir com o utilizador por som e voz com suporte de IA.

---

## ⚙️ 2. Funcionalidades Implementadas (Milestone 3)

### ✅ Monitorização e controlo (mantidas e consolidadas)

- 🌡️ **DHT22**: leitura de temperatura e humidade, com otimização por cache;
- 📏 **2× HC-SR04**: deteção de obstáculos (frente e trás);
- 🚗 **L298N**: controlo manual e modo automático com lógica de evasão;
- 💡 **2 OLED**: visualização de dados do sistema e estado da bateria em tempo real;
- 🔊 **Buzzer**: alerta sonoro em função da proximidade de obstáculos;
- 📶 **Wi-Fi + REST**: comunicação bidirecional ESP32 ↔ servidor Flask;
- 💬 **Telegram**: envio de alertas automáticos com controlo de spam.

### 🧠 Novas funcionalidades deste milestone (IA + LLM)

- 📈 **Previsões ambientais** com Regressão Linear (temperatura e humidade);
- 👏 **Deteção de clap** no ESP32 através do microfone **INMP441 (I2S)**;
- 🤖 **LLM Ollama** para gerar respostas textuais com base no contexto do sistema;
- 🗣️ **TTS (voz)**: o servidor gera ficheiros WAV e o ESP32 reproduz o áudio via **MAX98357 (I2S)**.

---

### 🔗 Continuidade em relação ao Milestone 2

Este milestone baseia-se diretamente no trabalho desenvolvido no **Milestone 2**, onde foi implementado e validado um protótipo funcional do sistema RoboESP32 – EcoTrack.  
Nesse milestone foram consolidadas a arquitetura cliente–servidor, a comunicação REST entre o ESP32 e o servidor Flask, o controlo de movimento, a leitura de sensores, o dashboard web e a base de dados.

No **Milestone 3**, esse protótipo funcional foi estendido e integrado com módulos de **Inteligência Artificial**, **interação natural** e **síntese de voz**, resultando numa solução completa, estável e pronta para demonstração final.

---

## 🧩 3. Arquitetura Implementada

Esta secção apresenta a arquitetura final do sistema **RoboESP32 – EcoTrack**,
descrevendo a organização dos seus principais módulos, os fluxos de comunicação
e a integração entre **hardware**, **software** e **Inteligência Artificial**.
A arquitetura foi concebida segundo um modelo **cliente–servidor**, permitindo
uma separação clara de responsabilidades, escalabilidade e facilidade de manutenção.

---

### 📐 3.0 Diagrama Geral da Arquitetura

O diagrama geral da arquitetura apresenta uma visão de alto nível do sistema
RoboESP32 – EcoTrack, evidenciando a separação entre o **módulo físico**
(Robot IoT baseado em ESP32) e o **módulo lógico** (Servidor Flask com integração
de Inteligência Artificial).

O módulo físico é responsável pela recolha de dados ambientais, controlo de
movimento, interação local e deteção de eventos sonoros, enquanto o módulo
lógico centraliza o processamento, armazenamento, visualização dos dados e
execução dos módulos de IA, incluindo previsões ambientais, interação com LLM
e síntese de voz.

A comunicação entre os dois módulos é realizada através de uma API REST sobre
Wi-Fi, permitindo o envio contínuo de leituras, a receção de comandos remotos
e a troca de eventos associados à interação natural (clap) e reprodução de
áudio (TTS).

Esta arquitetura cliente–servidor garante modularidade, escalabilidade e
facilidade de extensão do sistema, permitindo a integração de novos sensores,
modelos de Inteligência Artificial e funcionalidades futuras.


+----------------------------------------------------+
|                Servidor Flask + IA                 |
|----------------------------------------------------|
|  • API REST (Flask)                                |
|  • Base de Dados (SQLite)                          |
|      - leituras                                    |
|      - previsoes                                   |
|      - telegram_chat_ids                           |
|  • Módulo IA (Regressão Linear)                    |
|  • LLM (Ollama)                                    |
|  • TTS (Geração de WAV)                            |
|  • Sistema de Alertas (Telegram)                   |
|  • Dashboard Web (HTML + Chart.js)                 |
+-------------------------^--------------------------+
                          |
                    REST / HTTP (Wi-Fi)
                          |
+-------------------------v--------------------------+
|                 Robot ESP32 (IoT)                  |
|----------------------------------------------------|
|  • ESP32 DevKit                                    |
|  • Sensores:                                      |
|      - DHT22 (Temp/Hum)                            |
|      - HC-SR04 (Obstáculos)                        |
|      - INMP441 (Som / Clap)                        |
|  • Atuadores:                                     |
|      - Motores DC (L298N)                          |
|      - Buzzer / LED RGB                            |
|      - OLEDs                                      |
|  • Lógica Local:                                  |
|      - Modo manual                                |
|      - Modo automático                            |
|      - Deteção de clap                             |
|  • Reprodução de áudio (MAX98357 – I2S)            |
+----------------------------------------------------+



---

### 🔌 3.1 Módulo Físico – ESP32 (Robot IoT)

O módulo físico corresponde ao robô móvel baseado em **ESP32**, responsável
pela recolha de dados ambientais, interação local, controlo de movimento e
comunicação com o servidor.

#### Responsabilidades principais

**Leitura dos sensores**
- Sensor **DHT22** para medição de temperatura e humidade;
- Dois sensores ultrassónicos **HC-SR04** para deteção de obstáculos à frente e atrás;
- Microfone digital **INMP441** para análise do nível de som ambiente e deteção de eventos de “clap”.

**Controlo de movimento**
- Motores DC controlados através da ponte H **L298N**;
- Modo manual, acionado remotamente a partir do dashboard;
- Modo automático com lógica local de segurança e evasão de obstáculos.

**Output local**
- **OLED principal** para apresentação de dados ambientais, distâncias, modo de funcionamento e estado do som;
- **OLED secundário** dedicado à visualização da tensão e percentagem da bateria;
- **Buzzer** para alertas sonoros de proximidade;
- **LED RGB** para feedback visual do estado do sistema e do nível de som.

**Comunicação**
- Envio de leituras e eventos para o servidor através de pedidos REST;
- Receção de comandos de controlo remoto;
- Comunicação bidirecional para reprodução de áudio (TTS).

#### Endpoints utilizados pelo ESP32

| Endpoint | Método | Função |
|---------|--------|--------|
| `/dados` | POST | Envio de leituras ambientais e eventos (incluindo clap) |
| `/api/leituras` | GET | Consulta de dados para o dashboard |
| `/api/controlo_robo` | GET / POST | Receção e envio de comandos de movimento |
| `/api/speech/next` | GET | Verificação de áudio disponível para reprodução |
| `/api/speech/ack` | POST | Confirmação da reprodução do áudio |

---

### 🖥️ 3.2 Módulo Lógico – Servidor Flask + Dashboard + IA

O módulo lógico é responsável pelo processamento, armazenamento e visualização
dos dados recolhidos pelo robô, bem como pela execução dos módulos de Inteligência
Artificial e interação natural.

#### Responsabilidades principais

- Implementação de uma **API REST** em Flask para comunicação com o ESP32;
- Gestão de uma base de dados **SQLite**, composta pelas tabelas:
  - `leituras` – armazenamento de dados ambientais;
  - `previsoes` – armazenamento de previsões geradas pelo modelo preditivo;
  - `telegram_chat_ids` – gestão de utilizadores para alertas Telegram;
- **Dashboard Web** desenvolvido em HTML, Bootstrap e Chart.js, permitindo:
  - visualização de dados em tempo real;
  - consulta de histórico por datas;
  - apresentação gráfica das previsões ambientais;
- **Sistema de alertas automáticos** via Telegram;
- **Módulo de IA preditiva**, baseado em Regressão Linear, para previsão multi-step
  de temperatura e humidade;
- **Integração com LLM (Ollama)** para geração de respostas textuais após eventos de clap;
- **Sistema de síntese de voz (TTS)**, responsável pela geração de ficheiros WAV
  e disponibilização do áudio ao ESP32 através de endpoints dedicados.

---

### 🔌 3.3 Diagrama de Circuitos (versão final)

<img width="672" height="468" alt="Diagrama geral da arquitetura do sistema" src="https://github.com/user-attachments/assets/e3733fd1-c178-4567-ac83-e5d4af05dd5a" />

O diagrama de circuitos representa a implementação física final do sistema
RoboESP32 – EcoTrack, evidenciando as ligações elétricas entre o ESP32 e
todos os sensores, atuadores e módulos utilizados.

Estão incluídas as ligações dos sensores DHT22 e HC-SR04, dos módulos de áudio
INMP441 e MAX98357 via interface I2S, dos displays OLED via I2C e I2C secundário,
bem como do buzzer, LED RGB, ponte H L298N, motores DC e sistema de alimentação
com regulador de tensão XL6019.

Este diagrama corresponde à configuração final utilizada no Milestone 3 e
serviu de base para a implementação, testes e validação do sistema completo.

---

## 🔄 4. Fluxos de Comunicação

### 4.1 Fluxo principal – Sensores e dashboard
1. O ESP32 lê sensores e estado do sistema;
2. Envia dados para o servidor (`POST /dados`);
3. O servidor guarda na base de dados e atualiza variáveis internas;
4. O dashboard consulta (`GET /api/leituras`);
5. Os dados são apresentados em tempo real e em gráficos.

### 4.2 Fluxo de controlo remoto
1. O utilizador interage com o dashboard;
2. O dashboard envia comando (`POST /api/controlo_robo`);
3. O ESP32 faz polling (`GET /api/controlo_robo`);
4. O robô executa o comando (manual ou automático).

### 4.3 Fluxo de IA preditiva (Regressão Linear)
1. O servidor lê dados históricos da base de dados;
2. Calcula médias diárias;
3. Treina o modelo com lags (d-1 e d-2);
4. Gera previsões multi-step;
5. Guarda resultados na tabela `previsoes`;
6. Apresenta resultados na página **Previsões**.

### 4.4 Fluxo LLM + Voz (Interação natural)
1. O microfone INMP441 deteta um pico → clap;
2. O ESP32 envia evento no `POST /dados`;
3. O servidor valida se o evento é novo;
4. O Flask chama o **Ollama** para gerar uma frase curta;
5. O texto entra na fila TTS e é convertido em WAV;
6. O ESP32 faz polling (`/api/speech/next`);
7. O áudio é descarregado e reproduzido;
8. O ESP32 envia confirmação (`/api/speech/ack`).

---

## 📈 5. Módulo de IA – Regressão Linear

### 5.1 Preparação dos dados
- Leituras armazenadas em tempo real na tabela `leituras`;
- Cálculo de médias diárias de temperatura e humidade.

### 5.2 Features utilizadas (lags)
- `temp_d-1`, `temp_d-2`
- `hum_d-1`, `hum_d-2`

### 5.3 Treino e avaliação
- Modelo: **LinearRegression** (scikit-learn);
- Divisão temporal 80/20;
- Métrica: **RMSE** (erro médio quadrático).

### 5.4 Previsão multi-step
- Previsões realizadas em cadeia;
- O valor previsto para amanhã é usado para prever dias seguintes;
- Resultados armazenados e visualizados no dashboard.

---

## 🤖 6. Módulo LLM (Ollama)

**Objetivo**  
Permitir respostas naturais e curtas quando o utilizador interage com um clap.

**Contexto enviado ao LLM**
- temperatura atual;
- humidade atual;
- estado do som (SIL/MED/ALT);
- bateria (quando disponível);
- histórico curto para evitar repetição.

**Resultado**
- resposta curta (1–2 frases);
- sem listas nem emojis;
- fallback seguro em caso de falha do modelo.

---

## 🗣️ 7. Síntese de Voz (TTS) e Reprodução no ESP32

- Geração de ficheiros WAV (PCM 16-bit) no servidor;
- Reprodução no ESP32 via **I2S (MAX98357)**;
- Sistema de fila:
  - enqueue → gerar → disponibilizar → ack;
- Evita repetição de áudio e permite escalabilidade.

---

## 🛠️ 8. Atividades Realizadas

- Integração do módulo de IA preditiva no servidor;
- Implementação da interação natural (clap, LLM e TTS);
- Desenvolvimento de fila de áudio com confirmação (ACK);
- Integração das previsões no dashboard;
- Testes funcionais e de integração do sistema completo;
- Ajustes finais de desempenho, estabilidade e fiabilidade.

---

## 🧪 9. Testes Realizados e Resultados

### Testes funcionais
- Envio periódico de leituras pelo ESP32;
- Atualização do dashboard em tempo real;
- Execução correta de comandos remotos;
- Envio de alertas Telegram;
- Geração e visualização de previsões;
- Interação por clap com resposta por voz.

### Resultados
- Integração completa **IoT + IA + Web + Voz**;
- Sistema robusto com:
  - deduplicação de eventos (`clap_seq`);
  - fila de áudio com confirmação (ACK).

---
### 🎥 Demonstração do Sistema

Foi produzido um vídeo técnico com a demonstração completa do sistema RoboESP32 – EcoTrack,
onde são apresentadas as funcionalidades finais do robô, a comunicação com o dashboard,
a geração de previsões, bem como a interação natural por som e voz.

(colocar video)


---

## ⚠️ 10. Limitações e Funcionalidades Não Implementadas

Apesar do sistema atingir os objetivos principais, algumas funcionalidades inicialmente planeadas não foram totalmente implementadas devido a limitações de tempo, recursos e complexidade técnica, nomeadamente:

- utilização de modelos preditivos mais avançados (ARIMA, LSTM), que requerem maior volume de dados históricos e maior capacidade computacional;
- interação mais rica com o LLM, incluindo suporte completo à língua portuguesa e múltiplas intenções de interação;
- otimização adicional do modo automático de navegação, com algoritmos mais avançados de planeamento de trajetória;
- implementação de mecanismos de autenticação e segurança mais robustos na API REST;
- **integração de reconhecimento facial**, cujo desenvolvimento foi iniciado, mas não concluído dentro do tempo disponível, sendo considerado um objetivo relevante para futuras extensões do sistema, nomeadamente para identificação de utilizadores e personalização de interações.

Estas limitações não comprometem o funcionamento global do sistema, mas representam oportunidades claras de melhoria e evolução futura.


---

## 🚀 11. Próximas Etapas

Como trabalho futuro, o sistema RoboESP32 – EcoTrack pode ser evoluído em várias direções, reforçando o seu carácter inteligente, autónomo e escalável:

- Integração de modelos preditivos mais avançados (ex.: ARIMA, LSTM), à medida que exista maior volume de dados históricos;
- Expansão do conjunto de sensores ambientais, permitindo uma monitorização mais completa do ambiente;
- Implementação de mecanismos de segurança e autenticação na API REST, adequados a ambientes reais e multiutilizador;
- Otimização do modo automático de navegação, recorrendo a algoritmos mais avançados de planeamento de trajetória e evasão de obstáculos;
- Evolução da interação com o LLM, incluindo suporte à língua portuguesa, múltiplas intenções e respostas mais contextuais;
- Integração futura de reconhecimento facial, permitindo identificação de utilizadores e personalização das interações do robô.

Estas próximas etapas permitem que o projeto evolua de um protótipo académico para uma solução mais robusta e próxima de um sistema real.


---

## 🧰 12. Componentes Utilizados

| Componente           | Quantidade | Função |
|--------------------|-----------|--------|
| ESP32 DevKit | 1 | Microcontrolador principal |
| DHT22 | 1 | Sensor de temperatura e humidade |
| HC-SR04 | 2 | Deteção de obstáculos |
| INMP441 | 1 | Microfone digital |
| Buzzer | 1 | Sinal sonoro |
| XL6019 | 1 | Regulador de tensão |
| MCP23017 | 1 | Expansor de I/O |
| MAX98357 | 1 | Amplificador + speaker |
| OLED 0.96” | 1 | Display principal |
| OLED 0.91” | 1 | Display de bateria |
| LED RGB (KY-016) | 1 | Feedback visual |
| L298N | 1 | Ponte H |
| Motores DC + rodas | 4 | Locomoção |
| Pilhas | 1 | Alimentação |
| Breadboard e jumpers | — | Prototipagem |
| Chassis robótico 4WD | 1 | Estrutura física |

## 💻 12A. Software e Tecnologias Utilizadas
- ESP32 (Arduino IDE)
- Python
- Flask (API REST)
- SQLite
- Chart.js + Bootstrap (dashboard)
- Telegram Bot API
- scikit-learn (Regressão Linear)
- Ollama (LLM local)
- TTS (geração WAV PCM 16-bit)


---

## 👥 13. Distribuição de Tarefas

- **Ruben Ferreira**: firmware ESP32, sensores, atuadores, comunicação Wi-Fi, clap e áudio;
- **Sofia Leandro**: servidor Flask, API REST, base de dados, dashboard e Telegram;
- **Catarina Cardoso**: módulo de IA, regressão linear, previsões e apoio à documentação.

---

## 🏁 14. Conclusão

O projeto **RoboESP32 – EcoTrack** demonstra a integração bem-sucedida de conceitos de **Sistemas Distribuídos**, **Computação Física**, **IoT** e **Inteligência Artificial** num sistema real e funcional.  
O Milestone 3 consolida todo o trabalho desenvolvido, resultando numa plataforma inteligente, interativa e extensível.

---

## 📄 Autores

- Ruben Ferreira  
- Sofia Leandro  
- Catarina Cardoso  

📅 **Data:** 02/2026
