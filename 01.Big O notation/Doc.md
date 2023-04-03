<h1 align=center><b>Big O notation</b></h1>

> Algorithm - muammoni yechish uchun harakatlar ketma-ketligiga aytiladi.

> Data Structure - ma'lumotlarni saqlash va tartibga solish uchun ishlatiladigan konteyner yoki saqlagich.

**Computer Science**da biz ko'pincha algoritmlarning ishlashini tahlil qilishga qiziqamiz. Algoritm ishlash tezligini aniqlash uchun turli xil **input**lar uchun algoritmimiz qancha vaqt sarflayotganini bilishimiz kerak. Misol uchun ro'yxatni tartiblaydigan algoritm yaratsak, u 10 ta raqam uchun qancha vaqt, 100 ta raqam uchun qancha vaqt, 1000 ta raqam  uchun qancha vaqt ketishini o'lchashimiz mumkin.

Qachonki gap Algoritm **tahlil**i haqida ketganda, bizga quyidagi ikki narsa doim qiziq bo'lishi lozim:

1. **Time** - Qancha vaqt ketkazayabdi? (Nechta operatsiya bajaradi)
2. **Memory** - Qancha xotira ketkazayabdi? (Qancha joy oladi)

Bilamizki hayotda o'lchovchi asboblar mavjud, masalan suvni o'lchash uchun **litr** yozilgan maxsus konteynerlardan foydalanamiz, uzunlikni o'lchash uchun **sm** yoki **m** o'lchamlari bor lineyka va ruletkalardan foydalanamiz. Ammo Algoritmlar uchun nimadan foydalanamiz?

### **Big O notation - Katta O belgisi**

Big O notation Algoritmlarni tezligini o'lchash uchun ishlatiladigan asbob deb olsak bo'ladi. Algoritmga qanchalik katta hajmdagi ma'lumot kiritilsa u o'sha ma'lumot ustida bajaradigan operatsiyalar soni ham oshib boradi. Aynan shu orqali biz bilishimiz mumkinki, qancha xajmdagi ma'lumot uchun bizning algoritmimiz qancha vaqt va xotira talab qilishini.

> **Big O notation**ni tushunish uchun Matematikaga biroz murojaat qilamiz. Chunki Dasturlashda Matematikani o'rni juda muhim!

Matematikada funksiya degan tushuncha mavjud. Biz uni mana bu ko'rinishda ifodalashimiz mumkin.

`
f(x) = x + 2
`

Bu yerda biz `f(x)` dagi `x`ga necha qiymatni bersak u o'sha qiymatni qavsdan keyingi ifodaga ham beradi degani misol uchun mana bunday:

`
f(10) = 10 + 2
`

Dasturlashga buni qanday dahli bor deyishingiz mumkin ammo shoshilmang endi yetib kelayabmiz. `x`ga qancha katta qiymat bersak shuncha katta qiymat olayabmiz. Endi tasavvur qiling qiyinroq funksiyalarda bu ko'rsatgichlar qanchalik kattarishini. Endi algoritmlarni qanday o'lchashlikga o'tsak bo'ladi.

Qachonki biz algoritmlarni tahlil qilganimizda, qancha kattalikdagi qiymatga <i>nechta operatsiya bajarayabdi</i> va <i>qancha xotira talab qilayabdi</i> degan savolni ilg'or suramiz.

Tasavvur qiling, bizni algoritm berilgan **array**dagi qiymatlardan faqat juft sonlarni yangi arrayga qo'shib, oxirida o'sha **array**ni qaytarishi kerak.

```c
#include <stdio.h>

int* juftlar(int arry[], int n, int* result_size) {
    int* result = malloc(n * sizeof(int));
    *result_size = 0;
    for (int i = 0; i < n; i++) {
        if (arry[i] % 2 == 0) {
            result[*result_size] = arry[i];
            (*result_size)++;
        }
    }
    return result;
}
```

