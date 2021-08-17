---
title: SendAndReceiveReply Şablon Tasarımcısı
description: Önceden yapılandırılmış Bir çift Gönderme ve AlmaReply etkinlikleri oluşturmak için İş Akışı Tasarımcısı'da SendAndReceiveReply şablonunu nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: b39383e23f917f3f19c590e20f96dcdf8d611239ed6b1477aee4cd93bbcb12e9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121440428"
---
# <a name="sendandreceivereply-template-designer"></a>SendAndReceiveReply Şablon Tasarımcısı

**SendAndReceiveReply** şablonu, önceden yapılandırılmış ve etkinlik çifti oluşturmak <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> için kullanılır. Etkinlikler bir etkinliğin <xref:System.Activities.Statements.Sequence> parçasıdır ve istemcide istek/yanıt iletisi değişim deseninin bir parçası olarak ilişkilidir.

## <a name="the-sendandreceivereply-template"></a>SendAndReceiveReply şablonu

**SendAndReceiveReply** şablonunu eklemek, etkinlik içinde ve etkinliklerini <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> oluşturmanın yanı sıra üç şey <xref:System.Activities.Statements.Sequence> yapar:

- Etkinliğin <xref:System.ServiceModel.Activities.Send.OperationName%2A> ve <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> özelliklerini <xref:System.ServiceModel.Activities.Send> yapılandırıyor.

- Etkinliğin <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> özelliğini <xref:System.ServiceModel.Activities.ReceiveReply> etkinliğine <xref:System.ServiceModel.Activities.Send> bağlar.

- Üst <xref:System.ServiceModel.Activities.CorrelationHandle> etkinlikte değişken olarak bir oluşturur.

### <a name="use-the-sendandreceivereply-template-designer"></a>SendAndReceiveReply Şablon Tasarımcısını Kullanma

Araç Kutusunun **Mesajlaşma kategorisindeki SendAndReceiveReply** **etkinlik** **tasarımcısına erişin.** **SendAndReceiveReply** etkinlik **tasarımcısı, Etkinlikler** genellikle yerleştirildikten sonra Araç Kutusundan sürükleyip İş Akışı Tasarımcısı yüzeyine bırakılır. Etkinlik tasarımcısı bırakıldığında, Etkinlik gönder tasarımcısıyla yapılandırılan ve <xref:System.ServiceModel.Activities.Send>  <xref:System.ServiceModel.Activities.ReceiveReply> **ReceiveReplyForSend** tasarımcısıyla yapılandırılan bir ilişkili etkinlik oluşturur.

Etkinliği yapılandırmak için Gönder **tasarımcısını kullanma hakkında** daha fazla bilgi <xref:System.ServiceModel.Activities.Send> için bkz. [Gönder.](../workflow-designer/send-activity-designer.md)

### <a name="properties-of-receivereply"></a>ReceiveReply Özellikleri

Aşağıdaki tabloda özellikler <xref:System.ServiceModel.Activities.ReceiveReply> ve bunların tasarımcıda nasıl kullanıldıkları açık bulunmaktadır. Bu özellikler özellikler kılavuzunda düzenlenebilir ve bazıları da İş Akışı Tasarımcısı düzenlenebilir.

| Özellik Adı | Gerekli | Kullanım |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | Yanlış | Etkinliğin isteğe bağlı kolay <xref:System.ServiceModel.Activities.ReceiveReply> adı. Varsayılan değer ReceiveReplyForSend'tir.<br /><br /> Kolay için varsayılan olmayan bir değerin kullanımı kesinlikle gerekli değildir, ancak böyle bir değer <xref:System.Activities.Activity.DisplayName%2A> kullanmak en iyisidir. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | Doğru | Bu <xref:System.ServiceModel.Activities.Send> etkinlikle eşleştirilmiş etkinlik <xref:System.ServiceModel.Activities.ReceiveReply> başvurusu. Bu özellik **null olmamalıdır.** <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikleri, istek/yanıt mesajlaşma desenini modellemek için istemcide birlikte kullanılır. Bu özellik hangi <xref:System.ServiceModel.Activities.Send> etkinliğin eşleştirilmiş olduğunu belirtir. Tasarımcıda bu özelliği düzenleyemezsiniz çünkü bu özellik, etkinliği oluşturduğunuz <xref:System.ServiceModel.Activities.Send> etkinliğin otomatik olarak bağlı <xref:System.ServiceModel.Activities.ReceiveReply> olmasıdır. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | Yanlış | Alacak iletiyi veya parametre içeriğini belirtir. Bir etkinlik veya <xref:System.ServiceModel.Activities.ReceiveMessageContent> etkinlik <xref:System.ServiceModel.Activities.ReceiveParametersContent> olabilir. Özellik kılavuzunda İçerik alanı'nın yanındaki  üç nokta düğmesine tıklayarak veya Alma etkinliği tasarımcısının  yüzeyinde İçerik  etiketinin yanındaki Tanımla düğmesine tıklayarak bu özelliği düzenleyin.  Her ikisi de **İçerik Tanımı iletişim kutusunu** görüntüler. Bu kutunun kullanımı hakkında daha fazla bilgi için bkz. [İçerik Tanımı İletişim Kutusu.](../workflow-designer/content-definition-dialog-box.md) |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | Yanlış | bu etkinliği iş akışı <xref:System.ServiceModel.Activities.CorrelationInitializer> içinde yapılandıran <xref:System.ServiceModel.Activities.CorrelationHandle> birden çok nesne başlatan nesnelerin koleksiyonunu <xref:System.ServiceModel.Activities.Receive> belirtir. Özellikler kılavuzunda özelliğin yanındaki üç nokta düğmesine <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> tıklayarak Bağıntı **Başlatıcıları Ekle iletişim kutusunu** açın. Bu kutuyu kullanma hakkında daha fazla bilgi için, [bkz. Add CorrelationInitializers Dialog Box](../workflow-designer/add-correlationinitializers-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | Yanlış | İletinin eylem üst bilgilerini belirtir. Açıkça ayarlanmazsa, değeri varsayılan olarak şöyle olur:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`. |

## <a name="see-also"></a>Ayrıca bkz.

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Al](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Gönder](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)