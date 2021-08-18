---
title: Yerel klasöre dağıtma
description: Uygulamayı yerel klasöre dağıtma
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 36effcf08969c5233eaee54578c9f5e3101528b96e41cb7cbf6c0025c1f7c56b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "122058471"
---
1. Uygulamanın **Çözüm Gezgini** proje düğümüne sağ tıklayın ve Yayımla'yı seçin (Web Forms Web Uygulamasını **Yayımla).** 

    Daha önce herhangi bir yayımlama profili yapılandırdıysanız Yayımla **bölmesi** görüntülenir. Yeni **profil'e tıklayın.**

1. Yayımla **iletişim kutusunda** Klasör'e **tıklayın,** **Gözat'a** tıklayın ve **C:\Publish** yeni bir klasör oluşturun.

   ::: moniker range=">=vs-2019"

   :::image type="content" source="../media/vs-2019/remotedbg-publish-local.png" alt-text="Yayımlama hedefi olarak 'C:\Publish' Visual Studio'nin seçili olduğu Bir yayımlama hedefi seçin iletişim kutusunun ekran görüntüsü.":::

   Yayımlama **profilini** kaydetmek için Son'a tıklayın.
   ::: moniker-end
   ::: moniker range="vs-2017"
   ![Yayımlama hedefi olarak 'bin\Release\Publish' Visual Studio'nin seçili olduğu Bir yayımlama hedefi seçin iletişim kutusunun ekran görüntüsü.](../media/remotedbg_publish_local.png)
   Bir Web Forms için **Yayımla** iletişim kutusunda Özel'i seçin, bir profil adı girin ve Tamam'ı **seçin.**

   Açılan **listeden Profil** oluştur'a tıklayın ( Varsayılan değer Yayımla'dır).
   ::: moniker-end

1. Hata ayıklama yapılandırmasına geçiş.

   ::: moniker range=">=vs-2019"
   Profili **düzenlemek** için Düzenle'yi seçin ve sonra da **Ayarlar.** Bir Hata **ayıklama yapılandırması** seçin ve ardından Dosya Yayımlama **seçeneklerinin altında Hedefte** ek dosyaları **kaldır'ı** seçin.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Yeni **Ayarlar** iletişim kutusunda, Sonraki'ne tıklayarak hata ayıklamayı **etkinleştirin,** bir  **Hata** ayıklama yapılandırması seçin ve ardından Dosya Yayımlama seçenekleri altında Hedefte ek dosyaları **kaldır'ı** seçin.
   ::: moniker-end

   > [!NOTE]
   > Yayın derlemesi kullanıyorsanız, yayımlarkenweb.configdosyasında *hata ayıklamayı* devre dışı bırakın.

1. **Yayımla**’ya tıklayın.

    ![Yayımla iletişim kutusundaki Ayarlar sekmesinin ekran görüntüsü. Yapılandırma Hata Ayıkla olarak ayarlanır ve Yayımla düğmesi seçilidir.](../media/remotedbg_publish_debug_config.png)

    Uygulama, projenin **hata ayıklama yapılandırmasını** yerel klasöre yayımlar. İlerleme durumu Çıkış penceresinde gösterilir.

1. Visual Studio ASP.NET proje dizinini ASP.NET Sunucusu bilgisayarına (bu örnekte **C:\Publish**) yapılandırılan Windows yerel dizine kopyalayın. Bu öğreticide el ile kopyalamanız gerekir, ancak PowerShell, Xcopy veya Robocopy gibi diğer araçları kullanabilirsiniz.

    > [!CAUTION]
    > Kodda değişiklik yapmak veya yeniden oluşturmak için bu adımı yeniden yayımlamalı ve tekrarlaabilirsiniz. Uzak makineye kopyalanmış yürütülebilir dosya, yerel kaynağınız ve sembolleriniz ile tam olarak eşleşmeli. Bunu yapmasanız, işlemde hata ayıklamayı Visual Studio bir uyarı `cannot find or open the PDB file` alırsınız.

1. Windows Server'da, uygulamayı tarayıcınızda açarak uygulamayı doğru çalıştırabilirsiniz.

    Uygulama düzgün çalışmıyorsa, sunucunuza yüklenmiş ASP.NET sürümü ile Visual Studio makineniz arasında bir eşleşmezlik olabilir veya IIS veya Web sitesi yapılandırmanız ile ilgili bir sorun olabilir. Önceki adımları yeniden kontrol edin.
