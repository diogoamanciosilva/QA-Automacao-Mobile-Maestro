
## 🤖 Automação Mobile Maestro (qaFood)

<img width="405" height="860" alt="Screenshot do qaFood" src="https://github.com/user-attachments/assets/15ad61e5-2117-42e6-a2d8-b7ddb1f90092" />

O projeto consiste de Suíte de testes **end-to-end (E2E)** para o aplicativo **qaFood**, uma versão do **iFood** utilizada como projeto de estudo, desenvolvida pela **Qazando** (professores Eduardo Finotti e Hebert Soares).

Todos os testes e a estrutura deste repositório foram desenvolvidos por **Diogo Amancio**, com base nos conhecimentos adquiridos no curso **Automação Mobile com Maestro**.

---

## 📑 Índice

- [🎯 Tipos de teste realizados na suíte](#-tipos-de-teste-realizados-na-suíte)
- [⚙️ Estrutura da Suíte de Testes qaFood](#️-estrutura-da-suíte-de-testes-qafood)
- [📱 Sobre o app](#-sobre-o-app)
- [🛠️ Ambiente e rotina diária](#️-ambiente-e-rotina-diária)
- [📁 Estrutura do repositório](#-estrutura-do-repositório)
- [🧭 A Jornada do usuário](#-a-jornada-do-usuário)
- [💻 Features](#-features)
- [🔍 1. Feature Login](#-1-feature-login)
- [🔍 2. Feature Lojas](#-2-feature-lojas)
- [🔍 3. Feature Cardápio](#-3-feature-cardápio)
- [🔍 4. Feature Sacola (Carrinho)](#-4-feature-sacola-carrinho)
- [🔍 5. Feature Pedido](#-5-feature-pedido)
- [🐞 Bugs Encontrados](#-bugs-encontrados)
- [📊 Análise da Suíte de Testes ](#-análise-da-suíte-e-root-cause-analysis-rca)
- [🕵🏻‍♂️ Análise de Causa Raiz](#%E2%80%8D%EF%B8%8F-root-cause-analysis-rca)
- [🧪 Metodologia de teste](#-metodologia-de-teste)
- [🚧 Limitações e escopo](#-limitações-e-escopo)
- [🚀 Próximos passos (CI/CD)](#-próximos-passos-cicd)
- [💡 Aprendizados técnicos](#-aprendizados-técnicos)
- [🏷️ Tecnologias utilizadas](#️-tecnologias-utilizadas)
- [✅ Contato](#-contato)
  
---

## 📱 Sobre o app

O qaFood simula um aplicativo de delivery completo, cobrindo a jornada real de um usuário:

```text
Login → Lojas → Cardápio → Sacola → Pedido → Acompanhamento
```

**Abaixo segue o vídeo demonstrativo do cenário de teste end-to-end (E2E) descrito acima:**

https://github.com/user-attachments/assets/794fba4c-bc3d-45a3-a7b9-d5e267cb79f7

---

## 🤖 Maestro

O framework Maestro utiliza recursos e conceitos de outros frameworks como **Appium, Espresso, UIAutomator e XCTest**, aproveitando suas bases para a execução de testes automatizados.

### Pré-requisitos para utilização no Windows

* **Java JDK 11**
* **Android Studio**
* **Linux (WSL)**
  
---

## 🏷️ Tecnologias utilizadas

![Maestro](https://img.shields.io/badge/Maestro-Mobile%20Testing-1E88E5?style=for-the-badge)
![YAML](https://img.shields.io/badge/YAML-Test%20Scripts-CB171E?style=for-the-badge&logo=yaml&logoColor=white)
![Android](https://img.shields.io/badge/Android-Emulator-3DDC84?style=for-the-badge&logo=android&logoColor=white)
![WSL](https://img.shields.io/badge/WSL-Linux%20on%20Windows-4D4D4D?style=for-the-badge&logo=linux&logoColor=white)
![Git](https://img.shields.io/badge/Git-Version%20Control-F05032?style=for-the-badge&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-Repository-181717?style=for-the-badge&logo=github&logoColor=white)

---

## ⚙️ Estrutura da Suíte de Testes qaFood

A suíte de testes do qaFood é **organizada em 5 Features**, seguindo a jornada do usuário no aplicativo, do login à finalização e acompanhamento do pedido.

| Feature                   |  Testes |
| ------------------------- | ------: |
| Feature_Login             |      36 |
| Feature_Lojas             |      35 |
| Feature_Cardápio          |      17 |
| Feature_Sacola (Carrinho) |      18 |
| Feature_Pedido            |      12 |
| **Total**                 | **118** |

---

## 🎯 Tipos de teste realizados na suíte

A suíte de testes do qaFood é composta por todos os tipos de testes descritos abaixo:

| Tipo de Teste | O que valida | Exemplos na suíte |
| --- | --- | --- |
| **Funcionais** | Regras de negócio: autenticação, busca, cálculo de subtotal/total, adição/remoção de itens, confirmação de pedido | Categoria predominante — presente em todas as 5 Features |
| **E2E (ponta a ponta)** | Jornada completa atravessando múltiplas Features em sequência | "Após realizar o pedido, clicar em voltar e retornar a página de Lojas"; "Validar a Rotação de Tela após a Conclusão do Pedido" |
| **Integração** | Persistência e comunicação de estado entre telas/módulos | "Carrinho não duplica nem perde produto após múltiplas idas e vindas"; "Sacola não é mantida após fechar e reabrir o app" |
| **Negativos / Borda (edge cases)** | Entradas inválidas e valores-limite | Campos vazios, e-mail malformado, senha incorreta, espaços em branco, caracteres especiais, capitalização, cupom inválido |
| **Não Funcionais** | Comportamento sob condições do sistema operacional, não regra de negócio | Rotação de tela, app em segundo plano (Home + relaunch), tecla Enter/Done |
| **Concorrência** | Ações quase simultâneas / condição de corrida | "Duplo toque simultâneo no botão Entrar"; "Duplo toque rápido no botão de adicionar" |
| **Regressão** | Não é uma categoria de design — é a função da suíte quando reexecutada após mudanças no app | A suíte completa, ao rodar antes de cada release |
| **Aceitação** | Critérios básicos de aceite cumpridos informalmente (sem UAT/BDD formal) | Cenários de caminho feliz: login correto, pedido concluído com sucesso, busca encontrando o restaurante certo |

---

## 🚀 Como executar este projeto 

Um resumo rápido para quem está clonando este repositório pela primeira vez. Para ver o passo a passo completo, consulte a seção "🛠️ Ambiente e rotina diária" mais abaixo.

### Pré-requisitos

- **Java JDK 11**
- **Android Studio** (com um AVD configurado, este projeto usa `Pixel_4`)
- **WSL** (Linux) instalado no Windows
- **Maestro CLI** instalado dentro do WSL ([guia oficial de instalação](https://docs.maestro.dev/getting-started/installing-maestro))
- App **qaFood** já instalado no emulador (`appId: com.qazandoqafood`) — se ainda não estiver, veja a seção *"Instalação do aplicativo"* abaixo

### Passos

1. **Abra o emulador** (PowerShell):
```powershell
   cd $env:LOCALAPPDATA\Android\Sdk\emulator
   .\emulator.exe -avd Pixel_4 -gpu swiftshader_indirect
```
   Aguarde carregar completamente.

2. **Conecte o WSL ao emulador** (terminal WSL):
```bash
   adb kill-server
   adb connect <IP>:25555
   adb devices
```
   > O `<IP>` muda a cada reinício — descubra o valor atual com `ip route show default | awk '{print $3}'`

3. **Rode um teste**:
```bash
   maestro --host <IP> test "1 - Feature_Login/Login com credenciais corretas.yaml"
```

4. **(Opcional) Abra o Maestro Studio** para navegar visualmente pelos testes:
```bash
   cd ~/Downloads
   ./MaestroStudio.AppImage
```

🏆 **Se o passo 3 rodar sem erro de "Flow path does not exist" e o login acontecer no emulador, seu ambiente está pronto.**

---

## 🛠️ Ambiente e rotina diária

O ambiente de testes combina:

- **Emulador Android no Windows**
- **WSL (Linux)**
- **ADB**
- **Maestro CLI**
- **Maestro Studio**

### 1. Abrir o emulador — PowerShell

```powershell
cd $env:LOCALAPPDATA\Android\Sdk\emulator
.\emulator.exe -avd Pixel_4 -gpu swiftshader_indirect
```

Aguarde o emulador carregar completamente antes de seguir.

> ⚠️ **Importante:** não use o botão ▶ do Android Studio para iniciar o emulador. Utilize o comando acima.

### 2. Instalação do aplicativo — `qafoodcompletao.apk`

O arquivo `.apk` é apenas o **instalador do aplicativo**. Ele **não faz parte da conexão entre Windows, WSL, ADB e Maestro**.

A comunicação dos testes depende apenas de:

**Emulador rodando → ADB conectado via rede → Maestro apontando para o host correto**

O APK só precisa ser instalado nos seguintes casos:

1. Emulador novo, sem o aplicativo instalado;
2. Reset/Wipe do emulador, que remove os aplicativos instalados;
3. Necessidade de reinstalar o aplicativo;
4. Necessidade de trocar a versão do aplicativo.

#### Instalar o APK

Confirme que o emulador está rodando e conectado:

```bash
adb devices
```

Instale o APK no device correto:

```bash
adb -s <IP>:25555 install caminho/para/qafoodcompletao.apk
```

Confirme que a instalação foi realizada:

```bash
adb shell pm list packages | grep qazandoqafood
```

Resultado esperado:

```text
package:com.qazandoqafood
```

> 📌 **Importante:** depois que o aplicativo estiver instalado, o arquivo `.apk` não precisa ser utilizado novamente para executar os testes. O Maestro interage diretamente com o aplicativo por meio do `appId: com.qazandoqafood`.

### 3. Conectar o WSL ao emulador

```bash
adb kill-server
adb connect <IP>:25555
adb devices
```

> ⚠️ O IP não é fixo e pode mudar a cada reinício do Windows/WSL. Descubra o valor atual com:
>
> ```bash
> ip route show default | awk '{print $3}'
> ```
>
> Resultado esperado do `adb devices`:
>
> ```text
> <IP>:25555   device
> ```

### 4. Executar os testes com Maestro

```bash
maestro --host <IP> test <caminho-do-arquivo>.yaml
```

### 5. Abrir o Maestro Studio — opcional

```bash
cd ~/Downloads
./MaestroStudio.AppImage
```

Selecione o device `<IP>:25555` na lista.

> ⚠️ O streaming de tela ao vivo dentro do Studio não funciona neste ambiente devido a um erro de gRPC pela rede. Os testes continuam funcionando normalmente. Para acompanhamento visual, utilize a janela do emulador no Windows.

### Ordem diária

**PowerShell (emulador) → WSL/ADB (conexão) → Maestro/Maestro Studio (execução)**

---

## 📁 Estrutura do repositório

```text
Maestro/
├── 1 - Feature_Login/
├── 2 - Feature_Lojas/
├── 3 - Feature_Cardápio/
├── 4 - Feature_Sacola (Carrinho)/
└── 5 - Feature_Pedido/
```

Cada teste que depende de login reutiliza o mesmo flow base por meio de `runFlow`, evitando duplicação:

```yaml
- runFlow:
    file: "../1 - Feature_Login/A) 1. Login com credenciais corretas.yaml"
```

> 📌 O caminho do `runFlow` é sempre **relativo ao arquivo que o chama**. Testes salvos dentro de uma subpasta de Feature utilizam `../1 - Feature_Login/...`. Testes salvos diretamente na raiz `Maestro/` utilizam o caminho sem `../`.

---

## 🧭 A Jornada do usuário

A suíte tem como objetivo automatizar e validar a jornada completa do usuário dentro do qaFood:

```text
Login → Lojas → Cardápio → Sacola → Pedido → Acompanhamento
```

Os testes não validam apenas funcionalidades isoladas, mas também simulam comportamentos e situações próximas da utilização real de um aplicativo de delivery.

As informações a seguir apresentam a estrutura completa da suíte de testes do qaFood, organizada em cinco Features que representam, em sequência, a jornada do usuário no aplicativo. Cada Feature possui um conjunto de subtópicos que agrupa os cenários por funcionalidade e nível crescente de complexidade, permitindo visualizar de forma clara o que é validado em cada etapa, desde o login até a finalização e o acompanhamento do pedido.

## 💻 Features 

| Feature         | O que valida                                                                | Papel na jornada                         |
| --------------- | --------------------------------------------------------------------------- | ---------------------------------------- |
| **1.Login**    | Autenticação, campos, erros de validação e comportamento do botão de acesso | Ponto de entrada — “quero acessar o app” |
| **2.Lojas**    | Listagem, busca, navegação e permissão de localização                       | “Onde quero pedir?”                      |
| **3.Cardápio** | Produtos, carrinho, contador e navegação dentro do restaurante              | “O que vou comer?”                       |
| **4.Sacola**   | Gerenciamento do carrinho, subtotal e persistência                          | “Revisar minha compra”                   |
| **5.Pedido**   | Confirmação, pagamento, finalização e acompanhamento                        | “Confirmar, pagar e receber”             |


---

## 🔍 1. Feature Login

| Feature                   |  Testes |
| ------------------------- | ------: |
| Feature_Login             |      36 |

Valida o processo de autenticação e o comportamento dos campos e do botão de acesso, organizado em **8 subtópicos de testes**.

**Abaixo um vídeo demonstrativo de um dos cenários de testes da tela de Login:**

**A) 1. Login com credenciais corretas.yaml**

https://github.com/user-attachments/assets/e8c3bc69-581b-4647-b176-4fc54099d5a4

## 📍 Subtópicos de testes - Feature Login

**A) 1. Fluxo básico:**

<img width="503" height="267" alt="image" src="https://github.com/user-attachments/assets/852c6fb0-860e-42e2-9fee-c8c8d6541a7f" />


**B) 2. Validação de formato e conteúdo:**

<img width="451" height="266" alt="image" src="https://github.com/user-attachments/assets/e3c000d8-16fe-490c-8aad-40d301beb1e1" />


**C) 3. Validação de senha:**

<img width="470" height="145" alt="image" src="https://github.com/user-attachments/assets/62fa7c72-5181-444e-8b21-303b5311c45b" />


**D) 4. Correção e recuperação de erro:**

<img width="398" height="57" alt="image" src="https://github.com/user-attachments/assets/91be85aa-47fd-4ec0-b386-ba0c102ad6f0" />


**E) 5. Interações com teclado e sistema operacional:**

<img width="480" height="60" alt="image" src="https://github.com/user-attachments/assets/cded17ec-009b-4a02-8cda-863faf4d5123" />


**F) 6. Cliques repetidos e comportamento de interface:**

<img width="427" height="122" alt="image" src="https://github.com/user-attachments/assets/b6a28f50-c6b5-4ad2-b515-cb21eba3ce63" />


**G) 7. Concorrência e condição de corrida:**

<img width="543" height="32" alt="image" src="https://github.com/user-attachments/assets/e77560ad-d207-4c6d-baf7-e8b12e7d4993" />


**H) 8. Bloqueio por tentativas de senha:**

<img width="561" height="86" alt="image" src="https://github.com/user-attachments/assets/66dbc146-fa83-4169-9f93-fa783b9a0a9c" />

---

## 🔍 2. Feature Lojas

| Feature                   |  Testes |
| ------------------------- | ------: |
| Feature_Lojas             |      35 |

Valida a exibição, navegação e pesquisa dos restaurantes, organizada em **8 subtópicos de testes**.

**Abaixo um vídeo demonstrativo de um dos cenários de testes da tela de Lojas:**

**A) 2. Abrir cardápio ao clicar em restaurante da lista.yaml**

https://github.com/user-attachments/assets/03e83374-b7a0-45f2-ad3f-a2c33baab93c

## 📍 Subtópicos de testes - Feature Lojas

**A) 1. Acesso básico à tela de Lojas:**


<img width="480" height="91" alt="image" src="https://github.com/user-attachments/assets/ce33c954-46e8-4d1e-8aae-04aa6f559411" />


**B) 2. Navegação e visualização da lista:**


<img width="458" height="178" alt="image" src="https://github.com/user-attachments/assets/05a42e26-f733-47f6-ad06-6a59f09fd73c" />


**C) 3. Permissão e seleção de endereço:**


<img width="553" height="120" alt="image" src="https://github.com/user-attachments/assets/192bb61f-3c25-4f7d-8792-df28e1500743" />


**D) 4. Busca básica:**


<img width="608" height="147" alt="image" src="https://github.com/user-attachments/assets/2b1c3255-9eb0-4a0c-b0eb-4f8de8da7856" />


**E) 5. Busca por restaurantes específicos:**


<img width="387" height="178" alt="image" src="https://github.com/user-attachments/assets/88299dfb-1ccb-4884-ae62-dff02502f31f" />


**F) 6. Busca com espaços e capitalização:**


<img width="642" height="175" alt="image" src="https://github.com/user-attachments/assets/d356284d-0f6b-4488-9e8e-4aeab9b95ae5" />


**G) 7. Casos de borda da busca:**


<img width="560" height="82" alt="image" src="https://github.com/user-attachments/assets/d26038cd-5bfe-40e6-81da-16cd622055fe" />


**H) 8. Persistência e ciclo de vida do aplicativo:**


<img width="492" height="56" alt="image" src="https://github.com/user-attachments/assets/21071b80-9a43-493c-a53d-d9d46bedae91" />


---

## 🔍 3. Feature Cardápio

| Feature                   |  Testes |
| ------------------------- | ------: |
| Feature_Cardápio          |      17 |

Valida o acesso aos restaurantes e o comportamento dos produtos, organizada em **7 subtópicos de testes**.

**Abaixo um vídeo demonstrativo de um dos cenários de testes da tela de Cardápio:**

**E) 1. Adicionando vários itens do cardápio.yaml**


https://github.com/user-attachments/assets/14f05aaf-79a5-429b-a4a6-b2ac17bbe0eb


## 📍 Subtópicos de testes - Feature Cardápio


**A) 1. Acesso e carregamento básico do cardápio**

<img width="568" height="120" alt="image" src="https://github.com/user-attachments/assets/3365606a-167b-4bb3-be49-4a371295f129" />


**B) 2. Validação dos elementos do cardápio**



<img width="495" height="88" alt="image" src="https://github.com/user-attachments/assets/636d5765-14be-455f-b227-6c69117b01b6" />


**C) 3. Navegação dentro e fora do cardápio**


<img width="505" height="87" alt="image" src="https://github.com/user-attachments/assets/02fd2a7b-580b-41ba-89ed-74f101d7602e" />


**D) 4. Adição de um produto ao carrinho**

<img width="638" height="57" alt="image" src="https://github.com/user-attachments/assets/7ca5bfe1-acd3-40de-b049-d579615a8d26" />


**E) 5. Adição e persistência de múltiplos produtos**


<img width="692" height="92" alt="image" src="https://github.com/user-attachments/assets/b4aa6db4-a1d2-406e-a357-e57dd12b0d09" />


**F) 6. Persistência do estado em diferentes condições**

<img width="496" height="25" alt="image" src="https://github.com/user-attachments/assets/9ee55c16-81e4-4f47-9f32-f0511efa620e" />


**G) 7. Cenário de concorrência / múltiplas ações rápidas**


<img width="587" height="30" alt="image" src="https://github.com/user-attachments/assets/40c36103-245c-43fe-8f1f-a6ce549084c3" />

---

## 🔍 4. Feature Sacola (Carrinho)

| Feature                   |  Testes |
| ------------------------- | ------: |
| Feature_Sacola (Carrinho) |      18 |

Valida o funcionamento do carrinho, organizada em **7 subtópicos de testes**.

**Abaixo um vídeo demonstrativo de um dos cenários de testes da tela da Sacola (Carrinho):**

**E) 3. Limpar sacola e readicionar item usando o botão 'Adicionar itens' da própria sacola.yaml**

https://github.com/user-attachments/assets/1c144fbd-0f6f-49c2-bed9-fd91af716dd1


## 📍 Subtópicos de testes - Feature Sacola (Carrinho)

**A) 1. Operações básicas da Sacola**


