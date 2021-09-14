---
title: Araç Çubuklarının GUID'leri Visual Studio kimlikleri | Microsoft Docs
description: Tümleştirilmiş geliştirme ortamına (IDE) dahil edilen araç çubukları ve içerleri gruplar için GUID ve Visual Studio değerlerinin listesini görüntüleme.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- visual studio groups
- toolbars
- visual studio toolbar
- id
- toolgar group
- tool window toolbar
- guid
ms.assetid: c9cacd57-9225-450f-a9ac-cbf3168ea844
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 8ec564b6b4da3f9ee6cd706d1c6ab3796c03494f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725068"
---
# <a name="guids-and-ids-of-visual-studio-toolbars"></a>Araç çubuklarının GUID'Visual Studio kimlikleri
Bu konu, tümleşik geliştirme ortamına (IDE) ve içeren gruplara dahil edilen araç Visual Studio GUID ve kimlik değerlerini numaralandırmaktadır. Bu değerler, Visual Studio SDK'sı kapsamında yüklü olan *.vsct* dosyalarında tanımlanır. Daha fazla bilgi için bkz. [IDE tanımlı komutlar, menüler ve gruplar.](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)

> [!NOTE]
> Araç çubuklarının birçoğu Visual Studio tarafından tanımlanmaz Visual Studio GUID ve kimlik değerleri genel değildir. Bu konu başlığında yalnızca SDK *.vsct* dosyalarında Visual Studio araç çubukları listelanmıştır.

 *.vsct* dosyalarında tanımlanan IDE nesneleriyle çalışma hakkında daha fazla bilgi için [bkz. Menüleri ve komutları genişletme.](../../extensibility/extending-menus-and-commands.md)

 IDE tarafından sağlanan varsayılan araç Visual Studio, aksi takdirde söz dizimi kullanılarak belirtilenler dışında GUID `guidSHLMainMenu` `GUID:ID` kullanır.

## <a name="ide-toolbars"></a>IDE araç çubukları
 Aşağıdaki araç çubukları IDE'nin Visual Studio sağlanır. Araç çubukları, Araçlar menüsünün Araç Çubukları **alt** menüsünden seçerek **görüntülenebilir.** Araç pencerelerine araç çubukları bu bölüme dahil değildir.

 Doğrudan araç çubuklarından yalnızca gruplar azalan düzende olabilir. Grup eklemek için üst öğenin GUID'sini ve araç çubuğunun kimliğini ayarlayın. Bir araç çubuğuna düğme eklemek için üst öğesini araç çubuğundaki bir gruba ayarlayın.

|Araç Çubuğu|ID|
|-------------|--------|
|Standart|IDM_VS_TOOL_STANDARD|
|Oluşturma|IDM_VS_TOOL_BUILD|
|Metin düzenleyici|IDM_VS_TOOL_TEXTEDITOR|
|Hata Ayıklama|guidVSDebugGroup:IDM_DEBUG_TOOLBAR|
|Hata ayıklama konumu|guidVSDebugGroup:IDM_DEBUG_CONTEXT_TOOLBAR|

### <a name="special-toolbars"></a>Özel araç çubukları
 Bu araç çubukları IDE'Visual Studio tarafından tanımlanır, ancak özel işlevler sunar ve komut gruplarını barındırmaz.

|Araç Çubuğu|ID|
|-------------|--------|
|Add komutu|IDM_VS_TOOL_ADDCOMMAND|
|Tanımsız|IDM_VS_TOOL_UNDEFINED|
|XML şeması|IDM_VS_TOOL_SCHEMA|
|XML verileri|IDM_VS_TOOL_DATA|

## <a name="groups-on-the-ide-toolbars"></a>IDE araç çubuklarında gruplar
 Standart araç çubuğuna düğme eklemek için, aşağıdaki gruplardan birini üst grup olarak ayarlayın. Gruplar üst araç çubuğuna göre sıralanmış.

### <a name="standard-toolbar-groups"></a>Standart araç çubuğu grupları

|Name|ID|
|----------|--------|
|Kaydet/Aç|IDG_VS_TOOLSB_SAVEOPEN|
|Kes/Kopyala|IDG_VS_TOOLSB_CUTCOPY|
|Geri Al/Tekrarla|IDG_VS_TOOLSB_UNDOREDO|
|Çalıştırma/Derleme|IDG_VS_TOOLSB_RUNBUILD|
|Arayın|IDG_VS_TOOLSB_SEARCH|
|Windows|IDG_VS_TOOLSB_WINDOWS|
|Yeni pencereler|IDG_VS_TOOLSB_NEWWINDOWS|
|Yükle/Kaydet|IDG_VS_WINDOWUI_LOADSAVE|
|Ölçer|IDG_VS_TOOLSB_GAUGE|

