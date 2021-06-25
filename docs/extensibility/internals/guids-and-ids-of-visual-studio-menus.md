---
title: Visual Studio Menülerinin GUID'leri ve | Microsoft Docs
description: Tümleşik geliştirme ortamına (IDE) dahil edilen menü çubuğundaki menüler Visual Studio GUID ve Visual Studio değerlerinin listesini görüntüleme.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- visual studio menus
- visual studio groups
- id
- existing menus
- guid
- menus
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bceee5fce8a77ad5169020bd3d21896bdbc71443
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898077"
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>Menülerin GUID'leri ve Visual Studio kimlikleri
Bu makalede, menü çubuğundaki menülerin ve grupların GUID ve Visual Studio numaralar. Bu değerler, Visual Studio SDK'sı kapsamında yüklü olan *.vsct* dosyalarında tanımlanır. Daha fazla bilgi için bkz. [IDE tanımlı komutlar, menüler ve gruplar.](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)

 *.vsct* dosyalarında tanımlanan tümleşik geliştirme ortamı (IDE) nesneleriyle çalışma hakkında daha fazla bilgi için [bkz. Menüleri](../../extensibility/extending-menus-and-commands.md)ve komutları genişletme.

 Menü çubuğundaki menüler ve Visual Studio GUID'lerini `guidSHLMainMenu` kullanır. Menü çubuğunun kendi kimliği `IDM_VS_TOOL_MAINMENU` vardır.

## <a name="groups-on-the-visual-studio-menu-bar"></a>Visual Studio menü çubuğundaki gruplar
 Menü çubuğuna menü eklemek için bu gruplardan birini üst öğe olarak ayarlayın.

|Grup|ID|
|-----------|--------|
|Dosya/Düzenle/Görüntüle|IDG_VS_MM_FILEEDITVIEW|
|Yeniden Düzenle|IDG_VS_MM_REFACTORING:|
|Project|IDG_VS_MM_PROJECT|
|Oluşturma|IDG_VS_MM_BUILDDEBUGRUN|
|Biçim/Araçlar|IDG_VS_MM_TOOLSADDINS|
|Pencere/Yardım/Topluluk|IDG_VS_MM_WINDOWHELP|
|Eklentiler|IDG_VS_MM_MACROS|
|FullScreenBar|IDG_VS_MM_FULLSCREENBAR|

## <a name="menus-on-the-visual-studio-menu-bar"></a>Menü çubuğundaki Visual Studio menüler
 Mevcut bir menüye grup Visual Studio için, aşağıdaki menülerden birini üst menü olarak ayarlayın. Altlar bu listeye dahil değildir.

|Menü|ID|
|----------|--------|
|Dosya|IDM_VS_MENU_FILE|
|Düzenle|IDM_VS_MENU_EDIT|
|Görünüm|IDM_VS_MENU_VIEW|
|Yeniden düzenleme|IDM_VS_MENU_REFACTORING|
|Project|IDM_VS_MENU_PROJECT|
|Oluşturma|IDM_VS_MENU_BUILD|
|Biçimlendir|IDM_VS_MENU_FORMAT|
|Araçlar|IDM_VS_MENU_TOOLS|
|Uzantıları|IDM_VS_MENU_EXTENSIONS|
|Pencere|IDM_VS_MENU_WINDOW|
|Eklentiler|IDM_VS_MENU_ADDINS|
|Topluluk|IDM_VS_MENU_COMMUNITY|
|Help|IDM_VS_MENU_HELP|

## <a name="groups-on-visual-studio-menus"></a>Menülerde Visual Studio gruplar
 Aşağıdaki listeler, doğrudan menü çubuğundaki menülerden azalan Visual Studio gösterir. Bir Visual Studio menüsüne komut eklemenin en hızlı yolu, bu gruplardan birini üst öğe olarak ayarlamaktır. Alt mlerden azalan gruplar bu bölümde görünmez.

### <a name="file-menu-groups"></a>Dosya menüsü grupları

|Grup|ID|
|-----------|--------|
|Yeni/Aç|IDG_VS_FILE_FILE|
|Ekle|IDG_VS_FILE_ADD|
|Çözüm|IDG_VS_FILE_SOLUTION|
|Çeşitli|IDG_VS_FILE_MISC|
|Kaydet|IDG_VS_FILE_SAVE|
|Rename|IDG_VS_FILE_RENAME|
|Tarayıcı|IDG_VS_FILE_BROWSER|
|Yazdır|IDG_VS_FILE_PRINT|
|En Son Kullanılan|IDG_VS_FILE_MRU|
|Taşı|IDG_VS_FILE_MOVE|
|Çıkış|IDG_VS_FILE_EXIT|