<img width="662" height="122" alt="image" src="https://github.com/user-attachments/assets/b7f63ee8-240a-451e-849e-98a62885bdda" />


**B) 2. Cálculo/subtotal**

<img width="552" height="57" alt="image" src="https://github.com/user-attachments/assets/125bc761-00f3-468e-9806-cd19b8877c10" />


**C) 3. Navegação entre Sacola e Cardápio**


<img width="683" height="65" alt="image" src="https://github.com/user-attachments/assets/d5763925-dc3f-4937-875e-10139f452e72" />


**D) 4. Cancelamento**

<img width="637" height="57" alt="image" src="https://github.com/user-attachments/assets/0e3c83b5-03cf-4778-a695-6a2c53e7e449" />


**E) 5. Limpeza da Sacola**


<img width="593" height="60" alt="image" src="https://github.com/user-attachments/assets/b9e7bb64-1220-4581-a34a-6b5ca7712491" />


**F) 6. Múltiplos produtos e preservação de estado**


<img width="612" height="53" alt="image" src="https://github.com/user-attachments/assets/e6f55658-be0b-4c4c-8253-b3db5174ff87" />


**G) 7. Comportamento do aplicativo**


<img width="442" height="50" alt="image" src="https://github.com/user-attachments/assets/e691f621-42c0-42f4-baa2-1745dfe9889b" />


