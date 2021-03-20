---
title: msi-install
description: msiexec için devinit aracı.
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
ms.openlocfilehash: d2da7f26501cfa686cd0703f7dbbbef4053f761b
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104671646"
---
# <a name="msi-install"></a>msi-install

> [!IMPORTANT]
> 12 Nisan 2021 itibariyle, Visual Studio 2019 ' den GitHub Codespaces 'a bağlanmak artık desteklenmeyecektir ve bu özel önizleme sona ermiştir. Bulut destekli bir iç döngü ve çok sayıda Visual Studio iş yükü için iyileştirilmiş VDı çözümleri için gelişen deneyimlere odaklanıyoruz. Bu `devinit` ve ilişkili araçların bir parçası olarak artık kullanılabilir olmayacaktır. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi için, Visual Studio için geliştirici topluluğu forumumuza dahil etmeniz önerilir.

`msi-install`Araç, `.msi` [msiexec](https://docs.microsoft.com/windows-server/administration/windows-commands/msiexec)kullanarak paket dosya biçimlerini yüklemek için kullanılır.

## <a name="usage"></a>Kullanım

`input`Atlanırsa veya boşsa araç bir hata çıktısı olur.

| Ad                                         | Tür   | Gerekli | Değer                                                                             |
|----------------------------------------------|--------|----------|-----------------------------------------------------------------------------------|
| **açıklamaları**                                 | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                             |
| [**girişinin**](#input)                          | string | Yes      | Öğesini `msi` yüklemek için. Ayrıntılar için aşağıdaki [girişi](#input) inceleyin.                      |
| [**additionalOptions**](#additional-options) | dize | No       | Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.                  |

### <a name="input"></a>Giriş

Input özelliği, yüklenecek bir dosyanın yolunu veya URL 'sini belirtmek için kullanılır `.msi` . Yolu `.msi` yanlışsa veya URL doğrudan işaret vermezse `.msi` , `msi-install` yükleme paketinin açılmadığını unutmayın.

### <a name="additional-options"></a>Ek seçenekler

Ek yapılandırma seçenekleri additionalOptions değeri olarak geçirilebilir. Bu bağımsız değişkenler tarafından kullanılan bağımsız değişkenlere doğrudan geçiş yapılır `msiexec` ve `msiexec` [belgelerde](https://docs.microsoft.com/windows-server/administration/windows-commands/msiexec)tanımlanmıştır.

### <a name="built-in-options"></a>Yerleşik Seçenekler

MSI-install Aracı, `msiexec` MSI 'nin gözetimsiz olarak çalışmasını sağlamak için bir dizi komut satırı bağımsız değişkeni ayarlar. Bu bağımsız değişkenler aşağıda listelenmiştir ve belgelerde yer alan belgeler bulunabilir `msiexec` [](https://docs.microsoft.com/windows-server/administration/windows-commands/msiexec).

| Ad          | Açıklama                                                                                                                                                                                   |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /i            | Normal bir yükleme çalıştırır                                                                                                                                                                    |
| istemci bilgisayarlara        | Kullanıcı etkileşimi gerekmeden sessiz modu belirtir                                                                                                                                        |
| /QN           | Yükleme işlemi sırasında kullanıcı arabirimi olmadığını belirtir                                                                                                                                           |
| /passive      | Yüklemenin yalnızca bir ilerleme çubuğu gösterdiği katılımsız modu belirtir                                                                                                                    |
| /l * V          | Günlüğe kaydetmeyi etkinleştirir ve ayrıntılı bilgiler de dahil olmak üzere tüm bilgileri `devinit.log` makinenin yerel Temp klasöründeki bir dosyaya kaydeder. Araç başarısız olursa, günlük dosyası yolu görüntülenir.      |
| /norestart    | Yükleme tamamlandıktan sonra makinenin yeniden başlatılmasını engeller, ancak yeniden başlatma gerekirse 3010 çıkış kodu döndürür                                                                  |

### <a name="default-behavior"></a>Varsayılan davranış

`msi-install`Özelliğin gerekli olduğu şekilde aracın varsayılan davranışı hata olur `input` .

## <a name="example-usage"></a>Örnek kullanım
Kullanarak nasıl çalıştırılacağını gösteren bir örnek aşağıda verilmiştir `msi-install` `.devinit.json` .

#### <a name="devinitjson-that-will-install-the-7-zip-msi"></a>.devinit.js, 7-ZIP MSI ' yi yükleyecek:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-4.0",
    "run": [
        {
            "tool": "msi-install",
            "input": "https://www.7-zip.org/a/7z1900.msi"
        }
    ]
}
```
