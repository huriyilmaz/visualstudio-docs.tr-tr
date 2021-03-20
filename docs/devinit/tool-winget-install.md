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
ms.openlocfilehash: 4a2ad1ef30692d7d23f2d450f0ba32d6f38f8262
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672626"
---
# <a name="winget-install"></a>Winget-Install

> [!IMPORTANT]
> 12 Nisan 2021 itibariyle, Visual Studio 2019 ' den GitHub Codespaces 'a bağlanmak artık desteklenmeyecektir ve bu özel önizleme sona ermiştir. Bulut destekli bir iç döngü ve çok sayıda Visual Studio iş yükü için iyileştirilmiş VDı çözümleri için gelişen deneyimlere odaklanıyoruz. Bu `devinit` ve ilişkili araçların bir parçası olarak artık kullanılabilir olmayacaktır. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi için, Visual Studio için geliştirici topluluğu forumumuza dahil etmeniz önerilir.

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
