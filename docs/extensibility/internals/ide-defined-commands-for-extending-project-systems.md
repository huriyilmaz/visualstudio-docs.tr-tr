---
title: IDE-Defined Sistemlerini Genişletme komutlarını | Microsoft Docs
description: Proje sistemlerini genişletmek için kullanılan tümleşik Visual Studio ortamında (IDE) tanımlanan komutlar ve komut grupları hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4525802bf308d740ea5c468fac171e74bff2b34e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901168"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>Proje Sistemlerini Genişletmeye Yönelik IDE Tanımlı Komutlar
Proje sistemlerini genişletmek istediğiniz zaman, IDE tarafından sağlanan komutları ve komut gruplarını [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kullanabilirsiniz.

 Aşağıdaki bölümlerde, özellikle proje sistemlerini genişletmek için yararlı olan komut öğeleri listelemektedir.

## <a name="command-menus"></a>Komut Menüleri
 Aşağıdaki tabloda, proje genişleticisini çağıran üst düzey komutları koymak için kullanışlı konumlar olan komut menüleri yer almaktadır.

|Komut menüsü|Açıklama|
|------------------|-----------------|
|IDM_VS_MENU_PROJECT|**Proje üst** düzey menüsü.|
|IDM_VS_TOOL_PROJWIN|Araç **Çözüm Gezgini** çubuğu.|

## <a name="shortcut-menus"></a>Kısayol Menüleri
 Aşağıdaki **tabloda, Çözüm Gezgini**'de tek bir düğüm seçildiğinde veya Çözüm Gezgini'de birden çok homojen seçim olduğunda geçerli olan kısayol menüleri görüntülenir. Bu, seçilen tüm düğümlerin aynı türde olduğu durumdur.

|Kısayol menüsü|Açıklama|
|-------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Proje düğümü seçildiğinde geçerlidir.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Bir dosya seçildiğinde geçerlidir.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Bir klasör seçildiğinde geçerlidir.|
|IDM_VS_CTXT_WEBREFFOLDER|Web Başvurusu klasörü seçildiğinde geçerlidir.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|"Başvurular" adlı başvuru kök düğümü seçildiğinde geçerlidir.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Başvuru düğümleri seçildiğinde geçerlidir; Bunlar yalnızca derleme, COM ve proje başvurularını içerir. Web başvuruları dahil değildir.|

 Aşağıdaki tabloda, uygulamadaki seçim birden çok hiyerarşiye yay **Çözüm Gezgini** kısayol menüleri ve

|Kısayol menüsü|Açıklama|
|-------------------|-----------------|
|IDM_VS_CTXT_XPROJ_SLNPROJ|Geçerli seçim çözüm düğümünü ve kök proje düğümlerini içerdiğinde geçerlidir.|
|IDM_VS_CTXT_XPROJ_SLNITEM|Geçerli seçim çözüm düğümünü ve proje öğelerini içerdiğinde geçerlidir.|
|IDM_VS_CTXT_XPROJ_MULTIPROJ|Geçerli seçim yalnızca birden çok kök proje düğümünden oluşurken geçerlidir.|
|IDM_VS_CTXT_XPROJ_PROJITEM|Geçerli seçim kök proje düğümlerinin ve proje öğelerinin bir karışımını içerdiğinde geçerlidir. Ayrıca, seçim çözüm düğümünü içerebilir.|
|IDM_VS_CTXT_XPROJ_MULTIITEM|Geçerli seçim çözümdeki birden çok projeden proje öğeleri içerdiğinde veya aynı projede farklı türlerde öğeler seçildiğinde geçerlidir.|

## <a name="command-groups"></a>Komut Grupları
 Aşağıdaki tabloda, projeleri genişleterek kullanabileceğiniz ve kısayol menüsünden erişebilirsiniz komut grupları <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> yer alır.

|Komut grubu|Açıklama|
|-------------------|-----------------|
|IDG_VS_CTXT_PROJECT_BUILD|Projeyi oluşturma, yeniden oluşturma ve dağıtma komutları.|
|IDG_VS_CTXT_COMPILELINK|Projeyi derleme ve bağlama komutları.|
|IDG_VS_CTXT_PROJECT_CONFIG|Proje yapılandırmasını ve derleme siparişlerini ayaran komutlar.|
|IDG_VS_CTXT_PROJECT_ADD|Projeye öğe ekli komutlar.|
|IDG_VS_CTXT_PROJECT_START|F5 anahtarıyla ilişkili başlangıç projesini ayaran komutlar.|
|IDG_VS_CTXT_PROJECT_SAVE|Proje öğelerini kaydetme komutları.|
|IDG_VS_CTXT_PROJECT_DEBUG|Hata ayıklama komutları.|
|IDG_VS_CTXT_PROJECT_SCC|Kaynak denetimi için komutlar.|
|IDG_VS_CTXT_PROJECT_TRANSFER|Kesme, kopyalama ve yapıştırma işlemleri için komutlar.|
|IDG_VS_CTXT_PROJECT_PROPERTIES|Proje Özellikleri iletişim kutusuna **erişim sağlayan** komutlar.|

## <a name="see-also"></a>Ayrıca bkz.

- [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Yeniden Kullanılabilir Düğme Grupları Oluşturma](../../extensibility/creating-reusable-groups-of-buttons.md)
