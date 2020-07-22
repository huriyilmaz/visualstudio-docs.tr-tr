---
title: İş Akışı Tasarımcısı-etkinlik tasarımcısını al
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Receive.UI
ms.assetid: f58d3c70-944d-4bb4-90a7-e68c103caddc
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 55f49a32036fcfd5e9f75f3d8dd61499c4af0b2e
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86875728"
---
# <a name="receive-activity-designer"></a>Receive Etkinlik Tasarımcısı

**Alma** etkinliği Tasarımcısı, etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.ServiceModel.Activities.Receive> . <xref:System.ServiceModel.Activities.Receive>Etkinlik, ya da ya da <xref:System.ServiceModel.Channels.Message> <xref:System.IO.Stream> <xref:System.Xml.Linq.XElement> bir uygulama tanımlı veri sözleşmesi, ileti sözleşmesi veya seri hale getirilebilen XML sınıfı gibi yerleşik bir tür olabilecek bir ileti alan bir etkinliktir.

## <a name="the-receive-activity"></a>Alma etkinliği

<xref:System.ServiceModel.Activities.Receive>Etkinlik, kullanılan alma içeriğinin türüne göre tek bir öğe veya birden çok öğe alabilir. <xref:System.ServiceModel.Activities.SendReply>Etkinlik <xref:System.ServiceModel.Activities.Receive> , hizmette istek/yanıt iletisi değişim deseninin bir parçası olarak ileti alan bir etkinliğe bağlanabilir.

### <a name="using-the-receive-activity-designer"></a>Alma etkinliği tasarımcısını kullanma

**Araç kutusunun** **mesajlaşma** kategorisindeki **alma** etkinliği tasarımcısına erişin. **Alma** etkinliği Tasarımcısı **araç kutusundan** sürüklenip, etkinliklerin genellikle yerleştirildiği her yerde iş akışı Tasarımcısı yüzeyine bırakılabilir. Bu <xref:System.ServiceModel.Activities.Receive> , varsayılan alma için bir etkinlik oluşturur <xref:System.Activities.Activity.DisplayName%2A> . , <xref:System.Activities.Activity.DisplayName%2A> **Alma** etkinliği tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

Bir etkinlik oluşturup <xref:System.ServiceModel.Activities.SendReply> Seçili etkinliğe bağlamak Için <xref:System.ServiceModel.Activities.Receive> **alma** etkinliği tasarımcısına sağ tıklayın, bağlam menüsünde **SendReply öğesi oluştur** ' a tıklayın ve **alma** tasarımcısının altında **SendReplyToReceive** Tasarımcısı görüntülenir. <xref:System.ServiceModel.Activities.SendReply>Etkinlik, yanıt iletisini hizmette bir istek/yanıt iletisi değişim deseninin parçası olarak gönderen bir etkinliktir. **SendReplyToReceive** Tasarımcısı ile yapılandırılabilir.

Alternatif olarak, **araç kutusunun** **mesajlaşma** kategorisindeki **ReceiveAndSendReply** şablon Tasarımcısı, önceden yapılandırılmış ve etkinlik çifti oluşturmak için kullanılabilir <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> . **ReceiveAndSendReply** ve **SendReplyToReceive** şablonunun kullanımı hakkında daha fazla bilgi Için, bkz. [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) konusu.

### <a name="the-receive-activity-properties"></a>Alma etkinliği özellikleri

Aşağıdaki tabloda <xref:System.ServiceModel.Activities.Receive> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, Özellikler kılavuzunda veya İş Akışı Tasarımcısı yüzeyinde düzenlenebilir. Özelliği yalnızca gerekli olan özelliktir <xref:System.ServiceModel.Activities.Receive.OperationName%2A> .

