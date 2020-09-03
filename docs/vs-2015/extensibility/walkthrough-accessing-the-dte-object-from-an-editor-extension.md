---
title: 'İzlenecek yol: bir düzenleyici uzantısından DTE nesnesine erişme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b14b59465b94ddd0a09748f0e309166bf3d4114
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148885"
---
# <a name="walkthrough-accessing-the-dte-object-from-an-editor-extension"></a>İzlenecek Yol: Düzenleyici Uzantısından DTE Nesnesine Erişme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackages içinde, öğesini DTE nesnesi türüyle çağırarak DTE nesnesini alabilirsiniz <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> . Managed Extensibility Framework (MEF) uzantılarında, öğesini içeri aktarabilir <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> ve sonra <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> bir türüyle çağırabilirsiniz <xref:EnvDTE.DTE> .  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu yönergeyi izlemek için, Visual Studio SDK 'sını yüklemelisiniz. Daha fazla bilgi için bkz. [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="getting-the-dte-object"></a>DTE nesnesini alma  
  
#### <a name="to-get-the-dte-object-from-the-serviceprovider"></a>ServiceProvider içinden DTE nesnesini almak için  
  
1. Adlı bir C# VSıX projesi oluşturun `DTETest` . Bir düzenleyici sınıflandırıcı öğe şablonu ekleyin ve adlandırın `DTETest` . Daha fazla bilgi için bkz. [bir düzenleyici öğe şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
2. Aşağıdaki derleme başvurularını projeye ekleyin:  
  
    - EnvDTE  
  
    - EnvDTE80  
  
    - Microsoft. VisualStudio. Shell. sabit. 10.0  
  
3. DTETest.cs dosyasına gidin ve aşağıdaki `using` yönergeleri ekleyin:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio.Shell;  
  
    ```  
  
4. `GetDTEProvider`Sınıfında, bir alın <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> .  
  
    ```csharp  
    [Import]  
    internal SVsServiceProvider ServiceProvider = null;  
  
    ```  
  
5. `GetClassifier()`Yönteminde aşağıdaki kodu ekleyin.  
  
    ```csharp  
    DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));  
  
    ```  
  
6. Arabirimini kullanmanız gerekiyorsa <xref:EnvDTE80.DTE2> , DTE nesnesini buna atayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dil Hizmeti ve Düzenleyici Uzantı Noktaları](../extensibility/language-service-and-editor-extension-points.md)