---

## 🔍 5. Feature Pedido

| Feature                   |  Testes |
| ------------------------- | ------: |
| Feature_Pedido            |      12 |

Valida a confirmação e a finalização do pedido, organizada em **7 subtópicos de testes**.

**Abaixo um vídeo demonstrativo de um dos cenários de testes da tela de Pedido:**

**D) 3. Fazer pedido com Cartão de crédito confirma sucesso e forma de pagamento correta.yaml**

https://github.com/user-attachments/assets/b6225846-2b9d-406c-9fb7-45348867e1e4


## 📍 Subtópicos de testes - Feature Pedido

**A) 1. Acesso e confirmação básica do pedido**

<img width="602" height="61" alt="image" src="https://github.com/user-attachments/assets/6c969ce5-f368-4a82-8cb9-035728643967" />


**B) 2. Validação de dados e condições obrigatórias**


<img width="672" height="90" alt="image" src="https://github.com/user-attachments/assets/809e6f43-189e-48e8-8f09-be35bae40b48" />


**C) 3. Cancelamento da finalização e preservação do carrinho**


<img width="513" height="31" alt="image" src="https://github.com/user-attachments/assets/3b449fe0-20ce-48be-aefc-b9db32b959d0" />


**D) 4. Realização do pedido por diferentes formas de pagamento**


