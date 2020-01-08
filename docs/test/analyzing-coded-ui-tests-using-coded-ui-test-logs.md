---
title: Kodlanmış UI Test Günlüklerini Kullanarak Kodlanmış UI Testlerini Çözümleme
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: ec1025eaa53861fae2cf92395d8842854649fa8c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591222"
---
# <a name="analyzing-coded-ui-tests-using-coded-ui-test-logs"></a>Kodlanmış UI test günlüklerini kullanarak kodlanmış UI testlerini çözümleme

Kodlanmış UI test günlükleri, kodlanmış UI test çalışmalarınız hakkında önemli bilgileri filtreleyip kaydeder. Günlükler, hata ayıklama sorunlarını hızla sağlayan bir biçimde sunulur.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="step-1-enable-logging"></a>1\. Adım: günlüğü etkinleştirme

Senaryonuza bağlı olarak, günlüğü etkinleştirmek için aşağıdaki yöntemlerden birini kullanın:

- Test projenizde bir *app. config* dosyası yoksa:

   1. Testinizi çalıştırdığınızda hangi *QTAgent\*. exe* işleminin başlatılmayı saptayın. Bunu yapmanın bir yolu Windows **Görev Yöneticisi**'nde **Ayrıntılar** sekmesini izlerken.

   2. *% ProgramFiles (x86)% \ Microsoft Visual Studio\\\<sürüm >\\\<edition > \Common7\IDE* klasöründen karşılık gelen *. config* dosyasını açın. Örneğin, çalıştıran işlem *QTAgent_40. exe*ise, *QTAgent_40. exe. config*dosyasını açın.

   2. **EqtTraceLevel** değerini istediğiniz günlük düzeyi ile değiştirin.

      ```xml
      <!-- You must use integral values for "value".
           Use 0 for off, 1 for error, 2 for warn, 3 for info, and 4 for verbose. -->
      <add name="EqtTraceLevel" value="4" />
      ```

   3. Dosyayı kaydedin.

- Test projenizde bir *app. config* dosyası varsa:

  - Projedeki *app. config* dosyasını açın ve aşağıdaki kodu yapılandırma düğümü altına ekleyin:

    ```xml
    <system.diagnostics>
      <switches>
        <add name="EqtTraceLevel" value="4" />
      </switches>
    </system.diagnostics>`
    ```

- Test kodundan günlük kaydını etkinleştirin:

   ```csharp
   Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.LoggerOverrideState = HtmlLoggerState.AllActionSnapshot;
   ```

## <a name="step-2-run-your-coded-ui-test-and-view-the-log"></a>2\. Adım: kodlanmış UI testinizi çalıştırma ve günlüğü görüntüleme

*QTAgent\*. exe. config* dosyasındaki değişikliklerle birlikte KODLANMıŞ bir UI testi çalıştırdığınızda, **Test Gezgini** sonuçlarında bir çıkış bağlantısı görürsünüz. Günlük dosyaları yalnızca testiniz başarısız olduğunda değil, izleme düzeyi **verbose**olarak ayarlandığında de başarılı testler için değil.

1. **Test** menüsünde **Windows** ' u ve ardından **Test Gezgini**' ni seçin.

2. **Build** menüsünde **Build Solution**öğesini seçin.

3. **Test Gezgini**'nde, çalıştırmak ISTEDIĞINIZ kodlanmış UI testini seçin, kısayol menüsünü açın ve ardından **Testleri Seç**' i seçin.

     Otomatikleştirilmiş testler çalışır ve başarılı veya başarısız olup olmadığını gösterir.

    > [!TIP]
    > **Test Gezginini**görüntülemek Için, **Windows** > **Test** ' i seçin ve ardından **Test Gezgini**' ni seçin.

4. **Test Gezgini** sonuçlarında **Çıkış** bağlantısını seçin.

     ![Test Gezgininde çıkış bağlantısı](../test/media/cuit_htmlactionlog1.png)

     Bu, eylem günlüğüne bir bağlantı içeren test için çıktıyı görüntüler.

     ![Kodlanmış UI testinin sonuçları ve çıkış bağlantıları](../test/media/cuit_htmlactionlog2.png)

5. *Uitestactionlog. html* bağlantısını seçin.

     Günlük, Web tarayıcınızda görüntülenir.

     ![Kodlanmış UI testi günlük dosyası](../test/media/cuit_htmlactionlog3.png)

## <a name="see-also"></a>Ayrıca bkz.

- [UI otomasyonunu kullanarak kodunuzu test etme](../test/use-ui-automation-to-test-your-code.md)
- [Nasıl yapılır: Microsoft Visual Studio Testleri çalıştırma](https://msdn.microsoft.com/Library/1a1207a9-2a33-4a1e-a1e3-ddf0181b1046)
