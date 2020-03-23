---
title: Projeleri ve Çözümleri Oluşturma ve Temizleme
description: Bu makalede, Mac için Visual Studio'da bir proje nasıl inşa edilen açıklanmaktadır
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/19/2019
ms.assetid: E4B6CB42-9FE2-43B9-93B7-BD4BD50518B1
ms.openlocfilehash: 924bdb08154ecb3caad04cabf7e860bed9204e98
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "71128450"
---
# <a name="building-and-cleaning-projects-and-solutions"></a>Bina ve temizlik projeleri ve çözümleri

Bir çözümdeki projelerin tamamını veya bazılarını nasıl oluşturunuzu, yeniden oluşturunuzu veya temizleyeceklerinizi öğrenmek için bu makaledeki adımları izleyin.

> [!NOTE]
> Bu konu Mac için Visual Studio için geçerlidir. Windows'daki Visual Studio için [Visual Studio'da Yapı ve temiz projeler ve çözümler](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)bkz.

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Tüm çözümü oluşturmak, yeniden oluşturmak veya temizlemek için

1. **Çözüm Defteri'ndeki**Çözüm düğümünü seçin:

    ![Çözüm düğümünü seçme](media/compiling-and-building-image1.png)

2. Menü Çubuğu'ndaki **Ekle** menüsünü seçin ve aşağıdaki seçeneklerden birini seçin:

    ![tüm menü öğesini oluşturmayı seçme](media/compiling-and-building-image2.png)

    * En son yapılana göre değişen projedeki dosyaları ve bileşenleri derlemek için **Tümlerini Oluştur'u** seçin.

    * Çözümü "temizlemek" için **Tümlerini Yeniden Oluştur'u** seçin ve ardından tüm proje dosyalarını ve bileşenlerini oluşturun.

    * Ara ve çıktı dosyalarını silmek için **Tümünü Temizle'yi** seçin. Yalnızca proje ve bileşen dosyaları bırakıldığında, ara ve çıktı dosyalarının yeni örnekleri oluşturulabilir.

## <a name="to-build-or-rebuild-a-single-project"></a>Tek bir proje oluşturmak veya yeniden oluşturmak için

1. **Çözüm Defteri'ndeki**projeyi seçin.

2. Menü Çubuğu'ndan **Oluştur** menüsünü seçin.

3. Yapı[ProjectName], Rebuild[ProjectName]veya Temiz[ProjectName] seçeneğini belirleyin.

## <a name="to-stop-a-build"></a>Bir yapıyı durdurmak için

Bir yapıyı durdurmak için aşağıdaki seçeneklerden birini kullanın:

* Durum alanındaki kırmızı meydana basın:

    ![Yapıyı durdurmak için kırmızı meydana basın](media/compiling-and-building-image3.png)

* **Yapı** menüsünde **Durdur** öğesini kullanın.

* **Cmd+Shift+Return**tuşuna basın.

## <a name="see-also"></a>Ayrıca bkz.

- [Projeler ve çözümler oluşturun ve temizleyin (Windows'ta Visual Studio)](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)