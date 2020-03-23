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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591222"
---
# <a name="analyzing-coded-ui-tests-using-coded-ui-test-logs"></a>Kodlanmış UI test günlüklerini kullanarak kodlanmış UI testlerini çözümleme

Kodlanmış Kullanıcı Bira Test günlükleri filtreve kodlanmış Kullanıcı Bira test çalışır hakkında önemli bilgileri kaydedin. Günlükler, hata ayıklama sorunlarını hızlı bir şekilde ele alma olanağı sağlayan bir biçimde sunulur.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="step-1-enable-logging"></a>Adım 1: Günlük kaydetmeyi etkinleştirme

Senaryonuza bağlı olarak, günlüğü etkinleştirmek için aşağıdaki yöntemlerden birini kullanın:

- Test projenizde *App.config* dosyası yoksa:

   1. Testi çalıştırdığınızda hangi *QTAgent\*.exe* işleminin başlatıldığını belirleyin. Bunu yapmanın bir yolu, Windows Görev **Yöneticisi'ndeki** **Ayrıntılar** sekmesini izlemektir.

   2. *%ProgramFiles(x86)%\Microsoft\\\<Visual Studio sürümünden \\ \<* karşılık gelen *.config* dosyasını açın>\Common7\IDE klasörüne>. Örneğin, çalışan işlem *QTAgent_40.exe*ise, açık *QTAgent_40.exe.config*.

   2. **EqtTraceLevel** değerini istediğiniz günlük düzeyine değiştirin.

      ```xml
      <!-- You must use integral values for "value".
           Use 0 for off, 1 for error, 2 for warn, 3 for info, and 4 for verbose. -->
      <add name="EqtTraceLevel" value="4" />
      ```

   3. Dosyayı kaydedin.

- Test projenizde bir *App.config* dosyası varsa:

  - Projedeki *App.config* dosyasını açın ve yapılandırma düğümünün altına aşağıdaki kodu ekleyin:

    ```xml
    <system.diagnostics>
      <switches>
        <add name="EqtTraceLevel" value="4" />
      </switches>
    </system.diagnostics>`
    ```

- Test kodunun kendisinden günlüğe kaydetmeyi etkinleştirin:

   ```csharp
   Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.LoggerOverrideState = HtmlLoggerState.AllActionSnapshot;
   ```

## <a name="step-2-run-your-coded-ui-test-and-view-the-log"></a>Adım 2: Kodlanmış UI testinizi çalıştırın ve günlüğü görüntüleyin

*QTAgent\*.exe.config* dosyasında yapılan değişikliklerle birlikte kodlanmış bir ui testi çalıştırdığınızda, **Test Gezgini** sonuçlarında bir çıktı bağlantısı görürsünüz. Günlük dosyaları yalnızca test başarısız olduğunda değil, aynı zamanda izleme düzeyi **ayrıntılı**olarak ayarlandığında başarılı testler için de üretilir.

1. **Test** menüsünde **Windows'u** seçin ve ardından **Gezgini Test'i**seçin.

2. **Yapı** menüsünde **Çözüm Oluştur'u**seçin.

3. **Test Gezgini'nde,** çalıştırmak istediğiniz kodlanmış UI testini seçin, kısayol menüsünü açın ve ardından Testleri Seç'i **çalıştır'ı**seçin.

     Otomatik testler çalışır ve geçtiklerini veya başarısız olup olmadıklarını gösterir.

    > [!TIP]
    > Test **Gezgini'ni**görüntülemek**için, Windows** **Test'i** > seçin ve ardından **Sına Gezgini'ni**seçin.

4. **Test Gezgini** sonuçlarında **Çıktı** bağlantısını seçin.

     ![Test Gezgini'ndeki çıkış bağlantısı](../test/media/cuit_htmlactionlog1.png)

     Bu, eylem günlüğüne bir bağlantı içeren test çıktısını görüntüler.

     ![Kodlanmış UI testinden sonuçlar ve çıkış bağlantıları](../test/media/cuit_htmlactionlog2.png)

5. *UITestActionLog.html* bağlantısını seçin.

     Günlük web tarayıcınızda görüntülenir.

     ![Kodlanmış UI test günlüğü dosyası](../test/media/cuit_htmlactionlog3.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)
- [Nasıl çalıştırılır: Microsoft Visual Studio'dan testler çalıştırma](https://msdn.microsoft.com/Library/1a1207a9-2a33-4a1e-a1e3-ddf0181b1046)
