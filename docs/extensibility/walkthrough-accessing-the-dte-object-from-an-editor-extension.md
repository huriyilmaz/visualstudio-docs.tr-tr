---
title: Bir düzenleyici uzantısından DTE nesnesine erişme
description: Bu izlenecek yolda kod örneğini kullanarak bir düzenleyici uzantısından DTE nesnesine nasıl erişebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 04/24/2019
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7035842f608428f149dd2c0965b4792afa25db67
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062076"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>İzlenecek yol: bir düzenleyici uzantısından DTE nesnesine erişme

VSPackages içinde, öğesini DTE nesnesi türüyle çağırarak DTE nesnesini alabilirsiniz <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> . Managed Extensibility Framework (MEF) uzantılarında, öğesini içeri aktarabilir <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> ve sonra <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> bir türüyle çağırabilirsiniz <xref:EnvDTE.DTE> .

## <a name="prerequisites"></a>Önkoşullar

Bu yönergeyi izlemek için, Visual Studio SDK 'sını yüklemelisiniz. Daha fazla bilgi için bkz. [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md).

## <a name="get-the-dte-object"></a>DTE nesnesini Al

1. Bir C# VSıX projesi oluşturun ve **Dtetest** olarak adlandırın. Bir **Düzenleyici sınıflandırıcı** öğe şablonu ekleyin ve **dtetest** olarak adlandırın.

   Daha fazla bilgi için bkz. [bir düzenleyici öğe şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).

::: moniker range=">=vs-2019"

2. Aşağıdaki derleme başvurularını projeye ekleyin:

    - Microsoft. VisualStudio. Shell. Framework
    - Microsoft. VisualStudio. Shell. sabit. 10.0

3. *Dtetestprovider. cs* dosyasında aşağıdaki `using` yönergeleri ekleyin:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. `DTETestProvider`Sınıfında bir alın <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> .

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. Yönteminde, `GetClassifier()` aşağıdaki kodu `return` deyimden önce ekleyin:

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. Aşağıdaki derleme başvurularını projeye ekleyin:

   - EnvDTE
   - Microsoft. VisualStudio. Shell. Framework

3. *Dtetestprovider. cs* dosyasında aşağıdaki `using` yönergeleri ekleyin:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. `DTETestProvider`Sınıfında bir alın <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> .

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. Yönteminde, `GetClassifier()` aşağıdaki kodu `return` deyimden önce ekleyin:

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Dil hizmeti ve Düzenleyici uzantı noktaları](../extensibility/language-service-and-editor-extension-points.md)
- [DTE kullanarak Visual Studio’yu Başlatma](launch-visual-studio-dte.md)
