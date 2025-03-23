# Controle de Matriz de LEDs WS2812B com Raspberry Pi Pico

## Descrição
Este projeto demonstra como controlar uma matriz de LEDs WS2812B (também conhecidos como NeoPixel) usando um Raspberry Pi Pico. O projeto utiliza dois botões para alternar entre diferentes padrões de cores na matriz de LEDs. O código foi desenvolvido em C e utiliza a API do Pico SDK para interagir com o hardware.

---

## Estrutura do Projeto
O projeto consiste em:

- **Inicialização do hardware**: Configuração dos pinos e inicialização da máquina de estado PIO para controle dos LEDs.
- **Controle dos LEDs**: Definição de funções para configurar cores individuais dos LEDs, limpar a matriz e enviar dados para os LEDs.
- **Lógica dos botões**: Verificação do estado dos botões para alternar entre diferentes padrões de cores na matriz de LEDs.

---

## Configurações

### Hardware
- **Raspberry Pi Pico**: Microcontrolador baseado no RP2040.
- **Matriz de LEDs WS2812B**: Matriz de 5x5 LEDs controláveis individualmente.
- **Botões**: Dois botões conectados aos pinos GPIO 5 (Botão A) e GPIO 6 (Botão B).

### Conexões
- **LED_PIN**: Pino GPIO 7 conectado ao pino de dados da matriz de LEDs.
- **BUTTON_A**: Pino GPIO 5 conectado ao Botão A.
- **BUTTON_B**: Pino GPIO 6 conectado ao Botão B.

### Software
- **Pico SDK**: SDK oficial para desenvolvimento no Raspberry Pi Pico.
- **PIO (Programmable I/O)**: Utilizado para gerar o sinal de controle necessário para os LEDs WS2812B.

---

## Funcionamento do Código

### Inicialização
- `npInit(uint pin)`: Inicializa a máquina de estado PIO para controle dos LEDs. Configura o pino de dados e limpa o buffer de pixels.
- `npClear()`: Limpa o buffer de pixels, definindo todas as cores como preto (0, 0, 0).
- `npSetLED(uint index, uint8_t r, uint8_t g, uint8_t b)`: Define a cor de um LED específico no buffer.
- `npWrite()`: Envia os dados do buffer para os LEDs, atualizando suas cores.

### Lógica dos Botões
- **Botão A**: Quando pressionado, exibe um padrão de cores azul na matriz de LEDs.
- **Botão B**: Quando pressionado, exibe um padrão de cores verde na matriz de LEDs.
- **Ambos os Botões**: Quando ambos os botões são pressionados simultaneamente, a matriz de LEDs é mostrada de forma síncrona.

### Função de Mapeamento
- `getIndex(int x, int y)`: Converte coordenadas (x, y) da matriz 5x5 para o índice correspondente no vetor de LEDs, considerando o padrão de fiação da matriz (zig-zag).

---

## Como Compilar e Executar

### Configuração do Ambiente
1. Instale o Pico SDK e configure o ambiente de desenvolvimento conforme as instruções oficiais.
2. Conecte o Raspberry Pi Pico ao computador via USB.

### Compilação
1. Utilize o CMake para gerar os arquivos de build.
2. Compile o projeto usando o comando:
   ```sh
   make
   ```

### Upload
1. Copie o arquivo `.uf2` gerado para o Raspberry Pi Pico enquanto ele está em modo de bootloader (segure o botão BOOTSEL ao conectar o USB).

### Execução
- Após o upload, o programa será executado automaticamente.
- Pressione os botões A e B para alternar entre os padrões de cores.

---

## Explicação dos Padrões de Cores

### Padrão do Botão A
- Um padrão de "X" azul é exibido na matriz de LEDs.
- As cores são definidas pela matriz `matriz[5][5][3]`.

### Padrão do Botão B
- Um padrão de "T" verde é exibido na matriz de LEDs.
- As cores são definidas pela matriz `matriz2[5][5][3]`.

- ## Demonstração do Projeto

Confira o vídeo abaixo para ver o projeto em funcionamento:

https://youtu.be/OpmRPl6gOmk

---

## Considerações Finais
Este projeto é um exemplo básico de como controlar uma matriz de LEDs WS2812B usando o Raspberry Pi Pico. Ele pode ser expandido para incluir mais padrões de cores, efeitos de transição, ou até mesmo integração com sensores para criar interações mais complexas.

Para mais informações sobre o Pico SDK e a API PIO, consulte a [documentação oficial](https://github.com/raspberrypi/pico-sdk).

---

## Autor
- **Nome**: Phaola Paraguai Da Paixão Lustosa  
- **Data**: 15/02/2025  

Sinta-se à vontade para contribuir ou sugerir melhorias!

