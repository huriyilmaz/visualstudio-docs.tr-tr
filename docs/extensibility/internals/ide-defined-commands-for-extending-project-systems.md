---
title: Proje Sistemlerinin Genişletilmesi için IDE Tanımlı Komutlar | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 61c0b2924548f50ad650389e3ad81759be1986a4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707730"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>Proje Sistemlerini Genişletmeye Yönelik IDE Tanımlı Komutlar
Proje sistemlerini genişletmek istediğinizde, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE tarafından sağlanan komutları ve komut gruplarını kullanabilirsiniz.

 Aşağıdaki bölümlerde, proje sistemlerini genişletmek için özellikle yararlı olan komut öğeleri listelenir.

## <a name="command-menus"></a>Komut Menüleri
 Aşağıdaki tablo, proje genişletici çağıran üst düzey komutlar koymak için yararlı konumlar komut menüleri gösterir.

|Komut menüsü|Açıklama|
|------------------|-----------------|
|IDM_VS_MENU_PROJECT|**Proje** üst düzey menüsü.|
|IDM_VS_TOOL_PROJWIN|**Çözüm Gezgini** araç çubuğu.|

## <a name="shortcut-menus"></a>Kısayol Menüleri
 Aşağıdaki tablo, **Çözüm Gezgini'nde**tek bir düğüm seçildiğinde veya **Çözüm Gezgini'nde**birden çok homojen seçim olduğunda (seçili tüm düğümlerin aynı türde olduğu zaman) uygulanan kısayol menülerini gösterir.

|Kısayol menüsü|Açıklama|
|-------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Proje düğümü seçildiğinde geçerlidir.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Bir dosya seçildiğinde geçerlidir.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Bir klasör seçildiğinde geçerlidir.|
|IDM_VS_CTXT_WEBREFFOLDER|Web Başvuru klasörü seçildiğinde geçerlidir.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|"Başvurular" adlı başvurukök düğümü seçildiğinde geçerlidir.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Referans düğümleri seçildiğinde geçerlidir; bunlar yalnızca derleme, COM ve proje başvurularını içerir. Web başvurularını içermez.|

 Aşağıdaki tablo, **Çözüm Gezgini'ndeki** seçim birden çok hiyerarşiye yayıldığında uygulanan kısayol menülerini gösterir,

|Kısayol menüsü|Açıklama|
|-------------------|-----------------|
|IDM_VS_CTXT_XPROJ_SLNPROJ|Geçerli seçim çözüm düğümü ve kök proje düğümlerini içerdiğinde geçerlidir.|
|IDM_VS_CTXT_XPROJ_SLNITEM|Geçerli seçim çözüm düğümü ve proje öğelerini içerdiğinde geçerlidir.|
|IDM_VS_CTXT_XPROJ_MULTIPROJ|Geçerli seçim yalnızca birden çok kök proje düğümünden oluşuyorsa geçerlidir.|
|IDM_VS_CTXT_XPROJ_PROJITEM|Geçerli seçim kök proje düğümleri ve proje öğelerinin bir karışımını içeriyorsa geçerlidir. Ayrıca, seçim çözüm düğümü içerebilir.|
|IDM_VS_CTXT_XPROJ_MULTIITEM|Geçerli seçim, çözümdeki birden çok projeden proje öğeleri içeriyorsa veya aynı projede farklı türlerde öğeler seçildiğinde geçerlidir.|

## <a name="command-groups"></a>Komut Grupları
 Aşağıdaki tablo, projeleri genişletirken kullanabileceğiniz ve <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> kısayol menüsünden erişebileceğiniz komut gruplarını gösterir.

|Komut grubu|Açıklama|
|-------------------|-----------------|
|IDG_VS_CTXT_PROJECT_BUILD|Projeyi oluşturma, yeniden oluşturma ve dağıtma komutları.|
|IDG_VS_CTXT_COMPILELINK|Projeyi derlemek ve bağlamak için komutlar.|
|IDG_VS_CTXT_PROJECT_CONFIG|Proje yapılandırması ve oluşturma düzeni ayarlayan komutlar.|
|IDG_VS_CTXT_PROJECT_ADD|Projeye öğe ekleyen komutlar.|
|IDG_VS_CTXT_PROJECT_START|F5 anahtarıyla ilişkili başlangıç projesini ayarlayan komutlar.|
|IDG_VS_CTXT_PROJECT_SAVE|Proje öğelerini kaydetmek için komutlar.|
|IDG_VS_CTXT_PROJECT_DEBUG|Hata ayıklama komutları.|
|IDG_VS_CTXT_PROJECT_SCC|Kaynak denetimi için komutlar.|
|IDG_VS_CTXT_PROJECT_TRANSFER|Kesme, kopyalama ve yapıştırişlemleri için komutlar.|
|IDG_VS_CTXT_PROJECT_PROPERTIES|**Project Properties** iletişim kutusuna erişim sağlayan komutlar.|

## <a name="see-also"></a>Ayrıca bkz.

- [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Yeniden Kullanılabilir Düğme Grupları Oluşturma](../../extensibility/creating-reusable-groups-of-buttons.md)
