# 🎛️💡 Potentiometer → LED Brightness

في هذا المشروع سنستخدم **Potentiometer** للتحكم في شدة إضاءة LED. 💡

عند تدوير المقبض، تتغير إضاءة الـ LED تدريجيًا.

---

## 🎯 فكرة المشروع

```text
🎛️ Potentiometer
       ↓
   Arduino A0
       ↓
   تحويل القيمة
       ↓
💡 LED Brightness
```

عندما ندوّر الـ Potentiometer:

🔄 القيمة تتغير
⬇️
💡 شدة إضاءة LED تتغير

---

## 🧰 المكونات

* Arduino Uno 🤖
* Potentiometer 10kΩ 🎛️
* LED 💡
* Resistor 220Ω
* Breadboard
* Jumper Wires
* USB Cable

---

## 🔌 التوصيل

### Potentiometer

| Potentiometer | Arduino |
| ------------- | ------- |
| الطرف الأول   | 5V      |
| الطرف الأوسط  | A0      |
| الطرف الثالث  | GND     |

### LED

| LED         | Arduino               |
| ----------- | --------------------- |
| Anode (+)   | Pin 9 عبر مقاومة 220Ω |
| Cathode (-) | GND                   |

---

## 💻 كود Arduino

```cpp
int potentiometer = A0;
int ledPin = 9;

void setup()
{
  pinMode(ledPin, OUTPUT);
}

void loop()
{
  int value = analogRead(potentiometer);

  int brightness = map(value, 0, 1023, 0, 255);

  analogWrite(ledPin, brightness);
}
```

---

## 🧠 كيف يعمل الكود؟

Arduino يقرأ قيمة الـ Potentiometer:

```cpp
analogRead(potentiometer);
```

القيمة تكون بين:

```text
0 → 1023
```

لكن `analogWrite()` يستخدم قيمًا بين:

```text
0 → 255
```

لذلك نستخدم:

```cpp
map()
```

لتحويل القيمة.

```text
0     → LED مطفأ
127   → إضاءة متوسطة
255   → إضاءة قوية
```

---

## 💡 النتيجة

عند تدوير الـ Potentiometer:

🔄 إلى اليسار → 💡 إضاءة ضعيفة

🔄 في المنتصف → 💡 إضاءة متوسطة

🔄 إلى اليمين → 💡 إضاءة قوية

---

## 🚀 ماذا تعلمنا؟

من خلال هذا المشروع تعلمنا:

* 🎛️ قراءة Potentiometer
* 🔢 استخدام `analogRead()`
* 🔄 استخدام `map()`
* 💡 التحكم في شدة LED
* ⚡ استخدام `analogWrite()`
* 📊 تحويل القيم من مجال إلى مجال آخر

---

## 📚 في كتاب Arduino

هذا المشروع مرتبط بدرس:

**Potentiometer → التحكم في شدة إضاءة LED**
