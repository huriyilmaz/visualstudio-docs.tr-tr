---
title: 'Nasıl yapılır: bir Iş akışı projesine yeni öğe ekleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 004f079576b792fb76d596ee8ebac3f6f96f316e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656628"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Nasıl yapılır: bir Iş akışı projesine yeni öğe ekleme
Bir iş akışı projesi oluşturduktan sonra, iş akışı etkinliklerini, tasarımcıları ve diğer tanıdık [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] öğelerini projenize ekleyebilirsiniz.

 Aşağıdaki tabloda, bir iş akışı projesine ekleyebileceğiniz [!INCLUDE[wf](../includes/wf-md.md)] öğeleri listelenmektedir.

|Name|Açıklama|
|----------|-----------------|
|Etkinlik|Diğer etkinliklerden oluşan etkinlik. Bu öğenin seçilmesi, yeni bir proje için **etkinlik kitaplığı** şablonunu seçerken elde ettiğiniz xaml dosyasını projeye ekler. Bu yordamda [!INCLUDE[crabout](../includes/crabout-md.md)] bkz. [nasıl yapılır: etkinlik kitaplığı oluşturma](../workflow-designer/how-to-create-an-activity-library.md).|
|Etkinlik Tasarımcısı|Bir etkinliğin tasarım zamanı deneyimini özelleştirmek için bir tasarımcı. Bu öğe seçildiğinde, yeni bir proje için **etkinlik Tasarımcısı kitaplık** şablonunu seçerken elde ettiğiniz dosyalar projeye eklenir. Bu yordamda [!INCLUDE[crabout](../includes/crabout-md.md)] bkz. [nasıl yapılır: etkinlik Tasarımcısı kitaplığı oluşturma](../workflow-designer/how-to-create-an-activity-designer-library.md).|
|Kod etkinliği|Yürütme mantığı kod olarak yazılmış bir etkinlik. @No__t_0 yöntemi geçersiz kılmasına sahip bir kaynak kodu dosyası sizin için zaten oluşturulmuştur.|
|WCF Iş akışı hizmeti|İş akışı etkinlikleri kullanılarak oluşturulan bir [!INCLUDE[indigo2](../includes/indigo2-md.md)] hizmeti. Bu öğe seçildiğinde, yeni bir proje için **WCF Iş akışı hizmeti uygulama** şablonunu seçerken elde ettiğiniz dosyalar projeye eklenir. Bu yordamda [!INCLUDE[crabout](../includes/crabout-md.md)] bkz. [nasıl yapılır: WCF Iş akışı hizmeti uygulaması oluşturma](../workflow-designer/how-to-create-a-wcf-workflow-service-application.md).|

### <a name="to-add-a-new-item-to-a-workflow-project"></a>Bir iş akışı projesine yeni bir öğe eklemek için

1. **Proje** menüsünde **Yeni öğe Ekle... öğesine**tıklayın.

     **Yeni öğe Ekle** iletişim kutusu açılır.

2. **Yüklü şablonlar** bölmesinde **iş akışı** grubu ' nu seçin.

3. Dört öğeden birini seçin. Önceki tabloda kullanılabilen seçimler listelenmektedir.

4. İletişim kutusunun alt kısmındaki **ad** kutusuna öğe için uygun bir ad yazın.

5. Öğeyi geçerli iş akışı projesine eklemek için **Ekle** ' ye tıklayın.

## <a name="see-also"></a>Ayrıca Bkz.
 [İş Akışı Projesi Oluşturma](../workflow-designer/creating-a-workflow-project.md)