Yuqorida keltirilgan funksiyani oladigan bo'lsak biz qanchalik kattalikda array bersak u shunchalik ko'p operatsiya bajaradi. Misol uchun `[1, 2, 3, 4, 5]` ni bersak u 5ta sonni ham tekshiadi va ularni ichidan nechtasi juft bo'lsa uni yangi arrayga o'tkazadi. Agar array ichidagi elementlar soni 100ta bo'lsa 100ta operatsiya, `n` ta bo'lsa `n` ta operatsiya sodir qiladi. 

### **Time Complexity - Vaqt murakkabligi**

Biz buni `O(n)` ko'rinishda o'lchasak bo'ladi. Chunki qanchalik elementlar ko'p bo'lsa algoritm shunchalik ko'p operatsiya bajaradi. Ya'ni siz 100ta elementli array bersangiz funksiyadagi loop 100 marta iteratsiya qiladi, 1000 ta bersangiz 1000 marta iteratsiya qiladi. Har bir iteratsiya esa bu bitta operatisya (harakat) degani.

> Big O notation - algoritmni **worst case** xolati uchun ishlatiladi. Ya'ni worst case - eng yomon xolati deb tarjima qilsak bo'ladi.

Biz bu tahlilga algoritmimiz eng yomon ko'rsatkichda ishlaganda `n` marta ishlaydi deb qarasak bo'ladi. Agarda sizning algoritmingiz `O(n)` ko'rsatgichda bo'lsa dasturlashda uni `Linear Time` deb atashadi. Endi esa keling xotiraga ham to'xtalib o'tsak qanday qilib xotirani o'lchashimiz mumkin?

### **Space Complexity**

Biz xotira murakkabligini MB yoki GB larda o'lchamaymiz biz uni ham Big O notation orqali o'lchaymiz. Ammo qanday deyishingiz mumkin? Keling uni ham ko'rib chiqsak.

Yuqoridagi kodni **Time Complexity**si `O(n)` bo'lgan bo'lsa **Space Complexity**si ham `O(n)` bo'layabdi. Ammo nimaga asoslanib, keling tushuntiraman. 

Bu yerda array hajmi oshgani sari biz qaytaradigan `result` nomli array hajmi ham oshib boradi. Agar biz 50ta juft sonlardan iborat array kiritsak u barcha elementlarni `result`ga qo'shishiga to'g'ri keladi chunki ularni 50tasi ham juft. Ya'ni aytib o'tganimdek Big O notation **worst case** holatini o'lchash uchun ishlatiladi. 

Agar biz 100ta element bor array bersak va arraydagi 50ta raqam juft, 50tasi esa toq sonlardan iborat bo'lsa bining ko'rsatgich `O(n/2)` ko'rsatgichni beradi. Ammo foydalanuvchi qanday array berishi bizga noma'lumo bo'lgani uchun ham biz uni `O(n)` deb olaveramiz. Demak bu narsaga tushundingiz deb umid qilaman.

O'lchov birliklari juda ko'p. Ularni ba'zilarini hozir ushbu qo'llanma davomida o'rganishingiz mumkin, qolganlarini esa sayohatimiz va o'rganish paytida kashf qilib ketamiz.

<br>

<h2 align=center><b>Time Complexities</b></h2>

### **Constant Time - O(1)**

Constant - o'zgarmas degan ma'noni anglatadi. Matematikada konstant qiymat nimada bor desa men `pi ≈ 3.14159` ni ayta olaman. Biz constant qiymatni Big O da `O(1)` deb o'lchaymiz. Nima uchun aynan 1 soni keltirilganini tushuntirishga menimcha xojat yo'q chunki qiymat **bir**xil qolishi aytilayabdi. Kelin endi misol bilan ko'rsak

```c
#include <stdio.h>

void* access_element(void** arr, int index) {
    return arr[index];
}
```

