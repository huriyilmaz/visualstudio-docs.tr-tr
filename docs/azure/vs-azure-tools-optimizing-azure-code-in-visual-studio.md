---
title: Azure kodunuzu iyileştirme
description: Azure kod iyileştirme araçlarının kodunuzu daha sağlam Visual Studio daha iyi performansa nasıl yardımcı olduğunu öğrenin.
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: 9836f13ac97641876746e0c514f11efc297d2975
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633094"
---
# <a name="optimizing-your-azure-code"></a>Azure Kodunuzu İyileştirme
Microsoft Azure kullanan uygulamaları programlarken, bulut ortamında uygulama ölçeklenebilirliği, davranışı ve performansıyla ilgili sorunları önlemeye yardımcı olmak için izlemeniz gereken bazı kodlama uygulamaları vardır. Microsoft, sık karşılaşılan Code Analysis tanıtan ve tanımlayan ve bunları çözmenize yardımcı olan bir Azure Code Analysis aracı sağlar. Aracı NuGet aracılığıyla Visual Studio indirebilirsiniz.

## <a name="azure-code-analysis-rules"></a>Azure Code Analysis kuralları
Azure Code Analysis aracı, performansı etkileyen bilinen sorunları bulduğunda Azure kodunuzu otomatik olarak bayrakla bayrakla çarpmak için aşağıdaki kuralları kullanır. Algılanan sorunlar uyarı veya derleyici hataları olarak görünür. Uyarıyı veya hatayı çözümlemeye yönelik kod düzeltmeleri veya öneriler genellikle ampul simgesi aracılığıyla sağlanır.

## <a name="avoid-using-default-in-process-session-state-mode"></a>Varsayılan (işlem sırasında) oturum durumu modunu kullanmaktan kaçının
### <a name="id"></a>ID
AP0000

### <a name="description"></a>Description
Bulut uygulamaları için varsayılan (işlem sırasında) oturum durumu modunu kullanırsanız oturum durumunu kaybedebilirsiniz.

