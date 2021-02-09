---
title: choco-install
description: Chocolatey paketlerini yüklemek için devinit aracı Choco-Install.
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
ms.openlocfilehash: 386b41dd7f1b19d223703570b0423de0855e983a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904799"
---
# <a name="choco-install"></a>choco-install

`choco-install`Araç, [Chocolatey](https://chocolatey.org/) paketlerini yüklemek ve güncelleştirmek için kullanılabilir.

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa araç hiçbir şey yapmaz.

| Ad                                             | Tür   | Gerekli  | Değer                                                                                                          |
|--------------------------------------------------|--------|-----------|----------------------------------------------------------------------------------------------------------------|
| **açıklamaları**                                     | dize | No        | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                                                          |
| [**girişinin**](#input)                              | string | Yes       | Yüklenecek paket. Ayrıntılar için aşağıdaki [girişi](#input) inceleyin.                                                 |
| [**additionalOptions**](#additional-options)     | dize | No        | Araca geçirilecek ek seçenekler. Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.       |

### <a name="input"></a>Giriş

`input`Özelliği, Yüklenecek paketin adını (örneğin ' MongoDB ') veya aşağıdaki biçimlerdeki bir yapılandırma dosyasının yolunu belirtmek için kullanılır _packages.config_, _. nuspec_ ve _. nupkg_. Değeri, `input` öğesine `choco install` `choco install mongodb` özgü bağımsız değişkenlerle birlikte (örneğin,) [`additionalOptions`](#additional-options) ve yerleşik `choco` seçeneklere ( [aşağıda](#built-in-options)tanımlanmıştır) eklenir. Paketler [Chocolatey paket galerisinde](https://chocolatey.org/packages)bulunur. Bir yapılandırma dosyası kullanırken, bu dosyanın yolunu, `input` Örneğin, özelliğinde geçirebilirsiniz `"input":"packages.config"` .

### <a name="additional-options"></a>Ek seçenekler

Ek yapılandırma seçenekleri ' ın bir değeri olarak geçirilebilir `additionalOptions` . Bu bağımsız değişkenler tarafından kullanılan bağımsız değişkenlere doğrudan geçiş yapılır [`choco install`](https://chocolatey.org/docs/commands-install) ve Chocolatey belgelerinde tanımlanmıştır.

#### <a name="adding-new-feeds-to-chocolatey"></a>Chocolatey 'e yeni akışlar ekleme
Bir komuta benzer şekilde Chocolatey 'e yeni bir akış eklemek istiyorsanız `choco source add` , `additionalOptions` bunu yapmak için uygulamasına geçiş yapabilirsiniz. Yeni bir akış ekleme örneği [örnek kullanımdır](#example-usage). Özel bir akış eklemek istiyorsanız, bu aracı komut isteminde, kimlik bilgileri gerektirdiğinden çalıştırmayı öneririz. Örneğin,,,,,,,, `devinit run -t choco-install -i {package} -s "{feed link}" -u {user} -p {password}` `{package}` `{feed link}` `{user}` ve `{password}` özel paketinizi, akış bağlantısını, Kullanıcı adınızı ve parolanızı ifade eder. Daha fazla bilgi, yukarıda başvurulan Chocolatey belgelerinde bulunur. 

### <a name="built-in-options"></a>Yerleşik Seçenekler

`choco-install`Araç, gözetimsiz bir şekilde `choco` çalışmasını sağlamak için bir dizi komut satırı bağımsız değişkeni ayarlar `choco` . Bu bağımsız değişkenler aşağıda listelenmiştir ve bunlarla ilgili belgeler [Chocolatey belgelerinde](https://chocolatey.org/docs/)bulunabilir.

| Ad                  | Açıklama                                                                                        |
|-----------------------|----------------------------------------------------------------------------------------------------|
| **--Evet**             | Tüm istemleri Onayla-istem yerine onaylama yanıtını seçer. Gibi `--accept-license.` |
| **--devam ediyor**     | İlerleme durumunu gösterme-Ilerleme yüzdeleri gösterilmez.                                         |
| **--Skip-PowerShell** | PowerShell 'i atla-chocolateyInstall.ps1 çalıştırılmayacaktır.                                              |

### <a name="default-behavior"></a>Varsayılan davranış

`choco-install`Özelliğin gerekli olduğu şekilde aracın varsayılan davranışı hata olur `input` .

## <a name="example-usage"></a>Örnek kullanım
Kullanarak nasıl çalıştırılacağını gösteren örnekler aşağıda verilmiştir `choco-install` `.devinit.json` .

#### <a name="devinitjson-that-will-install-packages-listed-in-packagesconfig"></a>.devinit.js, packages.config listelenen paketleri yükleyecek:
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

#### <a name="devinitjson-that-will-install-mongodb"></a>MongoDB yükleyecek .devinit.js:
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

#### <a name="devinitjson-that-will-install-a-specific-version-of-mongodb"></a>.devinit.js, MongoDB 'nin belirli bir sürümünü yükleyecek:
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

#### <a name="devinitjson-that-adds-a-new-feed-to-chocolatey"></a>Chocolatey 'e yeni bir akış ekleyen .devinit.js:
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