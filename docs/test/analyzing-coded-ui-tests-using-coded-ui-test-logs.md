---
title: Kodlanmış UI Test Günlüklerini Kullanarak Kodlanmış UI Testlerini Çözümleme
description: Kodlanmış UI test çalıştırmaları hakkında önemli bilgileri filtreleten ve kaydeden kodlanmış UI test günlükleri hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 6459b6d5d91980f8963d45368695b0e6e2f5c0a9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092702"
---
# <a name="analyzing-coded-ui-tests-using-coded-ui-test-logs"></a>Kodlanmış UI test günlüklerini kullanarak kodlanmış UI testlerini analiz etme

Kodlanmış UI test günlükleri, kodlanmış UI test çalıştırmalarınızı filtreler ve önemli bilgileri kaydeder. Günlükler, sorunların hızla hata ayıklamasını sağlayan bir biçimde sunulmaktadır.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="step-1-enable-logging"></a>1. Adım: Günlüğü etkinleştirme

Senaryoya bağlı olarak, günlüğü etkinleştirmek için aşağıdaki yöntemlerden birini kullanın:

- Test projeniz içinde *App.config* dosya yoksa:

   1. Testini *çalıştırarak \*.exehangi QTAgent* işleminin başlat olduğunu belirleme. Bunu yapma yollarından biri, Görev **Yöneticisi'nde** ayrıntılar Windows **izlemektir.**

   2. *%ProgramFiles(x86)%\Microsoft Visual Studio \\ \<version> \\ \<edition> \Common7\IDE* klasöründen karşılık gelen.configdosyasını açın.  Örneğin, çalışan işlemQTAgent_40.exe *ise,* *QTAgent_40.exe.config.*

   2. **EqtTraceLevel** değerini istediğiniz günlük düzeyiyle değiştirme.

      ```xml
      <!-- You must use integral values for "value".
           Use 0 for off, 1 for error, 2 for warn, 3 for info, and 4 for verbose. -->
      <add name="EqtTraceLevel" value="4" />
      ```

   3. Dosyayı kaydedin.

- Test projenize bir *App.config* dosyası varsa:

  - Projedeki *App.config* dosyasını açın ve yapılandırma düğümü altına aşağıdaki kodu ekleyin:

    ```xml
    <system.diagnostics>
      <switches>
        <add name="EqtTraceLevel" value="4" />
      </switches>
    </system.diagnostics>`
    ```

- Test kodundan günlüğe kaydetmeyi etkinleştirin:

   ```csharp
   Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.LoggerOverrideState = HtmlLoggerState.AllActionSnapshot;
   ```

## <a name="step-2-run-your-coded-ui-test-and-view-the-log"></a>2. Adım: Kodlanmış UI testini çalıştırma ve günlüğü görüntüleme

QTAgent.exe.configdosyasında yapılan değişikliklerle *\* kodlanmış* bir UI **testi çalıştırsanız, Test** Gezgini sonuçlarında bir çıkış bağlantısı görüyorsunuz. Günlük dosyaları yalnızca test başarısız olduğunda değil, izleme düzeyi ayrıntılı olarak ayarlanmış başarılı testler **için de üretir.**

1. Test **menüsünde,** Test  Gezgini Windows'ni **seçin.**

2. Derleme menüsünde **Çözümü** **Derleme'yi seçin.**

3. **Test Gezgini'nde** çalıştırmak istediğiniz kodlanmış UI testini seçin, kısayol menüsünü açın ve Ardından Testleri **Çalıştır'ı seçin.**

     Otomatikleştirilmiş testler çalıştırıldı ve başarılı veya başarısız olup olduklarını gösteriyor.

    > [!TIP]
    > Test **Gezgini'ni görüntülemek** için **Test**  >  **Gezgini'ni Windows** ve ardından **Test Gezgini'ni seçin.**

4. Test **Gezgini sonuçlarında** Çıkış **bağlantısını** seçin.

     ![Test Gezgini'nde çıkış bağlantısı](../test/media/cuit_htmlactionlog1.png)

     Bu işlem, eylem günlüğünün bağlantısını içeren test çıkışını görüntüler.

     ![Kodlanmış UI testinde sonuçlar ve çıkış bağlantıları](../test/media/cuit_htmlactionlog2.png)

5. UITestActionLog.htm *l bağlantısını* seçin.

     Günlük web tarayıcınızda görüntülenir.

     ![Kodlanmış UI test günlüğü dosyası](../test/media/cuit_htmlactionlog3.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)
- [Nasıl Microsoft Visual Studio: Microsoft Visual Studio](/previous-versions/ms182470(v=vs.140))