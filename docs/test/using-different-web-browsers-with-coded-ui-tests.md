---
title: Kodlanmış UI Testleriyle Farklı Web Tarayıcıları Kullanma
ms.date: 11/04/2016
ms.topic: how-to
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 507da254d108ddc31f2b1c9fdf7f393d42934f2a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85289332"
---
# <a name="use-different-web-browsers-with-coded-ui-tests"></a>Kodlanmış UI Testleriyle farklı Web tarayıcıları kullanma

Kodlanmış UI testleri, web uygulamaları için Internet Explorer'ı kullanarak testlerinizi kaydederek sınamayı otomatikleştirebilirsiniz. Bu web uygulamaları için Internet Explorer veya başka tarayıcı türleri kullanarak testinizi özelleştirebilir ve geri oynatabilirsiniz.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

İlk olarak, [KODLANMıŞ UI çapraz tarayıcı testi Için Selenium bileşenlerini](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting)yüklemeniz gerekir.

## <a name="whats-supported-across-all-web-browsers"></a>Tüm Web tarayıcıları genelinde desteklenen özellikler nelerdir?

- Özellikler, arama ve kayıttan yürütme waiters gibi [özellikleri denetlemek için özel kod ekleyin](https://devblogs.microsoft.com/devops/coded-ui-test-configuring-search-properties-while-recording-on-internet-explorer/) .

- Açılır pencereler ve iletişim kutuları

- [Dönüş türü olmayan temel JavaScript 'ı yürütme](https://devblogs.microsoft.com/devops/introducing-javascript-execution-on-internetexplorer-and-crossbrowser-in-coded-ui-test/)

- Arama esnekliği (akıllı eşleşme kullanarak) ve [performans iyileştirmeleri](https://devblogs.microsoft.com/devops/guidelines-on-improving-performance-of-coded-ui-test-playback/)

## <a name="why-should-i-use-coded-ui-tests-across-multiple-web-browser-types"></a>Birden çok web tarayıcı türleri arasında kodlanmış UI testleri neden kullanmalıyım?

Çeşitli web tarayıcı türleri kullanarak, web uygulamanızı test ederek, farklı tarayıcılar çalıştıran kullanıcıların kullanıcı arabirimi deneyimi daha iyi benzetirsiniz. Örneğin, uygulamanız diğer web tarayıcıları ile uyumlu olmayan Internet Explorer denetim veya kod içerebilir. Diğer tarayıcılar arasında kodlanmış UI testleri çalıştırarak, müşterilerinizi etkilemeden önce herhangi bir sorunu keşfedebilir ve düzeltebilirsiniz.

## <a name="how-do-i-record-and-play-back-coded-ui-tests-on-web-applications-using-the-supported-web-browsers"></a>Kodlanmış UI testleri desteklenen web tarayıcısı kullanarak web uygulamaları üzerinde nasıl kaydederim ve kayıttan yürütürüm?

**Kayıt:** Web uygulaması testinizi Internet Explorer kullanarak kaydetmek için kodlanmış UI Test Oluşturucusu 'nu kullanmanız gerekir. İsteğe bağlı olarak, doğrulama ve kodlanmış UI testleri için normalde yaptığınız gibi önceden tanımlanmış bir özellik kümesi kullanarak sınanmış denetimler için özel kod ekleyebilirsiniz. Daha fazla bilgi için bkz. [kodunuzu test etmek IÇIN UI Otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md).

> [!NOTE]
> Google Chrome veya Mozilla Firefox tarayıcısı kullanarak kodlanmış UI testleri kaydedemezsiniz.

**Internet Explorer ile kayıttan Çal:** Açık bir tarayıcı belirtilmediğinde, testler varsayılan olarak Internet Explorer 'da çalışır. Test kodunuzda **BrowserWindow. CurrentBrowser** özelliğini ayarlayarak kullanılacak tarayıcıyı açıkça sağlayabilirsiniz. Internet Explorer için bu özellik **IE** veya **Internet Explorer**olarak ayarlanmalıdır.

**Internet Explorer olmayan Web tarayıcıları ile kayıttan yürütme:** Internet Explorer olmayan Web tarayıcılarında yeniden oynatmak için, test kodunuzda BrowserWindow. CurrentBrowser özelliğini **Firefox** veya **Chrome**olarak değiştirin.

IE olmayan Web tarayıcılarındaki testleri kayıttan yürütmek için, **KODLANMıŞ UI çapraz tarayıcı testi Için Selenium bileşenlerini**yüklemelisiniz.

### <a name="install-selenium-components"></a>Selenium bileşenlerini yükler

::: moniker range="vs-2017"

1. **Araçlar** menüsünde **Uzantılar ve güncelleştirmeler**' i seçin.

2. **Uzantılar ve güncelleştirmeler** iletişim kutusunda için arama yapın `Selenium components for Cross Browser Testing` .

::: moniker-end

::: moniker range=">=vs-2019"

1. **Uzantılar** menüsünde, **Uzantıları Yönet**' i seçin.

2. **Uzantıları Yönet** iletişim kutusunda, araması yapın `Selenium components for Cross Browser Testing` .

::: moniker-end

3. Uzantıyı vurgulayın ve **İndir**' i seçin.

    > [!TIP]
    > Ayrıca, kodlanmış UI çapraz tarayıcı testi için Selenium bileşenlerini [buradan](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting)indirebilirsiniz.

Kodlanmış UI testleri oluşturma ve kullanma hakkında daha fazla bilgi için bkz. [KODLANMıŞ UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md).

### <a name="enable-debugging"></a>Hata ayıklamayı etkinleştir

Web uygulamanızda hata ayıklamayı etkinleştirmek için aşağıdaki yapılandırma seçeneklerini tamamlamanız gerekir:

1. Yalnızca Kendi Kodumu Etkinleştir:

    1. **Araçlar** menüsünde **Seçenekler** ' i ve ardından **hata ayıklama**' yi seçin.

    2. **Yalnızca kendi kodum etkinleştir**' i seçin.

2. CLR özel durumları devre dışı bırakın:

    1. **Hata Ayıkla** menüsünde **özel durumlar**' ı seçin.

    2. **Ortak dil çalışma zamanı özel durumları**Için, **Kullanıcı tarafından işlenmeyen**onay işaretini kaldırın.

`BrowserWindow.CurrentBrowser`KODLANMıŞ UI testinde değiştirme seçeneğini görmüyorsanız, Visual Studio 'nun çeşitli web tarayıcıları kullanılarak KODLANMıŞ UI testlerini desteklemeyen bir sürümünü kullanıyor olabilirsiniz. Bu tür kodlanmış UI testlerini kullanmak için Visual Studio Enterprise sürümünü kullanmanız gerekir.

Bilmeniz gereken bazı şeyler aşağıda verilmiştir:

- Apple Safari web tarayıcısı desteklenmiyor.

- Web tarayıcısını başlatma eylemini, kodlanmış UI testi parçası olmalıdır.

   Internet Explorer kullanmadığınız sürece açık bir web tarayıcısına sahip ve adımlar üzerinde çalıştırmak istiyorsanız, kayıttan yürütme başarısız olur. Bu nedenle, web tarayıcınızı başlatması kodlanmış UI testleriniz bir parçası olarak dahil en iyi uygulamadır.

- Ekranı kapla, simge durumuna küçült, geri yükle gibi belirli tarayıcı tabanlı UI eylemlerini böyle otomatikleştirme desteklenmiyor.

## <a name="tips"></a>İpuçları

Çıktı kodlanmış UI günlüklerinde ekran görüntüleri dahil etmek için yapılandırabilirsiniz. Bunu yapmak için *QTAgent32.exe.config* dosyasında bazı yapılandırma ayarları ayarlamanız gerekir. Varsayılan olarak, bu dosya aşağıdaki konuma yüklenir:

*% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE*

Aşağıdaki değerleri ayarlayın:

- `EqtTraceLevel``system.diagnostics`bölümüne.

- `<add name="EqtTraceLevel" value="4" />`

   Değeri 3 veya üzeri olarak ayarlayarak, ekran görüntüleri her bir eylem için alınır. Değeri 1 veya 2'ye ayarlandığında, ekran görüntüleri yalnızca hata eylemleri alır.

Daha fazla bilgi için bkz. [KODLANMıŞ UI test günlüklerini kullanarak KODLANMıŞ UI testlerini çözümleme](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).

## <a name="video-resources"></a>Video kaynakları

[Her yerde IE ve kayıttan yürütme üzerinde Kaydet](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!183&authkey=!ANqaLtCZbtJrImU)

[Kodlanmış UI Test Oluşturucusu ile çapraz tarayıcı testleri yazma](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!184&authkey=!AKG8CSow_qmeTq8)

[UI haritası olmadan düz el kodlama kullanarak çapraz tarayıcı testleri yazma](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!186&authkey=!AJaEvxJnsefyAT4)

[Çoklu tarayıcılarda çapraz tarayıcı testlerini sırayla çalıştır](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!187&authkey=!ADI8eCQkxHnpOR8)

[Çapraz tarayıcı test hatalarıyla ilgili sorunları giderme](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!182&authkey=!AEpS48i295B49FI)

## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzu test etmek için UI Otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri ve eylem kayıtları için desteklenen konfigürasyonlar ve platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Kodlanmış UI test günlüklerini kullanarak kodlanmış UI testlerini çözümleme](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md)
