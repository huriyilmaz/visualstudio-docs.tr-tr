---
title: ReceiveAndSendReply Şablon Tasarımcısı
description: Önceden yapılandırılmış Receive ve SendReply etkinliklerinden bir çifti oluşturmak için İş Akışı Tasarımcısı'da ReceiveAndSendReply şablonunu kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: ba89478dcbc69104c89788708afe32e338ef7071
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135305"
---
# <a name="receiveandsendreply-template-designer"></a>ReceiveAndSendReply Şablon Tasarımcısı

**ReceiveAndSendReply** şablonu, önceden yapılandırılmış ve etkinlik çifti oluşturmak <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> için kullanılır. Etkinlikler bir etkinliğin parçasıdır ve sunucuda istek/yanıt iletisi değişim deseninin bir <xref:System.Activities.Statements.Sequence> parçası olarak ilişkilidir.

## <a name="the-receiveandsendreply-template"></a>ReceiveAndSendReply şablonu

**ReceiveAndSendReply şablonu** eklemek, etkinlikle ve etkinlikleri <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> oluşturmanın yanı sıra üç şey <xref:System.Activities.Statements.Sequence> yapar:

- Etkinliğin <xref:System.ServiceModel.Activities.Receive.OperationName%2A> ve <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> özelliklerini <xref:System.ServiceModel.Activities.Receive> yapılandırıyor.

- Etkinliğin <xref:System.ServiceModel.Activities.SendReply.Request%2A> özelliğini <xref:System.ServiceModel.Activities.Receive> etkinliğine <xref:System.ServiceModel.Activities.Send> bağlar.

- Üst <xref:System.ServiceModel.Activities.CorrelationHandle> etkinlikte değişken olarak bir oluşturur.

### <a name="use-the-receiveandsendreply-template-designer"></a>ReceiveAndSendReply şablon tasarımcısını kullanma

Araç Kutusunun **Mesajlaşma kategorisindeki ReceiveAndSendReply** **etkinlik** **tasarımcısına erişin.** **ReceiveAndSendReply** etkinlik **tasarımcısı, Etkinlikler** genellikle yerleştirildikten sonra Araç Kutusundan sürükleyip İş Akışı Tasarımcısı yüzeyine bırakılır. Etkinlik tasarımcısı bırakıldığında, Etkinlik gönder tasarımcısıyla yapılandırılan ve <xref:System.ServiceModel.Activities.Receive>  SendReplyToReceive tasarımcısıyla yapılandırılan bir <xref:System.ServiceModel.Activities.SendReply> ilişkili etkinlik oluşturur.

Etkinliği yapılandırmak için Alma tasarımcısını **kullanma hakkında** daha fazla bilgi <xref:System.ServiceModel.Activities.Receive> için bkz. Receive Activity [Designer](../workflow-designer/receive-activity-designer.md).

### <a name="properties-of-sendreply"></a>SendReply Özellikleri

Aşağıdaki tablo, <xref:System.ServiceModel.Activities.SendReply> özellikleri gösterir ve tasarımcıda nasıl kullanıldıklarını açıklar. Bu özellikler özellikler kılavuzunda düzenlenebilir ve bazıları da İş Akışı Tasarımcısı düzenlenebilir.

| Özellik Adı | Gerekli | Kullanım |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | Yanlış | Etkinliğin isteğe bağlı kolay <xref:System.ServiceModel.Activities.SendReply> adı. Varsayılan değer SendReplyToReceive'dır.<br /><br /> Kolay için varsayılan olmayan bir değerin kullanımı kesinlikle gerekli değildir, ancak böyle bir değer <xref:System.Activities.Activity.DisplayName%2A> kullanmak en iyisidir. |
| <xref:System.ServiceModel.Activities.SendReply.Request%2A> | Doğru | Bu <xref:System.ServiceModel.Activities.Receive> etkinlikle eşleştirilmiş etkinlik <xref:System.ServiceModel.Activities.SendReply> başvurusu. Bu özellik **null olmamalıdır.** <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> etkinlikleri, bir istek/yanıt mesajlaşma düzeni modellemek için sunucuda birlikte kullanılır. Bu özellik hangi <xref:System.ServiceModel.Activities.Send> etkinliğin eşleştirilmiş olduğunu belirtir. Tasarımcıda bu özelliği düzenleyemezsiniz çünkü bu özellik, etkinliği oluşturduğunuz <xref:System.ServiceModel.Activities.Send> etkinliğin otomatik olarak bağlı <xref:System.ServiceModel.Activities.SendReply> olmasıdır. |
| <xref:System.ServiceModel.Activities.SendReply.Content%2A> | Yanlış | Alacak iletiyi veya parametre içeriğini belirtir. Bir etkinlik veya <xref:System.ServiceModel.Activities.ReceiveMessageContent> etkinlik <xref:System.ServiceModel.Activities.ReceiveParametersContent> olabilir. Özellik kılavuzunda İçerik alanı'nın yanındaki üç nokta düğmesine tıklayarak veya  Alma etkinliği tasarımcısının yüzeyinde  İçerik etiketinin yanındaki Tanımla düğmesine tıklayarak bu özelliği düzenleyin.   Her ikisi de **İçerik Tanımı iletişim kutusunu** görüntüler. Bu kutunun kullanımı hakkında daha fazla bilgi için İçerik Tanımı [İletişim Kutusu konu başlığına](../workflow-designer/content-definition-dialog-box.md) bakın. |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> | Yanlış | bu etkinliği iş akışı <xref:System.ServiceModel.Activities.CorrelationInitializer> içinde yapılandıran <xref:System.ServiceModel.Activities.CorrelationHandle> birden çok nesne başlatan nesnelerin koleksiyonunu <xref:System.ServiceModel.Activities.Receive> belirtir. Özellikler kılavuzunda özelliğin yanındaki üç nokta düğmesine <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> tıklayarak Bağıntı **Başlatıcıları Ekle iletişim kutusunu** açın. Bu kutuyu kullanma hakkında daha fazla bilgi için [CorrelationInitializers Ekle İletişim Kutusu konu başlığına](../workflow-designer/add-correlationinitializers-dialog-box.md) bakın. |
| <xref:System.ServiceModel.Activities.SendReply.Action%2A> | Yanlış | İletinin eylem üst bilgilerini belirtir. Açıkça ayarlanmazsa, değeri varsayılan olarak şöyle olur:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` |
| <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A> | Yanlış | Yanıt iletisi gönderilmeden önce iş akışı örneğinin kalıcı olup olmadığını belirtir. Varsayılan değer **false** şeklindedir. |

## <a name="see-also"></a>Ayrıca bkz.

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Al](../workflow-designer/receive-activity-designer.md)
- [Gönder](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)