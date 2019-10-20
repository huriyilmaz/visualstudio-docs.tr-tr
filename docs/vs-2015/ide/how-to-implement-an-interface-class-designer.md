---
title: 'Nasıl yapılır: arabirim uygulama (Sınıf Tasarımcısı) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6b750830e8263d0016f52a71ad4eac8c6950eda8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651860"
---
# <a name="how-to-implement-an-interface-class-designer"></a>Nasıl Yapılır: Arabirimi Uygulama (Sınıf Tasarımcısı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sınıf Tasarımcısı ' de, arabirim yöntemleri için kod sağlayan bir sınıfa bağlayarak sınıf diyagramında bir arabirim uygulayabilirsiniz. Sınıf Tasarımcısı bir arabirim uygulaması oluşturur ve arabirim ile sınıf arasındaki ilişkiyi devralma ilişkisi olarak görüntüler. Arabirim ve sınıf arasında bir devralma çizgisi çizerek veya arabirimi Sınıf Görünümü sürükleyerek bir arabirim uygulayabilirsiniz.

> [!TIP]
> Arabirimleri, diğer türleri oluşturduğunuz şekilde oluşturabilirsiniz. Arabirim varsa, ancak sınıf diyagramında görünmezse, önce onu görüntüleyin. Daha fazla bilgi için bkz. [nasıl yapılır: Sınıf Tasarımcısı kullanarak tür oluşturma](../ide/how-to-create-types-by-using-class-designer.md) ve [nasıl yapılır: varolan türleri görüntüleme (sınıf Tasarımcısı)](../ide/how-to-view-existing-types-class-designer.md).

### <a name="to-implement-an-interface-by-drawing-an-inheritance-line"></a>Bir devralma çizgisi çizerek bir arabirim uygulamak için

1. Sınıf diyagramında arabirimini ve arabirimini uygulayacak sınıfı görüntüleyin.

2. Sınıfından ve arabiriminden devralma çizgisi çizin.

    Sınıfa iliştirilmiş bir Lollipop görünür ve arabirim adı olan bir etiket devralma ilişkisini tanımlar. Visual Studio tüm arabirim üyeleri için saplamalar oluşturur.

   Daha fazla bilgi için bkz. [nasıl yapılır: türler arasında devralma oluşturma (sınıf Tasarımcısı)](../ide/how-to-create-inheritance-between-types-class-designer.md).

### <a name="to-implement-an-interface-from-the-class-view-window"></a>Sınıf Görünümü penceresinden bir arabirim uygulamak için

1. Sınıf diyagramında, arabirimi uygulamak istediğiniz sınıfı görüntüleyin.

2. Sınıf Görünümü açın ve arabirimini bulun.

    > [!TIP]
    > Sınıf Görünümü açık değilse, **Görünüm** menüsünden sınıf görünümü açın. Sınıf Görünümü hakkında daha fazla bilgi için bkz. [sınıfları ve üyelerini görüntüleme](https://msdn.microsoft.com/71e9e8f3-261a-4e0c-87bf-5ec48b8bf333).

3. Arabirim düğümünü diyagramdaki sınıf şekline sürükleyin.

     Sınıfa iliştirilmiş bir Lollipop görünür ve arabirim adı olan bir etiket devralma ilişkisini tanımlar. Visual Studio tüm arabirim üyeleri için saplamalar oluşturur; Bu noktada, arabirim uygulanır.

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır: Sınıf Tasarımcısı kullanarak tür oluşturma](../ide/how-to-create-types-by-using-class-designer.md) [: nasıl yapılır: varolan türleri görüntüleme (sınıf Tasarımcısı)](../ide/how-to-view-existing-types-class-designer.md) [nasıl yapılır: türler arasında devralma oluşturma (sınıf Tasarımcısı)](../ide/how-to-create-inheritance-between-types-class-designer.md) [yeniden düzenleme sınıfları ve türleri (sınıf Tasarımcısı)](../ide/refactoring-classes-and-types-class-designer.md)
