---
title: İş Akışı Tasarımcısı-etkinlik tasarımcısını al
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Receive.UI
ms.assetid: f58d3c70-944d-4bb4-90a7-e68c103caddc
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8c9dc2a561ce424239df5ec08eb353453b831464
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650035"
---
# <a name="receive-activity-designer"></a>Receive Etkinlik Tasarımcısı

**Alma** etkinliği Tasarımcısı, bir <xref:System.ServiceModel.Activities.Receive> etkinliği oluşturmak ve yapılandırmak için kullanılır. @No__t_0 etkinlik, <xref:System.ServiceModel.Channels.Message>, <xref:System.IO.Stream> veya <xref:System.Xml.Linq.XElement> ya da bir uygulama tanımlı veri sözleşmesi, ileti sözleşmesi veya seri hale getirilemesiz XML sınıfı gibi yerleşik bir tür olabilecek bir ileti alan bir etkinliktir.

## <a name="the-receive-activity"></a>Alma etkinliği

@No__t_0 etkinlik, kullanılan alma içeriğinin türüne bağlı olarak tek bir öğe veya birden çok öğe alabilir. @No__t_0 bir etkinlik, hizmette bir istek/yanıt iletisi değişim deseninin parçası olarak bir ileti alan <xref:System.ServiceModel.Activities.Receive> etkinliğine bağlanabilir.

### <a name="using-the-receive-activity-designer"></a>Alma etkinliği tasarımcısını kullanma

**Araç kutusunun** **mesajlaşma** kategorisindeki **alma** etkinliği tasarımcısına erişin. **Alma** etkinliği Tasarımcısı **araç kutusundan** sürüklenip, etkinliklerin genellikle yerleştirildiği her yerde iş akışı Tasarımcısı yüzeyine bırakılabilir. Bu, varsayılan alma <xref:System.Activities.Activity.DisplayName%2A> bir <xref:System.ServiceModel.Activities.Receive> etkinlik oluşturur. @No__t_0, **alma** etkinliği tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

@No__t_0 bir etkinlik oluşturup seçili <xref:System.ServiceModel.Activities.Receive> etkinliğine bağlamak için, **alma** etkinliği tasarımcısına sağ tıklayın, bağlam menüsünde **SendReply öğesi oluştur** ' a tıklayın ve **SendReplyToReceive** Tasarımcısı ' nın altında **görünür Tasarımcı al** . @No__t_0 etkinliği, yanıt iletisini hizmette bir istek/yanıt iletisi değişim deseninin parçası olarak gönderen bir etkinliktir. **SendReplyToReceive** Tasarımcısı ile yapılandırılabilir.

Alternatif olarak, **araç kutusunun** **mesajlaşma** kategorisindeki **ReceiveAndSendReply** şablon tasarımcısı, önceden yapılandırılmış <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> etkinliğinin bir çiftini oluşturmak için kullanılabilir. **ReceiveAndSendReply** ve **SendReplyToReceive** şablonunun kullanımı hakkında daha fazla bilgi Için, bkz. [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) konusu.

### <a name="the-receive-activity-properties"></a>Alma etkinliği özellikleri

Aşağıdaki tabloda <xref:System.ServiceModel.Activities.Receive> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, Özellikler kılavuzunda veya İş Akışı Tasarımcısı yüzeyinde düzenlenebilir. Tek gerekli özelliği <xref:System.ServiceModel.Activities.Receive.OperationName%2A> özelliğidir.