### <a name="edit-menu-groups"></a>Menü gruplarını düzenleme

|Grup|ID|
|-----------|--------|
|Geri Al/Tekrarla|IDG_VS_EDIT_UNDOREDO|
|Kes/Kopyala/Yapıştır|IDG_VS_EDIT_CUTCOPY|
|Şunu seçin:|IDG_VS_EDIT_SELECT|
|Goto|IDG_VS_EDIT_GOTO|
|Bul|IDG_VS_EDIT_FIND|
|Nesneler|IDG_VS_EDIT_OBJECTS|
|OLE fiilleri|IDG_VS_EDIT_OLEVERBS|
|Komut kutusu|IDG_VS_EDIT_COMMANDWELL|

### <a name="refactor-menu-groups"></a>Menü gruplarını yeniden Düzenle

|Grup|ID|
|-----------|--------|
|Common|IDG_REFACTORING_COMMON|
|Gelişmiş|IDG_REFACTORING_ADVANCED|

### <a name="view-menu-groups"></a>Menü gruplarını görüntüle

|Grup|ID|
|-----------|--------|
|Form kodu|IDG_VS_VIEW_FORMCODE|
|Tarayıcı|IDG_VS_VIEW_BROWSER|
|Görünümleri tanımlama|IDG_VS_VIEW_DEFINEVIEWS|
|Windows|IDG_VS_VIEW_WINDOWS|
|Pencereleri mimarın|IDG_VS_VIEW_ARCH_WINDOWS|
|Kuruluş pencereleri|IDG_VS_VIEW_ORG_WINDOWS|
|Kod tarayıcısı|IDG_VS_VIEW_CODEBROWSENAV_WINDOWS|
|Geliştirme pencereleri|IDG_VS_VIEW_DEV_WINDOWS|
|Araç Çubukları|IDG_VS_VIEW_TOOLBARS|
|Simgeleri|IDG_VS_VIEW_SYMBOLNAVIGATE|
|Gidin|IDG_VS_VIEW_NAVIGATE|
|Küçük gezinme|IDG_VS_VIEW_SMALLNAVIGATE|
|Nesne Tarayıcısı|IDG_VS_VIEW_OBJBRWSR|
|Komut kutusu|IDG_VS_VIEW_COMMANDWELL|
|Özellik Sayfaları|IDG_VS_VIEW_PROPPAGES|
|Yenile|IDG_VS_VIEW_REFRESH|

### <a name="project-menu-groups"></a>Proje menüsü grupları

|Grup|ID|
|-----------|--------|
|Çeşitli ekleme|IDG_VS_PROJ_MISCADD|
|Ekle|IDG_VS_PROJ_ADD|
|Klasör|IDG_VS_PROJ_FOLDER|
|Kaldırma/yeniden yükleme|IDG_VS_PROJ_UNLOADRELOAD|
|Başvuru|IDG_VS_PROJ_REFERENCE|
|Seçenekler|IDG_VS_PROJ_OPTIONS|
|Ayarlar|IDG_VS_PROJ_SETTINGS|

### <a name="build-menu-groups"></a>Yapı menüsü grupları

|Grup|ID|
|-----------|--------|
|Çözüm|IDG_VS_BUILD_SOLUTION|
|Seçim|IDG_VS_BUILD_SELECTION|
|Profil Temelli İyileştirme|IDG_VS_PGO_SELECTION|
|Çeşitli|IDG_VS_BUILD_MISC|
|İptal|IDG_VS_BUILD_CANCEL|

### <a name="tools-menu-groups"></a>Araçlar menüsü grupları

|Grup|ID|
|-----------|--------|
|Komut Satırı|IDG_VS_TOOLS_CMDLINE|
|Kod Parçacıkları|IDG_VS_TOOLS_SNIPPETS|
|Nesne alt kümesi|IDG_VS_TOOLS_OBJSUBSET|
|Seçenekler|IDG_VS_TOOLS_OPTIONS|
|Diğer 2|IDG_VS_TOOLS_OTHER2|
|Dış Araçlar|IDG_VS_TOOLS_EXT_TOOLS|
|Dış özelleştirmeler|IDG_VS_TOOLS_EXT_CUST|

### <a name="window-menu-groups"></a>Pencere menüsü grupları

|Grup|ID|
|-----------|--------|
|Yeni|IDG_VS_WINDOW_NEW|
|Yerleştirme/Kapatma|IDG_VS_DOCKCLOSE|
|Yerleştirme/Gizleme|IDG_VS_DOCKHIDE|
|Yerleştir|IDG_VS_WINDOW_ARRANGE|
|Gezinti|IDG_VS_WINDOW_NAVIGATION|
|Liste|IDG_VS_WINDOW_LIST|

