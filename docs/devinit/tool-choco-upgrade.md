---
title: choco-upgrade
description: devinit aracı Choco-Upgrade.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 7db97694e129fe5c70de09aaf4c132656ae00746
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672228"
---
# <a name="choco-upgrade"></a>choco-upgrade

`choco-upgrade`Araç, [Chocolatey](https://chocolatey.org/docs/commandsupgrade) paketlerini yüklemek ve güncelleştirmek için kullanılabilir.

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa araç hiçbir şey yapmaz.

| Ad                                             | Tür   | Gerekli | Değer                                                                                                          |
|--------------------------------------------------|--------|----------|----------------------------------------------------------------------------------------------------------------|
| **açıklamaları**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                                                          |
| [**girişinin**](#input)                              | dize | No       | Yükseltilecek paket. Ayrıntılar için aşağıdaki [girişi](#input) inceleyin.                                                 |
| [**additionalOptions**](#additional-options)     | dize | No       | Araca geçirilecek ek seçenekler. Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.       |

### <a name="input"></a>Girdi

`input`Özelliği, Yükseltilecek paketin adını (örneğin ' MongoDB ') veya aşağıdaki biçimlerdeki bir yapılandırma dosyasının yolunu belirtmek için kullanılır _packages.config_, _. nuspec_ ve _. nupkg_. Değeri, `input` öğesine `choco upgrade` `choco upgrade mongodb` özgü bağımsız değişkenlerle birlikte (örneğin,) [`additionalOptions`](#additional-options) ve yerleşik `choco` seçeneklere ( [aşağıda](#built-in-options)tanımlanmıştır) eklenir. Paketler [Chocolatey paket galerisinde](https://chocolatey.org/packages)bulunabilir. Bir yapılandırma dosyası kullanırken, bu dosyanın yolunu özelliğinde geçirebilirsiniz, `input` Örneğin: `"input":"packages.config"` .

### <a name="additional-options"></a>Ek seçenekler

Ek yapılandırma seçenekleri ' ın bir değeri olarak geçirilebilir `additionalOptions` . Bu bağımsız değişkenler tarafından kullanılan bağımsız değişkenlere doğrudan geçiş yapılır [`choco upgrade`](https://chocolatey.org/docs/commands-upgrade) ve Chocolatey belgelerinde tanımlanmıştır.

## <a name="built-in-options"></a>Yerleşik Seçenekler

`choco-upgrade`Araç, gözetimsiz bir şekilde `choco` çalışmasını sağlamak için bir dizi komut satırı bağımsız değişkeni ayarlar `choco` . Bu bağımsız değişkenler aşağıda listelenmiştir ve bunlarla ilgili belgeler [Chocolatey belgelerinde](https://chocolatey.org/docs/)bulunabilir.

| Ad                  | Açıklama                                                                                        |
|-----------------------|----------------------------------------------------------------------------------------------------|
| **--Evet**             | Tüm istemleri Onayla-istem yerine onaylama yanıtını seçer. Şunu gösterir `--accept-license` . |
| **--devam ediyor**     | İlerleme durumunu gösterme-Ilerleme yüzdeleri gösterilmez.                                         |
| **--Skip-PowerShell** | PowerShell 'i atla-chocolateyInstall.ps1 çalıştırılmayacaktır.                                              |

## <a name="example-usage"></a>Örnek kullanım
Kullanarak nasıl çalıştırılacağını gösteren örnekler aşağıda verilmiştir `choco-upgrade` `.devinit.json` . 

#### <a name="devinitjson-that-will-update-packages-listed-in-packagesconfig"></a>.devinit.js, packages.config listelenen paketleri güncelleştirecek:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-upgrade",
            "input": "packages.config",
        }
    ]
}
```

#### <a name="devinitjson-that-will-upgrade-mongodb"></a>MongoDB 'yi yükseltecektir .devinit.js:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-upgrade",
            "input": "mongodb"
        }
    ]
}
```

#### <a name="devinitjson-that-will-upgrade-to-a-specific-version-of-mongodb"></a>.devinit.js, MongoDB 'nin belirli bir sürümüne yükseltecektir:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-upgrade",
            "input": "mongodb",
            "additionalOptions": "--version 4.2.7"
        }
    ]
}
```