| Özellik Adı | Gerekli | Kullanım |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | Yanlış | Etkinliğin kolay adını belirtir <xref:System.ServiceModel.Activities.Receive> . Varsayılan değer Al ' dır.<br /><br /> Kolay için varsayılan olmayan bir değer kullanılması <xref:System.Activities.Activity.DisplayName%2A> kesinlikle gerekli olmasa da, bu tür bir değer kullanmak en iyi uygulamadır. |
| <xref:System.ServiceModel.Activities.Receive.OperationName%2A> | Doğru | Bu etkinlik tarafından uygulanan hizmet işleminin adını belirtir <xref:System.ServiceModel.Activities.Receive> . Bu özellik, **Action özelliği açıkça** ayarlanmamışsa **Action** özelliğinin varsayılan değerini oluşturmak için kullanılır. |
| <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> | Yanlış | Hizmet sözleşmesinin adını belirtir. Bu özellik, hizmet işlemlerini tek tek hizmet sözleşmeleri halinde gruplandırmak için kullanılır. Aynı olan tüm <xref:System.ServiceModel.Activities.Receive> Etkinlikler <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> aynı hizmet SÖZLEŞMESINE (wsdl bağlantı noktası türü) gruplanır. Varsayılan değer, en üst düzey (root) etkinliğin tam CLR adıdır. |
| <xref:System.ServiceModel.Activities.Receive.Content%2A> | Yanlış | Alacak ileti veya parametre içeriğini belirtir. <xref:System.ServiceModel.Activities.ReceiveMessageContent>Etkinlik ya da <xref:System.ServiceModel.Activities.ReceiveParametersContent> etkinlik olabilir. Özellik kılavuzundaki **içerik** alanının yanındaki üç nokta düğmesini seçerek veya **alma** etkinliği Tasarımcısı yüzeyinde **içerik** etiketinin yanındaki **tanımla...** düğmesine tıklayarak bu özelliği düzenleyin. Her ikisi de **Içerik tanımı** iletişim kutusunu görüntüler. Bu kutunun nasıl kullanılacağı hakkında daha fazla bilgi için [Içerik tanımı Iletişim kutusu](../workflow-designer/content-definition-dialog-box.md) konusuna bakın. |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> | Yanlış | Bir <xref:System.ServiceModel.Activities.Receive> nesne ile bir iş akışının hizmet işlemlerinde etkinlikler arasındaki bağıntıları belirtir <xref:System.ServiceModel.MessageQuerySet> . Özellikler kılavuzundaki özelliğin yanındaki üç nokta düğmesine tıklayarak <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> **CorrelatesOn tanımı** iletişim kutusunu açın. Bu iletişim kutusunun kullanımı hakkında daha fazla bilgi için [Içerik tanımı Iletişim kutusu](../workflow-designer/content-definition-dialog-box.md) konusuna bakın. |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> | Yanlış | <xref:System.ServiceModel.Activities.CorrelationHandle>İletiyi uygun iş akışı örneğine yönlendirmek için kullanılan öğesini belirtir.<br /><br /> Özellikler kılavuzundaki özelliğin yanındaki üç nokta düğmesine tıklayarak <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> **ifade Düzenleyicisi** iletişim kutusunu açın. Bu iletişim kutusunun kullanımı hakkında daha fazla bilgi için bkz. [nasıl yapılır: Ifade düzenleyicisini kullanma](../workflow-designer/how-to-use-the-expression-editor.md) konusu. |
| <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> | Yanlış | <xref:System.ServiceModel.Activities.CorrelationInitializer> <xref:System.ServiceModel.Activities.CorrelationHandle> Bu <xref:System.ServiceModel.Activities.Receive> etkinliği iş akışı içinde yapılandıran birden çok nesneyi başlatacak nesne koleksiyonunu belirtir. Özellikler kılavuzundaki özelliğin yanındaki üç nokta düğmesine tıklayarak <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> **bağıntı başlatıcıları Ekle** iletişim kutusunu açın. Bu kutuyu kullanma hakkında daha fazla bilgi için bkz. [Correlationbaşlatıcıları ekleme Iletişim kutusu](../workflow-designer/add-correlationinitializers-dialog-box.md) konusu. |
| <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> | Yanlış | İleti mevcut bir iş akışı örneğiyle bağıntılı değilse, iletiyi işlemek için yeni bir iş akışı örneği oluşturulup oluşturulmayacağını belirleyen bir değer belirtir. Değer **true**olarak ayarlanırsa, ileti mevcut bir iş akışı örneğiyle bağıntılı olmadığında iletiyi işlemek için yeni bir iş akışı örneği oluşturulur. |
| <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> | Yanlış | Bu etkinlik tarafından uygulanan hizmet işlemi için bilinen türlerin bir koleksiyonunu belirtir <xref:System.ServiceModel.Activities.Receive> . Bu özellik, <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> özelliği olarak ayarlanmış özellik ile birlikte kullanılmalıdır <xref:System.Runtime.Serialization.DataContractSerializer> . Kullanılıyorsa yok sayılır <xref:System.Xml.Serialization.XmlSerializer> .<br /><br /> Özellik kılavuzunda **KnownTypes** alanının yanındaki üç nokta düğmesini seçerek ilgili türleri ekleyebileceğiniz **tür koleksiyonu Düzenleyicisi** iletişim kutusunu görüntüleyin. Bu kutuyu kullanma hakkında daha fazla bilgi için, [tür koleksiyonu Düzenleyicisi Iletişim kutusu](../workflow-designer/type-collection-editor-dialog-box.md) konusuna bakın. |
| <xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A> | Yanlış | <xref:System.Net.Security.ProtectionLevel>İleti için belirtir.<br /><br /> 1. <xref:System.Net.Security.ProtectionLevel> yalnızca kimlik doğrulaması anlamına gelir.<br />2. <xref:System.Net.Security.ProtectionLevel> aktarılan verilerin bütünlüğünü sağlamaya yardımcı olmak için imza verileri anlamına gelir.<br />3. <xref:System.Net.Security.ProtectionLevel> iletilen verilerin gizliliğini ve bütünlüğünü sağlamaya yardımcı olmak için verileri şifreleme ve imzalama anlamına gelir. |
| <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> | Yanlış | Etkinlik tarafından uygulanan hizmet işlemi için kullanılacak seri hale getirici türünü belirtir <xref:System.ServiceModel.Activities.Receive> . Varsayılan değer, <xref:System.Runtime.Serialization.DataContractSerializer> bir türdeki bir örneği BIR XML akışına veya sağlanan veri sözleşmesini kullanan belgeye seri hale getirir ve seri hale getirir. <xref:System.Xml.Serialization.XmlSerializer>XML üzerinde daha fazla denetim gerekliyse de kullanılabilir. |
| <xref:System.ServiceModel.Activities.Receive.Action%2A> | Yanlış | İletinin eylem üst bilgisini belirtir. Açıkça ayarlanmamışsa, değeri varsayılan olarak şu şekilde olur: `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` . |

## <a name="see-also"></a>Ayrıca bkz.

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Gönder](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)
