---
title: Web performansı ve yükleme testi projesi oluşturma
ms.date: 03/14/2018
ms.topic: quickstart
helpviewer_keywords:
- load testing, quickstart
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4f186e8c10d894b98e789480046d43fc957edd8a
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75566416"
---
# <a name="quickstart-create-a-load-test-project"></a>Hızlı Başlangıç: Yük testi projesi oluşturma

Bu 10 dakikalık hızlı başlangıçta, Visual Studio'da bir web performansı ve yükleme testi projesi oluşturmayı ve çalıştırmayı öğreneceksiniz. Yük testleri, aynı anda bir sunucuya erişen birçok kullanıcıyı simüle etmek için web performansını veya birim testlerini yürütür.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="software-requirements"></a>Yazılım gereksinimleri

Web performansı ve yük testi projeleri yalnızca Visual Studio'nun **Enterprise sayısında** mevcuttur.

## <a name="install-the-load-testing-component"></a>Yük test bileşenini yükleme

Web performansı ve yük test araçları bileşeni zaten yüklü değilseniz, Visual Studio Installer aracılığıyla yüklemeniz gerekir.

1. Windows'un **Başlat** menüsünden **Visual Studio Yükleyici'yi** açın. Ayrıca Visual Studio'da yeni proje iletişim kutusundan veya menü çubuğundan **Araçlar** > **Al Araçları ve Özellikleri** seçerek erişebilirsiniz.

1. **Visual Studio Installer'da,** Tek **tek bileşenler** sekmesini seçin ve **Hata Ayıklama ve Test** bölümüne gidin. **Web performansı ve yük test araçlarını**seçin.

   ![Web performansı ve yük test araçları bileşeni](media/web-perf-load-testing-tools-component.png)

1. **Değiştir** düğmesini seçin.

   Web performansı ve yük test araçları bileşeni yüklenir.

## <a name="create-a-load-test-project"></a>Yük testi projesi oluşturma

Bu bölümde, bir C# yük testi projesi oluşturacağız. İsterseniz Visual Basic yük testi projesi de oluşturabilirsiniz.

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

2. Menü çubuğundan **Yeni** > **Proje** **Dosyası'nı** > seçin.

   **Yeni Proje** iletişim kutusu açılır.

3. Yeni **Proje** iletişim kutusunda, **Yüklü** ve **Görsel C#** dosyasını genişletin ve ardından **Test** kategorisini seçin. Web **Performansı ve Yük Testi Projesi** şablonunu seçin.

   ![Web performansı ve yük testi proje şablonu](media/web-perf-load-test-project-template.png)

4. Varsayılan adı kullanmak istemiyorsanız proje için bir ad girin ve ardından **Tamam'ı**seçin.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın.

2. Başlangıç penceresinde yeni **bir proje oluştur'u**seçin.

3. Yeni **bir proje oluştur** sayfasında, arama kutusuna **web testi** yazın ve ardından C# için Web Performansı ve Yük Testi **Projesi \[Deprecated]** şablonunu seçin. **İleri**’yi seçin.

4. Varsayılan adı kullanmak istemiyorsanız proje için bir ad girin ve ardından **Oluştur'u**seçin.

::: moniker-end

   Visual Studio projeyi oluşturur ve **dosyaları Solution Explorer'da**görüntüler. Proje başlangıçta *WebTest1.webtest*adlı bir web test dosyası içerir.

## <a name="add-a-load-test-to-the-project"></a>Projeye yük testi ekleme

1. **Çözüm Gezgini'ndeki**proje düğümünün sağ tıklama menüsünden veya bağlam menüsünden**Yük Testi** **Ekle'yi** > seçin.

   **Yeni Yük Testi Sihirbazı** açılır.

1. Şirket **İçi Yük Testi** seçeneğini seçin ve sonra **İleri'yi**seçin. Bulut tabanlı yük [testi](/azure/devops/test/load-test/get-started-simple-cloud-load-test?view=vsts)hakkında daha fazla bilgi edinebilirsiniz.

   ![Yeni yük testi sihirbazı - ilk sayfa](media/load-test-wizard-page-1.png)

1. **Bir yük testi senaryosuna test ekle'ye** ulaşana kadar sihirbazda adım **atmak** ve test karışımı sayfasını düzenlemeyi seç. **Ekle** düğmesini seçin.

   **Testler Ekle** iletişim kutusu açılır.

1. **Kullanılabilir testler** **altında, WebTest1'i**seçin ve ardından **seçili testler** kutusuna taşımak için doğru oku seçin. **Tamam** düğmesini seçin.

   ![Testler iletişim kutusu ekle](media/add-tests-dialog-box.png)

1. **Yeni Yük Testi Sihirbazı'nda,** **Bitiş** düğmesini seçin.

   Yükleme testi projeye eklenir ve yükleme testi dosyası düzenleyici penceresinde açılır.

## <a name="run-the-load-test"></a>Yük testini çalıştırın

Çok fazla işe yaramabir bir yük testi oluşturduk, ama yine de çalıştıralım.

Düzenleyicide açık olan yük testinin sağ tıklama menüsünden veya bağlam menüsünden **Yük Testi Çalıştır'ı**seçin.

![Yük Testini Çalıştır menüsü](media/run-load-test.png)

Yük testi çalışmaya başlar. **Test Sonuçları** penceresi, testin devam ettiğini ve yük testi çözümleyicisinin düzenleyici penceresinde görüntülendiğini gösterir. Varsayılanları kabul ederseniz beş dakika olması gereken test tamamlandıktan sonra, düzenleyicide bir özet gösterilir. Yük testinin sonuçları hakkında farklı bilgiler almak için **Grafikler,** **Tablolar**veya **Ayrıntı'yı** seçebilirsiniz.

![Yük testi çözümleyicisi penceresi](media/load-test-analyzer.png)

## <a name="next-steps"></a>Sonraki adımlar

Artık basit bir yük testi projesi oluşturduğunuza göre, bir sonraki adım senaryoları, sayaç kümelerini yapılandırmak ve ayarları çalıştırmaktır.

> [!div class="nextstepaction"]
> [Test ayarlarını değiştir](edit-load-tests.md)
