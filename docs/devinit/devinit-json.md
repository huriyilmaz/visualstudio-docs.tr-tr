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
ms.openlocfilehash: 47859d00861c2361ed03931bf1417e22425d6e68
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908120"
---
# <a name="devinit-configuration-file"></a>devinit yapılandırma dosyası

`.devinit.json`Dosya, uygulamanızın çalıştırmak ve derlemek için ihtiyaç duyacağı sistem genelinde bağımlılıkları tanımlar. Sistem genelinde bağımlılıklar Node.js, SQL Server, IIS, Kbbitmq, Docker vb. gibi şeyler. Bunlar, normalde, belirli bir depoyla yüklenmeyen geliştirme kutusuna yüklediğiniz şeyleri sıralacağlardır. NuGet veya NPM gibi paket yöneticilerinde yaptığınız gibi uygulamaya özel bağımlılıklar tanımlamak bir yer değildir. Ancak, bu paket yöneticilerine ihtiyacınız olduğunu tanımlamak için bir yer vardır.

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
| **açıklamaları** | dize | No       | Dosya için açıklamalar.             |
| **çalışmaz**      | array  | Yes      | [RunTool nesnesi](#run-tool-object) |

#### <a name="run-tool-object"></a>Araç nesnesi Çalıştır

| Ad                  | Tür   | Gerekli | Değer                                                                                                      |
|-----------------------|--------|----------|------------------------------------------------------------------------------------------------------------|
| **açıklamaları**          | dize | No       | Araç girişi için açıklamalar.                                                                               |
| **Aracı**              | string | Yes      | Araç adı. `devinit list`Kullanılabilir araçların listesi için komutuna bakın.                            |
| **girişinin**             | dize | No       | Araç girişi. Araca göre farklılık gösterir. Örneğin, gerekli sürüm, paket KIMLIĞI, dosya adı veya klasör.|
| **additionalOptions** | dize | No       | Araca geçirilecek ek komut satırı bağımsız değişkenleri.                                                |

## <a name="examples"></a>Örnekler

Devinit kullanma hakkında daha fazla örnek için [örnekler bölümüne](sample-readme.md)bakın.
