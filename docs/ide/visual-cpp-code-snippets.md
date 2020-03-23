---
title: Görsel C++ kod parçacıkları
ms.date: 11/04/2016
ms.topic: reference
author: corob-msft
ms.author: corob
manager: markl
dev_langs:
- CPP
ms.workload:
- cplusplus
ms.openlocfilehash: db6ea1e233d32872322926a4d75b847ee6a49ba3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77277835"
---
# <a name="visual-c-code-snippets"></a>Görsel C++ kod parçacıkları

Visual Studio'da, C++ kod dosyalarınıza sık kullanılan kod eklemek için kod parçacıklarını kullanabilirsiniz. Genel olarak, kod parçacıklarını C#'dakiyle aynı şekilde kullanabilirsiniz, ancak varsayılan kod parçacıkları kümesi farklıdır.

Kodunuzdaki belirli bir konuma bir kod parçacığı ekleyebilir (ekleme) veya bazı seçili kodu kod parçacığıyla çevreleyebilirsiniz.

## <a name="insert-a-code-snippet"></a>Kod snippet ekleme

Bir kod parçacığı eklemek için, bir C++ kod dosyası *(.cpp* veya *.h)* açın, dosyanın içinde bir yere tıklayın ve aşağıdakilerden birini yapın:

- Bağlam menüsünü almak için sağ tıklatın ve **Snippet Ekle'yi** seçin

- **Edit / IntelliSense** menüsünde **Snippet Ekle'yi** seçin

- Kısayol tuşlarını kullanın: **Ctrl**+**K**+**X**

**#if**ile başlayan seçeneklerin listesini görmelisiniz. **#if**seçtiğinizde, dosyaya eklenen aşağıdaki kodu görmeniz gerekir:

```cpp
#if 0

#endif // 0
```

Daha sonra doğru koşul ile **0** değiştirebilirsiniz.

## <a name="use-a-code-snippet-to-surround-selected-code"></a>Seçili kodu çevreleyen bir kod parçacığı kullanma

Seçili kodu çevreleyen bir kod parçacığı kullanmak için bir satır (veya birden çok satır) seçin ve aşağıdakilerden birini yapın:

- Bağlam menüsünü almak için sağ tıklatın ve **Surround With'i** seçin

- **IntelliSense'i** **Edit** > menüsünden **Surround With'i** seçin

- Klavye kullanarak, **ctrl**+**K**+**S** tuşuna basın

**#if'ı**seçin. Şunun gibi bir görüntüyle karşılaşacaksınız:

```cpp
#if 0
#include "pch.h"  // or whatever line you had selected
#endif // 0
```

Daha sonra doğru koşul ile 0 değiştirebilirsiniz.

## <a name="where-can-i-find-a-complete-list-of-the-c-code-snippets"></a>C++ kod parçacıklarının tam listesini nerede bulabilirim?

**Kod Parçacıkları Yöneticisi'ne** giderek **(Araçlar** menüsünde) C++ kod parçacıklarının tam listesini bulabilir ve **Dili** **Visual C++** olarak ayarlayabilirsiniz. Aşağıdaki pencerede **Visual C++**'yı genişletin. Tüm C++ kod parçacıklarının adlarını alfabetik sırada görmelisiniz.

Çoğu kod parçacıklarının adları kendi kendini açıklar, ancak bazı adlar kafa karıştırıcı olabilir.

## <a name="class-vs-classi"></a>Sınıf ve classi

**Sınıf** parçacığı, kurucu ve yıkıcının tanımlarının sınıfın dışında yer aldığı uygun varsayılan oluşturucu ve yıkıcı ile adlandırılmış `MyClass`bir sınıfın tanımını sağlar:

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

**Classi** kodu snippet de adlı `MyClass`bir sınıfın tanımını sağlar, ancak varsayılan oluşturucu ve yıkıcı sınıf tanımı içinde tanımlanır:

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

## <a name="for-vs-forr-vs-rfor"></a>vs forr vs rfor için

Farklı `for` döngüler sağlayan parçacıklar **için** üç farklı vardır.

**Rfor** snippet döngü (bağlantı) için [bir aralık tabanlı](/cpp/cpp/range-based-for-statement-cpp) sağlar. Bu yapı dizin tabanlı `for` döngüler yerine tercih edilir.

```cpp
for (auto& i : v)
{

}
```

**For** snippet, `for` koşulun bir nesnenin uzunluğuna (in) `size_t`dayandığı bir döngü sağlar.

```cpp
for (size_t i = 0; i < length; i++)
{

}
```

**Forr** snippet, koşulun bir nesnenin uzunluğuna (tamsayılarda) dayandığı bir ters `for` döngü sağlar.

```cpp
for (int i = length - 1; i >= 0; i--)
{

}
```

## <a name="the-destructor-snippet-"></a>Yıkıcı parçacığı (~)

Yıkıcı parçacığı (**~**) farklı bağlamlarda farklı davranışlar gösterir. Bu parçacığı bir sınıfın içine eklerseniz, o sınıf için bir yıkıcı sağlar. Örneğin, aşağıdaki kod verilmiştir:

```cpp
class SomeClass {

};
```

Yıkıcı parçacığı eklerseniz, aşağıdakiler için `SomeClass`bir yıkıcı sağlar:

```cpp
class SomeClass {
    ~SomeClass()
    {

    }
};
```

Yıkıcı parçacığı bir sınıfın dışına eklemeye çalışırsanız, yer tutucu adı olan bir yıkıcı sağlar:

```cpp
~TypeNamePlaceholder()
{
```

## <a name="see-also"></a>Ayrıca bkz.

- [Kod parçacıkları](../ide/code-snippets.md)