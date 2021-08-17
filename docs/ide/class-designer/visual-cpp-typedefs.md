---
title: Sınıf Tasarımcısı'de C++ Typedefs
description: Anahtar sözcük türü Sınıf Tasarımcısı C++ typedef türlerini nasıl desteklediğini öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- cplusplus
ms.openlocfilehash: 9e00588b8ba0367be6f28873ec0f8940f92f04a9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122078407"
---
# <a name="c-typedefs-in-class-designer"></a>Sınıf Tasarımcısı'de C++ tür tanımları

[Typedef](/cpp/cpp/aliases-and-typedefs-cpp#typedefs) deyimleri, bir ad ile temel alınan türü arasında bir veya daha fazla dolaylı katman oluşturun. **Sınıf Tasarımcısı,** anahtar sözcüğüyle bildirilen C++ typedef türlerini `typedef` destekler, örneğin:

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
} COORD;
```

Daha sonra bu türü kullanarak bir örnek bildiresiniz:

`COORD OriginPoint;`

## <a name="class-and-struct-shapes"></a>Sınıf ve yapı şekilleri

Bu **Sınıf Tasarımcısı** C++ typedef, typedef içinde belirtilen tür şekline sahip olur. Kaynak `typedef class` bildirse, şeklin köşeleri yuvarlanmış ve Class etiketi **vardır.** için, `typedef struct` şeklin köşeleri ve Yapı etiketi **vardır.**

Sınıfların ve yapıların içinde bildirilen iç içe geçmiş tür tanımları olabilir. Bu **Sınıf Tasarımcısı** sınıf ve yapı şekilleri iç içe geçmiş typedef bildirimlerini iç içe şekiller olarak gösterebilir.

Typedef şekilleri, **sağ tıklama menüsündeki** **(bağlam menüsü)** İlişki olarak Göster ve Koleksiyon İlişkisi Olarak Göster komutlarını destekler.

### <a name="class-typedef-example"></a>Sınıf typedef örneği

```cpp
class B {};
typedef B MyB;
```

![Sınıf Tasarımcısı'de C++ sınıf türü Sınıf Tasarımcısı](media/cpp-class-typedef.png)

### <a name="struct-typedef-example"></a>Yapı typedef örneği

```cpp
typedef struct mystructtag
{
    int   i;
    double f;
} mystruct;
```

![Sınıf Tasarımcısı'da C++ yapı tür Sınıf Tasarımcısı](media/cpp-struct-typedef.png)

## <a name="unnamed-typedefs"></a>Adlandırlanmamış tür tanımları

Name olmadan typedef bildirebilirsiniz ancak **Sınıf Tasarımcısı** belirttiğiniz etiket adını kullanmaz. **Sınıf Tasarımcısı,** oluşturulan **Sınıf Görünümü** kullanır. Örneğin, aşağıdaki bildirim geçerlidir, ancak Sınıf Görünümü **ve Sınıf Tasarımcısı** adlı **bir** nesne **olarak** __unnamed:

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
};
```

> [!NOTE]
> **Sınıf Tasarımcısı,** kaynak türü işlev işaretçisi olan typedef'leri görüntülemez.

## <a name="see-also"></a>Ayrıca bkz.

- [C++ Koduyla Çalışma](working-with-visual-cpp-code.md)
- [Typedef](/cpp/cpp/aliases-and-typedefs-cpp#typedefs)
