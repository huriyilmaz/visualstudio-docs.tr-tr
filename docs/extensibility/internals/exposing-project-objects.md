---
title: Proje nesneleri gösteriliyor | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708480"
---
# <a name="expose-project-objects"></a>Proje nesnelerini kullanıma sunma

Özel proje türleri, otomasyon arabirimlerini kullanarak projeye erişime izin vermek için Otomasyon nesneleri sağlayabilir. Her proje türünün <xref:EnvDTE.Project> <xref:EnvDTE.Solution> , IDE 'de açık olan tüm projelerin bir koleksiyonunu içeren öğesinden erişilen standart Otomasyon nesnesini sağlaması beklenir. Projedeki her öğenin, ile erişilen bir nesne tarafından açığa çıkarılması beklenir <xref:EnvDTE.ProjectItem> `Project.ProjectItems` . Projeler, bu standart otomasyon nesnelerine ek olarak projeye özgü Otomasyon nesneleri sunmaya da seçim yapabilir.

Veya kullanarak kök DTE nesnesinden geç bağlanan bir şekilde erişebileceğiniz özel kök düzeyi Otomasyon nesneleri oluşturabilirsiniz `DTE.<customObjectName>` `DTE.GetObject("<customObjectName>")` . Örneğin Visual C++, veya kullanarak erişebileceğiniz *vcprojects* adlı C++ projesine özgü bir proje koleksiyonu oluşturur `DTE.VCProjects` `DTE.GetObject("VCProjects")` . Ayrıca, bir `Project.Object` Proje türü için benzersiz olan, `Project.CodeModel` en çok türetilmiş nesnesi için sorgulanabilen ve bir `ProjectItem` ve sunan bir oluşturabilirsiniz `ProjectItem.Object` `ProjectItem.FileCodeModel` .

Projeler için özel, projeye özgü bir proje koleksiyonunu ortaya çıkaran yaygın bir kuraldır. Örneğin, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] veya kullanarak erişebileceğiniz C++ özel proje koleksiyonu oluşturur `DTE.VCProjects` `DTE.GetObject("VCProjects")` . Ayrıca, bir `Project.Object` Proje türü için benzersiz olan bir oluşturabilirsiniz, bu, `Project.CodeModel` en çok türetilen nesne için sorgulanabilen, bir, `ProjectItem` `ProjectItem.Object` ve bir `ProjectItem.FileCodeModel` .

## <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Bir proje için VSPackage 'a özgü bir nesneye katkıda bulunmak için

1. VSPackage 'un *. pkgdef* dosyasına uygun anahtarları ekleyin.

     Örneğin, C++ dili projesi için *. pkgdef* ayarları aşağıda verilmiştir:

    ```
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]
    "VCProjects"=""
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]
    "VCProjectEngineEventsObject"=""
    ```

2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>Aşağıdaki örnekte olduğu gibi, yöntemine kodu uygulayın.

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

     Kodda, `g_wszAutomationProjects` Proje koleksiyonunuzun adıdır. `GetAutomationProjects`Yöntemi, `Projects` `IDispatch` Aşağıdaki kod örneğinde gösterildiği gibi, arabirimini uygulayan ve çağıran nesneye bir işaretçi döndüren bir nesne oluşturur.

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

     Otomasyon nesneniz için benzersiz bir ad seçin. Ad çakışmaları tahmin edilemez ve çakışmalar, birden fazla proje türü aynı adı kullanıyorsa çakışan bir nesne adının rastgele oluşturulmasına neden olur. Kurumsal adınızı veya ürün adının benzersiz bir bölümünü Otomasyon nesnesi adına dahil etmelisiniz.

     Özel `Projects` koleksiyon nesnesi, Proje Otomasyonu modelinizin kalan bölümü için kolaylık olan bir giriş noktasıdır. Proje nesneniz <xref:EnvDTE.Solution> proje koleksiyonundan de erişilebilir. Kullanıcılara koleksiyon nesneleri sağlayan uygun kodu ve kayıt defteri girdilerini oluşturduktan sonra `Projects` , uygulamanızın proje modeli için kalan Standart nesneleri sağlaması gerekir. Daha fazla bilgi için bkz. [Proje modelleme](../../extensibility/internals/project-modeling.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