<img width="603" height="93" alt="image" src="https://github.com/user-attachments/assets/3268d0f5-10b2-4eef-a169-0060ee6f284a" />


**E) 5. Validação completa do pedido realizado**

<img width="462" height="27" alt="image" src="https://github.com/user-attachments/assets/1b92901a-7bf2-40dd-a952-9ec07f1cfc63" />


**F) 6. Navegação após a conclusão do pedido**

<img width="488" height="36" alt="image" src="https://github.com/user-attachments/assets/24bb89a5-b36d-473e-b914-565f31f6ad98" />


**G) 7. Persistência do estado após alteração de orientação**


<img width="443" height="32" alt="image" src="https://github.com/user-attachments/assets/179e40f6-a924-4d58-b5d3-ad6d1ddc9d98" />

---

## 🐞 Bugs Encontrados

Durante a construção da suíte, além da validação funcional, foram identificados os seguintes comportamentos inesperados no aplicativo. Cada um foi isolado, reproduzido de forma consistente e documentado em um teste automatizado específico.

| ID | Bug | Severidade | Passos para reproduzir | Evidência (teste) |
|---|---|---|---|---|
| BUG-01 | A busca de restaurantes não localiza um restaurante existente quando o termo digitado contém **qualquer palavra inteira em maiúsculas** (ex: `"PASTELARIA da maria"` ou `"pastelaria da MARIA"`), mesmo que o restante da grafia esteja correto | Média | Na tela de Lojas, digitar no campo de busca o nome de um restaurante existente com uma das palavras totalmente em maiúsculas | `F) 3`, `F) 4`, `F) 5` — Feature Lojas |
| BUG-02 | A mesma busca falha mesmo com o termo **totalmente em minúsculas** (`"pastelaria da maria"`), sugerindo que a comparação exige a grafia exata cadastrada (`"Pastelaria da Maria"`), não apenas ausência de maiúsculas | Média | Digitar o nome do restaurante 100% em minúsculas no campo de busca | `F) 2` — Feature Lojas |
| BUG-03 | Os campos de e-mail (Login) e de busca (Lojas) não removem espaços em branco nas extremidades do texto digitado (`trim()`), causando falha de reconhecimento mesmo com o valor correto | Baixa | Digitar `" teste@teste.com "` no login ou `"  Pastelaria da Maria  "` na busca | `B) 6` — Feature Login; `F) 1` — Feature Lojas |
| BUG-04 | A tecla Enter/Done do teclado não submete o formulário de login — apenas o toque físico no botão "Entrar" funciona | Baixa | Preencher e-mail e senha e pressionar Enter no teclado, sem tocar no botão | `E) 1` — Feature Login |
| BUG-05 | A sessão de login não é mantida ao fechar e reabrir o aplicativo, mesmo sem limpeza de estado (`clearState: false`) — o usuário é sempre redirecionado para a tela de login | Baixa | Fazer login, fechar o app via `launchApp` sem limpar estado, e reabrir | `H) 1` — Feature Lojas |
| BUG-06 | O conteúdo da sacola (itens adicionados) é perdido ao fechar e reabrir o aplicativo, exigindo novo login e nova seleção de itens | Baixa | Adicionar um item ao carrinho, fechar o app e reabrir | `G) 3` — Feature Sacola |
| BUG-07 | Erro de digitação no texto exibido na tela de acompanhamento do pedido: "Previsão de **entrega**" (faltando o "n" de "entrega") | Cosmético (Interface/UI) | Finalizar um pedido e visualizar a tela "Pedido realizado" | `E) 1`, `G) 1` — Feature Pedido |
| BUG-08 | Erro de digitação no `id` do botão de adicionar item ao cardápio: `add-item-buttom` (com "m" no lugar de "n") — não impede o funcionamento, mas é uma inconsistência de nomenclatura no código do app | Cosmético (Interface/UI) | Inspecionar o elemento via `maestro hierarchy` na tela de Cardápio | Confirmado em todos os testes que interagem com o botão de adicionar item |

