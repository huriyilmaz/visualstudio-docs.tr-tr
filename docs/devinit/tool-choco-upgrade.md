---
title: choco-upgrade
description: devinit aracı Choco-Upgrade.
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
ms.openlocfilehash: bcd2288ef9399f27f53565ea7ea971579cad7858
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725368"
---
# <a name="choco-upgrade"></a>choco-upgrade

> [!IMPORTANT]
> 12 nisan 2021 itibariyle, Visual Studio 2019 ' den GitHub codespaces 'a bağlanmak artık desteklenmeyecektir ve bu özel önizleme sona ermiştir. bulut destekli bir iç döngü ve çok sayıda Visual Studio iş yükü için iyileştirilmiş vdı çözümleri için gelişen deneyimler üzerinde odaklanıyoruz. Bu `devinit` ve ilişkili araçların bir parçası olarak artık kullanılabilir olmayacaktır. gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi edinmek için Visual Studio geliştirici topluluğu forumumuza dahil etmeniz önerilir.

`choco-upgrade`Araç, [Chocolatey](https://chocolatey.org/docs/commandsupgrade) paketlerini yüklemek ve güncelleştirmek için kullanılabilir.

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa araç hiçbir şey yapmaz.

| Ad                                             | Tür   | Gerekli  | Değer                                                                                                          |
|--------------------------------------------------|--------|-----------|----------------------------------------------------------------------------------------------------------------|
| **yorumlar**                                     | dize | No        | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                                                          |
| [**girişinin**](#input)                              | string | Yes       | Yükseltilecek paket. Ayrıntılar için aşağıdaki [girişi](#input) inceleyin.                                                 |
| [**additionalOptions**](#additional-options)     | dize | No        | Araca geçirilecek ek seçenekler. Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.       |

### <a name="input"></a>Giriş

`input`Özelliği, Yükseltilecek paketin adını (örneğin ' MongoDB ') veya aşağıdaki biçimlerdeki bir yapılandırma dosyasının yolunu belirtmek için kullanılır _packages.config_, _. nuspec_ ve _. nupkg_. Değeri, `input` öğesine `choco upgrade` `choco upgrade mongodb` özgü bağımsız değişkenlerle birlikte (örneğin,) [`additionalOptions`](#additional-options) ve yerleşik `choco` seçeneklere ( [aşağıda](#built-in-options)tanımlanmıştır) eklenir. Paketler [Chocolatey paket galerisinde](https://chocolatey.org/packages)bulunabilir. Bir yapılandırma dosyası kullanırken, bu dosyanın yolunu özelliğinde geçirebilirsiniz, `input` Örneğin: `"input":"packages.config"` .

### <a name="additional-options"></a>Ek seçenekler

Ek yapılandırma seçenekleri ' ın bir değeri olarak geçirilebilir `additionalOptions` . Bu bağımsız değişkenler tarafından kullanılan bağımsız değişkenlere doğrudan geçiş yapılır [`choco upgrade`](https://chocolatey.org/docs/commands-upgrade) ve Chocolatey belgelerinde tanımlanmıştır.

### <a name="built-in-options"></a>Yerleşik Seçenekler

`choco-upgrade`Araç, gözetimsiz bir şekilde `choco` çalışmasını sağlamak için bir dizi komut satırı bağımsız değişkeni ayarlar `choco` . Bu bağımsız değişkenler aşağıda listelenmiştir ve bunlarla ilgili belgeler [Chocolatey belgelerinde](https://chocolatey.org/docs/)bulunabilir.

| Ad                  | Açıklama                                                                                        |
|-----------------------|----------------------------------------------------------------------------------------------------|
| **--Evet**             | Tüm istemleri Onayla-istem yerine onaylama yanıtını seçer. Şunu gösterir `--accept-license` . |
| **--devam ediyor**     | İlerleme durumunu gösterme-Ilerleme yüzdeleri gösterilmez.                                         |
| **--Skip-PowerShell** | PowerShell 'i atla-chocolateyInstall.ps1 çalıştırılmayacaktır.                                              |

### <a name="default-behavior"></a>Varsayılan davranış

`choco-upgrade`Özelliğin gerekli olduğu şekilde aracın varsayılan davranışı hata olur `input` .

## <a name="example-usage"></a>Örnek kullanım
Kullanarak nasıl çalıştırılacağını gösteren örnekler aşağıda verilmiştir `choco-upgrade` `.devinit.json` .

#### <a name="devinitjson-that-will-update-packages-listed-in-packagesconfig"></a>packages.config listelenen paketleri güncelleştirecek. devinit. JSON:
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

#### <a name="devinitjson-that-will-upgrade-mongodb"></a>MongoDB 'yi yükseltecek. devinit. JSON:
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

#### <a name="devinitjson-that-will-upgrade-to-a-specific-version-of-mongodb"></a>MongoDB 'nin belirli bir sürümüne yükseltilecek. devinit. JSON:
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