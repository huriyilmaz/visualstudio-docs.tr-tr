---
title: 'Nasıl yapılır: Windows Communication Foundation sözleşmesi Işlemini çağırma (eski) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6f42600a739561a27a6dd8f6caa237027bac4554
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72603698"
---
# <a name="how-to-invoke-a-windows-communication-foundation-contract-operation-legacy"></a>Nasıl Yapılır: Windows Communication Foundation Sözleşme İşlemi Çağırma (Eski)
Bu konu, veya ' i hedefleyen bir sözleşme işleminin nasıl çağırılacağını açıklar [!INCLUDE[indigo1](../includes/indigo1-md.md)] [!INCLUDE[wfd1](../includes/wfd1-md.md)] [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 Araç kutusundan bir **SendActivity** etkinliğini iş akışı tasarım yüzeyine sürükledikten sonra, var olan bir sözleşmeyi içeri aktarmanız ve bu **SendActivity** etkinliğinden hangi işlemin çağrılacağını belirlemelisiniz. [Işlem Seç Iletişim kutusu (eski)](../workflow-designer/choose-operation-dialog-box-legacy.md)aracılığıyla sözleşmenizi ve işlemlerini seçersiniz.

 Ayrıca, hizmetinize sahip bir yapılandırma dosyası kullanıyorsanız, bir belirtmeniz gerekir <xref:System.Workflow.Activities.ChannelToken> . , <xref:System.Workflow.Activities.ChannelToken> Gönderme etkinliğinizin iş akışı hizmetine bağlanmak için kullanacağı uç nokta yapılandırmasını tanımlar.

### <a name="to-invoke-a-wcf-contract-operation-from-a-sendactivity-activity"></a>Bir SendActivity etkinliğinden WCF sözleşme işlemini çağırmak için

1. Tasarımcıda **SendActivity** etkinliğine çift tıklayın veya **Özellikler** bölmesinde **ServiceOperationInfo** özelliğinin yanındaki üç noktaya tıklayın.

2. **Işlem Seç** iletişim kutusu açıldığında, iletişim kutusunun sağ üst köşesindeki **içeri aktar** ' a tıklayın.

     [Bir .NET türü görüntüle ve Seç Iletişim kutusu (eski)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) açılır.

3. İstediğiniz sözleşmeyi içeren bir derleme veya proje arayın.

4. Sözleşmeyi seçip **Tamam**' a tıklayın.

5. **Kullanılabilir işlemler**altında çağırmak istediğiniz işlemi seçin ve **Tamam**' a tıklayın.

### <a name="to-specify-a-channel-token"></a>Bir kanal belirteci belirtmek için

1. <xref:System.Workflow.Activities.SendActivity>Tasarımcıda etkinliği seçin.

2. **Özellikler** bölmesinde, için bir ad belirtin <xref:System.Workflow.Activities.ChannelToken> . Bu ad, kanal belirtecini benzersiz şekilde tanımlar.

3. Kanal belirteci düğümünü genişletin ve alanda kullanacağınız istemci uç noktası için bir ad belirtin <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A> . Yapılandırma dosyasındaki aynı adın uç nokta yapılandırması, kanalı yapılandırmak için kullanılacaktır.

4. Zaten mevcut değilse, yapılandırma dosyanızda uç nokta yapılandırmasını oluşturun. İstemcinizi yapılandırma hakkında daha fazla bilgi için bkz. [WCF Istemcisine genel bakış](https://msdn.microsoft.com/library/f60d9bc5-8ade-4471-8ecf-5a07a936c82d).

## <a name="see-also"></a>Ayrıca Bkz.
 [Işlem Seç Iletişim kutusu (eski)](../workflow-designer/choose-operation-dialog-box-legacy.md) [nasıl yapılır: WCF sözleşme işlemi (eski)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) [eski iş akışı etkinliklerini](../workflow-designer/legacy-workflow-activities.md) uygulama