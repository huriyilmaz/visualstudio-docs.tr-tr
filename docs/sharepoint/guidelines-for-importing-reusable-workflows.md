---
title: Yeniden kullanılabilir Iş akışlarını Içeri aktarma yönergeleri | Microsoft Docs
description: SharePoint tasarımcısında oluşturulan yeniden kullanılabilir iş akışlarını Visual Studio içine aktarmaya yönelik yönergeleri gözden geçirin.
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
ms.openlocfilehash: 76bdfd937fb054e2fa1b9bc533371ce347761d915074bb435705f9395a2270f5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121425458"
---
# <a name="guidelines-for-importing-reusable-workflows"></a>Yeniden kullanılabilir iş akışlarını içeri aktarma yönergeleri
  SharePoint tasarımcısında oluşturulan yeniden kullanılabilir iş akışlarını içeri aktarmak için, içinde yeniden kullanılabilir SharePoint 2010 iş akışı proje şablonunu kullanın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Bu şablon *bildirim temelli* bir *iş akışını* içeri aktarır ( [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] -yalnızca) ve bir *kod akışına* dönüştürerek, veya kod ile geliştirebileceğinizi bir iş akışıdır [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] . [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][izlenecek yol: SharePoint Designer yeniden kullanılabilir iş akışını Visual Studio içine aktarın](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).

 ancak, içeri aktarma yeniden kullanılabilir SharePoint 2010 iş akışı şablonu yalnızca grup çözümlerini içeri aktarabilir. iş akışınızı bir korumalı çözüm olarak dağıtmak istiyorsanız, içeri aktarma SharePoint 2010 çözüm paketi şablonuyla içeri aktarın. Bununla birlikte, bunu yaparak kod iş akışına dönüştüremezsiniz ve bu şekilde değiştiremeyecektir.

## <a name="import-reusable-workflows-by-using-the-import-reusable-workflow-template"></a>Yeniden kullanılabilir iş akışlarını Içeri aktarma yeniden kullanılabilir Iş akışı şablonunu kullanarak içeri aktarma
 yeniden kullanılabilir bir iş akışını içeri aktarma SharePoint 2010 iş akışı şablonunu kullanarak içeri aktarırsanız, çözümü diğer SharePoint çözümünde olduğu gibi çalıştırabilir veya değiştirebilirsiniz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , ancak bazı öğeleri el ile çözmeniz gerekebilir.

### <a name="import-task-forms"></a>Görev formlarını içeri aktarma
 yeniden kullanılabilir SharePoint 2010 iş akışı proje şablonu, tüm başlatma ve ilişkilendirme formlarını içeri aktarır, ancak yalnızca bir görev formu içeri aktarır çünkü kod iş akışı şeması yalnızca bir görev formuna izin verir. Özgün iş akışı çözümünden gelen tüm ek görev formları **Çözüm Gezgini** Içindeki **diğer içeri aktarılan dosyalar** klasörüne konur.

## <a name="import-reusable-workflows-by-using-the-import-sharepoint-2010-solution-package-template"></a>içeri aktarma SharePoint 2010 çözüm paketi şablonunu kullanarak yeniden kullanılabilir iş akışlarını içeri aktarma
 içeri aktarma SharePoint 2010 çözüm paketi şablonunu kullanarak yeniden kullanılabilir bir iş akışını içeri aktarırsanız, aşağıdaki sorunları göz önünde bulundurmanız gerekir:

- İş akışını içeri aktardıktan sonra [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **F5** tuşunu seçerek bunu hemen dağıtabilir ve çalıştırabilirsiniz. Ancak, içeri aktarılan çözümde iş akışındaki herhangi bir şeyi değiştirirseniz, iş akışını dağıtıp çalıştırmadan önce projedeki öğeleri el ile çözmeniz gerekebilir.

- İş akışı bildirime dayalı olduğundan, kod buna eklenemiyor. iş akışını bir kod iş akışına dönüştürmek için, yeniden [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kullanılabilir SharePoint 2010 iş akışı şablonunu kullanarak içine aktarmanız gerekir.

- Tasarım görünümü ' de iş akışı Tasarımcısı (. xoml) dosyasını düzenleyebilmeniz mümkün olsa da, iş akışı Tasarımcısı hatalı hataları gösterdiği için onu kaynak görünümünde düzenlemeniz önerilir.

- İş akışında hata ayıklama bildirim temelli içerik için çalışmıyor. İçinde ayarlanan kesme noktaları [!INCLUDE[wfd2](../sharepoint/includes/wfd2-md.md)] isabet etmez.

## <a name="import-globally-reusable-workflow-solutions"></a>Küresel olarak yeniden kullanılabilir iş akışı çözümlerini içeri aktarma
 genel olarak yeniden kullanılabilir iş akışları içeri aktarma yeniden kullanılabilir SharePoint 2010 iş akışı şablonu kullanılarak içeri aktarılamaz. küresel olarak yeniden kullanılabilir bir iş akışını içeri aktarmak için, bunu küresel olmayan bir iş akışına dönüştürmeniz veya SharePoint 2010 çözüm paketi şablonunu kullanmanız gerekir.

 iş akışını dönüştürmek için SharePoint tasarımcısında küresel olarak yeniden kullanılabilir iş akışının bir kopyasını oluşturun (iş akışının kısayol menüsünü açarak ve ardından **kopya olarak kaydet**' i seçerek). sonra, içinde yeniden kullanılabilir SharePoint 2010 iş akışı şablonuyla yeni yeniden kullanılabilir iş akışını içeri aktarın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

 global olarak yeniden kullanılabilir iş akışını değiştirmeden içeri aktarmak için SharePoint 2010 çözüm paketi şablonunu içeri aktar ' ı kullanın. Bu yöntemi kullanırsanız, iş akışı bir kod iş akışına dönüştürülmez ve bildirim temelli bir iş akışı kalır.

## <a name="see-also"></a>Ayrıca bkz.
- [mevcut bir SharePoint sitesinden öğeleri içeri aktar](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [izlenecek yol: SharePoint Designer yeniden kullanılabilir iş akışını Visual Studio içine aktarma](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)
