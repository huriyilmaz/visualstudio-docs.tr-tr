---
title: 'Nasıl yapılır: Tanılama Veri Bağdaştırıcısı Oluşturma'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter, creating
ms.assetid: bd7ad36c-54cb-4d2a-9aea-9d10ad98d7ba
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f196c3850c9413a7c68fd1fe67af50273915f249
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589181"
---
# <a name="how-to-create-a-diagnostic-data-adapter"></a>Nasıl kullanılır: Tanılama veri bağdaştırıcısı oluşturma

*Tanılama veri bağdaştırıcısı*oluşturmak için Visual Studio'yu kullanarak bir sınıf kitaplığı oluşturur sunuz ve ardından Visual Studio Enterprise tarafından sağlanan Tanılama Veri Bağdaştırıcısı API'lerini sınıf kitaplığınıza ekleyin. Test çalışması sırasında yükseltilen olayları işlerken, akış veya dosya olarak istediğiniz bilgileri çerçeve tarafından <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink> sağlanana gönderin. Sınava gönderilen akışlar veya <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink> dosyalar, testiniz bittiğinde test sonuçlarına ek olarak depolanır. Bu test sonuçlarından bir hata oluşturursanız [!INCLUDE[mtrlong](../test/includes/mtrlong_md.md)]veya kullandığınızda, dosyalar da hataya bağlanır.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Testlerinizin çalıştırıldığı makineyi veya uygulamanızı test altında çalıştırmak için kullandığınız ortamın bir parçası olan bir makineyi etkileyen bir tanılama veri bağdaştırıcısı oluşturabilirsiniz. Örneğin, testlerin çalıştırıldığı test makinenizde dosya toplamak veya uygulamanız için web sunucusu rolünde hizmet veren makinede dosya toplamak.

Microsoft Test Manager'ı kullanarak veya Visual Studio'u kullanarak test ayarlarınızı oluştururken tanılama veri bağdaştırıcınıza uygun bir ad verebilirsiniz. Test ayarları, testlerinizi çalıştırdığınızda ortamınızda belirli tanısal veri bağdaştırıcılarını çalıştıracak makine rolünü tanımlamanızı sağlar. Test ayarlarınızı oluştururken tanılama veri bağdaştırıcılarınızı da yapılandırabilirsiniz. Örneğin, web sunucunuzdan özel günlükler toplayan bir tanılama veri bağdaştırıcısı oluşturabilirsiniz. Test ayarlarınızı oluşturduğunuzda, bu tanılama veri bağdaştırıcısını bu web sunucusu rolünü gerçekleştiren makine veya makinelerde çalıştırmayı seçebilir ve oluşturulan son üç günlükleri toplamak için test ayarlarınızın yapılandırmasını değiştirebilirsiniz. Test ayarları hakkında daha fazla bilgi için [bkz.](../test/collect-diagnostic-information-using-test-settings.md)

Tanılama veri bağdaştırıcınızın testin o noktasında görevleri gerçekleştirebilmeleri için testlerinizi çalıştırdığınızda olaylar yükseltilir.

> [!IMPORTANT]
> Bu olaylar, özellikle birden çok makinede çalışan testler varsa, farklı iş parçacıkları üzerinde yükseltilebilir. Bu nedenle, olası iş parçacığı sorunlarının farkında olmalı ve yanlışlıkla özel bağdaştırıcının iç verilerini bozmamalısınız. Tanılama veri bağdaştırıcınızın iş parçacığı nın güvenli olduğundan emin olun.

Tanılama veri bağdaştırıcınızı oluştururken kullanabileceğiniz önemli olayların kısmi bir listesi aşağıda veda edilir. Tanılama veri bağdaştırıcısı olaylarının <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents> tam listesi için soyut sınıfa bakın.

|Olay|Açıklama|
|-|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.SessionStart>|Test çalışmanızın başlangıcı|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.SessionEnd>|Test çalışmanızın sonu|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseStart>|Test çalışmasındaki her testin başlangıcı|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseEnd>|Test çalışmasındaki her testin sonu|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestStepStart>|Bir testteki her test adımının başlangıcı|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestStepEnd>|Bir testteki her test adımının sonu|

