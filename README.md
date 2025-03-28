# Проекта прогнозирования цен на квартиры по их характеристикам

  Этот проект предназначен для предсказания стоимости жилой недвижимости на основе данных, предоставленных в соревновании Kaggle "House Prices - Advanced Regression Techniques". В проекте была использована глубокая нейронная сеть (DNN), обученная на характеристиках недвижимости, таких как площадь, количество комнат, год постройки и другие параметры.

1. Использованные данные
  Датасет содержит информацию о домах в США, включая числовые и категориальные признаки.
  Количественные признаки:
  OverallQual – общее качество материалов и отделки (1–10);
  GrLivArea – жилая площадь в квадратных футах;
  TotalBsmtSF – общая площадь подвала;
  1stFlrSF, 2ndFlrSF – площадь первого и второго этажей;
  GarageCars – количество машин, помещающихся в гараже;
  GarageArea – площадь гаража;
  YearBuilt – год постройки дома;
  YearRemodAdd – год последнего ремонта или реконструкции;
  LotArea – площадь земельного участка;
  FullBath, HalfBath – количество полных и половинных ванных комнат;
  TotRmsAbvGrd – общее количество комнат (без ванных);
  Fireplaces – количество каминов;
  MasVnrArea – площадь облицовки дома кирпичом

Все числовые данные были нормализованы с помощью StandardScaler, чтобы ускорить обучение нейросети.

2. Качественные признаки:
  Neighborhood – район, в котором находится дом;
  BldgType – тип здания (отдельный дом, таунхаус и т. д.);
  HouseStyle – архитектурный стиль;
  RoofStyle – тип крыши;
  Exterior1st, Exterior2nd – материалы внешней отделки;
  Foundation – тип фундамента;
  Heating – тип отопления;
  GarageType – тип гаража (пристроенный, встроенный и т. д.);
  SaleCondition – условия продажи (обычная, форсированная продажа и т. д.).
  Пропущенные значения в категориальных признаках заменялись значением "Unknown", чтобы избежать ошибок при обучении.

  Модель обучалась на комбинации числовых и категориальных признаков, что позволяет учитывать как физические характеристики дома, так и его расположение, качество постройки и условия продажи. Это дает более точные предсказания, так как учитываются различные факторы, влияющие на стоимость недвижимость.

3. Построение и обучение нейронной сети
Перед обучением модель должна работать только с числовыми данными. Поэтому мы:
  ✅ Удаляем ненужные столбцы (например, Id, который не несет полезной информации).
  ✅ Заполняем пропущенные значения (средними значениями для числовых данных, "Unknown" – для категориальных).
  ✅ Кодируем категориальные признаки с помощью One-Hot Encoding.
  ✅ Нормализуем данные, приводя их к одному масштабу (например, с помощью StandardScaler).

4. Структура нейронной сети
   Нейросеть состоит из входного слоя, нескольких скрытых слоев и выходного слоя.
   Входной слой получает данные с количеством признаков, равным числу столбцов в X_train;
   Скрытые слои содержат 128, 64 и 32 нейрона, используют ReLU в качестве функции активации;
   Выходной слой состоит из 1 нейрона без активации, так как нам нужно предсказать вещественное число (цену дома в $).

5. Заключение
Проект по предсказанию цен на недвижимость представляет собой полезный инструмент для автоматической оценки стоимости жилья на основе исторических данных. Он упрощает процесс ценообразования, позволяя продавцам и покупателям принимать обоснованные решения, а риэлторам и инвесторам – прогнозировать изменения на рынке. Благодаря использованию нейросетей модель учитывает множество факторов, исключая субъективность и ошибки, присущие традиционным методам оценки. Такой подход делает анализ недвижимости более точным, быстрым и доступным, что повышает эффективность работы в сфере недвижимости и финансов.

