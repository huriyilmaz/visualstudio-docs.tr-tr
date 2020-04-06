---
title: Görsel Stüdyo Menülerinin GUID'leri ve T'leri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio menus
- visual studio groups
- id
- existing menus
- guid
- menus
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a656d5cb9a126a9dc3988d70a290fceb3e56439e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708238"
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>Visual Studio menülerinin GUID'leri ve kılıkları
Bu makalede, Visual Studio menü çubuğundaki menü ve grupların GUID ve kimlik değerlerini kaydedebilirsiniz. Bu değerler Visual Studio SDK'nın bir parçası olarak yüklenen *.vsct* dosyalarında tanımlanır. Daha fazla bilgi için [IDE tanımlı komutlar, menüler ve gruplara](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)bakın.

 *.vsct* dosyalarında tanımlanan tümleşik geliştirme ortamı (IDE) nesneleri ile nasıl çalışacağıhakkında daha fazla bilgi için [bkz.](../../extensibility/extending-menus-and-commands.md)

 Visual Studio menü çubuğundaki menüler ve `guidSHLMainMenu`gruplar GUID'i kullanır. Menü çubuğunun `IDM_VS_TOOL_MAINMENU`kendisi nde bir kimlik var.

## <a name="groups-on-the-visual-studio-menu-bar"></a>Visual Studio menü çubuğundaki gruplar
 Menü çubuğuna menü eklemek için, bu gruplardan birini üst öğesi olarak ayarlayın.

|Grup|Kimlik|
|-----------|--------|
|Dosya/Edit/Görünüm|IDG_VS_MM_FILEEDITVIEW|
|Yeniden Düzenle|IDG_VS_MM_REFACTORING:|
|Project|IDG_VS_MM_PROJECT|
|Yapı|IDG_VS_MM_BUILDDEBUGRUN|
|Biçim/Araçlar|IDG_VS_MM_TOOLSADDINS|
|Pencere/Yardım/Topluluk|IDG_VS_MM_WINDOWHELP|
|Eklentiler|IDG_VS_MM_MACROS|
|FullScreenBar|IDG_VS_MM_FULLSCREENBAR|

## <a name="menus-on-the-visual-studio-menu-bar"></a>Visual Studio menü çubuğundaki menüler
 Varolan visual studio menüsüne bir grup eklemek için, aşağıdaki menülerden birini üst öğesi olarak ayarlayın. Alt menüler bu listeye dahil edilmez.

|Menü|Kimlik|
|----------|--------|
|Dosya|IDM_VS_MENU_FILE|
|Düzenle|IDM_VS_MENU_EDIT|
|Görüntüle|IDM_VS_MENU_VIEW|
|Yeniden Düzenleme (Refactor)|IDM_VS_MENU_REFACTORING|
|Project|IDM_VS_MENU_PROJECT|
|Yapı|IDM_VS_MENU_BUILD|
|Biçimlendir|IDM_VS_MENU_FORMAT|
|Araçlar|IDM_VS_MENU_TOOLS|
|Uzantıları|IDM_VS_MENU_EXTENSIONS|
|Pencere|IDM_VS_MENU_WINDOW|
|Eklentiler|IDM_VS_MENU_ADDINS|
|Topluluk|IDM_VS_MENU_COMMUNITY|
|Yardım|IDM_VS_MENU_HELP|

## <a name="groups-on-visual-studio-menus"></a>Visual Studio menülerinde gruplar
 Aşağıdaki listeler, Visual Studio menü çubuğundaki menülerden doğrudan gelen grupları gösterir. Visual Studio menüsüne komut eklemenin en hızlı yolu, bu gruplardan birini ebeveyn olarak ayarlamaktır. Alt menülerden gelen gruplar bu bölümde görünmez.

### <a name="file-menu-groups"></a>Dosya menü grupları

|Grup|Kimlik|
|-----------|--------|
|Yeni /Açık|IDG_VS_FILE_FILE|
|Ekle|IDG_VS_FILE_ADD|
|Çözüm|IDG_VS_FILE_SOLUTION|
|Çeşitli|IDG_VS_FILE_MISC|
|Kaydet|IDG_VS_FILE_SAVE|
|Rename|IDG_VS_FILE_RENAME|
|Tarayıcı|IDG_VS_FILE_BROWSER|
|Yazdır|IDG_VS_FILE_PRINT|
|En Son Kullanılanlar|IDG_VS_FILE_MRU|
|Taşı|IDG_VS_FILE_MOVE|
|Çık|IDG_VS_FILE_EXIT|

### <a name="edit-menu-groups"></a>Menü gruplarını edin

|Grup|Kimlik|
|-----------|--------|
|Geri/Yeniden Yap|IDG_VS_EDIT_UNDOREDO|
|Kes/Kopyala/Yapıştır|IDG_VS_EDIT_CUTCOPY|
|Şunu seçin:|IDG_VS_EDIT_SELECT|
|Goto|IDG_VS_EDIT_GOTO|
|Bul|IDG_VS_EDIT_FIND|
|Nesneler|IDG_VS_EDIT_OBJECTS|
|OLE Fiilleri|IDG_VS_EDIT_OLEVERBS|
|Komut Kuyusu|IDG_VS_EDIT_COMMANDWELL|

### <a name="refactor-menu-groups"></a>Menü gruplarını yeniden düzenleme

