---
title: Görsel Stüdyo Araç Çubuklarının GUID'leri ve T'leri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio groups
- toolbars
- visual studio toolbar
- id
- toolgar group
- tool window toolbar
- guid
ms.assetid: c9cacd57-9225-450f-a9ac-cbf3168ea844
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe42821cdacc038d767e52373d45ddd7b8954323
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708222"
---
# <a name="guids-and-ids-of-visual-studio-toolbars"></a>Visual Studio araç çubuklarının GUID'leri ve kılıkları
Bu konu, Visual Studio tümleşik geliştirme ortamında (IDE) bulunan araç çubuklarının ve içerdikleri grupların GUID ve kimlik değerlerini içerir. Bu değerler Visual Studio SDK'nın bir parçası olarak yüklenen *.vsct* dosyalarında tanımlanır. Daha fazla bilgi için [IDE tanımlı komutlar, menüler ve gruplara](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)bakın.

> [!NOTE]
> Visual Studio'nun kullanabileceği araç çubuklarının çoğu Visual Studio tarafından tanımlanmaz ve GUID ve kimlik değerleri herkese açık değildir. Bu konu yalnızca Visual Studio SDK *.vsct* dosyalarında tanımlanan araç çubuklarını listeler.

 *.vsct* dosyalarında tanımlanan IDE nesneleriile nasıl çalışılabilenler hakkında daha fazla bilgi için genişlet [menülerini ve komutlarını](../../extensibility/extending-menus-and-commands.md)görün.

 Visual Studio IDE tarafından sağlanan varsayılan araç `guidSHLMainMenu`çubukları, sözdizimi `GUID:ID` kullanılarak aksi belirtilmedikleri sürece GUID'i kullanır.

## <a name="ide-toolbars"></a>IDE araç çubukları
 Aşağıdaki araç çubukları Visual Studio IDE tarafından sağlanmaktadır. Araç çubukları **Araçlar** menüsünün Araç **Çubukları** alt menüsünde seçilerek görüntülenebilir. Araç pencerelerinde araç çubukları bu bölümde yer değildir.

 Yalnızca gruplar doğrudan araç çubuklarından inebilir. Bir grup eklemek için, üst öğesini araç çubuğunun GUID ve kimliğine ayarlayın. Araç çubuğuna düğme eklemek için, üst öğesini araç çubuğundaki bir gruba ayarlayın.

|Araç Çubuğu|Kimlik|
|-------------|--------|
|Standart|IDM_VS_TOOL_STANDARD|
|Yapı|IDM_VS_TOOL_BUILD|
|Metin düzenleyici|IDM_VS_TOOL_TEXTEDITOR|
|Hata ayıklama|guidVSDebugGroup:IDM_DEBUG_TOOLBAR|
|Hata ayıklama konumu|guidVSDebugGroup:IDM_DEBUG_CONTEXT_TOOLBAR|

### <a name="special-toolbars"></a>Özel araç çubukları
 Bu araç çubukları Visual Studio IDE tarafından tanımlanır, ancak özel işlevler hizmet ve komut grupları barındırmaz.

|Araç Çubuğu|Kimlik|
|-------------|--------|
|Add komutu|IDM_VS_TOOL_ADDCOMMAND|
|Tanımsız|IDM_VS_TOOL_UNDEFINED|
|XML şeması|IDM_VS_TOOL_SCHEMA|
|XML verileri|IDM_VS_TOOL_DATA|

## <a name="groups-on-the-ide-toolbars"></a>IDE araç çubuklarındaki gruplar
 Standart araç çubuğuna bir düğme eklemek için, aşağıdaki gruplardan birini üst öğesi olarak ayarlayın. Gruplar üst araç çubuğuna göre sıralanır.

### <a name="standard-toolbar-groups"></a>Standart araç çubuğu grupları

|Adı|Kimlik|
|----------|--------|
|Kaydet/Aç|IDG_VS_TOOLSB_SAVEOPEN|
|Kesme/Kopyalama|IDG_VS_TOOLSB_CUTCOPY|
|Geri/Yeniden Yap|IDG_VS_TOOLSB_UNDOREDO|
|Çalıştır/Oluştur|IDG_VS_TOOLSB_RUNBUILD|
|Arama|IDG_VS_TOOLSB_SEARCH|
|Windows|IDG_VS_TOOLSB_WINDOWS|
|Yeni pencereler|IDG_VS_TOOLSB_NEWWINDOWS|
|Yük/Kaydet|IDG_VS_WINDOWUI_LOADSAVE|
|Ölçer|IDG_VS_TOOLSB_GAUGE|

