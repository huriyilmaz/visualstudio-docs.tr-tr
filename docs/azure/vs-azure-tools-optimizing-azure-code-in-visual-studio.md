---
title: Azure kodunuzu en iyi duruma alma
description: Visual Studio'daki Azure kod optimizasyonu araçlarının kodunuzu daha sağlam ve daha iyi performans lı hale getirmeye nasıl yardımcı olduğu hakkında bilgi edinin.
author: ghogen
manager: jillfra
ms.assetid: ed48ee06-e2d2-4322-af22-07200fb16987
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: e42a746761b09e99e158ecef8e9054bc0049c03d
ms.sourcegitcommit: 59a8732dc563242590f7c6ccf4ced6c6d195533c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81489642"
---
# <a name="optimizing-your-azure-code"></a>Azure Kodunuzu İyileştirme
Microsoft Azure kullanan uygulamaları programlarken, bulut ortamında uygulama ölçeklenebilirliği, davranışı ve performansıyla ilgili sorunları önlemeye yardımcı olmak için izlemeniz gereken bazı kodlama uygulamaları vardır. Microsoft, sık karşılaşılan bu sorunlardan birkaçını tanıyan ve tanımlayan ve bunları çözmenize yardımcı olan bir Azure Kod Çözümleme aracı sağlar. Aracı NuGet üzerinden Visual Studio'dan indirebilirsiniz.

## <a name="azure-code-analysis-rules"></a>Azure Kod Analizi kuralları
Azure Kod Analizi aracı, performans etkileyen bilinen sorunları bulduğunda Azure kodunuzu otomatik olarak işaretlemek için aşağıdaki kuralları kullanır. Algılanan sorunlar bir uyarı veya derleyici hataları olarak görünür. Uyarı veya hatayı gidermek için kod düzeltmeleri veya öneriler genellikle bir ampul simgesi aracılığıyla sağlanır.

## <a name="avoid-using-default-in-process-session-state-mode"></a>Varsayılan (işlem) oturum durumu modunu kullanmaktan kaçının
### <a name="id"></a>Kimlik
AP0000

### <a name="description"></a>Açıklama
Bulut uygulamaları için varsayılan (işlem içi) oturum durum modunu kullanırsanız, oturum durumunu kaybedebilirsiniz.