|Grup|Kimlik|
|-----------|--------|
|Common|IDG_REFACTORING_COMMON|
|Gelişmiş|IDG_REFACTORING_ADVANCED|

### <a name="view-menu-groups"></a>Menü gruplarını görüntüleme

|Grup|Kimlik|
|-----------|--------|
|Form Kodu|IDG_VS_VIEW_FORMCODE|
|Tarayıcı|IDG_VS_VIEW_BROWSER|
|Görünümleri Tanımla|IDG_VS_VIEW_DEFINEVIEWS|
|Windows|IDG_VS_VIEW_WINDOWS|
|Mimar Pencereler|IDG_VS_VIEW_ARCH_WINDOWS|
|Kuruluş Pencereleri|IDG_VS_VIEW_ORG_WINDOWS|
|Kod Tarayıcı|IDG_VS_VIEW_CODEBROWSENAV_WINDOWS|
|Dev Windows|IDG_VS_VIEW_DEV_WINDOWS|
|Araç Çubukları|IDG_VS_VIEW_TOOLBARS|
|Simgeleri|IDG_VS_VIEW_SYMBOLNAVIGATE|
|Gidin|IDG_VS_VIEW_NAVIGATE|
|Küçük Gezinme|IDG_VS_VIEW_SMALLNAVIGATE|
|Nesne Tarayıcısı|IDG_VS_VIEW_OBJBRWSR|
|Komut Kuyusu|IDG_VS_VIEW_COMMANDWELL|
|Özellik Sayfaları|IDG_VS_VIEW_PROPPAGES|
|Yenile|IDG_VS_VIEW_REFRESH|

### <a name="project-menu-groups"></a>Proje menü grupları

|Grup|Kimlik|
|-----------|--------|
|Çeşitli Ekle|IDG_VS_PROJ_MISCADD|
|Ekle|IDG_VS_PROJ_ADD|
|Klasör|IDG_VS_PROJ_FOLDER|
|Boşaltma/Yeniden Yükleme|IDG_VS_PROJ_UNLOADRELOAD|
|Başvuru|IDG_VS_PROJ_REFERENCE|
|Seçenekler|IDG_VS_PROJ_OPTIONS|
|Ayarlar|IDG_VS_PROJ_SETTINGS|

### <a name="build-menu-groups"></a>Menü grupları oluşturma

|Grup|Kimlik|
|-----------|--------|
|Çözüm|IDG_VS_BUILD_SOLUTION|
|Seçim|IDG_VS_BUILD_SELECTION|
|Profil Temelli İyileştirme|IDG_VS_PGO_SELECTION|
|Çeşitli|IDG_VS_BUILD_MISC|
|İptal|IDG_VS_BUILD_CANCEL|

### <a name="tools-menu-groups"></a>Araçlar menü grupları

|Grup|Kimlik|
|-----------|--------|
|Komut Satırı|IDG_VS_TOOLS_CMDLINE|
|Kod Parçacıkları|IDG_VS_TOOLS_SNIPPETS|
|Nesne Alt Kümesi|IDG_VS_TOOLS_OBJSUBSET|
|Seçenekler|IDG_VS_TOOLS_OPTIONS|
|Diğer 2|IDG_VS_TOOLS_OTHER2|
|Harici Araçlar|IDG_VS_TOOLS_EXT_TOOLS|
|Dış Özelleştirmeler|IDG_VS_TOOLS_EXT_CUST|

### <a name="window-menu-groups"></a>Pencere menü grupları

|Grup|Kimlik|
|-----------|--------|
|Yeni|IDG_VS_WINDOW_NEW|
|Dock/Kapat|IDG_VS_DOCKCLOSE|
|Dock /Gizle|IDG_VS_DOCKHIDE|
|Yerleştir|IDG_VS_WINDOW_ARRANGE|
|Gezinti|IDG_VS_WINDOW_NAVIGATION|
|Liste|IDG_VS_WINDOW_LIST|

### <a name="help-menu-groups"></a>Yardım menüsü grupları

|Grup|Kimlik|
|-----------|--------|
|Örnekler|IDG_VS_HELP_SAMPLES|
|Destek|IDG_VS_HELP_SUPPORT|
|Hakkında|IDG_VS_HELP_ABOUT|

## <a name="submenus-of-visual-studio-menus"></a>Visual Studio menülerinin alt menüleri
 Aşağıdaki hiyerarşi, Visual Studio menü çubuğundaki menülerle ilişkili alt menüleri gösterir. Yalnızca bir grubun üst menüsü olabileceğinden, her alt menünün doğrudan menüden değil, menüdeki bir gruptan inmesi gerekir. Menüler, gruplar ve alt menüler arasındaki ilişki hakkında daha fazla bilgi için [bkz.](../../extensibility/adding-a-submenu-to-a-menu.md)

> [!NOTE]
> Visual Studio menü çubuğundaki menülerin adları bu hiyerarşide ayrı olarak gösterilmez, çünkü Bunlar IDE'deki gruplar için adlandırma kuralından çıkarılabilirler: *IDG_VS_\<Menü Adı\>_\<Grup Adı\>*.

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
- [Visual Studio araç çubuklarının GUID'leri ve kılıkları](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)
- [Visual Studio komutlarının GUID'leri ve kılıkları](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)
- [Visual Studio komut tablosu (.vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
