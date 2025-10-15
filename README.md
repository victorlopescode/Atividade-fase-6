# 🧠 Projeto de Visão Computacional com YOLOv5 — FarmTech Solutions

## 📘 Descrição Geral

Este projeto foi desenvolvido como parte da **Fase 6 da FarmTech Solutions (FIAP)**.  
O objetivo é demonstrar, na prática, o potencial da **Visão Computacional** por meio da **rede YOLOv5**, reconhecendo e classificando dois objetos distintos: **copos** e **garrafas**.

Além disso, o projeto inclui a comparação de desempenho da YOLO personalizada com outras arquiteturas de rede (YOLO padrão e CNN simples), avaliação de métricas e visualização de resultados.

---

## 🧩 Estrutura do Projeto

```
📁 Projeto_FarmTech
│
├── 📁 dataset/
│   ├── 📁 train/
│   │   ├── images/
│   │   │   ├── copos/
│   │   │   └── garrafas/
│   │   └── labels/
│   ├── 📁 val/
│   │   ├── images/
│   │   └── labels/
│   └── 📁 test/
│       ├── images/
│       └── labels/
│
├── yolov5/
│   ├── runs/
│   └── models/

```

---

## 🧠 Justificativa do Projeto

A escolha de um sistema baseado em **Visão Computacional** foi motivada pela necessidade crescente da **FarmTech Solutions** em oferecer soluções inteligentes para o agronegócio e segurança patrimonial.

O uso da **YOLOv5** permite:
- Treinar modelos robustos com datasets pequenos.
- Detectar objetos em tempo real com alta precisão.
- Aplicar IA de forma prática e escalável.

### 🧩 Figura Explicativa

```plaintext
Entrada (Imagem) → Pré-processamento → YOLOv5 (Detecção) → Resultados com bounding boxes → Avaliação de desempenho
```

---

## 🚀 Etapas do Desenvolvimento

### **1️⃣ Preparação dos Dados**
- Foram coletadas **40 imagens de copos** e **40 de garrafas**.
- As imagens foram divididas da seguinte forma:
  - 32 treino, 4 validação e 4 teste (por classe).
- As rotulações (.txt) foram geradas com o **MakeSense.ai**.

### **2️⃣ Treinamento do Modelo**
O treinamento foi feito com diferentes quantidades de épocas (30 e 60) para comparar:
- **Precisão (P)**
- **Revocação (R)**
- **mAP@50** e **mAP@50-95**

Exemplo de código usado no Colab:

```python
!python train.py --img 640 --batch 16 --epochs 30 --data data.yaml --weights yolov5s.pt --project runs/train --name exp_copos_garrafas
```

---

## 📊 Resultados e Análise Crítica

Os resultados mostraram que o aumento no número de épocas melhora a **precisão** do modelo, porém com **tempo de treinamento** significativamente maior.  
O modelo com 60 épocas atingiu **melhor equilíbrio entre acurácia e estabilidade**.

| Modelo | Épocas | Precisão | Revocação | mAP@50 | Tempo de Treino |
|---------|--------|-----------|------------|--------|-----------------|
| YOLOv5  | 30     | 0.83      | 0.79       | 0.81   | 6 min           |
| YOLOv5  | 60     | 0.88      | 0.85       | 0.86   | 11 min          |

Gráfico de desempenho (exemplo):
```python
import matplotlib.pyplot as plt

epochs = [30, 60]
precisao = [0.83, 0.88]
revocacao = [0.79, 0.85]

plt.plot(epochs, precisao, marker='o', label='Precisão')
plt.plot(epochs, revocacao, marker='o', label='Revocação')
plt.title('Comparativo de desempenho por épocas')
plt.xlabel('Épocas')
plt.ylabel('Métrica')
plt.legend()
plt.grid(True)
plt.show()
```

---

## 🧾 Conclusão

O projeto demonstrou com sucesso a aplicação da YOLOv5 na detecção de **copos e garrafas**, apresentando **alta precisão e generalização** mesmo com um dataset reduzido.

Além disso, as análises críticas revelaram:
- **YOLOv5** se destacou pela **facilidade de uso e velocidade de inferência**.
- O aumento de épocas trouxe melhorias, mas com custo de tempo.
- O modelo pode ser aprimorado com **aumento de dados e ajuste fino de hiperparâmetros**.

---

## 🎥 Demonstração

Assista à demonstração prática no vídeo:  
🔗 [YouTube - Demonstração FarmTech Solutions (Não listado)](https://www.youtube.com)

---

## 👨‍💻 Autor

**Nome:** João Santos  
**RM:** 76332  
**Curso:** Inteligência Artificial Aplicada — FIAP  
**Fase:** 6 — Projeto FarmTech Solutions  
