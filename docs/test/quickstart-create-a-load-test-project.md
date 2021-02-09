---
title: Web performansı ve yük testi projesi oluşturma
description: Bu hızlı başlangıç ile Visual Studio 'da Web performans ve yük testi projesi oluşturma ve çalıştırma hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 03/14/2018
ms.topic: quickstart
helpviewer_keywords:
- load testing, quickstart
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: d440b4d9fe175cb685b7e7ed3c5eb5911e541fde
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917603"
---
# <a name="quickstart-create-a-load-test-project"></a>Hızlı Başlangıç: Yük testi projesi oluşturma

Bu 10 dakikalık hızlı başlangıçta, Visual Studio 'da bir Web performans ve yük testi projesi oluşturmayı ve çalıştırmayı öğreneceksiniz. Yük testleri bir sunucuya aynı anda erişen birçok kullanıcının benzetimini yapmak için Web performansını veya birim testlerini yürütür.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="software-requirements"></a>Yazılım gereksinimleri

Web performansı ve yük testi projeleri yalnızca Visual Studio **Enterprise sürümünde** kullanılabilir.

## <a name="install-the-load-testing-component"></a>Yük testi bileşenini yükleme

Web performans ve yük testi Araçları bileşeni yüklü değilse, Visual Studio Yükleyicisi aracılığıyla yüklemeniz gerekir.

1. Windows 'un **Başlat** menüsünden **Visual Studio yükleyicisi** açın. Ayrıca, Visual Studio 'da yeni proje iletişim kutusundan veya **Araçlar**  >  **' ın araç ve Özellikler Al ' i** seçerek menü çubuğundan erişebilirsiniz.

1. **Visual Studio yükleyicisi**, **tek tek bileşenler** sekmesini seçin ve aşağı kaydırarak **hata ayıklama ve test** bölümüne gidin. **Web performansı ve yük testi Araçları '** nı seçin.

   ![Web performansı ve yük testi Araçları bileşeni](media/web-perf-load-testing-tools-component.png)

1. **Değiştir** düğmesini seçin.

   Web performans ve yük testi Araçları bileşeni yüklendi.

## <a name="create-a-load-test-project"></a>Yük testi projesi oluşturma

Bu bölümde, bir C# yük testi projesi oluşturacağız. Dilerseniz, bir Visual Basic yük testi projesi de oluşturabilirsiniz.

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

2. Menü çubuğundan **Dosya** > **Yeni** > **Proje** ' yi seçin.

   **Yeni proje** iletişim kutusu açılır.

3. **Yeni proje** iletişim kutusunda, **yüklü** ve **Visual C#**' yi genişletin ve ardından **Test** kategorisini seçin. **Web performansı ve yük testi proje** şablonunu seçin.

   ![Web performansı ve yük testi proje şablonu](media/web-perf-load-test-project-template.png)

4. Varsayılan adı kullanmak istemiyorsanız, proje için bir ad girin ve ardından **Tamam**' ı seçin.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın.

2. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

3. **Yeni proje oluştur** sayfasında, arama kutusuna **Web testi** yazın ve ardından C# için **Web performansı ve yük testi projesi \[ kullanım dışı bırakıldı]** şablonunu seçin. **İleri**’yi seçin.

4. Varsayılan adı kullanmak istemiyorsanız proje için bir ad girin ve ardından **Oluştur**' u seçin.

::: moniker-end

   Visual Studio projeyi oluşturur ve **Çözüm Gezgini** dosyaları görüntüler. Proje başlangıçta *WebTest1. webtest* adlı bir Web testi dosyası içerir.

## <a name="add-a-load-test-to-the-project"></a>Projeye yük testi ekleme

1. **Çözüm Gezgini** içindeki proje düğümünün sağ tıklama menüsünde veya bağlam menüsünde   >  **Yük testi** Ekle ' yi seçin.

   **Yeni Yük Testi Sihirbazı** açılır.

1. **Şirket Içi yük testi** seçeneğini belirleyin ve ardından **İleri**' yi seçin. Bulut tabanlı yük testi hakkında [buradan](/azure/devops/test/load-test/get-started-simple-cloud-load-test?view=vsts&preserve-view=true)daha fazla bilgi edinebilirsiniz.

   ![Yeni Yük Testi Sihirbazı-ilk sayfa](media/load-test-wizard-page-1.png)

1. **Yük testi senaryosuna teste ulaşana ve test karışımını düzenlemeye** kadar sihirbazda Ilerlemek için **İleri ' yi** seçin. **Ekle** düğmesini seçin.

   **Testler ekle** iletişim kutusu açılır.

1. **Kullanılabilir testler** altında **WebTest1**' ı seçin ve ardından sağ oku seçerek **Seçili testler** kutusuna taşıyın. **Tamam** düğmesini seçin.

   ![Testler Ekle iletişim kutusu](media/add-tests-dialog-box.png)

1. **Yeni Yük Testi Sihirbazı** geri dönüp **son** düğmesini seçin.

   Yük testi projeye eklenir ve yükleme testi dosyası düzenleyici penceresinde açılır.

## <a name="run-the-load-test"></a>Yük testini çalıştırma

Çok fazla olmayan bir yük testi oluşturduk, ancak yine de çalıştıralım.

Düzenleyicide açık olan yük testinin sağ tıklama menüsünde veya bağlam menüsünde **Yük testini çalıştır**' ı seçin.

![Yük testi menüsünü Çalıştır](media/run-load-test.png)

Yük testi çalışmaya başlar. **Test sonuçları** pencere, testin devam ettiğini ve Yük Testi Çözümleyicisinin düzenleyici penceresinde görüntülendiğini gösterir. Test tamamlandıktan sonra, Varsayılanları kabul ettiyseniz beş dakika olması gerekir, düzenleyicide bir Özet gösterilir. Yük testinin sonuçları hakkında farklı bilgiler almak için **grafikler**, **Tablolar** veya **ayrıntı** seçeneklerini belirleyebilirsiniz.

![Yük Testi Çözümleyicisi penceresi](media/load-test-analyzer.png)

## <a name="next-steps"></a>Sonraki adımlar

Artık basit bir yük testi projesi oluşturduğunuza göre, bir sonraki adım senaryolar, sayaç kümeleri ve çalışma ayarları yapılandırmak için kullanılır.

> [!div class="nextstepaction"]
> [Test ayarlarını Düzenle](edit-load-tests.md)
