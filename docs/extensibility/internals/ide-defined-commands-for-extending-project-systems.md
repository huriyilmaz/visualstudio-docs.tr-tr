---
title: Proje sistemlerini genişletmek için IDE tanımlı komutlar | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e406fb5ba9f221fa22faadfecaa8f0baaefebf75
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727341"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>Proje Sistemlerini Genişletmeye Yönelik IDE Tanımlı Komutlar
Proje sistemlerini genişletmek istediğinizde, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE tarafından sunulan komutları ve komut gruplarını kullanabilirsiniz.

 Aşağıdaki bölümlerde, özellikle proje sistemlerini genişletmek için yararlı olan komut öğeleri listelenmektedir.

## <a name="command-menus"></a>Komut menüleri
 Aşağıdaki tabloda, bir proje genişletici 'i çağıran üst düzey komutları yerleştirmeniz için yararlı konumlar olan komut menüleri gösterilmektedir.

|Komut menüsü|Açıklama|
|------------------|-----------------|
|IDM_VS_MENU_PROJECT|**Projenin** üst düzey menüsü.|
|IDM_VS_TOOL_PROJWIN|**Çözüm Gezgini** araç çubuğu.|

## <a name="shortcut-menus"></a>Kısayol Menüleri
 Aşağıdaki tabloda, **Çözüm Gezgini**tek bir düğüm seçildiğinde veya **Çözüm Gezgini**birden çok Hogense seçimi olduğunda uygulanan kısayol menüleri gösterilmektedir. Bu, seçilen tüm düğümlerin aynı türden olduğu durumlar olur.

|Kısayol menüsü|Açıklama|
|-------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Proje düğümü seçildiğinde geçerlidir.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Bir dosya seçildiğinde geçerlidir.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Bir klasör seçildiğinde geçerlidir.|
|IDM_VS_CTXT_WEBREFFOLDER|Web başvurusu klasörü seçildiğinde geçerlidir.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|"Başvurular" olarak adlandırılan başvurular kök düğümü seçildiğinde geçerlidir.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Başvuru düğümleri seçildiğinde geçerlidir; Bunlar yalnızca derleme, COM ve proje başvuruları içerir. Web başvuruları içermez.|

 Aşağıdaki tabloda, **Çözüm Gezgini** seçimi birden çok hiyerarşinin yayıldığı zaman uygulanan kısayol menüleri gösterilmektedir.

|Kısayol menüsü|Açıklama|
|-------------------|-----------------|
|IDM_VS_CTXT_XPROJ_SLNPROJ|Geçerli seçim çözüm düğümünü ve kök proje düğümlerini içerdiğinde geçerlidir.|
|IDM_VS_CTXT_XPROJ_SLNITEM|Geçerli seçim çözüm düğümünü ve proje öğelerini içerdiğinde geçerlidir.|
|IDM_VS_CTXT_XPROJ_MULTIPROJ|Geçerli seçim yalnızca birden çok kök proje düğümünden oluşuyorsa geçerlidir.|
|IDM_VS_CTXT_XPROJ_PROJITEM|Geçerli seçim kök proje düğümlerinin ve proje öğelerinin bir karışımını içerdiğinde geçerlidir. Ek olarak, seçim çözüm düğümünü de içerebilir.|
|IDM_VS_CTXT_XPROJ_MULTIITEM|Geçerli seçim çözümdeki birden çok projeden proje öğeleri içerdiğinde veya aynı projede farklı türlerde öğeler seçildiğinde geçerlidir.|

## <a name="command-groups"></a>Komut grupları
 Aşağıdaki tabloda, projeleri genişlettiğinizde kullanabileceğiniz ve <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> kısayol menüsüyle erişebileceğiniz komut grupları gösterilmektedir.

|Komut grubu|Açıklama|
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
- [MenuCommands ve OleMenuCommands karşılaştırması](../../extensibility/menucommands-vs-olemenucommands.md)
- [Yeniden Kullanılabilir Düğme Grupları Oluşturma](../../extensibility/creating-reusable-groups-of-buttons.md)