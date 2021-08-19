---
title: 'Nasıl Yapılır: Arabirimi Uygulama (Sınıf Tasarımcısı)'
description: Arabirim diyagramlarında arabirimi arabirim yöntemleri için kod sağlayan bir sınıfa bağlayarak nasıl uygulayabilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: a992800a6155aaa8afdd9ae2491b977885199ddd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122124197"
---
# <a name="how-to-implement-an-interface-in-class-designer"></a>Nasıl kullanılır: Sınıf Tasarımcısı'da arabirim uygulama

Bu **Sınıf Tasarımcısı,** arabirim yöntemleri için kod sağlayan bir sınıfa bağlayarak sınıf diyagramında bir arabirim gerçekleştirebilirsiniz. **Sınıf Tasarımcısı** bir arabirim uygulaması üretir ve arabirim ile sınıf arasındaki ilişkiyi devralma ilişkisi olarak görüntüler. Arabirim ile sınıfı arasında bir devralma çizgisi çizerek veya arabirimi bir devralma çizgisinden sürükleyerek bir arabirim Sınıf Görünümü.

> [!TIP]
> Arabirimleri, diğer türleri oluşturarak aynı şekilde oluşturabilirsiniz. Arabirim mevcutsa ancak sınıf diyagramında görünmüyorsa, önce bunu görüntüler. Daha fazla bilgi için [bkz. Nasıl 2.](how-to-create-types.md) Sınıf Tasarımcısı: Var olan [türleri görüntüleme.](how-to-view-existing-types.md)

## <a name="to-implement-an-interface-by-drawing-an-inheritance-line"></a>Devralma çizgisi çizerek bir arabirim uygulamak için

1. Sınıf diyagramında arabirimini ve arabirimi uygulayacak sınıfı görüntüler.

2. sınıfından ve arabiriminden bir devralma çizgisi çizin.

     Sınıfa eklenmiş bir lollipop görünür ve arabirim adına sahip bir etiket devralma ilişkisini tanımlar. Visual Studio tüm arabirim üyeleri için saplamalar üretir.

Daha fazla bilgi için, [bkz. How to: Create inheritance between types](how-to-create-inheritance-between-types.md).

## <a name="to-implement-an-interface-from-the-class-view-window"></a>Sınıf Görünümü penceresinden bir arabirim uygulamak için

1. Sınıf diyagramında, arabirimini uygulamak istediğiniz sınıfı görüntüler.

2. Sınıf Görünümü  açın ve arabirimini bulun.

    > [!TIP]
    > Açık **Sınıf Görünümü,** Görünüm menüsünden **Sınıf Görünümü'yi** açın  veya **Ctrl Shift** C + **tuşlarına** + **basın.**

3. Arabirim düğümünü diyagramda sınıf şekline sürükleyin.

     Sınıfa eklenmiş bir lollipop görünür ve arabirim adına sahip bir etiket devralma ilişkisini tanımlar. Visual Studio tüm arabirim üyeleri için saplamalar üretir; Bu noktada, arabirimi uygulanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır: Sınıf Tasarımcısı Kullanarak Tür Oluşturma](how-to-create-types.md)
- [Nasıl: Mevcut Türleri Görüntüleme](how-to-view-existing-types.md)
- [Nasıl: Türler Arasında Devralma Oluşturma](how-to-create-inheritance-between-types.md)
- [Sınıfları ve Türleri Yeniden Düzenleme](refactoring-classes-and-types.md)
