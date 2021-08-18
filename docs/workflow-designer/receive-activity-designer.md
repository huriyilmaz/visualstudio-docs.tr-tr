---
title: İş Akışı Tasarımcısı - Alma Etkinliği Tasarımcısı
description: Alma etkinliği ve Alma etkinliği oluşturmak ve yapılandırmak için Alma etkinlik tasarımcısını kullanma hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Receive.UI
ms.assetid: f58d3c70-944d-4bb4-90a7-e68c103caddc
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 1319dcbdbbefe6639fe6d52b4dfb5c5d5015ad22
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122045807"
---
# <a name="receive-activity-designer"></a>Receive Etkinlik Tasarımcısı

Etkinlik oluşturmak ve yapılandırmak için **Alma** etkinliği tasarımcısı <xref:System.ServiceModel.Activities.Receive> kullanılır. Etkinlik, , veya gibi yerleşik bir tür ya da seri hale getirilecek uygulama tanımlı bir veri sözleşmesi, ileti sözleşmesi veya XML sınıfı olarak iletiyi alan <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Channels.Message> bir <xref:System.IO.Stream> <xref:System.Xml.Linq.XElement> etkinliktir.

## <a name="the-receive-activity"></a>Alma Etkinliği

Etkinlik, <xref:System.ServiceModel.Activities.Receive> kullanılan alma içeriğinin türüne bağlı olarak tek bir öğe veya birden çok öğe alır. Bir etkinlik, hizmette istek/yanıt iletisi değişim deseninin bir <xref:System.ServiceModel.Activities.SendReply> parçası olarak ileti alan bir <xref:System.ServiceModel.Activities.Receive> etkinlike bağlı olabilir.

### <a name="using-the-receive-activity-designer"></a>Alma Etkinliği Tasarımcısını Kullanma

Araç Kutusunun **Mesajlaşma** **kategorisindeKimlik alma** etkinliği **tasarımcısına erişin.** Alma  etkinliği tasarımcısı Araç Kutusundan **sürüklenip** etkinlikler genellikle yerleştirildikten sonra İş Akışı Tasarımcısı yüzeyine bırakılır. Bu, varsayılan <xref:System.ServiceModel.Activities.Receive> Receive değerine sahip bir <xref:System.Activities.Activity.DisplayName%2A> etkinlik oluşturur. <xref:System.Activities.Activity.DisplayName%2A>, Receive etkinlik tasarımcısının üst  bilgisinde veya özellik kılavuzundaki **DisplayName** kutusunda düzenlenebilir.

Bir etkinlik oluşturmak ve seçili etkinlike bağlamak için Alma etkinliği tasarımcısına sağ tıklayın, bağlam menüsünde SendReply Oluştur öğesini tıklatın ve Alma tasarımcısının altında <xref:System.ServiceModel.Activities.SendReply> <xref:System.ServiceModel.Activities.Receive> **SendReplyToReceive** tasarımcısı görünür.    Etkinlik, <xref:System.ServiceModel.Activities.SendReply> hizmette istek/yanıt iletisi değişim deseninin bir parçası olarak yanıt iletisi gönderen bir etkinliktir. **SendReplyToReceive tasarımcısıyla yalıtıldığında.**

Alternatif olarak, Araç Kutusunun Mesajlaşma kategorisindeki  **ReceiveAndSendReply** şablon tasarımcısı, önceden yapılandırılmış ve etkinlik çifti oluşturmak  <xref:System.ServiceModel.Activities.Receive> için <xref:System.ServiceModel.Activities.SendReply> kullanılabilir. **ReceiveAndSendReply** ve **SendReplyToReceive** şablonunun kullanımı hakkında daha fazla bilgi için [ReceiveAndSendReply konu başlığına](../workflow-designer/receiveandsendreply-template-designer.md) bakın.

### <a name="the-receive-activity-properties"></a>Alma Etkinliği Özellikleri

Aşağıdaki tablo, <xref:System.ServiceModel.Activities.Receive> özellikleri gösterir ve tasarımcıda nasıl kullanıldıklarını açıklar. Bu özellikler özellikler kılavuzunda veya İş Akışı Tasarımcısı düzenlenebilir. Gereken tek özellik <xref:System.ServiceModel.Activities.Receive.OperationName%2A> özelliğidir.

