---
title: devinit yapılandırma dosyası
description: Devınit için bildirim dosyası .devinit.jsbelgeleri.
ms.date: 11/02/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 84c9123ea117b1a215473be8e804b8122e2c49364e5f570a131b0c93333e952d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121378392"
---
# <a name="devinit-configuration-file"></a>devinit yapılandırma dosyası

> [!IMPORTANT]
> 12 nisan 2021 itibariyle, Visual Studio 2019 ' den GitHub codespaces 'a bağlanmak artık desteklenmeyecektir ve bu özel önizleme sona ermiştir. bulut destekli bir iç döngü ve çok sayıda Visual Studio iş yükü için iyileştirilmiş vdı çözümleri için gelişen deneyimler üzerinde odaklanıyoruz. gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi edinmek için Visual Studio geliştirici topluluğu forumumuza dahil etmeniz önerilir.

`.devinit.json`Dosya, uygulamanızın çalıştırmak ve derlemek için ihtiyaç duyacağı sistem genelinde bağımlılıkları tanımlar. sistem genelinde bağımlılıklar Node.js, SQL Server, ııs, kbbitmq, docker vb. gibi şeyler. Bunlar, normalde, belirli bir depoyla yüklenmeyen geliştirme kutusuna yüklediğiniz şeyleri sıralacağlardır. NuGet veya npm gibi paket yöneticilerinde yaptığınız gibi uygulamaya özel bağımlılıklar tanımlamak bir yer değildir. Ancak, bu paket yöneticilerine ihtiyacınız olduğunu tanımlamak için bir yer vardır.

## <a name="file-location"></a>Dosya konumu

`devinit init`Komut, dosya aracılığıyla yönlendiriliyor `.devinit.json` . Varsayılan olarak, `devinit` aşağıdaki konumlarda dosyayı arar:

* {geçerli-dizin} \\ Üzerinde.devinit.js
* {geçerli-dizin} \\ Üzerindedevinit.js
* {geçerli-dizin} \\ . devinit \\.devinit.json
* {geçerli-dizin} \\ . devinit \\devinit.json
* {geçerli-dizin} \\ devinit \\.devinit.json
* {geçerli-dizin} \\ devinit \\devinit.json
* {geçerli-dizin} \\ . devcontainer \\.devinit.json
* {geçerli-dizin} \\ . devcontainer \\devinit.json

> [!NOTE]
> Birden çok varsayılan dosya bulunursa, devınit yukarıdaki listede ilk görüntülenen dosyayı kullanır.

`.devinit.json`Dosya ayrıca seçeneği aracılığıyla açıkça de belirtilebilir `--file` / `-f` .

### <a name="directories-and-relative-paths"></a>Dizinler ve göreli yollar

Yollar, devınit 'in çalıştığı konuma göre belirlenir. Bu, genellikle yürütülen geçerli çalışma dizinidir `devinit` .

## <a name="file-format"></a>Dosya Biçimi
Bir içinde `.devinit.json` , çalıştırmak için birden fazla araç belirtebilirsiniz. `run`Bölümünde istediğiniz sayıda nesne yerleştirebilirsiniz. Bunun bir örneği, tüm araçlarımızla birlikte örnek [.devinit.js](sample-all-tool.md) görülür.

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "comments": "string",
    "run": [
        {
            "comments": "string",
            "tool": "string",
            "input": "string|null|undefined",
            "additionalOptions": "string|null|undefined"
        }
    ]
}
```

### <a name="property-values"></a>Özellik değerleri

| Ad         | Tür   | Gerekli | Değer                              |
|--------------|--------|----------|------------------------------------|
| **yorumlar** | dize | No       | Dosya için açıklamalar.             |
| **çalışmaz**      | array  | Yes      | [RunTool nesnesi](#run-tool-object) |

#### <a name="run-tool-object"></a>Araç nesnesi Çalıştır

| Ad                  | Tür   | Gerekli | Değer                                                                                                      |
|-----------------------|--------|----------|------------------------------------------------------------------------------------------------------------|
| **yorumlar**          | dize | No       | Araç girişi için açıklamalar.                                                                               |
| **Aracı**              | string | Yes      | Araç adı. `devinit list`Kullanılabilir araçların listesi için komutuna bakın.                            |
| **girişinin**             | dize | No       | Araç girişi. Araca göre farklılık gösterir. Örneğin, gerekli sürüm, paket KIMLIĞI, dosya adı veya klasör.|
| **additionalOptions** | dize | No       | Araca geçirilecek ek komut satırı bağımsız değişkenleri.                                                |

## <a name="examples"></a>Örnekler

Devinit kullanma hakkında daha fazla örnek için [örnekler bölümüne](sample-readme.md)bakın.