| Özellik adı | Gerekli | Kullanım |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | @No__t_0 etkinliğinin kolay adını belirtir. Varsayılan değer Al ' dır.<br /><br /> Kolay <xref:System.Activities.Activity.DisplayName%2A> için varsayılan olmayan bir değer kullanımı kesinlikle gerekli olmasa da, bu tür bir değer kullanmak en iyi uygulamadır. |
| <xref:System.ServiceModel.Activities.Receive.OperationName%2A> | Doğru | Bu <xref:System.ServiceModel.Activities.Receive> etkinliği tarafından uygulanan hizmet işleminin adını belirtir. Bu özellik, **Action özelliği açıkça** ayarlanmamışsa **Action** özelliğinin varsayılan değerini oluşturmak için kullanılır. |
| <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> | False | Hizmet sözleşmesinin adını belirtir. Bu özellik, hizmet işlemlerini tek tek hizmet sözleşmeleri halinde gruplandırmak için kullanılır. Aynı <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> sahip olan tüm <xref:System.ServiceModel.Activities.Receive> etkinlikleri aynı hizmet sözleşmesine (WSDL bağlantı noktası türü) gruplanır. Varsayılan değer, en üst düzey (root) etkinliğin tam CLR adıdır. |
| <xref:System.ServiceModel.Activities.Receive.Content%2A> | False | Alacak ileti veya parametre içeriğini belirtir. @No__t_0 bir etkinlik veya bir <xref:System.ServiceModel.Activities.ReceiveParametersContent> etkinliği olabilir. Özellik kılavuzundaki **içerik** alanının yanındaki üç nokta düğmesini seçerek veya **alma** etkinliği Tasarımcısı yüzeyinde **içerik** etiketinin yanındaki **tanımla...** düğmesine tıklayarak bu özelliği düzenleyin. Her ikisi de **Içerik tanımı** iletişim kutusunu görüntüler. Bu kutunun nasıl kullanılacağı hakkında daha fazla bilgi için [Içerik tanımı Iletişim kutusu](../workflow-designer/content-definition-dialog-box.md) konusuna bakın. |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> | False | @No__t_1 nesnesi olan bir iş akışının hizmet işlemlerinde <xref:System.ServiceModel.Activities.Receive> etkinlikleri arasındaki bağıntıları belirtir. Özellikler kılavuzundaki <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> özelliğinin yanındaki üç nokta düğmesine tıklayarak **CorrelatesOn tanımı** iletişim kutusunu açın. Bu iletişim kutusunun kullanımı hakkında daha fazla bilgi için [Içerik tanımı Iletişim kutusu](../workflow-designer/content-definition-dialog-box.md) konusuna bakın. |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> | False | İletiyi uygun iş akışı örneğine yönlendirmek için kullanılan <xref:System.ServiceModel.Activities.CorrelationHandle> belirtir.<br /><br /> Özellikler kılavuzundaki <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> özelliğinin yanındaki üç nokta düğmesine tıklayarak **Ifade Düzenleyicisi** iletişim kutusunu açın. Bu iletişim kutusunun kullanımı hakkında daha fazla bilgi için bkz. [nasıl yapılır: Ifade düzenleyicisini kullanma](../workflow-designer/how-to-use-the-expression-editor.md) konusu. |
| <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> | False | Bu <xref:System.ServiceModel.Activities.Receive> etkinliğini iş akışı içinde yapılandıran birden çok <xref:System.ServiceModel.Activities.CorrelationHandle> nesnesini başlatacak <xref:System.ServiceModel.Activities.CorrelationInitializer> nesnelerinin koleksiyonunu belirtir. Özellikler kılavuzundaki <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> özelliğinin yanındaki üç nokta düğmesine tıklayarak **bağıntı başlatıcıları Ekle** iletişim kutusunu açın. Bu kutuyu kullanma hakkında daha fazla bilgi için bkz. [Correlationbaşlatıcıları ekleme Iletişim kutusu](../workflow-designer/add-correlationinitializers-dialog-box.md) konusu. |
| <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> | False | İleti mevcut bir iş akışı örneğiyle bağıntılı değilse, iletiyi işlemek için yeni bir iş akışı örneği oluşturulup oluşturulmayacağını belirleyen bir değer belirtir. Değer **true**olarak ayarlanırsa, ileti mevcut bir iş akışı örneğiyle bağıntılı olmadığında iletiyi işlemek için yeni bir iş akışı örneği oluşturulur. |
| <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> | False | Bu <xref:System.ServiceModel.Activities.Receive> etkinliği tarafından uygulanan hizmet işlemi için bilinen türlerin bir koleksiyonunu belirtir. Bu özellik, <xref:System.Runtime.Serialization.DataContractSerializer> olarak ayarlanmış <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> özelliği ile birlikte kullanılmalıdır. @No__t_0 kullanılırsa yok sayılır.<br /><br /> Özellik kılavuzunda **KnownTypes** alanının yanındaki üç nokta düğmesini seçerek ilgili türleri ekleyebileceğiniz **tür koleksiyonu Düzenleyicisi** iletişim kutusunu görüntüleyin. Bu kutuyu kullanma hakkında daha fazla bilgi için, [tür koleksiyonu Düzenleyicisi Iletişim kutusu](../workflow-designer/type-collection-editor-dialog-box.md) konusuna bakın. |
| <xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A> | False | İleti için <xref:System.Net.Security.ProtectionLevel> belirtir.<br /><br /> 1. <xref:System.Net.Security.ProtectionLevel> yalnızca kimlik doğrulaması anlamına gelir.<br />2. <xref:System.Net.Security.ProtectionLevel> aktarılan verilerin bütünlüğünü sağlamaya yardımcı olmak için imza verileri anlamına gelir.<br />3. <xref:System.Net.Security.ProtectionLevel> aktarılan verilerin gizliliğini ve bütünlüğünü sağlamaya yardımcı olmak için verileri şifreleme ve imzalama anlamına gelir. |
| <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> | False | @No__t_0 etkinliği tarafından uygulanan hizmet işlemi için kullanılacak seri hale getirici türünü belirtir. Varsayılan değer <xref:System.Runtime.Serialization.DataContractSerializer>, bir türün bir örneğini bir XML akışına veya sağlanan veri sözleşmesini kullanan belgeye seri hale getirir ve seri hale getirir. Ayrıca, XML üzerinde daha fazla denetim gerekliyse <xref:System.Xml.Serialization.XmlSerializer> de kullanılabilir. |
| <xref:System.ServiceModel.Activities.Receive.Action%2A> | False | İletinin eylem üst bilgisini belirtir. Açıkça ayarlanmamışsa, değeri varsayılan olarak: `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`. |

## <a name="see-also"></a>Ayrıca bkz.

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)
