---
title: Kodlanmış UI Testleriyle farklı Web tarayıcıları kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: a859595f-6517-43f2-9d61-c706cb55a388
caps.latest.revision: 25
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 31ca0fdbecf7ea3742fef60f99f2a0a25220f9cf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657233"
---
# <a name="using-different-web-browsers-with-coded-ui-tests"></a>Kodlanmış UI Testleriyle Farklı Web Tarayıcıları Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kodlanmış UI testleri, web uygulamaları için Internet Explorer'ı kullanarak testlerinizi kaydederek sınamayı otomatikleştirebilirsiniz. Bu web uygulamaları için Internet Explorer veya başka tarayıcı türleri kullanarak testinizi özelleştirebilir ve geri oynatabilirsiniz.

 **Requirements**

- Visual Studio Enterprise

- İşletim sistemleri:

  - Microsoft Windows 7

  - Microsoft Windows 8

  - Microsoft Windows Server 2008 R2 SP1

- Web tarayıcı sürümleri:

  - Windows Internet Explorer 9

  - Windows Internet Explorer 10

  - Mozilla Firefox ve Google Chrome 'un desteklenen sürümleri için [buraya](http://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d/) gidin

- [Kodlanmış Kullanıcı Arabirimi çapraz tarayıcı testi Için Selenium bileşenlerini](http://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d/)yükler.

  **Tüm Web tarayıcıları genelinde desteklenen özellikler nelerdir?**

- Özellikler, arama ve kayıttan yürütme waiters gibi [özellikleri denetlemek için özel kod ekleyin](http://blogs.msdn.com/b/visualstudioalm/archive/2012/12/10/coded-ui-test-configuring-search-properties-while-recording-on-internet-explorer.aspx) .

- Açılır pencereler ve iletişim kutuları

- [Dönüş türü olmayan temel JavaScript 'ı yürütme](http://blogs.msdn.com/b/visualstudioalm/archive/2013/01/18/introducing-jscript-execution-on-internetexplorer-and-crossbrowser-in-coded-ui-test.aspx)

- Arama esnekliği (akıllı eşleşme kullanarak) ve [performans iyileştirmeleri](http://blogs.msdn.com/b/visualstudioalm/archive/2012/02/01/guidelines-on-improving-performance-of-coded-ui-test-playback.aspx)

## <a name="why-should-i-use-coded-ui-tests-across-multiple-web-browser-types"></a>Birden çok web tarayıcı türleri arasında kodlanmış UI testleri neden kullanmalıyım?
 Çeşitli web tarayıcı türleri kullanarak, web uygulamanızı test ederek, farklı tarayıcılar çalıştıran kullanıcıların kullanıcı arabirimi deneyimi daha iyi benzetirsiniz. Örneğin, uygulamanız diğer web tarayıcıları ile uyumlu olmayan Internet Explorer denetim veya kod içerebilir. Diğer tarayıcılar arasında kodlanmış UI testleri çalıştırarak, müşterilerinizi etkilemeden önce herhangi bir sorunu keşfedebilir ve düzeltebilirsiniz.

## <a name="how-do-i-record-and-play-back-coded-ui-tests-on-web-applications-using-the-supported-web-browsers"></a>Kodlanmış UI testleri desteklenen web tarayıcısı kullanarak web uygulamaları üzerinde nasıl kaydederim ve kayıttan yürütürüm?
 **Kayıt:** Web uygulaması testinizi Internet Explorer kullanarak kaydetmek için kodlanmış UI Test Oluşturucusu 'nu kullanmanız gerekir. İsteğe bağlı olarak, doğrulama ve kodlanmış UI testleri için normalde yaptığınız gibi önceden tanımlanmış bir özellik kümesi kullanarak sınanmış denetimler için özel kod ekleyebilirsiniz. Daha fazla bilgi için bkz. [kodunuzu test etmek IÇIN UI Otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md).

> [!NOTE]
> Google Chrome veya Mozilla Firefox tarayıcısı kullanarak kodlanmış UI testleri kaydedemezsiniz.

 **Internet Explorer ile kayıttan Çal:** Açık bir tarayıcı belirtilmediğinde, testler varsayılan olarak Internet Explorer 'da çalışır. Test kodunuzda **BrowserWindow. CurrentBrowser** özelliğini ayarlayarak kullanılacak tarayıcıyı açıkça sağlayabilirsiniz. Internet Explorer için bu özellik **IE** veya **Internet Explorer**olarak ayarlanmalıdır.

 **Internet Explorer olmayan Web tarayıcıları ile kayıttan yürütme:** Internet Explorer olmayan Web tarayıcılarında yeniden oynatmak için, test kodunuzda BrowserWindow. CurrentBrowser özelliğini **Firefox** veya **Chrome**olarak değiştirin.

 IE olmayan Web tarayıcılarındaki testleri kayıttan yürütmek için, **KODLANMıŞ UI çapraz tarayıcı testi Için Selenium bileşenlerini**yüklemelisiniz.

#### <a name="installing-selenium-components"></a>Selenium bileşenlerini yükleme

1. **Araçlar** menüsünde **Uzantılar ve güncelleştirmeler**' i seçin.

2. Uzantı ve güncelleştirmeler iletişim kutusunda `Selenium components for Cross Browser Testing` aratın.

3. Uzantıyı vurgulayın ve **İndir**' i seçin.

   > [!TIP]
   > Ayrıca, kodlanmış UI çapraz tarayıcı testi için Selenium bileşenlerini [buradan](http://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d/)indirebilirsiniz.

   Kodlanmış UI testleri oluşturma ve kullanma hakkında daha fazla bilgi için bkz. [KODLANMıŞ UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).

### <a name="enable-debugging"></a>Hata ayıklamayı etkinleştir
 Web uygulamanızda hata ayıklamayı etkinleştirmek için aşağıdaki yapılandırma seçeneklerini tamamlamanız gerekir:

1. Yalnızca Kendi Kodumu Etkinleştir:

    1. **Araçlar** menüsünde **Seçenekler** ' i ve ardından **hata ayıklama**' yi seçin.

    2. **Yalnızca kendi kodum etkinleştir**' i seçin.

2. CLR özel durumları devre dışı bırakın:

    1. **Hata Ayıkla** menüsünde **özel durumlar**' ı seçin.

    2. **Ortak dil çalışma zamanı özel durumları**Için, **Kullanıcı tarafından işlenmeyen**onay işaretini kaldırın.

## <a name="generate"></a>*KODLANMıŞ UI testinde BrowserWindow. CurrentBrowser değiştirme seçeneğini görmüyorum.*
 Çeşitli web tarayıcıları kullanılarak kodlanmış UI testlerini desteklemeyen [!INCLUDE[vs2011_first](../includes/vs2011-first-md.md)] bir sürümünü kullanıyor olabilirsiniz. Bu tür kodlanmış UI testlerini kullanmak için Visual Studio Enterprise kullanmanız gerekir.

 *Başka ne bilmem gerekir?*
 **Notlar**

- ![Prerequsite](../test/media/prereq.png "Önkoşul") Apple Safari Web tarayıcısı desteklenmez.

- ![Prerequsite](../test/media/prereq.png "Önkoşul") Web tarayıcısını başlatma eylemi, kodlanmış UI testinin bir parçası olmalıdır.

   Internet Explorer kullanmadığınız sürece açık bir web tarayıcısına sahip ve adımlar üzerinde çalıştırmak istiyorsanız, kayıttan yürütme başarısız olur. Bu nedenle, web tarayıcınızı başlatması kodlanmış UI testleriniz bir parçası olarak dahil en iyi uygulamadır.

- ![Prerequsite](../test/media/prereq.png "Önkoşul") En yüksek ekran, en aza indirme ve geri yükleme gibi tarayıcıya özgü tabanlı kullanıcı arabirimi eylemlerinin otomatikleştirilmesi desteklenmez.

  **Uçları**

- ![İpucu](../test/media/tip.png "İpucu") Çıktıyı, kodlanmış UI günlüklerinde ekran görüntülerini içerecek şekilde yapılandırabilirsiniz. Bunu yapmak için bazı yapılandırma ayarlarını QTAgent32.exe.config dosyasında ayarlamanız gerekir. Varsayılan olarak, bu dosya aşağıdaki konuma yüklenir:

   **C:\Program Files (x86) \Microsoft Visual Studio 11.0 \ Common7\ıde**

   Aşağıdaki değerleri ayarlayın:

  - `system.diagnostics` bölümünde `EqtTraceLevel`.

  - `<add name="EqtTraceLevel" value="4" />`

     3 veya daha yüksek bir değere ayarlayarak ekran görüntüleri her eylem için alınır. Değeri 1 veya 2'ye ayarlandığında, ekran görüntüleri yalnızca hata eylemleri alır.

    Daha fazla bilgi için bkz. [kodlanmış UI test günlüklerini kullanarak KODLANMıŞ UI testlerini çözümleme](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).

## <a name="external-resources"></a>Dış Kaynaklar

### <a name="videos"></a>Videolar
 [Her yerde IE ve kayıttan yürütme üzerinde Kaydet](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!183&authkey=!ANqaLtCZbtJrImU)

 [Kodlanmış UI Test Oluşturucusu ile çapraz tarayıcı testleri yazma](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!184&authkey=!AKG8CSow_qmeTq8)

 [UI haritası olmadan düz el kodlama kullanarak çapraz tarayıcı testleri yazma](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!186&authkey=!AJaEvxJnsefyAT4)

 [Çoklu tarayıcılarda çapraz tarayıcı testlerini sırayla çalıştır](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!187&authkey=!ADI8eCQkxHnpOR8)

 [Çapraz tarayıcı test hatalarıyla ilgili sorunları giderme](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!182&authkey=!AEpS48i295B49FI)

### <a name="guidance"></a>Kılavuz
 [Visual Studio 2012 ile sürekli teslim için test etme – Bölüm 2: birim testi: Içini test etme](http://go.microsoft.com/fwlink/?LinkID=255188)

 [Visual Studio 2012 ile sürekli teslim için test etme – Bölüm 5: Sistem testlerini otomatikleştirme](http://go.microsoft.com/fwlink/?LinkID=255196)

### <a name="faq"></a>SSS
 [Kodlanmış UI testleri SSS-1](http://go.microsoft.com/fwlink/?LinkID=230576)

 [Kodlanmış UI testleri SSS-2](http://go.microsoft.com/fwlink/?LinkID=230578)

### <a name="forum"></a>Forum
 [Visual Studio UI Otomasyon testi (kodlanmış UI dahil)](http://go.microsoft.com/fwlink/?LinkID=224497)

## <a name="see-also"></a>Ayrıca Bkz.
 Kodlanmış UI [Testleri ve eylem kayıtları için](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md) kodlanmış UI [Test günlüklerini kullanarak kodlanmış UI testlerini ANALIZ](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md) [etmek için UI Otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)
