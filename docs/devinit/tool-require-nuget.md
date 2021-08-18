---
title: require-nuget
description: devinit tool require-nuget.
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
ms.openlocfilehash: fe907e78b694022a39768edf38c0f869234d51e7e1b6bdbbab62b1c797ac682d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121343233"
---
# <a name="require-nuget"></a>require-nuget

> [!IMPORTANT]
> 12 Nisan 2021'den itibaren Visual Studio 2019'dan GitHub Codespaces'a bağlanma desteklemeyecek ve bu özel önizleme sonuçlandırıldı. Bulut destekli iç döngü için gelişen deneyimlere ve çok çeşitli iş yükleri için iyileştirilmiş VDI çözümlerine Visual Studio odaklanacağız. Bu ve ilişkili `devinit` araçların bir parçası olarak artık kullanılamaz. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi için Visual Studio geliştirici topluluğu forummize katılın.

Araç, `require-nuget` NuGet CLI'sini indirir ve 'ye `PATH` ekler. NuGet CLI, proje dosyalarında hiçbir NuGet yapmadan paketleri yüklemek, oluşturmak, yayımlamak ve yönetmek için gereken tüm işlevleri sunar. CLI hakkında daha fazla NuGet burada [okuyun.](/nuget/reference/nuget-exe-cli-reference)

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak [açıklanmış varsayılan](#default-behavior) davranışı takip eder.

| Ad                                             | Tür   | Gerekli | Değer                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **yorumlar**                                     | dize | No       | İsteğe bağlı açıklamalar özelliği. Kullanılmadı.                                                |
| [**Giriş**](#input)                              | dize | No       | NuGet Yüklensin CLI sürümü. Ayrıntılar [için](#input) aşağıdaki girişe bakın. |
| [**additionalOptions**](#additional-options)     | dize | No       | Ayrıntılar [için aşağıdaki](#additional-options) Ek seçenekler'e bakın.                     |

### <a name="input"></a>Giriş

, `input` NuGet CLI sürümünün belirli bir sürümünü yüklemek için kullanılan isteğe bağlı bir özelliktir. `input`Atlanırsa, CLI'nın en son sürümü yüklenir.

### <a name="additional-options"></a>Ek seçenekler

Kullanılmadı.

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan davranışı, `require-nuget` NuGet CLI'nin en son sürümünü yüklemektir.

## <a name="example-usage"></a>Örnek kullanım
Aşağıda, kullanarak çalıştırmaya bir `require-nuget` örnek `.devinit.json` verilmiştir.

#### <a name="devinitjson-that-will-install-a-specified-version-of-nuget"></a>.devinit.jsbelirtilen sürümü yükecek olan NuGet:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-nuget",
            "input": "5.5.1",
        }
    ]
}
```