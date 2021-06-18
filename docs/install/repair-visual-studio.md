---
title: Visual Studio’yu onarın
titleSuffix: ''
description: Visual Studio 2017 yüklemesini onarmayı öğrenin
ms.date: 10/12/2020
ms.custom: acquisition
ms.topic: how-to
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 5fd791b035bc99d46f53d499339a9e9f80a42905
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306949"
---
# <a name="repair-visual-studio"></a>Visual Studio’yu onarın

Bazen Visual Studio veya bozuk hale gelir. Onarım, güncelleştirmeler de dahil olmak üzere tüm yükleme işlemleri boyunca yükleme zamanı sorunlarını düzeltmek için kullanışlıdır.

## <a name="when-to-use-repair"></a>Onarım ne zaman kullanımlı?
* Yükleme yüküyle ilgili sorunları varsa. Dosyayı diske yazma işlemi başarılı olmaz ve bozuk dosya silinerek düzeltilenemese de bu durum oluşabilir. Onarım, gerekli dosyaları yeniden edinebilirsiniz. 
* İstemci tarafı indirme sorunlarıyla karşıdan yüklensin. Tüm bağlantı veya ara sunucu sorunlarını çözmüş olduğunu varsayarak, onarım yardımcı olabilir. 
* Güncelleştirmeyle ilgili sorunları Visual Studio. Onarım birçok yaygın güncelleştirme sorununa çözüm sağlar. 

> [!TIP] 
> Yükleme sorunu, windows gibi temel bir Windows hizmet Windows Installer nedense, onarım aynı soruna neden olabilir. Sistemik sorunlar bozuk bir ağ bağlantısı Windows Installer kararsız İnternet bağlantısı içerebilir. Sistemik bir sorunu kontrol etmek için yükleme işlemiyle oluşturulan hata raporunu kullanın.

> [!NOTE] 
> Bu Visual Studio, kullanıcı ayarlarını sıfırlar ve zaten sahip olduğunuz derlemeleri yeniden yüklenir. Bir ürün sorunu yaşıyorsanız, onarım sorunu [çöze Visual Studio](https://aka.ms/feedback/suggest?space=8)için bir Geri Bildirim Bileti oluşturun.

## <a name="how-to-repair"></a>Onarım
::: moniker range="vs-2017"

1. Bilgisayarınızda **Visual Studio Yükleyicisi'ı** bulun.

     Örneğin, veya sonraki bir Windows 10 Yıldönümü Güncelleştirmesi çalıştıran bir bilgisayarda Başlat'ı seçin ve **ardından V** harfine kaydırın ve burada dosya adı **olarak Visual Studio Yükleyicisi.**

   > [!NOTE]
   > Bazı bilgisayarlarda, Visual Studio Yükleyicisi yükleyicisi olarak **"M"** harfi altında **Microsoft Visual Studio olabilir.**
   >
   > Alternatif olarak, aşağıdaki Visual Studio Yükleyicisi aşağıdaki konumda bulabilirsiniz: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Yükleyiciyi açın, **Diğer'i ve** ardından Onar'ı **seçin.**

    ![Çalışma Visual Studio onarımı Visual Studio Yükleyicisi](media/repair-visual-studio.png "Çalışma Visual Studio onarımı Visual Studio Yükleyicisi")

   > [!NOTE]
   > Bu Visual Studio, ortamı sıfırlar. Yükseltme, kullanıcı ayarları ve profiller olmadan yüklenmiş kullanıcı başına uzantılar gibi yerel özelleştirmeler kaldırılır. Temalar, renkler ve anahtar bağlamaları gibi eşitlenmiş ayarlarınız geri yüklenir.
   >

   > [!TIP]
   > Onar **seçeneği** yalnızca yüklü örnek örnekleri için Visual Studio. Onar seçeneğini görmüyorsanız, "Yüklü" yerine "Kullanılabilir" olarak listelenen bir sürümde Diğer'i Visual Studio Yükleyicisi seçeneğinin belirtilmiş olma olasılığı vardır.  

::: moniker-end

::: moniker range=">=vs-2019"

1. Bilgisayarınızda **Visual Studio Yükleyicisi'ı** bulun.

     Windows Başlat menüsü", "yükleyici" için arama da kullanabilirsiniz.

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
   > Onar **seçeneği** yalnızca yüklü örnek örnekleri için Visual Studio. Onar seçeneğini görmüyorsanız, "Yüklü" yerine "Kullanılabilir" olarak listelenen bir sürümde Diğer'i Visual Studio Yükleyicisi seçeneğinin belirtilmiş olma olasılığı vardır.  

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleme](install-visual-studio.md)
* [Visual Studio’yu güncelleştirme](update-visual-studio.md)
* [Visual Studio'yu kaldırma](uninstall-visual-studio.md)
* [Yükleme Visual Studio yükseltme sorunlarını giderme](troubleshooting-installation-issues.md)
