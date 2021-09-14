---
title: Visual Studio’yu onarın
titleSuffix: ''
description: Visual Studio 2017 yüklemesini onarmayı öğrenin
ms.date: 10/12/2020
ms.custom: vs-acquisition
ms.topic: how-to
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 98a7448bc3e257bb8a6f8047bf0e4a878aa41307
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635918"
---
# <a name="repair-visual-studio"></a>Visual Studio’yu onarın

Bazen Visual Studio veya bozuk hale gelir. Onarım, güncelleştirmeler de dahil olmak üzere tüm yükleme işlemleri boyunca yükleme zamanı sorunlarını düzeltmek için kullanışlıdır.

## <a name="when-to-use-repair"></a>Onarım ne zaman kullanımlı?
* Yükleme yüküyle ilgili sorunları varsa. Dosyayı diske yazma işlemi başarılı olmaz ve bozuk dosya silinerek düzeltilenemese de bu durum oluşabilir. Onarım, gerekli dosyaları yeniden edinebilirsiniz. 
* İstemci tarafı indirme sorunlarıyla karşıdan yüklensin. Tüm bağlantı veya ara sunucu sorunlarını çözmüş olduğunu varsayarak onarım yardımcı olabilir. 
* Uygulama güncelleştirme sorunlarıyla Visual Studio. Onarım birçok yaygın güncelleştirme sorununa çözüm sağlar. 

> [!TIP] 
> Yükleme sorunu, Windows Yükleyicisi gibi temel Windows hizmette yer alan bir sorundan kaynaksa, onarım aynı soruna neden olabilir. Sistemik sorunlar, bozuk bir Windows Yükleyicisi veya kararsız İnternet bağlantısı içerebilir. Sistemik bir sorunu kontrol etmek için yükleme işlemiyle oluşturulan hata raporunu kullanın.

> [!NOTE] 
> Bu Visual Studio, kullanıcı ayarlarını sıfırlar ve zaten sahip olduğunuz derlemeleri yeniden yüklenir. Bir ürün sorunu yaşıyorsanız, onarım sorunu [çöze Visual Studio](https://aka.ms/feedback/suggest?space=8)için bir Geri Bildirim Bileti oluşturun.

## <a name="how-to-repair"></a>Onarım
::: moniker range="vs-2017"

1. Bilgisayarınızda **Visual Studio Yükleyicisi'ı** bulun.

     Örneğin, Yıldönümü Güncelleştirmesi veya Windows 10 çalıştıran bir bilgisayarda Başlat'ı seçin ve ardından V harfine kaydırın ve burada dosya adı **olarak Visual Studio Yükleyicisi.**

   > [!NOTE]
   > Bazı bilgisayarlarda, Visual Studio Yükleyicisi yükleyicisi olarak **"M"** harfi altında **Microsoft Visual Studio olabilir.**
   >
   > Alternatif olarak, Visual Studio Yükleyicisi aşağıdaki konumda bulabilirsiniz:`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Yükleyiciyi açın, **Diğer'i ve** ardından Onar'ı **seçin.**

    ![Çalışma Visual Studio onarım Visual Studio Yükleyicisi](media/repair-visual-studio.png "Çalışma Visual Studio onarım Visual Studio Yükleyicisi")

   > [!NOTE]
   > Bu Visual Studio, ortamı sıfırlar. Yükseltme, kullanıcı ayarları ve profiller olmadan yüklenmiş kullanıcı başına uzantılar gibi yerel özelleştirmeler kaldırılır. Temalar, renkler ve anahtar bağlamaları gibi eşitlenmiş ayarlarınız geri yüklenir.
   >

   > [!TIP]
   > Onarım **seçeneği** yalnızca yüklü örnek örnekleri için Visual Studio. Onar seçeneğini görmüyorsanız, "Yüklü" yerine "Kullanılabilir" olarak listelenen bir sürümde Daha fazla seçeneğini Visual Studio Yükleyicisi olabilir.  

::: moniker-end

::: moniker range=">=vs-2019"

1. Bilgisayarınızda **Visual Studio Yükleyicisi'ı** bulun.

     Bu Windows Başlat menüsü "yükleyici" için arama da vesnesini arayabilirsiniz.

     ![Visual Studio Yükleyicisi](media/vs-2019/visual-studio-installer.png "Arama Visual Studio Yükleyicisi")

     > [!NOTE]
     > Aşağıdaki konumda Visual Studio Yükleyicisi da bulabilirsiniz:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Devam etmeden önce yükleyiciyi güncelleştirmeniz gerekir. Öyleyse, istemleri izleyin.

1. Yükleyicide, yüklemiş Visual Studio sürümünü ara. Ardından **Diğer'i ve** ardından Onar'ı **seçin.**

     ![Onarım Visual Studio 2019](media/vs-2019/vs-installer-repair.png "Onarım Visual Studio 2019")

   > [!NOTE]
   > Bu Visual Studio, ortamı sıfırlar. Yükseltme, kullanıcı ayarları ve profiller olmadan yüklenmiş kullanıcı başına uzantılar gibi yerel özelleştirmeler kaldırılır. Temalar, renkler ve anahtar bağlamaları gibi eşitlenmiş ayarlarınız geri yüklenir.
   >

   > [!TIP]
   > Onarım **seçeneği** yalnızca yüklü örnek örnekleri için Visual Studio. Onar seçeneğini görmüyorsanız, "Yüklü" yerine "Kullanılabilir" olarak listelenen bir sürümde Daha fazla seçeneğini Visual Studio Yükleyicisi olabilir.  

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleme](install-visual-studio.md)
* [Visual Studio’yu güncelleştirme](update-visual-studio.md)
* [Visual Studio'yu kaldırma](uninstall-visual-studio.md)
* [Yükleme Visual Studio yükseltme sorunlarını giderme](troubleshooting-installation-issues.md)
