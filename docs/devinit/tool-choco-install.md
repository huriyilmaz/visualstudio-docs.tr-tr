---
title: Choco-install
description: Chocolatey paketlerini yüklemek için devinit aracı Choco-Install.
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
ms.openlocfilehash: 0ad4c5c772ac9028ec369fe7cc63e1a2f7af6931
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810167"
---
# <a name="choco-install"></a>Choco-install

`choco-install`Araç, [Chocolatey](https://chocolatey.org/) paketlerini yüklemek ve güncelleştirmek için kullanılabilir.

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa araç hiçbir şey yapmaz.

| Ad                                             | Tür   | Gerekli | Değer                                                                                                          |
|--------------------------------------------------|--------|----------|----------------------------------------------------------------------------------------------------------------|
| **açıklamaları**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                                                          |
| [**girişinin**](#input)                              | dize | No       | Yüklenecek paket. Ayrıntılar için aşağıdaki [girişi](#input) inceleyin.                                                 |
| [**additionalOptions**](#additional-options)     | dize | No       | Araca geçirilecek ek seçenekler. Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.       |

### <a name="input"></a>Giriş

`input`Özelliği, Yüklenecek paketin adını (örneğin ' MongoDB ') veya aşağıdaki biçimlerdeki bir yapılandırma dosyasının yolunu belirtmek için kullanılır _packages.config_, _. nuspec_ve _. nupkg_. Değeri, `input` öğesine `choco install` `choco install mongodb` özgü bağımsız değişkenlerle birlikte (örneğin,) [`additionalOptions`](#additional-options) ve yerleşik `choco` seçeneklere ( [aşağıda](#built-in-options)tanımlanmıştır) eklenir. Paketler [Chocolatey paket galerisinde](https://chocolatey.org/packages)bulunabilir. Bir yapılandırma dosyası kullanırken, bu dosyanın yolunu, `input` Örneğin, özelliğinde geçirebilirsiniz `"input":"packages.config"` .

### <a name="additional-options"></a>Ek seçenekler

Ek yapılandırma seçenekleri ' ın bir değeri olarak geçirilebilir `additionalOptions` . Bu bağımsız değişkenler tarafından kullanılan bağımsız değişkenlere doğrudan geçiş yapılır [`choco install`](https://chocolatey.org/docs/commands-install) ve Chocolatey belgelerinde tanımlanmıştır.

### <a name="built-in-options"></a>Yerleşik Seçenekler

`choco-install`Araç, gözetimsiz bir şekilde `choco` çalışmasını sağlamak için bir dizi komut satırı bağımsız değişkeni ayarlar `choco` . Bu bağımsız değişkenler aşağıda listelenmiştir ve bunlarla ilgili belgeler [Chocolatey belgelerinde](https://chocolatey.org/docs/)bulunabilir.

| Ad                  | Açıklama                                                                                        |
|-----------------------|----------------------------------------------------------------------------------------------------|
| **--Evet**             | Tüm istemleri Onayla-istem yerine onaylama yanıtını seçer. Gibi `--accept-license.` |
| **--devam ediyor**     | İlerleme durumunu gösterme-Ilerleme yüzdeleri gösterilmez.                                         |
| **--Skip-PowerShell** | PowerShell 'i atla-chocolateyInstall.ps1 çalıştırılmayacaktır.                                              |

## <a name="example-usage"></a>Örnek kullanım

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will trigger the Default behavior of installing packages listed in a packages.config file.",
            "tool": "choco-install",
            "input": "packages.config",
        },
        {
            "comments": "Example that will install the package 'mongodb'.",
            "tool": "choco-install",
            "input": "mongodb"
        },
        {
            "comments": "Example that will install the '4.2.7' version of 'mongodb'.",
            "tool": "choco-install",
            "input": "mongodb",
            "additionalOptions": "--version 4.2.7"
        }
    ]
}
```
