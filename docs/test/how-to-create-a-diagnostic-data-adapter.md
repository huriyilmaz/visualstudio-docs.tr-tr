---
title: 'Nasıl yapılır: Tanılama Veri Bağdaştırıcısı Oluşturma'
description: Tanılama Veri Bağdaştırıcısı API'lerini kullanarak bir sınıf kitaplığı oluşturarak Visual Studio veri bağdaştırıcısı oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Diagnostic Data Adapter, creating
ms.assetid: bd7ad36c-54cb-4d2a-9aea-9d10ad98d7ba
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: cea308c8fd3734803663d597f2e23205a6848b70
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122033245"
---
# <a name="how-to-create-a-diagnostic-data-adapter"></a>Nasıl kullanılır: Tanılama veri bağdaştırıcısı oluşturma

Tanılama veri *bağdaştırıcısı oluşturmak için,* Visual Studio kullanarak bir sınıf kitaplığı oluşturun ve Visual Studio Enterprise tarafından sağlanan Tanılama Veri Bağdaştırıcısı API'lerini sınıf kitaplığınıza ekleyin. Test çalıştırması sırasında sınanan olayları işleme sırasında, çerçeve tarafından sağlanan bir akış veya dosya <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink> olarak istediğiniz tüm bilgileri gönderin. 'a gönderilen akışlar veya dosyalar, testiniz tamamlandığı zaman <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink> test sonuçlarına ek olarak depolanır. Bu test sonuçlarından bir hata sanız veya [!INCLUDE[mtrlong](../test/includes/mtrlong_md.md)] kullanıyorsanız, dosyalar da hataya bağlıdır.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Testlerinizi çalıştıracak makineyi etkileyen bir tanılama veri bağdaştırıcısı veya test altında uygulama çalıştırmak için kullanmakta olduğu ortamın bir parçası olan bir makine oluşturabilirsiniz. Örneğin, test makinenize testleri çalıştıran dosyaları toplama veya uygulamanıza web sunucusu rolünde hizmet veren makinede dosyaları toplama.

