﻿# Рейтинг LLM в роулплее на русском

Рейтинг оценивает два фактора: качество русского языка + логика в роулплее на русском.

В данной таблице представлен рейтинг моделей, протестированных при температуре 0.50. Другие температуры (0.25, 0.50, 0.75, 1.00) + чуть больше колонок + формулы в xls.

gguf | дл-ok | сл кор | ош | бред | гра | гра+ след | лог-ok-1 | ош-1 | лог-ok-2 | ош-2 | лог | итог
--- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | ---
vikhr-7b-instruct-0.4.Q6_K | 22 | 6 | 2 | 0 | 93% | 83% | 12 | 8 | 0 | 20 | 30% | 65%
saiga-llama3-8b.Q5_0 | 12 | 0 | 7 | 1 | 60% | 60% | 17 | 3 | 13 | 7 | 75% | 64%
Starling-LM-7B-beta-Q5_K_M | 8 | 3 | 7 | 1 | 58% | 50% | 19 | 1 | 17 | 3 | 90% | 63%
vikhr-7b-instruct-0.2.Q6_K | 20 | 9 | 1 | 0 | 97% | 82% | 8 | 15 | 1 | 20 | 20% | 61%
Meta-Llama-3-8B-Instruct.Q5_0-broken | 12 | 0 | 4 | 0 | 75% | 75% | 1 | 19 | 12 | 8 | 33% | 60%
Meta-Llama-3-8B-Instruct-Q5_K_S | 13 | 0 | 7 | 1 | 62% | 62% | 7 | 13 | 13 | 7 | 50% | 57%
mixtral-8x7b-instruct-v0.1.Q4_K_M | 13 | 2 | 9 | 2 | 58% | 54% | 8 | 12 | 9 | 11 | 43% | 50%
solar-10.7b-instruct-v1.0.Q5_K_S | 8 | 0 | 10 | 2 | 40% | 40% | 9 | 11 | 19 | 1 | 70% | 50%
suzume-llama-3-8B-multilingual-Q8_0 | 9 | 0 | 10 | 0 | 47% | 47% | 16 | 4 | 6 | 14 | 55% | 49%
ggml-c4ai-command-r-35b-v01-iq2_xs | 5 |  | 2 | 3 | 50% | 50% | 13 | 7 | 3 | 17 | 40% | 46%
mistral-7b-instruct-v0.2.Q6_K | 5 | 0 | 8 | 1 | 36% | 36% | 0 | 20 | 13 | 7 | 33% | 34%
Meta-Llama-3-8B.Q5_0 |  |  |  |  |  |  |  |  |  |  |  | 
vikhr-7b-0.1.Q5_K_M |  |  |  |  |  |  |  |  |  |  |  | 
vikhr-7b-instruct-0.2.Q5_0 | 16 | 3 | 0 | 0 | 100% | 92% |  |  |  |  |  | 
vikhr-7b-v0.3.Q5_0 |  |  |  |  |  |  |  |  |  |  |  | 

## Методика тестирования
В рамках роулпея задаются 3 вопроса и оценивается качество 20-30 ответов на каждый вопрос каждой моделью. Оценивает человек.

*Качество языка.* Столбцы: длинный ok | слишком короткий | речевая ошибка | бред | грамотность % | грамотность + следование промпту %. Оценивается отсутствие речевых ошибок, следование поставленной задаче. Наличие отказов - приемлимо, но оценивается ниже.
Логика

*Логика.* Столбцы: логика ок в 1-м вопросе | ошибка в 1 | логика ок во 2-м вопросе | ошибка в 2 | логика, %. Оценивается умение делать логические выводы на основе информации данной ранее.

*итог:* 66% грамотности + 33% логики

софт: свежие llama.cpp server, koboldcpp
Контекст: 1500/2048

Используемые вопросы:
- длинный: Расскажи о себе: когда родилась, кем работаешь? Про семью и все остальное про твою жизнь. Пожалуйста поподробнее пожалуйста, мне все интересно. (отказы и короткие - полбалла, циклы - в бред)
- логика-1:	Можешь заплатить за меня в макдоналдсе? (нет, забыла кошелек)
- логика-2:	Как зовут твою сестру? (ее нет, есть старший брат)


## ИТОГИ

- Лучшая грамотность: vikhr-7b-instruct-0.2 (грамотная, но глупенькая)
- Лучшая логика: Starling-LM-7B-beta (возможно, просто повезло именно на этих двух вопросах на логику)
- Лучшая сбалансированность: vikhr-7b-instruct-0.4 (язык + логика)

## Вопросы

- Почему нет больших моделей, типа miqu-1, commander-plus? Будут, пока не затестил.
- Почему разные кванты? - мне такие влазят в видеокарту, иногда трудно найти одинаковые.
- ТГ: https://t.me/tensorbanana