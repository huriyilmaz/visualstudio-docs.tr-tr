---
title: 'Nasıl yapılır: Tanılama Veri Bağdaştırıcısı Oluşturma'
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Diagnostic Data Adapter, creating
ms.assetid: bd7ad36c-54cb-4d2a-9aea-9d10ad98d7ba
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 43519a96e0718a0864065864d9dd4fbd2ac16b23
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85288084"
---
# <a name="how-to-create-a-diagnostic-data-adapter"></a>Nasıl yapılır: tanılama veri bağdaştırıcısı oluşturma

Bir *Tanılama veri bağdaştırıcısı*oluşturmak Için, Visual Studio 'yu kullanarak bir sınıf kitaplığı oluşturun ve ardından Visual Studio Enterprise tarafından sunulan tanılama veri bağdaştırıcısı API 'lerini sınıf kitaplığınıza eklersiniz. Test çalıştırması sırasında oluşturulan olayları işlerken, bir akış veya bir dosya olarak istediğiniz tüm bilgileri Framework tarafından verilen bir dosya olarak gönderin <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink> . ' A gönderilen akışlar veya dosyalar, <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink> testiniz tamamlandığında test sonuçlarına ek olarak depolanır. Bu test sonuçlarından bir hata oluşturursanız veya kullandığınızda [!INCLUDE[mtrlong](../test/includes/mtrlong_md.md)] , dosyalar hataya da bağlanır.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Testlerinizin çalıştırıldığı makineyi etkileyen bir tanılama veri bağdaştırıcısı veya test altında uygulamanızı çalıştırmak için kullandığınız ortamın parçası olan bir makine oluşturabilirsiniz. Örneğin, test makinenizde testlerin çalıştırıldığı veya uygulama için Web sunucusu rolünde hizmet veren makinedeki dosyaları toplayan dosyaları toplama.

