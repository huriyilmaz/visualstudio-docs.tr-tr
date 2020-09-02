---
title: Yeniden kullanılabilir Iş akışlarını Içeri aktarma yönergeleri | Microsoft Docs
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bb386a2d80931ece415b0b3939f2947678808261
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62557194"
---
# <a name="guidelines-for-importing-reusable-workflows"></a>Yeniden kullanılabilir iş akışlarını içeri aktarma yönergeleri
  SharePoint Designer 'da oluşturulan yeniden kullanılabilir iş akışlarını içeri aktarmak için, içinde yeniden kullanılabilir SharePoint 2010 Iş akışı proje şablonunu kullanın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Bu şablon *bildirim temelli* bir *iş akışını* içeri aktarır ( [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] -yalnızca) ve bir *kod akışına*dönüştürerek, veya kod ile geliştirebileceğinizi bir iş akışıdır [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] . [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Izlenecek yol: bir SharePoint Designer yeniden kullanılabilir iş akışını Visual Studio 'Ya Içeri aktarma](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).

 Bununla birlikte, Içeri aktarma yeniden kullanılabilir SharePoint 2010 Iş akışı şablonu yalnızca Grup çözümlerini içeri aktarabilir. İş akışınızı bir korumalı çözüm olarak dağıtmak istiyorsanız, SharePoint 2010 çözüm paketi şablonunu Içeri Aktar ' ı kullanarak içeri aktarın. Bununla birlikte, bunu yaparak kod iş akışına dönüştüremezsiniz ve bu şekilde değiştiremeyecektir.

## <a name="import-reusable-workflows-by-using-the-import-reusable-workflow-template"></a>Yeniden kullanılabilir iş akışlarını Içeri aktarma yeniden kullanılabilir Iş akışı şablonunu kullanarak içeri aktarma
 Yeniden kullanılabilir bir iş akışını Içeri aktarma yeniden kullanılabilir SharePoint 2010 Iş akışı şablonunu kullanarak içeri aktarırsanız, çözümü başka bir SharePoint çözümüne benzer şekilde çalıştırabilir veya değiştirebilirsiniz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , ancak bazı öğeleri el ile çözmeniz gerekebilir.

### <a name="import-task-forms"></a>Görev formlarını içeri aktarma
 Yeniden kullanılabilir SharePoint 2010 Iş akışı proje şablonu, tüm başlatma ve ilişkilendirme formlarını içeri aktarır, ancak yalnızca bir görev formu içeri aktarır çünkü kod iş akışı şeması yalnızca bir görev formuna izin verir. Özgün iş akışı çözümünden gelen tüm ek görev formları **Çözüm Gezgini**Içindeki **diğer içeri aktarılan dosyalar** klasörüne konur.

## <a name="import-reusable-workflows-by-using-the-import-sharepoint-2010-solution-package-template"></a>Yeniden kullanılabilir iş akışlarını içeri aktarma SharePoint 2010 çözüm paketi şablonunu kullanarak
 SharePoint 2010 çözüm paketi şablonunu Içeri Aktar ' ı kullanarak yeniden kullanılabilir bir iş akışını içeri aktarırsanız, aşağıdaki sorunları göz önünde bulundurmanız gerekir:

- İş akışını içeri aktardıktan sonra [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **F5** tuşunu seçerek bunu hemen dağıtabilir ve çalıştırabilirsiniz. Ancak, içeri aktarılan çözümde iş akışındaki herhangi bir şeyi değiştirirseniz, iş akışını dağıtıp çalıştırmadan önce projedeki öğeleri el ile çözmeniz gerekebilir.

- İş akışı bildirime dayalı olduğundan, kod buna eklenemiyor. İş akışını bir kod iş akışına dönüştürmek için, yeniden [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kullanılabilir SharePoint 2010 Iş akışı şablonunu Içeri Aktar ' ı kullanarak içine aktarmanız gerekir.

- Tasarım görünümü ' de iş akışı Tasarımcısı (. xoml) dosyasını düzenleyebilmeniz mümkün olsa da, iş akışı Tasarımcısı hatalı hataları gösterdiği için onu kaynak görünümünde düzenlemeniz önerilir.

- İş akışında hata ayıklama bildirim temelli içerik için çalışmıyor. İçinde ayarlanan kesme noktaları [!INCLUDE[wfd2](../sharepoint/includes/wfd2-md.md)] isabet etmez.

## <a name="import-globally-reusable-workflow-solutions"></a>Küresel olarak yeniden kullanılabilir iş akışı çözümlerini içeri aktarma
 Genel olarak yeniden kullanılabilir iş akışları Içeri aktarma yeniden kullanılabilir SharePoint 2010 Iş akışı şablonu kullanılarak içeri aktarılamaz. Küresel olarak yeniden kullanılabilir bir iş akışını içeri aktarmak için, onu genel olmayan bir iş akışına dönüştürmeniz veya SharePoint 2010 çözüm paketi şablonunu Içeri Aktar ' ı kullanmanız gerekir.

 İş akışını dönüştürmek için, SharePoint Designer 'da genel olarak yeniden kullanılabilir iş akışının bir kopyasını oluşturun (iş akışının kısayol menüsünü açarak ve ardından **kopya olarak kaydet**' i seçerek). Daha sonra, içindeki yeniden kullanılabilir SharePoint 2010 Iş akışı şablonuyla yeni yeniden kullanılabilir iş akışını içeri aktarın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

 Global olarak yeniden kullanılabilir iş akışını değiştirmeden içeri aktarmak için SharePoint 2010 çözüm paketi şablonunu Içeri Aktar ' ı kullanın. Bu yöntemi kullanırsanız, iş akışı bir kod iş akışına dönüştürülmez ve bildirim temelli bir iş akışı kalır.

## <a name="see-also"></a>Ayrıca bkz.
- [Mevcut bir SharePoint sitesinden öğeleri içeri aktar](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [İzlenecek yol: SharePoint Designer yeniden kullanılabilir iş akışını Visual Studio 'ya aktarma](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)
