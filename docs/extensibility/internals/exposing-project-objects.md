---
title: Proje Nesnelerini | Microsoft Docs
description: Otomasyon arabirimlerini kullanarak projeye erişim izni veren otomasyon Visual Studio özel proje türleri için nesneleri nasıl açığa çıkarabilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c3e89b4c80d64bedb77e68c648ba993794f8b658
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898298"
---
# <a name="expose-project-objects"></a>Proje nesnelerini açığa çıkarma

Özel proje türleri, otomasyon arabirimlerini kullanarak projeye erişim izni vermek için otomasyon nesneleri sağlar. Her proje türünün, IDE'de açık olan tüm projelerin bir koleksiyonunu içeren, üzerinden erişilen standart <xref:EnvDTE.Project> <xref:EnvDTE.Solution> otomasyon nesnesini sağlaması beklenir. Projede yer alan her öğenin ile erişilen bir nesne <xref:EnvDTE.ProjectItem> tarafından açığa çıkar olması `Project.ProjectItems` beklenir. Bu standart otomasyon nesnelerine ek olarak, projeler projeye özgü otomasyon nesneleri sunabilirsiniz.

veya kullanarak kök DTE nesnesinden geç bağlanarak erişebilecek özel kök düzeyinde otomasyon nesneleri `DTE.<customObjectName>` `DTE.GetObject("<customObjectName>")` oluşturabilirsiniz. Örneğin, Visual C++ kullanarak erişen *VCProjects* adlı bir C++ projesine özgü proje koleksiyonu `DTE.VCProjects` `DTE.GetObject("VCProjects")` oluşturur. Ayrıca, proje türü için benzersiz olan , en türetilmiş nesnesi için sorgulanlan bir ve ile 'i ortaya çıkaran `Project.Object` `Project.CodeModel` bir `ProjectItem` `ProjectItem.Object` `ProjectItem.FileCodeModel` oluşturabilirsiniz.

Projelerin özel, projeye özgü bir proje koleksiyonunu ortaya çıkararak yaygın bir kuraldır. Örneğin, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] veya kullanarak erişen C++'a özgü bir proje koleksiyonu `DTE.VCProjects` `DTE.GetObject("VCProjects")` oluşturur. Ayrıca, proje türü için benzersiz olan, en türetilmiş nesnesi için sorgulanlan bir , ve 'i ortaya çıkaran `Project.Object` `Project.CodeModel` bir `ProjectItem` `ProjectItem.Object` `ProjectItem.FileCodeModel` oluşturabilirsiniz.

## <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Bir proje için VSPackage'a özgü bir nesneye katkıda bulunmak için

1. VSPackage'nizin *.pkgdef* dosyasına uygun anahtarları ekleyin.

     Örneğin, C++ dil *projesi için .pkgdef* ayarları şu şekildedir:

    ```
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]
    "VCProjects"=""
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]
    "VCProjectEngineEventsObject"=""
    ```

2. Aşağıdaki örnekte olduğu <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> gibi yönteminin kodunu uygulama.

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

     Kodda, `g_wszAutomationProjects` proje koleksiyonun adıdır. yöntemi, aşağıdaki kod örneğinde gösterildiği gibi arabirimini uygulayan ve çağıran `GetAutomationProjects` `Projects` nesnenin `IDispatch` işaretçisini döndüren bir nesnesi oluşturur.

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

     Otomasyon nesneniz için benzersiz bir ad seçin. Ad çakışmaları öngörülemez ve çakışmalar, birden çok proje türü aynı adı kullanıyorsa çakışan bir nesne adının rastgele olarak ortaya çıkarılana neden olur. Otomasyon nesnesinin adına şirket adını veya ürün adının benzersiz bir yönünü dahil etmek gerekir.

     Özel koleksiyon `Projects` nesnesi, proje otomasyon modelinizin kalan bölümü için kullanışlı bir giriş noktasıdır. Proje nesnenize proje koleksiyonundan da <xref:EnvDTE.Solution> erişilebilir. Tüketicilere koleksiyon nesneleri sağlayan uygun kod ve kayıt defteri girdilerini oluşturduktan sonra, uygulamanız proje modeli için kalan `Projects` standart nesneleri sağlasa gerekir. Daha fazla bilgi için [bkz. Proje modelleme.](../../extensibility/internals/project-modeling.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