> [!NOTE]
> El ile sınama tamamlandığında, tanılama veri bağdaştırıcısına başka veri toplama olayı gönderilmez. Bir test yeniden çalıştırıldığında, yeni bir test çalışması tanımlayıcısı olacaktır. Bir kullanıcı bir test sırasında bir testi <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseReset> sıfırlarsa (bu da olayı yükseltir) veya bir test adımı sonucunu değiştirirse, tanılama veri bağdaştırıcısına veri toplama olayı gönderilmez, ancak test çalışması tanımlayıcısı aynı kalır. Bir test çalışmasının sıfırlanıp sıfırlanmadığını belirlemek için tanılama veri bağdaştırıcınızdaki test çalışması tanımlayıcısını izlemeniz gerekir.

Test ayarlarınızı oluştururken yapılandırdığınız bilgileri temel alan bir veri dosyası toplayan tanılama veri bağdaştırıcısı oluşturmak için aşağıdaki yordamı kullanın.

Özel bir yapılandırma düzenleyicisi de dahil olmak üzere tam bir örnek tanılama veri bağdaştırıcısı projesi için tanılama [veri bağdaştırıcısı oluşturmak için örnek projeye](../test/quickstart-create-a-load-test-project.md)bakın.

## <a name="create-and-install-a-diagnostic-data-adapter"></a>Tanılama veri bağdaştırıcısı oluşturma ve yükleme

1. Yeni bir **Sınıf Kitaplığı** projesi oluşturun.

2. Montaj **Microsoft.VisualStudio.QualityTools.ExecutionCommon**ekleyin.

   1. **Çözüm Gezgini'nde,** **Başvurular'ı** sağ tıklatın ve **Başvuru Ekle** komutunu seçin.

   2. **.NET'i** seçin ve **Microsoft.VisualStudio.QualityTools.ExecutionCommon.dll**adresini bulun.

   3. **Tamam'ı**seçin.

3. Montaj **Microsoft.VisualStudio.QualityTools.Common**ekleyin.

   1. **Çözüm Gezgini'nde,** **Başvurular'ı** sağ tıklatın ve **Başvuru Ekle** komutunu seçin.

   2. **/.NET**seçin, **Microsoft.VisualStudio.QualityTools.Common.dll**bulun .

   3. **Tamam'ı**seçin.

4. Sınıf dosyanıza aşağıdaki `using` yönergeleri ekleyin:

   ```csharp
   using Microsoft.VisualStudio.TestTools.Common;
   using Microsoft.VisualStudio.TestTools.Execution;
   using System.Linq;
   using System.Text;
   using System.Xml;
   using System;
   ```

5. <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorTypeUriAttribute> **Tanılama**veri bağdaştırıcınız için sınıfa ekleyerek tanılama veri bağdaştırıcısı olarak tanımlayın, Şirket, **Ürün**ve **Sürüm'ün** yerine Tanılama Veri Bağdaştırıcınız için uygun bilgileri ekleyin:

   ```csharp
   [DataCollectorTypeUri("datacollector://Company/Product/Version")]
   ```

6. Parametreleri <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorFriendlyNameAttribute> Tanılama Veri Bağdaştırıcınız için uygun bilgilerle değiştirerek sınıfa özniteliği ekleyin:

   ```csharp
   [DataCollectorFriendlyName("Collect Log Files", false)]
   ```

    Bu dostu ad, test ayarları etkinliğinde görüntülenir.

   > [!NOTE]
   > Ayrıca, bu <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> veri `Type` bağdaştırıcısı için özel yapılandırma düzenleyicinizi belirtme ve düzenleyici için kullanılacak yardım dosyasını isteğe bağlı olarak belirtme yi de ekleyebilirsiniz.
   >
   > Her zaman etkin <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorEnabledByDefaultAttribute> olması gerektiğini belirtmek için de uygulayabilirsiniz.

7. Tanılama veri bağdaştırıcısı sınıfınız <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector> aşağıdaki gibi sınıftan devralınmalıdır:

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

9. Yöntemi <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector.Initialize*> ve **Elden Çıkarma** yöntemini ekleyin. `Initialize` Yöntemde, veri lavabosu, test ayarlarından herhangi bir yapılandırma verileri başlatılması ve kullanmak istediğiniz olay işleyicileri aşağıdaki gibi kaydedin:

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

