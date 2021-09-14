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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725363"
---
# <a name="msi-install"></a>msi-install

> [!IMPORTANT]
> 12 Nisan 2021'den itibaren, Visual Studio 2019'dan GitHub Codespaces'a bağlanmak artık desteklemeyecek ve bu özel önizlemenin sonucuna varıldı. Bulut destekli iç döngü için gelişen deneyimlere ve çok çeşitli iş yükleri için iyileştirilmiş VDI çözümlerine Visual Studio odaklanacağız. Bu ve ilişkili `devinit` araçların bir parçası olarak artık kullanılamaz. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi almak Visual Studio geliştirici topluluğu forummize dahil olmak için sizi teşvik ediyoruz.

Araç, `msi-install` `.msi` msiexec kullanarak paket dosyası [biçimlerini yüklemek için kullanılır.](https://docs.microsoft.com/windows-server/administration/windows-commands/msiexec)

## <a name="usage"></a>Kullanım

atlanırsa `input` veya boşsa, araç bir hata verir.

| Ad                                         | Tür   | Gerekli | Değer                                                                             |
|----------------------------------------------|--------|----------|-----------------------------------------------------------------------------------|
| **yorumlar**                                 | dize | No       | İsteğe bağlı açıklamalar özelliği. Kullanılmadı.                                             |
| [**Giriş**](#input)                          | string | Yes      | Yüklenmek `msi` için . Ayrıntılar [için](#input) aşağıdaki Giriş'e bakın.                      |
| [**additionalOptions**](#additional-options) | dize | No       | Ayrıntılar [için aşağıdaki](#additional-options) Ek seçeneklere bakın.                  |

### <a name="input"></a>Giriş

Giriş özelliği, yüklenecek bir dosyanın yolunu veya `.msi` URL'sini belirtmek için kullanılır. yolu `.msi` yanlışsa veya URL doğrudan bir adresine işaret `.msi` etmese, `msi-install` yükleme paketinin açılamayacak olduğunu unutmayın.

### <a name="additional-options"></a>Ek seçenekler

Ek yapılandırma seçenekleri additionalOptions değeri olarak geçirebilirsiniz. Bu bağımsız değişkenler, tarafından kullanılan bağımsız değişkenlere doğrudan geçiştir `msiexec` ve belgelerinde `msiexec` [tanımlanmıştır.](https://docs.microsoft.com/windows-server/administration/windows-commands/msiexec)

### <a name="built-in-options"></a>Yerleşik seçenekler

msi-install aracı, msi'nin başsız çalışması için bir `msiexec` dizi komut satırı bağımsız değişkeni ayarlar. Bu bağımsız değişkenler aşağıda listelenmiştir ve bu bağımsız değişkenlerle ilgili belgeler belgelerinde `msiexec` [bulunabilir.](https://docs.microsoft.com/windows-server/administration/windows-commands/msiexec)

| Ad          | Açıklama                                                                                                                                                                                   |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /i            | Normal bir yükleme çalıştırır                                                                                                                                                                    |
| istemci bilgisayarlara        | Kullanıcı etkileşimi gerek olmadan sessiz modu belirtir                                                                                                                                        |
| /qn           | Yükleme işlemi sırasında kullanıcı arabirimi olmadığını belirtir                                                                                                                                           |
| /passive      | Yüklemenin yalnızca ilerleme çubuğunun olduğu katılımsız modu belirtir                                                                                                                    |
| /l*V          | Günlüğe kaydetmeyi ve ayrıntılı bilgiler de dahil olmak üzere tüm bilgileri makinenin yerel geçici klasöründeki `devinit.log` bir dosyaya kaydeder. Araç başarısız olursa günlük dosyası yolu görüntülenir.      |
| /norestart    | Yükleme tamamlandıktan sonra makinenin yeniden başlatılmasını durdurur, ancak yeniden başlatma gerekirse 3010 çıkış kodu geri döner                                                                  |

### <a name="default-behavior"></a>Varsayılan davranış

Özelliğin gerekli olması `msi-install` nedeniyle aracın varsayılan davranışı `input` hatadır.

## <a name="example-usage"></a>Örnek kullanım
Aşağıda, kullanarak çalıştırmaya bir `msi-install` örnek `.devinit.json` verilmiştir.

#### <a name="devinitjson-that-will-install-the-7-zip-msi"></a>7-Zip MSI'yi yükecek .devinit.json:
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
