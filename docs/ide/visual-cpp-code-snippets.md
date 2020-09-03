---
title: Visual C++ kod parçacıkları
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77277835"
---
# <a name="visual-c-code-snippets"></a>Visual C++ kod parçacıkları

Visual Studio 'da, C++ kod dosyalarınıza yaygın olarak kullanılan kodu eklemek için kod parçacıklarını kullanabilirsiniz. Genel olarak, kod parçacıklarını C# ile aynı şekilde kullanabilirsiniz, ancak varsayılan kod parçacıkları kümesi farklıdır.

Kodunuzda belirli bir konuma (ekleme) bir kod parçacığı ekleyebilir veya seçili bir kodu kod parçacığı ile çevreleyin.

## <a name="insert-a-code-snippet"></a>Kod parçacığı Ekle

Bir kod parçacığı eklemek için bir C++ kod dosyası (*. cpp* veya *. h*) açın, dosyanın içinde herhangi bir yere tıklayın ve aşağıdakilerden birini yapın:

- Bağlam menüsünü almak için sağ tıklayın ve **kod parçacığı Ekle** ' yi seçin.

- **Düzenle/IntelliSense** menüsünde **kod parçacığı Ekle** ' yi seçin.

- Kısayol tuşlarını kullanın: **CTRL** + **K** + **X**

**#İf**başlayan seçeneklerin bir listesini görmeniz gerekir. **#İf**' yi seçtiğinizde, dosyaya aşağıdaki kodun eklendiğini görmeniz gerekir:

```cpp
#if 0

#endif // 0
```

Daha sonra **0** değerini doğru koşulla değiştirebilirsiniz.

## <a name="use-a-code-snippet-to-surround-selected-code"></a>Seçilen kodu çevrelemek için bir kod parçacığı kullanın

Seçilen kodu çevrelemek için bir kod parçacığı kullanmak için bir satır (veya birden çok satır) seçin ve aşağıdakilerden birini yapın:

- Bağlam menüsünü almak için sağ tıklayın ve şununla **Çevrele** ' yi seçin

- **Edit**  >  **IntelliSense** düzenleme menüsünde **Şununla Çevrele** ' yi seçin

- Klavye kullanarak, şunu bas: **CTRL** + **K** + **S**

**#İf**seçin. Şuna benzer bir şey görmeniz gerekir:

```cpp
#if 0
#include "pch.h"  // or whatever line you had selected
#endif // 0
```

Daha sonra 0 değerini doğru koşulla değiştirebilirsiniz.

## <a name="where-can-i-find-a-complete-list-of-the-c-code-snippets"></a>C++ kod parçacıklarının tamamen bir listesini nerede bulabilirim?

C++ kod parçacıklarının tüm listesini **kod parçacıkları Yöneticisi** ' ne giderek ( **Araçlar** menüsünde) ve **dili** **Visual C++** olarak ayarlayarak bulabilirsiniz. Aşağıdaki pencerede **Visual C++**' ı genişletin. Tüm C++ kod parçacıklarının adlarını alfabetik sırada görmeniz gerekir.

Çoğu kod parçacıklarının adı kendi kendine açıklayıcıdır, ancak bazı adlar kafa karıştırıcı olabilir.

## <a name="class-vs-classi"></a>Sınıf ve classı karşılaştırması

**Sınıf** parçacığı, `MyClass` uygun varsayılan Oluşturucu ve yıkıcısı ile adlı bir sınıfın tanımını sağlar; burada Oluşturucu ve yıkıcının tanımlarının sınıfın dışında bulunduğu yer vardır:

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

**Classı** kod parçacığı ayrıca adlı bir sınıfın tanımını da sağlar `MyClass` , ancak varsayılan Oluşturucu ve yıkıcısı sınıf tanımı içinde tanımlanmıştır:

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

## <a name="for-vs-forr-vs-rfor"></a>vs. öğrencilerinize vs rfor için

Farklı türlerde döngüler sağlayan kod parçacıkları **için** üç farklı vardır `for` .

**Rfor** kod parçacığı, [Aralık tabanlı](/cpp/cpp/range-based-for-statement-cpp) bir for döngüsü (bağlantı) sağlar. Bu yapı, dizin tabanlı `for` Döngülerde tercih edilir.

```cpp
for (auto& i : v)
{

}
```

**For** kod parçacığında, `for` koşulun bir nesnenin uzunluğuna (içindeki) göre kullanıldığı bir döngü sağlar `size_t` .

```cpp
for (size_t i = 0; i < length; i++)
{

}
```

**Öğrencilerinize** kod parçacığı, `for` koşulun bir nesnenin uzunluğuna (tamsayı cinsinden) dayanmakta olduğu ters bir döngü sağlar.

```cpp
for (int i = length - 1; i >= 0; i--)
{

}
```

## <a name="the-destructor-snippet-"></a>Yıkıcı parçacığı (~)

Yıkıcı parçacığı ( **~** ) farklı bağlamlarda farklı davranışlar gösterir. Bu kod parçacığını bir sınıfın içine eklerseniz, bu sınıf için bir yıkıcı sağlar. Örneğin, aşağıdaki kod verildiğinde:

```cpp
class SomeClass {

};
```

Yıkıcı parçacığı eklerseniz, için bir yıkıcı sağlar `SomeClass` :

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

## <a name="see-also"></a>Ayrıca bkz.

- [Kod parçacıkları](../ide/code-snippets.md)