10. Test sırasında oluşturulan günlük dosyasını toplamak için aşağıdaki olay işleyicisi kodunu ve özel yöntemi kullanın:

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

     Bu dosyalar test sonuçlarına eklenir. Bu test sonuçlarından bir hata oluşturursanız [!INCLUDE[mtrlong](../test/includes/mtrlong_md.md)]veya kullandığınızda, dosyalar da hataya eklenir.

     Test ayarlarınızda kullanmak üzere veri toplamak için kendi düzenleyicinizi kullanmak istiyorsanız, [bkz.](../test/quickstart-create-a-load-test-project.md)

11. Bir test, kullanıcının test ayarlarında yapılandırdığınız ayarı temel alınca tamamlandığında bir günlük dosyası toplamak için bir *App.config* dosyası oluşturmanız ve çözüme eklemeniz gerekir. Bu dosya aşağıdaki biçime sahiptir ve tanılama veri bağdaştırıcınızın tanımlaması için URI'yi içermelidir. Gerçek değerleri "Şirket/Ürün Adı/Sürümü" yerine ait.

    > [!NOTE]
    > Tanılama veri bağdaştırıcınız için herhangi bir bilgi yapılandırmanız gerekmiyorsa, yapılandırma dosyası oluşturmanız gerekmez.

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
    > Varsayılan yapılandırma öğesi, gereksinim duyduğunuz verileri içerebilir. Kullanıcı tanılama veri bağdaştırıcısını test ayarlarında yapılandırmazsa, varsayılan veriler yürütüldüğünde tanılama verisi bağdaştırıcınıza aktarılır. `<DefaultConfigurations>` Bölüme eklediğiniz XML'nin bildirilen şemanın bir parçası olması olası olmadığından, oluşturduğu XML hatalarını yok sayabilirsiniz.
    >
    > Yükleme dizininize göre aşağıdaki yoldaki yapılandırma dosyalarının diğer örnekleri de vardır: *Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies\DataCollectors*.

     Test ayarlarınızı, testlerinizi çalıştırdığınızda bir ortamı kullanacak şekilde yapılandırma hakkında daha fazla bilgi için [bkz.](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)

     Yapılandırma dosyasını yükleme hakkında daha fazla bilgi için [bkz: Özel tanılama veri bağdaştırıcısı yükleme](../test/quickstart-create-a-load-test-project.md)

12. Tanılama veri bağdaştırıcısı derlemenizi oluşturmak için çözümünüzü oluşturun.

13. Özel düzenleyicinizi yükleme hakkında daha fazla bilgi için [bkz: Özel tanılama veri bağdaştırıcısı yükleyin.](../test/quickstart-create-a-load-test-project.md)

14. Test ayarlarınızı, testlerinizi çalıştırdığınızda bir ortamı kullanacak şekilde yapılandırma hakkında daha fazla bilgi için [bkz.](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)

15. Tanılama veri bağdaştırıcınızı seçmek için önce varolan bir test ayarlarını seçmeniz veya Microsoft Test Manager veya Visual Studio'dan yeni bir tane oluşturmanız gerekir. Bağdaştırıcı, test ayarlarınızın **Veri ve Tanılama** sekmesinde sınıfa atadığınız kolay adla görüntülenir.

16. Bu test ayarlarını etkin olacak şekilde ayarlayın. Test ayarları hakkında daha fazla bilgi için [bkz.](../test/collect-diagnostic-information-using-test-settings.md)

17. Tanılama veri adaptörünüz seçili test ayarlarını kullanarak testlerinizi çalıştırın.

    Belirttiğiniz veri dosyası test sonuçlarınıza eklenir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorTypeUriAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorFriendlyNameAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorEnabledByDefaultAttribute>
- [Test ayarlarını kullanarak tanılama bilgilerini toplama](../test/collect-diagnostic-information-using-test-settings.md)
- [El ile yapılan testlerde tanılama verileri toplama (Azure Test Planları)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)
- [Test ederken tanılama verileri toplama (Azure Test Planları)](/azure/devops/test/collect-diagnostic-data?view=vsts)
- [Nasıl kullanılır: Tanılama veri bağdaştırıcınız için veriler için özel bir düzenleyici oluşturma](../test/quickstart-create-a-load-test-project.md)
