---
title: İş Akışı Tasarımcısı-etkinlik tasarımcısını gönder
description: Gönderme etkinliği ve gönderme etkinliği oluşturmak ve yapılandırmak için gönderme etkinliği tasarımcısını nasıl kullanabileceğiniz hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Send.UI
ms.assetid: b514f2e4-767c-4b94-ac61-dd3a54d4b96d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b18323f42b67ebb3fb1162432a8b2fd296f2908e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876361"
---
# <a name="send-activity-designer"></a>Send Etkinlik Tasarımcısı

**Gönderme** etkinliği Tasarımcısı, etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.ServiceModel.Activities.Send> .

## <a name="the-send-activity"></a>Gönder etkinliği

 Bir <xref:System.ServiceModel.Activities.Send> etkinlik bir hizmete ileti göndermek için kullanılır. Bir <xref:System.ServiceModel.Activities.ReceiveReply> etkinlik <xref:System.ServiceModel.Activities.Send> , istemcideki istek/yanıt iletisi değişim deseninin bir parçası olarak ileti alan bir etkinliğe bağlanabilir.

### <a name="using-the-send-activity-designer"></a>Gönderme etkinliği tasarımcısını kullanma

**Araç kutusunun** **mesajlaşma** kategorisindeki etkinlik **Gönder** tasarımcısına erişin. **Gönderme** etkinliği Tasarımcısı **araç kutusundan** sürüklenip, etkinliklerin genellikle yerleştirildiği her yerde iş akışı Tasarımcısı yüzeyine bırakılabilir. Bu <xref:System.ServiceModel.Activities.Send> , varsayılan Send olan bir etkinlik oluşturur <xref:System.Activities.Activity.DisplayName%2A> . , <xref:System.Activities.Activity.DisplayName%2A> **Gönder** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

Bir etkinlik oluşturup <xref:System.ServiceModel.Activities.ReceiveReply> Seçili etkinliğe bağlamak için <xref:System.ServiceModel.Activities.Send> , **Gönder** etkinlik tasarımcısına sağ tıklayın, bağlam menüsünde **ReceiveReply öğesi oluştur** öğesini tıklatın ve **ReceiveReplyForSend** Tasarımcısı **gönderme** tasarımcısının altında görüntülenir. <xref:System.ServiceModel.Activities.ReceiveReply>Etkinlik, istemcideki istek/yanıt iletisi değişim deseninin bir parçası olarak bir ileti alan bir etkinliktir. **ReceiveReplyForSend** Tasarımcısı ile yapılandırılabilir.

Alternatif olarak, **araç kutusunun** **mesajlaşma** kategorisindeki **SendAndReceiveReply** şablon Tasarımcısı, önceden yapılandırılmış ve etkinlik çifti oluşturmak için kullanılabilir <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> . **SendAndReceiveReply** ve **ReceiveReplyForSend** şablonlarının kullanımı hakkında daha fazla bilgi Için bkz. [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) konusu.

### <a name="the-send-activity-properties"></a>Gönderme etkinliği özellikleri

Aşağıdaki tabloda <xref:System.ServiceModel.Activities.Send> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, Özellikler kılavuzunda veya İş Akışı Tasarımcısı yüzeyinde düzenlenebilir.