---

### ⚠️ Observação
```text
Nenhum dos bugs acima impede o uso do aplicativo, todos são desvios de comportamento esperado ou inconsistências de texto/nomenclatura, não falhas críticas. Os itens de severidade **Cosmético (Interface/UI)** foram incluídos por transparência e completude do processo de teste, não por representarem risco ao usuário.
```
---

## 📊 Análise da Suíte de Testes


### 📈 Distribuição de Testes por Feature

<img width="917" height="582" alt="image" src="https://github.com/user-attachments/assets/dedf281c-78bf-4c68-b17b-eb049b9a33eb" />

### 📈 Análise Testes por Feature

O gráfico apresenta 118 testes automatizados, distribuídos entre cinco Features. 

```text
A maior concentração está em Login (36 testes — 31%) e Lojas (35 testes — 30%), que juntas representam 71 testes, aproximadamente 60% da suíte.
```

Essa distribuição indica uma estratégia de cobertura mais intensa nos pontos de entrada e navegação inicial da aplicação. 

```text
A Feature Sacola possui 18 testes (15%), Cardápio 17 (14%) e Pedido 12 (10%), formando uma cobertura progressivamente menor nas etapas posteriores da jornada.
```

**Do ponto de vista de Root Cause Analysis, a quantidade de testes por Feature não deve ser interpretada diretamente como quantidade de problemas.** Ela representa principalmente onde a cobertura de testes foi concentrada. Portanto, Login e Lojas terem mais testes não significa necessariamente que sejam as áreas mais defeituosas.

