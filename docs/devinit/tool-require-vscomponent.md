---
title: require-vscomponent
description: devinit tool require-vscomponent.
ms.date: 02/08/2021
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 5ba58bfde22ad5d6d9a7a3a2c64d95326a5e33c43adb327285ac6ba73da8390b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121418022"
---
# <a name="require-vscomponent"></a>require-vscomponent

> [!IMPORTANT]
> 12 Nisan 2021'den itibaren Visual Studio 2019'dan GitHub Codespaces'a bağlanma desteklemeyecek ve bu özel önizleme sonuçlandırıldı. Bulut destekli iç döngü için gelişen deneyimlere ve çok çeşitli iş yükleri için iyileştirilmiş VDI çözümlerine Visual Studio odaklanacağız. Bu ve ilişkili `devinit` araçların bir parçası olarak artık kullanılamaz. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi için Visual Studio geliştirici topluluğu forummize katılın.

Araç, `require-vscomponent` yapılandırma yapılandırmalarını mevcut Visual Studio içeri aktarmaya Visual Studio. Burada hakkında daha fazla bilgi `.vsconfig` [okuyun.](../install/import-export-installation-configurations.md)

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı [olarak açıklanmış varsayılan](#default-behavior) davranışı takip eder.

| Ad                                     | Tür   | Gerekli | Değer                                                                |
|------------------------------------------|--------|----------|----------------------------------------------------------------------|
| **yorumlar**                             | dize | No       | İsteğe bağlı açıklamalar özelliği. Kullanılmadı.                                |
| [**Giriş**](#input)                      | dize | No       | tam `.vsconfig` yolu. Ayrıntılar [için](#input) aşağıdaki girişe bakın. |
| [additionalOptions](#additional-options) | dize | No       | Ayrıntılar [için aşağıdaki](#additional-options) Ek seçenekler'e bakın.     |

### <a name="input"></a>Giriş

`input`özelliği, dosyanın tam yolunu belirtmek için `.vsconfig` kullanılır. Bahsediliyorsa, araç geçerli dizinde bir araması ve değeri `.vsconfig` dizine Visual Studio Yükleyicisi.

### <a name="additional-options"></a>Ek seçenekler

Ek yapılandırma seçenekleri değeri olarak `additionalOptions` geçirebilirsiniz. 

| Ad                      | Tür      | Gerekli | Değer                                                                                                                                                                                    |
|---------------------------|-----------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| --installPath             | dize    | No       | Değiştirmek istediğiniz Visual Studio yükleme yolu.                                                                                                                       |

Herhangi bir yükleme yolu belirtilmezse, makineniz üzerinde birden çok örnek Visual Studio aracı makinenize en erken yüklenmiş yükleme aracını değiştirir. 

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan davranışı, geçerli dizinde bir dosyayı arama ve bu ayrıntılarla Visual Studio Yükleyicisi sessiz modda `require-vscomponent` `.vsconfig` çalıştırmadır. `require-vscomponent`yalnızca mevcut bir Visual Studio destekler. 

## <a name="example-usage"></a>Örnek kullanım
Aşağıda, kullanarak çalıştırmaya bir `require-vscomponent` örnek `.devinit.json` verilmiştir.

#### <a name="devinitjson-that-will-import-the-configurations-of-a-given-vsconfig-file-path"></a>.devinit.jsbir .vsconfig dosya yolunun yapılandırmalarını içeri aktaracak olan bir dosya adı:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "comments": "A sample dot-devinit file.",
    "run": [
        {
            "tool": "require-vscomponent",
            "input": "C:\\.vsconfig"
        }
    ]
}
```

#### <a name="devinitjson-that-will-import-the-configurations-of-a-given-vsconfig-file-path-to-the-visual-studio-instance-specified-via-an-install-path"></a>.devinit.js, belirli bir .vsconfig dosya yolunun yapılandırmalarını yükleme yoluyla belirtilen Visual Studio örneğine aktaracak:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "comments": "A sample dot-devinit file.",
    "run": [
        {
            "tool": "require-vscomponent",
            "input": "C:\\.vsconfig",
            "additionalOptions": "--installPath 'C:\\Program Files (x86)\\Microsoft Visual Studio\\2019\\Enterprise'"
        }
    ]
}
```