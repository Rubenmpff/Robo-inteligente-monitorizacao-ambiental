# 🤖 Robô Inteligente de Monitorização Ambiental

**Universidade:** IADE – Universidade Europeia  
**Faculdade:** Faculdade de Design, Tecnologia e Comunicação  

## 🏫 Identificação do Projeto
**Curso:** Engenharia Informática  
**Unidade Curricular:** PBL – Sistemas Distribuídos, IoT, IA e Engenharia de Software  
**Ano letivo:** 2025/2026  
**Grupo:** 1  
**Título do Projeto:** Robô Inteligente de Monitorização Ambiental  
**Palavras-chave:** IoT, ESP32, Inteligência Artificial, Robótica, Sensores, Voz, Visão  
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
| HC-SR04 | 1 | detectar obstáculos e distância |
| INMP441 | 1 | Microfone digital (nível de som) |
| OLED 0.96” | 1 | Mostrar expressões e dados |
| 1 LED RGB (KY-016) | 1 | Feedback visual (cor por nível de som/estado) |
| L298N | 1 | Ponte H para controlo dos motores |
| Motores DC + rodas | 4 | Locomoção do robô |
| Pilhas | 1 | Alimentação |
| Breadboard e jumpers | — | Ligações e prototipagem |
| Chassis robótico 4WD | 1 | Estrutura física do robô |


---

### 💻 Software

| Software / Tecnologia | Função |
|------------------------|--------|
| Arduino IDE  | Programação do ESP32 |
| Python | Processamento de dados e IA |
| Flask | Servidor local e API REST |
| SQLite / MySQL | Armazenamento de dados |
| GitHub | Controlo de versões e documentação |
| Draw.io / Fritzing | Criação de diagramas |
| Wokwi / easyeda | Simulação de circuitos e sensores |

---


## ⚙️ Desenho da Infraestrutura Computacional

O sistema é composto por dois módulos principais:  
- **Módulo físico (robô inteligente)** — responsável pela recolha de dados, movimento e interação.  
- **Módulo lógico (servidor local)** — responsável por processar, armazenar e visualizar as informações recolhidas pelo robô.

O robô utiliza o **ESP32** como controlador central, comunicando com sensores, atuadores e periféricos através de ligações digitais e analógicas.  
Os dados recolhidos são processados localmente e, quando disponível uma ligação Wi-Fi, são enviados para o **servidor local**, onde são armazenados numa **base de dados SQLite/MYSQL** e apresentados numa **interface web** desenvolvida em **Python**.

---

### 🧭 Arquitetura geral do sistema

    +-------------------------------------------+
    |               Servidor Local              |
    |-------------------------------------------|
    |  • Python                                 |
    |  • Base de Dados (SQLite / MySQL)         |
    |  • Interface Web de Monitorização         |
    +--------------------^----------------------+
                         |
                  Wi-Fi (Local Network)
                         |
    +--------------------v----------------------+
    |                Robô ESP32                 |
    |-------------------------------------------|
    |  • ESP32 DevKit                          |
    |  • Sensores: DHT22, HC-SR04              |
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
- Sensores frontais e laterais (DHT22, HC-SR04, INMP441);
- Ecrã OLED representando o “rosto” do robô;
- LEDs WS2812B para feedback visual e reação a som;
- Microfone integrado;
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
1. Ligar o robô e aguardar a inicialização do sistema.  
2. O robô ativa automaticamente os sensores DHT22, INMP441.  
3. Os valores de temperatura, humidade e nível de som são apresentados no ecrã OLED.
4. Os dados são enviados para o servidor local e registados na base de dados.

### 🎧 Guião 2 – Reação a Som
1. Colocar o robô num ambiente com diferentes níveis de ruído.  
2. O microfone (INMP441) deteta o volume ambiente.  
3. O LED RGB muda de cor conforme o nível de som (verde → azul → vermelho).
4. Quando o som diminui, o LED regressa a verde.

---

## 🧱 Diagrama de Circuitos
*(Opcional, faremos quando começarmos o projeto )*

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
| **Internet of Things (IoT)** | Integração de múltiplos sensores e atuadores conectados à rede, recolha e envio de dados ambientais. |
| **Inteligência Artificial (IA)** | Processamento de dados ambientais .|
| **Engenharia de Software** | Estruturação modular do código, definição de requisitos, testes, validação e documentação no GitHub. |

---

## 💬 Conclusão

O **Robô Inteligente de Monitorização Ambiental** é uma proposta inovadora que combina **IoT, IA e Engenharia de Software** num sistema físico e interativo.  
O projeto permitirá recolher e analisar dados ambientais, promovendo a eficiência energética e a interação homem–máquina num contexto acessível, educativo e prático.  

O desenvolvimento segue uma abordagem incremental, começando por um protótipo funcional e evoluindo para uma versão inteligente com autonomia, reconhecimento e comunicação.

---

📄 **Autores:**  
Ruben	Ferreira
Sofia Leandro
Catarina Cardoso	

📅 **Data:** Novembro 2025  
