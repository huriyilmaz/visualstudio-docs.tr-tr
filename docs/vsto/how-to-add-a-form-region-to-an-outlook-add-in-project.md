---
title: Nasıl Outlook Eklenti projesine form bölgesi ekleme
description: New Outlook Form Region sihirbazını kullanarak standart veya özel bir form Microsoft Office Outlook form genişletmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VSTO.NewFormRegionWizard.Page1
- VSTO.NewFormRegionWizard.Page3
- VSTO.NewFormRegionWizard.Page2
- VSTO.NewFormRegionWizard.Page0
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], adding
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 4afff086588d70ea8b09b6aaf74a3899c663d9ce
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122139874"
---
# <a name="how-to-add-a-form-region-to-an-outlook-add-in-project"></a>Nasıl Outlook Eklenti projesine form bölgesi ekleme
  Yeni Form Bölgesi sihirbazını kullanarak standart veya özel Microsoft Office Outlook **formu genişletmek için bir form Outlook** oluşturun. Yeni bir form bölgesi oluşturabilir ve Visual Studio'de kullanıcı arabirimini tasarabilir veya Outlook'de tasarlanmış bir form Visual Basic veya C# kodu içeri aktarabilirsiniz.

 Başka bir Outlook projesinde kullanılan bir Outlook form bölgeniz varsa, Mevcut Öğeyi Ekle iletişim kutusunu kullanarak Outlook VSTO Eklenti  projesinde yeniden kullanabilirsiniz. Daha fazla bilgi için [bkz. Form Outlook oluşturma.](../vsto/creating-outlook-form-regions.md)

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

### <a name="to-add-a-new-form-region-to-an-outlook-project"></a>Outlook projesine yeni bir form bölgesi eklemek için

1. içinde bir Outlook VSTO Eklenti projesi açın veya [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] oluşturun. Daha fazla bilgi için, [bkz. How to: Create Office projects in Visual Studio.](../vsto/how-to-create-office-projects-in-visual-studio.md)

2. Bu **Çözüm Gezgini,** eklenti Outlook VSTO proje düğümünü seçin.

3. Yeni **Project** Ekle'ye **tıklayın.**

4. Yeni Öğe **Ekle iletişim kutusunda** Form **Bölgesi'Outlook seçin.**

5. Ad kutusuna form bölgesi için bir ad **yazın ve** ekle'ye **tıklayın.**

     **NewOutlook Form Bölgesi** sihirbazı başlatılır.

6. Form **bölgesi oluşturmak** istediğiniz şekli seçin sayfasında, yönetilen denetimleri bir görsel tasarımcıya sürükleyerek form bölgesi tasarlamak mı yoksa form bölgesinde tasarlanmış bir form bölgesini içeri Outlook.

    > [!NOTE]
    > Outlook'de tasarlanmış bir form bölgelerini içeri aktarmayı seçerseniz, Outlook Form Depolama (*.ofs*) dosyasının konumunu belirtmeniz gerekir. Yönetilen denetimleri, bir form bölgesinde tasarlayın bir form Outlook; yalnızca mevcut kullanıcı arabiriminin arkasına kod eklersiniz. Daha fazla bilgi için [bkz. Form Outlook oluşturma.](../vsto/creating-outlook-form-regions.md)

7. Oluşturmak **istediğiniz form bölgesi türünü seçin sayfasında form** bölgesi türlerini gözden geçirerek birini seçin ve ardından Sonraki 'ye **tıklayın.** Form bölgesi türleri hakkında daha fazla bilgi için [bkz. Form Outlook oluşturma.](../vsto/creating-outlook-form-regions.md)

8. Açıklayıcı **metin girin ve görüntüleme tercihlerinizi seçin** sayfasındaki **Ad** kutusuna form bölgesi için bir ad yazın. Değiştirme ve tüm form bölgelerini değiştirme için Başlık **ve** **Açıklama** kutuları da kullanılabilir.

     Form bölgesini dağıtarak ad, başlık ve açıklamanın Outlook bilgi için bkz. Form [bölgelerini Outlook oluşturma.](../vsto/creating-outlook-form-regions.md)

9. Form bölgesinde görünmesini istediğiniz bir veya daha fazla görüntü modu seçin.

     Tüm form bölgesi türleri Denetçiler'de, oluşturma modunda (öğe oluşturmak için) ve okuma modunda (öğeleri görüntülemek için) görünebilir. Ekleme, değiştirme ve tüm form bölgelerini değiştirme türleri Okuma Bölmesi'nde de görünebilir.

10. **İleri**’ye tıklayın.

11. Bu **form bölgesi görüntüecek** ileti sınıflarını tanımla sayfasında, standart Outlook ileti sınıflarını seçin veya bir veya daha fazla özel ileti sınıfını yazın ve ardından Son'a **tıklayın.** Daha fazla bilgi için [bkz. Form bölgelerini bir form Outlook sınıfıyla ilişkilendirme.](../vsto/associating-a-form-region-with-an-outlook-message-class.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma zamanında form bölgelerine erişme](../vsto/accessing-a-form-region-at-run-time.md)
- [Outlook çözümleri](../vsto/outlook-solutions.md)
- [Form Outlook bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)
- [Form bölgelerini Outlook yönergeleri](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Adım adım kılavuz: Form Outlook tasarlama](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Adım adım kılavuz: Veri kaynağında tasarlanmış bir form Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [Form bölgelerinde Outlook eylemler](../vsto/custom-actions-in-outlook-form-regions.md)
