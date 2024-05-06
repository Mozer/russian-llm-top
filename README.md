﻿# Рейтинг LLM в роулплее на русском

Рейтинг оценивает два фактора: качество русского языка + логика в роулплее на русском.

В данной таблице представлен рейтинг моделей, протестированных при температуре 0.50. Другие температуры (0.25, 0.50, 0.75, 1.00) + чуть больше колонок + формулы в [xls](https://github.com/Mozer/russian-llm-top/blob/main/%D1%80%D1%83%D1%81%D1%81%D0%BA%D0%B8%D0%B9-%D1%80%D0%B5%D0%B9%D1%82%D0%B8%D0%BD%D0%B3-llm-%D0%B2-%D1%80%D0%BE%D1%83%D0%BB%D0%BF%D0%BB%D0%B5%D0%B5.xlsx). Расшифровка имен стоблцов - внизу.


# | gguf | дл-ok | сл кор | ош | бред | гра | гра+ след | лог-ok-1 | ош-1 | лог-ok-2 | ош-2 | лог | итог
--- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | ---
1 | Meta-Llama-3-70B-Instruct-Q4_K_M | 24 | 2 | 5 | 1 | 81% | 78% | 20 | 0 | 20 | 0 | 100% | 85%
2 | miqu-1-70b.q5_K_M | 21 | 0 | 5 | 0 | 81% | 81% | 20 | 3 | 19 | 1 | 91% | 83%
3 | c4ai-command-r-plus.IQ3_M | 18 | 0 | 2 | 1 | 86% | 86% | 9 | 11 | 19 | 1 | 70% | 80%
4 | vikhr-7b-instruct-0.4.Q6_K | 22 | 6 | 2 | 0 | 93% | 83% | 12 | 8 | 0 | 20 | 30% | 65%
5 | saiga-llama3-8b.Q5_0 | 12 | 0 | 7 | 1 | 60% | 60% | 17 | 3 | 13 | 7 | 75% | 64%
6 | Starling-LM-7B-beta-Q5_K_M | 8 | 3 | 7 | 1 | 58% | 50% | 19 | 1 | 17 | 3 | 90% | 63%
7 | vikhr-7b-instruct-0.2.Q6_K | 20 | 9 | 1 | 0 | 97% | 82% | 8 | 15 | 1 | 20 | 20% | 61%
8 | Meta-Llama-3-8B-Instruct.Q5_0-broken | 12 | 0 | 4 | 0 | 75% | 75% | 1 | 19 | 12 | 8 | 33% | 60%
9 | Meta-Llama-3-8B-Instruct-Q5_K_S | 13 | 0 | 7 | 1 | 62% | 62% | 7 | 13 | 13 | 7 | 50% | 57%
10 | mixtral-8x7b-instruct-v0.1.Q4_K_M | 13 | 2 | 9 | 2 | 58% | 54% | 8 | 12 | 9 | 11 | 43% | 50%
11 | solar-10.7b-instruct-v1.0.Q5_K_S | 8 | 0 | 10 | 2 | 40% | 40% | 9 | 11 | 19 | 1 | 70% | 50%
12 | suzume-llama-3-8B-multilingual-Q8_0 | 9 | 0 | 10 | 0 | 47% | 47% | 16 | 4 | 6 | 14 | 55% | 49%
13 | ggml-c4ai-command-r-35b-v01-iq2_xs | 11 | 0 | 6 | 4 | 52% | 52% | 13 | 7 | 3 | 17 | 40% | 48%
14 | mistral-7b-instruct-v0.2.Q6_K | 5 | 0 | 8 | 1 | 36% | 36% | 0 | 20 | 13 | 7 | 33% | 34%

## Методика тестирования
В рамках роулпея и контекста на 1500 токенов задаются 3 вопроса и оценивается качество 20-30 ответов на каждый вопрос каждой моделью при заданной температуре. Оценивает человек.

**Качество языка.** Столбцы: длинный ok | слишком короткий | речевая ошибка | бред | грамотность % | грамотность + следование промпту %. Оценивается отсутствие речевых ошибок, следование поставленной задаче. Наличие отказов - приемлемо, но оценивается ниже.

**Логика.** Столбцы: логика ок в 1-м вопросе | ошибка в 1 | логика ок во 2-м вопросе | ошибка в 2 | логика, %. Оценивается умение делать логические выводы на основе информации данной ранее.

**ИТОГ:** 66% грамотности + 33% логики

софт: свежие llama.cpp server, koboldcpp

Контекст: 1500/2048

Используемые вопросы:
- длинный: Расскажи о себе: когда родилась, кем работаешь? Про семью и все остальное про твою жизнь. Пожалуйста поподробнее, мне все интересно. (отказы и короткие - полбалла, циклы - в бред)
- логика-1:	Можешь заплатить за меня в макдоналдсе? (нет, забыла кошелек)
- логика-2:	Как зовут твою сестру? (ее нет, есть старший брат)

На счет температуры, и почему использую именно 0.50.
- 0.25 - минимум ошибок, но плохо с логикой, предсказуемость ответов
- 0.50 - баланс
- 0.75 - много речевых ошибок, хорошая логика
- 1.00 - шиза.

## ИТОГИ

- Лучшая грамотность: vikhr-7b-instruct-0.2 (грамотная, но глупенькая)
- Лучшая логика: Meta-Llama-3-70B-Instruct-Q4_K_M
- Лучшая сбалансированность: Meta-Llama-3-70B-Instruct-Q4_K_M (язык + логика)
- Лучшая сбалансированность среди малых LLM: vikhr-7b-instruct-0.4.Q6_K

## Замечания

- Почему разные кванты? - мне такие помещаются в видеокарту, иногда трудно найти одинаковые.
- Сайга-4 и suzume протестированы в старом кванте, но с override-kv tokenizer. По идее, качество не должно сильно пострадать, но имеет смысл переделать gguf
- llama-3-8b протестирована и в новом кванте и в старом + override-kv. Отличия - незначительные.
- Рейтинг - это мое личное мнение. В вашем варианте использования может быть абсолютно противоположный результат. Интересные модели и ваши мысли можете высказать в ТГ.
- ТГ: https://t.me/tensorbanana