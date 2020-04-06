---
title: Görsel Stüdyo SDK'da Olayları Ortaya Çıkarmak | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 48f1e0ea0dcd07bbc26fc89d5c61a6a5941d4727
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708483"
---
# <a name="expose-events-in-the-visual-studio-sdk"></a>Görsel Stüdyo SDK'daki olayları ortaya çıkarma
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]otomasyon u kullanarak olayları kaynak sağlar. Projeler ve proje öğeleri için etkinlik kaynağı yapmanızı öneririz.

 Olaylar otomasyon tüketicileri tarafından <xref:EnvDTE.DTEClass.Events%2A> nesneden <xref:EnvDTE.DTEClass.GetObject%2A> veya (örneğin) `GetObject("EventObjectName")`alınır. Ortam, `IDispatch::Invoke` bir olayı `DISPATCH_METHOD` `DISPATCH_PROPERTYGET` döndürmek için bayrakları veya bayrakları kullanarak çağırır.

 Aşağıdaki işlem, VSPackage'a özgü olayların nasıl döndürüldiyi açıklar.

1. Ortam başlar.

2. Tüm VSPackages'ın **Otomasyon**, Otomasyon **Etkinlikleri**ve **AutomationProperties** anahtarları altındaki tüm değer adlarını kayıt defterinden okur ve bu adları bir tabloda saklar.

3. Bu örnekte bir otomasyon `DTE.Events.AutomationProjectsEvents` tüketicisi çağırır veya `DTE.Events.AutomationProjectItemsEvents`.

4. Ortam, tablodaki dize parametresini bulur ve ilgili VSPackage'ı yükler.

5. Ortam, çağrıda <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> geçen adı kullanarak yöntemi çağırır; bu `AutomationProjectsEvents` örnekte, `AutomationProjectItemsEvents`ya da .

6. VSPackage gibi `get_AutomationProjectsEvents` yöntemleri olan bir kök nesne `get_AutomationProjectItemEvents` oluşturur ve sonra nesneye bir IDispatch işaretçisi döndürür.

7. Ortam, otomasyon çağrısına aktarılan ada göre uygun yöntemi çağırır.

8. Yöntem, `get_` hem `IConnectionPointContainer` arabirimi hem de `IConnectionPoint` arabirimi uygulayan ve nesneye bir `IDispatchpointer` alet döndüren başka bir IDispatch tabanlı olay nesnesi oluşturur.

   Bir olayı otomasyon kullanarak ortaya çıkarmak <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> için, kayıt defterine eklediğiniz dizeleri yanıtlamalı ve izlemeniz gerekir. Temel Proje örneğinde, dizeleri *BscProjectsEvents* ve *BscProjectItemsEvents*vardır.

## <a name="registry-entries-from-the-basic-project-sample"></a>Temel Proje örneğinden kayıt defteri girişleri
 Bu bölümde, kayıt defterine otomasyon olay değerlerinin nereye eklendiği gösterilmektedir.

 **[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Paketler\\<PkgGUID\>\AutomationEvents]**

 **AutomationProjectEvents** = `AutomationProjectEvents` Nesneyi döndürür.

 **AutomationProjectItemEvents** = `AutomationProjectItemsEvents` Nesneyi döndürür.

|Adı|Tür|Aralık|Açıklama|
|----------|----------|-----------|-----------------|
|Varsayılan (@)|REG_SZ|Kullanılmıyor|Kullanılmıyor. Belgeler için veri alanını kullanabilirsiniz.|
|*OtomasyonProjelerEtkinlikler*|REG_SZ|Olay nesnenizin adı.|Yalnızca anahtar adı alakalıdır. Belgeler için veri alanını kullanabilirsiniz.<br /><br /> Bu örnek Temel Proje örneğinden gelir.|
|*OtomasyonProjeItem Etkinlikleri*|REG_SZ|Olay nesnenizin adı|Yalnızca anahtar adı alakalıdır. Belgeler için veri alanını kullanabilirsiniz.<br /><br /> Bu örnek Temel Proje örneğinden gelir.|

 Olay nesneleriniz herhangi biri bir otomasyon tüketicisi tarafından istendiğinde, VSPackage'ınızın desteklediği herhangi bir olay için yöntemleri olan bir kök nesne oluşturun. Ortam bu nesne `get_` üzerinde uygun yöntemi çağırır. Örneğin, çağrıldığında, `DTE.Events.AutomationProjectsEvents` `get_AutomationProjectsEvents` kök nesneüzerindeki yöntem çağrılır.

 ![Visual Studio proje etkinlikleri](../../extensibility/internals/media/projectevents.gif "Proje Etkinlikleri") Etkinlikler için otomasyon modeli

 Sınıf `CProjectEventsContainer` *BscProjectsEvents*için kaynak nesneyi `CProjectItemsEventsContainer` temsil eder ve *BscProjectItemsEvents*için kaynak nesnetemsil eder.

 Çoğu durumda, çoğu olay nesnesi bir filtre nesnesi aldığı için her olay isteği için yeni bir nesne döndürmeniz gerekir. Olayınızı ateşlediğinizde, olay işleyicisinin çağrıldığını doğrulamak için bu filtreyi denetleyin.

 *AutomationEvents.h* ve *AutomationEvents.cpp* aşağıdaki tabloda sınıfların beyanlarını ve uygulamalarını içerir.

|Sınıf|Açıklama|
|-----------|-----------------|
|`CAutomationEvents`|Nesneden alınan bir olay kök `DTE.Events` nesnesi uygular.|
|`CProjectsEventsContainer` ve `CProjectItemsEventsContainer`|İlgili olayları ateşleyen olay kaynağı nesneleri uygulayın.|

 Aşağıdaki kod örneği, bir olay nesnesi isteğine nasıl yanıt verilebildiğini gösterir.

```cpp
STDMETHODIMP CVsPackage::GetAutomationObject(
    /* [in]  */ LPCOLESTR       pszPropName,
    /* [out] */ IDispatch **    ppIDispatch)
{
    ExpectedPtrRet(ppIDispatch);
    *ppIDispatch = NULL;

    if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)
        //Is the requested name our Projects object?
    {
        return GetAutomationProjects(ppIDispatch);
        // Gets our Projects object.
    }
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)
        //Is the requested name our ProjectsEvents object?
    {
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);
          // Gets our ProjectEvents object.
    }
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  //Is the requested name our ProjectsItemsEvents object?
    {
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);
          // Gets our ProjectItemsEvents object.
    }
    return E_INVALIDARG;
}
```

 Yukarıdaki kodda, `g_wszAutomationProjects` proje koleksiyonunuzun adı *(FigProjects*), `g_wszAutomationProjectsEvents` ( `g_wszAutomationProjectItemsEvents` *FigProjectsEvents*) ve (*FigProjectItemEvents*) VSPackage uygulamanızdan kaynaklanan proje olaylarının ve proje öğeleri etkinliklerinin adlarıdır.

 Olay nesneleri aynı merkezi konumdan, `DTE.Events` nesne alınır. Bu şekilde, son kullanıcıbelirli bir olayı bulmak için tüm nesne modeline göz atmak zorunda kalmaması için tüm olay nesneleri birlikte gruplandırılır. Bu, sistem genelindeki olaylar için kendi kodunuzu uygulamanızı gerektirmek yerine, belirli VSPackage nesnelerinizi sağlamanıza da olanak tanır. Ancak, arabiriminiz `ProjectItem` için bir olay bulması gereken son kullanıcı için, bu olay nesnesinin nereden alındığı hemen açık değildir.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
