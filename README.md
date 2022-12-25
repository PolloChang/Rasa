# Rasa
Rasa 學習筆記

## 執行 shell

```bash
rasa shell --model ~/Documents/gitContent/jameschang/Rasa/data/models/20221224-100156-counting-altitude.tar.gz
```

### 檢查模型

```
rasa shell nlu
```

```
NLU model loaded. Type a message and press enter to parse it.
Next message:
感冒了該吃什麼藥
Building prefix dict from the default dictionary ...
Loading model from cache /tmp/jieba.cache
Loading model cost 0.657 seconds.
Prefix dict has been built successfully.
{
  "text": "感冒了該吃什麼藥",
  "intent": {
    "name": "medicine",
    "confidence": 0.9999823570251465
  },
  "entities": [
    {
      "entity": "disease",
      "start": 0,
      "end": 2,
      "confidence_entity": 0.998053789138794,
      "value": "感冒",
      "extractor": "DIETClassifier"
    }
  ],
  "text_tokens": [
    [
      0,
      2
    ],
    [
      2,
      3
    ],
    [
      3,
      4
    ],
    [
      4,
      5
    ],
    [
      5,
      8
    ]
  ],
  "intent_ranking": [
    {
      "name": "medicine",
      "confidence": 0.9999823570251465
    },
    {
      "name": "medical_department",
      "confidence": 1.569145024404861e-05
    },
    {
      "name": "goodbye",
      "confidence": 8.522318921677652e-07
    },
    {
      "name": "greet",
      "confidence": 7.992261998879258e-07
    },
    {
      "name": "medical_hospital",
      "confidence": 2.627865853810363e-07
    }
  ]
}
```

## 訓練

```bash
rasa train --config config.yml --domain domain.yml --data data/
rasa train --config configs/config.yml --domain configs/domain.yml --data data/

```

### 模型: nlu

```
rasa train nlu
```

## API

```bash
curl http://127.0.0.1:5005/model/parse -d '{"text":"hello"}'
```

##

20221218-232143-clever-gunwale.tar