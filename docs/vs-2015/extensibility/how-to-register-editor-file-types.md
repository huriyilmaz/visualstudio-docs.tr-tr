---
title: 'Nasıl yapılır: düzenleyici dosya türlerini kaydetme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register file types
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8d22e61d88b5f6e3959a369f6957efbc824384b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204112"
---
# <a name="how-to-register-editor-file-types"></a>Nasıl Yapılır: Düzenleyici Dosya Türlerini Kaydetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Düzenleyici dosya türlerini kaydetmek için en kolay yol, [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] yönetilen paket çerçevesi (MPF) sınıflarının bir parçası olarak sağlanmış kayıt özniteliklerini kullanmaktır. Paketinizi yerel olarak uygulamadıysanız [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] , düzenleyicinizi ve ilişkili uzantıları kaydeden bir kayıt defteri betiği de yazabilirsiniz.  
  
## <a name="registration-using-mpf-classes"></a>MPF sınıfları kullanarak kayıt  
  
#### <a name="to-register-editor-file-types-using-mpf-classes"></a>MPF sınıfları kullanarak düzenleyici dosya türlerini kaydetmek için  
  
1. <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute>VSPackage sınıfının sınıfında düzenleyiciniz için uygun parametreleri sağlayın.  
  
    ```  
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,   
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",   
         TemplateDir = "..\\..\\Templates",   
         NameResourceID = 106)]  
    ```  
  
     Burada ". Örnek ", bu düzenleyici için kayıtlı olan uzantıdır ve" 32 "öncelik düzeyidir.  
  
     , `projectGuid` İçinde tanımlanan çeşitli dosya türlerinin GUID 'sidir <xref:Microsoft.VisualStudio.VSConstants.CLSID.MiscellaneousFilesProject_guid> . Çeşitli dosya türü, sonuçta elde edilen dosya yapı sürecinin bir parçası olarak kalmayacak şekilde sağlanır.  
  
     `TemplateDir` yönetilen temel düzenleyici örneğine dahil edilen şablon dosyalarını içeren klasörü temsil eder.  
  
     `NameResourceID` , BasicEditorUI projesinin resources. h dosyasında tanımlanır ve düzenleyiciyi "düzenleyicim" olarak tanımlar.  
  
2. Yöntemini geçersiz kılın <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> .  
  
     Yöntemi uygulamanızda, <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> yöntemi çağırın ve Düzenleyici fabrikanızın örneğini aşağıda gösterildiği gibi geçirin.  
  
    ```  
    protected override void Initialize()  
    {  
        Trace.WriteLine (string.Format(CultureInfo.CurrentCulture,   
        "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
           //Create Editor Factory  
        editorFactory = new EditorFactory(this);  
        base.RegisterEditorFactory(editorFactory);  
    }  
    ```  
  
     Bu adım hem düzenleyici fabrikası hem de düzenleyici dosya uzantılarını kaydeder.  
  
3. Düzenleyici fabrikalarının kaydını silin.  
  
     VSPackage atıldığı zaman düzenleyici fabrikaları otomatik olarak silinir. Düzenleyici Fabrika nesnesi arabirimini uyguluyorsa <xref:System.IDisposable> , bu özelliğin yöntemi, `Dispose` fabrikada kaydı yapıldıktan sonra çağrılır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="registration-using-a-registry-script"></a>Kayıt defteri betiği kullanarak kayıt  
 Düzenleyici fabrikalarını ve dosya türlerini yerel olarak kaydetmek [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] , aşağıda gösterildiği gibi Windows kayıt defterine yazmak için bir kayıt defteri betiği kullanılarak yapılır.  
  
#### <a name="to-register-editor-file-types-using-a-registry-script"></a>Kayıt defteri betiği kullanarak düzenleyici dosya türlerini kaydetmek için  
  
1. Kayıt defteri betiğinizde, `GUID_BscEditorFactory` aşağıdaki kayıt defteri komut dosyasının bölümünde gösterildiği gibi düzenleyici fabrikası ve düzenleyici FABRIKASı GUID dizesini tanımlayın. Ayrıca, düzenleyici uzantısının uzantısını ve önceliğini tanımlayın:  
  
    ```  
  
          NoRemove Editors     {         %GUID_BscEditorFactory% = s 'RTF Editor'         {             val Package = s '%CLSID_Package%'             val DisplayName = s 'An RTF Editor'             val ExcludeDefTextEditor = d 1             val AcceptBinaryFiles = d 0  
  
            LogicalViews  
            {  
                val %LOGVIEWID_TextView% = s ''  
            }  
  
            OpenWithEntries  
            {  
            }  
  
            Extensions            {                val rtf = d 50            }  
        }  
    }  
    ```  
  
     Bu örnekteki düzenleyici dosyası uzantısı ". RTF" ve önceliği "50" olarak tanımlanır. GUID dizeleri Bscedıt örnek projesinin Resource. h dosyasında tanımlanmıştır.  
  
2. VSPackage 'a kaydolun.  
  
3. Düzenleyici fabrikasını kaydedin.  
  
     Düzenleyici fabrikası, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> uygulamaya kaydedilir.  
  
    ```  
    // create editor factory.  
    if (m_srpEdFact == NULL)   
    {  
        CComObject<CBscEditorFactory> *pEdFact = new CComObject<CBscEditorFactory>;  
        if (NULL == pEdFact)  
          return E_OUTOFMEMORY;  
  
        if (!pEdFact->FInit(this))  
          return E_UNEXPECTED;  
  
        m_srpEdFact = (IVsEditorFactory *) pEdFact;    // Note: assignment to a smart pointer does an AddRef()  
    }  
    // Query service for IVsRegisterEditors, register the editor factory  
    CComPtr<IVsRegisterEditors> srpRegEd;  
    if ((SUCCEEDED(m_srpPkgSiteSP->QueryService(SID_SVsRegisterEditors, IID_IVsRegisterEditors,(void **)&srpRegEd ))) && (srpRegEd != NULL))  
      {  
        ATLTRACE(TEXT(">> CVsPackage, registering editor factory.\n"));  
          if (FAILED(srpRegEd->RegisterEditor(GUID_BscEditorFactory,  
                      m_srpEdFact, &m_dwEditorCookie)))   
          {  
             ATLTRACE(TEXT(">> CVsPackage, RegisterEditor() failed.\n"));  
            return E_FAIL;  
          }  
      }  
        return S_OK;  
    }  
    ```  
  
     GUID dizeleri Bscedıt projesinin Resource. h dosyasında tanımlanmıştır.
