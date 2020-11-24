---
title: require-azurecli
description: devinit aracı-azurecli gerektirir.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: d73fe7c1745ded16ca6b0c94acf117c1707c1063
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440424"
---
# <a name="require-azurecli"></a>require-azurecli

Araç Azure CLI `require-azurecli` MSI aracılığıyla [Azure CLI](/cli/azure/?view=azure-cli-latest&preserve-view=true) 'yı yüklemek için kullanılır.

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak açıklanan [varsayılan](#default-behavior) davranışı izler.

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

Aracın varsayılan davranışı, `require-azurecli` en son Azure CLI sürümünü yüklemek ve ' a eklemektir `PATH` .

## <a name="example-usage"></a>Örnek kullanım
Kullanarak nasıl çalıştırılacağını gösteren bir örnek aşağıda verilmiştir `require-azurecli` `.devinit.json` .

#### <a name="devinitjson-that-will-install-the-azure-cli"></a>Azure CLı 'yı yükleyecek .devinit.js:
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