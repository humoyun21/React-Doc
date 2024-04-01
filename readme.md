### useState

`useState` hook'i, React dasturlash kutubxonasida ishlatiladigan birinchi React Hooks'lardan biridir. Ushbu hook, funksiyalarni React funksiyon komponentlari ichida ma'lumotni saqlash va uni yangilash uchun qo'llaniladi. `useState` hook'i yordamida komponentning harakat holati (state) saqlanadi va o'zgartirilishi mumkin bo'ladi.

`useState` hook'idan foydalanish uchun, komponentda uni import qilib olishimiz kerak. Bu `React` kutubxonasidan ham import qilinadi.

```jsx
import React, { useState } from 'react';
```

Keyingi qadamda, `useState` funktsiyasini komponentning ichida ishlatamiz:

```jsx
function Example() {
  // `useState` orqali state yaratiladi
  // `count` o'zgaruvchisi hozirgi qiymatni saqlaydi,
  // `setCount` esa uni o'zgartiruvchi funksiyani ifodalaydi
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Siz {count} marta bosdingiz</p>
      <button onClick={() => setCount(count + 1)}>
        Bosing
      </button>
    </div>
  );
}
```

`useState` funktsiyasi yordamida, o'zgaruvchini (`count`) va uni o'zgartirish uchun funksiyani (`setCount`) yaratamiz. Yuqoridagi misolda `count` o'zgaruvchisi har bir bosish tugmasi bosilganda 1 ga oshadi va bu qiymat komponentning interfeysida ko'rsatiladi. 

Bu usul React funksiyon komponentlarida o'zgaruvchilarni qo'llab-quvvatlashda juda mashhurdir, chunki bu yaxshi qo'llaniladigan va oddiydir.


### Form

ReactJS-da formalar ishlash uchun qo'llaniladigan oddiy usulni quyidagi misolda ko'rish mumkin:

```jsx
import React, { useState } from 'react';

function MyForm() {
  // Formada saqlanadigan malumotlarni holdanaylik holati
  const [formData, setFormData] = useState({
    firstName: '',
    lastName: '',
    email: ''
  });

  // Input elementlari o'zgarishlarini qo'llab-quvvatlash
  const handleInputChange = (event) => {
    const { name, value } = event.target;
    setFormData({
      ...formData,
      [name]: value
    });
  };

  // Forma yuborish
  const handleSubmit = (event) => {
    event.preventDefault();
    // Formada saqlangan malumotlarni yuborish
    console.log(formData);
  };

  return (
    <form onSubmit={handleSubmit}>
      <div>
        <label>
          Ism:
          <input
            type="text"
            name="firstName"
            value={formData.firstName}
            onChange={handleInputChange}
          />
        </label>
      </div>
      <div>
        <label>
          Familiya:
          <input
            type="text"
            name="lastName"
            value={formData.lastName}
            onChange={handleInputChange}
          />
        </label>
      </div>
      <div>
        <label>
          Elektron pochta:
          <input
            type="email"
            name="email"
            value={formData.email}
            onChange={handleInputChange}
          />
        </label>
      </div>
      <button type="submit">Yuborish</button>
    </form>
  );
}

export default MyForm;
```

Ushbu kodda, ReactJS funksiyon komponenti `MyForm` yaratilgan. Uning ichida `useState` hook'i yordamida formadagi malumotlar (`formData`) saqlanadi. Har bir input o'zgaruvchisining o'zgartirishiga mos ravishda, `handleInputChange` funksiyasi orqali `formData` yangilanadi. `handleSubmit` funksiyasi orqali forma yuborish jarayoni boshlanadi.

Har bir input elementi (`<input />`) `value` atributi orqali `formData`ning mosligi bilan bog'langanligi uchun, o'zgartirishda ishlatiladigan funksiya (`onChange`) ko'rsatilgan. Bu usul orqali, har bir o'zgaruvchini kiritishda, `formData` avtomatik ravishda yangilanadi.

Forma yuborilganda, `handleSubmit` funksiyasi ishga tushadi va `formData` konsolga chiqariladi. Bizning misolda, konsolga chiqarish kerakligi uchun, `console.log(formData)` qo'llanilgan. Bunda siz forma yuborilganda, forma ichidagi malumotlar brauzer konsolida chiqadi. O'zgartirishlarni backendga yuborish uchun kerakli qadamni qo'shishingiz kerak.



### Events

ReactJS-da o'zgarishlarni aniqlash va boshqa amallarni bajarish uchun yana React-dan kelgan tuzilgan hodisalar (events) mavjud. Bundan foydalanish uchun, siz elementlarga tegishli hodisalarni belgilashingiz kerak.

Quyidagi misolda, qanday qilib `onClick` hodisasini qo'llab-quvvatlashni ko'rsataman:

```jsx
import React from 'react';

function MyComponent() {
  // Bu funksiya tugmani bosganda ishga tushadi
  const handleClick = () => {
    console.log('Tugma bosildi');
  };

  return (
    <div>
      {/* onClick hodisasi orqali handleClick funksiyasini chaqirish */}
      <button onClick={handleClick}>Bosing</button>
    </div>
  );
}

export default MyComponent;
```

Yuqoridagi misolda, `onClick` hodisasini qo'llab-quvvatlash uchun `handleClick` nomli funksiya aniqlangan. Bu funksiya tugmani bosganda ishga tushadi va konsolga "Tugma bosildi" matnini chiqaradi. `handleClick` funksiyasi boshqa har qanday JavaScript funksiyasi kabi ishlaydi.

ReactJS-da qo'llaniladigan boshqa hodisalar:

- `onChange`: Qiymatlarda o'zgarishlar bo'lganda ishga tushadi.
- `onSubmit`: Forma yuborilganda ishga tushadi.
- `onMouseEnter` va `onMouseLeave`: Elementga kirganda yoki uning ustiga tushganda ishga tushadi.
- va boshqalar.

Har bir hodisa uchun belgilash funksiyasini yaratish va uni React elementiga bog'lash juda oddiy va qulaydir.