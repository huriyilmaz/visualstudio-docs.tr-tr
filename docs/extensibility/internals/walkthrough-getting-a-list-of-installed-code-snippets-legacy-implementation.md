---
title: Yüklü Kod Parçacıkları (Eski) Listesi Alma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, retrieving list
- code snippets, retrieving list
- GetSnippets method
ms.assetid: 7d142f8b-35b1-44c4-a13e-f89f6460c906
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d3d5ef857973555c4b2d201f98957bd2c39328b5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703649"
---
# <a name="walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation"></a>İzlenecek Yol: Yüklü Kod Parçacıklarının Listesini Alma (Eski Uygulama)
Kod snippet, bir menü komutuyla (yüklü kod parçacıkları listesi arasında seçim yapılmasına olanak tanıyan) veya IntelliSense tamamlama listesinden bir snippet kısayolu seçerek kaynak arabelleğine eklenebilen bir kod parçasıdır.

 Yöntem, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.EnumerateExpansions%2A> belirli bir dil GUID için tüm kod parçacıklarını alır. Bu parçacıklar için kısayollar bir IntelliSense tamamlama listesine eklenebilir.

 Yönetilen paket çerçevesi (MPF) dil hizmetinde kod parçacıklarının uygulanmasıyla ilgili ayrıntılar için [Eski Dil Hizmeti'ndeki Kod](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md) Parçacıkları Desteği'ne bakın.

### <a name="to-retrieve-a-list-of-code-snippets"></a>Kod parçacıkları listesini almak için

1. Aşağıdaki kod, belirli bir dil için kod parçacıklarının listesini nasıl alacağımı gösterir. Sonuçlar bir dizi <xref:Microsoft.VisualStudio.TextManager.Interop.VsExpansion> yapıda depolanır. Bu <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> yöntem, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> arabirimi hizmetten almak için statik yöntemi kullanır. Ancak, VSPackage'ınıza verilen servis sağlayıcıyı kullanabilir <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> ve yöntemi arayabilirsiniz.

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

### <a name="to-call-the-getsnippets-method"></a>GetSnippets yöntemini aramak için

1. Aşağıdaki yöntem, ayrıştırma işlemi tamamlandığında yöntemin `GetSnippets` nasıl çağrıldığını gösterir. Yöntem, <xref:Microsoft.VisualStudio.Package.LanguageService.OnParseComplete%2A> nedeni <xref:Microsoft.VisualStudio.Package.ParseReason>ile başlatılan bir ayrıştırma işleminden sonra çağrılır.

> [!NOTE]
> Dizi `expansionsList` listesi performans nedenleriyle önbelleğe alındı. Parçacıklardaki değişiklikler, dil hizmeti durdurulup yeniden yüklenene (örneğin, durdurup yeniden başlatılıncaya [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]kadar) listeye yansıtılmamaktadır.

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

### <a name="to-use-the-snippet-information"></a>Parçacık bilgilerini kullanmak için

1. Aşağıdaki kod, yöntem tarafından döndürülen parçacık bilgilerinin `GetSnippets` nasıl kullanılacağını gösterir. Yöntem, `AddSnippets` kod parçacıkları nın listesini doldurmak için kullanılan herhangi bir ayrıştırıcı nedenine yanıt olarak ayrıştırıcıdan çağrılır. Bu tam ayrıştı ilk kez yapıldıktan sonra yer almalıdır.

     Yöntem, `AddDeclaration` daha sonra bir tamamlama listesinde görüntülenen bildirimlerlistesi nin listesini oluşturur.

     Sınıf, `TestDeclaration` bir tamamlama listesinde görüntülenebilecek tüm bilgileri ve bildirim türünü içerir.

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