### <a name="build-toolbar-groups"></a>Araç çubuğu grupları oluşturma

|Adı|Kimlik|
|----------|--------|
|Çubuk oluştur|IDG_VS_BUILDBAR|
|İptal|IDG_VS_BUILD_CANCEL|

### <a name="text-editor-toolbar-groups"></a>Metin düzenleyiciaraç çubuğu grupları

|Adı|Kimlik|
|----------|--------|
|Tamamlama|IDM_VS_TOOL_TEXTEDITOR|
|Girinti|IDG_VS_EDITTOOLBAR_INDENT|
|Açıklama|IDG_VS_EDITTOOLBAR_COMMENT|
|Yer İşaretleri|IDG_VS_EDITTOOLBAR_TEMPBOOKMARKS|

### <a name="debug-toolbar-groups"></a>Hata ayıklama araç çubuğu grupları

|Adı|Kimlik|
|----------|--------|
|Yürütme|IDM_DEBUG_TOOLBAR|
|Adım|IDG_DEBUG_TOOLBAR_STEPPING|
|İzle|IDG_DEBUG_TOOLBAR_WATCH|
|Windows|IDG_DEBUG_TOOLBAR_WINDOWS|

### <a name="debug-location-toolbar-groups"></a>Hata ayıklama konum araç çubuğu grupları

|Adı|Kimlik|
|----------|--------|
|Hata ayıklama konumu|IDG_DEBUG_CONTEXT_TOOLBAR|

## <a name="tool-window-toolbars"></a>Araç penceresi araç çubukları
 Araç çubukları doğrudan IDE'de veya Çözüm **Gezgini**gibi araç pencerelerinde görünebilir. Araç pencereleri *.vsct* dosyalarında tanımlanmadığından, araç penceresi araç çubuklarında tanımlı ebeveynler yoktur. Bunun yerine, kod yerleştirilir. Aşağıdaki tabloda, IDE'deki araç pencerelerinde görünen araç çubuklarını ve içerdikleri komut gruplarını gösterilmektedir.

> [!NOTE]
> Araç çubukları ve grupları `guidSHLMainMenu`GUID:ID sözdizimini kullanarak aksi belirtilmedikleri sürece GUID'i kullanır. Araç çubuğu için GUID belirtildiğinde, bu araç çubuğundan gelen gruplar için de geçerlidir.

