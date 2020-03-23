---
title: 'Nasıl Yapılır: Türler Arasında Devralma Oluşturma (Sınıf Tasarımcısı)'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritanceline
helpviewer_keywords:
- inheritance, relationship defining
- relationships, defining inheritance
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fbf540056318e092db13521dc80478cc7eb91948
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590377"
---
# <a name="how-to-create-inheritance-between-types-in-class-designer"></a>Nasıl? Sınıf Tasarımcısı'ndaki türler arasında kalıtım oluşturma

**Sınıf Tasarımcısı'nı**kullanarak sınıf diyagramındaki iki tür arasında devralma ilişkisi oluşturmak için, taban türünü türetilmiş türüveya türleri ile bağlayın. İki sınıf arasında, bir sınıf ve arabirim arasında veya iki arabirim arasında bir devralma ilişkisi olabilir.

## <a name="to-create-an-inheritance-between-types"></a>Türler arasında devralma oluşturmak için

1. **Solution Explorer'daki**projenizden bir sınıf diyagramı (.cd) dosyası açın.

     Sınıf diyagramın yoksa, oluşturun. [Bkz. Nasıl: Projelere Sınıf Diyagramları Ekleyin.](how-to-add-class-diagrams-to-projects.md)

2. Araç **Kutusunda**, **Sınıf Tasarımcısı**altında, **Kalıtım'ı**tıklatın.

3. Sınıf diyagramında, aşağıdakilerden başlayarak istediğiniz türler arasında bir devralma satırı çizin:

    - Taban sınıfa türetilmiş sınıf

    - Uygulanan arabirime uygulama sınıfı

    - Genişletilmiş arabirime uzanan bir arayüz

4. İsteğe bağlı olarak, genel bir türden türetilmiş bir tür varsa, devralma satırını tıklatın. **Özellikler** penceresinde, Genel tür için istediğiniz türle eşleşecek şekilde **Tür BağımsızLar** özelliğini ayarlayın.

    > [!NOTE]
    > Bir üst soyut sınıf en az bir özet üye içeriyorsa, tüm soyut üyeler soyut olmayan devralma sınıfları olarak uygulanır.
    >
    >  Varolan genel türleri görselleştirebiliyor olsanız da, yeni genel türler oluşturamazsınız. Ayrıca, varolan genel türlerin tür parametrelerini değiştiremezsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Devralma](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)
- [Devralma Temelleri](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [Nasıl yapılı: Türler Arasında Devralma Yı Görüntüle](how-to-view-inheritance-between-types.md)
- [Sınıf Tasarımcısında Visual C++ Sınıfları](visual-cpp-classes.md)
