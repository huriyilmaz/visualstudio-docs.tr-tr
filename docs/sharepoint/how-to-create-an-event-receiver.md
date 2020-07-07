---
title: 'Nasıl yapılır: olay alıcısı oluşturma | Microsoft Docs'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 26d8c9f433fad051716b6ebd37e3d1f3b3f9f4eb
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016917"
---
# <a name="how-to-create-an-event-receiver"></a>Nasıl yapılır: olay alıcısı oluşturma
  *Olay alıcıları*oluşturarak, bir kullanıcı listeler veya liste öğeleri gibi SharePoint öğeleriyle etkileşime geçtiğinde yanıt verebilirsiniz. Örneğin, bir kullanıcı takvimi değiştirdiğinde veya bir kişi listesinden bir adı silerse bir olay alıcısındaki kod tetiklenebilir. Bu konuyu izleyerek bir liste örneğine bir olay alıcısının nasıl ekleneceğini öğrenebilirsiniz.

 Bu adımları tamamlayabilmeniz için, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Windows ve SharePoint 'in yüklü ve desteklenen sürümlerini yüklemiş olmanız gerekir. Bu örnekte bir SharePoint projesi gerektiğinden, [Izlenecek yol: SharePoint için site sütunu, içerik türü ve liste oluşturma](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)konusundaki prosedürü de tamamlamış olmanız gerekir.

## <a name="adding-an-event-receiver"></a>Olay alıcısı ekleme
 [Izlenecek yol: SharePoint için site sütunu, içerik türü ve liste oluşturma](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) bölümünde oluşturduğunuz proje özel site sütunları, özel bir liste ve içerik türü içerir. Aşağıdaki yordamda, listeleri gibi SharePoint öğelerinde oluşan olayların nasıl işleneceğini göstermek için bir liste örneğine basit bir olay işleyicisi (bir olay alıcısı) ekleyerek bu projeyi genişlettireceksiniz.

#### <a name="to-add-an-event-receiver-to-the-list-instance"></a>Liste örneğine bir olay alıcısı eklemek için

1. [Izlenecek yol: SharePoint için site sütunu, içerik türü ve liste oluşturma](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)bölümünde oluşturduğunuz projeyi açın.

2. **Çözüm Gezgini**' de, **Clinic**adlı SharePoint proje düğümünü seçin.

3. Menü çubuğunda, **Proje**  >  **Yeni öğe Ekle**' yi seçin.

4. **Visual C#** veya **Visual Basic**altında **SharePoint** düğümünü genişletin ve ardından **2010** öğesini seçin.

5. **Şablonlar** bölmesinde **olay alıcısı**' nı seçin, **TestEventReceiver1**olarak adlandırın ve **Tamam** düğmesini seçin.

     **SharePoint Özelleştirme Sihirbazı** görüntülenir.

6. **Ne tür bir olay alıcısı istiyorsunuz?** listesinde, **liste öğesi olayları**' nı seçin.

7. **Hangi öğe olay kaynağı olmalıdır?** listesinde, **hastalar (klinic\hastalar)** öğesini seçin.

8. **Aşağıdaki olayları işle** listesinde, **öğe eklenmiş**seçeneğinin yanındaki onay kutusunu işaretleyin ve ardından **son** düğmesini seçin.

     Yeni olay alıcısının kod dosyası, adlı tek bir yöntem içerir `ItemAdded` . Sonraki adımda, bu yönteme kod ekleyeceksiniz, böylece her kişi varsayılan olarak Scott kahverengi olarak adlandırılır.

9. Mevcut `ItemAdded` yöntemi aşağıdaki kodla değiştirin ve **F5** tuşunu seçin:

     [!code-csharp[SP_EventReceiver#1](../sharepoint/codesnippet/CSharp/CustomField1/TestEventReceiver1/TestEventReceiver1.cs#1)]
     [!code-vb[SP_EventReceiver#1](../sharepoint/codesnippet/VisualBasic/CustomField1_VB/EventReceiver1/EventReceiver1.vb#1)]

     Kod çalışır ve SharePoint sitesi Web tarayıcısında görüntülenir.

10. Hızlı Başlat çubuğunda **hastalar** bağlantısını seçin ve ardından **Yeni öğe Ekle** bağlantısını seçin.

     Yeni öğeler için giriş formu açılır.

11. Alanlara veri girin ve ardından **Kaydet** düğmesini seçin.

     **Kaydet** düğmesini seçtikten sonra, **hasta adı** sütunu Scott kahverengi adına otomatik olarak güncelleştirilir.

## <a name="see-also"></a>Ayrıca bkz.

- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)