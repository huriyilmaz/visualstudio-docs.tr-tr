---
title: IDE sabitleri | Microsoft Docs
description: Vssabitleri sınıfı, IDE 'ye özel sabitler sağlar ve daha önce yalnızca üst bilgi dosyalarında tanımlanmış.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: reference
helpviewer_keywords:
- IDE, errors
- logical views
- errors [Visual Studio], IDE
- UI context constants
- constants, Visual Studio IDE
- IDE, constants
- physical views
ms.assetid: 5030e70a-241d-474a-ba8c-e3b1cf947ff0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ad1d6e159ac1e008112a97bdec76fe2f791433ba
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626211"
---
# <a name="ide-constants"></a>IDE sabitleri

<xref:Microsoft.VisualStudio.VSConstants>Sınıfı, tümleşik geliştirme ortamına (IDE) özgü ve daha önce yalnızca başlık dosyalarında tanımlanmış sabitler sağlar.

## <a name="logical-and-physical-views"></a>Mantıksal ve fiziksel görünümler

|Değer|Açıklama|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`işleyiciler bu değeri <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> , olası kod görünümlerinde Bu örnekte, **birlikte Aç** iletişim kutusunu almak için yöntemine iletmelidir.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`işleyiciler, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> **birlikte Aç** iletişim kutusunu almak için bu değeri yönteme iletir. Bu durumda, bu örnekte, ile <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid> aynı görünüme eşlenen olası hata ayıklama görünümleri ile doldurulur <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid> .|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Designer_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`işleyiciler <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> , form Tasarımcısı görünümlerini **görüntülemek** Için bu değeri, **birlikte Aç** iletişim kutusunu almak üzere yöntemine iletir.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Primary_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`işleyiciler <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> , **birlikte Aç** iletişim kutusunu almak için bu değeri yönteme iletir, bu durumda düzenleyici fabrikasının varsayılan/birincil görünümüdür.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.TextView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`işleyiciler, bu değeri <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> bir belge veya veri metni Düzenleyicisi görünümünde **birlikte Aç** iletişim kutusunu almak için yöntemine iletir.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.UserChooseView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`işleyiciler <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> , kullanıcıdan kullanılacak kullanıcı tanımlı görünümü seçmesini isteyen yöntemine bu değeri iletir.|

## <a name="editor-factory-flags"></a>Düzenleyici Fabrika bayrakları

|Değer|Açıklama|
|-----------|-----------------|
|[CEF. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|Eski bir bayrak, yöntemin ilk parametresi olarak bit seviyesinde Birleşik bit <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> .|
|[CEF. OpenAsNew](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenAsNew>)|, Yönteminin ilk parametresi olarak bit düzeyinde birleştirildi, <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> Bu, düzenleyici fabrikasının gerekli düzeltmeleri gerçekleştirmesi gerektiğini gösterir.|
|[CEF. Açıksa](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenFile>)|Yöntemin ilk parametresi olarak bit seviyesinde Birleşik bit düzeyinde <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> , bu bayrak CEF 'nin birbirini dışlar [. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>).|
|[CEF. Katılımı](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_Silent>)|Yöntemin ilk parametresi olarak bit seviyesinde Birleşik bit düzeyinde <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> , bu, düzenleyici fabrikasının bir kullanıcı arabirimi (UI) görüntülemeden düzenleyiciyi oluşturması gerektiğini gösterir.|

## <a name="visual-studio-errors"></a>Visual Studio hataları

|Değer|Açıklama|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Söz konusu nesne zaten meşgul olduğunda, zaman uyumsuz davranışa arabirimler tarafından döndürülen bir sabit|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|"uyumsuz belge verileri" için Visual Studio özel bir HRESULT hatası.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Visual Studio özel ve "paket yüklenmedi" olduğunu belirten bir HRESULT hatası.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Visual Studio 'e özgü ve "Project zaten var olduğunu belirten bir HRESULT hatası.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Visual Studio özel ve "Project yapılandırma başarısız oldu" olduğunu belirten bir HRESULT hatası.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Visual Studio özel ve "Project yüklenmedi" olduğunu belirten bir HRESULT hatası.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Visual Studio özel ve "çözümün zaten açık olduğunu" belirten bir HRESULT hatası.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Visual Studio özel ve "çözüm açık değil." belirten bir HRESULT hatası.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|Arabirimden bir dizi belirtmek için parametrelere sahip derleme arabirimleri tarafından döndürülür <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> , ancak uygulama yalnızca tüm çıkışlara yöntemi uygulayabilir.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>Belge düzenleyicide açılamadığı bir biçime sahipse, bu değeri döndürür.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|kullanıcının Visual Studio sihirbazında geri düğmesine geçtiğini belirten bir HRESULT değeri.|

## <a name="visual-studio-constants"></a>Visual Studio sabitleri

|Değer|Açıklama|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Visual Studio özel ve "Project iletildi" belirten bir HRESULT hatası.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|bir "araç kutusu işaretleyicisi için Visual Studio özgü bir sabit."|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|modül başlangıcını belirten yöntemi aracılığıyla bir bildirim iletisi yayınlamak için Visual Studio özgü bir sabit <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> .|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|modül sonunu belirten yöntemi aracılığıyla bir bildirim iletisi yayınlamak için Visual Studio özgü bir sabit <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> .|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A>komut çubuğu ölçümlerinin değiştiğini belirten yöntemi aracılığıyla bir bildirim iletisi yayınlamak için Visual Studio özgü bir sabit.|
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|bir tanımlama bilgisinin ayarlanmadığını belirten Visual Studio özgü bir sabit.|
|[VSITEMID. Boş](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|bir proje öğesinin yokluğunu temsil eden Visual Studio öğesi tanımlayıcısı. Bu değer, geçerli seçim olmadığında kullanılır.|
|[VSITEMID. Asıl](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|bir proje hiyerarşisinin kökünü temsil eden ve tek bir öğe yerine tüm hiyerarşiyi tanımlamak için kullanılan bir Visual Studio öğesi tanımlayıcısı.|
|[VSITEMID. Seçimi](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|hiyerarşinin kökünü içerebilen şu anda seçili olan öğeyi veya öğeleri temsil eden bir Visual Studio öğesi tanımlayıcısı.|

## <a name="ivsselectionevents"></a>IVsSelectionEvents
 Örneğin, bir çağrıda IDE 'nin hangi bileşenin seçili olduğunu açıklar <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> .

|Sabit|Değer|
|--------------|-----------|
|[SelectionElement. Belgeçerçevesi](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0x2|
|[SelectionElement. PropertyBrowserSID](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|4,|
|[SelectionElement. StartupProject](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0x3|
|[SelectionElement. UndoManager](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|'dır|
|[SelectionElement. UserContext](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0x5|
|[SelectionElement. WindowFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1|

## <a name="vsselelemid"></a>VSSELELIMON KIMLIĞI
 Yeni bir seçim durumunu göstermek için kullanılan sabitler.

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

## <a name="component-selector-dialog-constants"></a>Bileşen Seçici iletişim kutusu sabitleri

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
