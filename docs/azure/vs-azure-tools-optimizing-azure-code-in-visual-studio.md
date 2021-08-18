---
title: Azure kodunuzu iyileştirme
description: Azure kod iyileştirme araçlarının Visual Studio, kodunuzun daha sağlam ve daha iyi performans sağlama konusunda nasıl yardımcı olduğunu öğrenin.
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: 9836f13ac97641876746e0c514f11efc297d2975
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122134889"
---
# <a name="optimizing-your-azure-code"></a>Azure Kodunuzu İyileştirme
Microsoft Azure kullanan uygulamalar programlarken, bir bulut ortamında uygulama ölçeklenebilirliği, davranış ve performans sorunlarını önlemeye yardımcı olmak için izlemeniz gereken bazı kodlama uygulamaları vardır. Microsoft, yaygın olarak karşılaşılan sorunlardan birkaçını algılayan ve tanıtan bir Azure Code Analysis aracı sağlar ve bunları çözmenize yardımcı olur. aracı Visual Studio NuGet aracılığıyla indirebilirsiniz.

## <a name="azure-code-analysis-rules"></a>Azure Code Analysis kuralları
azure Code Analysis aracı, performans etkileyen bilinen sorunları bulduğunda azure kodunuzu otomatik olarak işaretlemek için aşağıdaki kuralları kullanır. Algılanan sorunlar bir uyarı veya derleyici hatası olarak görünür. Uyarı veya hatayı çözmek için kod düzeltmeleri veya öneriler, genellikle ampul simgesiyle sağlanır.

## <a name="avoid-using-default-in-process-session-state-mode"></a>Varsayılan (işlem içi) oturum durumu modunu kullanmaktan kaçının
### <a name="id"></a>ID
AP0000

### <a name="description"></a>Açıklama
Bulut uygulamaları için varsayılan (işlem içi) oturum durumu modunu kullanırsanız, oturum durumunu kaybedebilirsiniz.

