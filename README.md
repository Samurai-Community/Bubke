# Bubke
import time
import tracemalloc
import random

def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        for j in range(0, n - i - 1):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]

# Ввод пользователя
n = int(input("Введите размер массива n: "))

# Генерация случайного массива
arr = [random.randint(0, 10000) for _ in range(n)]

# Измерение времени
start_time = time.time()
tracemalloc.start()  # старт замера памяти

bubble_sort(arr)

current, peak = tracemalloc.get_traced_memory()
tracemalloc.stop()
end_time = time.time()

# Результаты
print(f"\nРазмер массива: {n}")
print(f"Время выполнения: {end_time - start_time:.6f} секунд")
print(f"Пиковое использование памяти: {peak / 1024:.2f} КБ")
