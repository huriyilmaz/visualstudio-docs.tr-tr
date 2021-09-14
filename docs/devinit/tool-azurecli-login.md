---
title: azurecli-login
description: devinit tool azurecli-login.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725370"
---
# <a name="azurecli-login"></a>azurecli-login

> [!IMPORTANT]
> 12 Nisan 2021'den itibaren GitHub Codespaces'a Visual Studio 2019'dan bağlanmak artık desteklemeyecek ve bu özel önizlemenin sonucuna varıldı. Bulut destekli iç döngü için gelişen deneyimlere ve çok çeşitli iş yükleri için iyileştirilmiş VDI çözümlerine Visual Studio odaklanacağız. Bu ve ilişkili `devinit` araçların bir parçası olarak artık kullanılamaz. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi için Visual Studio geliştirici topluluğu forummize katılın.

Araç, `azurecli-login` Azure CLI aracılığıyla Azure Active Directory için [kullanılır.](/cli/azure/authenticate-azure-cli?preserve-view=true&view=azure-cli-latest) Bu araç, oturum açma işlemini tamamlamak için konsola yazdırılan yönergeleri izlemeniz gereken Azure CLI `az login --use-device-code` komutunu kullanır.

## <a name="usage"></a>Kullanım

Her iki özellik de atlanırsa veya boşsa, araç aşağıda ayrıntılı [olarak açıklanmış varsayılan](#default-behavior) davranışı takip eder.

| Ad                                             | Tür   | Gerekli | Değer                                                                          |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------|
| **yorumlar**                                     | dize | No       | İsteğe bağlı açıklamalar özelliği. Kullanılmadı.                                          |
| [**Giriş**](#input)                              | dize | No       | Kullanılmadı. Ayrıntılar [için](#input) aşağıdaki Giriş'e bakın.                               |
| [**additionalOptions**](#additional-options)     | dize | No       | Kullanılmadı. Ayrıntılar [için aşağıdaki](#additional-options) Ek seçeneklere bakın.     |

### <a name="input"></a>Giriş

Kullanılmadı.

### <a name="additional-options"></a>Ek seçenekler

Kullanılmadı.

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan `azurecli-login` davranışı, Azure CLI'nın en son sürümünü yüklemek ve 'ye eklemektir. `PATH`

## <a name="example-usage"></a>Örnek kullanım
Aşağıda, kullanarak çalıştırmaya bir `azurecli-login` örnek `.devinit.json` verilmiştir.

#### <a name="devinitjson-that-will-trigger-azure-login"></a>Azure oturum açma bilgilerini tetikleyen .devinit.json:

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