lütfen fikirlerinizi ve geri bildiriminizi [Azure Code Analysis geri bildirimde](https://social.msdn.microsoft.com/Forums/en-US/home)paylaşın.

### <a name="reason"></a>Nedeni
Varsayılan olarak, web.config dosyasında belirtilen oturum durumu modu işlem içinde olur. Ayrıca, yapılandırma dosyasında bir giriş belirtilmemişse, oturum durumu modu varsayılan olarak işlem içinde olur. İşlem içi modu, oturum durumunu Web sunucusunda bellekte depolar. Bir örnek yeniden başlatıldığında veya yük dengeleme veya yük devretme desteği için yeni bir örnek kullanıldığında, Web sunucusunda bellekte depolanan oturum durumu kaydedilmez. Bu durum, uygulamanın bulutta ölçeklenebilir olmasını önler.

ASP.NET oturum durumu, oturum durumu verileri için birkaç farklı depolama seçeneğini destekler: ınproc, StateServer, SQLServer, özel ve kapalı. [Redin Için Azure oturum durumu sağlayıcısı](https://devblogs.microsoft.com/aspnet/announcing-asp-net-session-state-provider-for-redis-preview-release/)gibi bir dış oturum durumu deposunda verileri barındırmak için özel mod kullanmanız önerilir.

### <a name="solution"></a>Çözüm
Önerilen bir çözüm, oturum durumunu yönetilen bir önbellek hizmetinde depobir çözümdür. Oturum durumunu depolamak için [Azure oturum durumu sağlayıcısı 'Nı redsıs için](https://devblogs.microsoft.com/aspnet/announcing-asp-net-session-state-provider-for-redis-preview-release/) kullanmayı öğrenin. Ayrıca, uygulamanızın bulutta ölçeklenebilir olduğundan emin olmak için oturum durumunu başka yerlerde de saklayabilirsiniz. Alternatif çözümler hakkında daha fazla bilgi edinmek için lütfen [oturum durumu modlarını](/previous-versions/ms178586(v=vs.140))okuyun.

## <a name="run-method-should-not-be-async"></a>Run yöntemi zaman uyumsuz olmamalıdır
### <a name="id"></a>ID
AP1000

### <a name="description"></a>Açıklama
[Run ()](/previous-versions/azure/reference/ee772746(v=azure.100)) yönteminin dışında zaman uyumsuz Yöntemler ( [await](/dotnet/csharp/language-reference/operators/await)gibi) oluşturun ve sonra [()](/previous-versions/azure/reference/ee772746(v=azure.100))zaman uyumsuz yöntemleri çağırın. [[Run ()](/previous-versions/azure/reference/ee772746(v=azure.100))](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) yönteminin zaman uyumsuz olarak bildirilmesi, çalışan rolünün yeniden başlatma döngüsü girmesine neden olur.

lütfen fikirlerinizi ve geri bildiriminizi [Azure Code Analysis geri bildirimde](https://social.msdn.microsoft.com/Forums/en-US/home)paylaşın.

### <a name="reason"></a>Nedeni
[Run ()](/previous-versions/azure/reference/ee772746(v=azure.100)) yöntemi içinde zaman uyumsuz yöntemlerin çağrılması, bulut hizmeti çalışma zamanının çalışan rolünü geri dönüştürmesine neden olur. Bir çalışan rolü başladığında, tüm program yürütmesi [Run ()](/previous-versions/azure/reference/ee772746(v=azure.100)) yöntemi içinde gerçekleşir. Run yönteminden çıkıldığında çalışan rolünün yeniden başlatılmasına neden olur. Çalışan rolü çalışma zamanı zaman uyumsuz yöntemi ziyaret edildiğinde, zaman uyumsuz yöntemden sonra tüm işlemleri dağıtır ve ardından döndürür. Bu, çalışan rolünün çalıştırma yönteminden çıkmasına ve yeniden başlatılmasına neden olur. Yürütmenin bir sonraki yinelemesinde, çalışan rolü zaman uyumsuz yöntemi tekrar ziyaret ediyor ve yeniden başlatır, böylece çalışan rolü de yeniden geri dönüşüme neden olur.

### <a name="solution"></a>Çözüm
Tüm zaman uyumsuz işlemleri [Run ()](/previous-versions/azure/reference/ee772746(v=azure.100)) yöntemi dışında yerleştirin. Ardından, RunAsync () gibi run yönteminin içinden yeniden düzenlenmiş Async yöntemini çağırın. bekle. Azure Code Analysis aracı, bu sorunu gidermenize yardımcı olabilir.

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

## <a name="use-service-bus-shared-access-signature-authentication"></a>Service Bus paylaşılan erişim imzası kimlik doğrulamasını kullanma
### <a name="id"></a>ID
AP2000

### <a name="description"></a>Açıklama
Kimlik doğrulaması için paylaşılan erişim Imzasını (SAS) kullanın. Service Bus kimlik doğrulaması için Access Control Service (ACS) kullanım dışı bırakılıyor.

lütfen fikirlerinizi ve geri bildiriminizi [Azure Code Analysis geri bildirimde](https://social.msdn.microsoft.com/Forums/en-US/home)paylaşın.

### <a name="reason"></a>Nedeni
gelişmiş güvenlik için Azure Active Directory, ACS kimlik doğrulamasını SAS kimlik doğrulamasıyla değiştiriyor. geçiş planı hakkında bilgi için bkz. [Azure Active Directory ACS 'nin geleceği](https://cloudblogs.microsoft.com/enterprisemobility/2013/06/22/azure-active-directory-is-the-future-of-acs/) .

### <a name="solution"></a>Çözüm
Uygulamalarınızda SAS kimlik doğrulamasını kullanın. Aşağıdaki örnek, bir hizmet veri yolu ad alanına veya varlığına erişmek için mevcut bir SAS belirtecinin nasıl kullanılacağını gösterir.

```csharp
MessagingFactory listenMF = MessagingFactory.Create(endpoints, new StaticSASTokenProvider(subscriptionToken));
SubscriptionClient sc = listenMF.CreateSubscriptionClient(topicPath, subscriptionName);
BrokeredMessage receivedMessage = sc.Receive();
```

Daha fazla bilgi için aşağıdaki konulara bakın.

* Genel bakış için bkz. [Service Bus Ile paylaşılan erişim Imzası kimlik doğrulaması](/azure/service-bus-messaging/service-bus-sas)
* [Service Bus ile paylaşılan erişim Imzası kimlik doğrulaması kullanma](/azure/service-bus-messaging/service-bus-sas)

## <a name="consider-using-onmessage-method-to-avoid-receive-loop"></a>"Alma döngüsü" önlemek için OnMessage metodunu kullanmayı düşünün
### <a name="id"></a>ID
AP2002

### <a name="description"></a>Açıklama
"Alma döngüsüne" engel olmak için **OnMessage** metodunu **çağırmak, iletileri alma yöntemi çağrılmadan** daha iyi bir çözümdür. Ancak, **alma** yöntemini kullanmanız gerekiyorsa ve varsayılan olmayan bir sunucu bekleme süresi belirtirseniz, sunucu bekleme süresinin bir dakikadan fazla olduğundan emin olun.

lütfen fikirlerinizi ve geri bildiriminizi [Azure Code Analysis geri bildirimde](https://social.msdn.microsoft.com/Forums/en-US/home)paylaşın.

### <a name="reason"></a>Nedeni
**OnMessage** çağrılırken, istemci kuyruğu veya aboneliği sürekli yoklayan bir iç ileti göndericisi başlatır. Bu ileti göndericisi, ileti alma çağrısını veren sonsuz bir döngü içeriyor. Çağrı zaman aşımına uğrarsa, yeni bir çağrı yayınlar. Zaman aşımı aralığı, kullanılmakta olan [Messagingfactory](/dotnet/api/microsoft.servicebus.messaging.messagingfactory)'Nin [OperationTimeout](/dotnet/api/microsoft.servicebus.messaging.messagingfactorysettings) özelliğinin değerine göre belirlenir.

**OnMessage** 'i **alma** ile karşılaştırıldığında kullanmanın avantajı, kullanıcıların iletileri el ile yoklamasını, özel durumları işlemesini, paralel olarak birden çok iletiyi işlemesini ve iletileri tamamlamasını desteklemez.

**Alma** 'yı varsayılan değerini kullanmadan çağırırsanız, *ServerWaitTime* değerinin bir dakikadan fazla olduğundan emin olun. *ServerWaitTime* 'in birden fazla dakika olarak ayarlanması, iletinin tam olarak alınmadan önce sunucunun zaman aşımına uğramasını önler.

### <a name="solution"></a>Çözüm
Önerilen kullanımlar için lütfen aşağıdaki kod örneklerine bakın. Daha fazla ayrıntı için bkz. [Queueclient. OnMessage yöntemi (Microsoft. ServiceBus. Messaging)](/dotnet/api/microsoft.servicebus.messaging.queueclient) ve [Queueclient. Receive yöntemi (Microsoft. ServiceBus. Messaging)](/dotnet/api/microsoft.servicebus.messaging.queueclient).

Azure mesajlaşma altyapısının performansını artırmak için bkz. tasarım deseninin [zaman uyumsuz mesajlaşma](/previous-versions/msp-n-p/dn589781(v=pandp.10))bilgileri.

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

## <a name="consider-using-asynchronous-service-bus-methods"></a>zaman uyumsuz Service Bus yöntemleri kullanmayı düşünün
### <a name="id"></a>ID
AP2003

### <a name="description"></a>Açıklama
aracılı mesajlaşma ile performansı artırmak için zaman uyumsuz Service Bus yöntemler kullanın.

lütfen fikirlerinizi ve geri bildiriminizi [Azure Code Analysis geri bildirimde](https://social.msdn.microsoft.com/Forums/en-US/home)paylaşın.

### <a name="reason"></a>Nedeni
Zaman uyumsuz yöntemlerin kullanılması uygulama programı eşzamanlılık imkanı sağladığından her çağrının yürütülmesi ana iş parçacığını engellemez. Service Bus mesajlaşma yöntemlerini kullanırken bir işlem (gönderme, alma, silme, vb.) gerçekleştirmek zaman alır. bu süre, isteğin ve yanıtın gecikme süresinin yanı sıra Service Bus hizmeti tarafından işlemin işlenmesini içerir. Zaman başına işlem sayısını artırmak için, işlemlerin eşzamanlı olarak yürütülmesi gerekir. daha fazla bilgi için lütfen [Service Bus aracılı mesajlaşma kullanarak performans geliştirmeleri için en iyi uygulamalara](/previous-versions/azure/hh528527(v=azure.100))bakın.

### <a name="solution"></a>Çözüm
Önerilen zaman uyumsuz yöntemi kullanma hakkında bilgi için bkz. [Queueclient sınıfı (Microsoft. ServiceBus. Messaging)](/dotnet/api/microsoft.servicebus.messaging.queueclient) .

Azure mesajlaşma altyapısının performansını geliştirmek için bkz. Tasarım deseni [Zaman Uyumsuz Mesajlaşma İlkeleri.](/previous-versions/msp-n-p/dn589781(v=pandp.10))

## <a name="consider-partitioning-service-bus-queues-and-topics"></a>Kuyrukları ve Service Bus bölümlemeyi göz önünde bulundurabilirsiniz
### <a name="id"></a>ID
AP2004

### <a name="description"></a>Açıklama
Özel Service Bus daha iyi performans için kuyrukları ve konuları Service Bus bölümleme.

Lütfen görüşlerinizi ve geri bildiriminizi [Azure'da Code Analysis paylaşın.](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="reason"></a>Nedeni
Bölümlenmiş Service Bus veya konunun genel aktarım hızı artık tek bir ileti aracısı veya mesajlaşma deposu performansıyla sınırlı olmadığı için, kuyrukları ve konu başlıklarını bölümleme, performans aktarım hızını ve hizmet kullanılabilirliğini artırır. Buna ek olarak, mesajlaşma deposunun geçici bir kesintisi, bölümlenmiş bir kuyruğu veya konuyu kullanılamaz hale getirir. Daha fazla bilgi için [bkz. Mesajlaşma Varlıklarını Bölümleme.](/previous-versions/azure/dn520246(v=azure.100))

### <a name="solution"></a>Çözüm
Aşağıdaki kod parçacığında, mesajlaşma varlıklarının nasıl bölümlen olduğu gösterir.

```csharp
// Create partitioned topic.
NamespaceManager ns = NamespaceManager.CreateFromConnectionString(myConnectionString);
TopicDescription td = new TopicDescription(TopicName);
td.EnablePartitioning = true;
ns.CreateTopic(td);
```

Daha fazla bilgi için [bkz. Bölümlenmiş Service Bus Kuyrukları ve Konu Başlıkları | Microsoft Azure Blog'da](https://azure.microsoft.com/blog/2013/10/29/partitioned-service-bus-queues-and-topics/) bölümlenmiş [Microsoft Azure Service Bus örneğine göz](https://code.msdn.microsoft.com/windowsazure/Service-Bus-Partitioned-7dfd3f1f) atabilirsiniz.

## <a name="do-not-set-sharedaccessstarttime"></a>SharedAccessStartTime ayarlanma
### <a name="id"></a>ID
AP3001

### <a name="description"></a>Açıklama
Paylaşılan Erişim ilkesi hemen başlatmak için SharedAccessStartTimeset'i geçerli saatle birlikte kullanmaktan kaçınmalısınız. Bu özelliği yalnızca Paylaşılan Erişim ilkesi daha sonra başlatmak istediğiniz zaman ayarlayabilirsiniz.

Lütfen görüşlerinizi ve geri bildiriminizi [Azure'da Code Analysis paylaşın.](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="reason"></a>Nedeni
Saat eşitlemesi, veri merkezleri arasında küçük bir zaman farkına neden olur. Örneğin, bir depolama SAS ilkesi başlangıç saatlerini DateTime kullanarak geçerli saat olarak ayarlamayı mantıksal olarak düşünebilirsiniz.Şimdi veya benzer bir yöntem SAS ilkesi hemen etkili olur. Ancak veri merkezleri arasındaki küçük zaman farkları bu soruna neden olabilir çünkü bazı veri merkezi süreleri başlangıç zamanından biraz daha uzun, bazıları ise önünde olabilir. Sonuç olarak, ilke ömrü çok kısa ayarlanırsa SAS ilkesi hızlı bir şekilde (hatta hemen) sona erer.

Azure depolamada Paylaşılan Erişim İmzası kullanma hakkında daha fazla rehberlik için bkz. Tablo [SAS'ye Giriş (Paylaşılan](https://blogs.msdn.microsoft.com/windowsazurestorage/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas/)Erişim İmzası), Kuyruk SAS ve Blob SAS'ye güncelleştirme - Microsoft Azure Depolama Ekip Blogu - Site Giriş - MSDN Blogları.

### <a name="solution"></a>Çözüm
Paylaşılan erişim ilkesi başlangıç saatlerini ayaran deyimini kaldırın. Azure Code Analysis aracı bu sorun için bir düzeltme sağlar. Güvenlik yönetimi hakkında daha fazla bilgi için lütfen Vale Anahtarı Deseni [tasarım modeline bakın.](/previous-versions/msp-n-p/dn568102(v=pandp.10))

Aşağıdaki kod parçacığında bu sorunun kod düzeltmesi gösterildi.

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

## <a name="shared-access-policy-expiry-time-must-be-more-than-five-minutes"></a>Paylaşılan Erişim İlkesi süre sonu beş dakikadan uzun olması gerekir
### <a name="id"></a>ID
AP3002

### <a name="description"></a>Açıklama
"Saat çarpıklığı" olarak bilinen bir koşul nedeniyle farklı konumlarda yer alan veri merkezleri arasında saatlerde beş dakika kadar fark olabilir. SAS ilke belirtecinden önceki sürenin dolmasını önlemek için süre sonu süresini beş dakikadan uzun olacak şekilde ayarlayın.

Lütfen görüşlerinizi ve geri bildiriminizi [Azure'da Code Analysis paylaşın.](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="reason"></a>Nedeni
Dünyanın farklı konumlarında yer alan veri merkezleri saat sinyaliyle eşitlenir. Saat sinyalinin farklı konumlara seyahatsi zaman alalı olduğundan, her şeyin eşitlenmesi gerekirken farklı coğrafi konumlarda yer alan veri merkezleri arasında zaman varyansı olabilir. Bu zaman farkı Paylaşılan Erişim ilkesi başlangıç saati ve sona erme aralığını etkileyebilir. Bu nedenle, Paylaşılan Erişim ilkesi hemen geçerli olduğundan emin olmak için başlangıç saati belirtmeyin. Ayrıca, erken zaman aşımını önlemek için süre sonu süresinin 5 dakikadan uzun olduğundan emin olun.

Azure depolamada Paylaşılan Erişim İmzası kullanma hakkında daha fazla bilgi için bkz. Tablo [SAS'ye Giriş (Paylaşılan](https://blogs.msdn.microsoft.com/windowsazurestorage/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas/)Erişim İmzası), KUYRUK SAS ve Blob SAS'ye güncelleştirme - Microsoft Azure Depolama Ekip Blogu - Site Giriş - MSDN Blogları.

### <a name="solution"></a>Çözüm
Güvenlik yönetimi hakkında daha fazla bilgi için Vale Anahtarı Deseni [tasarım modeline bakın.](/previous-versions/msp-n-p/dn568102(v=pandp.10))

Aşağıda, Paylaşılan Erişim ilkesi başlangıç zamanı belirtmeyen bir örnek ve bir örnek ve ardından ve ve ardından bir örnek veılır.

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

Aşağıda, ilke süre sonu süresi beş dakikadan uzun olan bir Paylaşılan Erişim ilkesi başlangıç zamanı belirtme örneği verilmektedir.

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

Daha fazla bilgi için [bkz. Kapsayıcılar ve bloblar için anonim genel okuma erişimini yapılandırma.](/azure/storage/blobs/anonymous-read-access-configure?tabs=portal)

## <a name="use-cloudconfigurationmanager"></a>CloudConfigurationManager kullanma
### <a name="id"></a>ID
AP4000

### <a name="description"></a>Açıklama
Azure Web Sitesi ve Azure mobil hizmetleri gibi projeler için [ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) sınıfını kullanmak çalışma zamanı sorunlarına neden olmayacaktır. Ancak, en iyi uygulama olarak, tüm Azure Bulut uygulamaları için yapılandırmaları yönetmenin birleşik bir yolu olarak Cloud[ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) kullanmak iyi bir fikirdir.

Lütfen görüşlerinizi ve geri bildiriminizi [Azure'da Code Analysis paylaşın.](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="reason"></a>Nedeni
CloudConfigurationManager, uygulama ortamına uygun yapılandırma dosyasını okur.

[CloudConfigurationManager](/previous-versions/azure/)

### <a name="solution"></a>Çözüm
[CloudConfigurationManager Sınıfını kullanmak için kodunuzu yeniden düzenleme.](/previous-versions/azure/reference/mt634650(v=azure.100)) Bu soruna ilişkin bir kod düzeltmesi, Azure Code Analysis sağlanır.

Aşağıdaki kod parçacığında bu sorunun kod düzeltmesi gösterildi. Değiştir

`var settings = ConfigurationManager.AppSettings["mySettings"];`

örneklerini şununla değiştirin:

`var settings = CloudConfigurationManager.GetSetting("mySettings");`

Yapılandırma ayarının bir dosyada veya dosyada nasıl depo App.config Web.config: Ayarları yapılandırma dosyasının appSettings bölümüne ekleyin. Aşağıda, önceki Web.config örnek için aşağıdaki örnek bir dosya ve bir sonraki örnek vetir.

```xml
<appSettings>
    <add key="webpages:Version" value="3.0.0.0" />
    <add key="webpages:Enabled" value="false" />
    <add key="ClientValidationEnabled" value="true" />
    <add key="UnobtrusiveJavaScriptEnabled" value="true" />
    <add key="mySettings" value="[put_your_setting_here]"/>
  </appSettings>
```

## <a name="avoid-using-hard-coded-connection-strings"></a>Sabit kodlu bağlantı dizelerini kullanmaktan kaçının
### <a name="id"></a>ID
AP4001

### <a name="description"></a>Açıklama
Sabit kodlu bağlantı dizelerini kullanıyorsanız ve bunları daha sonra güncelleştirmeniz gerekirse, kaynak kodunda değişiklik yapma ve uygulamayı yeniden derlemeniz gerekir. Ancak, bağlantı dizelerinizi bir yapılandırma dosyasında depolarsanız, bunları daha sonra yalnızca yapılandırma dosyasını güncelleştirerek değiştirebilirsiniz.

Lütfen görüşlerinizi ve geri bildiriminizi [Azure'da Code Analysis paylaşın.](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="reason"></a>Nedeni
Bağlantı dizelerinin hızlı bir şekilde değişmesi gereken sorunlara neden olduğundan bağlantı dizelerini sabit kodlamak kötü bir uygulamadır. Ayrıca, projenin kaynak denetimine iade edişi gerekirse, sabit kodlu bağlantı dizeleri, dizeler kaynak kodda görüntülenene kadar güvenlik açıklarına neden olur.

### <a name="solution"></a>Çözüm
Bağlantı dizelerini yapılandırma dosyalarında veya Azure ortamlarında depolar.

* Tek başına uygulamalar için bağlantı app.config depolamak üzere tek başına uygulama kullanın.
* IIS tarafından barındırılan web uygulamaları için, bağlantı dizelerini web.config web uygulamalarını kullanın.
* vNext ASP.NET için, bağlantı dizelerini configuration.jsiçin üzerinde bağlantı dizeleri kullanın.

Web Yapılandırma Yönergeleri gibi yapılandırma dosyalarını kullanma hakkında web.config app.config [bkz. ASP.NET Yapılandırma Yönergeleri.](/aspnet/web-forms/overview/deployment/visual-studio-web-deployment/web-config-transformations) Azure ortam değişkenlerinin çalışması hakkında bilgi için [bkz. Azure Web Siteleri: Uygulama Dizeleri ve Bağlantı Dizeleri Nasıl Çalışır?](https://azure.microsoft.com/blog/2013/07/17/windows-azure-web-sites-how-application-strings-and-connection-strings-work/) Bağlantı dizesini kaynak denetiminde depolama hakkında bilgi için bkz. Bağlantı dizeleri gibi hassas bilgileri kaynak kod deposunda [depolanan dosyalara koymaktan kaçının.](/aspnet/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/source-control)

## <a name="use-diagnostics-configuration-file"></a>Tanılama yapılandırma dosyasını kullanma
### <a name="id"></a>ID
AP5000

### <a name="description"></a>Açıklama
Microsoft.WindowsAzure.Diagnostics programlama API'sini kullanmak gibi tanılama ayarlarını kodunuzla yapılandırmak yerine diagnostics.wadcfg dosyasında tanılama ayarlarını yapılandırmanız gerekir. (Veya Azure SDK 2.5 kullanıyorsanız diagnostics.wadcfgx). Bunu yaparak, kodunuzu yeniden derlemek zorunda kalmadan tanılama ayarlarını değiştirebilirsiniz.

Lütfen görüşlerinizi ve geri bildiriminizi [Azure'da Code Analysis paylaşın.](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="reason"></a>Nedeni
Azure SDK 2.5 'den (Azure tanılama 1.3 kullanan) önce, Azure Tanılama (WAD) birkaç farklı yöntem kullanılarak yalıtabilir: depolamada yapılandırma blobu ekleme, uygulamalı kod, bildirimli yapılandırma veya varsayılan yapılandırma kullanılarak. Ancak, tanılamayı yapılandırmanın tercih edilen yolu, uygulama projesinde bir XML yapılandırma dosyası (SDK 2.5 ve sonrası için diagnostics.wadcfgx veya diagnostics.wadcfgx) kullanmaktır. Bu yaklaşımda diagnostics.wadcfg dosyası yapılandırmayı tamamen tanımlar ve istediğiniz zaman güncelleştirilebilir ve yeniden dağıtılabilir. Tanılama. wadcfg yapılandırma dosyasının kullanımını [Diagnosticmonitor](/previous-versions/azure/reference/ee758597(v=azure.100))veya [Roleınstancediagnosticmanager](/previous-versions/azure/reference/ee773157(v=azure.100))sınıflarını kullanarak yapılandırma ayarlarının programlı yöntemleriyle karıştırma, karışıklıklara yol açabilir. Daha fazla bilgi için bkz. [Azure tanılama yapılandırmayı başlatma veya değiştirme](/previous-versions/azure/hh411537(v=azure.100)) .

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

### <a name="description"></a>Açıklama
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