Yuqorida keltirilgan kodda bizning `access_element` funksyamizga istalgan kattalikda input bermaylik u bu ishni qilishga bir xil vaqt sarflaydi. Ya'ni operatsiyalar soni bu yerda 1ta. 

```c
#include <stdio.h>

int access_element(int *arr, int index) {
    return arr[index];
}
```

Bu ham huddi shunday istalgan xajmdagi qiymat bermaylik operatsiyalar soni oshmaydi ya'ni doim bitta operatsiya amalga oshiradi. Shuning uchun ham uni **worst case**da `O(1)` deb o'lchaymiz. 

<br>

### **Linear Time - O(n)**

Linear - Chiziqli degan ma'noni anglatadi. Tasavvur qiling oldingizda 100ta xona bor va har bir xona eshigida uning raqami bor. Xonalarni 99tasi bo'sha ammo bittasida xazina yashiringan. Siz esa o'sha xazinani topishingiz kerak. Xonalarni siz 1-eshikdan ochishni boshlaysiz keyin 2-eshik keyin 3-eshik va h.k.z.

Eng ko'pi bilan siz 100ta xonani barchasini ochishingizga to'g'ri keladi. Ko'rib turibsizki omadingiz bo'lsa uni 1tada ham topishingiz mumkin. Agar unday bo'lmasa demak 100ta eshikni ham ochib ko'rasiz. Bir narsani yana eslatib o'taman biz Big O notation bilan faqat **worst case** holatini tahlil qilamiz. Kelin endi kod bilan ko'radigan bo'lsak.

```c
#include <stdio.h>

int* juftlar(int arry[], int n, int* result_size) {
    int* result = malloc(n * sizeof(int));
    *result_size = 0;
    for (int i = 0; i < n; i++) {
        if (arry[i] % 2 == 0) {
            result[*result_size] = arry[i];
            (*result_size)++;
        }
    }
    return result;
}
```

Yuqoridagi kodda tasvirlanganidek biz `result` degan o'zgaruvchi ochib uni 0ga tenglashtirdik. Va keyin for loop orqali, funksiyaga beriladigan list qiymatini iteratsiya qilamiz. Iteratsiya har bir raqamni `result` o'zgaruvchisizga increment qilib borayabdi va oxirida esa uni qaytarayabdi. 

Demak bu yerda operatsiyalar soni bevosita funksiyaga beriladigan listning hajmiga bog'liq. Agar listda 23 ta element bo'lsa funksiyamiz 23 operatsiya bajaradi, agar 1 ta bo'lsa 1ta agar `n`ta bo'lsa `n`ta. Biz buni `O(n)` deb o'lchadik!

<br>

### **Quadratic Time - O(n<sup>2</sup>)**

Quadratic - Kvadrat darajali degan ma'noni anglatadi. Tasavvur qiling ishxonada ho'jayiningiz sizga "Xonani 2 marta tekshiring" desa siz 4 marta tekshirasiz, "4 marta tekshiring" desa siz 16 marta tekshirasiz. Mana shu jarayon aynan quadratic deb atasak bo'ladi.

```c
#include <stdio.h>

void numered_num(int num) {
    for (int i = 0; i < num; i++) {
        for (int j = 0; j < num; j++) {
            printf("%d.%d\n", i, j);
        }
    }
}
```

Yuqorida keltirilgan kodda nested-loop tasvirlangan. Biz funksiyaga necha qiymatni bersak u o'sha qiymatni kvadratichalik ko'p operatsiya bajaradi. Agar biz unga 2 ni kiritsak u 4 ta operatsiya qiladi, agar 5 ni kiritsak u 25 ta operatsiya bajaradi. Demak biz uni <code>O(n<sup>2</sup>)</code> 

<br>

<h2 align=center><b>Space Complexities</b></h2>

### **Constant Space**

