---
title: azurecli-login
description: devinit aracı azurecli-oturum açma.
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
ms.openlocfilehash: 64b215912c21a405c2b2c3a0feb3720a4ab16c44
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104671667"
---
# <a name="azurecli-login"></a>azurecli-login

> [!IMPORTANT]
> 12 Nisan 2021 itibariyle, Visual Studio 2019 ' den GitHub Codespaces 'a bağlanmak artık desteklenmeyecektir ve bu özel önizleme sona ermiştir. Bulut destekli bir iç döngü ve çok sayıda Visual Studio iş yükü için iyileştirilmiş VDı çözümleri için gelişen deneyimlere odaklanıyoruz. Bu `devinit` ve ilişkili araçların bir parçası olarak artık kullanılabilir olmayacaktır. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi için, Visual Studio için geliştirici topluluğu forumumuza dahil etmeniz önerilir.

`azurecli-login`Araç, [Azure clı](/cli/azure/authenticate-azure-cli?preserve-view=true&view=azure-cli-latest)aracılığıyla Azure Active Directory oturum açmak için kullanılır. Bu araç Azure CLı komutunu kullanır: `az login --use-device-code` , oturum açma işleminin tamamlanabilmesi için konsola yazdırılan yönergeleri izlemeniz gerekir.

## <a name="usage"></a>Kullanım

Her iki özellik de atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak açıklanan [varsayılan](#default-behavior) davranışı izler.

| Ad                                             | Tür   | Gerekli | Değer                                                                          |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------|
| **açıklamaları**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                          |
| [**girişinin**](#input)                              | dize | No       | Kullanılmadı. Ayrıntılar için aşağıdaki [girişi](#input) inceleyin.                               |
| [**additionalOptions**](#additional-options)     | dize | No       | Kullanılmadı. Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.     |

### <a name="input"></a>Giriş

Kullanılmadı.

### <a name="additional-options"></a>Ek seçenekler

Kullanılmadı.

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan davranışı, `azurecli-login` en son Azure CLI sürümünü yüklemek ve ' a eklemektir `PATH` .

## <a name="example-usage"></a>Örnek kullanım
Kullanarak nasıl çalıştırılacağını gösteren bir örnek aşağıda verilmiştir `azurecli-login` `.devinit.json` .

#### <a name="devinitjson-that-will-trigger-azure-login"></a>Azure oturum açma tetiklenecek .devinit.js:

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "azurecli-login"
        }
    ]
}
```