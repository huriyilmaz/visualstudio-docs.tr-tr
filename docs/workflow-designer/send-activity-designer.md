---
title: İş Akışı Tasarımcısı - Etkinlik Tasarımcısı Gönder
description: Gönder etkinliği hakkında bilgi ve Send etkinliği oluşturmak ve yapılandırmak için Etkinlik gönder tasarımcısını nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Send.UI
ms.assetid: b514f2e4-767c-4b94-ac61-dd3a54d4b96d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 1574d6b48e904288cde5ea66be6350430b81bc44
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963704"
---
# <a name="send-activity-designer"></a>Send Etkinlik Tasarımcısı

Etkinlik **oluşturmak** ve yapılandırmak için Etkinlik gönder tasarımcısı <xref:System.ServiceModel.Activities.Send> kullanılır.

## <a name="the-send-activity"></a>Gönderme Etkinliği

 Bir <xref:System.ServiceModel.Activities.Send> hizmete ileti göndermek için etkinlik kullanılır. Bir etkinlik, istemcide istek/yanıt iletisi değişim deseninin bir <xref:System.ServiceModel.Activities.ReceiveReply> parçası olarak ileti alan bir <xref:System.ServiceModel.Activities.Send> etkinlike bağlı olabilir.

### <a name="using-the-send-activity-designer"></a>Etkinlik Tasarımcısı gönder'i kullanma

Araç **Kutusunun Mesajlaşma** **kategorisindeKimlik gönder** etkinliği **tasarımcısına erişin.** Etkinlik **gönder** tasarımcısı Araç Kutusundan **sürüklenip** etkinlikler genellikle yerleştirildikten sonra İş Akışı Tasarımcısı yüzeyine bırakılır. Bu, varsayılan <xref:System.ServiceModel.Activities.Send> Send değerine sahip bir <xref:System.Activities.Activity.DisplayName%2A> etkinlik oluşturur. <xref:System.Activities.Activity.DisplayName%2A>, Etkinlik gönder tasarımcısının üst  bilgisinde veya özellik kılavuzundaki **DisplayName** kutusunda düzenlenebilir.

Bir etkinlik oluşturmak ve seçilen etkinlike bağlamak için, Etkinlik gönder tasarımcısına sağ tıklayın, bağlam menüsünde ReceiveReply Oluştur'a tıklayın ve Gönder tasarımcısının altında <xref:System.ServiceModel.Activities.ReceiveReply> <xref:System.ServiceModel.Activities.Send> **ReceiveReplyForSend** tasarımcısı görünür.    Etkinlik, <xref:System.ServiceModel.Activities.ReceiveReply> istemcide istek/yanıt iletisi değişim deseninin bir parçası olarak ileti alan bir etkinliktir. **ReceiveReplyForSend tasarımcısıyla yalıtıldığında.**

Alternatif olarak, Araç Kutusunun Mesajlaşma kategorisindeki **SendAndReceiveReply** şablon tasarımcısı, önceden yapılandırılmış ve etkinlik çifti oluşturmak için   <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> kullanılabilir. **SendAndReceiveReply** ve **ReceiveReplyForSend** şablonlarının kullanımı hakkında daha fazla bilgi için [SendAndReceiveReply konu başlığına](../workflow-designer/sendandreceivereply-template-designer.md) bakın.

### <a name="the-send-activity-properties"></a>Etkinlik Özelliklerini Gönderme

Aşağıdaki tablo, <xref:System.ServiceModel.Activities.Send> özellikleri gösterir ve tasarımcıda nasıl kullanıldıklarını açıklar. Bu özellikler özellikler kılavuzunda veya İş Akışı Tasarımcısı düzenlenebilir.

