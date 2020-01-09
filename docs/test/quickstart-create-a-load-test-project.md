---
title: Web performansı ve yük testi projesi oluşturma
ms.date: 03/14/2018
ms.topic: quickstart
helpviewer_keywords:
- load testing, quickstart
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4f186e8c10d894b98e789480046d43fc957edd8a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75566416"
---
# <a name="quickstart-create-a-load-test-project"></a>Hızlı Başlangıç: Yük testi projesi oluşturma

10 dakikalık bu hızlı başlangıçta, oluşturma ve bir web performansı ve yük testi projesi Visual Studio'da çalıştırma öğreneceksiniz. Yük testleri, web performans veya bir sunucu aynı anda erişen birçok kullanıcının benzetimini yapmak için birim testleri yürütün.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="software-requirements"></a>Yazılım gereksinimleri

Web performansı ve yük testi projeleri yalnızca Visual Studio **Enterprise sürümünde** kullanılabilir.

## <a name="install-the-load-testing-component"></a>Yük testi bileşeni yükle

Yoksa zaten web performansı ve yük testi araçları bileşeninin yüklü ise, Visual Studio yükleyicisi yüklemeniz gerekir.

1. Açık **Visual Studio yükleyicisi** gelen **Başlat** Windows menüsü. Ayrıca, Visual Studio 'da yeni proje iletişim kutusundan veya > **Araçlar** ' a tıklayarak menü çubuğundan **Araçlar ve Özellikler al** ' a erişebilirsiniz.

1. İçinde **Visual Studio yükleyicisi**, seçin **tek tek bileşenler** sekmesini ve ekranı aşağı kaydırarak **hata ayıklama ve test** bölümü. Seçin **Web performansı ve yük testi Araçları**.

   ![Web performansı ve yük testi araçları bileşeni](media/web-perf-load-testing-tools-component.png)

1. Seçin **Değiştir** düğmesi.

   Web performansı ve yük testi araçları bileşeni yüklenir.

## <a name="create-a-load-test-project"></a>Yük testi projesi oluşturma

Bu bölümde, bir C# yük testi projesi oluşturacağız. Tercih ederseniz, Visual Basic yük testi projesi oluşturabilirsiniz.

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

2. Menü çubuğundan **dosya** > **Yeni** > **projesi** öğesini seçin.

   **Yeni proje** iletişim kutusu açılır.

3. İçinde **yeni proje** iletişim kutusunda **yüklü** ve **Visual C#** ve ardından **Test** kategorisi. Seçin **Web performansı ve yük testi projesi** şablonu.

   ![Web performansı ve yük testi projesi şablonu](media/web-perf-load-test-project-template.png)

4. Varsayılan adı kullanın ve ardından istemiyorsanız, proje için bir ad girin **Tamam**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın.

2. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

3. **Yeni proje oluştur** sayfasında, arama kutusuna **Web testi** yazın ve daha sonra Için **Web performansı ve yük testi projesi \[kullanım dışı]** C#şablonunu seçin. Seçin **sonraki**.

4. Varsayılan adı kullanmak istemiyorsanız proje için bir ad girin ve ardından **Oluştur**' u seçin.

::: moniker-end

   Visual Studio projeyi oluşturur ve **Çözüm Gezgini**dosyaları görüntüler. Projeyi başlangıçta adlı bir web testi dosyası içeren *WebTest1.webtest*.

## <a name="add-a-load-test-to-the-project"></a>Bir yük testi projeye Ekle

1. Sağ tıklama menüsünden veya proje düğümünün kısayol menüsünü **Çözüm Gezgini**, seçin **Ekle** > **yük testi**.

   **Yeni Yük Testi Sihirbazı** açılır.

1. Seçin **şirket içi yük testi** seçeneğini ve ardından **sonraki**. Bulut tabanlı yük testi hakkında daha fazla bilgi [burada](/azure/devops/test/load-test/get-started-simple-cloud-load-test?view=vsts).

   ![Yeni Yük Testi Sihirbazı - ilk sayfa](media/load-test-wizard-page-1.png)

1. Seçin **sonraki** adımına ulaşana kadar sihirbazı takip **bir yük testi senaryosuna testleri ekleme ve test karışımını düzenleme** sayfası. Seçin **Ekle** düğmesi.

   **Test Ekle** iletişim kutusu açılır.

1. Altında **kullanılabilir testler**seçin **WebTest1'i**seçip için taşıyabiliyor için sağ ok **Seçili testler** kutusu. Seçin **Tamam** düğmesi.

   ![Testleri iletişim kutusu Ekle](media/add-tests-dialog-box.png)

1. Geri **Yeni Yük Testi Sihirbazı**, seçin **son** düğmesi.

   Yük testi projenize eklenir ve yük testi dosyası düzenleyici penceresinde açılır.

## <a name="run-the-load-test"></a>Yük testi çalıştırma

Çok fazla yapmak değil ancak çalıştıralım, yine de bir yük testi oluşturduk.

Sağ tıklama menüsünü ya da Yük Testi Düzenleyicisi'nde açık olan bağlam menüsünden seçin **yük testi Çalıştır**.

![Yük testi menüsünden çalıştırın](media/run-load-test.png)

Yük testi çalışmaya başlar. **Test sonuçları** test ediyor ve Yük Testi Çözümleyicisi düzenleyici penceresinde görüntülenen pencerede gösterilir. Varsayılanları kabul beş dakika olmalıdır, test, tamamlandıktan sonra düzenleyicide bir özeti gösterilir. Seçebileceğiniz **grafikleri**, **tabloları**, veya **ayrıntı** yük testi sonuçlarıyla ilgili farklı bilgi almak için.

![Yük Testi Çözümleyicisi penceresi](media/load-test-analyzer.png)

## <a name="next-steps"></a>Sonraki adımlar

Basit yük testi projesi oluşturduğunuza göre sıradaki adım senaryoları, sayaç kümeleri, yapılandırma ve çalıştırma ayarları olacak.

> [!div class="nextstepaction"]
> [Test Ayarlarını Düzenle](edit-load-tests.md)
