---
title: İş Akışı Tasarımcısı - Etkinlik Tasarımcısı Gönder
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Send.UI
ms.assetid: b514f2e4-767c-4b94-ac61-dd3a54d4b96d
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8690d5ccf18c752aacb37a71243d9f591fb9ee30
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395214"
---
# <a name="send-activity-designer"></a>Send Etkinlik Tasarımcısı

**Bir** <xref:System.ServiceModel.Activities.Send> etkinlik oluşturmak ve yapılandırmak için Etkinlik Gönder tasarımcısı kullanılır.

## <a name="the-send-activity"></a>Gönderme Etkinliği

 Bir <xref:System.ServiceModel.Activities.Send> hizmete ileti göndermek için bir etkinlik kullanılır. Bir <xref:System.ServiceModel.Activities.ReceiveReply> etkinlik, istemcideki <xref:System.ServiceModel.Activities.Send> istek/yanıt iletisi değiştirme deseninin bir parçası olarak ileti alan bir aktiviteye bağlanabilir.

### <a name="using-the-send-activity-designer"></a>Etkinlik Gönder Tasarımcısını Kullanma

**Araç Kutusu'nun** **Mesajlaşma** kategorisinde etkinlik **tasarımcısıgönder'e** erişin. **Etkinlik gönder** tasarımcısı **Araç Kutusundan** sürüklenebilir ve etkinliklerin genellikle yerleştirildiği her yerde İş Akışı Tasarımcısı yüzeyine bırakılabilir. Bu, Gönder <xref:System.ServiceModel.Activities.Send> varsayılanı <xref:System.Activities.Activity.DisplayName%2A> olan bir etkinlik oluşturur. Etkinlik <xref:System.Activities.Activity.DisplayName%2A> **gönder** tasarımcısının üstbilgisinde veya özellik ızgarasının **DisplayName** kutusunda düzenlenebilir.

Bir <xref:System.ServiceModel.Activities.ReceiveReply> etkinlik oluşturmak ve seçili <xref:System.ServiceModel.Activities.Send> aktiviteye bağlamak için, **Etkinlik Gönder** tasarımcısını sağ tıklatın, bağlam menüsünde Yanıt Al öğesini **oluştur'u** tıklatın ve Gönder **tasarımcısının** altında **ReceiveReplyForSend** tasarımcısı görünür. Etkinlik, <xref:System.ServiceModel.Activities.ReceiveReply> istemcideki istek/yanıt iletisi değiştirme deseninin bir parçası olarak ileti alan bir etkinliktir. **ReceiveReplyForSend** tasarımcısı ile yapılandırılabilir.

Alternatif olarak, **Araç Kutusu'nun** **Mesajlaşma** kategorisindeki **SendAndReceiveReply** şablonu tasarımcısı, önceden yapılandırılmış <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply> bir çift etkinlik oluşturmak için kullanılabilir. **SendAndReceiveReply** ve **ReceiveReplyForSend** şablonlarının kullanımı hakkında daha fazla bilgi için [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) konusuna bakın.

### <a name="the-send-activity-properties"></a>Etkinlik Gönder Özellikleri

Aşağıdaki tablo <xref:System.ServiceModel.Activities.Send> özellikleri gösterir ve tasarımcınasıl kullanıldığını açıklar. Bu özellikler özellikleri ızgara veya İş Akışı Tasarımcısı yüzeyinde düzenlenebilir.