|Araç penceresi|Araç Çubuğu|Gruplar|
|-----------------|-------------|------------|
|Çözüm Gezgini|IDM_VS_TOOL_PROJWIN|IDG_VS_PROJ_TOOLBAR1... 5|
|Sunucu Gezgini|guid_SE_MenuGroup:IDM_SE_TOOLBAR_SERVEREXPLORER|IDG_SE_TOOLBAR_REFRESH|
|Özellikler|IDM_VS_TOOL_PROPERTIES|IDG_VS_PROPERTIES_SORT<br /><br /> IDG_VS_PROPERTIES_PAGES|
|Sınıf Görünümü|IDM_VS_TOOL_CLASSVIEW|IDG_VS_CLASSVIEW_FOLDERS<br /><br /> IDG_VS_CLASSVIEW_SEARCH<br /><br /> IDG_VS_CLASSVIEW_SETTINGS|
|Sınıf Görünümü|IDM_VS_TOOL_CLASSVIEW_GO|IDG_VS_CLASSVIEW_SEARCH2|
|Nesne Tarayıcısı|IDM_VS_TOOL_OBJBROWSER|IDG_VS_OBJBROWSER_SUBSETS<br /><br /> IDG_VS_OBJBROWSER_SEARCH<br /><br /> IDG_VS_OBJBROWSER_ADDREFERENCE<br /><br /> IDG_VS_OBJBROWSER_BROWSERSETTINGS|
|Nesne Tarayıcısı|IDM_VS_TOOL_OBJECT_BROWSER_GO|IDG_VS_OBJBROWSER_SEARCH2|
|Çıkış|IDM_VS_TOOL_OUTPUTWINDOW|IDG_VS_OUTPUTWINDOW_SELECT<br /><br /> IDG_VS_OUTPUTWINDOW_GOTO<br /><br /> IDG_VS_OUTPUTWINDOW_NEXTPREV<br /><br /> IDG_VS_OUTPUTWINDOW_CLEAR<br /><br /> IDG_VS_OUTPUTWINDOW_WORDWRAP|
|Bulma ve Değiştirme|IDM_VS_TOOL_UNIFIEDFIND|IDG_VS_FINDTAB<br /><br /> IDG_VS_REPLACETAB|
|Sonuçları Bul 1|IDM_VS_TOOL_FINDRESULTS1|IDG_VS_FINDRESULTS1_GOTO<br /><br /> IDG_VS_FINDRESULTS1_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS1_CLEAR<br /><br /> IDG_VS_FINDRESULTS1_STOPFIND|
|Sonuçları Bul 2|IDM_VS_TOOL_FINDRESULTS2|IDG_VS_FINDRESULTS2_GOTO<br /><br /> IDG_VS_FINDRESULTS2_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS2_CLEAR<br /><br /> IDG_VS_FINDRESULTS2_STOPFIND|
|Kod Parçacığı|IDM_VS_TOOL_SNIPPETMENUS|IDG_VS_SNIPPET_REPL<br /><br /> IDG_VS_SNIPPET_REF<br /><br /> IDG_VS_SNIPPET_PROP|
|Yer İşaretleri|IDM_VS_TOOL_BOOKMARKWIND|IDG_VS_BWNEWFOLDER<br /><br /> IDG_VS_BWNEXTBM<br /><br /> IDG_VS_BWNEXTBMF<br /><br /> IDG_VS_BWENABLE<br /><br /> IDG_VS_BWDELETE|
|Görev Listesi|IDM_VS_TOOL_TASKLIST|IDG_VS_TASKLIST_PROVIDERLIST|
|Kullanıcı Görevleri|IDM_VS_TOOL_USERTASKS|IDG_VS_TASKLIST_PROVIDERLIST<br /><br /> IDG_VS_USERTASKS_EDIT|
|Hata Listesi|IDM_VS_TOOL_ERRORLIST|IDG_VS_ERRORLIST_ERRORGROUP<br /><br /> IDG_VS_ERRORLIST_WARNINGGROUP<br /><br /> IDG_VS_ERRORLIST_MESSAGEGROUP|
|Tarayıcıyı Ara|IDM_VS_TOOL_CALLBROWSER1... 16|IDG_VS_TOOLBAR_CALLBROWSER1_ACTIONS<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_TYPE<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_CBSETTINGS|
|Kesme Noktaları|guidVSDebugGroup:IDM_BREAKPOINTS_WINDOW_TOOLBAR|IDG_BREAKPOINTS_WINDOW_NEW<br /><br /> IDG_BREAKPOINTS_WINDOW_DELETE<br /><br /> IDG_BREAKPOINTS_WINDOW_ALL<br /><br /> IDG_BREAKPOINTS_WINDOW_VIEW<br /><br /> IDG_BREAKPOINTS_WINDOW_EDIT<br /><br /> IDG_BREAKPOINTS_WINDOW_COLUMNS|
|Demontaj|guidVSDebugGroup:IDM_DISASM_WINDOW_TOOLBAR|IDG_DISASM_WINDOW_TOOLBAR|
|Bellek 1-4|guidVSDebugGroup:IDM_MEMORY_WINDOW_TOOLBAR1... 4|IDG_MEMORY_EXPRESSION1... 4<br /><br /> IDG_MEMORY_COLUMNS1... 4|
|İşlemler|guidVSDebugGroup:IDM_ATTACHED_PROCS_TOOLBAR|IDG_ATTACHED_PROCS_EXECCNTRL IDG_ATTACHED_PROCS_STEPPING<br /><br /> IDG_ATTACHED_PROCS_EXECCNTRL2<br /><br /> IDG_ATTACHED_PROCS_ATTACH<br /><br /> IDG_ATTACHED_PROCS_COLUMNS|

## <a name="see-also"></a>Ayrıca bkz.
- [Araç çubuğuna menü denetleyicisi ekleme](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)
- [Araç penceresine araç çubuğu ekleme](../../extensibility/adding-a-toolbar-to-a-tool-window.md)
- [Visual Studio menülerinin GUID'leri ve kılıkları](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)
