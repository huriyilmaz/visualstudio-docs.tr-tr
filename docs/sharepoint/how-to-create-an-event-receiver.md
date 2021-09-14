---
title: 'Nasıl: Olay Alıcısı Oluşturma | Microsoft Docs'
description: Bir kullanıcı listeler veya liste öğeleri gibi öğelerle etkileşim kurduğunda yanıt ver SharePoint bir olay alıcısı oluşturun.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.SPE.EventReceiver
dev_langs:
- VB
- CSharp
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
ms.openlocfilehash: 66b62a619b64534f56039e6213b01d4d12bb941a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636926"
---
# <a name="how-to-create-an-event-receiver"></a>Nasıl: Olay alıcısı oluşturma
  Olay alıcıları *oluşturarak,* bir kullanıcı listeler veya liste öğeleri gibi SharePoint ile etkileşim kurduğunda yanıt veabilirsiniz. Örneğin, bir kullanıcı takvimi değiştirirken veya kişi listesinden bir ad slendiğinde olay alıcısındaki kod tetiklenir. Bu konuyu takip etmek için bir liste örneğine olay alıcısı ekleme hakkında bilgi öğrenebilirsiniz.

 Bu adımları tamamlamak için, Windows ve [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint'nin yüklü ve desteklenen sürümlerine sahip SharePoint. Bu örnek bir SharePoint projesi gerektirdiği için, Adım adım kılavuz: Site sütunu, içerik türü ve SharePoint için liste oluşturma konu başlığında yer alan [yordamı tamamlamış SharePoint.](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)

## <a name="adding-an-event-receiver"></a>Olay alıcısı ekleme
 Adım adım kılavuz: Site [sütunu,](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) içerik türü ve liste oluşturma içinde oluşturduğunuz proje SharePoint özel site sütunları, özel bir liste ve bir içerik türü içerir. Aşağıdaki yordamda, listeler gibi öğelerde oluşan olayları işlemeyi göstermek için bir liste örneğine basit bir olay işleyicisi (olay alıcısı) ekleyerek bu SharePoint genişleteceğiz.

#### <a name="to-add-an-event-receiver-to-the-list-instance"></a>Liste örneğine olay alıcısı eklemek için

1. Adım adım kılavuz: Site sütunu, içerik türü ve site listesi oluşturma içinde oluşturduğunuz [projeyi SharePoint.](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)

2. Bu **Çözüm Gezgini**, SharePoint proje düğümünü **seçin.**

3. Menü çubuğunda Yeni Öğe **Ekle'Project**  >  **seçin.**

4. Visual **C# veya** **Visual Basic** altında, SharePoint **düğümünü** genişletin ve ardından **2010 öğesini** seçin.

5. Şablonlar **bölmesinde Olay** Alıcısı'ı **seçin,** **TestEventReceiver1** olarak ad girin ve ardından Tamam **düğmesini** seçin.

     SharePoint **Özelleştirme Sihirbazı** görüntülenir.

6. Ne **tür bir olay alıcısı istiyor musunuz? listesinde** Öğe Olaylarını **Listele'yi seçin.**

7. Olay **kaynağı hangi öğe olmalı? listesinde Patients** **(Clinic\Patients) öğesini seçin.**

8. Aşağıdaki **olayları işle listesinde** Öğe eklendi seçeneğinin yanındaki onay kutusunu **işaretleyin** ve ardından Son **düğmesini** seçin.

     Yeni olay alıcısının kod dosyası adlı tek bir yöntem `ItemAdded` içerir. Bir sonraki adımda, bu yönteme kod ekerek her kişinin varsayılan olarak Scott Brown olarak adlandırılmış olması için bu yöntemi ekleyebilirsiniz.

9. Mevcut yöntemi `ItemAdded` aşağıdaki kodla değiştirin ve **F5 anahtarını** seçin:

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/CustomField1/TestEventReceiver1/TestEventReceiver1.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/CustomField1_VB/EventReceiver1/EventReceiver1.vb" id="Snippet1":::

     Kod çalışır ve SharePoint sitesi web tarayıcısında görünür.

10. QuickLaunch çubuğunda Patients (Hastalar) **bağlantısını** ve ardından **Add New Item (Yeni** Öğe Ekle) bağlantısını seçin.

     Yeni öğeler için giriş formu açılır.

11. Alanlara veri girin ve kaydet **düğmesini** seçin.

     Kaydet düğmesini **seçtikten** sonra Patient **Name** sütunu otomatik olarak Scott Brown adıyla lenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Yeni SharePoint geliştirme](../sharepoint/developing-sharepoint-solutions.md)