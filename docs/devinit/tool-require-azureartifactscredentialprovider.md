---
title: gerektir-azureartifactscredentialprovider
description: devinit Aracı,-azureartifactscredentialprovider gerektirir.
ms.date: 08/28/2020
ms.topic: reference
author: andster
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 74e8775fb9dc864e8026f73e3bc75604dbf32e10
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810914"
---
# <a name="require-azureartifactscredentialprovider"></a>gerektir-azureartifactscredentialprovider

`require-azureartifactscredentialprovider`Araç Azure Artifacts kimlik bilgisi sağlayıcısını yüklüyor. Azure Artifacts kimlik bilgisi sağlayıcısı, .NET geliştirme iş akışınızın bir parçası olarak NuGet paketlerini geri yüklemek için gereken kimlik bilgilerinin alımını otomatikleştirir. Azure Artifacts kimlik [bilgisi sağlayıcısı hakkında](https://github.com/microsoft/artifacts-credprovider/blob/master/README.md)daha fazla bilgi edinin.

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak açıklanan [varsayılan](#default-behavior) davranışı izler.

| Ad                                             | Tür   | Gerekli | Değer                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **açıklamaları**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                                |
| [**girişinin**](#input)                              | dize | No       | Kullanılmadı. Ayrıntılar için aşağıdaki [girişi](#input) inceleyin. |
| [**additionalOptions**](#additional-options)     | dize | No       | Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.                     |

### <a name="input"></a>Giriş

Kullanılmadı. Bahsedildiğinde herhangi bir girişi yoksayar.

### <a name="additional-options"></a>Ek seçenekler

Ek seçenekler, kimlik bilgisi sağlayıcısı komutuna olduğu gibi geçirilir.

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan davranışı, `require-azureartifactscredentialprovider` Azure Artifacts kimlik bilgisi sağlayıcısı 'nın en son sürümünü yüklemektir.

## <a name="example-usage"></a>Örnek kullanım

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "comments": "A sample dot-devinit file that installs Azure Artifacts Credential Provider.'",
    "run": [
        {
            "tool": "require-azureartifactscredentialprovider",
            "comments": "Installs Azure Artifacts Credential Provider."
        }
    ]
}
```