### <a name="build-toolbar-groups"></a>Araç çubuğu grupları oluşturma

|Name|ID|
|----------|--------|
|Derleme çubuğu|IDG_VS_BUILDBAR|
|İptal|IDG_VS_BUILD_CANCEL|

### <a name="text-editor-toolbar-groups"></a>Metin düzenleyici araç çubuğu grupları

|Name|ID|
|----------|--------|
|Tamamlama|IDM_VS_TOOL_TEXTEDITOR|
|Girinti|IDG_VS_EDITTOOLBAR_INDENT|
|Yorum|IDG_VS_EDITTOOLBAR_COMMENT|
|Yer işaretleri|IDG_VS_EDITTOOLBAR_TEMPBOOKMARKS|

### <a name="debug-toolbar-groups"></a>Araç çubuğu gruplarında hata ayıklama

|Name|ID|
|----------|--------|
|Yürütme|IDM_DEBUG_TOOLBAR|
|Adım|IDG_DEBUG_TOOLBAR_STEPPING|
|İzle|IDG_DEBUG_TOOLBAR_WATCH|
|Windows|IDG_DEBUG_TOOLBAR_WINDOWS|

### <a name="debug-location-toolbar-groups"></a>Hata ayıklama konumu araç çubuğu grupları

|Name|ID|
|----------|--------|
|Hata ayıklama konumu|IDG_DEBUG_CONTEXT_TOOLBAR|

## <a name="tool-window-toolbars"></a>Araç penceresi araç çubukları
 Araç çubukları doğrudan IDE 'de veya **Çözüm Gezgini** gibi araç pencereleri içinde görünebilir. Araç pencereleri *. vsct* dosyalarında tanımlanmadığı için araç penceresi araç çubuklarının tanımlı üst öğeleri yok. Bunun yerine, kod içine yerleştirilir. Aşağıdaki tablo, IDE 'deki araç pencereleri ve içerdikleri komut grupları üzerinde görünen araç çubuklarını gösterir.

> [!NOTE]
> Araç çubukları ve gruplar GUID `guidSHLMainMenu` : ID sözdizimi kullanılarak BELIRTILMEDIKÇE GUID 'yi kullanır. Bir araç çubuğu için bir GUID belirtildiğinde, bu araç çubuğundan gelen gruplar için de geçerli olur.

