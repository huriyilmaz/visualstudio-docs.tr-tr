---
title: DTE Nesnesine bir düzenleyici uzantısından erişme
description: Bu kılavuzda yer alan kod örneğini kullanarak bir düzenleyici uzantısından DTE nesnesine erişmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 04/24/2019
ms.topic: tutorial
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 094a37960fa5b32d018eebe3becee4fde43cc392
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905130"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>Adım adım kılavuz: DTE nesnesine bir düzenleyici uzantısından erişme

VSPackages'ta, DTE nesnesinin türüyle yöntemini çağırarak <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> DTE nesnesini elde edersiniz. Bu Managed Extensibility Framework (MEF) uzantılarını içeri aktararak <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> türünü <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> kullanarak yöntemini <xref:EnvDTE.DTE> çağırabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu takip etmek için Visual Studio SDK'sı yüklemeniz gerekir. Daha fazla bilgi için [bkz. Visual Studio SDK.](../extensibility/visual-studio-sdk.md)

## <a name="get-the-dte-object"></a>DTE nesnesini al

1. Bir C# VSIX projesi oluşturun ve **DTETest olarak ad girin.** Bir Düzenleyici **Sınıflandırıcı öğesi** şablonu ekleyin ve **bunu DTETest olarak ad girin.**

   Daha fazla bilgi için [bkz. Düzenleyici öğesi şablonuyla uzantı oluşturma.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

::: moniker range=">=vs-2019"

2. Aşağıdaki derleme başvurularını projeye ekleyin:

    - Microsoft.VisualStudio.Shell.Framework
    - Microsoft.VisualStudio.Shell.Immutable.10.0

3. *DTETestProvider.cs* dosyasına aşağıdaki yönergeleri `using` ekleyin:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. sınıfında, `DTETestProvider` bir içeri <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> aktarın.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. yönteminde `GetClassifier()` deyiminden önce aşağıdaki kodu `return` ekleyin:

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. Aşağıdaki derleme başvurularını projeye ekleyin:

   - Envdte
   - Microsoft.VisualStudio.Shell.Framework

3. *DTETestProvider.cs* dosyasına aşağıdaki yönergeleri `using` ekleyin:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. sınıfında, `DTETestProvider` bir içeri <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> aktarın.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. yönteminde `GetClassifier()` deyiminden önce aşağıdaki kodu `return` ekleyin:

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Dil hizmeti ve düzenleyici uzantısı noktaları](../extensibility/language-service-and-editor-extension-points.md)
- [DTE kullanarak Visual Studio’yu Başlatma](launch-visual-studio-dte.md)
