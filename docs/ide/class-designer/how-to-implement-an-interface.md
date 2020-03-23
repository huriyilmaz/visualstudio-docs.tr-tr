---
title: 'Nasıl Yapılır: Arabirimi Uygulama (Sınıf Tasarımcısı)'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fbe8db6c6bd7df5285880f7f860df5bb26db736a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590117"
---
# <a name="how-to-implement-an-interface-in-class-designer"></a>Nasıl yapılır: Sınıf Tasarımcısı'nda arabirim uygulama

**Sınıf**Tasarımcısı'nda, arabirim yöntemleri için kod sağlayan bir sınıfa bağlayarak sınıf diyagramında bir arabirim uygulayabilirsiniz. **Sınıf Tasarımcısı** bir arabirim uygulaması oluşturur ve bir devralma ilişkisi olarak arabirim ve sınıf arasındaki ilişkiyi görüntüler. Arabirim ve sınıf arasında bir devralma çizgisi çizerek veya arabirimi Sınıf Görünümü'nden sürükleyerek bir arabirim uygulayabilirsiniz.

> [!TIP]
> Diğer türleri oluşturduğunuz gibi arabirimler oluşturabilirsiniz. Arabirim varsa ancak sınıf diyagramında görünmüyorsa, önce görüntüleyin. Daha fazla bilgi için [bkz: Sınıf Tasarımcısı'nı kullanarak türleri oluşturma](how-to-create-types.md) ve [nasıl oluşturulacak: Varolan türleri görüntüleyin.](how-to-view-existing-types.md)

## <a name="to-implement-an-interface-by-drawing-an-inheritance-line"></a>Bir devralma çizgisi çizerek arabirim uygulamak için

1. Sınıf diyagramında arabirimi ve arabirimi uygulayacak sınıfı görüntüleyin.

2. Sınıftan ve arabirimden bir devralma satırı çizin.

     Sınıfa bağlı bir lolipop görünür ve arabirim adı olan bir etiket devralma ilişkisini tanımlar. Visual Studio tüm arayüz üyeleri için saplamalar oluşturur.

Daha fazla bilgi için [bkz: Türler arasında devralma oluşturma](how-to-create-inheritance-between-types.md).

## <a name="to-implement-an-interface-from-the-class-view-window"></a>Sınıf Görünümü penceresinden bir arabirim uygulamak için

1. Sınıf diyagramında, arabirimi uygulamak istediğiniz sınıfı görüntüleyin.

2. **Sınıf Görünümü'ni** açın ve arabirimi bulun.

    > [!TIP]
    > **Sınıf Görünümü** açık değilse, **Görünüm** menüsünden **Sınıf Görünümü'nü** açın veya **Ctrl**+**Shift**+**C**tuşuna basın.

3. Arabirim düğümlerini diyagramdaki sınıf şekline sürükleyin.

     Sınıfa bağlı bir lolipop görünür ve arabirim adı olan bir etiket devralma ilişkisini tanımlar. Visual Studio tüm arayüz üyeleri için saplamalar oluşturur; bu noktada, arabirim uygulanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır: Sınıf Tasarımcısı Kullanarak Tür Oluşturma](how-to-create-types.md)
- [Nasıl yapılı: Varolan Türleri Görüntüleme](how-to-view-existing-types.md)
- [Nasıl yapılacağını: Türler Arasında Devralma Oluşturma](how-to-create-inheritance-between-types.md)
- [Sınıfları ve Türleri Yeniden Düzenleme](refactoring-classes-and-types.md)