| Özellik Adı | Gerekli | Kullanım |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | Yanlış | Etkinliğin kolay adı <xref:System.ServiceModel.Activities.Send> . Varsayılan değer Gönder ' dir. <xref:System.Activities.Activity.DisplayName%2A>Kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır. |
| <xref:System.ServiceModel.Activities.Send.OperationName%2A> | Doğru | Bu etkinlik tarafından çağrılan hizmet işleminin adı <xref:System.ServiceModel.Activities.Send> . Bu özellik, **Action özelliği açıkça** ayarlanmamışsa **Action** özelliğinin varsayılan değerini oluşturmak için kullanılır. |
| <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> | Doğru | Çağrılacak hizmetin uyguladığı hizmet sözleşmesinin adı. |
| <xref:System.ServiceModel.Activities.Send.Content%2A> | Yanlış | Alacak ileti veya parametre içeriğini belirtir. <xref:System.ServiceModel.Activities.ReceiveMessageContent>Etkinlik ya da <xref:System.ServiceModel.Activities.ReceiveParametersContent> etkinlik olabilir. Özellik kılavuzundaki **içerik** alanının yanındaki üç nokta düğmesini seçerek veya **alma** etkinliği Tasarımcısı yüzeyinde **içerik** etiketinin yanındaki **tanımla...** düğmesine tıklayarak bu özelliği düzenleyin. Her ikisi de **Içerik tanımı** iletişim kutusunu görüntüler. Bu kutunun nasıl kullanılacağı hakkında daha fazla bilgi için [Içerik tanımı Iletişim kutusu](../workflow-designer/content-definition-dialog-box.md) konusuna bakın. |
| <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> | Yanlış | <xref:System.ServiceModel.Activities.CorrelationHandle>İletiyi uygun iş akışı örneğine yönlendirmek için kullanılan öğesini belirtir.<br /><br /> Özellikler kılavuzundaki özelliğin yanındaki üç nokta düğmesine tıklayarak <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> **ifade Düzenleyicisi** iletişim kutusunu açın. Bu iletişim kutusunun kullanımı hakkında daha fazla bilgi için bkz. [nasıl yapılır: Ifade düzenleyicisini kullanma](../workflow-designer/how-to-use-the-expression-editor.md) konusu. |
| <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> | Yanlış | <xref:System.ServiceModel.Activities.CorrelationInitializer> <xref:System.ServiceModel.Activities.CorrelationHandle> Bu <xref:System.ServiceModel.Activities.Send> etkinliği iş akışı içinde yapılandıran birden çok nesneyi başlatacak nesne koleksiyonunu belirtir. Özellikler kılavuzundaki özelliğin yanındaki üç nokta düğmesine tıklayarak <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> **bağıntı başlatıcıları Ekle** iletişim kutusunu açın. Bu kutuyu kullanma hakkında daha fazla bilgi için bkz. [Correlationbaşlatıcıları ekleme Iletişim kutusu](../workflow-designer/add-correlationinitializers-dialog-box.md) konusu. |
| <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> | Yanlış | Bu etkinlik tarafından çağrılacak hizmet işlemi için bilinen türlerin bir koleksiyonu <xref:System.ServiceModel.Activities.Send> . Bu özellik, özelliği olarak ayarlanmış bir ile birlikte kullanılmalıdır <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> <xref:System.Runtime.Serialization.DataContractSerializer> . Kullanılıyorsa yok sayılır <xref:System.Xml.Serialization.XmlSerializer> .<br /><br /> Özellik kılavuzunda **KnownTypes** alanının yanındaki üç nokta düğmesini seçerek ilgili türleri ekleyebileceğiniz **tür koleksiyonu Düzenleyicisi** iletişim kutusunu görüntüleyin.<br /><br /> Özellik kılavuzunda **KnownTypes** alanının yanındaki üç nokta düğmesini seçerek ilgili türleri ekleyebileceğiniz **tür koleksiyonu Düzenleyicisi** iletişim kutusunu görüntüleyin. Bu kutuyu kullanma hakkında daha fazla bilgi için, [tür koleksiyonu Düzenleyicisi Iletişim kutusu](../workflow-designer/type-collection-editor-dialog-box.md) konusuna bakın. |
| <xref:System.ServiceModel.Activities.Send.ProtectionLevel%2A> | Doğru | <xref:System.Net.Security.ProtectionLevel>İleti için belirtir.<br /><br /> 1.  <xref:System.Net.Security.ProtectionLevel> yalnızca kimlik doğrulaması anlamına gelir.<br />2.  <xref:System.Net.Security.ProtectionLevel> aktarılan verilerin bütünlüğünü sağlamaya yardımcı olmak için imza verileri anlamına gelir.<br />3.  <xref:System.Net.Security.ProtectionLevel> iletilen verilerin gizliliğini ve bütünlüğünü sağlamaya yardımcı olmak için verileri şifreleme ve imzalama anlamına gelir. |
| <xref:System.ServiceModel.Activities.Send.SerializerOption%2A> | Doğru | Etkinlik tarafından çağrılacak hizmet işlemi için kullanılacak seri hale getirici <xref:System.ServiceModel.Activities.Send> . Varsayılan değer, bir <xref:System.Runtime.Serialization.DataContractSerializer> tür örneğini seri hale getirilen ve BIR XML akışına veya belgeye sağlanan bir veri sözleşmesini kullanarak seri hale getirir. |
| <xref:System.ServiceModel.Activities.Send.Action%2A> | Yanlış | İletinin eylem üst bilgisini belirtir. Açıkça ayarlanmamışsa, değeri varsayılan olarak şu şekilde olur: `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` . Bir <xref:System.ServiceModel.Activities.Send> etkinlikte belirtilmişse <xref:System.ServiceModel.Activities.Receive> iletiyi alan etkinliğin, ileti doğru şekilde teslim edilebilmesi için aynı değere sahip olması gerekir. |
| <xref:System.ServiceModel.Activities.Send.TokenImpersonationLevel%2A> | | <xref:System.Security.Principal.TokenImpersonationLevel>İleti alıcısı için izin verildi. Bir sunucu işleminin bir istemci işlemi adına işlem yapması için gereken dereceyi belirleyen güvenlik kimliğe bürünme düzeylerini tanımlar.<xref:System.Security.Principal.TokenImpersonationLevel> kimliğe bürünme düzeyi atanmamış olduğunu gösterir. <xref:System.Security.Principal.TokenImpersonationLevel> Sunucu işleminin istemciyle ilgili kimlik bilgilerini alamadığını ve istemcinin kimliğine bürünemediğini belirtir. <xref:System.Security.Principal.TokenImpersonationLevel> Sunucu işleminin istemci hakkında güvenlik tanımlayıcıları ve ayrıcalıklar gibi bilgiler edinebileceğini ancak istemcinin kimliğine bürünemediğini belirtir. Bu, kendi nesnelerini dışarı veren sunucular (örneğin, tabloları ve görünümleri dışa aktarma veritabanı ürünleri) için kullanışlıdır. Alınan istemci güvenlik bilgilerini kullanarak, sunucu, istemcinin güvenlik bağlamını kullanan diğer hizmetleri kullanabilmeniz için erişim doğrulama kararları verebilir. <xref:System.Security.Principal.TokenImpersonationLevel> Sunucu işleminin, yerel sisteminde istemcinin güvenlik bağlamını taklit edebilir olduğunu gösterir. Sunucu, uzak sistemlerde istemcinin kimliğine bürünemedi. <xref:System.Security.Principal.TokenImpersonationLevel> Sunucu işleminin uzak sistemlerde istemcinin güvenlik bağlamını taklit edebilir olduğunu gösterir. |
| <xref:System.ServiceModel.Activities.Send.Endpoint%2A> | | <xref:System.ServiceModel.Endpoint> <xref:System.ServiceModel.Activities.Send> Etkinliğin iletiyi gönderdiği yer. Bu özellik ayarlandıysa, <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> özelliği **null** olmalıdır. |
| <xref:System.ServiceModel.Activities.Send.EndpointAddress%2A> | | <xref:System.ServiceModel.EndpointAddress>İletinin gönderildiği yer. |
| <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> | | Uç nokta yapılandırmasının adı. Bu özellik, bir yapılandırma dosyasında bir uç nokta yapılandırırken ayarlanır. Bu özellik **\<endpoint>** yapılandırma dosyanızdaki öğesinde verilen ada ayarlanmalıdır. Bu özellik ayarlandıysa, <xref:System.ServiceModel.Activities.Send.Endpoint%2A> özelliği **null** olmalıdır. |

## <a name="see-also"></a>Ayrıca bkz.

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Al](../workflow-designer/receive-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)