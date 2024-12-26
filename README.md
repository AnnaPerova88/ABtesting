# ABtesting

# Методы анализа для A/B тестирования

Этот репозиторий включает реализации статистических методов для A/B тестирования, таких как **Bootstrap**, **Стратификация**, **CUPED** и **CUPAC**.

---

## Методы

### 1. **Bootstrap**
Метод используется для оценки доверительных интервалов метрик с помощью повторной выборки.

**Пример кода**:
```python
ci = confidence_interval(sample, confidence=0.95)
print(f"Доверительный интервал: {ci}")

### 2. **Стратификация**
Снижает вероятность ложных срабатываний за счет разделения данных на страты (бинны).

A_strat, B_strat = stratified_samples(df, 'metric', 'strata', bins, 1000)
pvalue = ttest_ind(A_strat, B_strat)[1]
print(f"P-value: {pvalue}")

### 3. **CUPED**
Уменьшает вариативность метрик с использованием ковариат из предварительных данных, повышая точность анализа.

df_cuped = cuped(df, target='arpu_now', groups='treat_flag', covariate='arpu_prev')
print(f"Отношение стандартных отклонений: {std_after / std_before}")

### 4. **CUPAC** 
Расширяет CUPED для работы с категориальными ковариатами.
df_cupac = cupac(df, target='metric', groups='test_group', covariate='category_feature')
