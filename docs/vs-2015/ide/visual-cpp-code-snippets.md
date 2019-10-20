---
title: Görsel C++ kod parçacıkları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 74e26fd4-e5ca-4611-a816-0a521b4947a0
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 213f4299ac71c08118563a008abe065f2c02423e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655398"
---
# <a name="visual-c-code-snippets"></a>Visual C++ Kod Parçacıkları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'da kod dosyalarınıza yaygın olarak kullanılan kodu C++ eklemek için kod parçacıklarını kullanabilirsiniz. Genel olarak, kod parçacıklarını ile aynı şekilde kullanabilirsiniz C#, ancak varsayılan kod parçacıkları kümesi farklıdır.

 Kodunuzda belirli bir konuma (ekleme) bir kod parçacığı ekleyebilir veya seçili bir kodu kod parçacığı ile çevreleyin.

## <a name="inserting-a-code-snippet"></a>Kod parçacığı ekleme
 Bir kod parçacığı eklemek için bir C++ kod dosyası (. cpp veya. h) açın, dosyanın içinde herhangi bir yere tıklayın ve aşağıdakilerden birini yapın:

- Bağlam menüsünü almak için sağ tıklayın ve **kod parçacığı Ekle** ' yi seçin.

- **Düzenle/IntelliSense** menüsünde **kod parçacığı Ekle** ' yi seçin.

- Kısayol tuşlarını kullanın: **CTRL + K + X**

  **#İf**başlayan seçeneklerin bir listesini görmeniz gerekir. **#İf**' yi seçtiğinizde, dosyaya aşağıdaki kodun eklendiğini görmeniz gerekir:

```cpp
#if 0

#endif // 0
```

 Daha sonra 0 değerini doğru koşulla değiştirebilirsiniz.

## <a name="using-a-code-snippet-to-surround-selected-code"></a>Seçilen kodu çevrelemek için bir kod parçacığı kullanma
 Seçilen kodu çevrelemek için bir kod parçacığı kullanmak için bir satır (veya birden çok satır) seçin ve aşağıdakilerden birini yapın:

1. Bağlam menüsünü almak için sağ tıklayın ve şununla **Çevrele** ' yi seçin

2. **Düzenle/IntelliSense** menüsünde **Şununla Çevrele** ' yi seçin

3. Kısayol tuşlarını kullanın: **CTRL + K + S**

   **#İf**seçin. Şuna benzer bir şey görmeniz gerekir:

```cpp
#if 0
#include "pch.h"  // or whatever line you had selected
#endif // 0
```

 Daha sonra 0 değerini doğru koşulla değiştirebilirsiniz.

## <a name="where-can-i-find-a-complete-list-of-the-c-code-snippets"></a>C++ Kod parçacıklarının tamamen bir listesini nerede bulabilirim?
 Kod parçacıkları **yöneticisine** ( **Araçlar** menüsünde) C++ gidip **dili** **C++görsele**ayarlayarak kod parçacıklarının tüm listesini bulabilirsiniz. Aşağıdaki pencerede, **görsel C++** ' i genişletin. Tüm C++ kod parçacıklarının adlarını alfabetik sırada görmeniz gerekir.

 Çoğu kod parçacıklarının adı kendi kendine açıklayıcıdır, ancak bazı adlar kafa karıştırıcı olabilir.

## <a name="class-vs-classi"></a>Sınıf ve classı karşılaştırması
 **Sınıf** parçacığı, uygun varsayılan Oluşturucu ve yıkıcısıyla MyClass adlı bir sınıfın tanımını sağlar; burada Oluşturucu ve yıkıcının tanımlarının sınıfın dışında bulunduğu bir değer:

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

 Classı kod parçacığı, MyClass adlı bir sınıfın tanımını da sağlar, ancak varsayılan Oluşturucu ve yıkıcısı sınıf tanımı içinde tanımlanmıştır:

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

## <a name="for-vs-foreach-vs-forr-vs-rfor"></a>Vs. ForEach vs. öğrencilerinize vs rfor için
 Farklı türlerde döngüler sağlayan kod parçacıkları için dört farklı vardır.

 **For** kod parçacığında, koşulun bir nesnenin uzunluğuna (`size_t`) dayalı olduğu `for` bir döngüsü sağlar:

```cpp
for (size_t i = 0; i < length; i++)
{

}
```

 **Foreach** parçacığı, bir koleksiyonun üyeleri üzerinde yineleme yapan bir `for each` döngüsü sağlar:

```cpp
for each (object var in collection_to_loop)
{

}
```

 **Öğrencilerinize** kod parçacığı, koşulun bir nesnenin uzunluğuna (tamsayı cinsinden) dayanmakta olduğu bir ters `for` döngüsü sağlar:

```cpp
for (int i = length - 1; i >= 0; i--)
{

}
```

 **Rfor** kod parçacığı, [Aralık tabanlı](https://msdn.microsoft.com/library/5750ba1d-ba48-4236-a923-e32de8345c2d) bir for döngüsü (bağlantı) sağlar:

```cpp
for (auto& i : v)
{

}
```

## <a name="the-destructor-snippet-"></a>Yıkıcı parçacığı (~)
 Yıkıcı parçacığı ( **~** ) farklı bağlamlarda farklı davranışlar gösterir. Bu kod parçacığını bir sınıfın içine eklerseniz, bu sınıf için bir yıkıcı sağlar. Örneğin, aşağıdaki kod verildiğinde:

```cpp
class SomeClass {

};
```

 Yıkıcı parçacığı eklerseniz, SomeClass için bir yıkıcı sağlar:

```cpp
class SomeClass {
    ~SomeClass()
    {

    }
};
```

 Yıkıcı parçacığı bir sınıfın dışında eklemeye çalışırsanız, yer tutucu adına sahip bir yıkıcı sağlar:

```cpp
~TypeNamePlaceholder()
{

```
