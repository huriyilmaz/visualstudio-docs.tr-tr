---
title: IDE Sabitleri | Microsoft Docs
description: VSConstants sınıfı, IDE'ye özgü sabitler sağlar ve daha önce yalnızca üst bilgi dosyalarında tanımlanmıştır.
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
ms.openlocfilehash: 4cdec9bea2883e67bf9ff2383319b966b4b73d8caeab7f6c92b1faaf3878fb8d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359864"
---
# <a name="ide-constants"></a>IDE sabitleri

sınıfı, tümleşik geliştirme ortamına (IDE) özgü ve önceden yalnızca üst bilgi dosyalarında tanımlanmış <xref:Microsoft.VisualStudio.VSConstants> sabitler sağlar.

## <a name="logical-and-physical-views"></a>Mantıksal ve fiziksel görünümler

|Değer|Açıklama|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>işleyiciler, bu değeri yöntemine ile Aç iletişim kutusunu (bu durumda olası `cmdidOpenWith` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> kod görünümlerini) almak için yöntemine iletir. |
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>işleyiciler bu değeri yöntemine ile aç iletişim kutusunu almak için yöntemine iletir. Bu durumda, ile aynı görünüme eşilen olası hata ayıklama `cmdidOpenWith` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> görünümleri  <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid> <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid> doldurulur.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Designer_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>işleyiciler bu değeri yöntemine ile Aç iletişim kutusunu `cmdidOpenWith` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> (bu durumda Form tasarımcısı **görünümlerini görüntüleme)** almak için yöntemine iletir. |
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Primary_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>işleyiciler bu değeri yöntemine ile Aç iletişim kutusunu (bu durumda düzenleyici fabrikasının varsayılan/birincil görünümünü) `cmdidOpenWith` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> almak için yöntemine iletir. |
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.TextView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>işleyiciler bu değeri yöntemine ile aç iletişim kutusunu almak için bu değeri bir belge veya veri `cmdidOpenWith` metin düzenleyicisi görünümü için buraya <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> iletir. |
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.UserChooseView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>işleyiciler bu değeri yöntemine iletir ve `cmdidOpenWith` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> kullanıcıdan hangi kullanıcı tanımlı görünümün kullanılamayacaklarını seçmesini istenir.|

## <a name="editor-factory-flags"></a>Düzenleyici Fabrika Bayrakları

|Değer|Açıklama|
|-----------|-----------------|
|[Cef. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|Yöntemin ilk parametresi olarak bit olarak birleştirilmiş eski bir <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> bayrak.|
|[Cef. OpenAsNew](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenAsNew>)|, yönteminin ilk parametresi olarak bit olarak <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> birleştirildi, bu düzenleyici fabrikasının gerekli düzeltmeleri gerçekleştirmesi gerektiğini gösterir.|
|[Cef. Openfile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenFile>)|Bit olarak yönteminin ilk parametresi olarak bir <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> araya gelen bu bayrak, CEF'nin birbirini [dışlar. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>).|
|[Cef. Sessiz](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_Silent>)|Yöntemin ilk parametresi olarak bit olarak bir araya gelen bu, düzenleyici fabrikasının bir kullanıcı arabirimi (UI) görüntülemeden <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> düzenleyiciyi oluşturması gerektiğini gösterir.|

## <a name="visual-studio-errors"></a>Visual Studio hataları

|Değer|Açıklama|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Söz konusu nesne zaten meşgul olduğunda arabirimler tarafından zaman uyumsuz davranışa döndürülen sabit|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|"Uyumsuz belge verileri" için özel Visual Studio HRESULT hatası.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|"Paket yüklenmedi" iletisini gösteren Visual Studio HRESULT hatası.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Hata HRESULT özeldir Visual Studio ve "Project zaten var olduğunu gösterir."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Hata HRESULT özeldir ve "Visual Studio yapılandırma başarısız oldu" Project belirtir.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Hata HRESULT özeldir Visual Studio ve "Project değil."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|"Çözüm zaten açık" iletisini gösteren Visual Studio HRESULT hatası.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|"Çözüm açık değil" iletisini gösteren Visual Studio HRESULT hatası.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|Arabiriminden dizi belirtme parametrelerine sahip derleme arabirimleri tarafından döndürülür, ancak uygulama yalnızca <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> yöntemini tüm çıkışlara uygulayabilir.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|Belge <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> düzenleyicide açılamıyor bir biçime sahipse yöntemi bu değeri döndürür.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|Kullanıcının bir uygulama sihirbazında geri düğmesine basmış olduğunu gösteren bir HRESULT Visual Studio.|

## <a name="visual-studio-constants"></a>Visual Studio sabitleri

|Değer|Açıklama|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Hata HRESULT özeldir ve "Visual Studio iletildi" Project gösterir.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|"Araç kutusu işaretçisi" Visual Studio özel sabit.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Kalıcılık başlangıcını Visual Studio yöntemi aracılığıyla bir bildirim iletisi yayınlamaya özel bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> sabit.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Kalıcılık sonunu Visual Studio yöntemi aracılığıyla bir bildirim iletisi yayınlamaya <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> özel bir sabit.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Komut çubuğu ölçümlerinin değiştiğini Visual Studio yöntemi aracılığıyla bir bildirim iletisi yayınlamaya özel bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> sabit.|
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Tanımlama bilgisinin ayar Visual Studio özel sabit.|
|[VSITEMID. Nil](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|Proje Visual Studio olmamasını temsil eden bir öğe tanımlayıcısı. Bu değer, geçerli seçim mevcut değilken kullanılır.|
|[VSITEMID. Kök](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|Bir Visual Studio proje hiyerarşisinin kökünü temsil eden ve tek bir öğe yerine hiyerarşinin tamamını tanımlamak için kullanılan bir öğe tanımlayıcısı.|
|[VSITEMID. Seçim](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|Hiyerarşinin Visual Studio dahil olmak üzere seçili öğeyi veya öğeleri temsil eden bir öğe tanımlayıcısı.|

## <a name="ivsselectionevents"></a>IVsSelectionEvents
 Örneğin, bir çağrıda IDE'nin hangi bileşeninin <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> seçili olduğunu açıklar.

|Sabit|Değer|
|--------------|-----------|
|[SelectionElement.DocumentFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0x2|
|[SelectionElement.PropertyBrowserSID](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0x4|
|[SelectionElement.StartupProject](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0x3|
|[SelectionElement.UndoManager](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0x0|
|[SelectionElement.UserContext](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0x5|
|[SelectionElement.WindowFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1|

## <a name="vsselelemid"></a>VSSELELEMID
 Yeni seçim durumunu belirtmek için kullanılan sabitler.

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

## <a name="component-selector-dialog-constants"></a>Bileşen seçici iletişim kutusu sabitleri

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
