---
title: Projeleri ve Çözümleri Oluşturma ve Temizleme
description: bu makalede Mac için Visual Studio içinde bir projenin nasıl oluşturulacağı açıklanır
author: jmatthiesen
ms.author: jomatthi
manager: dominicn
ms.date: 09/19/2019
ms.assetid: E4B6CB42-9FE2-43B9-93B7-BD4BD50518B1
ms.topic: how-to
ms.openlocfilehash: fdc6a3ac2474bec07185423e1e1d6d17466c867d
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135803225"
---
# <a name="building-and-cleaning-projects-and-solutions"></a>Projeleri ve çözümleri oluşturma ve Temizleme

Bir çözümdeki projelerin tümünü veya bir kısmını oluşturma, yeniden oluşturma veya temizleme hakkında bilgi edinmek için bu makaledeki adımları izleyin.

> [!NOTE]
> bu konu Mac için Visual Studio için geçerlidir. Windows Visual Studio için bkz. [Visual Studio 'da projeler ve çözümler oluşturma ve temizleme](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio).

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Tüm çözümü derlemek, yeniden derlemek veya temizlemek için

1. **Çözüm penceresinde** çözüm düğümünü seçin:

    ![Çözüm düğümünü seçme](media/compiling-and-building-image1.png)

2. Menü çubuğunda **Yapı** menüsünü seçin ve aşağıdaki seçeneklerden birini belirleyin:

    ![Tümünü Oluştur menü öğesi seçiliyor](media/compiling-and-building-image2.png)

    * En son derlemeden bu yana değiştirilen proje içindeki dosya ve bileşenleri derlemek için **Tümünü derle** ' yi seçin.

    * Çözümü "temizlemek" için **tümünü yeniden derle** ' yi seçin ve ardından tüm proje dosyalarını ve bileşenlerini derleyin.

    * Tüm ara ve çıkış dosyalarını silmek için **Tümünü Temizle** ' yi seçin. Yalnızca proje ve bileşen dosyaları solda, ara ve çıkış dosyalarının yeni örnekleri derlenebilir.

## <a name="to-build-or-rebuild-a-single-project"></a>Tek bir projeyi derlemek veya yeniden derlemek için

1. **Çözüm penceresinde** projeyi seçin.

2. Menü çubuğundan **Yapı** menüsünü seçin.

3. Build [ProjectName], Rebuild [ProjectName] veya Clean [ProjectName] öğesini seçin.

## <a name="to-stop-a-build"></a>Bir derlemeyi durdurmak için

Bir derlemeyi durdurmak için, aşağıdaki seçeneklerden birini kullanın:

* Durum alanında kırmızı kareye basın:

    ![Derlemeyi durdurmak için kırmızı kare tuşuna basın](media/compiling-and-building-image3.png)

* **Derleme** menüsündeki **Durdur** öğesini kullanın.

* **Cmd + SHIFT + Return** tuşlarına basın.

## <a name="see-also"></a>Ayrıca bkz.

- [projeleri ve çözümleri oluşturma ve temizleme (Windows Visual Studio)](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)