|Araç penceresi|Araç Çubuğu|Gruplar|
|-----------------|-------------|------------|
|Çözüm Gezgini|IDM_VS_TOOL_PROJWIN|IDG_VS_PROJ_TOOLBAR1.. e|
|Sunucu Gezgini|guid_SE_MenuGroup: IDM_SE_TOOLBAR_SERVEREXPLORER|IDG_SE_TOOLBAR_REFRESH|
|Özellikler|IDM_VS_TOOL_PROPERTIES|IDG_VS_PROPERTIES_SORT<br /><br /> IDG_VS_PROPERTIES_PAGES|
|Sınıf Görünümü|IDM_VS_TOOL_CLASSVIEW|IDG_VS_CLASSVIEW_FOLDERS<br /><br /> IDG_VS_CLASSVIEW_SEARCH<br /><br /> IDG_VS_CLASSVIEW_SETTINGS|
|Sınıf Görünümü|IDM_VS_TOOL_CLASSVIEW_GO|IDG_VS_CLASSVIEW_SEARCH2|
|Nesne Tarayıcısı|IDM_VS_TOOL_OBJBROWSER|IDG_VS_OBJBROWSER_SUBSETS<br /><br /> IDG_VS_OBJBROWSER_SEARCH<br /><br /> IDG_VS_OBJBROWSER_ADDREFERENCE<br /><br /> IDG_VS_OBJBROWSER_BROWSERSETTINGS|
|Nesne Tarayıcısı|IDM_VS_TOOL_OBJECT_BROWSER_GO|IDG_VS_OBJBROWSER_SEARCH2|
|Çıktı|IDM_VS_TOOL_OUTPUTWINDOW|IDG_VS_OUTPUTWINDOW_SELECT<br /><br /> IDG_VS_OUTPUTWINDOW_GOTO<br /><br /> IDG_VS_OUTPUTWINDOW_NEXTPREV<br /><br /> IDG_VS_OUTPUTWINDOW_CLEAR<br /><br /> IDG_VS_OUTPUTWINDOW_WORDWRAP|
|Bulma ve Değiştirme|IDM_VS_TOOL_UNIFIEDFIND|IDG_VS_FINDTAB<br /><br /> IDG_VS_REPLACETAB|
|Sonuçları Bul 1|IDM_VS_TOOL_FINDRESULTS1|IDG_VS_FINDRESULTS1_GOTO<br /><br /> IDG_VS_FINDRESULTS1_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS1_CLEAR<br /><br /> IDG_VS_FINDRESULTS1_STOPFIND|
|Sonuçları bul 2|IDM_VS_TOOL_FINDRESULTS2|IDG_VS_FINDRESULTS2_GOTO<br /><br /> IDG_VS_FINDRESULTS2_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS2_CLEAR<br /><br /> IDG_VS_FINDRESULTS2_STOPFIND|
|Kod Parçacığı|IDM_VS_TOOL_SNIPPETMENUS|IDG_VS_SNIPPET_REPL<br /><br /> IDG_VS_SNIPPET_REF<br /><br /> IDG_VS_SNIPPET_PROP|
|Yer işaretleri|IDM_VS_TOOL_BOOKMARKWIND|IDG_VS_BWNEWFOLDER<br /><br /> IDG_VS_BWNEXTBM<br /><br /> IDG_VS_BWNEXTBMF<br /><br /> IDG_VS_BWENABLE<br /><br /> IDG_VS_BWDELETE|
|Görev Listesi|IDM_VS_TOOL_TASKLIST|IDG_VS_TASKLIST_PROVIDERLIST|
|Kullanıcı görevleri|IDM_VS_TOOL_USERTASKS|IDG_VS_TASKLIST_PROVIDERLIST<br /><br /> IDG_VS_USERTASKS_EDIT|
|Hata Listesi|IDM_VS_TOOL_ERRORLIST|IDG_VS_ERRORLIST_ERRORGROUP<br /><br /> IDG_VS_ERRORLIST_WARNINGGROUP<br /><br /> IDG_VS_ERRORLIST_MESSAGEGROUP|
|Çağrı Tarayıcısı|IDM_VS_TOOL_CALLBROWSER1.. k|IDG_VS_TOOLBAR_CALLBROWSER1_ACTIONS<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_TYPE<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_CBSETTINGS|
|Kesme noktaları|Gudvsdebuggroup: IDM_BREAKPOINTS_WINDOW_TOOLBAR|IDG_BREAKPOINTS_WINDOW_NEW<br /><br /> IDG_BREAKPOINTS_WINDOW_DELETE<br /><br /> IDG_BREAKPOINTS_WINDOW_ALL<br /><br /> IDG_BREAKPOINTS_WINDOW_VIEW<br /><br /> IDG_BREAKPOINTS_WINDOW_EDIT<br /><br /> IDG_BREAKPOINTS_WINDOW_COLUMNS|
|Ayrıştırılmış kod|Gudvsdebuggroup: IDM_DISASM_WINDOW_TOOLBAR|IDG_DISASM_WINDOW_TOOLBAR|
|Bellek 1-4|Gudvsdebuggroup: IDM_MEMORY_WINDOW_TOOLBAR1... 4|IDG_MEMORY_EXPRESSION1.. 4<br /><br /> IDG_MEMORY_COLUMNS1.. 4|
|İşlemler|Gudvsdebuggroup: IDM_ATTACHED_PROCS_TOOLBAR|IDG_ATTACHED_PROCS_EXECCNTRL IDG_ATTACHED_PROCS_STEPPING<br /><br /> IDG_ATTACHED_PROCS_EXECCNTRL2<br /><br /> IDG_ATTACHED_PROCS_ATTACH<br /><br /> IDG_ATTACHED_PROCS_COLUMNS|

## <a name="see-also"></a>Ayrıca bkz.
- [Araç çubuğuna menü denetleyicisi ekleme](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)
- [Araç penceresine araç çubuğu ekleme](../../extensibility/adding-a-toolbar-to-a-tool-window.md)
- [Visual Studio menülerinin guıd 'leri ve kimlikleri](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)
