---
title: Azure kodunuzu iyileştirme
description: Kodunuzu daha sağlam ve çökmelerin hale iyileştirme araçları Visual Studio'da Azure nasıl kod hakkında yardımcı olduğunu öğrenin.
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
ms.openlocfilehash: b5deb4a3abc944d40fdf94f6d9b6aaf3237e6be7
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298972"
---
# <a name="optimizing-your-azure-code"></a>Azure Kodunuzu İyileştirme
Microsoft Azure kullanan uygulamalar programlama, uygulama ölçeklenebilirlik, davranış ve bulut ortamlarında performans sorunlarını önlemek için izlemeniz gereken kodlama bazı yöntemler vardır. Microsoft tanır ve birkaç bu sık karşılaşılan sorunları tanımlar ve bunları çözmenize yardımcı olan bir Azure Kod Analizi aracı sağlar. NuGet aracılığıyla Visual Studio araç indirebilirsiniz.

## <a name="azure-code-analysis-rules"></a>Azure Kod Analizi kuralları
Azure Kod Analizi aracına performansı etkileyen bilinen bir sorun bulduğunda Azure kodunuzu otomatik olarak işaretlemek için aşağıdaki kuralları kullanır. Algılanan sorunları bir uyarı olarak görünür veya derleyici hataları. Kod düzeltmeleri veya uyarı veya hatayı gidermek için önerileri genellikle bir ampul simgesini sağlanır.

## <a name="avoid-using-default-in-process-session-state-mode"></a>Varsayılan (işlem içi) oturum durumu modu kullanmaktan kaçının
### <a name="id"></a>Kimlik
AP0000

### <a name="description"></a>Açıklama
Bulut uygulamaları için varsayılan (işlem içi) oturum durumu modunu kullanıyorsanız, oturum durumu kaybedebilir.

