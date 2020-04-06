---
title: IDE Sabitleri | Microsoft Dokümanlar
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- IDE, errors
- logical views
- errors [Visual Studio], IDE
- UI context constants
- constants, Visual Studio IDE
- IDE, constants
- physical views
ms.assetid: 5030e70a-241d-474a-ba8c-e3b1cf947ff0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc2eddac1cc7d7e616deb197752adf41a4d68d15
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710497"
---
# <a name="ide-constants"></a>IDE sabitleri

Sınıf, <xref:Microsoft.VisualStudio.VSConstants> tümleşik geliştirme ortamına (IDE) özgü ve daha önce yalnızca üstbilgi dosyalarında tanımlanan sabitler sağlar.

## <a name="logical-and-physical-views"></a>Mantıksal ve fiziksel görünümler

|Değer|Açıklama|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` işleyicileri iletişim kutusu ile <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> **aç** almak için yönteme bu değeri geçirmelidir, bu durumda olası kod görünümleri.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` işleyicileri iletişim kutusu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> **ile açık** almak için yönteme bu değeri geçmek, <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid> bu durumda aynı görünüme eşolası <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>hata ayıklama görünümleri ile doldurulur .|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Designer_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` işleyiciler bu değeri <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> iletişim **kutusuyla Aç'ı** almak için yönteme, bu durumda form tasarımcı görünümlerini **görüntüle'ye** geçirirler.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Primary_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` işleyiciler bu değeri <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> iletişim **kutusuyla Aç'ı** almak için yönteme geçirir, bu durumda düzenleyici fabrikasının varsayılan/birincil görünümü.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.TextView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` işleyiciler, bu değerin bir belge veya veri metni düzenleyicisi görünümü için iletişim <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> **kutusuyla Aç'ı** alma yöntemine iletir.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.UserChooseView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` işleyiciler bu değeri, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> kullanıcıdan hangi kullanıcı tanımlı görünümün kullanılacağını seçmesini gerektiren yönteme geçirir.|

## <a name="editor-factory-flags"></a>Editör Fabrika Bayrakları

|Değer|Açıklama|
|-----------|-----------------|
|[Cef. KlonDosya](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|Yöntemin ilk parametresi <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> olarak bit yönünde birleştirilmiş eski bir bayrak bayrağı.|
|[Cef. OpenAsNew](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenAsNew>)|Bitwise, yöntemin <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>ilk parametresi olarak kombine, bu düzenleyici fabrika gerekli düzeltmeleri gerçekleştirmek gerektiğini gösterir.|
|[Cef. Openfile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenFile>)|<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> Yöntemin ilk parametresi olarak bitwise kombine, bu bayrak cef birbirini [dışlar. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>).|
|[Cef. Sessiz](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_Silent>)|<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> Yöntemin ilk parametresi olarak bitwise kombine, bu düzenleyici fabrika bir kullanıcı arabirimi (UI) görüntülemeden düzenleyici oluşturmalı gösterir.|

## <a name="visual-studio-errors"></a>Visual Studio hataları

|Değer|Açıklama|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Söz konusu nesne zaten meşgul olduğunda, arabirimler tarafından eşzamanlı davranışa döndürülen sabit|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|"Uyumsuz belge verileri" için Visual Studio'ya özgü bir hata HRESULT'ı.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Visual Studio'ya özgü ve "Paket yüklenmedi" anlamına gelen bir hata HRESULT'ı.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Visual Studio'ya özgü ve "Proje zaten var olduğunu" gösteren bir hata HRESULT'ı.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Visual Studio'ya özgü ve "Project yapılandırması başarısız oldu" belirten bir hata HRESULT'ı.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Visual Studio'ya özgü ve "Project loaded değil" ibaresini gösteren bir hata HRESULT'ı.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Visual Studio'ya özgü ve "Çözüm zaten açık" olduğunu gösteren bir hata HRESULT'ı.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Visual Studio'ya özgü ve "Çözüm açık değil" diyen bir hata HRESULT'ı.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> Arabirimden bir dizi belirtmek için parametreleri olan yapı arabirimleri tarafından döndürülür, ancak uygulama yalnızca tüm çıktılara yöntem uygulayabilir.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|Belgenin <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> düzenleyicide açılamayacak bir biçimi varsa yöntem bu değeri döndürür.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|Kullanıcının Visual Studio sihirbazında arka düğmeye basdığını gösteren bir HRESULT değeri.|

## <a name="visual-studio-constants"></a>Visual Studio sabitleri

|Değer|Açıklama|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Visual Studio'ya özgü ve "Proje iletilir" ibaresini gösteren bir hata HRESULT'ı.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|Visual Studio'ya "Araç Kutusu işaretçisi" için özel olan bir sabit.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Görsel Stüdyo'ya özel bir sabit, yöntemin <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> başlangıcını gösteren yöntem le bir bildirim iletisi yayınlamak için.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Görsel Studio'ya özel bir sabit, yöntemin <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> sonunu gösteren yöntem aracılığıyla bir bildirim iletisi yayınlamak için.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Komut çubuğu ölçümlerinin değiştiğini belirten yöntem le <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> bir bildirim iletisi yayınlamak için Visual Studio'ya özgü bir sabit.|
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Visual Studio'ya özgü bir tanımlama bilgisinin ayarlanmadığını gösteren bir sabit.|
|[VSITEMID. Nil](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|Proje öğesinin yokluğunu temsil eden görsel stüdyo öğesi tanımlayıcısı. Geçerli seçim olmadığında bu değer kullanılır.|
|[VSITEMID. Kök](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|Proje hiyerarşisinin kökünü temsil eden ve tek bir öğenin aksine tüm hiyerarşiyi tanımlamak için kullanılan Görsel Stüdyo öğe tanımlayıcısı.|
|[VSITEMID. Seçim](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|Hiyerarşinin kökünü içerebilen, şu anda seçili öğeyi veya öğeleri temsil eden görsel stüdyo öğe tanımlayıcısı.|

## <a name="ivsselectionevents"></a>IVsSelectionEtkinlikler
 Örneğin, bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> çağrıda IDE'nin hangi bileşeninin seçildiğini açıklar.

|Sabit|Değer|
|--------------|-----------|
|[SelectionElement.DocumentFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0x2|
|[SelectionElement.PropertyBrowserSID](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0x4|
|[SelectionElement.StartupProject](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0x3|
|[SelectionElement.UndoManager](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0x0|
|[SelectionElement.UserContext](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0x5|
|[SelectionElement.WindowFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1|

## <a name="vsselelemid"></a>VSSELELEMID
 Yeni bir seçim durumunu belirtmek için kullanılan sabitler.

|Sabit|Değer|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|2|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|7|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|4|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|6|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|3|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|0|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|5|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|1|

## <a name="component-selector-dialog-constants"></a>Bileşen seçici iletişim sabitleri

|Sabit|Değer|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELCHANGED>|WM_USER + 1280|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELDBLCLICK>|WM_USER + 1281|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_CLEARSELECTION>|WM_USER + 1290|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_GETSELECTION>|WM_USER + 1287|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZELIST>|WM_USER + 1285|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZETAB>|WM_USER + 1288|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_QUERYCANSELECT>|WM_USER + 1286|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_SETMULTISELECT>|WM_USER + 1289|

## <a name="see-also"></a>Ayrıca bkz.

- [Proje sistemlerini genişletmek için IDE tanımlı komutlar](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
