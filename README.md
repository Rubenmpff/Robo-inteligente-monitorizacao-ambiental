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

*(Metemos Imagem quando começarmos o projeto)*

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

| Fase | Atividade | Responsável | Prazo |
|------|------------|--------------|--------|
| 1️⃣ | Levantamento de requisitos e planeamento | Todos | semana 1/2 |
| 2️⃣ | Desenvolvimento do protótipo | Catarina | semana 3/4 |
| 3️⃣ | Programação do ESP32 e controlo de movimento | Ruben | semana 4/5 |
| 4️⃣ | Integração com servidor Python | Sofia | semana 5/6 |
| 5️⃣ | Plataforma Web e Base de dados | Todos  | semana 6/7 |
| 6️⃣ | Testes e validação final | Todos | semana 7 |

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
-----------------------------------------------------------------------------------------------------------------------------------------

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

📸 *Inserir aqui uma fotografia do robô montado / protótipo físico em funcionamento*

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

📸 *Inserir aqui fotos das ligações e montagem física*

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
