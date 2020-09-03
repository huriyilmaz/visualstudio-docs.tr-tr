---
title: 'Nasıl yapılır: Windows Communication Foundation sözleşmesi Işlemini uygulama (eski) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1f6f54e781dfae15b4b1c1159d73ac3495b35c21
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72603872"
---
# <a name="how-to-implement-a-windows-communication-foundation-contract-operation-legacy"></a>Nasıl Yapılır: Windows Communication Foundation Sözleşme İşlemi Uygulama (Eski)
Bu konu, veya ' i hedefleyen bir sözleşme işleminin nasıl uygulanacağını açıklar [!INCLUDE[indigo1](../includes/indigo1-md.md)] [!INCLUDE[wfd1](../includes/wfd1-md.md)] [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 Araç kutusundan bir **ReceiveActivity** etkinliğini iş akışı tasarım yüzeyine sürükledikten sonra, yeni bir [!INCLUDE[indigo2](../includes/indigo2-md.md)] sözleşme oluşturacaksınız veya var olan bir sözleşmeyi içeri aktarıp işlemleri uygulayacaksınız. [Işlem Seç Iletişim kutusu (eski)](../workflow-designer/choose-operation-dialog-box-legacy.md)aracılığıyla sözleşmenizi ve/veya işlemlerini seçin ve/veya oluşturabilirsiniz.

### <a name="to-implement-a-wcf-contract-operation"></a>Bir WCF sözleşme işlemi uygulamak için

1. Tasarımcıda **ReceiveActivity** etkinliğine çift tıklayın veya **Özellikler** bölmesinde **ServiceOperationInfo** özelliğinin yanındaki üç noktaya tıklayın.

2. Şunlardan birini yapın:

   - İletişim kutusunun sağ üst köşesindeki **sözleşme Ekle** ' ye tıklayın. Bu, [!INCLUDE[indigo2](../includes/indigo2-md.md)] sizin için yeni bir sözleşme ve işlem oluşturur.

      -veya-

   - İletişim kutusunun sağ üst köşesindeki **Içeri aktar** ' a tıklayın. [Bir .NET türü görüntüle ve Seç Iletişim kutusu (eski)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) açılır. İstediğiniz sözleşmeyi içeren bir derleme veya proje arayın. Sözleşmeyi seçip **Tamam**' a tıklayın.

     Bir sözleşme oluşturulduktan veya alındıktan sonra, oluşturulan veya içeri aktarılan sözleşmeye yeni işlemler ekleyebilirsiniz. Yeni bir işlem eklemek için sözleşmeyi seçin ve iletişim kutusunun sağ üst köşesindeki **Işlem Ekle** ' ye tıklayın. İşlem ekleme işlemini tamamladığınızda adım 3 ' e geçin.

3. **ReceiveActivity** etkinliğiyle ilişkilendirmek istediğiniz işlemi seçin. İşlemin tanımını, işlemin adını, parametrelerini, özelliklerini ve izin ayarlarını değiştirerek düzenleyebilirsiniz.

    Adı değiştirmek için, **Işlem adı** metin kutusuna yeni adı girin.

    İşlem parametrelerine erişmek için **Parametreler** sekmesine tıklayın. Bir parametrenin adını, türünü veya yönünü değiştirebilir ve işlemden parametre ekleyebilir veya silebilirsiniz.

    İşlem koruma düzeyi ve işlemin desteklenen ileti değişimi işlevselliğine erişmek için **Özellikler** sekmesine tıklayın.

    Hangi grubun işlemi uygulamasına izin verildiğini belirtmek için **izinler** sekmesine tıklayın.

4. **Tamam** ' a tıkladığınızda, **ReceiveActivity** etkinliğinde uyguladığı işlem için işlem adı görüntülenir.

5. Bu işlemin uygulanması için kullanacağınız iş akışı etkinliklerini **ReceiveActivity** etkinliği içinde yerleştirin.

## <a name="see-also"></a>Ayrıca Bkz.
 [Işlem Seç Iletişim kutusu (eski)](../workflow-designer/choose-operation-dialog-box-legacy.md) [nasıl yapılır: WCF sözleşme işlemi (eski)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md) [eski iş akışı etkinliklerini](../workflow-designer/legacy-workflow-activities.md) çağırma