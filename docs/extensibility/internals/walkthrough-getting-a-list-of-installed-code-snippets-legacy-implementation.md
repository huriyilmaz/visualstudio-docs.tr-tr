---
title: Yüklü Kod Parçacıklarının (Eski) Listesini Alma | Microsoft Docs
description: Belirli bir dil GUID'i için tüm kod parçacıklarını nasıl ala öğrenin. Bu kod parçacıklarının kısayolları bir IntelliSense tamamlama listesine eklenebilir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- snippets, retrieving list
- code snippets, retrieving list
- GetSnippets method
ms.assetid: 7d142f8b-35b1-44c4-a13e-f89f6460c906
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 1d41475bef1a4da3a0eff1583a81c8e4953a3832
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126724986"
---
# <a name="walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation"></a>İzlenecek yol: Yüklü Kod Parçacıklarının Listesini Alma (Eski Uygulama)
Kod parçacığı, bir menü komutuyla (yüklü kod parçacıkları listesinden seçime olanak sağlar) veya IntelliSense tamamlama listesinden bir kod parçacığı kısayolu seçerek kaynak arabelleğe eklen bir kod parçasıdır.

 yöntemi, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.EnumerateExpansions%2A> belirli bir dil GUID'i için tüm kod parçacıklarını alır. Bu kod parçacıklarının kısayolları bir IntelliSense tamamlama listesine eklenebilir.

 Yönetilen [paket çerçevesi](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md) (MPF) dil hizmetine kod parçacıkları uygulama hakkında ayrıntılı bilgi için bkz. Eski Dil Hizmeti'ne Kod Parçacıkları Desteği.

### <a name="to-retrieve-a-list-of-code-snippets"></a>Kod parçacıklarının listesini almak için

1. Aşağıdaki kodda, belirli bir dil için kod parçacıklarının listesinin nasıl elde edildiklerine yer verilmiştir. Sonuçlar bir yapı dizisinde <xref:Microsoft.VisualStudio.TextManager.Interop.VsExpansion> depolanır. Bu yöntem, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> hizmetten arabirimi almak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> için statik yöntemini <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> kullanır. Ancak, VSPackage'ınıza verilen hizmet sağlayıcısını da kullanabilir ve yöntemini <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> çağırabilirsiniz.

    ```csharp
    using System;
    using System.Collections;
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.Package;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.TextManager.Interop;

    [Guid("00000000-0000-0000-0000-000000000000")] //create a new GUID for the language service
    namespace TestLanguage
    {
        class TestLanguageService : LanguageService
        {
            private void GetSnippets(Guid languageGuid,
                                     ref ArrayList expansionsList)
            {
                IVsTextManager textManager = (IVsTextManager)Package.GetGlobalService(typeof(SVsTextManager));
                if (textManager != null)
                {
                    IVsTextManager2 textManager2 = (IVsTextManager2)textManager;
                    if (textManager2 != null)
                    {
                        IVsExpansionManager expansionManager = null;
                        textManager2.GetExpansionManager(out expansionManager);
                        if (expansionManager != null)
                        {
                            // Tell the environment to fetch all of our snippets.
                            IVsExpansionEnumeration expansionEnumerator = null;
                            expansionManager.EnumerateExpansions(languageGuid,
                            0,     // return all info
                            null,    // return all types
                            0,     // return all types
                            1,     // include snippets without types
                            0,     // do not include duplicates
                            out expansionEnumerator);
                            if (expansionEnumerator != null)
                            {
                                // Cache our expansions in a VsExpansion array
                                uint count   = 0;
                                uint fetched = 0;
                                VsExpansion expansionInfo = new VsExpansion();
                                IntPtr[] pExpansionInfo   = new IntPtr[1];

                                // Allocate enough memory for one VSExpansion structure. This memory is filled in by the Next method.
                                pExpansionInfo[0] = Marshal.AllocCoTaskMem(Marshal.SizeOf(expansionInfo));

                                expansionEnumerator.GetCount(out count);
                                for (uint i = 0; i < count; i++)
                                {
                                    expansionEnumerator.Next(1, pExpansionInfo, out fetched);
                                    if (fetched > 0)
                                    {
                                        // Convert the returned blob of data into a structure that can be read in managed code.
                                        expansionInfo = (VsExpansion)Marshal.PtrToStructure(pExpansionInfo[0], typeof(VsExpansion));

                                        if (!String.IsNullOrEmpty(expansionInfo.shortcut))
                                        {
                                            expansionsList.Add(expansionInfo);
                                        }
                                    }
                                }
                                Marshal.FreeCoTaskMem(pExpansionInfo[0]);
                            }
                        }
                    }
                }
            }
        }
    }
    ```

