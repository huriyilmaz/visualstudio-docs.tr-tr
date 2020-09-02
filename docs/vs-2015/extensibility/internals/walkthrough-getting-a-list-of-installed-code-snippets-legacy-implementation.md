---
title: 'İzlenecek yol: yüklü kod parçacıklarının listesini alma (eski uygulama) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- snippets, retrieving list
- code snippets, retrieving list
- GetSnippets method
ms.assetid: 7d142f8b-35b1-44c4-a13e-f89f6460c906
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 256430c0e41bfc0452282c89407335d997cc715c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64822423"
---
# <a name="walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation"></a>İzlenecek yol: Yüklü Kod Parçacıklarının Listesini Alma (Eski Uygulama)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kod parçacığı, bir menü komutuyla (yüklü kod parçacıkları listesi arasında seçim yapılmasına izin veren) veya bir IntelliSense tamamlanma listesinden bir kod parçacığı kısayolu seçerek kaynak arabelleğine eklenebilen bir kod parçasıdır.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.EnumerateExpansions%2A>Yöntemi, belirli bir DIL GUID 'si için tüm kod parçacıklarını alır. Bu kod parçacıklarının kısayolları bir IntelliSense tamamlanma listesine eklenebilir.  
  
 Yönetilen bir paket çerçevesi (MPF) dil hizmetinde kod parçacıkları uygulama hakkında daha fazla bilgi için bkz. [eski dil hizmetindeki kod parçacıkları Için destek](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md) .  
  
### <a name="to-retrieve-a-list-of-code-snippets"></a>Kod parçacıklarının listesini almak için  
  
1. Aşağıdaki kod, belirli bir dil için kod parçacıkları listesinin nasıl alınacağını gösterir. Sonuçlar bir yapı dizisinde depolanır <xref:Microsoft.VisualStudio.TextManager.Interop.VsExpansion> . Bu yöntem, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> hizmeti arabirimden almak için statik yöntemi kullanır <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> . Ancak, VSPackage 'a verilen hizmet sağlayıcısını da kullanabilir ve <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> yöntemini çağırabilirsiniz.  
  
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
  
### <a name="to-call-the-getsnippets-method"></a>Getparçacıklar yöntemini çağırmak için  
  
1. Aşağıdaki yöntem, `GetSnippets` bir ayrıştırma işleminin tamamlandığında yönteminin nasıl çağrılacağını gösterir. <xref:Microsoft.VisualStudio.Package.LanguageService.OnParseComplete%2A>Yöntemi, neden ile başlatılan bir ayrıştırma işleminden sonra çağrılır <xref:Microsoft.VisualStudio.Package.ParseReason> .  
  
> [!NOTE]
> `expansionsList`Dizi listis performans nedeniyle önbelleğe alındı. Dil hizmeti durdurulup yeniden yükleninceye kadar kod parçacıklarında yapılan değişiklikler listede yansıtılmaz (örneğin, durduruluyor ve yeniden başlatılır [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ).  
  
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
  
1. Aşağıdaki kod, yöntemi tarafından döndürülen kod parçacığı bilgilerinin nasıl kullanılacağını gösterir `GetSnippets` . `AddSnippets`Yöntemi, kod parçacıklarının listesini doldurmak için kullanılan herhangi bir ayrıştırma nedenine yanıt olarak Ayrıştırıcıdan çağrılır. Bu işlem, tam ayrıştırma ilk kez gerçekleştirildikten sonra gerçekleşmelidir.  
  
     `AddDeclaration`Yöntemi, daha sonra tamamlama listesinde görüntülenen bildirimlerin bir listesini oluşturur.  
  
     `TestDeclaration`Sınıfı, tamamlama listesinde görüntülenebilen tüm bilgileri ve bildirimin türünü içerir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski Dil Hizmetinde Kod Parçacıkları için Destek](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)
