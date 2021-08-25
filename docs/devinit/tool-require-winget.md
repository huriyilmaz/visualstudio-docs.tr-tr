---
title: require-winget
description: devinit tool require-winget.
ms.date: 02/08/2021
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 3cc07190f125b071bae40587552e25cc9515fd6d
ms.sourcegitcommit: aef3e3f99e022675d339b7fe381cb37202be5be2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2021
ms.locfileid: "122785721"
---
# <a name="require-winget"></a>require-winget

> [!IMPORTANT]
> 12 Nisan 2021'den itibaren, Visual Studio 2019'dan GitHub Codespaces'a bağlanmak artık desteklemeyecek ve bu özel önizlemenin sonucuna varıldı. Bulut destekli iç döngü için gelişen deneyimlere ve çok çeşitli iş yükleri için iyileştirilmiş VDI çözümlerine Visual Studio odaklanacağız. Bu ve ilişkili `devinit` araçların bir parçası olarak artık kullanılamaz. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi almak Visual Studio geliştirici topluluğu forummize dahil olmak için sizi teşvik ediyoruz.

araç, `require-winget` [winget'i yüklemek için kullanılır.](/windows/package-manager/winget/) 
## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak [açıklanmış varsayılan](#default-behavior) davranışı takip eder.

| Ad                                             | Tür   | Gerekli | Değer                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **yorumlar**                                     | dize | No       | İsteğe bağlı açıklamalar özelliği. Kullanılmadı.                                                |
| [**Giriş**](#input)                              | dize | No       | Kullanılmadı.                                                                            |
| [**additionalOptions**](#additional-options)     | dize | No       | Kullanılmadı.                                                                            |

### <a name="input"></a>Giriş

Kullanılmadı.

### <a name="additional-options"></a>Ek seçenekler

Kullanılmadı.

### <a name="default-behavior"></a>Varsayılan davranış

Aracın Varsayılan `require-winget` davranışı, git deposunu kullanarak en son [ `winget-cli` sürümü yüklemektir.](https://github.com/microsoft/winget-cli)

## <a name="example-usage"></a>Örnek kullanım

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-6.0",
    "comments": "Example that installs the latest version of winget",
    "run": [
        {
            "tool": "require-winget",
            "comments": "Installs winget",
        }
    ]
}
```