| Özellik Adı | Gerekli | Kullanım |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Aktivitenin <xref:System.ServiceModel.Activities.Send> dostça adı. Varsayılan olarak Gönder'dir. Kesinlikle <xref:System.Activities.Activity.DisplayName%2A> gerekli olmasa da, bir kullanmak için en iyi uygulamadır. |
| <xref:System.ServiceModel.Activities.Send.OperationName%2A> | True | Bu <xref:System.ServiceModel.Activities.Send> etkinlik tarafından çağrılan hizmet işleminin adı. Bu özellik, **Eylem** özelliği açıkça ayarlanmamışsa, **Eylem** özelliği için varsayılan değeri oluşturmak için kullanılır. |
| <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> | True | Çağrılacak hizmet sözleşmesinin adı uygular. |
| <xref:System.ServiceModel.Activities.Send.Content%2A> | False | Alınacak ileti veya parametre içeriğini belirtir. Bir <xref:System.ServiceModel.Activities.ReceiveMessageContent> etkinlik veya bir <xref:System.ServiceModel.Activities.ReceiveParametersContent> etkinlik olabilir. Özellik **ızgarasındaKi İçerik** alanının yanındaki elips düğmesini seçerek veya **Etkinlik** tasarımcısı **yüzeyindeİçerik** etiketinin yanındaki **Tanımla düğmesini** tıklatarak bu özelliği düzenleme. Her ikisi de **İçerik Tanımı** iletişim kutusunu görüntüler. Bu kutunun nasıl kullanılacağı hakkında daha fazla bilgi için [İçerik Tanımı İletişim Kutusu](../workflow-designer/content-definition-dialog-box.md) konusuna bakın. |
| <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> | False | İletiyi <xref:System.ServiceModel.Activities.CorrelationHandle> uygun iş akışı örneğine yönlendirmek için kullanılanları belirtir.<br /><br /> **İfade Düzenleyicisi** iletişim kutusunu <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> açmak için özellikler ızgarasındaki özelliğin yanındaki elips düğmesini tıklatın. Bu iletişim kutusunun kullanımı hakkında daha fazla bilgi için [nasıl kullanılır: İfade Düzenleyicisi](../workflow-designer/how-to-use-the-expression-editor.md) konusunu kullanın. |
| <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> | False | İş akışı içinde <xref:System.ServiceModel.Activities.CorrelationInitializer> bu <xref:System.ServiceModel.Activities.CorrelationHandle> <xref:System.ServiceModel.Activities.Send> etkinliği yapılandıran birden çok nesneyi açan nesnelerin toplanmasını belirtir. <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> **Bağıntı Ekle Initializers** iletişim kutusunu açmak için özellikler ızgarasında ki özelliğin yanındaki elips düğmesini tıklatın. Bu kutuyu kullanma hakkında daha fazla bilgi [için, Bağıntı EkleInitializers İletişim Kutusu](../workflow-designer/add-correlationinitializers-dialog-box.md) konusuna bakın. |
| <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> | False | Bu <xref:System.ServiceModel.Activities.Send> etkinlik tarafından çağrılacak hizmet çalışması için bilinen türler topluluğu. Bu özellik, '' <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> olarak <xref:System.Runtime.Serialization.DataContractSerializer>ayarlanmış özellik ile birlikte kullanılmalıdır. Kullanılırsa <xref:System.Xml.Serialization.XmlSerializer> yoksayılır.<br /><br /> Özellik Tablosundaki **KnownTypes** alanının yanındaki elips düğmesini seçerek, ilgili türleri ekleyebileceğiniz **Tür Koleksiyonu Düzenleyicisi** iletişim kutusunu görüntüleyin.<br /><br /> Özellik **ızgarasındaki KnownTypes** alanının yanındaki elips düğmesini seçerek, ilgili türleri ekleyebileceğiniz **Tür Koleksiyonu Düzenleyicisi** iletişim kutusunu görüntüleyin. Bu kutuyu kullanma hakkında daha fazla bilgi [için, Tür Koleksiyonu Düzenleyicisi İletişim Kutusu](../workflow-designer/type-collection-editor-dialog-box.md) konusuna bakın. |
| <xref:System.ServiceModel.Activities.Send.ProtectionLevel%2A> | True | İleti için <xref:System.Net.Security.ProtectionLevel> belirtir.<br /><br /> 1. <xref:System.Net.Security.ProtectionLevel> yalnızca kimlik doğrulama anlamına gelir.<br />2. <xref:System.Net.Security.ProtectionLevel> aktarılan verilerin bütünlüğünü sağlamaya yardımcı olmak için veri işareti anlamına gelir.<br />3. <xref:System.Net.Security.ProtectionLevel> aktarılan verilerin gizliliğini ve bütünlüğünü sağlamaya yardımcı olmak için verileri şifrelemek ve imzalamak anlamına gelir. |
| <xref:System.ServiceModel.Activities.Send.SerializerOption%2A> | True | Hizmet işlemi için kullanılacak serileştirici <xref:System.ServiceModel.Activities.Send> etkinlik tarafından çağrılacak. Varsayılan değer, <xref:System.Runtime.Serialization.DataContractSerializer>sağlanan bir veri sözleşmesi kullanarak bir tür örneğini XML akışına veya belgeye serileştiren ve deserialize eden değerdir. |
| <xref:System.ServiceModel.Activities.Send.Action%2A> | False | İletinin eylem üstbilgisini belirtir. Açıkça ayarlanmazsa, değeri varsayılan olarak: `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`. Bir <xref:System.ServiceModel.Activities.Send> etkinlikte belirtiliyorsa, iletiyi alan <xref:System.ServiceModel.Activities.Receive> etkinliğin, iletinin doğru teslim edilmesi için aynı değere sahip olması gerekir. |
| <xref:System.ServiceModel.Activities.Send.TokenImpersonationLevel%2A> | | İletinin <xref:System.Security.Principal.TokenImpersonationLevel> alıcısı için izin verilir. Bir sunucu işleminin istemci işlemi adına hareket etme derecesini yöneten güvenlik kimliğe bürünme düzeylerini tanımlar.<xref:System.Security.Principal.TokenImpersonationLevel> bir kimliğe bürünme düzeyiatanmadığını gösterir. <xref:System.Security.Principal.TokenImpersonationLevel>sunucu işleminin istemci hakkında kimlik bilgileri elde edemeyeceğini ve istemcinin kimliğine bürünemeyeceğini gösterir. <xref:System.Security.Principal.TokenImpersonationLevel>sunucu işleminin istemci hakkında güvenlik tanımlayıcıları ve ayrıcalıkları gibi bilgiler edinebileceğini, ancak istemcinin kimliğine bürünemeyeceğini gösterir. Bu, tabloları ve görünümleri dışa aktaran veritabanı ürünleri gibi kendi nesnelerini dışa aktaran sunucular için yararlıdır. Sunucu, alınan istemci güvenlik bilgilerini kullanarak, istemcinin güvenlik bağlamını kullanan diğer hizmetleri kullanamadan erişim doğrulama kararları alabilir. <xref:System.Security.Principal.TokenImpersonationLevel>sunucu işleminin istemcinin güvenlik bağlamını yerel sisteminde taklit edebileceğini gösterir. Sunucu uzak sistemlerde istemcinin kimliğine bürünemez. <xref:System.Security.Principal.TokenImpersonationLevel>sunucu işleminin istemcinin güvenlik bağlamını uzak sistemlerde taklit edebileceğini gösterir. |
| <xref:System.ServiceModel.Activities.Send.Endpoint%2A> | | <xref:System.ServiceModel.Endpoint> Etkinliğin iletiyi <xref:System.ServiceModel.Activities.Send> gönderdiği. Bu özellik ayarlanmışsa <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> özellik **null**olmalıdır. |
| <xref:System.ServiceModel.Activities.Send.EndpointAddress%2A> | | <xref:System.ServiceModel.EndpointAddress> İletinin gönderildiği. |
| <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> | | Bitiş noktası yapılandırmasının adı. Yapılandırma dosyasında bir bitiş noktası yapılandırırken bu özellik ayarlanır. Bu özellik, yapılandırma dosyanızdaki ** \<bitiş noktası>** öğesinde verilen ada ayarlanmalıdır. Bu özellik ayarlanmışsa, <xref:System.ServiceModel.Activities.Send.Endpoint%2A> özellik **null**olmalıdır. |

## <a name="see-also"></a>Ayrıca bkz.

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Al](../workflow-designer/receive-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)