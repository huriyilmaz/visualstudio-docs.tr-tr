---
title: choco-install
description: Chocolatey paketlerini yüklemek için devinit aracı choco-install.
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
ms.openlocfilehash: 075d085e12926f30ea9e71512decb2fb77b7456cdfb3502295e7a40b6dff39b9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121390714"
---
# <a name="choco-install"></a>choco-install

> [!IMPORTANT]
> 12 Nisan 2021'den itibaren Visual Studio 2019'dan GitHub Codespaces'a bağlanma desteklemeyecek ve bu özel önizleme sonuçlandırıldı. Bulut destekli iç döngü için gelişen deneyimlere ve çok çeşitli iş yükleri için iyileştirilmiş VDI çözümlerine Visual Studio odaklanacağız. Bu ve ilişkili `devinit` araçların bir parçası olarak artık kullanılamaz. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi için Visual Studio geliştirici topluluğu forummize katılın.

Araç, `choco-install` çikolata paketlerini yüklemek ve güncelleştirmek [için](https://chocolatey.org/) kullanılabilir.

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa araç hiçbir şey yapmaz.

| Ad                                             | Tür   | Gerekli  | Değer                                                                                                          |
|--------------------------------------------------|--------|-----------|----------------------------------------------------------------------------------------------------------------|
| **yorumlar**                                     | dize | No        | İsteğe bağlı açıklamalar özelliği. Kullanılmadı.                                                                          |
| [**Giriş**](#input)                              | string | Yes       | Yüklenilen paket. Ayrıntılar [için](#input) aşağıdaki Giriş'e bakın.                                                 |
| [**additionalOptions**](#additional-options)     | dize | No        | Aracı geçmek için ek seçenekler. Ayrıntılar [için aşağıdaki](#additional-options) Ek seçenekler'e bakın.       |

### <a name="input"></a>Giriş

özelliği, yüklemek için paketin adını (örneğin,'mongodb') veya aşağıdaki biçimlerde bir yapılandırma dosyasının yolunu belirtmek için kullanılır `input` _packages.config_, _.nuspec_ ve _.nupkg._ değeri, komutuna (örneğin ) ve yerleşik seçeneklerine (aşağıda tanımlanmıştır) özgü bağımsız `input` `choco install` `choco install mongodb` [`additionalOptions`](#additional-options) `choco` değişkenlerle birlikte [eklenir.](#built-in-options) Paketler [Chocolatey paket galerisinde bulunur.](https://chocolatey.org/packages) Bir yapılandırma dosyası kullanırken, özelliğinde bu dosyanın yolunu `input` (örneğin, ) `"input":"packages.config"` geçebilirsiniz.

### <a name="additional-options"></a>Ek seçenekler

Ek yapılandırma seçenekleri değeri olarak `additionalOptions` geçirebilirsiniz. Bu bağımsız değişkenler tarafından kullanılan bağımsız değişkenlere doğrudan geçiştir [`choco install`](https://chocolatey.org/docs/commands-install) ve çikolatalı belgelerde tanımlanmıştır.

#### <a name="adding-new-feeds-to-chocolatey"></a>Chocolatey'ye yeni akışlar ekleme
Chocolatey'ye komutuna benzer şekilde yeni bir akış eklemek `choco source add` için komutuna `additionalOptions` geçebilirsiniz. Yeni akış eklemeye örnek olarak Örnek [kullanım'dır.](#example-usage) Özel akış eklemek isterseniz, kimlik bilgileri gerektirdiği için aracı komut isteminde çalıştırmanız önerilir. Örneğin, `devinit run -t choco-install -i {package} -s "{feed link}" -u {user} -p {password}` burada `{package}` , `{feed link}` , ve belirli bir paketinize, akış `{user}` bağlantınıza, kullanıcı `{password}` adınıza ve parolanıza bakın. Yukarıda başvurulan Chocolatey belgelerinde daha fazla bilgi bulabilirsiniz. 

### <a name="built-in-options"></a>Yerleşik seçenekler

Araç, `choco-install` başsız `choco` çalıştırılana kadar bir dizi komut satırı `choco` bağımsız değişkeni ayarlar. Bu bağımsız değişkenler aşağıda listelenmiştir ve bu bağımsız değişkenlerle ilgili belgeler [chocolatey belgelerinde bulunabilir.](https://chocolatey.org/docs/)

| Ad                  | Açıklama                                                                                        |
|-----------------------|----------------------------------------------------------------------------------------------------|
| **--yes**             | Tüm istemleri onaylayın - Sorularak değil, olumlu yanıtı seçer. Ima `--accept-license.` |
| **--no-progress**     | İlerlemeyi gösterme - İlerleme yüzdeleri gösterilmez.                                         |
| **--skip-powershell** | PowerShell'chocolateyInstall.ps1 atla - bu komutlar hiçbir zaman açık olmayacak.                                              |

### <a name="default-behavior"></a>Varsayılan davranış

Özelliğin gerekli olması `choco-install` nedeniyle aracın varsayılan davranışı `input` hatadır.

## <a name="example-usage"></a>Örnek kullanım
Aşağıda, kullanarak çalıştırma örnekleri `choco-install` `.devinit.json` verilmiştir.

#### <a name="devinitjson-that-will-install-packages-listed-in-packagesconfig"></a>.devinit.js, aşağıdakiler altında listelenen paketleri packages.config:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-install",
            "input": "packages.config",
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-mongodb"></a>.devinit.jsMongoDB'yi yükley on:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-install",
            "input": "mongodb"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-mongodb"></a>.devinit.jsMongoDB'nin belirli bir sürümünü yükecek olan bir dosya vardır:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-install",
            "input": "mongodb",
            "additionalOptions": "--version 4.2.7"
        }
    ]
}
```

#### <a name="devinitjson-that-adds-a-new-feed-to-chocolatey"></a>.devinit.jsChocolatey'ye yeni bir akış ekleyeceksiniz:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-install",
            "input": "packages.config",
            "additionalOptions": "-s '{feed link}'"
        }
    ]
}
```