---
title: 'Nasıl Yapılır: Arabirimi Uygulama (Sınıf Tasarımcısı)'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf03046abcf79933044cfb01bf079aee64d09077
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647711"
---
# <a name="how-to-implement-an-interface-in-class-designer"></a>Nasıl yapılır: Sınıf Tasarımcısı bir arabirimi uygulama

**Sınıf Tasarımcısı**' de, arabirim yöntemleri için kod sağlayan bir sınıfa bağlayarak sınıf diyagramında bir arabirim uygulayabilirsiniz. **Sınıf Tasarımcısı** bir arabirim uygulaması oluşturur ve arabirim ile sınıf arasındaki ilişkiyi devralma ilişkisi olarak görüntüler. Arabirim ve sınıf arasında bir devralma çizgisi çizerek veya arabirimi Sınıf Görünümü sürükleyerek bir arabirim uygulayabilirsiniz.

> [!TIP]
> Arabirimleri, diğer türleri oluşturduğunuz şekilde oluşturabilirsiniz. Arabirim varsa, ancak sınıf diyagramında görünmezse, önce onu görüntüleyin. Daha fazla bilgi için bkz. [nasıl yapılır: Sınıf Tasarımcısı kullanarak tür oluşturma](how-to-create-types.md) ve [nasıl yapılır: varolan türleri görüntüleme](how-to-view-existing-types.md).

## <a name="to-implement-an-interface-by-drawing-an-inheritance-line"></a>Bir devralma çizgisi çizerek bir arabirim uygulamak için

1. Sınıf diyagramında arabirimini ve arabirimini uygulayacak sınıfı görüntüleyin.

2. Sınıfından ve arabiriminden devralma çizgisi çizin.

     Sınıfa iliştirilmiş bir Lollipop görünür ve arabirim adı olan bir etiket devralma ilişkisini tanımlar. Visual Studio tüm arabirim üyeleri için saplamalar oluşturur.

Daha fazla bilgi için bkz. [nasıl yapılır: türler arasında devralma oluşturma](how-to-create-inheritance-between-types.md).

## <a name="to-implement-an-interface-from-the-class-view-window"></a>Sınıf Görünümü penceresinden bir arabirim uygulamak için

1. Sınıf diyagramında, arabirimi uygulamak istediğiniz sınıfı görüntüleyin.

2. **Sınıf görünümü** açın ve arabirimini bulun.

    > [!TIP]
    > **Sınıf görünümü** açık değilse, **Görünüm** menüsünden **sınıf görünümü** açın veya **CTRL** +**SHIFT** +**C**tuşlarına basın.

3. Arabirim düğümünü diyagramdaki sınıf şekline sürükleyin.

     Sınıfa iliştirilmiş bir Lollipop görünür ve arabirim adı olan bir etiket devralma ilişkisini tanımlar. Visual Studio tüm arabirim üyeleri için saplamalar oluşturur; Bu noktada, arabirim uygulanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır: Sınıf Tasarımcısı Kullanarak Tür Oluşturma](how-to-create-types.md)
- [Nasıl yapılır: varolan türleri görüntüleme](how-to-view-existing-types.md)
- [Nasıl yapılır: türler arasında devralma oluşturma](how-to-create-inheritance-between-types.md)
- [Sınıfları ve Türleri Yeniden Düzenleme](refactoring-classes-and-types.md)