| Özellik Adı | Gerekli | Kullanım |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | Yanlış | Etkinliğin kolay adını <xref:System.ServiceModel.Activities.Receive> belirtir. Varsayılan değer Alma'dır.<br /><br /> Kolay için varsayılan olmayan bir değerin kullanımı kesinlikle gerekli değildir, ancak böyle bir <xref:System.Activities.Activity.DisplayName%2A> değeri kullanmak en iyi uygulamadır. |
| <xref:System.ServiceModel.Activities.Receive.OperationName%2A> | Doğru | Bu etkinlik tarafından uygulanan hizmet işlemi adını <xref:System.ServiceModel.Activities.Receive> belirtir. Bu özellik, Action özelliği açıkça ayarlanmazsa **Action** özelliği **için** varsayılan değeri oluşturmak için kullanılır. |
| <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> | Yanlış | Hizmet sözleşmesinin adını belirtir. Bu özellik, hizmet işlemlerini tek tek hizmet sözleşmelerine grup etmek için kullanılır. Aynı <xref:System.ServiceModel.Activities.Receive> olan tüm etkinlikler aynı hizmet <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> sözleşmesine (WSDL Bağlantı Noktası Türü) gruplandı. Varsayılan değer, üst düzey (kök) etkinliğin tam CLR adıdır. |
| <xref:System.ServiceModel.Activities.Receive.Content%2A> | Yanlış | Alacak iletiyi veya parametre içeriğini belirtir. Bir etkinlik veya <xref:System.ServiceModel.Activities.ReceiveMessageContent> etkinlik <xref:System.ServiceModel.Activities.ReceiveParametersContent> olabilir. Özellik kılavuzunda İçerik alanı'nın yanındaki  üç nokta düğmesini seçerek veya Alma etkinliği tasarımcısı  yüzeyinde İçerik etiketinin yanındaki **Tanımla...** düğmesine tıklayarak bu özelliği düzenleyin.  Her ikisi de **İçerik Tanımı iletişim kutusunu** görüntüler. Bu kutunun kullanımı hakkında daha fazla bilgi için İçerik Tanımı [İletişim Kutusu konu başlığına](../workflow-designer/content-definition-dialog-box.md) bakın. |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> | Yanlış | Bir nesnesi olan bir iş <xref:System.ServiceModel.Activities.Receive> akışının hizmet işlemlerine yönelik etkinlikler arasındaki bağıntıları <xref:System.ServiceModel.MessageQuerySet> belirtir. Özellikler kılavuzunda özelliğin yanındaki üç nokta düğmesine tıklayarak <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> **CorrelatesOn Tanımı iletişim kutusunu** açın. Bu iletişim kutusunun kullanımı hakkında daha fazla bilgi için İçerik Tanımı [İletişim Kutusu konu başlığına](../workflow-designer/content-definition-dialog-box.md) bakın. |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> | Yanlış | İletiyi <xref:System.ServiceModel.Activities.CorrelationHandle> uygun iş akışı örneğine yönlendirmek için kullanılanı belirtir.<br /><br /> İfade Düzenleyicisi iletişim kutusunu açmak için <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> özellikler kılavuzunda özelliğin yanındaki üç **nokta düğmesine** tıklayın. Bu iletişim kutusunun kullanımı hakkında daha fazla bilgi için İfade [Düzenleyicisi'ni Kullanma konu başlığına](../workflow-designer/how-to-use-the-expression-editor.md) bakın. |
| <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> | Yanlış | bu etkinliği iş akışı <xref:System.ServiceModel.Activities.CorrelationInitializer> içinde yapılandıran <xref:System.ServiceModel.Activities.CorrelationHandle> birden çok nesne başlatan nesnelerin koleksiyonunu <xref:System.ServiceModel.Activities.Receive> belirtir. Özellikler kılavuzunda özelliğin yanındaki üç nokta düğmesine <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> tıklayarak Bağıntı **Başlatıcıları Ekle iletişim kutusunu** açın. Bu kutuyu kullanma hakkında daha fazla bilgi için [CorrelationInitializers Ekle İletişim Kutusu konu başlığına](../workflow-designer/add-correlationinitializers-dialog-box.md) bakın. |
| <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> | Yanlış | İletinin mevcut bir iş akışı örneğiyle ilişkili olmadığı durumlarda iletiyi işlemesi için yeni bir iş akışı örneğinin oluşturulıp oluşturulmay olmadığını belirleyen bir değer belirtir. Değer true olarak **ayarlanırsa,** ileti mevcut bir iş akışı örneğiyle ilişkili değilken iletiyi işlemesi için yeni bir iş akışı örneği oluşturulur. |
| <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> | Yanlış | Bu etkinlik tarafından uygulanan hizmet işlemi için bilinen türlerden bir koleksiyon <xref:System.ServiceModel.Activities.Receive> belirtir. Bu özellik, olarak ayarlanmış özelliğiyle <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> birlikte <xref:System.Runtime.Serialization.DataContractSerializer> kullanılmalıdır. Kullanılırsa <xref:System.Xml.Serialization.XmlSerializer> yoksayılır.<br /><br /> özellik kılavuzunda **KnownTypes** alanı yanındaki üç nokta düğmesini seçerek ilgili türleri **ekyebilirsiniz** Tür Koleksiyonu Düzenleyicisi iletişim kutusunu açın. Bu kutuyu kullanma hakkında daha fazla bilgi için Tür [Koleksiyonu Düzenleyicisi İletişim Kutusu konu başlığına](../workflow-designer/type-collection-editor-dialog-box.md) bakın. |
| <xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A> | Yanlış | İleti <xref:System.Net.Security.ProtectionLevel> için belirtir.<br /><br /> 1.  <xref:System.Net.Security.ProtectionLevel> Yalnızca kimlik doğrulaması anlamına gelir.<br />2.  <xref:System.Net.Security.ProtectionLevel> aktarılan verilerin bütünlüğünü sağlamaya yardımcı olmak için veri imzalama anlamına gelir.<br />3.  <xref:System.Net.Security.ProtectionLevel> aktarılan verilerin gizliliğini ve bütünlüğünü sağlamaya yardımcı olmak için verileri şifreleme ve imzalama anlamına gelir. |
| <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> | Yanlış | Etkinlik tarafından uygulanan hizmet işlemi için kullanmak seri hale getirici türünü <xref:System.ServiceModel.Activities.Receive> belirtir. Varsayılan değer, bir türün örneğini verilen veri sözleşmesini kullanan bir XML akışında veya belgede seri hale getiren ve seri durumdan alan <xref:System.Runtime.Serialization.DataContractSerializer> değeridir. <xref:System.Xml.Serialization.XmlSerializer>, XML üzerinde daha fazla denetim gerektiğinde de kullanılabilir. |
| <xref:System.ServiceModel.Activities.Receive.Action%2A> | Yanlış | İletinin eylem üst bilgilerini belirtir. Açıkça ayarlanmaması, değerinin varsayılan değeri: `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` . |

## <a name="see-also"></a>Ayrıca bkz.

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Gönder](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)
