---
title: 'İzlenecek yol: özel site Iş akışı etkinliği oluşturma | Microsoft Docs'
description: bu kılavuzda, Visual Studio kullanarak site düzeyi SharePoint iş akışı için özel etkinlik oluşturma bölümüne bakın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, custom workflow activities
- site workflows [SharePoint development in Visual Studio]
- workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, site workflows
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 8a7beaea3b9a7becc2b162304287b4e1b340fceb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135864"
---
# <a name="walkthrough-create-a-custom-site-workflow-activity"></a>İzlenecek yol: özel site iş akışı etkinliği oluşturma
  Bu izlenecek yol, kullanarak site düzeyinde iş akışı için özel bir etkinliğin nasıl oluşturulacağını gösterir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . (Site düzeyi iş akışları yalnızca sitede bir liste değil, tüm site için geçerlidir.) Özel etkinlik bir yedekleme duyuruları listesi oluşturur ve sonra Duyurular listesinin içeriğini buna kopyalar.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Site düzeyinde iş akışı oluşturma.

- Özel iş akışı etkinliği oluşturma.

- SharePoint listesi oluşturma ve silme.

- Öğeleri bir listeden diğerine kopyalama.

- Hızlı Başlat çubuğunda bir liste görüntüleme.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]Ve SharePoint desteklenen sürümleri.

- Visual Studio.

## <a name="create-a-site-workflow-custom-activity-project"></a>Site iş akışı özel etkinlik projesi oluşturma
 İlk olarak, özel iş akışı etkinliğini tutacak ve test eden bir proje oluşturun.

#### <a name="to-create-a-site-workflow-custom-activity-project"></a>Bir site iş akışı özel etkinlik projesi oluşturmak için

1.   >    >  **yeni Project** iletişim kutusunu göstermek için menü çubuğunda dosya yeni **Project** öğesini seçin.

2. **Visual C#** veya **Visual Basic** altındaki **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

3. **şablonlar** bölmesinde **SharePoint 2010 Project** şablonunu seçin.

4. **Ad** kutusuna **AnnouncementBackup** girin ve **Tamam** düğmesini seçin.

     **SharePoint özelleştirme sihirbazı** görüntülenir.

5. **Hata ayıklama için site ve güvenlik düzeyini belirtin** sayfasında, **Grup çözümü olarak dağıt** seçenek düğmesini seçin ve ardından güven düzeyini ve varsayılan siteyi kabul etmek için **son** düğmesini seçin.

     Bu adım, iş akışı projeleri için kullanılabilir tek seçenek olan çözüm için güven düzeyini Grup çözümü olarak ayarlar.

6. **Çözüm Gezgini**, proje düğümünü seçin ve ardından menü çubuğunda, **Project**  >  **yeni öğe ekle**' yi seçin.

7. **Visual C#** veya **Visual Basic** altında **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

8. **Şablonlar** bölmesinde, **sıralı iş akışı (yalnızca Grup çözümü)** şablonunu seçin ve ardından **Ekle** düğmesini seçin.

     **SharePoint özelleştirme sihirbazı** görüntülenir.

9. **Hata ayıklama için iş akışı adını belirtin** sayfasında, varsayılan adı (AnnouncementBackup-Workflow1) kabul edin. İş akışı şablonu türünü **site Iş akışı** olarak değiştirin ve ardından **İleri** düğmesini seçin.

10. Kalan varsayılan ayarları kabul etmek için **son** düğmesini seçin.

## <a name="add-a-custom-workflow-activity-class"></a>Özel iş akışı etkinlik sınıfı ekleme
 Sonra, özel iş akışı etkinliğinin kodunu içermesi için projeye bir sınıf ekleyin.

#### <a name="to-add-a-custom-workflow-activity-class"></a>Özel bir iş akışı etkinlik sınıfı eklemek için

1. menü çubuğunda, yeni   >  **öğe** ekle iletişim kutusunu göstermek için Project **yeni öğe ekle** ' yi seçin.

2. **Yüklü şablonlar** ağacı görünümünde, **kod** düğümünü seçin ve ardından proje öğesi şablonları listesinden **sınıf** şablonunu seçin. Class1 varsayılan adını kullanın. **Ekle** düğmesini seçin.

3. Class1 içindeki tüm kodu aşağıdakiler ile değiştirin:

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/announcementbackup/class1.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/announcementbackupvb/class1.vb" id="Snippet1":::

4. Projeyi kaydedin ve sonra menü **çubuğunda yapı**  >  **oluşturma çözümü**' ni seçin.

     Class1, **AnnouncementBackup bileşenleri** sekmesindeki **araç kutusunda** özel bir eylem olarak görünür.

## <a name="add-the-custom-activity-to-the-site-workflow"></a>Özel etkinliği site iş akışına ekleme
 Ardından, özel kodu içermesi için Iş akışına bir etkinlik ekleyin.

#### <a name="to-add-a-custom-activity-to-the-site-workflow"></a>Site iş akışına özel etkinlik eklemek için

1. Tasarım görünümünde iş akışı tasarımcısında Workflow1 öğesini açın.

2. Etkinlik altında görünmesi için **araç kutusundan** Class1 ' ı sürükleyin `onWorkflowActivated1` veya Class1 için kısayol menüsünü açın, **Kopyala**' yı seçin, etkinliğin altındaki satır için kısayol menüsünü açın `onWorkflowActivated1` ve ardından **Yapıştır**' ı seçin.

3. Projeyi kaydedin.

## <a name="test-the-site-workflow-custom-activity"></a>Site iş akışı özel etkinliğini test etme
 Sonra, projeyi çalıştırın ve site iş akışını başlatın. Özel etkinlik bir yedekleme duyuruları listesi oluşturur ve içeriği geçerli Duyurular listesinden buraya kopyalar. Kod ayrıca, bir yedekleme listesinin oluşturmadan önce zaten var olup olmadığını denetler. Bir yedekleme listesi zaten varsa, silinir. kod ayrıca SharePoint sitesinin hızlı başlat çubuğundaki yeni listeye bir bağlantı ekler.

#### <a name="to-test-the-site-workflow-custom-activity"></a>Site iş akışı özel etkinliğini test etmek için

1. Projeyi çalıştırmak ve SharePoint dağıtmak için **F5** tuşunu seçin.

2. hızlı başlat çubuğunda, SharePoint sitesinde bulunan tüm listeleri göstermek için **listeler** bağlantısını seçin. **Duyurular** adlı duyurular için yalnızca bir liste olduğuna dikkat edin.

3. SharePoint web sayfasının en üstünde **Site iş akışları** bağlantısını seçin.

4. Yeni bir Iş akışı Başlat bölümünde **AnnouncementBackup-Workflow1** bağlantısını seçin. Bu, site iş akışını başlatır ve özel eylemde kodu çalıştırır.

5. Hızlı Başlat çubuğunda **Duyurular yedekleme** bağlantısını seçin. **Duyurular** listesinde yer alan tüm Duyurular bu yeni listeye kopyalanmış olduğuna dikkat edin.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: olay alıcısı oluşturma](../sharepoint/how-to-create-an-event-receiver.md)
- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)