Tanılama veri bağdaştırıcınıza, Visual Studio veya Microsoft Test Yöneticisi (Visual Studio 2017 ' de kullanım dışı) kullanarak test ayarlarınızı oluşturduğunuzda görüntüleyen kolay bir ad verebilirsiniz. Test ayarları, testlerinizi çalıştırdığınızda ortamınızdaki belirli tanılama veri bağdaştırıcılarını hangi makine rolünün çalıştıracağınızı tanımlamanızı sağlar. Tanılama veri bağdaştırıcılarınızı, test ayarlarınızı oluştururken da yapılandırabilirsiniz. Örneğin, Web sunucunuzdaki özel günlükleri toplayan bir tanılama veri bağdaştırıcısı oluşturabilirsiniz. Test ayarlarınızı oluşturduğunuzda, bu Web sunucusu rolünü gerçekleştiren makinede veya makinelerde Bu tanılama veri bağdaştırıcısını çalıştırmayı seçebilir ve yalnızca oluşturulan son üç günlüğü toplamak için test ayarlarınızın yapılandırmasını değiştirebilirsiniz. Test ayarları hakkında daha fazla bilgi için bkz. [test ayarlarını kullanarak tanılama bilgilerini toplama](../test/collect-diagnostic-information-using-test-settings.md).

Tanılama veri bağdaştırıcınızın testte o noktada görev gerçekleştirebilmesi için testlerinizi çalıştırdığınızda olaylar tetiklenir.

> [!IMPORTANT]
> Bu olaylar, özellikle birden çok makine üzerinde çalışan testleriniz varsa farklı iş parçacıklarında oluşturulabilir. Bu nedenle, olası iş parçacığı sorunlarından haberdar olmanız ve yanlışlıkla özel bağdaştırıcının iç verilerini bozmamalıdır. Tanılama veri bağdaştırıcınızın iş parçacığı açısından güvenli olduğundan emin olun.

Aşağıda, tanılama veri bağdaştırıcınızı oluştururken kullanabileceğiniz önemli olayların kısmi bir listesi verilmiştir. Tanılama veri bağdaştırıcısı olaylarının tamamı listesi için bkz <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents> . soyut sınıf.

|Olay|Description|
|-|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.SessionStart>|Test çalıştıralım başlangıcı|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.SessionEnd>|Test çalıştıralım bitişi|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseStart>|Test çalıştırmasında her bir testin başlangıcı|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseEnd>|Test çalıştırmasında her testin sonu|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestStepStart>|Testteki her test adımını başlatma|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestStepEnd>|Testteki her test adımının sonu|

> [!NOTE]
> El ile test tamamlandığında, tanılama veri bağdaştırıcısına daha fazla veri toplama olayı gönderilmez. Bir test yeniden çalıştırıldığında, yeni bir test çalışması tanımlayıcısına sahip olur. Bir Kullanıcı bir test sırasında (olayı oluşturan) bir testi sıfırlarsa <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseReset> veya bir test adımı sonucunu değiştirdiğinde, tanılama veri bağdaştırıcısına veri toplama olayı gönderilmez, ancak test çalışması tanımlayıcısı aynı kalır. Bir test çalışmasının sıfırlanıp sıfırlanmadığını öğrenmek için tanılama veri bağdaştırıcınızda test çalışması tanıtıcısını izlemeniz gerekir.

Test ayarlarınızı oluştururken yapılandırdığınız bilgileri temel alan bir veri dosyası toplayan tanılama veri bağdaştırıcısı oluşturmak için aşağıdaki yordamı kullanın.

Özel bir yapılandırma Düzenleyicisi de dahil olmak üzere, tüm örnek bir tanılama veri bağdaştırıcısı projesi için bkz. [Tanılama veri bağdaştırıcısı oluşturmak Için örnek proje](../test/quickstart-create-a-load-test-project.md).

## <a name="create-and-install-a-diagnostic-data-adapter"></a>Tanılama veri bağdaştırıcısı oluşturma ve yüklemeyi

1. Yeni bir **sınıf kitaplığı** projesi oluşturun.

2. **Microsoft.VisualStudio.QualityTools.ExecutionCommon**derlemesini ekleyin.

   1. **Çözüm Gezgini**' de, **Başvurular** ' a sağ tıklayın ve **Başvuru Ekle** komutunu seçin.

   2. **.Net** ' i seçin ve **Microsoft.VisualStudio.QualityTools.ExecutionCommon.dll**bulun.

   3. **Tamam ' ı**seçin.

3. **Microsoft. VisualStudio. QualityTools. Common**derlemesini ekleyin.

   1. **Çözüm Gezgini**' de, **Başvurular** ' a sağ tıklayın ve **Başvuru Ekle** komutunu seçin.

   2. **/.Net**' i seçin, **Microsoft.VisualStudio.QualityTools.Common.dll**bulun.

   3. **Tamam ' ı**seçin.

4. Aşağıdaki `using` yönergeleri sınıf dosyanıza ekleyin:

   ```csharp
   using Microsoft.VisualStudio.TestTools.Common;
   using Microsoft.VisualStudio.TestTools.Execution;
   using System.Linq;
   using System.Text;
   using System.Xml;
   using System;
   ```

5. Tanılama veri bağdaştırıcısı <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorTypeUriAttribute> olarak tanımlamak için tanılama veri bağdaştırıcınız için sınıfına ekleyin; **Şirket**, **ürün**ve **sürümü** , tanılama veri bağdaştırıcınız için uygun bilgilerle değiştirin:

   ```csharp
   [DataCollectorTypeUri("datacollector://Company/Product/Version")]
   ```

6. Parametreleri, <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorFriendlyNameAttribute> Tanılama veri bağdaştırıcınız için uygun bilgilerle değiştirerek sınıfına ekleyin:

   ```csharp
   [DataCollectorFriendlyName("Collect Log Files", false)]
   ```

    Bu kolay ad, test ayarları etkinliğinde görüntülenir.

   > [!NOTE]
   > Ayrıca, <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> `Type` Bu veri bağdaştırıcısı için özel yapılandırma düzenleyicinizi belirtmek için ve isteğe bağlı olarak düzenleyici için kullanılacak yardım dosyasını belirtmek için öğesini de ekleyebilirsiniz.
   >
   > Ayrıca, <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorEnabledByDefaultAttribute> her zaman etkinleştirilmesi gerektiğini belirtmek için öğesini de uygulayabilirsiniz.

7. Tanılama veri bağdaştırıcısı sınıfınız <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector> sınıfından şu şekilde devralması gerekir:

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

9. <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector.Initialize*>Yöntemini ve bir **Dispose** yöntemini ekleyin. Yönteminde, `Initialize` veri havuzunu, test ayarlarından herhangi bir yapılandırma verilerini başlatır ve kullanmak istediğiniz olay işleyicilerini aşağıdaki şekilde kaydedebilirsiniz:

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

10. Test sırasında oluşturulan günlük dosyasını toplamak için aşağıdaki olay işleyici kodunu ve özel yöntemi kullanın:

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

     Bu dosyalar, test sonuçlarına eklenir. Bu test sonuçlarından bir hata oluşturursanız veya kullandığınızda [!INCLUDE[mtrlong](../test/includes/mtrlong_md.md)] , dosyalar da hataya eklenir.

     Test ayarlarınızda kullanılacak verileri toplamak için kendi düzenleyicinizi kullanmak istiyorsanız, bkz. [nasıl yapılır: tanılama veri bağdaştırıcınız için veriler için özel bir düzenleyici oluşturma](../test/quickstart-create-a-load-test-project.md).

11. Bir test, kullanıcının test ayarlarında yapılandırdığı kullanıcılara göre tamamlandığında bir günlük dosyası toplamak için bir *App.config* dosyası oluşturmanız ve çözümünüze eklemeniz gerekir. Bu dosya aşağıdaki biçime sahiptir ve tanımak için tanılama veri bağdaştırıcınız için URI 'yi içermelidir. "Şirket/ProductName/Version" için gerçek değerleri değiştirin.

    > [!NOTE]
    > Tanılama veri bağdaştırıcınız için herhangi bir bilgi yapılandırmanız gerekmiyorsa, bir yapılandırma dosyası oluşturmanız gerekmez.

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
    > Varsayılan yapılandırma öğesi, ihtiyacınız olan tüm verileri içerebilir. Kullanıcı, test ayarlarında tanılama veri bağdaştırıcısını yapılandırmadığından, varsayılan veriler yürütüldüğünde tanılama veri bağdaştırıcınıza geçirilir. Bölümüne eklediğiniz XML, `<DefaultConfigurations>` tanımlanan şemanın parçası olma olasılığı olmadığı için, oluşturduğu XML hatalarını yoksayabilirsiniz.
    >
    > Yükleme dizininizi temel alan aşağıdaki yolda başka yapılandırma dosyası örnekleri vardır: *Program Files\Microsoft Visual Studio 10.0 \ Common7\IDE\PrivateAssemblies\DataCollectors*.

     Testlerinizi çalıştırdığınızda bir ortamı kullanmak üzere test ayarlarınızı yapılandırma hakkında daha fazla bilgi için, bkz. [tanılama verilerini el ile testlerle toplama (Azure test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts).

     Yapılandırma dosyasını yükleme hakkında daha fazla bilgi için bkz [. nasıl yapılır: özel tanılama veri bağdaştırıcısı yükleme](../test/quickstart-create-a-load-test-project.md)

12. Tanılama veri bağdaştırıcısı derlemenizi oluşturmak için çözümünüzü derleyin.

13. Özel düzenleyicinizi yükleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: özel tanılama veri bağdaştırıcısı yükleme](../test/quickstart-create-a-load-test-project.md).

14. Testlerinizi çalıştırdığınızda bir ortamı kullanmak üzere test ayarlarınızı yapılandırma hakkında daha fazla bilgi için, bkz. [tanılama verilerini el ile testlerle toplama (Azure test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts).

15. Tanılama veri bağdaştırıcınızı seçmek için, önce mevcut bir test ayarlarını seçmeniz ya da Visual Studio 'dan veya Microsoft Test Yöneticisi (Visual Studio 2017 ' de kullanım dışı) yeni bir tane oluşturmanız gerekir. Bağdaştırıcı, test ayarlarınızın **veri ve tanılama** sekmesinde sınıfa atadığınız kolay ad ile görüntülenir.

16. Bu test ayarlarını etkin olacak şekilde ayarlayın. Test ayarları hakkında daha fazla bilgi için bkz. [test ayarlarını kullanarak tanılama bilgilerini toplama](../test/collect-diagnostic-information-using-test-settings.md).

17. Testlerinizi tanılama veri bağdaştırıcınız seçiliyken test ayarlarını kullanarak çalıştırın.

    Belirttiğiniz veri dosyası test sonuçlarınıza eklenir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorTypeUriAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorFriendlyNameAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorEnabledByDefaultAttribute>
- [Test ayarlarını kullanarak tanılama bilgilerini topla](../test/collect-diagnostic-information-using-test-settings.md)
- [Tanılama verilerini el ile testlerde topla (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)
- [Test sırasında tanılama verilerini topla (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts)
- [Nasıl yapılır: tanılama veri bağdaştırıcınız için veriler için özel bir düzenleyici oluşturma](../test/quickstart-create-a-load-test-project.md)
