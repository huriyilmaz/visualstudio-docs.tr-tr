---
title: require-azurecli
description: devinit tool require-azurecli.
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
ms.openlocfilehash: 84b6506f2aa9c284a97521bf865572773f61908b2def3ef17644cc20234ac037
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121390560"
---
# <a name="require-azurecli"></a>require-azurecli

> [!IMPORTANT]
> 12 Nisan 2021'den itibaren, Visual Studio 2019'dan GitHub Codespaces'a bağlanmak artık desteklemeyecek ve bu özel önizlemenin sonucuna varıldı. Bulut destekli iç döngü için gelişen deneyimlere ve çok çeşitli iş yükleri için iyileştirilmiş VDI çözümlerine Visual Studio odaklanacağız. Bu ve ilişkili `devinit` araçların bir parçası olarak artık kullanılamaz. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi almak Visual Studio geliştirici topluluğu forummize dahil olmak için sizi teşvik ediyoruz.

Araç, `require-azurecli` Azure CLI MSI aracılığıyla Azure [CLI'sini](/cli/azure/?view=azure-cli-latest&preserve-view=true) yüklemek için kullanılır.

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı [olarak açıklanmış varsayılan](#default-behavior) davranışı takip eder.

| Ad                                             | Tür   | Gerekli | Değer                                                                          |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------|
| **yorumlar**                                     | dize | No       | İsteğe bağlı açıklamalar özelliği. Kullanılmadı.                                          |
| [**Giriş**](#input)                              | dize | No       | Kullanılmadı. Ayrıntılar [için](#input) aşağıdaki Giriş'e bakın.                               |
| [**additionalOptions**](#additional-options)     | dize | No       | Kullanılmadı. Ayrıntılar [için aşağıdaki](#additional-options) Ek seçenekler'e bakın.     |

### <a name="input"></a>Giriş

Kullanılmadı.

### <a name="additional-options"></a>Ek seçenekler

Kullanılmadı.

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan `require-azurecli` davranışı, Azure CLI'nin en son sürümünü yüklemek ve 'ye eklemektir. `PATH`

## <a name="example-usage"></a>Örnek kullanım
Aşağıda, kullanarak çalıştırmaya bir `require-azurecli` örnek `.devinit.json` verilmiştir.

#### <a name="devinitjson-that-will-install-the-azure-cli"></a>.devinit.jsAzure CLI'sini yükleyecek olan
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-azurecli"
        }
    ]
}
```