# 🧩 Milestone 2 – Desenvolvimento e Prototipagem

## 🧠 1. Descrição da Funcionalidade do Protótipo

Durante esta segunda fase foi desenvolvido e testado o **protótipo funcional RoboSP32**, um robô móvel baseado em **ESP32**, capaz de monitorizar o ambiente e interagir com o utilizador.

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

### 🧩 Módulo Físico (ESP32 – Robô IoT)

- Leitura dos sensores (**DHT22**, **HC-SR04**)
- Controlo dos motores (**L298N**)
- Exibição dos dados (**OLED**)
- Envio de dados (**POST /dados**) para o servidor Flask
- Receção de comandos (**GET /api/controlo_robo**)
- Modo automático com lógica de navegação e segurança

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


📊 *Inserir aqui um print ou esquema do dashboard Flask em funcionamento*

---

### 🧱 Arquitetura Geral

┌──────────────────────────┐
│ Dashboard Web            │
│ (HTML, JS, Chart.js)     │
└─────────────▲────────────┘
              │ HTTP (REST)
┌─────────────┴────────────┐
│ Servidor Flask           │
│ Base de Dados SQLite     │
│ Alertas Telegram / IA    │
└─────────────▲────────────┘
              │ Wi-Fi (JSON)
┌─────────────┴────────────┐
│ ESP32 (Robô)             │
│ DHT22 | HC-SR04 | OLED   │
│ L298N | Buzzer | Motores │
└──────────────────────────┘


📐 *Inserir aqui um diagrama de arquitetura feito em Draw.io ou Lucidchart*

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
| Alimentação          | VIN / GND                               |

### 🔧 Esquema Simplificado

ESP32
├── DHT22 → GPIO 15
├── HC-SR04 (frente) → TRIG 4, ECHO 18
├── HC-SR04 (trás) → TRIG 5, ECHO 19
├── L298N → IN1 13, IN2 12, IN3 14, IN4 27
├── OLED → SDA 21, SCL 22
└── Buzzer → GPIO 26


🧰 O diagrama elétrico foi criado no **Wokwi**, com todas as ligações simuladas.  
📸 *Inserir aqui print do circuito no Wokwi ou foto real do circuito na breadboard*

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

📟 *Inserir print do código ou captura do terminal com leituras a chegar*

---

### 🌐 Servidor e Dashboard

- Desenvolvimento da **API REST** em Flask
- Base de dados **SQLite** funcional
- Dashboard interativo com **gráficos e botões de controlo**
- Sistema de **alertas Telegram** funcional

📊 *Inserir print do dashboard web e exemplo de alerta Telegram*

---

### ✅ Testes e Resultados

- Comunicação **ESP32 ↔ Flask** validada
- Dados armazenados e exibidos em **tempo real**
- Alertas **Telegram** e **comandos de movimento** testados com sucesso

---

## 🚀 Próximas Etapas

- Integração do **módulo de IA** (previsões ambientais)
- Otimização do **modo automático** e do **servidor**
- Melhorias na **interface web** e documentação final

---

### 📄 Autores

- **Ruben Ferreira**  
- **Sofia Leandro**  
- **Catarina Cardoso**

📅 **Data:** Dezembro 2025  
🏫 **Instituição:** IADE – Universidade Europeia


