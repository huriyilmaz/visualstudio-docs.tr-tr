---
title: Proje Nesnelerini Açığa Çıkarma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81446fa582524872b03199ae707f658776787961
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708480"
---
# <a name="expose-project-objects"></a>Proje nesnelerini açığa çıkarma

Özel proje türleri, otomasyon arabirimleri kullanarak projeye erişimsağlamak için otomasyon nesneleri sağlayabilir. Her proje <xref:EnvDTE.Project> <xref:EnvDTE.Solution>türünün, IDE'de açık olan tüm projelerin bir koleksiyonunu içeren standart otomasyon nesnesinden erişilen standart otomasyon nesnesini sağlaması beklenir. Projedeki her öğenin, '' <xref:EnvDTE.ProjectItem> ile `Project.ProjectItems`erişilen bir nesne tarafından ortaya alınması bekleniyor. Bu standart otomasyon nesnelerine ek olarak, projeler projeye özel otomasyon nesneleri sunmayı seçebilir.

Kök DTE nesnesinden geç bağlanabileceğiniz özel kök düzeyi otomasyon nesneleri `DTE.<customObjectName>` oluşturabilirsiniz `DTE.GetObject("<customObjectName>")`veya. Örneğin, Visual C++ *vcprojects* `DTE.VCProjects` adlı bir C++ proje özel proje koleksiyonu `DTE.GetObject("VCProjects")`oluşturur kullanarak erişebilirsiniz veya . Ayrıca, proje `Project.Object`türü için benzersiz bir , `Project.CodeModel`bir , en çok türetilmiş nesne için `ProjectItem`sorgulanabilir `ProjectItem.Object` bir `ProjectItem.FileCodeModel`ve bir , hangi ortaya çıkarır ve bir .

Projelerin özel, projeye özgü bir proje koleksiyonunu ortaya çıkarması ortak bir kuraldır. Örneğin, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] daha sonra kullanarak `DTE.VCProjects` erişebileceğiniz c++ özel bir `DTE.GetObject("VCProjects")`proje koleksiyonu oluşturur veya . Ayrıca, proje `Project.Object`türü için benzersiz bir , `Project.CodeModel`bir , en çok türetilen nesne için `ProjectItem`sorgulanabilir `ProjectItem.Object`bir , `ProjectItem.FileCodeModel`bir , hangi ortaya çıkarır , ve bir .

## <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Bir proje için VSPackage'a özgü bir nesneye katkıda bulunmak için

1. VSPackage'ınızın *.pkgdef* dosyasına uygun tuşları ekleyin.

     Örneğin, C++ dil projesinin *.pkgdef* ayarları şunlardır:

    ```
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]
    "VCProjects"=""
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]
    "VCProjectEngineEventsObject"=""
    ```

2. Aşağıdaki örnekte <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> olduğu gibi, yöntemde kodu uygulayın.

    ```cpp
    STDMETHODIMP CVsPackage::GetAutomationObject(
    /* [in]  */ LPCOLESTR       pszPropName,
    /* [out] */ IDispatch **    ppIDispatch)
    {
    ExpectedPtrRet(pszPropName);
    ExpectedPtrRet(ppIDispatch);
    *ppIDispatch = NULL;

        if (m_fZombie)
            return E_UNEXPECTED;

        if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)
        {
            return GetAutomationProjects(ppIDispatch);
        }
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)
        {
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);
        }
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)
        {
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);
        }
        return E_INVALIDARG;
    }
    ```

     Kodda, `g_wszAutomationProjects` proje koleksiyonunuzun adı veda sı. Yöntem, `GetAutomationProjects` `Projects` arabirimi uygulayan bir nesne oluşturur `IDispatch` ve aşağıdaki kod örneğinde gösterildiği gibi bir işaretçiyi çağıran nesneye döndürür.

    ```cpp
    HRESULT CVsPackage::GetAutomationProjects(/* [out] */ IDispatch ** ppIDispatch)
    {
        ExpectedPtrRet(ppIDispatch);
        *ppIDispatch = NULL;

        if (!m_srpAutomationProjects)
        {
            HRESULT hr = CACProjects::CreateInstance(&m_srpAutomationProjects);
            IfFailRet(hr);
            ExpectedExprRet(m_srpAutomationProjects != NULL);
        }
        return m_srpAutomationProjects.CopyTo(ppIDispatch);
    }
    ```

     Otomasyon nesneniz için benzersiz bir ad seçin. Ad çakışmaları öngörülemez dir ve çakışan bir nesne adı, birden çok proje türü aynı adı kullanıyorsa rasgele atılmasına neden olur. Şirket adınızı veya ürün adının benzersiz bir yönünü otomasyon nesnesinin adına eklemeniz gerekir.

     Özel `Projects` toplama nesnesi, proje otomasyon modelinizin kalan bölümü için kolaylık bir giriş noktasıdır. Proje nesnenize <xref:EnvDTE.Solution> proje koleksiyonundan da erişilebilir. Tüketicilere `Projects` koleksiyon nesneleri sağlayan uygun kod ve kayıt defteri girişlerini oluşturduktan sonra, uygulamanızın proje modeli için kalan standart nesneleri sağlaması gerekir. Daha fazla bilgi için [Proje modellemesi'ne](../../extensibility/internals/project-modeling.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
