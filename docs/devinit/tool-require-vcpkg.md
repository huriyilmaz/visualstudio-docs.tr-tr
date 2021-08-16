---
title: require-vcpkg
description: devinit tool require-vcpkg.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: d0e5f71d51e4e86f11b5b58f0b9a98f48f8d036056d3fef8bd5061151cef1845
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121378297"
---
# <a name="require-vcpkg"></a>require-vcpkg

> [!IMPORTANT]
> 12 Nisan 2021'den itibaren, Visual Studio 2019'dan GitHub Codespaces'a bağlanmak artık desteklemeyecek ve bu özel önizlemenin sonucuna varıldı. Bulut destekli iç döngü için gelişen deneyimlere ve çok çeşitli iş yükleri için iyileştirilmiş VDI çözümlerine Visual Studio odaklanacağız. Bu ve ilişkili `devinit` araçların bir parçası olarak artık kullanılamaz. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi almak Visual Studio geliştirici topluluğu forummize dahil olmak için sizi teşvik ediyoruz.

Araç, `require-vcpkg` 'i yüklemek [vcpkg.](https://github.com/microsoft/vcpkg)

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı [olarak açıklanmış varsayılan](#default-behavior) davranışı takip eder.

| Ad                                             | Tür   | Gerekli | Değer                                                                      |
|--------------------------------------------------|--------|----------|----------------------------------------------------------------------------|
| **yorumlar**                                     | dize | No       | İsteğe bağlı açıklamalar özelliği. Kullanılmadı.                                      |
| [**Giriş**](#input)                              | dize | No       | Kullanılmadı. Ayrıntılar [için](#input) aşağıdaki Giriş'e bakın.                           |
| [**additionalOptions**](#additional-options)     | dize | No       | Kullanılmadı. Ayrıntılar [için aşağıdaki](#additional-options) Ek seçenekler'e bakın. |

### <a name="input"></a>Giriş

Kullanılmadı.

### <a name="additional-options"></a>Ek seçenekler

Kullanılmadı.

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan `require-vcpkg` davranışı, vcpkg yüklemek ve 'ye eklemektir. `PATH`

## <a name="example-usage"></a>Örnek kullanım
Aşağıda, kullanarak çalıştırmaya bir `require-vcpkg` örnek `.devinit.json` verilmiştir.

#### <a name="devinitjson-that-will-install-vcpkg"></a>.devinit.js, şunları vcpkg:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-vcpkg"
        }
    ]
}
```
