---
title: Azure kodunuzu iyileştirme
description: Visual Studio 'daki Azure Code Optimization araçları, kodunuzun daha sağlam ve daha iyi performans sağlanmasına nasıl yardımcı olduğunu öğrenin.
author: ghogen
manager: jillfra
ms.assetid: ed48ee06-e2d2-4322-af22-07200fb16987
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: ghogen
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: e34c51db062528c83e08e2cb463a1cc44ab476f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75915753"
---
# <a name="optimizing-your-azure-code"></a>Azure Kodunuzu İyileştirme
Microsoft Azure kullanan uygulamalar programlarken, bir bulut ortamında uygulama ölçeklenebilirliği, davranış ve performans sorunlarını önlemeye yardımcı olmak için izlemeniz gereken bazı kodlama uygulamaları vardır. Microsoft, yaygın olarak karşılaşılan bu sorunlardan birkaçını algılayan ve tanıtan bir Azure Kod Analizi Aracı sağlar ve bunları çözmenize yardımcı olur. Visual Studio 'da NuGet aracılığıyla aracı indirebilirsiniz.

## <a name="azure-code-analysis-rules"></a>Azure kod analizi kuralları
Azure Kod Analizi Aracı, performans etkileyen bilinen sorunları bulduğunda Azure kodunuzu otomatik olarak işaretlemek için aşağıdaki kuralları kullanır. Algılanan sorunlar bir uyarı veya derleyici hatası olarak görünür. Uyarı veya hatayı çözmek için kod düzeltmeleri veya öneriler, genellikle ampul simgesiyle sağlanır.

## <a name="avoid-using-default-in-process-session-state-mode"></a>Varsayılan (işlem içi) oturum durumu modunu kullanmaktan kaçının
### <a name="id"></a>ID
AP0000

### <a name="description"></a>Description
Bulut uygulamaları için varsayılan (işlem içi) oturum durumu modunu kullanırsanız, oturum durumunu kaybedebilirsiniz.

### <a name="reason"></a>Neden
Varsayılan olarak, web.config dosyasında belirtilen oturum durumu modu işlem içinde olur. Ayrıca, yapılandırma dosyasında bir giriş belirtilmemişse, oturum durumu modu varsayılan olarak işlem içinde olur. İşlem içi modu, oturum durumunu Web sunucusunda bellekte depolar. Bir örnek yeniden başlatıldığında veya yük dengeleme veya yük devretme desteği için yeni bir örnek kullanıldığında, Web sunucusunda bellekte depolanan oturum durumu kaydedilmez. Bu durum, uygulamanın bulutta ölçeklenebilir olmasını önler.

