---
title: Winget-Install
description: Winget için devinit aracı.
ms.date: 02/08/2021
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 3c236e63686d3882ed199c122fed9ebddfa8fa20
ms.sourcegitcommit: e262f4c2a147c3fa2d27de666aae3a0497317867
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2021
ms.locfileid: "100012370"
---
# <a name="winget-install"></a>Winget-Install

`winget-install`Araç, [Winget paketlerini](https://docs.microsoft.com/windows/package-manager/winget/)yüklemek için kullanılır.

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa araç bir hata çıktısı olur.

| Ad                                         | Tür   | Gerekli | Değer                                                                             |
|----------------------------------------------|--------|----------|-----------------------------------------------------------------------------------|
| **açıklamaları**                                 | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                             |
| [**girişinin**](#input)                          | dize | No       | Yüklenecek paket. Ayrıntılar için aşağıdaki [girişi](#input) inceleyin.                    |
| [**additionalOptions**](#additional-options) | dize | No       | Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.                  |

### <a name="input"></a>Giriş

Giriş özelliği, `Id` `Name` Yüklenecek paketin veya uygulamasının (örneğin ' MongoDB. Server ') belirtilmesi için kullanılır. Girişin değeri bir `winget install` komuta eklenir (örneğin `winget install MongoDB.Server` ). Paket adı benzersiz değilse ve diğer paketlerle eşleşiyorsa, paketin `Id` kimliğini belirtebilir ve `--exact` `additionalOptions` paket kimliğinin tam olarak eşleştiğinden emin olmak için bayrağını öğesine ekleyebilirsiniz. `Id`Bir paketin, `winget search` komutu yürüterek ve `Id` bir paketin parametresi kullanılarak bulunması bulunabilir.  

### <a name="additional-options"></a>Ek seçenekler

Ek yapılandırma seçenekleri additionalOptions değeri olarak geçirilebilir. Bu bağımsız değişkenler tarafından kullanılan bağımsız değişkenlere doğrudan geçiş yapılır `winget install` ve `winget install` [belgelerde](https://docs.microsoft.com/windows/package-manager/winget/install)tanımlanmıştır.

#### <a name="manifests"></a>Listeleri

Tarafından desteklenen ek bir isteğe bağlı, `winget` Yüklenecek paketin ayrıntısına bir [bildirim dosyası](https://docs.microsoft.com/windows/package-manager/winget/install#local-install) sağlama yeteneğidir. Bu özelliği devinit ile kullanmak için `input` parametresi boş olmalıdır ve bu özellik, `additionalOptions` `--manifest` bildirimin yolunu izlemelidir (örneğin `--manifest path.to.manifest.yml` ).

### <a name="built-in-options"></a>Yerleşik Seçenekler

Winget-Install Aracı, wınget 'in gözetimsiz olarak çalışmasını sağlamak için bir dizi Winget komut satırı bağımsız değişkeni ayarlar. Bu bağımsız değişkenler aşağıda listelenmiştir ve belgelerde yer alan belgeler bulunabilir `winget install` [](https://docs.microsoft.com/windows/package-manager/winget/install).

| Ad     | Açıklama                                                                                                                       |
|----------|-----------------------------------------------------------------------------------------------------------------------------------|
| --sessiz | Yükleyiciyi sessiz modda çalıştırır. Bu, tüm Kullanıcı arabirimini bastırır. Varsayılan deneyim yükleyicinin ilerlemesini gösterir.                       | 

## <a name="example-usage"></a>Örnek kullanım

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-6.0",
    "run": [
        {
            "comments": "Installs Microsoft PowerToys.",
            "tool": "winget-install",
            "input": "Microsoft.PowerToys",
            "additionalOptions": "--version 0.15.2",
        },
        {
            "comments": "Installs PostgreSQL.",
            "tool": "winget-install",
            "input": "PostgreSQL.PostgreSQL",
            "additionalOptions": "--exact"
        },
        {
            "comments": "Installs the package defined in winget-manifest.yml.",
            "tool": "winget-install",
            "additionalOptions": "--manifest winget-manifest.yml"
        }
    ]
}
```