```c
#include <stdio.h>

int summing(int numbers[], int n) {
    int result = 0;
    for (int i = 0; i < n; i++) {
        result += numbers[i];
    }
    return result;
}
```

Yuqorida keltirilgan kodning **space complexity**si `O(1)`. Sababi bizning funksiyamiz 100 ta elementli listga ham 1 000 000 000 elementli listga ham bir xil ishlaydi. Operatsiyalar soni ko'p bo'lgani bilan biz barchasini faqat bitta `result` degan o'zgaruvchiga saqlayabmiz.

```c
#include <stdio.h>

void sum_odds_evens(int nums[], int n) {
    int odds = 0;
    int evens = 0;
    for (int i = 0; i < n; i++) {
        if (nums[i] % 2 == 0) {
            evens += nums[i];
        } else {
            odds += nums[i];
        }
    }
    printf("odds = %d, evens = %d", odds, evens);
}
```

Mana bu kodda ham **Space Complexity** `O(1)`ga teng. Chunki bizda funksiya boshlanishida ham tugashida ham faqat 2ta o'zgaruvchi qolayabdi. Ya'ni funksiyamiz yangi o'zgaruvchilar ochmayabdi, faqat bor o'zgaruvchilarni qiymati o'zgarayabdi. Demak agar funksiyangizdagi o'zgaruvchilar soni oshmasa.

<br>

### **Linear Space**

```c
#include <stdio.h>
#include <stdlib.h>

void count_frequency(int arr[], int n) {
    int* freq_dict = (int*) calloc(n, sizeof(int));
    for (int i = 0; i < n; i++) {
        freq_dict[arr[i]]++;
    }
    printf("{ ");
    for (int i = 0; i < n; i++) {
        if (freq_dict[i] > 0) {
            printf("%d:%d, ", i, freq_dict[i]);
        }
    }
    printf("}");
    free(freq_dict);
}
```

Bu funksiya berilgan list ichida takrorlangan elementlar sonini sanaydi. Keling pastda qiymat berib ko'ramiz va berilgan qiymatga u qanday javob berishini Output orqali ifodalaymiz.

```c
// Input: ["apple", "banana", "apple", "orange", "apple"]

// Output: {'apple': 3, 'banana': 1, 'orange': 1}
```

Yuqorida ko'rib turganingizdek array ichida takrorlanmaydigan so'zlar bo'lsa **worst case**da bizning funksiyamizni **Space Complexity**si `O(n)` ni tashkil qiladi. Agar omadimiz kelib takrorlanuvchi so'zlar bo'lsa n ta emas 1 ta ham bo'lishi mumkin.

<br>

### **Quadratic Space**

```c
#include <stdio.h>
#include <stdlib.h>

void generate_pairs(int arr[], int n) {
    printf("[ ");
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            printf("(%d, %d), ", arr[i], arr[j]);
        }
    }
    printf("]");
}
```

Yuqoridagi funksiya list ichidagi har bir elementni sherik qilib `pairs` degan yangi listga qo'shib boradi.

```c
// Input: [1, 2, 3]

// Output: [(3, 3), (3, 6), (3, 9), (6, 3), (6, 6), (6, 9), (9, 3), (9, 6), (9, 9)]
```

Ko'rib turibsizki listimiz hajmi qancha kattalashsa qaytariladigan qiymat soni ham uning kvadratiga teng bo'ladi. Yuqoridagi misolda bizning listimizda 3 ta element bor edi ammo funksiya qaytargan yangi list esa 9ta elementdan iborat bo'ldi. Shuning uchun ham biz uni <code>O(n<sup>2</sup>)</code> deb o'lchaymiz.

<br>

Yana bir necha misolla keltirishimiz mumkin ammo qolganini sayohatimiz davomida o'rganib ketamiz. Hozircha shular edi.

[➡️ Keyingi darsga o'tish](#)

[⬅️ Asosiy sahifaga qaytish](../README.md) 
