---
title: Yeniden Kullanılabilir İş Akışlarını İçeri Aktarma yönergeleri | Microsoft Docs
description: SharePoint Designer'da oluşturulan yeniden kullanılabilir iş akışlarını Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- SharePoint development in Visual Studio, reusable workflows
- importing items [SharePoint development in Visual Studio]
- reusable workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: a65af6481b9cffbff268553f93acd7105066aa1c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122149565"
---
# <a name="guidelines-for-importing-reusable-workflows"></a>Yeniden kullanılabilir iş akışlarını içeri aktarma yönergeleri
  SharePoint Designer'da oluşturulan yeniden kullanılabilir iş akışlarını içeri aktarın, içinde Yeniden Kullanılabilir İş Akışı SharePoint 2010 İş Akışı proje şablonunu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kullanın. Bu şablon bildirimli *bir*  iş akışını (yalnızca) içeri aktarır ve bir kod iş akışına dönüştürür. Bu iş akışı, ya da kod ile [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]  [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] geliştirebilirsiniz. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Adım adım kılavuz: SharePoint Tasarımcısı yeniden](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)kullanılabilir iş akışını Visual Studio.

 Ancak 2010 İş Akışı SharePoint İçeri Aktar şablonu yalnızca grup çözümlerini içeri aktarabilir. İş akışınızı korumalı alanlı bir çözüm olarak dağıtmak için İçeri Aktarma paketi 2010 SharePoint şablonuyla içeri aktarın. Ancak bunu yaparak kod iş akışına dönüştüresiniz ve bu şekilde değiştiremezsiniz.

## <a name="import-reusable-workflows-by-using-the-import-reusable-workflow-template"></a>Yeniden Kullanılabilir İş Akışını İçeri Aktar şablonunu kullanarak yeniden kullanılabilir iş akışlarını içeri aktarma
 Yeniden kullanılabilir bir iş akışını Yeniden Kullanılabilir İş Akışını İçeri Aktar SharePoint 2010 İş Akışı şablonunu kullanarak içeri aktardısanız, çözümü diğer tüm SharePoint çözümlerde olduğu gibi çalıştırabilir veya değiştirebilirsiniz, ancak bazı öğeleri el ile [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] düzeltmeniz gerekebilir.

### <a name="import-task-forms"></a>Görev formlarını içeri aktarma
 Yeniden Kullanılabilir İçeri Aktar SharePoint 2010 İş Akışı proje şablonu tüm başlatma ve ilişkilendirme formlarını içeri aktarıyor, ancak kod iş akışı şeması yalnızca bir görev formuna izin vermesi nedeniyle yalnızca bir görev formunu içeri aktarıyor. Özgün iş akışı çözümünden gelen ek görev formları, içinde **Diğer İçe Aktarılan Dosyalar** **klasörüne Çözüm Gezgini.**

## <a name="import-reusable-workflows-by-using-the-import-sharepoint-2010-solution-package-template"></a>2010 Çözüm Paketi şablonunu İçeri Aktar SharePoint yeniden kullanılabilir iş akışlarını içeri aktarma
 2010 Çözüm Paketi İçeri Aktar şablonunu kullanarak yeniden kullanılabilir bir iş akışını içeri SharePoint, aşağıdaki sorunları göz önünde bulundurabilirsiniz:

- İş akışını içeri aktardikten sonra F5 anahtarını seçerek hemen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dağıtabilirsiniz ve **içinde çalıştırabilirsiniz.** Ancak, içe aktarılan çözümde iş akışında herhangi bir şeyi değiştirirsanız, iş akışını dağıtarak çalıştırmadan önce proje öğeleri el ile düzeltmeniz gerekebilir.

- İş akışı bildirimli olduğundan, buna kod ek olamaz. İş akışını bir kod iş akışına dönüştürmek için 2010 İş Akışı şablonunda Yeniden Kullanılabilir SharePoint'ı kullanarak iş akışını içine [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aktarmalısınız.

- İş akışı tasarımcısı (.xoml) dosyasını Tasarım görünümü, ancak iş akışı tasarımcısı yanlış hatalar görüntüleyeden Kaynak görünümünde düzenlemeniz önerilir.

- İş akışında hata ayıklama bildirimli içerik için çalışmıyor. içinde ayarlanmış kesme [!INCLUDE[wfd2](../sharepoint/includes/wfd2-md.md)] noktalarına isabet değildir.

## <a name="import-globally-reusable-workflow-solutions"></a>Genel olarak yeniden kullanılabilir iş akışı çözümlerini içeri aktarma
 Genel olarak yeniden kullanılabilir iş akışları, 2010 İş Akışı şablonunda Yeniden Kullanılabilir SharePoint kullanılarak içeri aktarılamaz. Genel olarak yeniden kullanılabilir bir iş akışını içeri aktaracak şekilde genel olarak yeniden kullanılabilir olmayan bir iş akışına dönüştürmeniz veya İçeri Aktarma SharePoint 2010 Çözüm Paketi şablonunu kullansanız gerekir.

 İş akışını dönüştürmek için genel olarak yeniden kullanılabilir iş akışının bir kopyasını SharePoint Tasarımcısı'nda (iş akışının kısayol menüsünü açarak ve ardından Kopyala olarak **kaydet'i seçerek).** Ardından, 'de Yeniden Kullanılabilir İş Akışını İçeri Aktar 2010 SharePoint yeni yeniden kullanılabilir iş akışını içeri [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aktarın.

 Genel olarak yeniden kullanılabilir iş akışını değiştirmeden içeri aktarın, 2010 Çözüm Paketi SharePoint aktar şablonunu kullanın. Bu yöntemi kullanırsanız, iş akışı bir kod iş akışına dönüştürülmesiz ve bildirime açık bir iş akışı olarak kalır.

## <a name="see-also"></a>Ayrıca bkz.
- [Mevcut bir siteden öğeleri SharePoint alma](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Adım adım kılavuz: SharePoint Tasarımcısı yeniden kullanılabilir iş akışını Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)
