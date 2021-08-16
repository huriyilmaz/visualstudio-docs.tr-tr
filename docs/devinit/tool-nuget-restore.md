---
title: nuget-restore
description: devinit tool nuget-restore.
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
ms.openlocfilehash: b7675b46697900382917cceaf83922968b800a7885f02e0046477c06a2188ad8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121390616"
---
# <a name="nuget-restore"></a>nuget-restore

> [!IMPORTANT]
> 12 Nisan 2021'den itibaren Visual Studio 2019'dan GitHub Codespaces'a bağlanma desteklemeyecek ve bu özel önizleme sonuçlandırıldı. Bulut destekli iç döngü için gelişen deneyimlere ve çok çeşitli iş yükleri için iyileştirilmiş VDI çözümlerine Visual Studio odaklanacağız. Bu ve ilişkili `devinit` araçların bir parçası olarak artık kullanılamaz. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi için Visual Studio geliştirici topluluğu forummize katılın.

Araç, `nuget-restore` proje dosyasında belirtilen bağımlılıkları ve projeye özgü araçları geri yükleme. Geri yükleme hakkında daha NuGet buradan [okuyun.](/nuget/reference/cli-reference/cli-ref-restore)

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak [açıklanmış varsayılan](#default-behavior) davranışı takip eder.

| Ad                                             | Tür   | Gerekli | Değer                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **yorumlar**                                     | dize | No       | İsteğe bağlı açıklamalar özelliği. Kullanılmadı.                                                |
| [**Giriş**](#input)                              | dize | No       | Geri yüklemek için proje/çözüm dosyasının yolu. Ayrıntılar [için](#input) aşağıdaki girişe bakın. |
| [**additionalOptions**](#additional-options)     | dize | No       | Ayrıntılar [için aşağıdaki](#additional-options) Ek seçenekler'e bakın.                     |

### <a name="input"></a>Giriş

Geri yüklemek için proje/çözüm dosyasının yolu.

### <a name="additional-options"></a>Ek seçenekler

Ek seçenekler, geri yükleme komutuna olduğu NuGet geçirildi.

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan davranışı `nuget-restore` geçerli dizinde `NuGet restore` çalıştırmaktır.

## <a name="example-usage"></a>Örnek kullanım
Aşağıda, kullanarak çalıştırmaya bir `nuget-restore` örnek `.devinit.json` verilmiştir.

#### <a name="devinitjson-that-will-restore-dependencies-and-tools-of-a-project"></a>.devinit.jsprojenin bağımlılıklarını ve araçlarını geri yüklemesini sağlar:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "nuget-restore",
            "input": "C:\\nuget\\Nuget.config"
        }
    ]
}
```