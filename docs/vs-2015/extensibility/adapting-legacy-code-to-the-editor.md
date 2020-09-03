---
title: Eski kodu düzenleyiciye uyarlatma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapters
ms.assetid: a208d38e-9bea-41c9-9fe2-38bd86a359cb
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0bb90723a72c10dbf6cfda5edd4aa68f71f1c6b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184916"
---
# <a name="adapting-legacy-code-to-the-editor"></a>Eski Kodu Düzenleyiciye Uyarlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio Düzenleyicisi, varolan kod bileşenlerinden erişebileceğiniz birçok özelliğe sahiptir. Aşağıdaki yönergelerde, düzenleyici işlevlerini kullanmak için bir VSPackage gibi, MEF olmayan bir bileşeni nasıl uyarlayacağınız gösterilmektedir. Yönergeler Ayrıca, hem yönetilen hem de yönetilmeyen koddaki düzenleyicinin hizmetlerini almak için bağdaştırıcıların nasıl kullanılacağını gösterir.  
  
## <a name="editor-adapters"></a>Düzenleyici bağdaştırıcıları  
 Düzenleyici bağdaştırıcıları veya dolgu, API 'de sınıfları ve arabirimleri kullanıma sunan düzenleyici nesneleri için sarmalayıcılardır <xref:Microsoft.VisualStudio.TextManager.Interop> . Düzenleyiciden, Visual Studio Kabuk komutları ve Düzenleyici Hizmetleri gibi düzenleyici olmayan hizmetler arasında geçiş yapmak için kullanabilirsiniz. (Bu, düzenleyicinin Şu anda Visual Studio 'da barındırılıyor.) Bağdaştırıcılar, eski düzenleyici ve dil hizmeti uzantılarının Visual Studio 'da doğru şekilde çalışmasını da sağlar.  
  
## <a name="using-editor-adapters"></a>Düzenleyici bağdaştırıcılarını kullanma  
 , <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> Yeni düzenleyici arabirimleri ve eski arabirimler arasında geçiş yapan Yöntemler ve ayrıca bağdaştırıcılar oluşturan yöntemler sağlar.  
  
 Bu hizmeti bir MEF bileşeni bölümünde kullanıyorsanız, hizmeti aşağıdaki şekilde içeri aktarabilirsiniz.  
  
```  
[Import(typeof(IVsEditorAdaptersFactoryService))]  
internal IVsEditorAdaptersFactoryService editorFactory;  
```  
  
 Bu hizmeti MEF olmayan bir bileşende kullanmak istiyorsanız, bu konunun ilerleyen kısımlarında yer alarak "MEF olmayan bir bileşende Visual Studio Düzenleyicisi Hizmetleri 'Ni kullanma" bölümündeki yönergeleri izleyin.  
  
## <a name="switching-between-the-new-editor-api-and-the-legacy-api"></a>Yeni Düzenleyici API 'SI ile eski API arasında geçiş yapma  
 Bir düzenleyici nesnesi ve eski arabirim arasında geçiş yapmak için aşağıdaki yöntemleri kullanın.  
  
|Yöntem|Dönüştürme|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetBufferAdapter%2A>|Bir <xref:Microsoft.VisualStudio.Text.ITextBuffer> öğesine dönüştürür <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> .|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDataBuffer%2A>|Bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> öğesine dönüştürür <xref:Microsoft.VisualStudio.Text.ITextBuffer> .|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDocumentBuffer%2A>|Bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> öğesine dönüştürür <xref:Microsoft.VisualStudio.Text.ITextBuffer> .|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetViewAdapter%2A>|Bir <xref:Microsoft.VisualStudio.Text.Editor.ITextView> öğesine dönüştürür <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetWpfTextView%2A>|Bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> öğesine dönüştürür <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> .|  
  
## <a name="creating-adapters"></a>Bağdaştırıcılar oluşturma  
 Eski arabirimler için bağdaştırıcılar oluşturmak üzere aşağıdaki yöntemleri kullanın.  
  
|Yöntem|Dönüştürme|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsCodeWindowAdapter%2A>|Oluşturur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> .|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>Belirtilen bir için oluşturur <xref:Microsoft.VisualStudio.Utilities.IContentType> .|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Oluşturur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> .|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferCoordinatorAdapter%2A>|Oluşturur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> .|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> için oluşturur <xref:Microsoft.VisualStudio.Text.Editor.ITextViewRoleSet> .|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Oluşturur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .|  
  
## <a name="creating-adapters-in-unmanaged-code"></a>Yönetilmeyen kodda bağdaştırıcılar oluşturma  
 Tüm bağdaştırıcı sınıfları yerel ortak oluşturulmuş tablo olarak kaydedilir ve işlevi kullanılarak oluşturulabilir `VsLocalCreateInstance()` .  
  
 Tüm bağdaştırıcılar, içindeki Vsshlids. h dosyasında tanımlanan GUID 'Ler kullanılarak oluşturulur. Visual Studio SDK yüklemesinin \VisualStudioIntegration\Common\Inc\ klasörü. VsTextBufferAdapter örneği oluşturmak için aşağıdaki kodu kullanın.  
  
```  
IVsTextBuffer *pBuf = NULL;  
VsLocalCreateInstance(CLSID_VsTextBuffer, NULL, CLSCTX_INPROC_SERVER, IID_IVsTextBuffer, (void**)&pBuf);  
```  
  
