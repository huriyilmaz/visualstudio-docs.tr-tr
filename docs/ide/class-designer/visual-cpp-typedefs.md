---
title: Sınıf Tasarımcısıc++ Typedefs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.typedef
- vs.classdesigner.aliasofline
helpviewer_keywords:
- Class Designer [Visual Studio], typedefs
ms.assetid: c1984108-71fc-4d3a-b4d4-3eac2c6b4ebf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 4c57382809b7730df2d7c674c24902d70ccab647
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590702"
---
# <a name="c-typedefs-in-class-designer"></a>Sınıf Tasarımcısı'nda C++ typedefs

[Typedef](/cpp/cpp/aliases-and-typedefs-cpp#typedefs) deyimleri, bir ad ve altta yatan türü arasında bir veya daha fazla yön katmanı oluşturur. **Sınıf Tasarımcısı,** örneğin anahtar kelimeyle `typedef`birlikte bildirilen C++ typedef türlerini destekler:

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
} COORD;
```

Daha sonra bir örneği bildirmek için bu türü kullanabilirsiniz:

`COORD OriginPoint;`

## <a name="class-and-struct-shapes"></a>Sınıf ve yapı şekilleri

**Sınıf Tasarımcısı'nda**C++ typedef typedef'te belirtilen tür şekline sahiptir. Kaynak bildirirse, `typedef class`şekil yuvarlak köşeleri ve etiket **Sınıf**vardır. Için, `typedef struct`şekil kare köşeleri ve etiket **Struct**vardır.

Sınıflar ve yapılar iç içe yazı disinlari içlerinde bildirilmiş olabilir. **Sınıf Tasarımcısı,** sınıf ve yapı şekilleri iç içe bağlı şekiller olarak iç içe yazı bildirgelerini gösterebilir.

Typedef şekilleri sağ tıklama menüsünde (bağlam menüsünde) **İlişki olarak Göster** ve Koleksiyon Birliği komutları olarak **göster'i** destekler.

### <a name="class-typedef-example"></a>Sınıf typedef örneği

```cpp
class B {};
typedef B MyB;
```

![Sınıf Tasarımcısı'nda C++ sınıfı typedef](media/cpp-class-typedef.png)

### <a name="struct-typedef-example"></a>Struct typedef örneği

```cpp
typedef struct mystructtag
{
    int   i;
    double f;
} mystruct;
```

![Sınıf Tasarımcısı'nda C++ yapı tipi](media/cpp-struct-typedef.png)

## <a name="unnamed-typedefs"></a>İsimsiz typedefs

Adsız bir typedef bildirebilirsiniz, ancak **Sınıf Tasarımcısı** belirttiğiniz etiket adını kullanmaz. **Sınıf Tasarımcısı,** **Sınıf Görünümü'nün** oluşturduğu adı kullanır. Örneğin, aşağıdaki bildirim geçerlidir, ancak **Sınıf Görünümü** ve Sınıf **Tasarımcısı'nda __unnamed**adlı bir nesne olarak görünür: **Class Designer**

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
};
```

> [!NOTE]
> **Sınıf Tasarımcısı,** kaynak türü işlev işaretçisi olan typedefs'i görüntülemez.

## <a name="see-also"></a>Ayrıca bkz.

- [C++ Kodu ile Çalışma](working-with-visual-cpp-code.md)
- [Typedef](/cpp/cpp/aliases-and-typedefs-cpp#typedefs)
