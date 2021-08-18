---
title: 'Nasıl yapılır: olay alıcısı oluşturma | Microsoft Docs'
description: bir kullanıcı listeler veya liste öğeleri gibi SharePoint öğelerle etkileşime geçtiğinde yanıt verebilmeniz için bir olay alıcısı oluşturun.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148954"
---
# <a name="how-to-create-an-event-receiver"></a>Nasıl yapılır: olay alıcısı oluşturma
  *olay alıcıları* oluşturarak, bir kullanıcı listeler veya liste öğeleri gibi SharePoint öğelerle etkileşime geçtiğinde yanıt verebilirsiniz. Örneğin, bir kullanıcı takvimi değiştirdiğinde veya bir kişi listesinden bir adı silerse bir olay alıcısındaki kod tetiklenebilir. Bu konuyu izleyerek bir liste örneğine bir olay alıcısının nasıl ekleneceğini öğrenebilirsiniz.

 bu adımları tamamlayabilmeniz için, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Windows ve SharePoint 'ın yüklü ve desteklenen sürümlerini yüklemiş olmanız gerekir. bu örnek bir SharePoint projesi gerektirdiğinden, [izlenecek yol: bir site sütunu, içerik türü ve SharePoint listesi oluşturma](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)konusunun yordamını tamamlamış olmanız gerekir.

## <a name="adding-an-event-receiver"></a>Olay alıcısı ekleme
 [izlenecek yol: bir site sütunu, içerik türü ve SharePoint liste oluşturma](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) bölümünde oluşturduğunuz proje, özel site sütunları, özel bir liste ve içerik türü içerir. aşağıdaki yordamda, listeler gibi SharePoint öğelerde oluşan olayların nasıl işleneceğini göstermek için bir liste örneğine basit bir olay işleyicisi (bir olay alıcısı) ekleyerek bu projeyi genişlettireceksiniz.

#### <a name="to-add-an-event-receiver-to-the-list-instance"></a>Liste örneğine bir olay alıcısı eklemek için

1. [Izlenecek yol: bir site sütunu, içerik türü ve SharePoint için liste oluşturma](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)bölümünde oluşturduğunuz projeyi açın.

2. **Çözüm Gezgini**' de, **Clinic** adlı SharePoint projesi düğümünü seçin.

3. menü çubuğunda **Project**  >  **yeni öğe ekle**' yi seçin.

4. **Visual C#** veya **Visual Basic** altında **SharePoint** düğümünü genişletin ve ardından **2010** öğesini seçin.

5. **Şablonlar** bölmesinde **olay alıcısı**' nı seçin, **TestEventReceiver1** olarak adlandırın ve **Tamam** düğmesini seçin.

     **SharePoint özelleştirme sihirbazı** görüntülenir.

6. **Ne tür bir olay alıcısı istiyorsunuz?** listesinde, **liste öğesi olayları**' nı seçin.

7. **Hangi öğe olay kaynağı olmalıdır?** listesinde, **hastalar (klinic\hastalar)** öğesini seçin.

8. **Aşağıdaki olayları işle** listesinde, **öğe eklenmiş** seçeneğinin yanındaki onay kutusunu işaretleyin ve ardından **son** düğmesini seçin.

     Yeni olay alıcısının kod dosyası, adlı tek bir yöntem içerir `ItemAdded` . Sonraki adımda, bu yönteme kod ekleyeceksiniz, böylece her kişi varsayılan olarak Scott kahverengi olarak adlandırılır.

9. Mevcut `ItemAdded` yöntemi aşağıdaki kodla değiştirin ve **F5** tuşunu seçin:

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/CustomField1/TestEventReceiver1/TestEventReceiver1.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/CustomField1_VB/EventReceiver1/EventReceiver1.vb" id="Snippet1":::

     kod çalışır ve SharePoint sitesi web tarayıcısında görüntülenir.

10. Hızlı Başlat çubuğunda **hastalar** bağlantısını seçin ve ardından **Yeni öğe Ekle** bağlantısını seçin.

     Yeni öğeler için giriş formu açılır.

11. Alanlara veri girin ve ardından **Kaydet** düğmesini seçin.

     **Kaydet** düğmesini seçtikten sonra, **hasta adı** sütunu Scott kahverengi adına otomatik olarak güncelleştirilir.

## <a name="see-also"></a>Ayrıca bkz.

- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)