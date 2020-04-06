---
title: DTE Nesnesi'ne bir düzenleyici uzantısından erişin
ms.date: 04/24/2019
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e37bdb21b7c8132f0dfb166d19e03d36e838245d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697652"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>Walkthrough: DTE nesnesini bir düzenleyici uzantısından erişin

VSPackages'te, <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> yöntemi DTE nesnesinin türüyle arayarak DTE nesnesini alabilirsiniz. Yönetilen Genişletilebilirlik Çerçevesi (MEF) uzantılarında, <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> yöntemi bir tür .'le <xref:EnvDTE.DTE>içe aktarıp çağırabilirsiniz.

## <a name="prerequisites"></a>Ön koşullar

Bu izlenmeyi takip etmek için Visual Studio SDK'yı yüklemeniz gerekir. Daha fazla bilgi için [Visual Studio SDK'ya](../extensibility/visual-studio-sdk.md)bakın.

## <a name="get-the-dte-object"></a>DTE nesnesini alın

1. Bir C# VSIX projesi oluşturun ve **DTETest**adını. Bir **Düzenleyici Sınıflandırıcı** öğe şablonu ekleyin ve **dTETest**adını.

   Daha fazla bilgi için [bkz.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

::: moniker range=">=vs-2019"

2. Projeye aşağıdaki derleme başvurularını ekleyin:

    - Microsoft.VisualStudio.Shell.Framework
    - Microsoft.VisualStudio.Shell.Immutable.10.0

3. *DTETestProvider.cs* dosyasına aşağıdaki `using` yönergeleri ekleyin:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. `DTETestProvider` Sınıfta, bir <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. `GetClassifier()` Yöntemde, deyimden `return` önce aşağıdaki kodu ekleyin:

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. Projeye aşağıdaki derleme başvurularını ekleyin:

   - Envdte
   - Microsoft.VisualStudio.Shell.Framework

3. *DTETestProvider.cs* dosyasına aşağıdaki `using` yönergeleri ekleyin:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. `DTETestProvider` Sınıfta, bir <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. `GetClassifier()` Yöntemde, deyimden `return` önce aşağıdaki kodu ekleyin:

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Dil hizmeti ve editör uzantı noktaları](../extensibility/language-service-and-editor-extension-points.md)
- [DTE kullanarak Visual Studio’yu Başlatma](launch-visual-studio-dte.md)