A distribuição também evidencia uma característica positiva da estratégia: os testes não estão concentrados exclusivamente no fluxo feliz. Nas Features foram explorados cenários de validação, casos negativos, navegação, persistência de estado, rotação de tela, ciclo de vida e interações repetidas, aumentando a capacidade de identificar comportamentos inconsistentes.

Conclusão: a suíte apresenta uma cobertura distribuída por toda a jornada principal do aplicativo, com maior profundidade em Login e Lojas. Para uma evolução da análise, o próximo passo seria relacionar quantidade de testes × bugs encontrados × criticidade, permitindo identificar quais áreas apresentam maior concentração de problemas em relação ao esforço de teste.

### 📈 Bugs por Severidade

<img width="930" height="575" alt="image" src="https://github.com/user-attachments/assets/e5777cf5-5b3a-48c4-acee-d47a5348db60" />

### 📈 Análise Bugs Encontrados por Severidade

O gráfico apresenta 8 bugs encontrados, distribuídos em três níveis:

```text
Baixa: 4 bugs — 50%
Média: 2 bugs — 25%
Cosmético / UI: 2 bugs — 25%
```

**A maior concentração está em problemas de baixa severidade, responsáveis por metade dos achados. Outros 25% possuem severidade média e os 25% restantes estão relacionados a aspectos cosméticos ou de interface.**

Sob a perspectiva de Root Cause Analysis, o dado mais importante é que os problemas encontrados não estão concentrados exclusivamente em uma única camada. A análise realizada anteriormente identificou ocorrências relacionadas a busca e normalização de dados, persistência de estado, interação por teclado e revisão de textos/nomenclatura, mostrando diferentes possíveis origens dos problemas.

Também é importante não interpretar a ausência de categorias de maior severidade como prova de que não existem problemas críticos na aplicação. O gráfico representa os 8 bugs identificados pela suíte analisada. Portanto, ele demonstra o perfil dos achados encontrados durante esse escopo de testes, e não necessariamente o risco absoluto de toda a aplicação.

Desta forma, a distribuição dos testes indica que a suíte conseguiu identificar principalmente problemas de comportamento, validação e qualidade de interface, além de problemas que precisam ser investigados para determinar se representam limitações da aplicação ou defeitos funcionais.

### 📈 Conclusão

**Dos 8 bugs identificados, 6 estão nas categorias Baixa ou Cosmético/UI (75%), enquanto 2 possuem severidade Média (25%).**
O resultado demonstra que a suíte possui capacidade de encontrar problemas de diferentes naturezas, mas a severidade deve sempre ser analisada em conjunto com impacto, frequência, alcance e risco para o usuário, e não apenas pela quantidade de ocorrências.

### Análise Relação entre os dois gráficos

Os gráficos, analisados em conjunto, mostram duas dimensões diferentes da estratégia utilizada:

```text
Gráfico Testes por Feature → Onde os testes foram concentrados.
Gráfico Bugs por Severidade → Qual foi o perfil de severidade dos problemas encontrados.
```

Dessa maneira, não é correto concluir que uma Feature é mais problemática apenas por ter recebido mais testes ou apresentado mais bugs. Neste projeto, o escopo foi definido com base exclusivamente no que estava disponível e observável na versão demo do qaFood, sem acesso a dados reais de produção, logs, histórico de incidentes ou casos reportados por usuários.

Para uma análise de causa raiz mais completa, seria necessário cruzar os dados em uma matriz **Feature × quantidade de bugs × severidade × causa raiz**, considerando também fatores como impacto e recorrência. Esse cruzamento permitiria identificar onde há maior concentração de risco na aplicação, evitando conclusões baseadas apenas na quantidade de testes ou defeitos encontrados.

##  🕵🏻‍♂️ Root Cause Analysis (RCA) 

Os 8 bugs documentados na suíte não são falhas isoladas: eles se agrupam em 4 causas raiz distintas, cada uma revelando uma lacuna específica no processo de desenvolvimento do aplicativo, não apenas um sintoma pontual na interface.

### 🫆 Causa Raiz 1: Busca sem normalização

<img width="1598" height="988" alt="mermaid-diagram" src="https://github.com/user-attachments/assets/c6b41a55-e742-485e-aef5-8ef9ac90342e" />

- **Busca sem normalização** é a que concentra o maior número de ocorrências (3 bugs: BUG-01, BUG-02, BUG-03). 