### <a name="to-call-the-getsnippets-method"></a>GetSnippets yöntemini çağırma

1. Aşağıdaki yöntem, ayrıştırma işlemi `GetSnippets` tamamlandıktan sonra yönteminin nasıl çağrıl olduğunu gösterir. yöntemi, <xref:Microsoft.VisualStudio.Package.LanguageService.OnParseComplete%2A> nedeni ile başlayan bir ayrıştırma işlemi sonrasında çağrılır. <xref:Microsoft.VisualStudio.Package.ParseReason>

> [!NOTE]
> Dizi `expansionsList` listesi performans nedeniyle önbelleğe alınmış. Dil hizmeti durdurulana ve yeniden yüklenene (örneğin, durdurularak ve yeniden başlatarak) kadar kod parçacıklarında yapılan değişiklikler listede [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yansıtlanmaz.

```csharp
class TestLanguageService : LanguageService
{
    private ArrayList expansionsList;

    public override void OnParseComplete(ParseRequest req)
    {
        if (this.expansionsList == null)
        {
            this.expansionsList = new ArrayList();
            GetSnippets(this.GetLanguageServiceGuid(),
                ref this.expansionsList);
        }
    }
}
```

### <a name="to-use-the-snippet-information"></a>Kod parçacığı bilgilerini kullanmak için

1. Aşağıdaki kod, yöntemi tarafından döndürülen kod parçacığı bilgilerini nasıl kullanabileceğinizi `GetSnippets` gösterir. yöntemi, kod parçacıkları listesini doldurmak için kullanılan herhangi bir ayrıştırma nedene yanıt olarak `AddSnippets` ayrıştırıcıdan çağrılır. Bu, tam ayrıştırma ilk kez yapıldıktan sonra yapılır.

     yöntemi, `AddDeclaration` daha sonra tamamlama listesinde görüntülenen bildirimlerin listesini derleme.

     `TestDeclaration`sınıfı, bir tamamlama listesinde görüntülenilen tüm bilgileri ve bildirim türünü içerir.

    ```csharp
    class TestAuthoringScope : AuthoringScope
    {
        public void AddDeclarations(TestDeclaration declaration)
        {
            if (m_declarations == null)
                m_declarations = new List<TestDeclaration>();
            m_declarations.Add(declaration);
         }
    }
    class TestDeclaration
    {
        private string m_name;
        private string m_description;
        private string m_type;

        public TestDeclaration(string name, string desc, string type)
        {
            m_name = name;
            m_description = desc;
            m_type = type;
        }

    class TestLanguageService : LanguageService
    {
        internal void AddSnippets(ref TestAuthoringScope scope)
        {
            if (this.expansionsList != null && this.expansionsList.Count > 0)
            {
                int count = this.expansionsList.Count;
                for (int i = 0; i < count; i++)
                {
                    VsExpansion expansionInfo = (VsExpansion)this.expansionsList[i];
                    scope.AddDeclaration(new TestDeclaration(expansionInfo.title,
                         expansionInfo.description,
                         "snippet"));
                }
            }
        }
    }

    ```

## <a name="see-also"></a>Ayrıca bkz.
- [Eski Dil Hizmetinde Kod Parçacıkları için Destek](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)
