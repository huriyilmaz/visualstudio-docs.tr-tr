---
title: Projeleri ve Çözümleri Oluşturma ve Temizleme
description: Bu makalede, Mac için Visual Studio'de proje oluşturma açık Mac için Visual Studio
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/19/2019
ms.assetid: E4B6CB42-9FE2-43B9-93B7-BD4BD50518B1
ms.topic: how-to
ms.openlocfilehash: 89c09e685f3deab221265c312353133687026c1c69513cb1a547e7e18c3df74f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121381673"
---
# <a name="building-and-cleaning-projects-and-solutions"></a>Projeleri ve çözümleri bina ve temizleme

Bir çözümde tüm projelerinizi veya bazı projelerinizi derlemeyi, yeniden derlemeyi veya temizlemeyi öğrenmek için bu makaledeki adımları izleyin.

> [!NOTE]
> Bu konu, Mac için Visual Studio. Bir Visual Studio hakkında Windows için [bkz. Visual Studio'de proje ve çözüm oluşturma ve temizleme.](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Çözümün tamamını derlemek, yeniden derlemek veya temizlemek için

1. Çözüm Penceresinde Çözüm **düğümünü seçin:**

    ![Çözüm düğümünü seçme](media/compiling-and-building-image1.png)

2. Menü **Çubuğundan** Derleme menüsünü seçin ve aşağıdaki seçeneklerden birini belirleyin:

    ![Tüm derleme menü öğesini seçme](media/compiling-and-building-image2.png)

    * Proje **içindeki en son** derlemeden bu yana değişen dosyaları ve bileşenleri derlemek için Hepsini Derle'yi seçin.

    * Çözümü **"temizlemek",** sonra da tüm proje dosyalarını ve bileşenlerini derlemek için Hepsini Yeniden Oluştur'a seçin.

    * Ara **ve çıkış dosyalarını** silmek için Hepsini Temizle'yi seçin. Yalnızca proje ve bileşen dosyaları bırakıla birlikte, ara ve çıkış dosyalarının yeni örnekleri daha sonra inşa edilecektir.

## <a name="to-build-or-rebuild-a-single-project"></a>Tek bir projeyi derlemek veya yeniden derlemek için

1. Çözüm Penceresinde **projeyi seçin.**

2. Menü **Çubuğundan** Derleme menüsünü seçin.

3. Build[ProjectName], Rebuild[ProjectName] veya Clean[ProjectName] seçin.

## <a name="to-stop-a-build"></a>Derlemeyi durdurmak için

Derlemeyi durdurmak için aşağıdaki seçeneklerden birini kullanın:

* Durum alanında kırmızı kareye basın:

    ![Derlemeyi durdurmak için kırmızı kareye basın](media/compiling-and-building-image3.png)

* Derleme **menüsündeki** Durdur **öğesini** kullanın.

* **Cmd+Shift+Return tuşlarına basın.**

## <a name="see-also"></a>Ayrıca bkz.

- [Projeleri ve çözümleri oluşturma ve temizleme (Visual Studio üzerinde Windows)](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)