A raiz comum é que a comparação de texto na busca e no login não normaliza maiúsculas, minúsculas e espaços antes de comparar com o valor cadastrado — um problema clássico de ausência de sanitização de input no lado do cliente ou do backend. É a causa mais recorrente e, por isso, a que mais impacta a experiência real do usuário: qualquer variação natural de digitação (Caps Lock ligado, espaço acidental) quebra uma funcionalidade central do app.

### 🫆 Causa Raiz 2: Falta de persistência de estado

<img width="1075" height="948" alt="mermaid-diagram" src="https://github.com/user-attachments/assets/ede1e549-2de8-44ca-b645-8b3876bf816f" />

- **Falta de persistência:** de estado agrupa BUG-05 e BUG-06, ambos derivados da mesma origem: a ausência de persistência de sessão entre reinicializações do aplicativo. É importante notar que essa causa raiz foi classificada como "Limitação / possível bug", diferente da Causa Raiz 1, que é bug de UX confirmado, aqui existe a possibilidade de ser uma decisão arquitetural intencional (por exemplo, política de segurança que força reautenticação). Isso está corretamente sinalizado nos dois cards e deveria ser validado com o time de desenvolvimento antes de ser tratado como defeito a corrigir.

### 🫆 Causa Raiz 3: Eventos de teclado

- **Eventos de teclado:** é a única com um único bug associado (BUG-04), mas com uma causa raiz bem definida: o formulário de login escuta apenas o evento de toque no botão, ignorando completamente os eventos de submissão via teclado (Enter/Done). Diferente das outras três causas, essa é classificada diretamente como "Bug funcional", sem ambiguidade pois a submissão via teclado é um comportamento padrão esperado em qualquer formulário mobile bem implementado, não uma decisão de design defensável.

<img width="550" height="948" alt="mermaid-diagram (1)" src="https://github.com/user-attachments/assets/1e99d03f-5c44-4f8f-8b5c-b43e5f5fa3dc" />

### 🫆 Causa Raiz 4: Revisão de texto e nomenclatura

<img width="1078" height="983" alt="mermaid-diagram" src="https://github.com/user-attachments/assets/db3b7673-8a4b-4052-a682-c196de54a1c0" />

- **Revisão de texto e nomenclatura:** agrupa os dois bugs cosméticos (BUG-07, BUG-08), com uma causa raiz de processo, não de lógica: ausência de uma etapa de QA de copy/nomenclatura antes do build. Vale notar que essa é a única causa raiz que produz dois tipos de classificação diferentes a partir da mesma origem "Bug de conteúdo/UI" (o typo visível ao usuário) e "Problema de nomenclatura" (o tipo interno no código, invisível ao usuário final, mas relevante para manutenibilidade).

### 🫆 Conclusão

Das quatro causas raiz, **duas (Causa Raiz 1 e 3)** apontam para o mesmo tipo de lacuna: tratamento insuficiente de entrada do usuário, seja normalização de texto e também na captura de eventos de interação. Isso sugere que o time de desenvolvimento pode se beneficiar de uma revisão mais ampla de como os formulários da aplicação lidam com input do usuário, em vez de tratar cada bug como um caso isolado a corrigir individualmente.

Já a **Causa Raiz 2**, por ser classificada como possível decisão intencional, é a única que exige confirmação externa antes de qualquer ação. Dessa maneira, reforça a importância de não tratar toda observação de QA como bug automático, mas de manter a diferenciação entre "comportamento inesperado" e "comportamento não confirmado como esperado".

---

## 🧪 Metodologia de teste

A construção da suíte qaFood seguiu um processo iterativo, combinando técnicas formais de design de testes com investigação exploratória sempre que o comportamento do aplicativo não estava documentado previamente.

**Particionamento de equivalência e análise de valor-limite**

Foram aplicados de forma sistemática, principalmente na Feature Login e na Feature Lojas: campos testados com valores válidos, valores vazios, valores no limite de tamanho (e-mails e senhas muito longos) e valores fora do padrão esperado (caracteres especiais, espaços em branco isolados ou combinados).

- **Teste negativo:** Foi usado extensivamente para garantir que o aplicativo rejeita corretamente entradas inválidas sem quebrar, credenciais incorretas, buscas sem resultado, cupons inválidos e tentativas de finalizar pedido sem forma de pagamento selecionada.

- **Teste exploratório:** Foi a técnica central para descobrir comportamentos não óbvios do aplicativo, como a sensibilidade da busca a texto em maiúsculas. Esse bug específico não foi encontrado por um caso de teste pré-planejado, mas por uma investigação incremental: cada resultado inesperado gerava uma nova hipótese, testada isoladamente até isolar exatamente o padrão do problema (qualquer palavra inteira em maiúsculas, independentemente da posição no termo buscado).

- **Teste de regressão implícito:** Ocorre a cada nova execução completa da suíte, servindo como rede de segurança para identificar quebras de comportamento em versões futuras do aplicativo.

- **Teste de condição de corrida (concorrência):** Foi aplicado em pontos críticos de interação rápida do usuário — duplo toque no botão de login e no botão de adicionar item ao carrinho — para verificar se o app processa múltiplas ações quase simultâneas sem duplicar submissões indevidamente.

- **Teste de robustez do sistema operacional:** Validou o comportamento do app sob condições fora do controle direto da aplicação: rotação de tela, transição para segundo plano e retorno, e reinicialização completa do processo, cobrindo cenários de uso real que vão além da interação direta com a interface.

### ⚠️ Observação
```text
Essa combinação de técnicas  planejadas e exploratórias, permitiu não apenas confirmar que as funcionalidades atendem ao comportamento esperado, mas também identificar bugs reais que não estariam cobertos por um roteiro de teste estritamente linear.
```
---

