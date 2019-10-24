---
title: C++Sınıf Tasarımcısı 'de Typedefs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.typedef
- vs.classdesigner.aliasofline
helpviewer_keywords:
- Class Designer [Visual Studio], typedefs
ms.assetid: c1984108-71fc-4d3a-b4d4-3eac2c6b4ebf
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 94dc4a6687a2aaede7fc901884c5d3acc6fbf56f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748003"
---
# <a name="c-typedefs-in-class-designer"></a>C++Sınıf Tasarımcısı 'de tür tanımları

[Typedef](/cpp/cpp/aliases-and-typedefs-cpp#typedefs) deyimleri, bir ad ve temel alınan türü arasında bir veya daha fazla yöneltme katmanı oluşturur. **Sınıf Tasarımcısı** , C++ anahtar sözcüğü `typedef` ile belirtilen typedef türlerini destekler, örneğin:

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
} COORD;
```

Daha sonra bu türü bir örnek bildirmek için kullanabilirsiniz:

`COORD OriginPoint;`

## <a name="class-and-struct-shapes"></a>Sınıf ve yapı şekilleri

**Sınıf Tasarımcısı**, bir typedef C++ , typedef içinde belirtilen türde bir şekle sahiptir. Kaynak `typedef class` bildiriyorsa, şekil yuvarlak köşeler ve Label **sınıfına**sahiptir. @No__t_0 için, şekil kare köşeleri ve Label **yapısına**sahiptir.

Sınıfların ve yapıların içinde bildirildiği iç içe tür tanımları olabilir. **Sınıf Tasarımcısı**, sınıf ve yapı şekilleri iç içe geçmiş bir typedef bildirimini iç içe geçmiş şekiller olarak gösterebilir.

TypeDef şekilleri, sağ tıklama menüsünde (bağlam menüsü) **ilişki olarak göster** ve **koleksiyon ilişkilendirme olarak göster** komutlarını destekler.

### <a name="class-typedef-example"></a>Sınıf typedef örneği

```cpp
class B {};
typedef B MyB;
```

![C++Sınıf Tasarımcısı sınıf typedef](media/cpp-class-typedef.png)

### <a name="struct-typedef-example"></a>Struct typedef örneği

```cpp
typedef struct mystructtag
{
    int   i;
    double f;
} mystruct;
```

![C++Sınıf Tasarımcısı içinde struct typedef](media/cpp-struct-typedef.png)

## <a name="unnamed-typedefs"></a>Adlandırılmamış tür tanımları

Bir typedef adı olmadan bildirebilseniz de **Sınıf Tasarımcısı** belirttiğiniz etiket adını kullanmaz. **Sınıf Tasarımcısı** , **sınıf görünümü** oluşturduğu adı kullanır. Örneğin, aşağıdaki bildirim geçerlidir, ancak **sınıf görünümü** ve **__adlandırılmamış**adlı bir nesne olarak **Sınıf Tasarımcısı** görünür:

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
};
```

> [!NOTE]
> **Sınıf Tasarımcısı** , kaynak türü bir işlev işaretçisi olan tür tanımları öğesini görüntülemez.

## <a name="see-also"></a>Ayrıca bkz.

- [C++ Kodla çalışma](working-with-visual-cpp-code.md)
- [Tür tanımları](/cpp/cpp/aliases-and-typedefs-cpp#typedefs)