| Özellik Adı | Gerekli | Kullanım |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | Yanlış | Etkinliğin kolay <xref:System.ServiceModel.Activities.Send> adı. Varsayılan değer Gönder'tir. kesinlikle <xref:System.Activities.Activity.DisplayName%2A> gerekli değildir, ancak bir tane kullanmak en iyi uygulamadır. |
| <xref:System.ServiceModel.Activities.Send.OperationName%2A> | Doğru | Bu etkinlik tarafından çağrılan hizmet işlemi <xref:System.ServiceModel.Activities.Send> adı. Bu özellik, Action özelliği açıkça ayarlanmazsa **Action** özelliği **için** varsayılan değeri oluşturmak için kullanılır. |
| <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> | Doğru | Çağrılacak hizmetin uygulayan hizmet sözleşmesinin adı. |
| <xref:System.ServiceModel.Activities.Send.Content%2A> | Yanlış | Alacak iletiyi veya parametre içeriğini belirtir. Bir etkinlik veya <xref:System.ServiceModel.Activities.ReceiveMessageContent> etkinlik <xref:System.ServiceModel.Activities.ReceiveParametersContent> olabilir. Özellik kılavuzunda İçerik alanı'nın yanındaki  üç nokta düğmesini seçerek veya Alma etkinliği tasarımcısı  yüzeyinde İçerik etiketinin yanındaki **Tanımla...** düğmesine tıklayarak bu özelliği düzenleyin.  Her ikisi de **İçerik Tanımı iletişim kutusunu** görüntüler. Bu kutunun kullanımı hakkında daha fazla bilgi için İçerik Tanımı [İletişim Kutusu konu başlığına](../workflow-designer/content-definition-dialog-box.md) bakın. |
| <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> | Yanlış | İletiyi <xref:System.ServiceModel.Activities.CorrelationHandle> uygun iş akışı örneğine yönlendirmek için kullanılanı belirtir.<br /><br /> İfade Düzenleyicisi iletişim kutusunu açmak için <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> özellikler kılavuzunda özelliğin yanındaki üç **nokta düğmesine** tıklayın. Bu iletişim kutusunun kullanımı hakkında daha fazla bilgi için İfade [Düzenleyicisi'ni Kullanma konu başlığına](../workflow-designer/how-to-use-the-expression-editor.md) bakın. |
| <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> | Yanlış | bu etkinliği iş akışı <xref:System.ServiceModel.Activities.CorrelationInitializer> içinde yapılandıran <xref:System.ServiceModel.Activities.CorrelationHandle> birden çok nesne başlatan nesnelerin koleksiyonunu <xref:System.ServiceModel.Activities.Send> belirtir. Özellikler kılavuzunda özelliğin yanındaki üç nokta düğmesine <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> tıklayarak Bağıntı **Başlatıcıları Ekle iletişim kutusunu** açın. Bu kutuyu kullanma hakkında daha fazla bilgi için [CorrelationInitializers Ekle İletişim Kutusu konu başlığına](../workflow-designer/add-correlationinitializers-dialog-box.md) bakın. |
| <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> | Yanlış | Bu etkinlik tarafından çağrılan hizmet işlemi için bilinen türlerden bir <xref:System.ServiceModel.Activities.Send> koleksiyon. Bu özellik, olarak ayarlanmış özellik ile <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> birlikte <xref:System.Runtime.Serialization.DataContractSerializer> kullanılmalıdır. Kullanılırsa <xref:System.Xml.Serialization.XmlSerializer> yoksayılır.<br /><br /> özellik kılavuzunda **KnownTypes** alanı yanındaki üç nokta düğmesini seçerek ilgili türleri **ekyebilirsiniz** Tür Koleksiyonu Düzenleyicisi iletişim kutusunu açın.<br /><br /> özellik kılavuzunda **KnownTypes** alanı yanındaki üç nokta düğmesini seçerek ilgili türleri **ekyebilirsiniz** Tür Koleksiyonu Düzenleyicisi iletişim kutusunu açın. Bu kutuyu kullanma hakkında daha fazla bilgi için Tür [Koleksiyonu Düzenleyicisi İletişim Kutusu konu başlığına](../workflow-designer/type-collection-editor-dialog-box.md) bakın. |
| <xref:System.ServiceModel.Activities.Send.ProtectionLevel%2A> | Doğru | İleti <xref:System.Net.Security.ProtectionLevel> için belirtir.<br /><br /> 1.  <xref:System.Net.Security.ProtectionLevel> Yalnızca kimlik doğrulaması anlamına gelir.<br />2.  <xref:System.Net.Security.ProtectionLevel> aktarılan verilerin bütünlüğünü sağlamaya yardımcı olmak için veri imzalama anlamına gelir.<br />3.  <xref:System.Net.Security.ProtectionLevel> aktarılan verilerin gizliliğini ve bütünlüğünü sağlamaya yardımcı olmak için verileri şifreleme ve imzalama anlamına gelir. |
| <xref:System.ServiceModel.Activities.Send.SerializerOption%2A> | Doğru | Etkinlik tarafından çağrılarak hizmet işlemi için kullanmak üzere seri hale <xref:System.ServiceModel.Activities.Send> getirici. Varsayılan değer, sağlanan bir veri sözleşmesini kullanarak bir türün örneğini bir XML akışında veya belgede seri hale getiren ve seri durumdan alan <xref:System.Runtime.Serialization.DataContractSerializer> değeridir. |
| <xref:System.ServiceModel.Activities.Send.Action%2A> | Yanlış | İletinin eylem üst bilgilerini belirtir. Açıkça ayarlanmaması, değerinin varsayılan değeri: `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` . Bir etkinlikte belirtilirse, iletinin doğru teslimi için iletiyi <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.Receive> alan etkinliğin aynı değere sahip olması gerekir. |
| <xref:System.ServiceModel.Activities.Send.TokenImpersonationLevel%2A> | | İletinin <xref:System.Security.Principal.TokenImpersonationLevel> alıcısı için izin verilen. Güvenlik kimliğe bürünme düzeylerini tanımlar ve bu düzey, bir sunucu işleminin bir istemci işlemi adına ne derece davrana bir işlemle ilgili olarak hareket yetkisine sahip olduğunu yönetir.<xref:System.Security.Principal.TokenImpersonationLevel> kimliğe bürünme düzeyinin atanmamış olduğunu gösterir. <xref:System.Security.Principal.TokenImpersonationLevel> , sunucu işleminin istemci hakkında tanımlama bilgileri edinemey olduğunu ve istemcinin kimliğine bürünemey olduğunu gösterir. <xref:System.Security.Principal.TokenImpersonationLevel> , sunucu işleminin güvenlik tanımlayıcıları ve ayrıcalıklar gibi istemci hakkında bilgi edinebilir, ancak istemcinin kimliğine bürünemey olduğunu gösterir. Bu, tabloları ve görünümleri dışarı aktaran veritabanı ürünleri gibi kendi nesnelerini dışarı aktaran sunucular için yararlıdır. Sunucu, alınan istemci güvenliği bilgilerini kullanarak, istemcinin güvenlik bağlamını kullanan diğer hizmetleri kullanamadan erişim doğrulama kararları alabilir. <xref:System.Security.Principal.TokenImpersonationLevel> , sunucu işleminin yerel sisteminde istemcinin güvenlik bağlamının kimliğine bürünüle olduğunu gösterir. Sunucu, uzak sistemlerde istemcinin kimliğine bürünamaz. <xref:System.Security.Principal.TokenImpersonationLevel> , sunucu işleminin uzak sistemlerde istemcinin güvenlik bağlamının kimliğine bürünüle olduğunu gösterir. |
| <xref:System.ServiceModel.Activities.Send.Endpoint%2A> | | <xref:System.ServiceModel.Endpoint>Etkinliğin <xref:System.ServiceModel.Activities.Send> iletiyi gönderdiği. Bu özellik ayarlanırsa özelliği <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> **null olmalıdır.** |
| <xref:System.ServiceModel.Activities.Send.EndpointAddress%2A> | | İletinin <xref:System.ServiceModel.EndpointAddress> gönderildiği. |
| <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> | | Uç nokta yapılandırmasının adı. Bu özellik, bir yapılandırma dosyasında uç nokta yapılandırırken ayarlanır. Bu özellik, yapılandırma dosyanız içinde öğesinde **\<endpoint>** verilen ad olarak ayar gerekir. Bu özellik ayarlanırsa, özelliği <xref:System.ServiceModel.Activities.Send.Endpoint%2A> **null olmalıdır.** |

## <a name="see-also"></a>Ayrıca bkz.

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Al](../workflow-designer/receive-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)