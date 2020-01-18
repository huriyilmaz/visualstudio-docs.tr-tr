---
title: Bir düzenleyici uzantısından DTE nesnesine erişme
ms.date: 04/24/2019
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d023359412b423c9c12d7c7d8a37e79571cbc11a
ms.sourcegitcommit: e3c3d2b185b689c5e32ab4e595abc1ac60b6b9a8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/18/2020
ms.locfileid: "76269087"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>İzlenecek yol: bir düzenleyici uzantısından DTE nesnesine erişme

VSPackages içinde, DTE nesnesinin türüyle <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> yöntemini çağırarak DTE nesnesini alabilirsiniz. Managed Extensibility Framework (MEF) uzantılarında, <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> içeri aktarabilir ve sonra <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> yöntemini bir <xref:EnvDTE.DTE>türü ile çağırabilirsiniz.

## <a name="prerequisites"></a>Prerequisites

Bu izlenecek yolda takip etmek için Visual Studio SDK'yı yüklemeniz gerekir. Daha fazla bilgi için [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="get-the-dte-object"></a>DTE nesnesini Al

1. Bir C# VSIX projesi oluşturun ve **dtetest**olarak adlandırın. Bir **Düzenleyici sınıflandırıcı** öğe şablonu ekleyin ve **dtetest**olarak adlandırın.

   Daha fazla bilgi için bkz. [bir düzenleyici öğe şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).

::: moniker range=">=vs-2019"

2. Aşağıdaki derleme başvurularını projeye ekleyin:

    - Microsoft. VisualStudio. Shell. Framework
    - Microsoft. VisualStudio. Shell. sabit. 10.0

3. *DTETestProvider.cs* dosyasında aşağıdaki `using` yönergelerini ekleyin:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. `DTETestProvider` sınıfında bir <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>içeri aktarın.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. `GetClassifier()` yönteminde, `return` deyimden önce aşağıdaki kodu ekleyin:

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. Aşağıdaki derleme başvurularını projeye ekleyin:

   - EnvDTE
   - Microsoft. VisualStudio. Shell. Framework

3. *DTETestProvider.cs* dosyasında aşağıdaki `using` yönergelerini ekleyin:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. `DTETestProvider` sınıfında bir <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>içeri aktarın.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. `GetClassifier()` yönteminde, `return` deyimden önce aşağıdaki kodu ekleyin:

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Dil hizmeti ve Düzenleyici uzantı noktaları](../extensibility/language-service-and-editor-extension-points.md)
- [DTE kullanarak Visual Studio 'Yu başlatma](launch-visual-studio-dte.md)