Tanılama veri bağdaştırıcınıza, Visual Studio veya Microsoft Test Yöneticisi kullanarak (Visual Studio 2017'de kullanım dışı) kullanarak test ayarlarınızı oluşturmanızı gösteren kolay Visual Studio veebilirsiniz. Test ayarları, testlerinizi çalıştırarak ortamınıza özgü tanılama veri bağdaştırıcılarını hangi makine rolünün çalıştıracaklarını tanımlamanızı sağlar. Test ayarlarınızı oluşturmadan tanılama veri bağdaştırıcılarınızı da yapılandırabilirsiniz. Örneğin, web sunucunuzdan özel günlükler toplayan bir tanılama veri bağdaştırıcısı oluşturabilirsiniz. Test ayarlarınızı oluşturulduğunda, bu tanılama veri bağdaştırıcısını bu web sunucusu rolünü gerçekleştiren makinede veya makinelerde çalıştırmayı seçebilirsiniz ve test ayarlarınızın yapılandırmasını yalnızca oluşturulan son üç günlüğü toplayan şekilde değiştirebilirsiniz. Test ayarları hakkında daha fazla bilgi için [bkz. Test ayarlarını kullanarak tanılama bilgilerini toplama.](../test/collect-diagnostic-information-using-test-settings.md)

Tanılama veri bağdaştırıcınız testin o noktasında görevler gerçekleştiresin diye testlerinizi çalıştırarak olaylar ortaya çıkar.

> [!IMPORTANT]
> Bu olaylar, özellikle birden çok makinede çalışan testlere sahip olduğunda farklı iş parçacıklarında ortaya çıkar. Bu nedenle, olası iş parçacığı oluşturma sorunlarının farkında olmak ve özel bağdaştırıcının iç verilerini yanlışlıkla bozmamanız gerekir. Tanılama veri bağdaştırıcınızı iş parçacığı güvenli olduğundan emin olun.

Tanılama veri bağdaştırıcınızı ekleyebilirsiniz anahtar olaylarının kısmi bir listesi aşağıdadır. Tanılama veri bağdaştırıcısı olaylarının tam listesi için soyut sınıfına <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents> bakın.

|Olay|Açıklama|
|-|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.SessionStart>|Test çalıştırmanızı başlatma|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.SessionEnd>|Test çalıştırmanızı sona erer|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseStart>|Test çalıştırması içinde her testin başlangıcı|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseEnd>|Test çalıştırması içinde her testin sonu|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestStepStart>|Testte her test adımının başlangıcı|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestStepEnd>|Testte her test adımının sonu|

> [!NOTE]
> El ile test tamamlandığında, tanılama veri bağdaştırıcısına başka veri toplama olayları gönderilmez. Bir test yeniden çalıştır geldiğinde, yeni bir test çalışma tanımlayıcısına sahip olur. Bir kullanıcı test sırasında bir testi sıfırlarsa (olayı başlatan) veya test adımı sonucunu değiştirirse, tanılama veri bağdaştırıcısına veri toplama olayı gönderilmez, ancak test çalışma tanımlayıcısı aynı <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseReset> kalır. Bir test çalışma sıfırlaması olup olmadığını belirlemek için, tanılama veri bağdaştırıcısında test çalışma tanımlayıcısı izlemeniz gerekir.

Test ayarlarınızı oluşturma sırasında yapılandırılan bilgilere dayalı bir veri dosyası toplayan tanılama veri bağdaştırıcısı oluşturmak için aşağıdaki yordamı kullanın.

Özel yapılandırma düzenleyicisi de dahil olmak üzere tam bir örnek tanılama veri bağdaştırıcısı projesi için bkz. Tanılama [veri bağdaştırıcısı oluşturmak için örnek proje.](../test/quickstart-create-a-load-test-project.md)

## <a name="create-and-install-a-diagnostic-data-adapter"></a>Tanılama veri bağdaştırıcısı oluşturma ve yükleme

1. Yeni bir Sınıf **Kitaplığı projesi** oluşturun.

2. **cutionCommonMicrosoft.VisualStudio.QualityTools.Exeekleyin.**

   1. Bu **Çözüm Gezgini,** Başvurular'a **sağ tıklayın** ve Başvuru Ekle **komutunu** seçin.

   2. **.NET'i** seçin **ve** Microsoft.VisualStudio.QualityTools.ExecutionCommon.dll.

   3. **Tamam'ı seçin.**

3. **Microsoft.VisualStudio.QualityTools.Common derlemeyi ekleyin.**

   1. Bu **Çözüm Gezgini,** Başvurular'a **sağ tıklayın** ve Başvuru Ekle **komutunu** seçin.

   2. **/.NET'i** seçin, **Microsoft.VisualStudio.QualityTools.Common.dll.**

   3. **Tamam'ı seçin.**

4. Sınıf `using` dosyanıza aşağıdaki yönergeleri ekleyin:

   ```csharp
   using Microsoft.VisualStudio.TestTools.Common;
   using Microsoft.VisualStudio.TestTools.Execution;
   using System.Linq;
   using System.Text;
   using System.Xml;
   using System;
   ```

5. Tanılama veri bağdaştırıcınızı tanılama veri bağdaştırıcısı olarak tanımlamak için sınıfa ekleyin ve Şirket, Ürün ve Sürüm yerine Tanılama Veri Bağdaştırıcınız için uygun <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorTypeUriAttribute> bilgileri ekleyin:   

   ```csharp
   [DataCollectorTypeUri("datacollector://Company/Product/Version")]
   ```

6. parametresini <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorFriendlyNameAttribute> Tanılama Veri Bağdaştırıcınız için uygun bilgilerle değiştirerek özniteliğini sınıfına ekleyin:

   ```csharp
   [DataCollectorFriendlyName("Collect Log Files", false)]
   ```

    Bu kolay ad, test ayarları etkinliğinde görüntülenir.

   > [!NOTE]
   > Ayrıca, bu veri bağdaştırıcısı için özel yapılandırma düzenleyicinizi belirtmek ve isteğe bağlı olarak düzenleyici için kullanmak üzere yardım dosyasını <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> belirtmek için de `Type` ekebilirsiniz.
   >
   > Ayrıca her zaman <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorEnabledByDefaultAttribute> etkinleştirilmesi gerektiğini belirtmek için de uygulayabilirsiniz.

7. Tanılama veri bağdaştırıcısı sınıfınız aşağıdaki gibi <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector> sınıfından devralmalı:

   ```csharp
   public class MyDiagnosticDataAdapter : DataCollector
   ```

8. Yerel değişkenleri aşağıdaki gibi ekleyin:

   ```csharp
   private DataCollectionEvents dataEvents;
   private DataCollectionLogger dataLogger;
   private DataCollectionSink dataSink;
   private XmlElement configurationSettings;
   ```

9. yöntemini <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector.Initialize*> ve **dispose yöntemini** ekleyin. yönteminde, veri havuzlarını ve test ayarlarından tüm yapılandırma verilerini başlatacak ve kullanmak istediğiniz `Initialize` olay işleyicilerini aşağıdaki gibi kaydedebilirsiniz:

    ```csharp
    public override void Initialize(
        XmlElement configurationElement,
        DataCollectionEvents events,
        DataCollectionSink sink,
        DataCollectionLogger logger,
        DataCollectionEnvironmentContext environmentContext)
    {
           dataEvents = events;  // The test events
           dataLogger = logger;  // The error and warning log
           dataSink = sink;      // Saves collected data
           // Configuration from the test settings
           configurationSettings = configurationElement;

           // Register common events for the data collector
           // Not all of the events are used in this class
        dataEvents.SessionStart +=
            new EventHandler<SessionStartEventArgs>(OnSessionStart);
        dataEvents.SessionEnd +=
            new EventHandler<SessionEndEventArgs>(OnSessionEnd);
        dataEvents.TestCaseStart +=
            new EventHandler<TestCaseStartEventArgs>(OnTestCaseStart);
        dataEvents.TestCaseEnd +=
            new EventHandler<TestCaseEndEventArgs>(OnTestCaseEnd);
    }

    public override void Dispose(bool disposing)
    {
        if (disposing)
        {
            // Unregister the registered events
            dataEvents.SessionStart -=
                new EventHandler<SessionStartEventArgs>(OnSessionStart);
            dataEvents.SessionEnd -=
                new EventHandler<SessionEndEventArgs>(OnSessionEnd);
            dataEvents.TestCaseStart -=
                new EventHandler<TestCaseStartEventArgs>(OnTestCaseStart);
            dataEvents.TestCaseEnd -=
                new EventHandler<TestCaseEndEventArgs>(OnTestCaseEnd);
        }
    }
    ```

10. Test sırasında oluşturulan günlük dosyasını toplamak için aşağıdaki olay işleyicisi kodunu ve özel yöntemini kullanın:

    ```csharp
    public void OnTestCaseEnd(sender, TestCaseEndEventArgs e)
    {
        // Get any files to be collected that are
        // configured in your test settings
        List<string> files = getFilesToCollect();

        // For each of the files, send the file to the data sink
        // which will attach it to the test results or to a bug
        foreach (string file in files)
        {
            dataSink.SendFileAsync(e.Context, file, false);
        }
    }

    // A private method that returns the file names
    private List<string> getFilesToCollect()
    {
        // Get a namespace manager with our namespace
        XmlNamespaceManager nsmgr =
            new XmlNamespaceManager(
                configurationSettings.OwnerDocument.NameTable);
        nsmgr.AddNamespace("ns",
            "http://MyCompany/schemas/MyDataCollector/1.0");

        // Find all of the "File" elements under our configuration
        XmlNodeList files =
            configurationSettings.SelectNodes(
                "//ns:MyDataCollector/ns:File");

        // Build the list of files to collect from the
        // "FullPath" attributes of the "File" nodes.
        List<string> result = new List<string>();
        foreach (XmlNode fileNode in files)
        {
            XmlAttribute pathAttribute =
                fileNode.Attributes["FullPath"];
            if (pathAttribute != null &&
                !String.IsNullOrEmpty(pathAttribute.Value))
            {
                result.Add(pathAttribute.Value);
            }
        }

        return result;
    }
    ```

     Bu dosyalar test sonuçlarına iliştirilmiş. Bu test sonuçlarından bir hata sanız veya [!INCLUDE[mtrlong](../test/includes/mtrlong_md.md)] kullanıyorsanız, dosyalar da hataya eklenir.

     Test ayarlarınıza kullanmak üzere veri toplamak için kendi düzenleyicinizi kullanmak için bkz. Nasıl kullanılır: Tanılama veri bağdaştırıcınız için veriler için [özel düzenleyici oluşturma.](../test/quickstart-create-a-load-test-project.md)

11. Kullanıcının test ayarlarında yapılandırmış olduğu yapılandırmalara göre test sona ede bir  günlük dosyası toplamak için birApp.configdosyası oluşturmanız ve bunu çözümünüze eklemeniz gerekir. Bu dosya aşağıdaki biçimdedir ve tanılama veri bağdaştırıcınızı tanımlamak için URI'yi içermesi gerekir. "Company/ProductName/Version" yerine gerçek değerleri yazın.

    > [!NOTE]
    > Tanılama veri bağdaştırıcınız için herhangi bir bilgi yapılandırmanız gerek yoksa, yapılandırma dosyası oluşturmanıza gerek olmaz.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <configuration>
      <configSections>
        <section name="DataCollectorConfiguration" type="Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationSection, Microsoft.VisualStudio.QualityTools.ExecutionCommon, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a "/>
      </configSections>
      <DataCollectorConfiguration xmlns="http://microsoft.com/schemas/VisualStudio/TeamTest/2010">
        <DataCollector typeUri="datacollector://MyCompany/MyProduct/1.0">
          <DefaultConfiguration>
            <!-- Your default config settings -->
            <Binaries>
              <Binary FullPath="C:\Example\Example.dll"/>
              <Binary FullPath="\\Server2\Example2.dll"/>
            </Binaries>
            <Symbols>
              <Symbol FullPath="\\ExampleServer\ExampleSymbol.pdb"/>
            </Symbols>
          </DefaultConfiguration>
        </DataCollector>
      </DataCollectorConfiguration>
    </configuration>
    ```

    > [!NOTE]
    > Varsayılan yapılandırma öğesi, size gereken tüm verileri içerebilir. Kullanıcı, tanılama veri bağdaştırıcısını test ayarlarında yapılandırmazsanız, varsayılan veriler yürütülürken tanılama veri bağdaştırıcınıza geçirülür. bölümüne ekley istediğiniz XML'in bildirilen şemanın bir parçası olma olasılığı düşük olduğundan, bu xml `<DefaultConfigurations>` hatalarının neden olduğu hataları yoksayabilirsiniz.
    >
    > Yükleme dizininize bağlı olarak aşağıdaki yolda yapılandırma dosyalarının başka örnekleri de vardır: *Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies\DataCollectors*.

     Testlerinizi çalıştırarak ortam kullanmak üzere test ayarlarınızı yapılandırma hakkında daha fazla bilgi için bkz. El ile yapılan testlerde tanılama [verileri toplama (Azure Test Plans).](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts&preserve-view=true)

     Yapılandırma dosyasını yükleme hakkında daha fazla bilgi için [bkz. Nasıl kullanılır: Özel tanılama veri bağdaştırıcısı yükleme](../test/quickstart-create-a-load-test-project.md)

12. Tanılama veri bağdaştırıcısı derlemenizi oluşturmak için çözümlerinizi oluşturun.

13. Özel düzenleyicinizi yükleme hakkında daha fazla bilgi için [bkz. Nasıl kullanılır: Özel tanılama veri bağdaştırıcısı yükleme.](../test/quickstart-create-a-load-test-project.md)

14. Testlerinizi çalıştırarak ortam kullanmak üzere test ayarlarınızı yapılandırma hakkında daha fazla bilgi için bkz. El ile yapılan testlerde tanılama [verileri toplama (Azure Test Plans).](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts&preserve-view=true)

15. Tanılama veri bağdaştırıcınızı seçmek için önce mevcut test ayarlarını seçmeniz veya Visual Studio veya Microsoft Test Yöneticisi'den yeni bir tane oluşturmanız gerekir (Visual Studio 2017'de kullanım dışıdır). Bağdaştırıcı, test **ayarlarınızın Veri** ve Tanılama sekmesinde, sınıfına atadığı kolay adla görüntülenir.

16. Bu test ayarlarını etkin olarak ayarlayın. Test ayarları hakkında daha fazla bilgi için [bkz. Test ayarlarını kullanarak tanılama bilgilerini toplama.](../test/collect-diagnostic-information-using-test-settings.md)

17. Tanılama veri bağdaştırıcınız seçiliyken test ayarlarını kullanarak testlerinizi çalıştırın.

    Belirttiğiniz veri dosyası test sonuçlarınıza eklenmiş.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorTypeUriAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorFriendlyNameAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorEnabledByDefaultAttribute>
- [Test ayarlarını kullanarak tanılama bilgilerini toplama](../test/collect-diagnostic-information-using-test-settings.md)
- [Tanılama verilerini el ile yapılan testlerde toplama (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts&preserve-view=true)
- [Test sırasında tanılama verilerini toplama (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts&preserve-view=true)
- [Nasıl kullanılır: Tanılama veri bağdaştırıcınız için veriler için özel düzenleyici oluşturma](../test/quickstart-create-a-load-test-project.md)