## 🚧 Limitações e escopo

Por se tratar de um aplicativo de estudo e não uma base de produção real, o escopo de testes foi definido a partir apenas do que estava disponível e observável na versão demo utilizada. Diferente de um ambiente de produção, onde o QA tem acesso a logs, dados reais de usuários, variações de cenários trazidas por bugfixes e hotfixes recorrentes, e uma base maior de casos de uso reportados diariamente pelo time e pelos clientes, este projeto foi construído com as informações que puderam ser confirmadas manualmente, tela a tela, ao longo do processo de exploração do app qaFood.

Isso significa que alguns cenários ficaram intencionalmente fora do escopo por falta de confirmação de comportamento ou de elementos de interface disponíveis para inspeção:

- **Remoção individual de item da sacola**: Não foi possível confirmar a existência nem o identificador do botão de remoção/decremento de quantidade.
- **Aplicação de cupom válido**: Só foi possível validar o fluxo de cupom inválido e cupom vazio; nenhum cupom promocional válido estava disponível para teste.
- **Categorias/abas do cardápio**: Não foi confirmado se o cardápio possui navegação por categorias (ex: "Lanches", "Bebidas") ou se é uma lista única rolável.
- **Login social e Funcionalidade de mostrar/ocultar senha**: Confirmado que essas funcionalidades não existem na versão testada do app.
- **Testes de Rede**: (Modo avião, Conexão instável), exigiriam manipulação via ADB fora do escopo do Maestro puro, e não foram priorizados para este projeto.
---

## 🚀 Próximos passos (CI/CD)

Atualmente, a suíte é executada manualmente, com o emulador Android rodando localmente no Windows e os testes disparados via Maestro CLI a partir do WSL. A automação da execução via **GitHub Actions** foi avaliada como evolução natural do projeto, mas não foi implementada nesta fase por uma limitação técnica real, não por falta de planejamento:

O Maestro depende de um **emulador Android ativo** (ou um dispositivo físico conectado) para executar qualquer teste — ele não interage com o app de forma "headless" ou simulada. Rodar um emulador Android dentro de um runner padrão do GitHub Actions exige:

- Um runner com suporte a virtualização aninhada e aceleração de hardware (KVM), o que limita as opções gratuitas do GitHub Actions e normalmente exige runners self-hosted ou serviços de nuvem especializados em Android (como Firebase Test Lab ou runners customizados com GPU).
- Tempo de boot do emulador consideravelmente mais alto em ambiente de CI do que localmente, aumentando o tempo total de pipeline e, consequentemente, o custo de execução.
- Configuração adicional de rede para expor o emulador ao Maestro dentro do runner, replicando a mesma ponte ADB usada localmente entre Windows, WSL e o emulador.

Diante dessas restrições, a decisão consciente foi priorizar a qualidade e a cobertura da suíte nesta fase, deixando a automação via CI como **próximo passo declarado** do projeto. Uma futura implementação consideraria:

```bash
1. Uso de runners self-hosted com suporte a KVM, ou serviços de nuvem para testes Android (Firebase Test Lab, BrowserStack App Automate).
2. Gatilho do pipeline em pull requests e merges para a branch principal.
3. Publicação automática dos relatórios de execução do Maestro como artefato do workflow.
4. Notificação de falhas via integração com Slack ou e-mail.
```
Essa análise técnica, por si só, já reflete uma etapa importante do planejamento de qualidade: reconhecer as limitações de infraestrutura antes de tentar implementar uma automação que não seria sustentável no formato gratuito do GitHub Actions.

Essas exclusões não representam falhas na cobertura, mas sim decisões conscientes de escopo, tomadas com base na informação disponível em cada momento, uma prática comum e necessária em qualquer ciclo real de testes.

---

## 💡 Aprendizados técnicos

- **Sintaxe YAML:** `appId` fica no cabeçalho do arquivo, antes do `---`, nunca dentro da lista de comandos. Seletores como `id:` precisam de indentação correta e espaço após os dois-pontos (`id: "email"`, e não `id:"email"`).
- **`tapOn` não digita:** para preencher campos, utilize `inputText` após o comando de toque, quando necessário.
- **Ambiguidade de seletores:** `rightOf: "texto"` e `point: "x%,y%"` são frágeis após scroll e podem clicar no elemento errado sem gerar erro. Prefira o `id` real do elemento, descoberto via `maestro hierarchy` ou pelo Inspector do Maestro Studio.
- **`scrollUntilVisible` é just-in-time:** revelar um elemento não garante que os próximos também fiquem visíveis. Utilize um `scrollUntilVisible` para cada elemento que precise ser tocado ou validado.
- **Alertas e pop-ups de confirmação:** título e corpo do modal geralmente são utilizados com `assertVisible` para validação; o botão de ação final deve ser acionado com `tapOn`.
- **IDs confirmados no app:** `add-item-buttom` (sic — contém erro de digitação no próprio app), `open-cart-button` e `back-button`.
- **Mensagens reais confirmadas:** `"Erro ao realizar login"`, `"CUPOM inválido"` e `"Selecione uma forma de pagamento"`.
- **Ciclo de vida do aplicativo:** fechar/reabrir o app com `launchApp: clearState: false` **não preserva a sessão de login neste aplicativo**. É necessário refazer o `runFlow` de login mesmo sem limpar o estado.

---

## ✅ Contato

 
| LinkedIn                   |  https://www.linkedin.com/in/diogoamanciosilva/ |
| ------------------------- | ------: |

| E-mail                   |  diogoamanciosilva@gmail.com/ |
| ------------------------- | ------: |

