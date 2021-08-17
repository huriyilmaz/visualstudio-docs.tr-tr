---
title: choco-upgrade
description: devinit tool choco-upgrade.
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
ms.openlocfilehash: 63ea33101bbd0062ebab9dc74925ac98d7d206984d3ffdb256644618afbb86da
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121390672"
---
# <a name="choco-upgrade"></a>choco-upgrade

> [!IMPORTANT]
> 12 Nisan 2021'den itibaren Visual Studio 2019'dan GitHub Codespaces'a bağlanma desteklemeyecek ve bu özel önizleme sonuçlandırıldı. Bulut destekli iç döngü için gelişen deneyimlere ve çok çeşitli iş yükleri için iyileştirilmiş VDI çözümlerine Visual Studio odaklanacağız. Bu ve ilişkili `devinit` araçların bir parçası olarak artık kullanılamaz. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi için Visual Studio geliştirici topluluğu forummize katılın.

Araç, `choco-upgrade` çikolata paketlerini yüklemek ve güncelleştirmek [için](https://chocolatey.org/docs/commandsupgrade) kullanılabilir.

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa araç hiçbir şey yapmaz.

| Ad                                             | Tür   | Gerekli  | Değer                                                                                                          |
|--------------------------------------------------|--------|-----------|----------------------------------------------------------------------------------------------------------------|
| **yorumlar**                                     | dize | No        | İsteğe bağlı açıklamalar özelliği. Kullanılmadı.                                                                          |
| [**Giriş**](#input)                              | string | Yes       | Yükseltilen paket. Ayrıntılar [için](#input) aşağıdaki Giriş'e bakın.                                                 |
| [**additionalOptions**](#additional-options)     | dize | No        | Araç için ek geçiş seçenekleri. Ayrıntılar [için aşağıdaki](#additional-options) Ek seçenekler'e bakın.       |

### <a name="input"></a>Giriş

özelliği, yükseltilen paketin adını (örneğin , 'mongodb') veya aşağıdaki biçimlerde bir yapılandırma dosyasının yolunu `input` _(packages.config_, _.nuspec_ ve _.nupkg)_ belirtmek için kullanılır. değeri, komutuna (örneğin ) ve yerleşik seçeneklerine (aşağıda tanımlanmıştır) özgü bağımsız `input` `choco upgrade` `choco upgrade mongodb` [`additionalOptions`](#additional-options) `choco` değişkenlerle birlikte [eklenir.](#built-in-options) Paketler Chocolatey paket [galerisinde bulunabilir.](https://chocolatey.org/packages) Bir yapılandırma dosyası kullanırken, özelliğinde bu dosyanın yolunu `input` geçebilirsiniz, örneğin: `"input":"packages.config"` .

### <a name="additional-options"></a>Ek seçenekler

Ek yapılandırma seçenekleri değeri olarak `additionalOptions` geçirebilirsiniz. Bu bağımsız değişkenler tarafından kullanılan bağımsız değişkenlere doğrudan geçiştir [`choco upgrade`](https://chocolatey.org/docs/commands-upgrade) ve çikolatalı belgelerde tanımlanmıştır.

### <a name="built-in-options"></a>Yerleşik seçenekler

Araç, `choco-upgrade` başsız `choco` çalıştırılana kadar bir dizi komut satırı `choco` bağımsız değişkeni ayarlar. Bu bağımsız değişkenler aşağıda listelenmiştir ve bu bağımsız değişkenlerle ilgili belgeler [chocolatey belgelerinde bulunabilir.](https://chocolatey.org/docs/)

| Ad                  | Açıklama                                                                                        |
|-----------------------|----------------------------------------------------------------------------------------------------|
| **--yes**             | Tüm istemleri onaylayın - Sorularak değil, olumlu yanıtı seçer. anlamına `--accept-license` gelir. |
| **--no-progress**     | İlerlemeyi gösterme - İlerleme yüzdeleri gösterilmez.                                         |
| **--skip-powershell** | PowerShell'chocolateyInstall.ps1 atla - bu komutlar hiçbir zaman açık olmayacak.                                              |

### <a name="default-behavior"></a>Varsayılan davranış

Özelliğin gerekli olması `choco-upgrade` nedeniyle aracın varsayılan davranışı `input` hatadır.

## <a name="example-usage"></a>Örnek kullanım
Aşağıda, kullanarak çalıştırma örnekleri `choco-upgrade` `.devinit.json` verilmiştir.

#### <a name="devinitjson-that-will-update-packages-listed-in-packagesconfig"></a>.devinit.js' da listelenen paketleri güncelleştirecek packages.config:
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

#### <a name="devinitjson-that-will-upgrade-mongodb"></a>.devinit.jsMongoDB'yi yükseltecek olan tek şey:
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

#### <a name="devinitjson-that-will-upgrade-to-a-specific-version-of-mongodb"></a>.devinit.jsMongoDB'nin belirli bir sürümüne yükseltecek olan diğer sürümler:
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