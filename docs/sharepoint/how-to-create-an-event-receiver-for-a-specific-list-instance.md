---
title: 'Nasıl: Belirli bir Liste Örneği Örneği için Olay Alıcısı Oluşturma | Microsoft Docs'
titleSuffix: ''
description: Belirli bir liste örneği için olay alıcısı oluşturun. Liste örneği olay alıcısı, liste tanımının herhangi bir örneğinde oluşan olaylara yanıt verir.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, event receivers
- event receivers [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 815cb4a46141ddc5f6e85fefe4ff71a53cd473e958ffaa5c2779e99355aca6cf
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121228564"
---
# <a name="how-to-create-an-event-receiver-for-a-specific-list-instance"></a>Nasıl ekleyebilirsiniz: Belirli bir liste örneği için olay alıcısı oluşturma
  Liste örneği olay alıcısı, liste tanımının herhangi bir örneğinde oluşan olaylara yanıt verir. Olay alıcı şablonu belirli bir liste örneğinin hedefini etkinleştirmese de, belirli bir liste örneğinde olaylara yanıt vermek için bir liste tanımı kapsamına sahip olay alıcısını değiştirebilirsiniz.

 Belirli bir liste örneğini hedeflemek *için* Elements.xmlalıcısının url'sini ile değiştirin ve `ListTemplateId` liste `ListUrl` örneğinin URL'sini ekleyin.

## <a name="create-a-list-instance-event-receiver"></a>Liste örneği olay alıcısı oluşturma
 Aşağıdaki adımlarda, bir liste öğesi olay alıcısının yalnızca özel bir duyurular-liste örneğinde oluşan olaylara yanıt vermek üzere nasıl değiştirnerek değiştirilebilecekleri açıktır.

#### <a name="to-modify-an-event-receiver-to-respond-to-a-specific-list-instance"></a>Bir olay alıcısını belirli bir liste örneğine yanıt vermek için değiştirmek için

1. Tarayıcıda SharePoint açın.

2. Gezinti bölmesinde Listeler **bağlantısı.**

3. Tüm **Site İçeriği sayfasında** Oluştur **bağlantısını** seçin.

4. Oluştur **iletişim** kutusunda Duyurular türünü **seçin,** duyuruya **TestAnnouncements adını ve** ardından Oluştur **düğmesini** seçin.

5. içinde, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] bir olay alıcı projesi oluşturun.

6. Ne **tür bir olay alıcısı istiyor musunuz? listesinde** Öğe Olaylarını **Listele'yi seçin.**

    > [!NOTE]
    > Bir liste tanımına kapsamı olan başka bir olay alıcısı türü de seçebilirsiniz; örneğin, E-posta **Olaylarını Listele** veya İş **Akışı Olaylarını Listele.**

7. Olay **kaynağı hangi öğe olmalı? listesinde Duyurular'ı** **seçin.**

8. Aşağıdaki **olayları işle listesinde** Bir öğe **ekleniyor** onay kutusunu ve ardından Son **düğmesini** seçin.

9. Bu **Çözüm Gezgini,** EventReceiver1 altında *Elements.xml.*

     Olay alıcısı şu anda aşağıdaki satırı kullanarak Duyurular liste tanımına başvurur:

    ```xml
    <Receivers ListTemplateId="104">
    ```

     Bu satırı aşağıdaki metinle değiştirebilirsiniz:

    ```xml
    <Receivers ListUrl="Lists/TestAnnouncements">
    ```

     Bu, olay alıcısını yalnızca az önce oluşturduğunuz **yeni TestAnnouncements** duyuruları listesinde oluşan olaylara yanıt vermeye yönlendirer. özniteliğini, `ListURL` SharePoint sunucusundaki herhangi bir liste örneğine başvurarak değiştirebilirsiniz.

10. Olay alıcısının kod dosyasını açın ve ItemAdding yöntemine bir kesme noktası girin.

11. Çözümü **derlemek ve** çalıştırmak için F5 anahtarını seçin.

12. Bu SharePoint gezinti bölmesinde **TestAnnouncements** bağlantısını seçin.

13. Yeni duyuru **ekle bağlantısını** seçin.

14. Duyuru için bir başlık girin ve kaydet **düğmesini** seçin.

     Özel duyurular listesine yeni öğe eklenmiştir.

15. Devam etmek **için F5** tuşuna basın.

16. Gezinti bölmesinde Listeler bağlantısını **ve** ardından Duyurular **bağlantısını** seçin.

17. Yeni bir duyuru ekleyin.

     Alıcı yalnızca **TestAnnouncements** özel duyuru listesi örneğinde olaylara yanıt vermek üzere yapılandırıldığından, olay alıcısının yeni duyuruda tetiklenene bir şey olmadığını fark etmek.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl: Olay alıcısı oluşturma](../sharepoint/how-to-create-an-event-receiver.md)
- [Yeni SharePoint geliştirme](../sharepoint/developing-sharepoint-solutions.md)