ASP.NET oturum durumu, oturum durumu verileri için birkaç farklı depolama seçeneğini destekler: InProc, StateServer, SQLServer, özel ve kapalı. [Redin Için Azure oturum durumu sağlayıcısı](https://blogs.msdn.com/b/webdev/archive/2014/05/12/announcing-asp-net-session-state-provider-for-redis-preview-release.aspx)gibi bir dış oturum durumu deposunda verileri barındırmak için özel mod kullanmanız önerilir.

### <a name="solution"></a>Çözüm
Önerilen bir çözüm, oturum durumunu yönetilen bir önbellek hizmetinde depobir çözümdür. Oturum durumunu depolamak için [Azure oturum durumu sağlayıcısı 'Nı redsıs için](https://blogs.msdn.com/b/webdev/archive/2014/05/12/announcing-asp-net-session-state-provider-for-redis-preview-release.aspx) kullanmayı öğrenin. Ayrıca, uygulamanızın bulutta ölçeklenebilir olduğundan emin olmak için oturum durumunu başka yerlerde de saklayabilirsiniz. Alternatif çözümler hakkında daha fazla bilgi edinmek için lütfen [oturum durumu modlarını](https://msdn.microsoft.com/library/ms178586)okuyun.

## <a name="run-method-should-not-be-async"></a>Run yöntemi zaman uyumsuz olmamalıdır
### <a name="id"></a>ID
AP1000

### <a name="description"></a>Description
[Run ()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) yönteminin dışında zaman uyumsuz Yöntemler ( [await](https://msdn.microsoft.com/library/hh156528.aspx)gibi) oluşturun ve sonra [()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)zaman uyumsuz yöntemleri çağırın. [[Run ()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) yönteminin zaman uyumsuz olarak bildirilmesi, çalışan rolünün yeniden başlatma döngüsü girmesine neden olur.

Lütfen [Azure kod analizi geri bildirimi](https://social.msdn.microsoft.com/Forums/en-US/home)'nde fikirlerinizi ve geri bildiriminizi paylaşın.

### <a name="reason"></a>Neden
[Run ()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) yöntemi içinde zaman uyumsuz yöntemlerin çağrılması, bulut hizmeti çalışma zamanının çalışan rolünü geri dönüştürmesine neden olur. Bir çalışan rolü başladığında, tüm program yürütmesi [Run ()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) yöntemi içinde gerçekleşir. [Run ()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) yönteminden çıkılırken çalışan rolünün yeniden başlatılmasına neden olur. Çalışan rolü çalışma zamanı zaman uyumsuz yöntemi ziyaret edildiğinde, zaman uyumsuz yöntemden sonra tüm işlemleri dağıtır ve ardından döndürür. Bu, çalışan rolünün [[[[Run ()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) yönteminden çıkmasına ve yeniden başlatılmasına neden olur. Yürütmenin bir sonraki yinelemesinde, çalışan rolü zaman uyumsuz yöntemi tekrar ziyaret ediyor ve yeniden başlatır, böylece çalışan rolü de yeniden geri dönüşüme neden olur.

### <a name="solution"></a>Çözüm
Tüm zaman uyumsuz işlemleri [Run ()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) yöntemi dışında yerleştirin. Ardından, yeniden düzenlenmiş Async yöntemini [[Run ()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) yönteminin Içinden RunAsync () gibi çağırın. bekle. Azure Kod Analizi Aracı, bu sorunu gidermenize yardımcı olabilir.

Aşağıdaki kod parçacığı, bu soruna yönelik kod düzeltmesini gösterir:

```csharp
public override void Run()
{
    RunAsync().Wait();
}

public async Task RunAsync()
{
    //Asynchronous operations code logic
    // This is a sample worker implementation. Replace with your logic.

    Trace.TraceInformation("WorkerRole1 entry point called");

    HttpClient client = new HttpClient();

    Task<string> urlString = client.GetStringAsync("https://msdn.microsoft.com");

    while (true)
    {
        Thread.Sleep(10000);
        Trace.TraceInformation("Working");

        string stream = await urlString;
    }

}
```

## <a name="use-service-bus-shared-access-signature-authentication"></a>Service Bus paylaşılan erişim Imzası kimlik doğrulamasını kullanma
### <a name="id"></a>ID
AP2000

### <a name="description"></a>Description
Kimlik doğrulaması için paylaşılan erişim Imzasını (SAS) kullanın. Service Bus kimlik doğrulaması için Access Control Service (ACS) kullanım dışı bırakılıyor.

### <a name="reason"></a>Neden
Gelişmiş güvenlik için Azure Active Directory, ACS kimlik doğrulamasını SAS kimlik doğrulamasıyla değiştiriyor. Geçiş planı hakkında bilgi için bkz. [Azure ACTIVE DIRECTORY ACS 'nin geleceği](https://cloudblogs.microsoft.com/enterprisemobility/2013/06/22/azure-active-directory-is-the-future-of-acs/) .

### <a name="solution"></a>Çözüm
Uygulamalarınızda SAS kimlik doğrulamasını kullanın. Aşağıdaki örnek, bir hizmet veri yolu ad alanına veya varlığına erişmek için mevcut bir SAS belirtecinin nasıl kullanılacağını gösterir.

```csharp
MessagingFactory listenMF = MessagingFactory.Create(endpoints, new StaticSASTokenProvider(subscriptionToken));
SubscriptionClient sc = listenMF.CreateSubscriptionClient(topicPath, subscriptionName);
BrokeredMessage receivedMessage = sc.Receive();
```

Daha fazla bilgi için aşağıdaki konulara bakın.

* [Service Bus ile paylaşılan erişim Imzası kimlik doğrulaması kullanma](/azure/service-bus-messaging/service-bus-sas)

## <a name="consider-using-onmessage-method-to-avoid-receive-loop"></a>"Alma döngüsü" önlemek için OnMessage metodunu kullanmayı düşünün
### <a name="id"></a>ID
AP2002

### <a name="description"></a>Description
"Alma döngüsüne" engel olmak için **OnMessage** metodunu **çağırmak, iletileri alma yöntemi çağrılmadan** daha iyi bir çözümdür. Ancak, **alma** yöntemini kullanmanız gerekiyorsa ve varsayılan olmayan bir sunucu bekleme süresi belirtirseniz, sunucu bekleme süresinin bir dakikadan fazla olduğundan emin olun.

### <a name="reason"></a>Neden
**OnMessage**çağrılırken, istemci kuyruğu veya aboneliği sürekli yoklayan bir iç ileti göndericisi başlatır. Bu ileti göndericisi, ileti alma çağrısını veren sonsuz bir döngü içeriyor. Çağrı zaman aşımına uğrarsa, yeni bir çağrı yayınlar. Zaman aşımı aralığı, kullanılmakta olan [Messagingfactory](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.messagingfactory.aspx)'Nin [OperationTimeout](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.messagingfactorysettings.operationtimeout.aspx) özelliğinin değerine göre belirlenir.

**OnMessage** 'i **alma** ile karşılaştırıldığında kullanmanın avantajı, kullanıcıların iletileri el ile yoklamasını, özel durumları işlemesini, paralel olarak birden çok iletiyi işlemesini ve iletileri tamamlamasını desteklemez.

**Alma** 'yı varsayılan değerini kullanmadan çağırırsanız, *ServerWaitTime* değerinin bir dakikadan fazla olduğundan emin olun. *ServerWaitTime* 'in birden fazla dakika olarak ayarlanması, iletinin tam olarak alınmadan önce sunucunun zaman aşımına uğramasını önler.

### <a name="solution"></a>Çözüm
Önerilen kullanımlar için lütfen aşağıdaki kod örneklerine bakın. Daha fazla ayrıntı için bkz. [Queueclient. OnMessage yöntemi (Microsoft. ServiceBus. Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.onmessage.aspx)ve [Queueclient. Receive yöntemi (Microsoft. ServiceBus. Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.receive.aspx).

Azure mesajlaşma altyapısının performansını artırmak için bkz. tasarım deseninin [zaman uyumsuz mesajlaşma](https://msdn.microsoft.com/library/dn589781.aspx)bilgileri.

Aşağıda ileti almak için **OnMessage** kullanımı örneği verilmiştir.

```csharp
void ReceiveMessages()
{
    // Initialize message pump options.
    OnMessageOptions options = new OnMessageOptions();
    options.AutoComplete = true; // Indicates if the message-pump should call complete on messages after the callback has completed processing.
    options.MaxConcurrentCalls = 1; // Indicates the maximum number of concurrent calls to the callback the pump should initiate.
    options.ExceptionReceived += LogErrors; // Enables you to get notified of any errors encountered by the message pump.

    // Start receiving messages.
    QueueClient client = QueueClient.Create("myQueue");
    client.OnMessage((receivedMessage) => // Initiates the message pump and callback is invoked for each message that is received, calling close on the client will stop the pump.
    {
        // Process the message.
    }, options);
    Console.WriteLine("Press any key to exit.");
    Console.ReadKey();
```

Aşağıda, varsayılan sunucu bekleme zamanına sahip **alma** kullanımına ilişkin bir örnek verilmiştir.

```csharp
string connectionString =
CloudConfigurationManager.GetSetting("Microsoft.ServiceBus.ConnectionString");

QueueClient Client =
    QueueClient.CreateFromConnectionString(connectionString, "TestQueue");

while (true)
{
   BrokeredMessage message = Client.Receive();
   if (message != null)
   {
      try
      {
         Console.WriteLine("Body: " + message.GetBody<string>());
         Console.WriteLine("MessageID: " + message.MessageId);
         Console.WriteLine("Test Property: " +
            message.Properties["TestProperty"]);

         // Remove message from queue
         message.Complete();
      }

      catch (Exception)
      {
         // Indicate a problem, unlock message in queue
         message.Abandon();
      }
   }
```

Aşağıda, varsayılan olmayan bir sunucu bekleme süresi ile **alma** kullanmanın bir örneği verilmiştir.

```csharp
while (true)
{
   BrokeredMessage message = Client.Receive(new TimeSpan(0,1,0));

   if (message != null)
   {
      try
      {
         Console.WriteLine("Body: " + message.GetBody<string>());
         Console.WriteLine("MessageID: " + message.MessageId);
         Console.WriteLine("Test Property: " +
            message.Properties["TestProperty"]);

         // Remove message from queue
         message.Complete();
      }

      catch (Exception)
      {
         // Indicate a problem, unlock message in queue
         message.Abandon();
      }
   }
}
```

## <a name="consider-using-asynchronous-service-bus-methods"></a>Zaman uyumsuz Service Bus yöntemleri kullanmayı düşünün
### <a name="id"></a>ID
AP2003

### <a name="description"></a>Description
Aracılı mesajlaşma ile performansı artırmak için zaman uyumsuz Service Bus yöntemler kullanın.

### <a name="reason"></a>Neden
Zaman uyumsuz yöntemlerin kullanılması uygulama programı eşzamanlılık imkanı sağladığından her çağrının yürütülmesi ana iş parçacığını engellemez. Service Bus mesajlaşma yöntemlerini kullanırken bir işlem (gönderme, alma, silme, vb.) gerçekleştirmek zaman alır. Bu süre, isteğin ve yanıtın gecikme süresinin yanı sıra Service Bus hizmeti tarafından işlemin işlenmesini içerir. Zaman başına işlem sayısını artırmak için, işlemlerin eşzamanlı olarak yürütülmesi gerekir. Daha fazla bilgi için lütfen [Service Bus Aracılı mesajlaşma kullanarak performans geliştirmeleri Için En Iyi uygulamalara](https://msdn.microsoft.com/library/azure/hh528527.aspx)bakın.

### <a name="solution"></a>Çözüm
Önerilen zaman uyumsuz yöntemi kullanma hakkında bilgi için bkz. [Queueclient sınıfı (Microsoft. ServiceBus. Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.aspx) .

Azure mesajlaşma altyapısının performansını artırmak için bkz. tasarım deseninin [zaman uyumsuz mesajlaşma](https://msdn.microsoft.com/library/dn589781.aspx)bilgileri.

## <a name="consider-partitioning-service-bus-queues-and-topics"></a>Service Bus sıralarını ve konuları bölümlemeyi düşünün
### <a name="id"></a>ID
AP2004

### <a name="description"></a>Description
Service Bus mesajlaşma ile daha iyi performans için Service Bus kuyrukları ve konuları bölümleyin.

### <a name="reason"></a>Neden
Bölümlenmiş bir sıranın veya konunun genel performansı artık tek bir ileti aracısının veya mesajlaşma deposunun performansıyla sınırlı olmadığından, Service Bus kuyruklarını ve konularını bölümlemek, performans aktarım hızını ve hizmet kullanılabilirliğini artırır. Ayrıca, bir mesajlaşma deposunun geçici bir kesinti, bölümlenmiş bir kuyruğu veya konuyu kullanılamaz hale getirir. Daha fazla bilgi için bkz. [mesajlaşma varlıklarını bölümlendirme](https://msdn.microsoft.com/library/azure/dn520246.aspx).

### <a name="solution"></a>Çözüm
Aşağıdaki kod parçacığı, mesajlaşma varlıklarının nasıl bölümlenmesi gerektiğini gösterir.

```csharp
// Create partitioned topic.
NamespaceManager ns = NamespaceManager.CreateFromConnectionString(myConnectionString);
TopicDescription td = new TopicDescription(TopicName);
td.EnablePartitioning = true;
ns.CreateTopic(td);
```

Daha fazla bilgi için bkz. [bölümlenmiş Service Bus kuyruklar ve konular | Blog Microsoft Azure](https://azure.microsoft.com/blog/2013/10/29/partitioned-service-bus-queues-and-topics/) ve [Microsoft Azure Service Bus bölümlenmiş sıra](https://code.msdn.microsoft.com/windowsazure/Service-Bus-Partitioned-7dfd3f1f) örneğine göz atın.

## <a name="do-not-set-sharedaccessstarttime"></a>SharedAccessStartTime ayarlama
### <a name="id"></a>ID
AP3001

### <a name="description"></a>Description
Paylaşılan erişim ilkesini hemen başlatmak için SharedAccessStartTimeset ' i Şu anki zamana göre kullanmaktan kaçının. Yalnızca paylaşılan erişim ilkesini daha sonra başlatmak istiyorsanız bu özelliği ayarlamanız gerekir.

### <a name="reason"></a>Neden
Saat eşitleme, veri merkezleri arasında hafif bir zamana farklılık oluşmasına neden olur. Örneğin, bir depolama SAS ilkesinin başlangıç saatini DateTime kullanarak geçerli zaman olarak ayarlamayı düşünebilirsiniz. şimdi veya benzer bir yöntem SAS ilkesinin hemen geçerli olmasına neden olur. Ancak, veri merkezleri arasındaki hafif zaman farkları, bazı veri merkezi süreleri başlangıç zamanından biraz daha daha sonra olabileceğinden, bu nedenle sorun oluşmasına neden olabilir. Sonuç olarak, ilke ömrü çok kısa bir süre ayarlanmışsa SAS ilkesinin süresi hızla (veya hatta hemen) dolacak.

Azure depolama 'da paylaşılan erişim Imzasını kullanma hakkında daha fazla bilgi için bkz. [tablo SAS (paylaşılan erişim imzası), kuyruk SAS ve BLOB SAS güncelleştirme-Microsoft Azure depolama Team blog-site Home-MSDN blogları](https://blogs.msdn.microsoft.com/windowsazurestorage/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas/).

### <a name="solution"></a>Çözüm
Paylaşılan erişim ilkesinin başlangıç saatini ayarlayan ifadeyi kaldırın. Azure Kod Analizi Aracı bu sorun için bir çözüm sağlar. Güvenlik yönetimi hakkında daha fazla bilgi için lütfen tasarım deseninin [Valet anahtar düzenine](https://msdn.microsoft.com/library/dn568102.aspx)bakın.

Aşağıdaki kod parçacığı, bu sorunun kod düzeltmesini gösterir.

```csharp
// The shared access policy provides
// read/write access to the container for 10 hours.
blobPermissions.SharedAccessPolicies.Add("mypolicy", new SharedAccessBlobPolicy()
{
   // To ensure SAS is valid immediately, don’t set start time.
   // This way, you can avoid failures caused by small clock differences.
   SharedAccessExpiryTime = DateTime.UtcNow.AddHours(10),
   Permissions = SharedAccessBlobPermissions.Write |
      SharedAccessBlobPermissions.Read
});
```

## <a name="shared-access-policy-expiry-time-must-be-more-than-five-minutes"></a>Paylaşılan erişim Ilkesi süre sonu zamanı beş dakikadan fazla olmalıdır
### <a name="id"></a>ID
AP3002

### <a name="description"></a>Description
"Saat eğriltme" olarak bilinen bir koşula bağlı olarak, farklı konumlardaki veri merkezleri arasındaki saatler için beş dakikalık fark olabilir. SAS ilke belirtecinin planlanandan daha önce dolmasını engellemek için, sona erme süresini beş dakikadan uzun olacak şekilde ayarlayın.

Lütfen [Azure kod analizi geri bildirimi](https://social.msdn.microsoft.com/Forums/en-US/home)'nde fikirlerinizi ve geri bildiriminizi paylaşın.

### <a name="reason"></a>Neden
Dünya genelindeki farklı konumlardaki veri merkezleri saat sinyaliyle eşitlenir. Saat sinyalinin farklı konumlara aktarılması zaman aldığı için, her şeyin farklı coğrafi konumlardaki veri merkezleri arasında bir zaman farkı olabilir. Bu süre farkı, paylaşılan erişim ilkesi başlangıç zamanı ve süre sonu aralığını etkileyebilir. Bu nedenle, paylaşılan erişim ilkesinin hemen etkili olmasını sağlamak için başlangıç saatini belirtmeyin. Ayrıca, sona erme süresinin erken zaman aşımını engellemek için 5 dakikadan fazla olduğundan emin olun.

Azure depolama 'da paylaşılan erişim Imzasını kullanma hakkında daha fazla bilgi için bkz. [tablo SAS (paylaşılan erişim imzası), kuyruk SAS ve BLOB SAS güncelleştirmesi-Microsoft Azure depolama Team blog-site Home-MSDN blogları](https://blogs.msdn.microsoft.com/windowsazurestorage/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas/).

### <a name="solution"></a>Çözüm
Güvenlik yönetimi hakkında daha fazla bilgi için bkz. tasarım deseninin [Valet anahtar stili](https://msdn.microsoft.com/library/dn568102.aspx).

Aşağıda, paylaşılan erişim ilkesi başlangıç zamanını Belirtmemeye yönelik bir örnek verilmiştir.

```csharp
// The shared access policy provides
// read/write access to the container for 10 hours.
blobPermissions.SharedAccessPolicies.Add("mypolicy", new SharedAccessBlobPolicy()
{
   // To ensure SAS is valid immediately, don’t set start time.
   // This way, you can avoid failures caused by small clock differences.
   SharedAccessExpiryTime = DateTime.UtcNow.AddHours(10),
   Permissions = SharedAccessBlobPermissions.Write |
      SharedAccessBlobPermissions.Read
});
```

Aşağıda, bir ilke süre sonu süresi beş dakikadan fazla olan bir paylaşılan erişim ilkesi başlangıç zamanı belirtmenin bir örneği verilmiştir.

```csharp
// The shared access policy provides
// read/write access to the container for 10 hours.
blobPermissions.SharedAccessPolicies.Add("mypolicy", new SharedAccessBlobPolicy()
{
   // To ensure SAS is valid immediately, don’t set start time.
   // This way, you can avoid failures caused by small clock differences.
  SharedAccessStartTime = new DateTime(2014,1,20),
 SharedAccessExpiryTime = new DateTime(2014, 1, 21),
   Permissions = SharedAccessBlobPermissions.Write |
      SharedAccessBlobPermissions.Read
});
```

Daha fazla bilgi için bkz. [paylaşılan erişim Imzası oluşturma ve kullanma](https://msdn.microsoft.com/library/azure/jj721951.aspx).

## <a name="use-cloudconfigurationmanager"></a>CloudConfigurationManager kullanma
### <a name="id"></a>ID
AP4000

### <a name="description"></a>Description
Azure Web sitesi ve Azure Mobil Hizmetleri gibi projeler için [ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) sınıfının kullanılması çalışma zamanı sorunları oluşturmayacaktır. Bununla birlikte, en iyi uygulama olarak, tüm Azure bulut uygulamalarına yönelik yapılandırmaların yönetilmesi için birleştirilmiş bir yöntem olarak bulutta[ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) kullanmak iyi bir fikirdir.

### <a name="reason"></a>Neden
CloudConfigurationManager, uygulama ortamına uygun yapılandırma dosyasını okur.

[CloudConfigurationManager](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.cloudconfigurationmanager.aspx)

### <a name="solution"></a>Çözüm
[Cloudconfigurationmanager sınıfını](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.cloudconfigurationmanager.aspx)kullanmak için kodunuzu yeniden düzenleyin. Bu soruna yönelik bir kod sorunu, Azure Kod Analizi Aracı tarafından sağlanmaktadır.

Aşağıdaki kod parçacığı, bu sorunun kod düzeltmesini gösterir. Değiştir

`var settings = ConfigurationManager.AppSettings["mySettings"];`

örneklerini şununla değiştirin:

`var settings = CloudConfigurationManager.GetSetting("mySettings");`

Yapılandırma ayarının bir App.config veya Web.config dosyasında nasıl depolayabileceği hakkında bir örnek aşağıda verilmiştir. Ayarları yapılandırma dosyasının appSettings bölümüne ekleyin. Aşağıda, önceki kod örneği için Web.config dosyası verilmiştir.

```xml
<appSettings>
    <add key="webpages:Version" value="3.0.0.0" />
    <add key="webpages:Enabled" value="false" />
    <add key="ClientValidationEnabled" value="true" />
    <add key="UnobtrusiveJavaScriptEnabled" value="true" />
    <add key="mySettings" value="[put_your_setting_here]"/>
  </appSettings>
```

## <a name="avoid-using-hard-coded-connection-strings"></a>Sabit kodlanmış bağlantı dizeleri kullanmaktan kaçının
### <a name="id"></a>ID
AP4001

### <a name="description"></a>Description
Sabit kodlanmış bağlantı dizeleri kullanırsanız ve daha sonra güncelleştirmeniz gerekiyorsa, kaynak kodunuzda değişiklik yapmanız ve uygulamayı yeniden derlemeniz gerekir. Ancak, bağlantı dizelerinizi bir yapılandırma dosyasında depoluyorsa yapılandırma dosyasını güncelleştirerek daha sonra değiştirebilirsiniz.

### <a name="reason"></a>Neden
Bağlantı dizelerinin hızlı bir şekilde değiştirilmesi gerektiğinde sorun ortaya çıkardığından, sabit kodlama bağlantı dizeleri hatalı bir uygulamadır. Ayrıca, projenin kaynak denetimine iade olması gerekiyorsa, dizelerin kaynak kodunda görüntülenebilmesi için, sabit kodlanmış bağlantı dizeleri güvenlik açıklarını ortaya çıkarabilir.

### <a name="solution"></a>Çözüm
Bağlantı dizelerini yapılandırma dosyalarında veya Azure ortamlarında depolayın.

* Tek başına uygulamalar için, bağlantı dizesi ayarlarını depolamak için app.config kullanın.
* IIS tarafından barındırılan Web uygulamaları için bağlantı dizelerini depolamak üzere web.config kullanın.
* ASP.NET vNext uygulamaları için bağlantı dizelerini depolamak üzere üzerinde configuration.jskullanın.

web.config veya app.config gibi yapılandırma dosyalarını kullanma hakkında daha fazla bilgi için bkz. [ASP.NET Web Configuration yönergeleri](https://msdn.microsoft.com/library/vstudio/ff400235\(v=vs.100\).aspx). Azure ortam değişkenlerinin nasıl çalıştığı hakkında bilgi için bkz. [Azure Web siteleri: uygulama dizeleri ve bağlantı dizeleri nasıl çalışır?](https://azure.microsoft.com/blog/2013/07/17/windows-azure-web-sites-how-application-strings-and-connection-strings-work/). Kaynak denetiminde bağlantı dizesini depolama hakkında bilgi için, bkz. [kaynak kodu deposunda depolanan dosyalardaki bağlantı dizeleri gibi hassas bilgileri yerleştirmekten kaçının](/aspnet/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/source-control).

## <a name="use-diagnostics-configuration-file"></a>Tanılama yapılandırma dosyası kullan
### <a name="id"></a>ID
AP5000

### <a name="description"></a>Description
Kodunuzda, Microsoft. WindowsAzure. Diagnostics programlama API 'sini kullanarak tanılama ayarlarını yapılandırmak yerine, tanılama ayarlarını Diagnostics. wadcfg dosyasında yapılandırmanız gerekir. (Veya Azure SDK 2,5 kullanıyorsanız, Diagnostics. wadcfgx). Bunu yaparak, kodunuzu yeniden derlemek zorunda kalmadan tanılama ayarlarını değiştirebilirsiniz.

### <a name="reason"></a>Neden
Azure SDK 2,5 (Azure tanılama 1,3 kullanan) öncesinde, Azure Tanılama (WAD) birkaç farklı yöntem kullanılarak yapılandırılabilir: zorunlu kod, bildirime dayalı yapılandırma veya varsayılan yapılandırmayı kullanarak, depolama alanındaki yapılandırma blobuna ekleme. Ancak, tanılamayı yapılandırmak için tercih edilen yöntem, uygulama projesindeki bir XML yapılandırma dosyası (SDK 2,5 ve üzeri için tanılama. wadcfgx) kullanmaktır. Bu yaklaşımda, Diagnostics. wadcfg dosyası yapılandırmayı tamamen tanımlar ve ' de güncelleştirilecektir ve yeniden dağıtılabilir. Tanılama. wadcfg yapılandırma dosyasının kullanımını [Diagnosticmonitor](https://msdn.microsoft.com/library/microsoft.windowsazure.diagnostics.diagnosticmonitor.aspx)veya [Roleınstancediagnosticmanager](https://msdn.microsoft.com/library/microsoft.windowsazure.diagnostics.management.roleinstancediagnosticmanager.aspx) sınıflarını kullanarak yapılandırma ayarlarının programlı yöntemleriyle karıştırma, karışıklıklara yol açabilir. Daha fazla bilgi için bkz. [Azure tanılama yapılandırmayı başlatma veya değiştirme](https://msdn.microsoft.com/library/azure/hh411537.aspx) .

WAD 1,3 (Azure SDK 2,5 ' de bulunur) ile başlayarak, tanılamayı yapılandırmak için artık kodu kullanmak mümkün değildir. Sonuç olarak, yalnızca tanılama uzantısını uygularken veya güncelleştirirken yapılandırmayı sağlayabilirsiniz.

### <a name="solution"></a>Çözüm
Tanılama ayarlarını tanılama yapılandırma dosyasına (SDK 2,5 ve üzeri için tanılama. wadcfg veya Diagnostics. wadcfgx) taşımak için tanılama yapılandırma tasarımcısını kullanın. Ayrıca, [Azure SDK 2,5](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2015AzurePack.appids) ' i yükleyip en son Tanılama özelliğini kullanmanız önerilir.

1. Yapılandırmak istediğiniz rolün kısayol menüsünde Özellikler ' i seçin ve ardından yapılandırma sekmesini seçin.
2. **Tanılama** bölümünde, **tanılamayı etkinleştir** onay kutusunun seçili olduğundan emin olun.
3. **Yapılandır** düğmesini seçin.

   ![Tanılamayı etkinleştir seçeneğine erişme](./media/vs-azure-tools-optimizing-azure-code-in-visual-studio/IC796660.png)

   Daha fazla bilgi için bkz. [Azure Cloud Services Için tanılamayı yapılandırma ve sanal makineler](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md) .

## <a name="avoid-declaring-dbcontext-objects-as-static"></a>DbContext nesnelerini statik olarak bildirmemeye özen gösterin
### <a name="id"></a>ID
AP6000

### <a name="description"></a>Description
Belleği kaydetmek için DBContext nesnelerini static olarak bildirmemeye özen gösterin.

### <a name="reason"></a>Neden
DBContext nesneleri her çağrının sorgu sonuçlarını tutar. Statik DBContext nesneleri, uygulama etki alanı kaldırılana kadar atılamaz. Bu nedenle, statik bir DBContext nesnesi büyük miktarda bellek tüketebilir.

### <a name="solution"></a>Çözüm
DBContext 'i yerel bir değişken veya statik olmayan örnek alanı olarak bildirin, bunu bir görev için kullanın ve ardından, kullanım sonrasında elden çıkarılmasına izin verin.

Aşağıdaki örnek MVC denetleyici sınıfı, DBContext nesnesinin nasıl kullanılacağını gösterir.

```csharp
public class BlogsController : Controller
    {
        //BloggingContext is a subclass to DbContext
        private BloggingContext db = new BloggingContext();
        // GET: Blogs
        public ActionResult Index()
        {
            //business logics…
            return View();
        }
        protected override void Dispose(bool disposing)
        {
            if (disposing)
            {
                db.Dispose();
            }
            base.Dispose(disposing);
        }
    }
```

## <a name="next-steps"></a>Sonraki adımlar
Azure uygulamalarını iyileştirme ve sorunlarını giderme hakkında daha fazla bilgi edinmek için bkz. [Visual Studio kullanarak Azure App Service Web uygulaması sorunlarını giderme](/azure/app-service/web-sites-dotnet-troubleshoot-visual-studio).
