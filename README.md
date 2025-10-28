# ATIVIDADE PONDERADA DE PROGRAMAÇÃO SEMANA 3

Bill of Materials

| material | quantidade |
| -----|-----|
| jumper fêmea - macho | 6 |
| resistores | 3 |
| protoboard | 1 |
| arduíno UNO | 1 |
| USB tipo A-B | 1 |

# Tabela de Avaliação entre Pares

**Avaliador:** Antonio Di Cillo

| Critério | Contempla (Pontos) | Contempla Parcialmente (Pontos) | Não Contempla (Pontos) | Observações do Avaliador |
|-----------|--------------------|----------------------------------|------------------------|---------------------------|
| Montagem física com cores corretas, boa disposição dos fios e uso adequado de resistores | Nota 3 | Nota 1,5 | 0 | Nota 3 (por mais que o aarelo tenha quebrado, foi esperto ao utilizar outra cor) |
| Temporização adequada conforme tempos medidos com auxílio de algum instrumento externo | Até 3 | Até 1,5 | 0 | Nota 3 |
| Código implementa corretamente as fases do semáforo e estrutura do código (variáveis representativas e comentários) | Até 3 | Até 1,5 | 0 | Nota 3 (bem comentado e estruturado) |
| Ir além: Implementou um componente de extra, fez com millis() ao invés do delay() e/ou usou ponteiros no código | Até 1 | Até 0,5 | 0 | Nota 1 |
| **Pontuação Total** | - | - | - | 10 |

# Tabela de Avaliação entre Pares

**Avaliador:** Caue Taddeo

| Critério | Contempla (Pontos) | Contempla Parcialmente (Pontos) | Não Contempla (Pontos) | Observações do Avaliador |
|-----------|--------------------|----------------------------------|------------------------|---------------------------|
| Montagem física com cores corretas, boa disposição dos fios e uso adequado de resistores | Nota 3 | Nota 1,5 | 0 | Nota 3 |
| Temporização adequada conforme tempos medidos com auxílio de algum instrumento externo | Até 3 | Até 1,5 | 0 | Nota 3 |
| Código implementa corretamente as fases do semáforo e estrutura do código (variáveis representativas e comentários) | Até 3 | Até 1,5 | 0 | Nota 3 (bem comentado e estruturado) |
| Ir além: Implementou um componente de extra, fez com millis() ao invés do delay() e/ou usou ponteiros no código | Até 1 | Até 0,5 | 0 | Nota 1 |
| **Pontuação Total** | - | - | - | 10 |

##Código utilizado:
```cpp
// declaração das variáveis intervalo e previousMillis
int intervalo;
unsigned long previousMillis = 0;

bool tempoMillis(int interval){ // / criação da função tempoMillis() para temporizar e controlar o tempo do semáforo usando millis()
  intervalo = interval;
    unsigned long currentMillis = millis(); // obtém o tempo atual desde que o Arduino foi iniciado
    if (currentMillis - previousMillis >= intervalo) { // verifica se o intervalo desejado já passou
      previousMillis = currentMillis; // atualiza o tempo anterior
      return true; // retorna verdadeiro para indicar que o tempo foi atingido
    } else {
      return false; /// caso contrário, ainda não atingiu o intervalo
}
}

void setup()  {  
  pinMode(11, OUTPUT);
  pinMode(10, OUTPUT);
  pinMode(13, OUTPUT);
  Serial.begin(5000);
};

void loop()  {
  while (!tempoMillis(6000)) { // enquanto não se passam 6 segundos, acende o led vermelho e apaga os outros
    digitalWrite(10, HIGH);
    digitalWrite(13, LOW);
    digitalWrite(11, LOW);
  }
  while(!tempoMillis(4000)){ // enquanto não se passam 4 segundos, acende o led verde e apaga os outros
    digitalWrite(10, LOW);
    digitalWrite(13, HIGH);
    digitalWrite(11, LOW);
  }
  while(!tempoMillis(2000)){ // enquanto não se passam 2 segundos, acende o led amarelo e apaga os outros
    digitalWrite(10, LOW);
    digitalWrite(13, LOW);
    digitalWrite(11, HIGH);
  }
};
```

LINK DEMONSTRAÇÃO DO VÍDEO - https://github.com/thuliobacco/ponderada_prog_ard2.git

![WhatsApp Image 2025-10-28 at 14 58 38](https://github.com/user-attachments/assets/5aac2ae0-c5f7-4960-847b-dae851775be6)
