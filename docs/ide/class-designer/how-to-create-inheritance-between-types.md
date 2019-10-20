---
title: 'Nasıl yapılır: türler arasında devralma oluşturma (Sınıf Tasarımcısı)'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritanceline
helpviewer_keywords:
- inheritance, relationship defining
- relationships, defining inheritance
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8a7d7f3facf1408f87ef23dfa8ed8462195c172
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647724"
---
# <a name="how-to-create-inheritance-between-types-in-class-designer"></a>Nasıl yapılır: Sınıf Tasarımcısı türler arasında devralma oluşturma

**Sınıf Tasarımcısı**kullanarak bir sınıf diyagramında iki tür arasında bir devralma ilişkisi oluşturmak için, temel türü türetilen tür veya türleriyle bağlayın. İki sınıf arasında, bir sınıf ile arabirim arasında veya iki arabirim arasında bir devralma ilişkisine sahip olabilirsiniz.

## <a name="to-create-an-inheritance-between-types"></a>Türler arasında devralma oluşturmak için

1. **Çözüm Gezgini**' de projenizden bir sınıf diyagramı (. CD) dosyası açın.

     Bir sınıf diyagramınız yoksa, oluşturun. Bkz. [nasıl yapılır: projelere sınıf diyagramları ekleme](how-to-add-class-diagrams-to-projects.md).

2. **Araç kutusunda**, **Sınıf Tasarımcısı**altında **Devralma**' ı tıklatın.

3. Sınıf diyagramında, buradan başlayarak istediğiniz türler arasında bir devralma çizgisi çizin:

    - Taban sınıfına türetilmiş bir sınıf

    - Uygulanan arabirim için uygulama sınıfı

    - Genişletilmiş arabirime yönelik genişletme arabirimi

4. İsteğe bağlı olarak, genel bir türden türetilmiş bir türse, devralma satırına tıklayın. **Özellikler** penceresinde, **tür bağımsız değişkenleri** özelliğini genel tür için istediğiniz türle eşleşecek şekilde ayarlayın.

    > [!NOTE]
    > Bir üst soyut sınıf en az bir soyut üye içeriyorsa, tüm soyut Üyeler soyut olmayan devralma sınıfları olarak uygulanır.
    >
    >  Mevcut genel türleri görselleştirebilseniz de, yeni genel türler oluşturamazsınız. Ayrıca, varolan genel türler için tür parametrelerini değiştiremezsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Devralma](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)
- [Devralma Temelleri](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [Nasıl yapılır: türler arasında devralmayı görüntüleme](how-to-view-inheritance-between-types.md)
- [Sınıf Tasarımcısında Visual C++ Sınıfları](visual-cpp-classes.md)