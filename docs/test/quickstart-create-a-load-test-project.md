---
title: Web performansı ve yük testi projesi oluşturma
description: Bu hızlı başlangıç ile bir web performansı ve yük testi projesi Visual Studio ve çalıştırmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/14/2018
ms.topic: quickstart
helpviewer_keywords:
- load testing, quickstart
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: dfc8f4835c2534c80109b3fc93eb7907bcef729d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122054242"
---
# <a name="quickstart-create-a-load-test-project"></a>Hızlı Başlangıç: Yük testi projesi oluşturma

Bu 10 dakikalık hızlı başlangıçta web performansı ve yük testi projesi oluşturma ve çalıştırma hakkında bilgi Visual Studio. Yük testleri, aynı anda bir sunucuya erişen birçok kullanıcının benzetimini yapmak için web performansı veya birim testleri yürütür.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="software-requirements"></a>Yazılım gereksinimleri

Web performansı ve yük testi projeleri yalnızca **Enterprise'nin Visual Studio.**

## <a name="install-the-load-testing-component"></a>Yük testi bileşenini yükleme

Web performansı ve yük testi araçları bileşeni henüz yüklü değilse, web uygulaması aracılığıyla yüklemeniz Visual Studio Yükleyicisi.

1. Yeni **Visual Studio Yükleyicisi** başlat **menüsünden** Windows. Yeni proje iletişim kutusundan Visual Studio araç çubuğundan Araçlar Araçları ve Özellikleri Al'ı seçerek de  >   erişebilirsiniz.

1. Bu **Visual Studio Yükleyicisi** Tek bileşenler **sekmesini** seçin ve hata ayıklama ve test bölümüne **inin.** Web **performansı ve yük testi araçları'ı seçin.**

   ![Web performansı ve yük testi araçları bileşeni](media/web-perf-load-testing-tools-component.png)

1. Değiştir **düğmesini** seçin.

   Web performansı ve yük testi araçları bileşeni yüklenir.

## <a name="create-a-load-test-project"></a>Yük testi projesi oluşturma

Bu bölümde bir C# yük testi projesi oluşturuz. Tercih ederseniz bir Visual Basic test projesi de oluşturabilirsiniz.

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

2. Menü  > **çubuğundan** > **Project** Yeni Dosya'ya tıklayın.

   Yeni **Project** iletişim kutusu açılır.

3. Yeni **Project** iletişim kutusunda Yüklü ve  Visual **C#** öğesini genişletin ve ardından **Test kategorisini** seçin. Web Performansı **ve Yük Testi Project** seçin.

   ![Web performansı ve yük testi proje şablonu](media/web-perf-load-test-project-template.png)

4. Varsayılan adı kullanmak istemiyorsanız proje için bir ad girin ve tamam'ı **seçin.**

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın.

2. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

3. Yeni **proje oluştur sayfasında** arama kutusuna **web testi** yazın ve C# için Web Performansı ve Yük Testi Project **Kullanım \[ Dışı]** şablonunu seçin. **İleri**’yi seçin.

4. Varsayılan adı kullanmak istemiyorsanız proje için bir ad girin ve oluştur'a **basın.**

::: moniker-end

   Visual Studio projeyi oluşturur ve dosyaları **Çözüm Gezgini.** Proje başlangıçta *WebTest1.webtest* adlı bir web test dosyası içerir.

## <a name="add-a-load-test-to-the-project"></a>Projeye yük testi ekleme

1. Çözüm Gezgini'daki proje düğümünün sağ tıklama **menüsünden veya bağlam** menüsünden Yük Testi **Ekle'yi**  >  **seçin.**

   Yeni **Yük Testi Sihirbazı** açılır.

1. Şirket **İçi Yük Testi seçeneğini ve** ardından Sonraki'yi **seçin.** Bulut tabanlı yük testi hakkında daha fazla bilgi için buraya [bakabilirsiniz.](/azure/devops/test/load-test/get-started-simple-cloud-load-test?view=vsts&preserve-view=true)

   ![Yeni yük testi sihirbazı - ilk sayfa](media/load-test-wizard-page-1.png)

1. Bir **yük** testi senaryosuna test ekle ve test karışımı sayfasını düzenleyene kadar sihirbazda adım adım gitmek için **Sonraki'yi** seçin. **Ekle** düğmesini seçin.

   Test **Ekle iletişim** kutusu açılır.

1. Kullanılabilir **testler'in** altında **WebTest1'i** seçin ve ardından sağ oku seçerek Seçili testler **kutusuna taşıyın.** Tamam **düğmesini** seçin.

   ![Test Ekle iletişim kutusu](media/add-tests-dialog-box.png)

1. Yeni Giriş **Yük Testi Sihirbazı,** Son **düğmesini** seçin.

   Yük testi projeye eklenir ve yük testi dosyası düzenleyici penceresinde açılır.

## <a name="run-the-load-test"></a>Yük testini çalıştırma

Çok fazla bir şey yapmayan bir yük testi oluşturduk ama yine de çalıştır bakalım.

Düzenleyicide açık olan yük testinin sağ tıklama menüsünden veya bağlam menüsünden Yük Testi **Çalıştır'ı seçin.**

![Yük Testi Çalıştır menüsü](media/run-load-test.png)

Yük testi çalışmaya başlar. Test Sonuçları  penceresinde testin devam ediyor olduğu ve yük testi çözümleyicisi düzenleyici penceresinde görüntüleniyor. Test tamamlandıktan sonra varsayılan değerleri kabul edersiniz beş dakika içinde düzenleyicide bir özet gösterilir. Yük **testinin sonuçları hakkında** **farklı bilgiler** almak **için** Graflar, Tablolar veya Ayrıntı'ı seçebilirsiniz.

![Yük testi çözümleyicisi penceresi](media/load-test-analyzer.png)

## <a name="next-steps"></a>Sonraki adımlar

Basit bir yük testi projesi oluşturduğunuza göre, sonraki adım senaryoları, sayaç kümelerini ve çalıştırma ayarlarını yapılandırmaktır.

> [!div class="nextstepaction"]
> [Test ayarlarını düzenleme](edit-load-tests.md)