## <a name="creating-adapters-in-managed-code"></a>Yönetilen kodda bağdaştırıcılar oluşturma  
 Yönetilen kodda, bağdaştırıcıları yönetilmeyen kod için açıklanan şekilde birlikte oluşturabilirsiniz. Ayrıca, bağdaştırıcılar oluşturup bunlarla etkileşime girebilmenizi sağlayan bir MEF hizmeti de kullanabilirsiniz. Bu şekilde bir bağdaştırıcı almak, ortak oluşturduğunuz zaman daha ayrıntılı denetim imkanı sunar.  
  
#### <a name="to-create-an-adapter-for-ivstextview"></a>IVsTextView için bir bağdaştırıcı oluşturmak için  
  
1. Microsoft.VisualStudio.Editor.dll bir başvuru ekleyin. ' `CopyLocal` Nin olarak ayarlandığından emin olun `false` .  
  
2. <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>Aşağıdaki gibi örneğini oluşturun.  
  
    ```  
    using Microsoft.VisualStudio.Editor;  
    ...  
    IVsEditorAdaptersFactoryService adapterFactoryService = ComponentModel.GetService<IVsEditorAdaptersFactoryService>();  
    ```  
  
3. Yöntemini çağırın `CreateX()` .  
  
    ```  
    adapterFactoryService.CreateTextViewAdapter(textView);  
    ```  
  
## <a name="using-the-visual-studio-editor-directly-from-unmanaged-code"></a>Doğrudan yönetilmeyen koddan Visual Studio düzenleyicisini kullanma  
 Microsoft. VisualStudio. platform. VSEditor ad alanı ve Microsoft. VisualStudio. platform. VSEditor. Interop ad alanı COM çağrılabilir arabirimlerini IX * arabirimleri olarak kullanıma sunar. Örneğin, Microsoft. VisualStudio. platform. VSEditor. Interop. ıxtextbuffer arabirimi arabirimin COM sürümüdür <xref:Microsoft.VisualStudio.Text.ITextBuffer> . ' Den, `IVxTextBuffer` arabellek anlık görüntülerine erişim sağlayabilir, arabelleği değiştirebilir, arabellekteki metin değişikliği olaylarını dinleyebilir ve izleme noktaları ve yayılma alanları oluşturabilirsiniz. Aşağıdaki adımlarda, ' dan ' a nasıl erişebileceğiniz gösterilmektedir `IVxTextBuffer` `IVsTextBuffer` .  
  
#### <a name="to-get-an-ivxtextbuffer"></a>Ixtextbuffer almak için  
  
1. IX * arabirimlerinin tanımları, içindeki VSEditor. h dosyasıdır. Visual Studio SDK yüklemesinin \VisualStudioIntegration\Common\Inc\ klasörü.  
  
2. Aşağıdaki kod yöntemini kullanarak bir metin arabelleği oluşturur `IVsUserData->GetData()` . Aşağıdaki kodda, bir `pData` nesnesi işaretçisi olur `IVsUserData` .  
  
    ```  
    #include <textmgr.h>  
    #include <VSEditor.h>  
    #include <vsshlids.h>  
  
    CComPtr<IVsTextBuffer> pVsTextBuffer;  
    CComPtr<IVsUserData> pData;  
    CComPtr<IVxTextBuffer> pVxBuffer;  
    ...  
    if (SUCCEEDED(pVsTextBuffer->QueryInterface(IID_IVsUserData, &pData))  
    {  
        CComVariant vt;  
        if (SUCCEEDED(pData->GetData(GUID_VxTextBuffer, &vt)) &&  
        (vt.Type == VT_UNKNOWN) && (vt.punkVal != NULL))  
        {  
            vt.punkVal->QueryInterface(IID_IVxTextBuffer, (void**)&pVxBuffer);  
        }  
    }  
    ```  
  
## <a name="using-visual-studio-editor-services-in-a-non-mef-component"></a>MEF olmayan bir bileşende Visual Studio Düzenleyicisi hizmetlerini kullanma  
 MEF kullanmayan ve Visual Studio Düzenleyicisi 'nin hizmetlerini kullanmak istediğiniz mevcut bir yönetilen kod bileşenine sahipseniz, ComponentModelHost VSPackage içeren derlemeye bir başvuru eklemeniz ve onun SComponentModel hizmetini almanız gerekir.  
  
#### <a name="to-consume-visual-studio-editor-components-from-a-non-mef-component"></a>MEF olmayan bir bileşenden Visual Studio Düzenleyicisi bileşenlerini kullanmak için  
  
1. İçindeki Microsoft.VisualStudio.ComponentModelHost.dll derlemesine bir başvuru ekleyin. Visual Studio yüklemesinin \Common7\IDE\ klasörü. ' `CopyLocal` Nin olarak ayarlandığından emin olun `false` .  
  
2. `IComponentModel`Visual Studio Düzenleyicisi hizmetlerini kullanmak istediğiniz sınıfa aşağıdaki gibi özel bir üye ekleyin.  
  
    ```  
    using Microsoft.VisualStudio.ComponentModelHost;  
    ....  
    private IComponentModel componentModel;  
    ```  
  
3. Bileşeninizin başlatma yönteminde bileşen modelini oluşturun.  
  
    ```  
    componentModel =  
     (IComponentModel)Package.GetGlobalService(typeof(SComponentModel));  
    ```  
  
4. Bundan sonra, istediğiniz hizmet için yöntemini çağırarak Visual Studio Düzenleyicisi hizmetlerinden herhangi birini edinebilirsiniz `IComponentModel.GetService<T>()` .  
  
    ```  
    textBufferFactoryService =  
         componentModel.GetService<ITextBufferFactoryService>();     
    ```
