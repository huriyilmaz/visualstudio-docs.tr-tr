---
title: Yerelleştirme için bağımsız kaynak dilleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- localization [Visual Studio], resources
- NeutralResourcesLanguageAttribute class
- globalization [Visual Studio], resources
- resources [Visual Studio], fallback system
- culture, locating resources
- neutral resources
ms.assetid: ef064995-3b84-4698-a708-9689b7723533
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 85e0be0172f27732f8efeb882cbcde5b9c6aef3d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670385"
---
# <a name="neutral-resources-languages-for-localization"></a>Yerelleştirme İçin Bağımsız Kaynak Dilleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

@No__t_0 sınıfı, ana derlemede yer alan kaynakların kültürünü belirtir. Bu öznitelik, <xref:System.Resources.ResourceManager> nesnesinin ana derlemede yer alan kaynakları araymaması için performans geliştirmesi olarak kullanılır.

 Aşağıdaki kod, nötr kaynaklar dilinin nasıl ayarlanacağını gösterir. Kod, derleme betiğine veya AssemblyInfo. vb ya da AssemblyInfo.cs dosyasına yerleştirilebilir.

```vb
' Set neutral resources language for assembly.
<Assembly: NeutralResourcesLanguageAttribute("en")>

```

```csharp
// Set neutral resources language for assembly.
[assembly: NeutralResourcesLanguageAttribute("en")]
```

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Resources.ResourceManager>, [Yerelleştirme yerelleştirmesini sağlamak Için kaynak .NET Framework hiyerarşik kuruluşa](../ide/hierarchical-organization-of-resources-for-localization.md) [](../ide/localizing-applications.md) [göre uluslararası uygulamalara giriş,](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md) [uygulamaları Genelleştirme ve yerelleştirme](../ide/globalizing-and-localizing-applications.md)
