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
ms.openlocfilehash: b6ceee76d8c24ccddb41e47c0865d96c79e6fc32
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102249876"
---
1. **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve **Yayımla** ' yı (Web Forms, **Web uygulaması Yayımla**) seçin.

    Daha önce herhangi bir yayımlama profili yapılandırdıysanız, **Yayımla** bölmesi görüntülenir. **Yeni profil**' e tıklayın.

1. **Yayımla** Iletişim kutusunda **klasör**' i seçin, **Araştır**' a tıklayın ve yeni bir klasör oluşturun, **C:\publish**.

   ::: moniker range=">=vs-2019"

   :::image type="content" source="../media/vs-2019/remotedbg-publish-local.png" alt-text="Yayımla hedefi olarak seçilen ' C:\Publish ' klasörüyle Visual Studio 'da bir Yayımla hedefi seç iletişim kutusunun ekran görüntüsü.":::

   Yayımla profilini kaydetmek için **son** ' a tıklayın.
   ::: moniker-end
   ::: moniker range="vs-2017"
   ![Yayımla hedefi olarak seçili ' bin\Release\Publish ' klasörünü içeren Visual Studio 'da bir Yayımla hedefi seç iletişim kutusunun ekran görüntüsü.](../media/remotedbg_publish_local.png)
   Web Forms uygulama için Yayımla iletişim kutusunda **özel** ' i seçin, bir profil adı girin ve **Tamam**' ı seçin.

   Açılan listede **Profil oluştur** ' a tıklayın (**Publish** varsayılan değerdir).
   ::: moniker-end

1. Hata ayıklama yapılandırmasına geçiş yapın.

   ::: moniker range=">=vs-2019"
   Profili düzenlemek için **Düzenle** ' yi seçin ve ardından **Ayarlar**' ı seçin. Bir **hata ayıklama** yapılandırması seçin ve ardından **dosya yayımlama** seçenekleri altında **Hedefteki ek dosyaları Kaldır** ' ı seçin.
   ::: moniker-end
   ::: moniker range="vs-2017"
   **Ayarlar** iletişim kutusunda, **İleri**' ye tıklayarak hata ayıklamayı etkinleştirin, **hata ayıklama** yapılandırması ' nı seçin ve ardından **dosya yayımlama** seçenekleri altında **Hedefteki ek dosyaları Kaldır** ' ı seçin.
   ::: moniker-end

   > [!NOTE]
   > Yayın derlemesi kullanıyorsanız, yayımladığınızda *web.config* dosyasında hata ayıklamayı devre dışı bırakabilirsiniz.

1. **Yayımla**’ya tıklayın.

    ![Yayımla iletişim kutusundaki ayarlar sekmesinin ekran görüntüsü. Yapılandırma hata ayıklama olarak ayarlanır ve Yayımla düğmesi seçilidir.](../media/remotedbg_publish_debug_config.png)

    Uygulama, projenin **hata ayıklama** yapılandırmasını yerel klasöre yayımlar. İlerleme, çıkış penceresinde görüntülenir.

1. Visual Studio bilgisayarından ASP.NET proje dizinini, Windows Server bilgisayarındaki ASP.NET uygulaması (Bu örnekte, **C:\publish**) için yapılandırılmış yerel dizine kopyalayın. Bu öğreticide, el ile kopyaladığınızı varsayıyoruz, ancak PowerShell, xcopy veya Robocopy gibi diğer araçları da kullanabilirsiniz.

    > [!CAUTION]
    > Kodda değişiklik yapmanız veya yeniden oluşturmanız gerekiyorsa, bu adımı yeniden yayımlamanız ve yinelemeniz gerekir. Uzak makineye kopyaladığınız yürütülebilir dosya yerel kaynak ve sembollerle tam olarak eşleşmelidir. Bunu yapmazsanız `cannot find or open the PDB file` , işlemde hata ayıklamaya çalıştığınızda Visual Studio 'da bir uyarı alırsınız.

1. Windows Server 'da uygulamayı tarayıcınızda açarak uygulamayı doğru şekilde çalıştırabildiğinizi doğrulayın.

    Uygulama düzgün çalışmazsa, sunucunuzda ve Visual Studio makinenizde yüklü olan ASP.NET sürümü arasında uyuşmazlık olabilir veya IIS veya Web sitesi yapılandırmanızda bir sorun olabilir. Önceki adımları yeniden denetleyin.