Lütfen [Azure kod analizi geri bildirimi](https://go.microsoft.com/fwlink/?LinkId=403771)'nde fikirlerinizi ve geri bildiriminizi paylaşın.

### <a name="reason"></a>Neden
Varsayılan olarak, işlem içi oturum durumu modunu web.config dosyasında belirtilen. Ayrıca, yapılandırma dosyasında belirtilen giriş, oturum durumu modu işlem içi varsayılan kullanır. İşlem modu, web sunucusu üzerindeki bellekte oturum durumunu depolar. Örneği yeniden başlatılır ya da yeni bir örneği, Yük Dengeleme veya yük devretme desteği için kullanılan web sunucusu üzerindeki bellekte oturum durumu kaydedilmez. Bu durum uygulamanın bulutta ölçeklenebilir olmasını engeller.

ASP.NET oturum durumu için oturum durumu verilerini birkaç farklı depolama seçeneklerini destekler: InProc, StateServer, SQLServer, özel ve kapalı. [Redin Için Azure oturum durumu sağlayıcısı](https://go.microsoft.com/fwlink/?LinkId=401521)gibi bir dış oturum durumu deposunda verileri barındırmak için özel mod kullanmanız önerilir.

### <a name="solution"></a>Çözüm
Bir yönetilen önbellek hizmeti üzerinde oturum durumunu depolamak için önerilen bir çözüm var. Oturum durumunu depolamak için [Azure oturum durumu sağlayıcısı 'Nı redsıs için](https://go.microsoft.com/fwlink/?LinkId=401521) kullanmayı öğrenin. Oturum durumu, bulutta uygulamanızın ölçeklenebilir olduğundan emin olmak için diğer yerlerde da depolayabilirsiniz. Alternatif çözümler hakkında daha fazla bilgi edinmek için lütfen [oturum durumu modlarını](https://msdn.microsoft.com/library/ms178586)okuyun.

## <a name="run-method-should-not-be-async"></a>Zaman uyumsuz çalışma yöntemi olmamalıdır
### <a name="id"></a>Kimlik
AP1000

### <a name="description"></a>Açıklama
[Run ()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) yönteminin dışında zaman uyumsuz Yöntemler ( [await](https://msdn.microsoft.com/library/hh156528.aspx)gibi) oluşturun ve sonra [()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)zaman uyumsuz yöntemleri çağırın. [[Run ()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) yönteminin zaman uyumsuz olarak bildirilmesi, çalışan rolünün yeniden başlatma döngüsü girmesine neden olur.

Lütfen [Azure kod analizi geri bildirimi](https://go.microsoft.com/fwlink/?LinkId=403771)'nde fikirlerinizi ve geri bildiriminizi paylaşın.

### <a name="reason"></a>Neden
[Run ()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) yöntemi içinde zaman uyumsuz yöntemlerin çağrılması, bulut hizmeti çalışma zamanının çalışan rolünü geri dönüştürmesine neden olur. Bir çalışan rolü başladığında, tüm program yürütmesi [Run ()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) yöntemi içinde gerçekleşir. [Run ()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) yönteminden çıkılırken çalışan rolünün yeniden başlatılmasına neden olur. Çalışan rolü çalışma zamanı zaman uyumsuz yöntemin ulaştığında, zaman uyumsuz yöntemin sonra tüm işlemleri gönderir ve döndürür. Bu, çalışan rolünün [[[[Run ()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) yönteminden çıkmasına ve yeniden başlatılmasına neden olur. Yürütme sonraki yinelemesine, çalışan rolü zaman uyumsuz yöntem yeniden ziyaret sayısı ve yeniden aynı zamanda geri dönüştürmek çalışan rolü neden yeniden başlatır.

### <a name="solution"></a>Çözüm
Tüm zaman uyumsuz işlemleri [Run ()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) yöntemi dışında yerleştirin. Ardından, yeniden düzenlenmiş Async yöntemini [[Run ()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) yönteminin Içinden RunAsync () gibi çağırın. bekle. Azure Kod Analizi aracı, bu sorunu gidermenize yardımcı olabilir.

Aşağıdaki kod parçacığını bu sorunla ilgili kod düzeltme gösterir:

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

## <a name="use-service-bus-shared-access-signature-authentication"></a>Service Bus paylaşılan erişim imzası kimlik doğrulaması kullan
### <a name="id"></a>Kimlik
AP2000

### <a name="description"></a>Açıklama
Paylaşılan erişim imzası (SAS) kimlik doğrulaması için kullanın. Hizmet veri yolu kimlik doğrulaması için Access Control Service (ACS) kullanımdan kaldırılıyor.

Lütfen [Azure kod analizi geri bildirimi](https://go.microsoft.com/fwlink/?LinkId=403771)'nde fikirlerinizi ve geri bildiriminizi paylaşın.

### <a name="reason"></a>Neden
Gelişmiş güvenlik için SAS kimlik doğrulaması ile ACS kimlik doğrulaması Azure Active Directory yerini alıyor. Geçiş planı hakkında bilgi için bkz. [Azure ACTIVE DIRECTORY ACS 'nin geleceği](https://cloudblogs.microsoft.com/enterprisemobility/2013/06/22/azure-active-directory-is-the-future-of-acs/) .

### <a name="solution"></a>Çözüm
SAS kimlik doğrulaması, uygulamalarınızda kullanabilirsiniz. Aşağıdaki örnek, bir service bus ad alanı veya varlık erişmek için var olan bir SAS belirteci kullanmayı gösterir.

```csharp
MessagingFactory listenMF = MessagingFactory.Create(endpoints, new StaticSASTokenProvider(subscriptionToken));
SubscriptionClient sc = listenMF.CreateSubscriptionClient(topicPath, subscriptionName);
BrokeredMessage receivedMessage = sc.Receive();
```

Daha fazla bilgi için aşağıdaki konulara bakın.

* Genel bakış için bkz. [Service Bus Ile paylaşılan erişim Imzası kimlik doğrulaması](https://msdn.microsoft.com/library/dn170477.aspx)
* [Service Bus ile paylaşılan erişim Imzası kimlik doğrulaması kullanma](https://msdn.microsoft.com/library/dn205161.aspx)

## <a name="consider-using-onmessage-method-to-avoid-receive-loop"></a>"Döngü Al" önlemek için Onmessageoptions yöntemi kullanmayı düşünün
### <a name="id"></a>Kimlik
AP2002

### <a name="description"></a>Açıklama
"Alma döngüsüne" engel olmak için **OnMessage** metodunu **çağırmak, iletileri alma yöntemi çağrılmadan** daha iyi bir çözümdür. Ancak, **alma** yöntemini kullanmanız gerekiyorsa ve varsayılan olmayan bir sunucu bekleme süresi belirtirseniz, sunucu bekleme süresinin bir dakikadan fazla olduğundan emin olun.

Lütfen [Azure kod analizi geri bildirimi](https://go.microsoft.com/fwlink/?LinkId=403771)'nde fikirlerinizi ve geri bildiriminizi paylaşın.

### <a name="reason"></a>Neden
**OnMessage**çağrılırken, istemci kuyruğu veya aboneliği sürekli yoklayan bir iç ileti göndericisi başlatır. Bu ileti pompası iletileri almak için bir çağrı sorunları sonsuz bir döngü içeriyor. Arama zaman aşımına uğrarsa, yeni bir çağrı verir. Zaman aşımı aralığı, kullanılmakta olan [Messagingfactory](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.messagingfactory.aspx)'Nin [OperationTimeout](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.messagingfactorysettings.operationtimeout.aspx) özelliğinin değerine göre belirlenir.

**OnMessage** 'i **alma** ile karşılaştırıldığında kullanmanın avantajı, kullanıcıların iletileri el ile yoklamasını, özel durumları işlemesini, paralel olarak birden çok iletiyi işlemesini ve iletileri tamamlamasını desteklemez.

**Alma** 'yı varsayılan değerini kullanmadan çağırırsanız, *ServerWaitTime* değerinin bir dakikadan fazla olduğundan emin olun. *ServerWaitTime* 'in birden fazla dakika olarak ayarlanması, iletinin tam olarak alınmadan önce sunucunun zaman aşımına uğramasını önler.

### <a name="solution"></a>Çözüm
Aşağıdaki kod örnekleri önerilen kullanımlar için lütfen bkz. Daha fazla ayrıntı için bkz. [Queueclient. OnMessage yöntemi (Microsoft. ServiceBus. Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.onmessage.aspx)ve [Queueclient. Receive yöntemi (Microsoft. ServiceBus. Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.receive.aspx).

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

## <a name="consider-using-asynchronous-service-bus-methods"></a>Service Bus zaman uyumsuz yöntemler kullanmayı düşünün
### <a name="id"></a>Kimlik
AP2003

### <a name="description"></a>Açıklama
Aracılı Mesajlaşma ile performansı artırmak için Service Bus zaman uyumsuz yöntemleri kullanın.

Lütfen [Azure kod analizi geri bildirimi](https://go.microsoft.com/fwlink/?LinkId=403771)'nde fikirlerinizi ve geri bildiriminizi paylaşın.

### <a name="reason"></a>Neden
Her çağrıyı yürütmeden ana iş parçacığını engellemez çünkü zaman uyumsuz yöntemler kullanarak uygulama programı eşzamanlılık sağlar. Mesajlaşma yöntemleri, bir işlemi gerçekleştirilirken bir Service Bus kullanırken (gönderme, alma, silme, vb.) sürer. Bu süre, istek ve yanıt gecikmeye ek olarak Service Bus hizmeti tarafından işlemi işlenmesini içerir. İşlem Saati başına sayıyı artırmak için işlemler aynı anda yürütmeniz gerekir. Daha fazla bilgi için lütfen [Service Bus Aracılı mesajlaşma kullanarak performans geliştirmeleri Için En Iyi uygulamalara](https://msdn.microsoft.com/library/azure/hh528527.aspx)bakın.

### <a name="solution"></a>Çözüm
Önerilen zaman uyumsuz yöntemi kullanma hakkında bilgi için bkz. [Queueclient sınıfı (Microsoft. ServiceBus. Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.aspx) .

Azure mesajlaşma altyapısının performansını artırmak için bkz. tasarım deseninin [zaman uyumsuz mesajlaşma](https://msdn.microsoft.com/library/dn589781.aspx)bilgileri.

## <a name="consider-partitioning-service-bus-queues-and-topics"></a>Bölümleme Service Bus kuyrukları ve konuları göz önünde bulundurun.
### <a name="id"></a>Kimlik
AP2004

### <a name="description"></a>Açıklama
Partition Service Bus kuyrukları ve konuları Service Bus mesajlaşması ile daha iyi performans için.

Lütfen [Azure kod analizi geri bildirimi](https://go.microsoft.com/fwlink/?LinkId=403771)'nde fikirlerinizi ve geri bildiriminizi paylaşın.

### <a name="reason"></a>Neden
Bölümlenmiş bir kuyruk veya konuda genel verimini artık bir tek ileti aracısı veya ileti deposu performansını sınırlı olduğundan, Service Bus kuyrukları ve konuları bölümleme performans aktarım hızı ve hizmet kullanılabilirliğini artırır. Ayrıca, bir Mesajlaşma deposunun geçici bir kesinti bölümlenmiş bir kuyruk veya konuda kullanılamaz yapmaz. Daha fazla bilgi için bkz. [mesajlaşma varlıklarını bölümlendirme](https://msdn.microsoft.com/library/azure/dn520246.aspx).

### <a name="solution"></a>Çözüm
Aşağıdaki kod parçacığı, Mesajlaşma varlıkları bölümleme işlemi gösterilmektedir.

```csharp
// Create partitioned topic.
NamespaceManager ns = NamespaceManager.CreateFromConnectionString(myConnectionString);
TopicDescription td = new TopicDescription(TopicName);
td.EnablePartitioning = true;
ns.CreateTopic(td);
```

Daha fazla bilgi için bkz. [bölümlenmiş Service Bus kuyruklar ve konular | Blog Microsoft Azure](https://azure.microsoft.com/blog/2013/10/29/partitioned-service-bus-queues-and-topics/) ve [Microsoft Azure Service Bus bölümlenmiş sıra](https://code.msdn.microsoft.com/windowsazure/Service-Bus-Partitioned-7dfd3f1f) örneğine göz atın.

## <a name="do-not-set-sharedaccessstarttime"></a>SharedAccessStartTime ayarlı değil
### <a name="id"></a>Kimlik
AP3001

### <a name="description"></a>Açıklama
Paylaşılan Erişim İlkesi hemen başlatmak için geçerli saate SharedAccessStartTimeset kullanarak kaçınmanız gerekir. Yalnızca paylaşılan erişim ilkesi daha sonraki bir zamanda başlatmak istiyorsanız bu özelliği ayarlayın gerekir.

Lütfen [Azure kod analizi geri bildirimi](https://go.microsoft.com/fwlink/?LinkId=403771)'nde fikirlerinizi ve geri bildiriminizi paylaşın.

### <a name="reason"></a>Neden
Saat eşitlemesi veri merkezleri arasında bir küçük zaman farkı neden olur. Örneğin, DateTime.Now kullanarak bir depolama SAS İlkesi başlangıç saati geçerli saati ayarlama mantıksal olarak düşündüğünüz veya SAS ilke hemen etkili olması benzer bir yöntem neden olur. Ancak, veri merkezi zamanlarda, önceden sahipken başlangıç saatinden biraz daha sonra veri merkezleri arasında hafif saat farklılıklarını bu sorunlara neden olabilir. Sonuç olarak, SAS İlkesi hızla (veya hatta hemen) süresinin dolmasını sağlayabilir ilke yaşam süresi çok kısa olarak ayarlanmışsa.

Azure depolama 'da paylaşılan erişim Imzasını kullanma hakkında daha fazla bilgi için bkz. [tablo SAS (paylaşılan erişim imzası), kuyruk SAS ve BLOB SAS güncelleştirme-Microsoft Azure depolama Team blog-site Home-MSDN blogları](https://blogs.msdn.microsoft.com/windowsazurestorage/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas/).

### <a name="solution"></a>Çözüm
Paylaşılan erişim ilkesinin başlangıç saatini ayarlar deyimi kaldırın. Azure Kod çözümleme aracı, bu sorun için düzeltme sağlar. Güvenlik yönetimi hakkında daha fazla bilgi için lütfen tasarım deseninin [Valet anahtar düzenine](https://msdn.microsoft.com/library/dn568102.aspx)bakın.

Aşağıdaki kod parçacığını bu sorunla ilgili kod düzeltme gösterir.

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

## <a name="shared-access-policy-expiry-time-must-be-more-than-five-minutes"></a>Paylaşılan Erişim İlkesi süre sonu beş dakikadan fazla olmalıdır
### <a name="id"></a>Kimlik
AP3002

### <a name="description"></a>Açıklama
Beş dakikalık fark kadar "saat dengesizliği gösteriyor." bilinen bir koşul nedeniyle, farklı konumlardaki veri merkezleri arasında saatler içinde olabilir SAS önlemek için beş dakikadan fazla olacak şekilde sona erme saati planlanandan daha erken sona erecek gelen ilke belirteci ayarlayın.

Lütfen [Azure kod analizi geri bildirimi](https://go.microsoft.com/fwlink/?LinkId=403771)'nde fikirlerinizi ve geri bildiriminizi paylaşın.

### <a name="reason"></a>Neden
Dünyanın dört bir yanındaki farklı konumlardaki veri merkezlerine saat sinyali ile eşitleyin. Farklı bir konuma seyahat saat sinyali zaman alır çünkü her şeyin beklendiği gibi eşitlenir ancak farklı coğrafi konumlarda veri merkezleri arasında bir saat farkı olabilir. Bu zaman farkı, paylaşılan erişim ilkesi başlangıç saati ve sona erme aralığını etkileyebilir. Bu nedenle, paylaşılan erişim ilkesi hemen etkinlik kazanır emin olmak için başlangıç saati belirtmezsiniz. Ayrıca, erken zaman aşımını önlemek için birden fazla 5 dakika süre olduğundan emin olun.

Azure depolama 'da paylaşılan erişim Imzasını kullanma hakkında daha fazla bilgi için bkz. [tablo SAS (paylaşılan erişim imzası), kuyruk SAS ve BLOB SAS güncelleştirmesi-Microsoft Azure depolama Team blog-site Home-MSDN blogları](https://blogs.msdn.microsoft.com/windowsazurestorage/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas/).

### <a name="solution"></a>Çözüm
Güvenlik yönetimi hakkında daha fazla bilgi için bkz. tasarım deseninin [Valet anahtar stili](https://msdn.microsoft.com/library/dn568102.aspx).

Bir paylaşılan erişim ilkesi başlangıç saati belirtmeden bir örnek verilmiştir.

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

Beş dakikadan uzun bir ilke sona erme süresi ile bir paylaşılan erişim ilkesi başlangıç saati belirten bir örnek verilmiştir.

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

## <a name="use-cloudconfigurationmanager"></a>CloudConfigurationManager kullanın
### <a name="id"></a>Kimlik
AP4000

### <a name="description"></a>Açıklama
Azure Web sitesi ve Azure Mobil Hizmetleri gibi projeler için [ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) sınıfının kullanılması çalışma zamanı sorunları oluşturmayacaktır. Bununla birlikte, en iyi uygulama olarak, tüm Azure bulut uygulamalarına yönelik yapılandırmaların yönetilmesi için birleştirilmiş bir yöntem olarak bulutta[ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) kullanmak iyi bir fikirdir.

Lütfen [Azure kod analizi geri bildirimi](https://go.microsoft.com/fwlink/?LinkId=403771)'nde fikirlerinizi ve geri bildiriminizi paylaşın.

### <a name="reason"></a>Neden
CloudConfigurationManager uygulama ortamınız için uygun yapılandırma dosyasını okur.

[CloudConfigurationManager](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.cloudconfigurationmanager.aspx)

### <a name="solution"></a>Çözüm
[Cloudconfigurationmanager sınıfını](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.cloudconfigurationmanager.aspx)kullanmak için kodunuzu yeniden düzenleyin. Bu sorun için bir kod düzeltme Azure Kod Analizi araç tarafından sağlanır.

Aşağıdaki kod parçacığını bu sorunla ilgili kod düzeltme gösterir. Değiştir

`var settings = ConfigurationManager.AppSettings["mySettings"];`

şununla değiştirin

`var settings = CloudConfigurationManager.GetSetting("mySettings");`

Yapılandırma ayarı bir App.config veya Web.config dosyasında depolamak nasıl bir örnek aşağıda verilmiştir. Ayarları yapılandırma dosyasının appSettings bölümünü ekleyin. Önceki kod örneği için Web.config dosyası verilmiştir.

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
### <a name="id"></a>Kimlik
AP4001

### <a name="description"></a>Açıklama
Sabit kodlanmış bağlantı dizeleri kullanın ve bunları daha sonra güncelleştirmeyi ihtiyacınız varsa, kaynak kodunuzda değişiklikler yapın ve uygulamayı yeniden derlemenize zorunda kalırsınız. Bağlantı dizelerinizi yapılandırma dosyasında depoladığınızda, ancak, bunları daha sonra yapılandırma dosyasını güncelleştirerek değiştirebilirsiniz.

Lütfen [Azure kod analizi geri bildirimi](https://go.microsoft.com/fwlink/?LinkId=403771)'nde fikirlerinizi ve geri bildiriminizi paylaşın.

### <a name="reason"></a>Neden
Sabit kodlama bağlantı dizeleri olduğundan hatalı bir uygulama bağlantı dizeleri hızlı bir şekilde değiştirilmesi gerektiğinde sorunları oluşabilir. Ayrıca, projeyi kaynak denetimine iade edilmesi gerekiyorsa, sabit kodlanmış bağlantı dizeleri güvenlik açıklarını dizeleri kaynak kodunda görüntülenebilir beri tanıtır.

### <a name="solution"></a>Çözüm
Bağlantı dizelerini yapılandırma dosyaları veya Azure ortamlarını Store.

* Tek başına uygulamalar için bağlantı dizesi ayarlarını depolamak için app.config kullanın.
* IIS barındırılan web uygulamaları için web.config bağlantı dizeleri depolamak için kullanın.
* ASP.NET vNext uygulamaları için bağlantı dizeleri depolamak için configuration.json kullanın.

Web. config veya App. config gibi yapılandırma dosyalarını kullanma hakkında daha fazla bilgi için bkz. [ASP.NET Web Configuration yönergeleri](https://msdn.microsoft.com/library/vstudio/ff400235\(v=vs.100\).aspx). Azure ortam değişkenlerinin nasıl çalıştığı hakkında bilgi için bkz. [Azure Web siteleri: uygulama dizeleri ve bağlantı dizeleri nasıl çalışır?](https://azure.microsoft.com/blog/2013/07/17/windows-azure-web-sites-how-application-strings-and-connection-strings-work/). Kaynak denetiminde bağlantı dizesini depolama hakkında bilgi için, bkz. [kaynak kodu deposunda depolanan dosyalardaki bağlantı dizeleri gibi hassas bilgileri yerleştirmekten kaçının](https://docs.microsoft.com/aspnet/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/source-control).

## <a name="use-diagnostics-configuration-file"></a>Tanılama yapılandırma dosyası kullanın
### <a name="id"></a>Kimlik
AP5000

### <a name="description"></a>Açıklama
Tanılama ayarları gibi kodunuzda API'si ile programlama Microsoft.WindowsAzure.Diagnostics kullanarak yapılandırmak yerine diagnostics.wadcfg dosyasında tanılama ayarları yapılandırmanız gerekir. (Ya da Azure SDK 2.5 kullanırsanız diagnostics.wadcfgx). Bunu yaparak, kodunuzu yeniden derlemenize gerek kalmadan tanılama ayarlarını değiştirebilirsiniz.

Lütfen [Azure kod analizi geri bildirimi](https://go.microsoft.com/fwlink/?LinkId=403771)'nde fikirlerinizi ve geri bildiriminizi paylaşın.

### <a name="reason"></a>Neden
Azure SDK 2.5 (Bu, Azure tanılama 1.3 kullanır), Azure tanılama (WAD) birkaç farklı yöntem kullanarak yapılandırılabilir önce: Bu yapılandırma blob depolama, kesinlik temelli Kodun, bildirim temelli yapılandırması ya da varsayılan kullanarak ekleme yapılandırma. Ancak, tanılamayı yapılandırmak için tercih edilen yöntem, uygulama projesindeki bir XML yapılandırma dosyası (SDK 2,5 ve üzeri için tanılama. wadcfgx) kullanmaktır. Bu yaklaşımda, diagnostics.wadcfg dosya tamamen yapılandırmasını tanımlar ve güncelleştirilebilir ve dilediğiniz zaman yeniden dağıtıldı. Tanılama. wadcfg yapılandırma dosyasının kullanımını [Diagnosticmonitor](https://msdn.microsoft.com/library/microsoft.windowsazure.diagnostics.diagnosticmonitor.aspx)veya [Roleınstancediagnosticmanager](https://msdn.microsoft.com/library/microsoft.windowsazure.diagnostics.management.roleinstancediagnosticmanager.aspx) sınıflarını kullanarak yapılandırma ayarlarının programlı yöntemleriyle karıştırma, karışıklıklara yol açabilir. Daha fazla bilgi için bkz. [Azure tanılama yapılandırmayı başlatma veya değiştirme](https://msdn.microsoft.com/library/azure/hh411537.aspx) .

WAD 1.3 (Azure SDK 2.5 ile dahil) itibaren artık kod tanılamayı yapılandırmak için kullanmak mümkündür. Sonuç olarak, yalnızca uygulama ya da tanılama uzantısını güncelleştirilirken yapılandırması sağlayabilir.

### <a name="solution"></a>Çözüm
Tanılama ayarlarını tanılama yapılandırma dosyasına (SDK 2,5 ve üzeri için tanılama. wadcfg veya Diagnostics. wadcfgx) taşımak için tanılama yapılandırma tasarımcısını kullanın. Ayrıca, [Azure SDK 2,5](https://go.microsoft.com/fwlink/?LinkId=513188) ' i yükleyip en son Tanılama özelliğini kullanmanız önerilir.

1. Yapılandırmak istediğiniz rol kısayol menüsünde Özellikler'i seçin ve ardından yapılandırma sekmesini seçin.
2. **Tanılama** bölümünde, **tanılamayı etkinleştir** onay kutusunun seçili olduğundan emin olun.
3. **Yapılandır** düğmesini seçin.

   ![Tanılamayı Etkinleştir seçeneğine erişme](./media/vs-azure-tools-optimizing-azure-code-in-visual-studio/IC796660.png)

   Daha fazla bilgi için bkz. [Azure Cloud Services Için tanılamayı yapılandırma ve sanal makineler](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md) .

## <a name="avoid-declaring-dbcontext-objects-as-static"></a>Statik olarak DbContext nesneleri bildirme kaçının
### <a name="id"></a>Kimlik
AP6000

### <a name="description"></a>Açıklama
Bellek kaydetmek için statik olarak DBContext nesneleri bildirme kaçının.

Lütfen [Azure kod analizi geri bildirimi](https://go.microsoft.com/fwlink/?LinkId=403771)'nde fikirlerinizi ve geri bildiriminizi paylaşın.

### <a name="reason"></a>Neden
Sorgu sonuçları her çağrıdan DBContext nesneleri barındırır. Uygulama etki alanı bellekten kaldırılana kadar statik DBContext nesneler atıldı değil. Bu nedenle, statik bir DBContext nesnesini büyük miktarlarda bellek tüketebilir.

### <a name="solution"></a>Çözüm
DBContext bir yerel değişken veya statik olmayan örnek alanı olarak bildirmek, bir görev için kullanacağınız ve bunu kullandıktan sonra değerini sağlar.

Aşağıdaki örnek MVC denetleyici sınıfı DBContext nesnesinin nasıl kullanılacağını gösterir.

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
