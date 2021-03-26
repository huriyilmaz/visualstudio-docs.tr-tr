---
title: Proje sistemlerini genişletmek için IDE-Defined komutları | Microsoft Docs
description: Visual Studio tümleşik geliştirme ortamında (IDE) proje sistemlerini genişletmek için kullanılan komutlar ve komut grupları hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6fedca7081c531fef257e20e64426f8b35e88e87
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086007"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>Proje Sistemlerini Genişletmeye Yönelik IDE Tanımlı Komutlar
Proje sistemlerini genişletmek istediğinizde, IDE tarafından sunulan komutları ve komut gruplarını kullanabilirsiniz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 Aşağıdaki bölümlerde, özellikle proje sistemlerini genişletmek için yararlı olan komut öğeleri listelenmektedir.

## <a name="command-menus"></a>Komut menüleri
 Aşağıdaki tabloda, bir proje genişletici 'i çağıran üst düzey komutları yerleştirmeniz için yararlı konumlar olan komut menüleri gösterilmektedir.

|Komut menüsü|Description|
|------------------|-----------------|
|IDM_VS_MENU_PROJECT|**Projenin** üst düzey menüsü.|
|IDM_VS_TOOL_PROJWIN|**Çözüm Gezgini** araç çubuğu.|

## <a name="shortcut-menus"></a>Kısayol Menüleri
 Aşağıdaki tabloda, **Çözüm Gezgini** tek bir düğüm seçildiğinde veya **Çözüm Gezgini** birden çok Hogense seçimi olduğunda uygulanan kısayol menüleri gösterilmektedir. Bu, seçilen tüm düğümlerin aynı türden olduğu durumlar olur.

|Kısayol menüsü|Description|
|-------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Proje düğümü seçildiğinde geçerlidir.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Bir dosya seçildiğinde geçerlidir.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Bir klasör seçildiğinde geçerlidir.|
|IDM_VS_CTXT_WEBREFFOLDER|Web başvurusu klasörü seçildiğinde geçerlidir.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|"Başvurular" olarak adlandırılan başvurular kök düğümü seçildiğinde geçerlidir.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Başvuru düğümleri seçildiğinde geçerlidir; Bunlar yalnızca derleme, COM ve proje başvuruları içerir. Web başvuruları içermez.|

 Aşağıdaki tabloda, **Çözüm Gezgini** seçimi birden çok hiyerarşinin yayıldığı zaman uygulanan kısayol menüleri gösterilmektedir.

|Kısayol menüsü|Description|
|-------------------|-----------------|
|IDM_VS_CTXT_XPROJ_SLNPROJ|Geçerli seçim çözüm düğümünü ve kök proje düğümlerini içerdiğinde geçerlidir.|
|IDM_VS_CTXT_XPROJ_SLNITEM|Geçerli seçim çözüm düğümünü ve proje öğelerini içerdiğinde geçerlidir.|
|IDM_VS_CTXT_XPROJ_MULTIPROJ|Geçerli seçim yalnızca birden çok kök proje düğümünden oluşuyorsa geçerlidir.|
|IDM_VS_CTXT_XPROJ_PROJITEM|Geçerli seçim kök proje düğümlerinin ve proje öğelerinin bir karışımını içerdiğinde geçerlidir. Ek olarak, seçim çözüm düğümünü de içerebilir.|
|IDM_VS_CTXT_XPROJ_MULTIITEM|Geçerli seçim çözümdeki birden çok projeden proje öğeleri içerdiğinde veya aynı projede farklı türlerde öğeler seçildiğinde geçerlidir.|

## <a name="command-groups"></a>Komut grupları
 Aşağıdaki tabloda, projeleri genişlettiğinizde kullanabileceğiniz ve kısayol menüsü üzerinden erişebileceğiniz komut grupları gösterilmektedir <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> .

|Komut grubu|Description|
|-------------------|-----------------|
|IDG_VS_CTXT_PROJECT_BUILD|Projeyi oluşturmaya, yeniden oluşturmaya ve dağıtmaya yönelik komutlar.|
|IDG_VS_CTXT_COMPILELINK|Projeyi derlemek ve bağlamak için komutlar.|
|IDG_VS_CTXT_PROJECT_CONFIG|Proje yapılandırmasını ve derleme sırasını ayarlama komutları.|
|IDG_VS_CTXT_PROJECT_ADD|Projeye öğe ekleyen komutlar.|
|IDG_VS_CTXT_PROJECT_START|F5 tuşuyla ilişkili başlangıç projesini ayarlama komutları.|
|IDG_VS_CTXT_PROJECT_SAVE|Proje öğelerini kaydetme komutları.|
|IDG_VS_CTXT_PROJECT_DEBUG|Hata ayıklama komutları.|
|IDG_VS_CTXT_PROJECT_SCC|Kaynak denetimi için komutlar.|
|IDG_VS_CTXT_PROJECT_TRANSFER|Kesme, kopyalama ve yapıştırma işlemlerine yönelik komutlar.|
|IDG_VS_CTXT_PROJECT_PROPERTIES|**Proje özellikleri** iletişim kutusuna erişim sağlayan komutlar.|

## <a name="see-also"></a>Ayrıca bkz.

- [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Yeniden Kullanılabilir Düğme Grupları Oluşturma](../../extensibility/creating-reusable-groups-of-buttons.md)
