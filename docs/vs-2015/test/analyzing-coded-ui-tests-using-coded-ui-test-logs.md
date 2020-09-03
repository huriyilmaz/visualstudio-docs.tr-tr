---
title: Kodlanmış UI test günlüklerini kullanarak kodlanmış UI testlerini çözümleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 7e795873-1d4b-4a13-a52a-a411d87fb759
caps.latest.revision: 15
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d3ebb18aaff78d9782b6210e25bcd697d21c8570
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660763"
---
# <a name="analyzing-coded-ui-tests-using-coded-ui-test-logs"></a>Kodlanmış UI Test Günlüklerini Kullanarak Kodlanmış UI Testlerini Çözümleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kodlanmış UI test günlükleri, kodlanmış UI test çalışmalarınız hakkında önemli bilgileri filtreleyip kaydeder.

 **Gereksinimler**

- Visual Studio Enterprise

## <a name="why-should-i-do-this"></a>Neden bunu yapmam gerekir?
 Günlükler, hata ayıklama sorunlarını hızla sağlayan bir biçimde sunulur.

## <a name="how-do-i-do-this"></a>Bunu nasıl yapabilirim?

### <a name="step-1-enable-logging"></a>1. Adım: günlüğü etkinleştirme
 Senaryonuza bağlı olarak, günlüğü etkinleştirmek için aşağıdaki yöntemlerden birini kullanın.

- Test projesinde App.config dosyası bulunmayan hedef .NET Framework sürüm 4

  - **QTAgent32_40.exe.config** dosyasını açın.

    Bu dosya varsayılan olarak ** \<drvie> : \Program Files (x86) \Microsoft Visual Studio 12.0 \ Common7\IDE**konumunda bulunur.

    EqtTraceLevel değerini istediğiniz günlük düzeyi ile değiştirin.

    Dosyayı kaydedin.

- Test projesinde App.config dosyası bulunmayan .NET Framework sürüm 4,5 hedef

  - **QTAgent32.exe.config** dosyasını açın.

    Bu dosya varsayılan olarak ** \<drvie> : \Program Files (x86) \Microsoft Visual Studio 12.0 \ Common7\IDE**konumunda bulunur.

    EqtTraceLevel değerini istediğiniz günlük düzeyi ile değiştirin.

    Dosyayı kaydedin.

- Test projesinde mevcut App.config dosyası

  - Projede App.config dosyası açın.

    Yapılandırma düğümü altına aşağıdaki kodu ekleyin:

    `<system.diagnostics>     <switches>       <add name="EqtTraceLevel" value="4" />     </switches>  </system.diagnostics>`

- Test kodundan günlük kaydını etkinleştir

  - <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.LoggerOverrideState%2A> = HtmlLoggerState. AllActionSnapshot;

### <a name="step-2-run-your-coded-ui-test-and-view-the-log"></a>2. Adım: kodlanmış UI testinizi çalıştırma ve günlüğü görüntüleme
 **QTAgent32.exe.config** dosyadaki değişikliklerle birlikte KODLANMıŞ bir UI testi çalıştırdığınızda, test Gezgini sonuçlarında bir çıkış bağlantısı olduğunu görürsünüz. Günlük dosyaları yalnızca testiniz başarısız olduğunda değil, izleme düzeyi "verbose" olarak ayarlandığında başarılı testler için de oluşturulur.

1. **Test** menüsünde **Windows** ' u ve ardından **Test Gezgini**' ni seçin.

2. **Build** menüsünde **Build Solution**öğesini seçin.

3. Test Gezgini 'nde, çalıştırmak istediğiniz kodlanmış UI testini seçin, kısayol menüsünü açın ve ardından **Testleri Seç**' i seçin.

     Otomatikleştirilmiş testler çalışır ve başarılı veya başarısız olup olmadığını gösterir.

    > [!TIP]
    > Test **menüsünden**test Gezgini 'ni görüntülemek Için, **Windows** 'A gelin ve ardından **Test Gezgini**' ni seçin.

4. Test Gezgini sonuçlarında **Çıkış** bağlantısını seçin.

     ![Test Gezgininde çıkış bağlantısı](../test/media/cuit-htmlactionlog1.png "CUIT_HTMLActionLog1")

     Bu, eylem günlüğüne bir bağlantı içeren test için çıktıyı görüntüler.

     ![Kodlanmış UI testinin sonuçları ve çıkış bağlantıları](../test/media/cuit-htmlactionlog2.png "CUIT_HTMLActionLog2")

5. UITestActionLog.html bağlantısını seçin.

     Günlük, Web tarayıcınızda görüntülenir.

     ![Kodlanmış UI testi günlük dosyası](../test/media/cuit-htmlactionlog3.png "CUIT_HTMLActionLog3")

## <a name="q--a"></a>Soru-Cevap

### <a name="q-what-happened-to-the-enablehtmllogger-key"></a>S: Enablehtmlgünlükçü anahtarına ne oldu?
 Visual Studio 'nun önceki sürümlerinde, kodlanmış UI testinde HTML günlükçüsü etkinleştirmek için iki yapılandırma ayarı daha vardı:

```

<add key="EnableHtmlLogger" value="true"/>

<add key="EnableSnapshotInfo" value="true"/>

```

 Bu ayarların her ikisi de Visual Studio 2012 sonrasında kullanımdan kaldırılmıştır. EqtTraceLevel, Htmlgünlükçü 'yi etkinleştirecek şekilde değiştirilmesi gereken tek ayardır.

## <a name="see-also"></a>Ayrıca Bkz.
 [Kodunuzu test etmek IÇIN UI otomasyonunu kullanın](../test/use-ui-automation-to-test-your-code.md) [: Microsoft Visual Studio Testleri çalıştırma](https://msdn.microsoft.com/library/1a1207a9-2a33-4a1e-a1e3-ddf0181b1046)