Lütfen fikirlerinizi ve geri bildirimlerinizi [Azure Kod Analizi geri bildiriminde](https://social.msdn.microsoft.com/Forums/en-US/home)paylaşın.

### <a name="reason"></a>Neden
Varsayılan olarak, web.config dosyasında belirtilen oturum durumu modu işlem aşamasındadır. Ayrıca, yapılandırma dosyasında giriş belirtilmemişse, Oturum Durumu modu varsayılan olarak işlem içi moduna geçer. İşlem içi modu, oturum durumunu web sunucusundaki bellekte depolar. Bir örnek yeniden başlatıldığında veya yük dengeleme veya başarısız destek için yeni bir örnek kullanıldığında, web sunucusunda bellekte depolanan oturum durumu kaydedilmez. Bu durum, uygulamanın bulutta ölçeklenebilir olmasını önler.

ASP.NET oturum durumu, oturum durumu verileri için birkaç farklı depolama seçeneğini destekler: InProc, StateServer, SQLServer, Custom ve Off. [Redis için Azure Oturum Durumu sağlayıcısı](https://devblogs.microsoft.com/aspnet/announcing-asp-net-session-state-provider-for-redis-preview-release/)gibi harici bir Oturum Durumu deposunda veri barındırmak için Özel mod kullanmanız önerilir.

### <a name="solution"></a>Çözüm
Önerilen çözümlerden biri, oturum durumunu yönetilen bir önbellek hizmetinde depolamaktır. Oturum durumunuzu depolamak [için Redis için Azure Oturum Durumu sağlayıcısını](https://devblogs.microsoft.com/aspnet/announcing-asp-net-session-state-provider-for-redis-preview-release/) nasıl kullanacağınızı öğrenin. Uygulamanızın bulutta ölçeklenebilir olduğundan emin olmak için oturum durumunu başka yerlerde de depolayabilirsiniz. Alternatif çözümler hakkında daha fazla bilgi edinmek için lütfen [Oturum Durum Modları'nı](https://msdn.microsoft.com/library/ms178586)okuyun.

## <a name="run-method-should-not-be-async"></a>Çalıştırma yöntemi async olmamalıdır
### <a name="id"></a>Kimlik
AP1000

### <a name="description"></a>Açıklama
[Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) yönteminin dışında eşzamanlı yöntemler [(bekleme](https://msdn.microsoft.com/library/hh156528.aspx)gibi) oluşturun ve ardından [Run()'den](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)async yöntemlerini arayın. [[Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) yöntemini eşit olarak bildirmek, alt rolün yeniden başlatma döngüsüne girmesine neden olur.

Lütfen fikirlerinizi ve geri bildirimlerinizi [Azure Kod Analizi geri bildiriminde](https://social.msdn.microsoft.com/Forums/en-US/home)paylaşın.

### <a name="reason"></a>Neden
[Çalıştır()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) yöntemi içinde async yöntemlerini çağırmak, bulut hizmeti çalışma zamanının çalışan rolü geri dönüştürmesine neden olur. Bir alt rol başladığında, tüm program yürütme [Çalıştır()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) yöntemi içinde gerçekleşir. [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) yönteminden çıkmak, alt rolün yeniden başlatılmasına neden olur. Alt rol çalışma süresi async yöntemine ulaştığında, async yönteminden sonra tüm işlemleri gönderir ve sonra döndürür. Bu, alt rolün [[[[Çalıştır()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) yönteminden çıkmasına ve yeniden başlatılmasına neden olur. Yürütmenin bir sonraki yinelemesinde, alt rol async yöntemine tekrar vurur ve yeniden başlatılır ve bu da alt rolün yeniden dönüştürülmesine neden olur.

### <a name="solution"></a>Çözüm
Tüm async işlemlerini [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) yönteminin dışına yerleştirin. Ardından, Run() yönteminin içinden [[run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) yöntemini ()bekleme gibi yeniden etkenleştirilmiş async yöntemini arayın. Azure Kod Çözümlemesi aracı bu sorunu gidermenize yardımcı olabilir.

Aşağıdaki kod snippet bu sorun için kod düzeltmesi gösterir:

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

## <a name="use-service-bus-shared-access-signature-authentication"></a>Hizmet Veri Servisi PaylaşPaylaşılan Erişim İmza kimlik doğrulaması kullanın
### <a name="id"></a>Kimlik
AP2000

### <a name="description"></a>Açıklama
Kimlik doğrulaması için Paylaşılan Erişim İmzası'nı (SAS) kullanın. Erişim Kontrol Hizmeti (ACS), servis veri aracı kimlik doğrulaması için küçümsüyor.

Lütfen fikirlerinizi ve geri bildirimlerinizi [Azure Kod Analizi geri bildiriminde](https://social.msdn.microsoft.com/Forums/en-US/home)paylaşın.

### <a name="reason"></a>Neden
Azure Active Directory, gelişmiş güvenlik için ACS kimlik doğrulamasını SAS kimlik doğrulamasıyla değiştirir. Bkz. Azure Etkin Dizini, geçiş planı hakkında bilgi için [ACS'nin geleceğidir.](https://cloudblogs.microsoft.com/enterprisemobility/2013/06/22/azure-active-directory-is-the-future-of-acs/)

### <a name="solution"></a>Çözüm
Uygulamalarınızda SAS kimlik doğrulamasını kullanın. Aşağıdaki örnek, bir hizmet veri aracı ad alanına veya varlığa erişmek için varolan bir SAS belirtecinin nasıl kullanılacağını gösterir.

```csharp
MessagingFactory listenMF = MessagingFactory.Create(endpoints, new StaticSASTokenProvider(subscriptionToken));
SubscriptionClient sc = listenMF.CreateSubscriptionClient(topicPath, subscriptionName);
BrokeredMessage receivedMessage = sc.Receive();
```

Daha fazla bilgi için aşağıdaki konulara bakın.

* Genel bakış için, [Hizmet Veri Servisi ile Paylaşılan Erişim İmza Kimlik Doğrulaması'na](https://msdn.microsoft.com/library/dn170477.aspx) bakın
* [Hizmet Veri Yol laması ile Paylaşılan Erişim İmza Kimlik Doğrulaması nasıl kullanılır?](https://msdn.microsoft.com/library/dn205161.aspx)
* Örnek bir proje için, [Hizmet Veri Aracı Abonelikleri ile Paylaşılan Erişim İmzası (SAS) kimlik doğrulamasını kullanma](https://code.msdn.microsoft.com/windowsapps/Shared-Access-Signature-0a88adf8)

## <a name="consider-using-onmessage-method-to-avoid-receive-loop"></a>"Alma döngüsü"nden kaçınmak için OnMessage yöntemini kullanmayı düşünün
### <a name="id"></a>Kimlik
AP2002

### <a name="description"></a>Açıklama
"Alma döngüsüne" girmemek **için, OnMessage** yöntemini çağırmak, ileti almak için **Alma** yöntemini aramaktan daha iyi bir çözümdür. Ancak, **Alma** yöntemini kullanmanız gerekiyorsa ve varsayılan olmayan bir sunucu bekleme süresi belirtirseniz, sunucu bekleme süresinin bir dakikadan fazla olduğundan emin olun.

Lütfen fikirlerinizi ve geri bildirimlerinizi [Azure Kod Analizi geri bildiriminde](https://social.msdn.microsoft.com/Forums/en-US/home)paylaşın.

### <a name="reason"></a>Neden
**OnMessage'ı**ararken istemci, sırayı veya aboneliği sürekli olarak yoklayan bir dahili ileti pompası başlatır. Bu ileti pompası, ileti almak için bir çağrı sorunları sonsuz bir döngü içerir. Arama zaman ları dolursa, yeni bir arama yayınlar. Zaman aralığı, kullanılan [MessagingFactory'nin](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.messagingfactory.aspx) [OperationTimeout](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.messagingfactorysettings.operationtimeout.aspx) özelliğinin değerine göre belirlenir.

**OnMessage'ı** **Receive** ile karşılaştırıldığında kullanmanın avantajı, kullanıcıların iletiler için el ile yoklama yapmak, özel durumları işlemek, birden çok iletiyi paralel olarak işlemek ve iletileri tamamlamak zorunda kalmamasıdır.

Varsayılan değerini kullanmadan **Al'ı** ararsanız, *ServerWaitTime* değerinin bir dakikadan fazla olduğundan emin olun. *ServerWaitTime'ı* bir dakikadan fazlasına ayarlamak, ileti tam olarak alınmadan önce sunucunun zamanlamasını engeller.

### <a name="solution"></a>Çözüm
Lütfen önerilen kullanımlar için aşağıdaki kod örneklerine bakın. Daha fazla bilgi için [QueueClient.OnMessage Yöntemi (Microsoft.ServiceBus.Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.onmessage.aspx) ve [QueueClient.Receive Metodu (Microsoft.ServiceBus.Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.receive.aspx)'ye bakın.

Azure ileti altyapısının performansını artırmak için [Asynchronous Messaging Primer](https://msdn.microsoft.com/library/dn589781.aspx)tasarım desenine bakın.

Aşağıda, ileti almak için **OnMessage'ı** kullanmanın bir örneği verilmiştir.

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

Aşağıda, varsayılan sunucu bekleme süresiyle **Receive'ı** kullanmanın bir örneği verilmiştir.

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

Aşağıda, varsayılan olmayan bir sunucu bekleme süresiyle **Receive'ı** kullanma nın bir örneği verilmiştir.

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

## <a name="consider-using-asynchronous-service-bus-methods"></a>Eşzamanlı Servis Veri Servisi yöntemlerini kullanmayı düşünün
### <a name="id"></a>Kimlik
AP2003

### <a name="description"></a>Açıklama
Aracılı iletilerle performansı artırmak için eşzamanlı Servis Veri Servisi yöntemlerini kullanın.

Lütfen fikirlerinizi ve geri bildirimlerinizi [Azure Kod Analizi geri bildiriminde](https://social.msdn.microsoft.com/Forums/en-US/home)paylaşın.

### <a name="reason"></a>Neden
Eşsenkronize yöntemlerin kullanılması, her çağrının yürütülmesi ana iş parçacığı engellemez, çünkü uygulama programı eşzamanlılık sağlar. Servis Veri Servisi mesajlaşma yöntemlerini kullanırken, bir işlemi gerçekleştirmek (gönderme, alma, silme, vb.) zaman alır. Bu süre, isteğin gecikmesine ve yanıtına ek olarak Servis Veri Servisi tarafından işlemin işlenmesini içerir. Zaman başına işlem sayısını artırmak için, işlemlerin aynı anda yürütülmesi gerekir. Daha fazla bilgi için lütfen [Servis Veri Aracılı Mesajlaşma kullanarak Performans Geliştirmeleri için En İyi Uygulamalar](https://msdn.microsoft.com/library/azure/hh528527.aspx)bakın.

### <a name="solution"></a>Çözüm
Önerilen eşzamanlı yöntemin nasıl kullanılacağı hakkında bilgi için [QueueClient Class (Microsoft.ServiceBus.Messaging) (Microsoft.ServiceBus.Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.aspx) bakın.

Azure ileti altyapısının performansını artırmak için [Asynchronous Messaging Primer](https://msdn.microsoft.com/library/dn589781.aspx)tasarım desenine bakın.

## <a name="consider-partitioning-service-bus-queues-and-topics"></a>Servis Veri Günü kuyruklarını ve konularını bölümleme yi göz önünde bulundurun
### <a name="id"></a>Kimlik
AP2004

### <a name="description"></a>Açıklama
Servis Otobüsü iletisi ile daha iyi performans için Bölüm Hizmeti Veri Günü kuyrukları ve konuları.

Lütfen fikirlerinizi ve geri bildirimlerinizi [Azure Kod Analizi geri bildiriminde](https://social.msdn.microsoft.com/Forums/en-US/home)paylaşın.

### <a name="reason"></a>Neden
Bölümlenmiş bir sıranın veya konunun genel iş ortası artık tek bir ileti aracıcısının veya ileti deposunun performansıyla sınırlı olmadığından, Hizmet Veri Hizmetleri kuyruklarını ve konularını bölümleme performans verime ve hizmet kullanılabilirliğini artırır. Ayrıca, bir ileti deposunun geçici kesintisi, bölümlenmiş bir sırayı veya konuyu kullanılamaz hale getirmez. Daha fazla bilgi için [bkz.](https://msdn.microsoft.com/library/azure/dn520246.aspx)

### <a name="solution"></a>Çözüm
Aşağıdaki kod snippet nasıl bölüm ileti varlıkları gösterir.

```csharp
// Create partitioned topic.
NamespaceManager ns = NamespaceManager.CreateFromConnectionString(myConnectionString);
TopicDescription td = new TopicDescription(TopicName);
td.EnablePartitioning = true;
ns.CreateTopic(td);
```

Daha fazla bilgi için bkz: [Bölümlenmiş Servis Veri Günü Kuyrukları ve Konuları | Microsoft Azure Blog'u](https://azure.microsoft.com/blog/2013/10/29/partitioned-service-bus-queues-and-topics/) ve [Microsoft Azure Hizmet Veri Gönderi Bölümlenmiş Sıra](https://code.msdn.microsoft.com/windowsazure/Service-Bus-Partitioned-7dfd3f1f) örneğine göz atın.

## <a name="do-not-set-sharedaccessstarttime"></a>SharedAccessStartTime'ı ayarlama
### <a name="id"></a>Kimlik
AP3001

### <a name="description"></a>Açıklama
Paylaşılan Erişim ilkesini hemen başlatmak için Geçerli saate kadar SharedAccessStartTimeset kullanmaktan kaçınmalısınız. Paylaşılan Erişim ilkesini daha sonra başlatmak istiyorsanız bu özelliği ayarlamanız gerekir.

Lütfen fikirlerinizi ve geri bildirimlerinizi [Azure Kod Analizi geri bildiriminde](https://social.msdn.microsoft.com/Forums/en-US/home)paylaşın.

### <a name="reason"></a>Neden
Saat eşitlemesi veri merkezleri arasında hafif bir zaman farkı neden olur. Örneğin, DateTime.Now veya benzer bir yöntemi kullanarak bir depolama SAS ilkesinin başlangıç saatini geçerli saat olarak ayarlamanın SAS ilkesinin hemen etkili olmasını sağlayacağını düşünebilirsiniz. Ancak, veri merkezleri arasındaki küçük zaman farkları, bazı veri merkezi süreleri başlangıç saatinden biraz daha geç, diğerleri ise öncesinde olabileceğinden, bu nda sorunlara neden olabilir. Sonuç olarak, ilke ömrü çok kısa ayarlanırsa, SAS ilkesinin süresi hızla (hatta hemen) dolabilir.

Azure depolama alanında Paylaşılan Erişim İmzasını kullanma hakkında daha fazla bilgi için bkz: [Tablo SAS (Paylaşılan Erişim İmzası), Sıra SAS ve Blob SAS ' a güncelleme - Microsoft Azure Depolama Ekibi Blogu - Site Evi - MSDN Bloglar.](https://blogs.msdn.microsoft.com/windowsazurestorage/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas/)

### <a name="solution"></a>Çözüm
Paylaşılan erişim ilkesinin başlangıç saatini ayarlayan deyimi kaldırın. Azure Kod Çözümlemesi aracı bu sorun için bir düzeltme sağlar. Güvenlik yönetimi hakkında daha fazla bilgi için lütfen tasarım deseni [Vale Key Pattern'e](https://msdn.microsoft.com/library/dn568102.aspx)bakın.

Aşağıdaki kod snippet bu sorun için kod düzeltmesi gösterir.

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

## <a name="shared-access-policy-expiry-time-must-be-more-than-five-minutes"></a>Paylaşılan Erişim İlkesi son kullanma süresi beş dakikadan fazla olmalıdır
### <a name="id"></a>Kimlik
AP3002

### <a name="description"></a>Açıklama
"Saat eğriltme" olarak bilinen bir durum nedeniyle farklı konumlardaki veri merkezleri arasında beş dakikalık bir fark olabilir. SAS ilke belirtecinin planlanandan daha erken sona ermesini önlemek için, son kullanma süresini beş dakikadan fazla olarak ayarlayın.

Lütfen fikirlerinizi ve geri bildirimlerinizi [Azure Kod Analizi geri bildiriminde](https://social.msdn.microsoft.com/Forums/en-US/home)paylaşın.

### <a name="reason"></a>Neden
Dünyanın farklı yerlarındaki veri merkezleri saat sinyali yle senkronize olur. Saat sinyalinin farklı konumlara seyahat etmesi zaman aldığından, her şey sözde senkronize olmasına rağmen farklı coğrafi konumlardaki veri merkezleri arasında bir zaman farkı olabilir. Bu zaman farkı Paylaşılan Erişim ilkesinin başlangıç saatini ve sona erme aralığını etkileyebilir. Bu nedenle, Paylaşılan Erişim ilkesinin hemen etkin olmasını sağlamak için başlangıç saatini belirtmeyin. Buna ek olarak, erken zaman aşımını önlemek için son kullanma süresinin 5 dakikadan fazla olduğundan emin olun.

Azure depolama alanında Paylaşılan Erişim İmzasını kullanma hakkında daha fazla bilgi için [Bkz. Tablo SAS (Paylaşılan Erişim İmzası), Sıra SAS ve Blob SAS ' a güncelleme - Microsoft Azure Depolama Ekibi Blogu - Site Evi - MSDN Blogları](https://blogs.msdn.microsoft.com/windowsazurestorage/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas/).

### <a name="solution"></a>Çözüm
Güvenlik yönetimi hakkında daha fazla bilgi için, tasarım deseni [Vale Key Pattern](https://msdn.microsoft.com/library/dn568102.aspx)bakın.

Aşağıda Paylaşılan Erişim ilkesi başlangıç saatini belirtmemeye bir örnek verilmiştir.

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

Aşağıda, beş dakikadan uzun bir ilke sona erme süresiyle Paylaşılan Erişim ilkesi nin başlangıç saatini belirtmenin bir örneği verilmiştir.

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

Daha fazla bilgi için [bkz.](https://msdn.microsoft.com/library/azure/jj721951.aspx)

## <a name="use-cloudconfigurationmanager"></a>CloudConfigurationManager'ı kullanma
### <a name="id"></a>Kimlik
AP4000

### <a name="description"></a>Açıklama
Azure Web Sitesi ve Azure mobil hizmetleri gibi projeler için [ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) sınıfını kullanmak çalışma zamanı sorunlarına yol açmaz. Ancak en iyi uygulama olarak, Cloud[ConfigurationManager'ı](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) tüm Azure Bulut uygulamaları için yapılandırmaları birleşik bir şekilde yönetmek için kullanmak iyi bir fikirdir.

Lütfen fikirlerinizi ve geri bildirimlerinizi [Azure Kod Analizi geri bildiriminde](https://social.msdn.microsoft.com/Forums/en-US/home)paylaşın.

### <a name="reason"></a>Neden
CloudConfigurationManager, uygulama ortamına uygun yapılandırma dosyasını okur.

[CloudConfigurationManager](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.cloudconfigurationmanager.aspx)

### <a name="solution"></a>Çözüm
[CloudConfigurationManager Sınıfını](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.cloudconfigurationmanager.aspx)kullanmak için kodunuzu yeniden düzenleme. Bu sorun için bir kod düzeltmesi Azure Kod Çözümlemesi aracı tarafından sağlanır.

Aşağıdaki kod snippet bu sorun için kod düzeltmesi gösterir. Değiştir

`var settings = ConfigurationManager.AppSettings["mySettings"];`

örneklerini şununla değiştirin:

`var settings = CloudConfigurationManager.GetSetting("mySettings");`

Yapılandırma ayarını App.config veya Web.config dosyasında nasıl depolayabildiğini anlatan bir örnek aşağıda verilmiştir. Ayarları yapılandırma dosyasının uygulama Ayarları bölümüne ekleyin. Aşağıda önceki kod örneği için Web.config dosyası verilmiştir.

```xml
<appSettings>
    <add key="webpages:Version" value="3.0.0.0" />
    <add key="webpages:Enabled" value="false" />
    <add key="ClientValidationEnabled" value="true" />
    <add key="UnobtrusiveJavaScriptEnabled" value="true" />
    <add key="mySettings" value="[put_your_setting_here]"/>
  </appSettings>
```

## <a name="avoid-using-hard-coded-connection-strings"></a>Sabit kodlu bağlantı dizeleri kullanmaktan kaçının
### <a name="id"></a>Kimlik
AP4001

### <a name="description"></a>Açıklama
Sabit kodlu bağlantı dizeleri kullanıyorsanız ve bunları daha sonra güncelleştirmeniz gerekiyorsa, kaynak kodunuzda değişiklik yapmanız ve uygulamayı yeniden derlemeniz gerekir. Ancak, bağlantı dizelerinizi bir yapılandırma dosyasında depolarsanız, yapılandırma dosyasını yalnızca güncelleştirerek bunları daha sonra değiştirebilirsiniz.

Lütfen fikirlerinizi ve geri bildirimlerinizi [Azure Kod Analizi geri bildiriminde](https://social.msdn.microsoft.com/Forums/en-US/home)paylaşın.

### <a name="reason"></a>Neden
Bağlantı dizeleri hızlı bir şekilde değiştirilmesi gerektiğinde sorunları ortaya çıkarmak, çünkü sabit kodlama bağlantı dizeleri kötü bir uygulamadır. Ayrıca, projenin kaynak denetimi için iade edilmesi gerekiyorsa, dizeleri kaynak kodunda görüntülenebildiği için sabit kodlu bağlantı dizeleri güvenlik açıklarına neden olur.

### <a name="solution"></a>Çözüm
Bağlantı dizelerini yapılandırma dosyalarında veya Azure ortamlarında depolayın.

* Bağımsız uygulamalar için bağlantı dize ayarlarını depolamak için app.config'i kullanın.
* IIS tarafından barındırılan web uygulamaları için bağlantı dizelerini depolamak için web.config'i kullanın.
* ASP.NET vNext uygulamaları için bağlantı dizelerini depolamak için configuration.json'ı kullanın.

web.config veya app.config gibi yapılandırmaları kullanma hakkında daha fazla bilgi için [Web Yapılandırma YönergeleriASP.NET](/aspnet/web-forms/overview/deployment/visual-studio-web-deployment/web-config-transformations)bakın. Azure ortam değişkenlerinin nasıl çalıştığı hakkında bilgi için [bkz: Azure Web Siteleri: Uygulama Dizeleri ve Bağlantı Dizeleri nasıl çalışır.](https://azure.microsoft.com/blog/2013/07/17/windows-azure-web-sites-how-application-strings-and-connection-strings-work/) Kaynak denetiminde bağlantı dizesini depolama hakkında bilgi için [bkz.](/aspnet/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/source-control)

## <a name="use-diagnostics-configuration-file"></a>Tanılama yapılandırma dosyalarını kullanma
### <a name="id"></a>Kimlik
AP5000

### <a name="description"></a>Açıklama
Microsoft.WindowsAzure.Diagnostics programlama API'sini kullanarak kodunuzda tanılama ayarlarını yapılandırmak yerine, diagnostics.wadcfg dosyasında tanılama ayarlarını yapılandırmanız gerekir. (Veya Azure SDK 2.5 kullanıyorsanız diagnostics.wadcfgx). Bunu yaparak, kodunuzu yeniden derlemek zorunda kalmadan tanılama ayarlarını değiştirebilirsiniz.

Lütfen fikirlerinizi ve geri bildirimlerinizi [Azure Kod Analizi geri bildiriminde](https://social.msdn.microsoft.com/Forums/en-US/home)paylaşın.

### <a name="reason"></a>Neden
Azure SDK 2.5'ten önce (Azure tanılama 1.3'ü kullanır), Azure Tanılama (WAD) birkaç farklı yöntem kullanılarak yapılandırılabilir: depolamadaki yapılandırma blob'una ekleyerek, zorunlu kod, bildirimsel yapılandırma veya varsayılan yapılandırma kullanılarak. Ancak, tanılama yapılandırmak için tercih edilen yolu uygulama projesinde bir XML yapılandırma dosyası (diagnostics.wadcfg veya diagnostics.wadcfg s sd2.5 ve sonrası için wadcfgx) kullanmaktır. Bu yaklaşımda, diagnostics.wadcfg dosyası yapılandırmayı tamamen tanımlar ve kendi iradesiyle güncellenebilir ve yeniden dağıtılabilir. Diagnostics.wadcfg yapılandırma dosyasının kullanılmasını [DiagnosticMonitor](https://msdn.microsoft.com/library/microsoft.windowsazure.diagnostics.diagnosticmonitor.aspx)veya [RoleInstanceDiagnosticManager](https://msdn.microsoft.com/library/microsoft.windowsazure.diagnostics.management.roleinstancediagnosticmanager.aspx)sınıflarını kullanarak yapılandırmaları ayarlamanın programlı yöntemleriyle karıştırmak karışıklığa yol açabilir. Daha fazla bilgi için [Azure TanıLama Yapılandırması'nı Başlatma veya Değiştir'e](https://msdn.microsoft.com/library/azure/hh411537.aspx) bakın.

WAD 1.3 ile başlayarak (Azure SDK 2.5 ile birlikte), tanılamayı yapılandırmak için kodu kullanmak artık mümkün değildir. Sonuç olarak, yapılandırmayı yalnızca tanılama uzantısını uygularken veya güncellerken sağlayabilirsiniz.

### <a name="solution"></a>Çözüm
Tanılama yapılandırma dosyasına (sdk 2.5 ve sonrası için diagnostics.wadcfg veya diagnostics.wadcfgx) taşımak için tanılama yapılandırma tasarımcısını kullanın. [Ayrıca Azure SDK 2.5'i](https://social.msdn.microsoft.com/Forums/en-US/home) yüklemeniz ve en son tanılama özelliğini kullanmanız önerilir.

1. Yapılandırmak istediğiniz rol için kısayol menüsünde Özellikler'i seçin ve ardından Yapılandırma sekmesini seçin.
2. **Tanılama** bölümünde, **Tanılamayı Etkinleştir** onay kutusunun seçildiğinden emin olun.
3. **Yapılık** düğmesini seçin.

   ![Tanılamayı Etkinleştir seçeneğine erişim](./media/vs-azure-tools-optimizing-azure-code-in-visual-studio/IC796660.png)

   Daha fazla bilgi [için Azure Bulut Hizmetleri ve Sanal Makineler için Tanılama](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md) Yapılandırma'ya bakın.

## <a name="avoid-declaring-dbcontext-objects-as-static"></a>DbContext nesnelerini statik olarak bildirmekten kaçının
### <a name="id"></a>Kimlik
AP6000

### <a name="description"></a>Açıklama
Bellek kaydetmek için, DBContext nesnelerini statik olarak bildirmekten kaçının.

Lütfen fikirlerinizi ve geri bildirimlerinizi [Azure Kod Analizi geri bildiriminde](https://social.msdn.microsoft.com/Forums/en-US/home)paylaşın.

### <a name="reason"></a>Neden
DBContext nesneleri her aramadan gelen sorgu sonuçlarını tutar. Statik DBContext nesneleri, uygulama etki alanı kaldırılına kadar atılmaz. Bu nedenle, statik bir DBContext nesnesi büyük miktarda bellek tüketebilir.

### <a name="solution"></a>Çözüm
DBContext'ı yerel değişken veya statik olmayan örnek alanı olarak bildirin, bir görev için kullanın ve kullanımdan sonra imha edilmesine izin verin.

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
Azure uygulamalarını en iyi duruma getirmek ve sorun giderme hakkında daha fazla bilgi edinmek için [Visual Studio'yu kullanarak Azure Uygulama Hizmeti'ndeki bir web uygulamasını sorun giderme](/azure/app-service/web-sites-dotnet-troubleshoot-visual-studio)'ye bakın.
