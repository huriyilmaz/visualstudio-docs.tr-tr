---
title: Visual C++ kod parçacıkları
description: C++ kod dosyalarınıza yaygın olarak kullanılan kod eklemek için kod parçacıklarını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: corob-msft
ms.author: corob
manager: markl
dev_langs:
- CPP
ms.workload:
- cplusplus
ms.openlocfilehash: 2e8b8f46cfd0ff2a7c7174186f32187782ed3a3d98956f333b8e592e7ff4f44e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121411782"
---
# <a name="visual-c-code-snippets"></a>Visual C++ kod parçacıkları

Bu Visual Studio C++ kod dosyalarınıza yaygın olarak kullanılan kodu eklemek için kod parçacıklarını kullanabilirsiniz. Genel olarak, kod parçacıklarını C# ile aynı şekilde kullanabilirsiniz, ancak varsayılan kod parçacıkları kümesi farklıdır.

Kodunuz içinde belirli bir konuma kod parçacığı ekleyebilir (ekleme) veya seçilen kodun çevresini kod parçacığıyla çevrelersiniz.

## <a name="insert-a-code-snippet"></a>Kod parçacığı ekleme

Kod parçacığı eklemek için bir C++ kod dosyası açın (*.cpp* veya *.h),* dosyanın içinde bir yere tıklayın ve aşağıdakilerden birini yapın:

- Bağlam menüsünü almak için sağ tıklayın ve Kod Parçacığı **Ekle'yi seçin**

- Düzenle **/ IntelliSense menüsünde** Kod Parçacığı Ekle'yi **seçin**

- Kısayol tuşlarını kullanma: **Ctrl** + **K** + **X**

ile başlayan seçeneklerin listesini **#if.** öğesini **#if** dosyasına aşağıdaki kodun ekli olduğunu görüyor olun:

```cpp
#if 0

#endif // 0
```

Ardından **0'ı doğru** koşulla değiştirebilirsiniz.

## <a name="use-a-code-snippet-to-surround-selected-code"></a>Seçili kodu çevrelerken kod parçacığı kullanma

Seçilen kodu çevreleyen bir kod parçacığı kullanmak için bir satır (veya birden çok satır) seçin ve aşağıdakilerden birini yapın:

- Bağlam menüsünü almak için sağ tıklayın ve Çevrele'yi **seçin**

-   >  **IntelliSense'i Düzenle menüsünde** Çevrele'yi **seçin**

- Klavye kullanarak şu tuşa basın: **Ctrl** + **K** + **S**

Öğesini **#if.** Şuna benzer bir şey görmeniz gerekir:

```cpp
#if 0
#include "pch.h"  // or whatever line you had selected
#endif // 0
```

Ardından 0'ı doğru koşulla değiştirebilirsiniz.

## <a name="where-can-i-find-a-complete-list-of-the-c-code-snippets"></a>C++ kod parçacıklarının tam listesini nerede bulamıyorum?

C++ kod parçacıklarının tam listesini, Kod Parçacıkları Yöneticisi'ne gidip  **(Araçlar** menüsünde) ve **Dil'i** **Visual C++.** Aşağıdaki pencerede, **Visual C++.** Tüm C++ kod parçacıklarının adlarını alfabetik sırada görüyor gerekir.

Çoğu kod parçacığının adları kendi kendine açıklayıcıdır, ancak bazı adlar kafa karıştırıcı olabilir.

## <a name="class-vs-classi"></a>Sınıf ve classi karşılaştırması

Sınıf **parçacığı,** oluşturucu ve yıkıcı tanımlarının sınıfın dışında bulunduğu uygun varsayılan oluşturucu ve yok etme ile adlı bir sınıfın `MyClass` tanımını sağlar:

```cpp
class MyClass
{
public:
    MyClass();
    ~MyClass();

private:

};

MyClass::MyClass()
{
}

MyClass::~MyClass()
{
}
```

classi **kod** parçacığı, adlı bir sınıfın tanımını da sağlar, ancak varsayılan oluşturucu ve yıkıcı `MyClass` sınıf tanımı içinde tanımlanır:

```cpp
class MyClass
{
public:
    MyClass()
    {
    }

    ~MyClass()
    {
    }

private:

};
```

## <a name="for-vs-forr-vs-rfor"></a>for vs. forr vs rfor

Farklı türlerde **döngüler** sağlayan kod parçacıkları için üç `for` farklı vardır.

**rfor kod parçacığı,** döngü [(bağlantı) için](/cpp/cpp/range-based-for-statement-cpp) aralık tabanlı bir sağlar. Bu yapı, dizin tabanlı döngülere göre `for` tercih edilir.

```cpp
for (auto& i : v)
{

}
```

for  kod parçacığı, `for` koşulun bir nesnenin uzunluğuna (içinde) bağlı `size_t` olduğu bir döngü sağlar.

```cpp
for (size_t i = 0; i < length; i++)
{

}
```

Forr **kod** parçacığı, koşulun bir nesnenin uzunluğunu (tamsayı olarak) temel alan `for` bir ters döngü sağlar.

```cpp
for (int i = length - 1; i >= 0; i--)
{

}
```

## <a name="the-destructor-snippet-"></a>Yıkıcı kod parçacığı (~)

Yıkıcı kod parçacığı ( **~** ) farklı bağlamlarda farklı davranışları gösterir. Bu kod parçacığını bir sınıfın içine eklersiniz, bu sınıf için bir yıkıcı sağlar. Örneğin, aşağıdaki koda göre:

```cpp
class SomeClass {

};
```

Yıkıcı kod parçacığını eklersanız, için bir yıkıcı `SomeClass` sağlar:

```cpp
class SomeClass {
    ~SomeClass()
    {

    }
};
```

Yıkıcı kod parçacığını bir sınıfın dışına eklemeye çalışsanız, yer tutucu adına sahip bir yıkıcı sağlar:

```cpp
~TypeNamePlaceholder()
{
```

## <a name="see-also"></a>Ayrıca bkz.

- [Kod parçacıkları](../ide/code-snippets.md)