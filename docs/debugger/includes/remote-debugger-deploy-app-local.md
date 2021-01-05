---
title: Yerel klasöre dağıt
description: Bir uygulamayı yerel bir klasöre dağıtma
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 1d049bc8b74b83028e04fe92e7ce96f45907d042
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/24/2020
ms.locfileid: "97762630"
---
1. **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve **Yayımla** ' yı (Web Forms, **Web uygulaması Yayımla**) seçin.

    Daha önce herhangi bir yayımlama profili yapılandırdıysanız, **Yayımla** bölmesi görüntülenir. **Yeni profil**' e tıklayın.

1. **Yayımla** Iletişim kutusunda **klasör**' i seçin, **Araştır**' a tıklayın ve yeni bir klasör oluşturun, **C:\publish**.

    ![Yayımla hedefi olarak seçili ' bin\Release\Publish ' klasörünü içeren Visual Studio 'da bir Yayımla hedefi seç iletişim kutusunun ekran görüntüsü.](../media/remotedbg_publish_local.png)

    Web Forms uygulama için Yayımla iletişim kutusunda **özel** ' i seçin, bir profil adı girin ve **Tamam**' ı seçin.

1. Açılan listede **Profil oluştur** ' a tıklayın (**Publish** varsayılan değerdir).

1. **Yayımla** Iletişim kutusunda **Ayarlar** bağlantısına tıklayın ve ardından **Ayarlar** sekmesini seçin.

1. Yapılandırmayı **Hata Ayıkla** olarak ayarlayın, **yayımlamadan önce tüm mevcut dosyaları sil**' i seçin ve ardından **Kaydet**' e tıklayın.

    > [!NOTE]
    > Yayın derlemesi kullanıyorsanız, yayımladığınızda web.config dosyasında hata ayıklamayı devre dışı bırakabilirsiniz.

1. **Yayımla**’ya tıklayın.

    ![Yayımla iletişim kutusundaki ayarlar sekmesinin ekran görüntüsü. Yapılandırma hata ayıklama olarak ayarlanır ve Yayımla düğmesi seçilidir.](../media/remotedbg_publish_debug_config.png)

    Uygulama, projenin **hata ayıklama** yapılandırmasını yerel klasöre yayımlar. İlerleme, çıkış penceresinde görüntülenir.

1. Visual Studio bilgisayarından ASP.NET proje dizinini, Windows Server bilgisayarındaki ASP.NET uygulaması (Bu örnekte, **C:\publish**) için yapılandırılmış yerel dizine kopyalayın. Bu öğreticide, el ile kopyaladığınızı varsayıyoruz, ancak PowerShell, xcopy veya Robocopy gibi diğer araçları da kullanabilirsiniz.

    > [!CAUTION]
    > Kodda değişiklik yapmanız veya yeniden oluşturmanız gerekiyorsa, bu adımı yeniden yayımlamanız ve yinelemeniz gerekir. Uzak makineye kopyaladığınız yürütülebilir dosya yerel kaynak ve sembollerle tam olarak eşleşmelidir.    Bunu yapmazsanız `cannot find or open the PDB file` , işlemde hata ayıklamaya çalıştığınızda Visual Studio 'da bir uyarı alırsınız.

1. Windows Server 'da uygulamayı tarayıcınızda açarak uygulamayı doğru şekilde çalıştırabildiğinizi doğrulayın.

    Uygulama düzgün çalışmazsa, sunucunuzda ve Visual Studio makinenizde yüklü olan ASP.NET sürümü arasında uyuşmazlık olabilir veya IIS veya Web sitesi yapılandırmanızda bir sorun olabilir. Önceki adımları yeniden denetleyin.
