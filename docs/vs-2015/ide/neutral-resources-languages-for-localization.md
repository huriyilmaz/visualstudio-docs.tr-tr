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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670385"
---
# <a name="neutral-resources-languages-for-localization"></a>Yerelleştirme İçin Bağımsız Kaynak Dilleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:System.Resources.NeutralResourcesLanguageAttribute>Sınıfı, ana derlemede yer alan kaynakların kültürünü belirtir. Bu öznitelik, bir performans geliştirmesi olarak kullanılır, böylece <xref:System.Resources.ResourceManager> nesne ana derlemede yer alan kaynakları aramaz.

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
 <xref:System.Resources.ResourceManager>[Yerelleştirme yerelleştirmesini sağlamak Için kaynakların hiyerarşik .NET Framework hiyerarşik kuruluşuna](../ide/hierarchical-organization-of-resources-for-localization.md) [Localizing Applications](../ide/localizing-applications.md) [göre uluslararası uygulamalara giriş,](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md) [uygulamaları Genelleştirme ve yerelleştirme](../ide/globalizing-and-localizing-applications.md)
