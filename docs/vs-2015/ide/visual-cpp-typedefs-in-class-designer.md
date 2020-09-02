---
title: Sınıf Tasarımcısı Visual C++ Typedefs | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.typedef
- vs.classdesigner.aliasofline
helpviewer_keywords:
- Class Designer [Visual Studio], typedefs
ms.assetid: c1984108-71fc-4d3a-b4d4-3eac2c6b4ebf
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 980c49aafba55e29714d786e492f7bb37a8ca621
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646744"
---
# <a name="visual-c-typedefs-in-class-designer"></a>Sınıf Tasarımcısında Visual C++ Typedefs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

TypeDef deyimleri, bir ad ve temel alınan türü arasında bir veya daha fazla yöneltme katmanı oluşturur. Sınıf Tasarımcısı, anahtar sözcüğüyle belirtilen C++ typedef türlerini destekler `typedef` , örneğin:

```
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
} COORD;
```

 Daha sonra bu türü bir örnek bildirmek için kullanabilirsiniz:

 `COORD OriginPoint;`

 Bir typedef adı olmadan bildirebilseniz de Sınıf Tasarımcısı belirttiğiniz etiket adını kullanmaz; Sınıf Görünümü oluşturduğu adı kullanacaktır. Örneğin, aşağıdaki bildirim geçerlidir, ancak Sınıf Görünümü ve Sınıf Tasarımcısı **__unnamed**adlı bir nesne olarak görünür:

```
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
};
```

 Türü kullanma hakkında daha fazla bilgi için `typedef` bkz. [(NOTINBUILD) typedef tanımlayıcısı](https://msdn.microsoft.com/cc96cf26-ba93-4179-951e-695d1f5fdcf1).

 C++ typedef şeklinin, typedef içinde belirtilen türün şekli vardır. Örneğin, kaynak bildirirse `typedef class` , şekil yuvarlak köşeler ve Label **sınıfına**sahiptir. İçin `typedef struct` , şeklinin kare köşeleri ve Label **yapısı**vardır.

 Sınıfların ve yapıların içinde bildirildiği iç içe tür tanımları olabilir; Bu nedenle, sınıf ve yapı şekilleri iç içe geçmiş bir typedef bildirimini iç içe geçmiş şekiller olarak gösterebilir

 TypeDef şekilleri bağlam menüsünde **Ilişkilendirmeyi göster** ve **koleksiyon ilişkilendirme olarak göster** komutlarını destekler.

 Aşağıda Sınıf Tasarımcısı tarafından desteklenen typdef türlerinin bazı örnekleri verilmiştir:

 `typedef type name`

 *ad* : *tür*

  typedef

 Mümkünse, tür *adına*bağlanan bir ilişkilendirme satırı çizer.

 `typedef void (*func)(int)`

 `func: void (*)(int)`

  typedef

 İşlev işaretçileri için typedef. Hiçbir ilişkilendirme çizgisi çizilmez.

 Sınıf Tasarımcısı, kaynak türü bir işlev işaretçisiyse bir typedef görüntülemez.

```
typedef int MyInt;
class A {
   MyInt I;
};
```

 `MyInt: int`

  typedef

 `A`

 Sınıf

 Kaynak türü şeklinden hedef tür şekline işaret eden bir ilişkilendirme çizgisi çizer.

 `Class B {};`

 `typedef B MyB;`

 `B`

 Sınıf

 `MyB : B`

  typedef

 Bir typedef şekline sağ tıklayıp, **Ilişkilendirmeyi göster** ' e tıkladığınızda typedef veya sınıf ve iki şekle katılan çizginin bir **diğer adı** (ilişki hattına benzer) görüntülenir.

 `typedef B MyB;`

 `typedef MyB A;`

 `MyBar : Bar`

  typedef

 Yukarıdaki gibi.

```
Class B {};
typedef B MyB;

class A {
   MyB B;
};
```

 `B`

 Sınıf

 `MyB : B`

  typedef

 `A`

 Sınıf

 `MyB` iç içe geçmiş bir typedef şekli.

 `#include <vector>`

 `...`

 `using namespace std;`

 `...`

 `typedef vector<int> MyIntVect;`

 `vector<T>`Sınıf

 `MyIntVect : vector<int>`

  typedef

 `class B {};`

 `typedef B MyB;`

 `class A : MyB {};`

 `MyB : B`

  typedef

 -> B

 `B`

 `A`

 Sınıf

 -> MyB

 Sınıf Tasarımcısı, bir bağlam menüsü komutu kullanarak bu tür bir ilişkinin görüntülenmesini desteklemez.

 `#include <vector>`

 `Typedef MyIntVect std::vector<int>;`

 `Class MyVect : MyIntVect {};`

 `std::vector<T>`

 Sınıf

 `MyIntVect : std::vector<int>`

  typedef

 `MyVect`

 Sınıf

 -> MyIntVect

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual C++ Code (sınıf Tasarımcısı)](../ide/working-with-visual-cpp-code-class-designer.md) [(NOTINBUILD) typedef belirticisi](https://msdn.microsoft.com/cc96cf26-ba93-4179-951e-695d1f5fdcf1) ile çalışma
