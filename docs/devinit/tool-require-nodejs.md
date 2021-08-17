---
title: require-nodejs
description: devinit tool require-nodejs.
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
ms.openlocfilehash: 9aecdbfc113f21c719a210b86e6df64f7da725c274f7741414561a6ebbdb530f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121343228"
---
# <a name="require-nodejs"></a>require-nodejs

> [!IMPORTANT]
> 12 Nisan 2021'den itibaren Visual Studio 2019'dan GitHub Codespaces'a bağlanma desteklemeyecek ve bu özel önizleme sonuçlandırıldı. Bulut destekli iç döngü için gelişen deneyimlere ve çok çeşitli iş yükleri için iyileştirilmiş VDI çözümlerine Visual Studio odaklanacağız. Bu ve ilişkili `devinit` araçların bir parçası olarak artık kullanılamaz. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi için Visual Studio geliştirici topluluğu forummize katılın.

Araç,Node.jskuruluş `require-nodejs` [ tarafından dağıtılan ](https://nodejs.org/) bir MSI aracılığıyla Node.js kullanılır.

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı [olarak açıklanmış varsayılan](#default-behavior) davranışı takip eder.

| Ad                                             | Tür   | Gerekli | Değer                                                                     |
|--------------------------------------------------|--------|----------|---------------------------------------------------------------------------|
| **yorumlar**                                     | dize | No       | İsteğe bağlı açıklamalar özelliği. Kullanılmadı.                                     |
| [**Giriş**](#input)                              | dize | No       | Yüklenmek Node.JS sürümü. Ayrıntılar [için](#input) aşağıdaki Giriş'e bakın. |
| [**additionalOptions**](#additional-options)     | dize | No       | Ayrıntılar [için aşağıdaki](#additional-options) Ek seçenekler'e bakın.          |

### <a name="input"></a>Giriş

özelliği, `input` Node.js kullanılır. Sürümlerin listesi, indirme sayfasında [Node.js bulunabilir.](https://nodejs.org/en/download/) Herhangi biri atlanırsa yükleme başarısız olur. Tam sürüm numarası Major.Minor.Path (örneğin 14.4.0) gereklidir.

### <a name="additional-options"></a>Ek seçenekler

Ek yapılandırma seçenekleri değeri olarak `additionalOptions` geçirebilirsiniz. Bu bağımsız değişkenler, MSI yükleyicisi için doğrudan geçiştir ve Node.js.  

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan davranışı, düğümün en son LTS sürümünü web sitesinde `require-nodejs` ayrıntılı olarak Node.JS [yüklemektir.](https://nodejs.org/en/download/)

## <a name="example-usage"></a>Örnek kullanım
Aşağıda, kullanarak çalıştırma örnekleri `require-nodejs` `.devinit.json` verilmiştir. 

#### <a name="devinitjson-that-will-install-the-lts-of-nodejs"></a>.devinit.jsltS'lerini yükecek Node.js:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-nodejs"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-nodejs"></a>.devinit.jsbelirli bir sürümü yükecek olan Node.js:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-nodejs",
            "input": "14.4.0"
        }
    ]
}
```