### <a name="help-menu-groups"></a>Yardım menü grupları

|Grup|ID|
|-----------|--------|
|Örnekler|IDG_VS_HELP_SAMPLES|
|Destek|IDG_VS_HELP_SUPPORT|
|Hakkında|IDG_VS_HELP_ABOUT|

## <a name="submenus-of-visual-studio-menus"></a>Visual Studio menülerinin alt menüsü
 Aşağıdaki hiyerarşi, menü çubuğundaki menülerle ilişkili alt menüleri Visual Studio gösterir. Yalnızca bir grubun üst öğesi olarak bir menüye sahip olması nedeniyle, her alt menü doğrudan menüden değil, bir menüden aşağı doğru iner. Menüler, gruplar ve alt menüler arasındaki ilişki hakkında daha fazla bilgi için [bkz. Menüye alt menü ekleme.](../../extensibility/adding-a-submenu-to-a-menu.md)

> [!NOTE]
> Visual Studio menü çubuğundaki menülerin adları IDE'de grupların adlandırma kuralından alınamalarından dolayı bu hiyerarşide ayrı ayrı gösterilmez: *IDG_VS_ \<Menu Name\> _ \<Group Name\>*.

|Üst grup|Alt menü|Alt gruplar|
|------------------|-------------|------------------|
|IDG_VS_FILE_FILE|IDM_VS_CSCD_NEW|IDG_VS_FILE_NEW_CASCADE|
||IDM_VS_CSCD_OPEN|IDG_VS_FILE_OPENP_CASCADE|
|||IDG_VS_FILE_OPENF_CASCADE|
|IDG_VS_FILE_ADD|IDM_VS_CSCD_ADD|IDG_VS_FILE_ADD_PROJECT_NEW|
|||IDG_VS_FILE_ADD_PROJECT_EXI|
|IDG_VS_FILE_MRU|IDM_VS_CSCD_FILEMRU|IDG_VS_FILE_FMRU_CASCADE|
||IDM_VS_CSCD_PROJMRU|IDG_VS_FILE_PMRU_CASCADE|
|IDG_VS_FILE_MOVE|IDM_VS_CSCD_MOVETOPRJ|IDG_VS_FILE_MOVE_CASCADE|
|||IDG_VS_FILE_MOVE_PICKER|
|IDG_VS_VIEW_DEV_WINDOWS|IDM_VS_CSCD_FINDRESULTS|IDG_VS_WNDO_FINDRESULTS|
||IDM_VS_CSCD_WINDOWS|IDG_VS_VIEW_CALLBROWSER|
|||IDG_VS_WNDO_OTRWNDWS1... 6|
|||IDG_VS_WNDO_WINDOWS2|
|IDG_VS_VIEW_TOOLBARS|IDM_VS_CSCD_COMMANDBARS||
|IDG_VS_EDIT_GOTO|IDM_VS_EDITOR_FIND_MENU||
|IDG_VS_EDIT_OBJECTS|IDM_VS_CSCD_MNUDES|IDG_VS_MNUDES_INSERT|
|||IDG_VS_MNUDES_EDITNAMES|
||IDM_VS_CSCD_OLEVERBS|IDG_VS_EDIT_OLEVERBS|
|IDG_VS_BUILD_SELECTION|IDM_VS_CSCD_BUILD|IDG_VS_BUILD_CASCADE|
|||IDG_VS_BUILD_PROJPICKER|
||IDM_VS_CSCD_REBUILD|IDG_VS_REBUILD_CASCADE|
|||IDG_VS_REBUILD_PROJPICKER|
||IDM_VS_CSCD_PROJONLY|IDG_VS_PROJONLY_CASCADE|
||IDM_VS_CSCD_CLEAN|IDG_VS_CLEAN_CASCADE|
|||IDG_VS_CLEAN_PROJPICKER|
||IDM_VS_CSCD_DEPLOY|IDG_VS_DEPLOY_CASCADE|
|||IDG_VS_DEPLOY_PROJPICKER|
|IDG_VS_PGO_SELECTION|IDM_VS_CSCD_PGO_BUILD|IDG_VS_PGO_BUILD_CASCADE_BUILD|
|||IDG_VS_PGO_BUILD_CASCADE_RUN|

## <a name="see-also"></a>Ayrıca bkz.
- [Araç çubuklarının GUID'Visual Studio kimlikleri](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)
- [Visual Studio komutlarının GUID'leri ve kimlikleri](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)
- [Visual Studio tablosu (.vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
