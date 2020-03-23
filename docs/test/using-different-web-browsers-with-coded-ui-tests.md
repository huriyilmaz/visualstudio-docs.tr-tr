---
title: Kodlanmış UI Testleriyle Farklı Web Tarayıcıları Kullanma
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 104bdcc7a3f609456d521e710ac6ec2aeda2bb75
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585580"
---
# <a name="use-different-web-browsers-with-coded-ui-tests"></a>Kodlu UI testleri ile farklı web tarayıcıları kullanın

Kodlanmış UI testleri, web uygulamaları için Internet Explorer'ı kullanarak testlerinizi kaydederek sınamayı otomatikleştirebilirsiniz. Bu web uygulamaları için Internet Explorer veya başka tarayıcı türleri kullanarak testinizi özelleştirebilir ve geri oynatabilirsiniz.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

İlk olarak, [kodlanmış UI çapraz tarayıcı testi için Selenyum bileşenlerini yükleyin.](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting)

## <a name="whats-supported-across-all-web-browsers"></a>Tüm web tarayıcılarında neler desteklenir?

- Özellikleri, arama ve oynatma garsonları gibi [özellikleri denetlemek için özel kod ekleyin.](https://devblogs.microsoft.com/devops/coded-ui-test-configuring-search-properties-while-recording-on-internet-explorer/)

- Açılır pencereler ve iletişim kutuları

- [İade türü olmadan temel JavaScript'i çalıştırın](https://devblogs.microsoft.com/devops/introducing-javascript-execution-on-internetexplorer-and-crossbrowser-in-coded-ui-test/)

- Arama esnekliği (akıllı eşleşme kullanarak) ve [performans iyileştirmeleri](https://devblogs.microsoft.com/devops/guidelines-on-improving-performance-of-coded-ui-test-playback/)

## <a name="why-should-i-use-coded-ui-tests-across-multiple-web-browser-types"></a>Birden çok web tarayıcı türleri arasında kodlanmış UI testleri neden kullanmalıyım?

Çeşitli web tarayıcı türleri kullanarak, web uygulamanızı test ederek, farklı tarayıcılar çalıştıran kullanıcıların kullanıcı arabirimi deneyimi daha iyi benzetirsiniz. Örneğin, uygulamanız diğer web tarayıcıları ile uyumlu olmayan Internet Explorer denetim veya kod içerebilir. Diğer tarayıcılar arasında kodlanmış UI testleri çalıştırarak, müşterilerinizi etkilemeden önce herhangi bir sorunu keşfedebilir ve düzeltebilirsiniz.

## <a name="how-do-i-record-and-play-back-coded-ui-tests-on-web-applications-using-the-supported-web-browsers"></a>Kodlanmış UI testleri desteklenen web tarayıcısı kullanarak web uygulamaları üzerinde nasıl kaydederim ve kayıttan yürütürüm?

**Kayıt:** Internet Explorer'ı kullanarak web uygulama testinizi kaydetmek için Kodlu Kullanıcı Bira Testi Oluşturucusu'nu kullanmanız gerekir. İsteğe bağlı olarak, doğrulama ve kodlanmış UI testleri için normalde yaptığınız gibi önceden tanımlanmış bir özellik kümesi kullanarak sınanmış denetimler için özel kod ekleyebilirsiniz. Daha fazla bilgi için [kodunuzu sınamak için Kullanıcı Arabirimi otomasyonunu kullanın'a](../test/use-ui-automation-to-test-your-code.md)bakın.

> [!NOTE]
> Google Chrome veya Mozilla Firefox tarayıcısı kullanarak kodlanmış UI testleri kaydedemezsiniz.

**Internet Explorer ile oynatma:** Hiçbir tarayıcı açıkça belirtilmediğinde, testler varsayılan olarak Internet Explorer'da çalışır. Tarayıcının test kodundaki **BrowserWindow.CurrentBrowser** özelliğini ayarlayarak kullanılacak tarayıcıyı açıkça belirtebilirsiniz. Internet Explorer için bu özellik **IE** veya **Internet Explorer**olarak ayarlanmalıdır.

**Internet Explorer olmayan web tarayıcılarıyla oynatma:** Internet Explorer olmayan web tarayıcılarında oynatmak için, test kodunuzdaki BrowserWindow.CurrentBrowser özelliğini **Firefox** veya **Chrome**olarak değiştirin.

IE olmayan web tarayıcılarında testleri oynatmak **için, Kodlu UI Çapraz Tarayıcı Testi için Selenium bileşenlerini**yüklemeniz gerekir.

### <a name="install-selenium-components"></a>Selenyum bileşenlerini kurun

::: moniker range="vs-2017"

1. **Araçlar** menüsünde **Uzantılar ve Güncelleştirmeler'i**seçin.

2. **Uzantılar ve Güncelleştirmeler** iletişim kutusunda, `Selenium components for Cross Browser Testing`.

::: moniker-end

::: moniker range=">=vs-2019"

1. **Uzantılar** menüsünde **Uzantıları Yönet'i**seçin.

2. Uzantıları **Yönet** iletişim kutusunda, `Selenium components for Cross Browser Testing`.

::: moniker-end

3. Uzantıyı vurgulayın ve **İndir'i**seçin.

    > [!TIP]
    > Ayrıca kodlu UI Çapraz Tarayıcı Testi için Selenyum [bileşenlerini buradan](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting)indirebilirsiniz.

Kodlanmış Kullanıcı Arabirimi testleri oluşturma ve kullanma hakkında daha fazla bilgi için [kodlanmış Kullanıcı Arabirimi testleri oluştur'a](../test/use-ui-automation-to-test-your-code.md)bakın.

### <a name="enable-debugging"></a>Hata ayıklamayı etkinleştir

Web uygulamanızda hata ayıklamayı etkinleştirmek için aşağıdaki yapılandırma seçeneklerini tamamlamanız gerekir:

1. Yalnızca Kendi Kodumu Etkinleştir:

    1. **Araçlar** menüsünde **Seçenekler'i** seçin ve ardından **Hata Ayıklama'yı**seçin.

    2. **Yalnızca Kodumu Etkinleştir'i**seçin.

2. CLR özel durumları devre dışı bırakın:

    1. Hata **Ayıklama** menüsünde **Özel Durumlar'ı**seçin.

    2. **Ortak Dil Çalışma Zamanı Özel Durumları**için, Kullanıcı nın **denetimini**kaldırın.

Kodlanmış UI testinde `BrowserWindow.CurrentBrowser` değişiklik seçeneğini görmüyorsanız, Visual Studio'nun çeşitli web tarayıcıları kullanarak kodlanmış UI testlerini desteklemeyen bir sürümünü kullanıyor olabilirsiniz. Bu tür kodlanmış ui testlerini kullanmak için Visual Studio Enterprise sürümünü kullanmanız gerekir.

Bilmeniz gereken diğer bazı şeyler şunlardır:

- Apple Safari web tarayıcısı desteklenmiyor.

- Web tarayıcısını başlatma eylemini, kodlanmış UI testi parçası olmalıdır.

   Internet Explorer kullanmadığınız sürece açık bir web tarayıcısına sahip ve adımlar üzerinde çalıştırmak istiyorsanız, kayıttan yürütme başarısız olur. Bu nedenle, web tarayıcınızı başlatması kodlanmış UI testleriniz bir parçası olarak dahil en iyi uygulamadır.

- Ekranı kapla, simge durumuna küçült, geri yükle gibi belirli tarayıcı tabanlı UI eylemlerini böyle otomatikleştirme desteklenmiyor.

## <a name="tips"></a>İpuçları

Çıktı kodlanmış UI günlüklerinde ekran görüntüleri dahil etmek için yapılandırabilirsiniz. Bunu yapmak için *QTAgent32.exe.config* dosyasında bazı yapılandırma ayarlarını ayarlamanız gerekir. Varsayılan olarak, bu dosya aşağıdaki konuma yüklenir:

*%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*

Aşağıdaki değerleri ayarlayın:

- `EqtTraceLevel``system.diagnostics` bölümünde.

- `<add name="EqtTraceLevel" value="4" />`

   Değeri 3 veya daha yüksek olarak ayarlayarak, her eylem için ekran görüntüleri alınır. Değeri 1 veya 2'ye ayarlandığında, ekran görüntüleri yalnızca hata eylemleri alır.

Daha fazla bilgi için bkz: [Kodlanmış Kullanıcı Arabirimi test günlüklerini kullanarak kodlanmış Kullanıcı Arabirimi testlerini çözümle.](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md)

## <a name="video-resources"></a>Video kaynakları

[IE'de kayıt ve her yerde oynatma](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!183&authkey=!ANqaLtCZbtJrImU)

[Kodlu UI test oluşturucu ile yazar çapraz tarayıcı testleri](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!184&authkey=!AKG8CSow_qmeTq8)

[Yazar çapraz tarayıcı testleri UI Harita olmadan düz el kodlama kullanarak](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!186&authkey=!AJaEvxJnsefyAT4)

[Birden çok tarayıcıda çapraz tarayıcı testlerini sırayla çalıştırın](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!187&authkey=!ADI8eCQkxHnpOR8)

[Tarayıcılar arası test hatalarını giderme](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!182&authkey=!AEpS48i295B49FI)

## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri ve eylem kayıtları için desteklenen yapılandırmalar ve platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Kodlanmış UI test günlüklerini kullanarak kodlanmış UI testlerini analiz edin](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md)