Lütfen fikirlerinizi ve geri bildiriminizi [Azure'da Code Analysis paylaşın.](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="reason"></a>Nedeni
Varsayılan olarak, web.config dosyada belirtilen oturum durumu modu devam ediyor. Ayrıca, yapılandırma dosyasında hiçbir giriş belirtilmezse Oturum Durumu modu varsayılan olarak işlem içinde olur. İşlem sırasında modu, oturum durumunu web sunucusunda bellekte depolar. Bir örnek yeniden başlatıldığında veya yük dengeleme veya yük devretme desteği için yeni bir örnek kullanılırsa, web sunucusunda bellekte depolanan oturum durumu kaydedilemiyor. Bu durum, uygulamanın bulutta ölçeklenebilir olması engel olur.

ASP.NET durumu, oturum durumu verileri için çeşitli farklı depolama seçeneklerini destekler: InProc, StateServer, SQLServer, Özel ve Kapalı. Redis için Azure Oturum Durumu sağlayıcısı gibi bir dış Oturum Durumu deposuna veri barındırmak için [Özel modu kullanmanız önerilir.](https://devblogs.microsoft.com/aspnet/announcing-asp-net-session-state-provider-for-redis-preview-release/)

### <a name="solution"></a>Çözüm
Önerilen çözümlerden biri, oturum durumunu yönetilen önbellek hizmetine depolamaktır. Redis için [Azure Oturum Durumu sağlayıcısını kullanarak oturum](https://devblogs.microsoft.com/aspnet/announcing-asp-net-session-state-provider-for-redis-preview-release/) durumunu depolamayı öğrenin. Ayrıca, uygulamanın bulutta ölçeklenebilir olduğundan emin olmak için oturum durumunu başka yerlerde de depoabilirsiniz. Alternatif çözümler hakkında daha fazla bilgi edinmek için lütfen Oturum [Durumu Modları makalelerini okuyun.](/previous-versions/ms178586(v=vs.140))

## <a name="run-method-should-not-be-async"></a>Run yöntemi zaman uyumsuz olmalı
### <a name="id"></a>ID
AP1000

### <a name="description"></a>Description
Run() yönteminin dışında zaman uyumsuz yöntemler [(await](/dotnet/csharp/language-reference/operators/await)gibi) oluşturun ve [ardından Run()](/previous-versions/azure/reference/ee772746(v=azure.100)) işlevinden zaman uyumsuz yöntemleri [çağırarak.](/previous-versions/azure/reference/ee772746(v=azure.100)) [[Run()](/previous-versions/azure/reference/ee772746(v=azure.100))](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) yönteminin zaman uyumsuz olarak bildirerek çalışan rolünün yeniden başlatma döngüsüne girebilirsiniz.

Lütfen fikirlerinizi ve geri bildiriminizi [Azure'da Code Analysis paylaşın.](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="reason"></a>Nedeni
Run() yöntemi içinde zaman uyumsuz yöntemlerin [çağrıl kullanılması,](/previous-versions/azure/reference/ee772746(v=azure.100)) bulut hizmeti çalışma zamanının çalışan rolünü geri dönüştürmesini sağlar. Bir çalışan rolü başladığında, tüm program yürütme [run() yöntemi içinde](/previous-versions/azure/reference/ee772746(v=azure.100)) olur. Run yöntemi'nin çık olması çalışan rolünün yeniden başlatılmasına neden olur. Çalışan rolü çalışma zamanı zaman uyumsuz yönteme isabet ettikten sonra tüm işlemleri zaman uyumsuz yöntemden sonra döndürür. Bu, çalışan rolünün Run yönteminden çıkışa ve yeniden başlatmaya neden olur. Bir sonraki yürütme yinelemesinde, çalışan rolü yeniden zaman uyumsuz yönteme isabet ediyor ve yeniden başlatıyor, bu da çalışan rolünün de yeniden geri dönüşüme neden oluyor.

### <a name="solution"></a>Çözüm
Tüm zaman uyumsuz işlemleri [Run() yönteminin dışına](/previous-versions/azure/reference/ee772746(v=azure.100)) yer. Ardından RunAsync().wait gibi Run yönteminin içinden yeniden düzenleme async yöntemini çağırın. Azure Code Analysis aracı bu sorunu çözmenize yardımcı olabilir.

Aşağıdaki kod parçacığında bu sorunun kod düzeltmesi gösterildi:

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

## <a name="use-service-bus-shared-access-signature-authentication"></a>Paylaşılan Service Bus İmzası kimlik doğrulamasını kullanma
### <a name="id"></a>ID
AP2000

### <a name="description"></a>Description
Kimlik doğrulaması için Paylaşılan Erişim İmzası (SAS) kullanın. Access Control Service (ACS), Service Bus kimlik doğrulaması için kullanım dışıdır.

Lütfen fikirlerinizi ve geri bildiriminizi [Azure'da Code Analysis paylaşın.](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="reason"></a>Nedeni
Gelişmiş güvenlik için ACS Azure Active Directory yerine SAS kimlik doğrulaması kullanılır. Geçiş [Azure Active Directory bilgi için bkz. ACS'nin](https://cloudblogs.microsoft.com/enterprisemobility/2013/06/22/azure-active-directory-is-the-future-of-acs/) geleceğidir.

### <a name="solution"></a>Çözüm
Uygulamalarınız için SAS kimlik doğrulamasını kullanın. Aşağıdaki örnekte, service bus ad alanına veya varlığa erişmek için var olan bir SAS belirteci nasıl kullanılır?

```csharp
MessagingFactory listenMF = MessagingFactory.Create(endpoints, new StaticSASTokenProvider(subscriptionToken));
SubscriptionClient sc = listenMF.CreateSubscriptionClient(topicPath, subscriptionName);
BrokeredMessage receivedMessage = sc.Receive();
```

Daha fazla bilgi için aşağıdaki konulara bakın.

* Genel bakış için bkz. [Service Bus ile Paylaşılan Erişim İmzası Kimlik Doğrulaması](/azure/service-bus-messaging/service-bus-sas)
* [Service Bus ile Paylaşılan Erişim İmzası Kimlik Doğrulamasını kullanma](/azure/service-bus-messaging/service-bus-sas)

## <a name="consider-using-onmessage-method-to-avoid-receive-loop"></a>"Alma döngüsü" ile önlemek için OnMessage yöntemini kullanmayı göz önünde bulundurarak
### <a name="id"></a>ID
AP2002

### <a name="description"></a>Description
Bir "alma döngüsüne" girilmekten kaçınmak **için, OnMessage** yönteminin çağrılması iletileri almak için Receive yöntemini çağırmaya göre daha **iyi bir çözümdür.** Ancak, Receive yöntemini **kullanıyorsanız** ve varsayılan olmayan bir sunucu bekleme süresi belirtirsiniz, sunucu bekleme süresi bir dakikanın üzerinde olduğundan emin olun.

Lütfen fikirlerinizi ve geri bildiriminizi [Azure'da Code Analysis paylaşın.](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="reason"></a>Nedeni
**OnMessage çağrısı sırasında,** istemci kuyruğu veya aboneliği sürekli yoklar bir iç ileti pompasını başlatır. Bu ileti pompası, iletileri almak için bir çağrıda bulunduran sonsuz bir döngü içerir. Çağrı zaman out, yeni bir çağrı sağlar. Zaman aşımı aralığı, kullanılan [MessagingFactory'nin](/dotnet/api/microsoft.servicebus.messaging.messagingfactory) [OperationTimeout](/dotnet/api/microsoft.servicebus.messaging.messagingfactorysettings) özelliğinin değerine göre belirlenir.

**OnMessage** kullanmanın **Receive** ile karşılaştırıldığında avantajı, kullanıcıların iletileri el ile yoklaması, özel durumları işlemesi, birden çok iletileri paralel olarak işlemesi ve iletileri tamamlaması gerekmez.

Varsayılan değerini **kullanmadan Receive** çağrısı yaptısanız *ServerWaitTime değerinin* bir dakikadan uzun olduğundan emin olun. *ServerWaitTime ayarının* bir dakikayı alaması, ileti tam olarak alınmadan önce sunucunun zamanlamasını önler.

### <a name="solution"></a>Çözüm
Önerilen kullanımlar için lütfen aşağıdaki kod örneklerine bakın. Daha fazla ayrıntı için bkz. [QueueClient.OnMessage Metodu (Microsoft.ServiceBus.Messaging)](/dotnet/api/microsoft.servicebus.messaging.queueclient) ve [QueueClient.Receive Metodu (Microsoft.ServiceBus.Messaging)](/dotnet/api/microsoft.servicebus.messaging.queueclient).

Azure mesajlaşma altyapısının performansını geliştirmek için bkz. Tasarım deseni [Zaman Uyumsuz Mesajlaşma Primer.](/previous-versions/msp-n-p/dn589781(v=pandp.10))

Aşağıda, iletileri almak için **OnMessage kullanma örneği** ve ardından ve bir örnek ve ardından yer alır.

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

Aşağıda, varsayılan sunucu bekleme **süresiyle Alma'nın** kullanımına bir örnek ve ardından yer alır.

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

Aşağıda, Varsayılan olmayan bir sunucu **bekleme** süresiyle Alma kullanma örneği ve ardından bir örnek ve ardından yer alır.

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

## <a name="consider-using-asynchronous-service-bus-methods"></a>Zaman uyumsuz veri Service Bus düşünün
### <a name="id"></a>ID
AP2003

### <a name="description"></a>Description
Aracılı mesajlaşma ile Service Bus için zaman uyumsuz veri doğrulama yöntemleri kullanın.

Lütfen fikirlerinizi ve geri bildiriminizi [Azure'da Code Analysis paylaşın.](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="reason"></a>Nedeni
Her çağrının yürütülmesi ana iş parçacığını engellemey olduğundan, zaman uyumsuz yöntemlerin kullanımı uygulama programı eşzamanlılığını sağlar. Mesajlaşma Service Bus kullanırken bir işlem (gönderme, alma, silme vb.) gerçekleştirmek zaman alır. Bu süre, isteğin ve yanıtın gecikme süresine ek olarak Service Bus hizmeti tarafından işlemeyi içerir. İşlemlerin zaman başına sayısını artırmak için işlemlerin eşzamanlı olarak yürütmesi gerekir. Daha fazla bilgi için lütfen [Aracılı Mesajlaşmayı Kullanarak Performans geliştirmeleri Service Bus En İyi Yöntemler'e bakın.](/previous-versions/azure/hh528527(v=azure.100))

### <a name="solution"></a>Çözüm
Önerilen zaman uyumsuz yöntemi kullanma hakkında bilgi için bkz. [QueueClient Sınıfı (Microsoft.ServiceBus.Messaging).](/dotnet/api/microsoft.servicebus.messaging.queueclient)

Azure mesajlaşma altyapısının performansını artırmak için bkz. tasarım deseninin [zaman uyumsuz mesajlaşma](/previous-versions/msp-n-p/dn589781(v=pandp.10))bilgileri.

## <a name="consider-partitioning-service-bus-queues-and-topics"></a>Service Bus sıralarını ve konuları bölümlemeyi düşünün
### <a name="id"></a>ID
AP2004

### <a name="description"></a>Description
Service Bus mesajlaşma ile daha iyi performans için Service Bus kuyrukları ve konuları bölümleyin.

lütfen fikirlerinizi ve geri bildiriminizi [Azure Code Analysis geri bildirimde](https://social.msdn.microsoft.com/Forums/en-US/home)paylaşın.

### <a name="reason"></a>Nedeni
bölümlenmiş bir sıranın veya konunun genel performansı artık tek bir ileti aracısının veya mesajlaşma deposunun performansıyla sınırlı olmadığından, Service Bus kuyruklarını ve konularını bölümlemek, performans aktarım hızını ve hizmet kullanılabilirliğini artırır. Ayrıca, bir mesajlaşma deposunun geçici bir kesinti, bölümlenmiş bir kuyruğu veya konuyu kullanılamaz hale getirir. Daha fazla bilgi için bkz. [mesajlaşma varlıklarını bölümlendirme](/previous-versions/azure/dn520246(v=azure.100)).

### <a name="solution"></a>Çözüm
Aşağıdaki kod parçacığı, mesajlaşma varlıklarının nasıl bölümlenmesi gerektiğini gösterir.

```csharp
// Create partitioned topic.
NamespaceManager ns = NamespaceManager.CreateFromConnectionString(myConnectionString);
TopicDescription td = new TopicDescription(TopicName);
td.EnablePartitioning = true;
ns.CreateTopic(td);
```

daha fazla bilgi için bkz. [bölümlenmiş Service Bus kuyruklar ve konular | Microsoft Azure Blog](https://azure.microsoft.com/blog/2013/10/29/partitioned-service-bus-queues-and-topics/) ve [Microsoft Azure Service Bus bölümlenmiş sıra](https://code.msdn.microsoft.com/windowsazure/Service-Bus-Partitioned-7dfd3f1f) örneğine göz atın.

## <a name="do-not-set-sharedaccessstarttime"></a>SharedAccessStartTime ayarlama
### <a name="id"></a>ID
AP3001

### <a name="description"></a>Description
Paylaşılan erişim ilkesini hemen başlatmak için SharedAccessStartTimeset ' i Şu anki zamana göre kullanmaktan kaçının. Yalnızca paylaşılan erişim ilkesini daha sonra başlatmak istiyorsanız bu özelliği ayarlamanız gerekir.

lütfen fikirlerinizi ve geri bildiriminizi [Azure Code Analysis geri bildirimde](https://social.msdn.microsoft.com/Forums/en-US/home)paylaşın.

### <a name="reason"></a>Nedeni
Saat eşitleme, veri merkezleri arasında hafif bir zamana farklılık oluşmasına neden olur. Örneğin, bir depolama SAS ilkesinin başlangıç saatini DateTime kullanarak geçerli zaman olarak ayarlamayı düşünebilirsiniz. şimdi veya benzer bir yöntem SAS ilkesinin hemen geçerli olmasına neden olur. Ancak, veri merkezleri arasındaki hafif zaman farkları, bazı veri merkezi süreleri başlangıç zamanından biraz daha daha sonra olabileceğinden, bu nedenle sorun oluşmasına neden olabilir. Sonuç olarak, ilke ömrü çok kısa bir süre ayarlanmışsa SAS ilkesinin süresi hızla (veya hatta hemen) dolacak.

Azure depolama 'da paylaşılan erişim imzasını kullanma hakkında daha fazla bilgi için bkz. [tablo sas (paylaşılan erişim imzası), kuyruk sas ve Blob sas güncelleştirme-Microsoft Azure Depolama Team Blog-Site Home-MSDN blogları](https://blogs.msdn.microsoft.com/windowsazurestorage/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas/).

### <a name="solution"></a>Çözüm
Paylaşılan erişim ilkesinin başlangıç saatini ayarlayan ifadeyi kaldırın. Azure Code Analysis aracı bu sorun için bir çözüm sağlar. Güvenlik yönetimi hakkında daha fazla bilgi için lütfen tasarım deseninin [Valet anahtar düzenine](/previous-versions/msp-n-p/dn568102(v=pandp.10))bakın.

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

lütfen fikirlerinizi ve geri bildiriminizi [Azure Code Analysis geri bildirimde](https://social.msdn.microsoft.com/Forums/en-US/home)paylaşın.

### <a name="reason"></a>Nedeni
Dünya genelindeki farklı konumlardaki veri merkezleri saat sinyaliyle eşitlenir. Saat sinyalinin farklı konumlara aktarılması zaman aldığı için, her şeyin farklı coğrafi konumlardaki veri merkezleri arasında bir zaman farkı olabilir. Bu süre farkı, paylaşılan erişim ilkesi başlangıç zamanı ve süre sonu aralığını etkileyebilir. Bu nedenle, paylaşılan erişim ilkesinin hemen etkili olmasını sağlamak için başlangıç saatini belirtmeyin. Ayrıca, sona erme süresinin erken zaman aşımını engellemek için 5 dakikadan fazla olduğundan emin olun.

Azure depolama 'da paylaşılan erişim imzasını kullanma hakkında daha fazla bilgi için bkz. [tablo sas (paylaşılan erişim imzası), kuyruk sas ve Blob sas güncelleştirmesi-Microsoft Azure Depolama Team Blog-Site Home-MSDN blogları](https://blogs.msdn.microsoft.com/windowsazurestorage/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas/).

### <a name="solution"></a>Çözüm
Güvenlik yönetimi hakkında daha fazla bilgi için bkz. tasarım deseninin [Valet anahtar stili](/previous-versions/msp-n-p/dn568102(v=pandp.10)).

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

Daha fazla bilgi için bkz. [kapsayıcılar ve Bloblar için anonim genel okuma erişimini yapılandırma](/azure/storage/blobs/anonymous-read-access-configure?tabs=portal).

## <a name="use-cloudconfigurationmanager"></a>CloudConfigurationManager kullanma
### <a name="id"></a>ID
AP4000

### <a name="description"></a>Description
Azure Web sitesi ve Azure Mobil Hizmetleri gibi projeler için [ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) sınıfının kullanılması çalışma zamanı sorunları oluşturmayacaktır. Bununla birlikte, en iyi uygulama olarak, tüm Azure bulut uygulamalarına yönelik yapılandırmaların yönetilmesi için birleştirilmiş bir yöntem olarak bulutta[ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) kullanmak iyi bir fikirdir.

lütfen fikirlerinizi ve geri bildiriminizi [Azure Code Analysis geri bildirimde](https://social.msdn.microsoft.com/Forums/en-US/home)paylaşın.

### <a name="reason"></a>Nedeni
CloudConfigurationManager, uygulama ortamına uygun yapılandırma dosyasını okur.

[CloudConfigurationManager](/previous-versions/azure/)

### <a name="solution"></a>Çözüm
[Cloudconfigurationmanager sınıfını](/previous-versions/azure/reference/mt634650(v=azure.100))kullanmak için kodunuzu yeniden düzenleyin. bu sorun için bir kod sorunu, Azure Code Analysis aracı tarafından sağlanmaktadır.

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

lütfen fikirlerinizi ve geri bildiriminizi [Azure Code Analysis geri bildirimde](https://social.msdn.microsoft.com/Forums/en-US/home)paylaşın.

### <a name="reason"></a>Nedeni
Bağlantı dizelerinin hızlı bir şekilde değiştirilmesi gerektiğinde sorun ortaya çıkardığından, sabit kodlama bağlantı dizeleri hatalı bir uygulamadır. Ayrıca, projenin kaynak denetimine iade olması gerekiyorsa, dizelerin kaynak kodunda görüntülenebilmesi için, sabit kodlanmış bağlantı dizeleri güvenlik açıklarını ortaya çıkarabilir.

### <a name="solution"></a>Çözüm
Bağlantı dizelerini yapılandırma dosyalarında veya Azure ortamlarında depolayın.

* Tek başına uygulamalar için, bağlantı dizesi ayarlarını depolamak için app.config kullanın.
* IIS tarafından barındırılan Web uygulamaları için bağlantı dizelerini depolamak üzere web.config kullanın.
* ASP.NET vnext uygulamaları için, bağlantı dizelerini depolamak üzere configuration. json kullanın.

web.config veya app.config gibi yapılandırma dosyalarını kullanma hakkında daha fazla bilgi için bkz. [ASP.NET Web yapılandırma yönergeleri](/aspnet/web-forms/overview/deployment/visual-studio-web-deployment/web-config-transformations). Azure ortam değişkenlerinin nasıl çalıştığı hakkında bilgi için bkz. [Azure Web siteleri: uygulama dizeleri ve bağlantı dizeleri nasıl çalışır?](https://azure.microsoft.com/blog/2013/07/17/windows-azure-web-sites-how-application-strings-and-connection-strings-work/). Kaynak denetiminde bağlantı dizesini depolama hakkında bilgi için, bkz. [kaynak kodu deposunda depolanan dosyalardaki bağlantı dizeleri gibi hassas bilgileri yerleştirmekten kaçının](/aspnet/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/source-control).

## <a name="use-diagnostics-configuration-file"></a>Tanılama yapılandırma dosyası kullan
### <a name="id"></a>ID
AP5000

### <a name="description"></a>Description
Kodunuzda, Microsoft. WindowsAzure. Diagnostics programlama API 'sini kullanarak tanılama ayarlarını yapılandırmak yerine, tanılama ayarlarını Diagnostics. wadcfg dosyasında yapılandırmanız gerekir. (Veya Azure SDK 2,5 kullanıyorsanız, Diagnostics. wadcfgx). Bunu yaparak, kodunuzu yeniden derlemek zorunda kalmadan tanılama ayarlarını değiştirebilirsiniz.

lütfen fikirlerinizi ve geri bildiriminizi [Azure Code Analysis geri bildirimde](https://social.msdn.microsoft.com/Forums/en-US/home)paylaşın.

### <a name="reason"></a>Nedeni
Azure SDK 2,5 (Azure tanılama 1,3 kullanan) öncesinde, Azure Tanılama (WAD) birkaç farklı yöntem kullanılarak yapılandırılabilir: zorunlu kod, bildirime dayalı yapılandırma veya varsayılan yapılandırmayı kullanarak, depolama alanındaki yapılandırma blobuna ekleme. Ancak, tanılamayı yapılandırmak için tercih edilen yöntem, uygulama projesindeki bir XML yapılandırma dosyası (SDK 2,5 ve üzeri için tanılama. wadcfgx) kullanmaktır. Bu yaklaşımda, Diagnostics. wadcfg dosyası yapılandırmayı tamamen tanımlar ve ' de güncelleştirilecektir ve yeniden dağıtılabilir. Tanılama. wadcfg yapılandırma dosyasının kullanımını [Diagnosticmonitor](/previous-versions/azure/reference/ee758597(v=azure.100))veya [Roleınstancediagnosticmanager](/previous-versions/azure/reference/ee773157(v=azure.100))sınıflarını kullanarak yapılandırma ayarlarının programlı yöntemleriyle karıştırma, karışıklıklara yol açabilir. Daha fazla bilgi için bkz. [Azure tanılama yapılandırmayı başlatma veya değiştirme](/previous-versions/azure/hh411537(v=azure.100)) .

WAD 1,3 (Azure SDK 2,5 ' de bulunur) ile başlayarak, tanılamayı yapılandırmak için artık kodu kullanmak mümkün değildir. Sonuç olarak, yalnızca tanılama uzantısını uygularken veya güncelleştirirken yapılandırmayı sağlayabilirsiniz.

### <a name="solution"></a>Çözüm
Tanılama ayarlarını tanılama yapılandırma dosyasına (SDK 2,5 ve üzeri için tanılama. wadcfg veya Diagnostics. wadcfgx) taşımak için tanılama yapılandırma tasarımcısını kullanın. Ayrıca, [Azure SDK 2,5](https://social.msdn.microsoft.com/Forums/en-US/home) ' i yükleyip en son Tanılama özelliğini kullanmanız önerilir.

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

lütfen fikirlerinizi ve geri bildiriminizi [Azure Code Analysis geri bildirimde](https://social.msdn.microsoft.com/Forums/en-US/home)paylaşın.

### <a name="reason"></a>Nedeni
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
Azure uygulamalarını iyileştirme ve sorunlarını giderme hakkında daha fazla bilgi için bkz. [Visual Studio kullanarak Azure App Service bir Web uygulamasında sorun giderme](/azure/app-service/web-sites-dotnet-troubleshoot-visual-studio).
