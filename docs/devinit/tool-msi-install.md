---
title: msi-install
description: msiexec için devinit aracı.
ms.date: 10/13/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: ab56157d531e762ed36f8c2349e50e76596b05ec
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672175"
---
# <a name="msi-install"></a>msi-install

`msi-install`Araç, `.msi` [msiexec](https://docs.microsoft.com/windows-server/administration/windows-commands/msiexec)kullanarak paket dosya biçimlerini yüklemek için kullanılır.

## <a name="usage"></a>Kullanım

`input`Atlanırsa veya boşsa araç bir hata çıktısı olur.

| Ad                                         | Tür   | Gerekli | Değer                                                                             |
|----------------------------------------------|--------|----------|-----------------------------------------------------------------------------------|
| **açıklamaları**                                 | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                             |
| [**girişinin**](#input)                          | string | Yes      | Öğesini `msi` yüklemek için. Ayrıntılar için aşağıdaki [girişi](#input) inceleyin.                      |
| [**additionalOptions**](#additional-options) | dize | No       | Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.                  |

### <a name="input"></a>Girdi

Input özelliği, yüklenecek bir dosyanın yolunu veya URL 'sini belirtmek için kullanılır `.msi` . Yolu `.msi` yanlışsa veya URL doğrudan işaret vermezse `.msi` , `msi-install` yükleme paketinin açılmadığını unutmayın.

### <a name="additional-options"></a>Ek seçenekler

Ek yapılandırma seçenekleri additionalOptions değeri olarak geçirilebilir. Bu bağımsız değişkenler tarafından kullanılan bağımsız değişkenlere doğrudan geçiş yapılır `msiexec` ve `msiexec` [belgelerde](https://docs.microsoft.com/windows-server/administration/windows-commands/msiexec)tanımlanmıştır.

### <a name="built-in-options"></a>Yerleşik Seçenekler

MSI-install Aracı, `msiexec` MSI 'nin gözetimsiz olarak çalışmasını sağlamak için bir dizi komut satırı bağımsız değişkeni ayarlar. Bu bağımsız değişkenler aşağıda listelenmiştir ve belgelerde yer alan belgeler bulunabilir `msiexec` [documentation](https://docs.microsoft.com/windows-server/administration/windows-commands/msiexec).

| Ad          | Açıklama                                                                                                                                                                                   |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /i            | Normal bir yükleme çalıştırır                                                                                                                                                                    | 
| istemci bilgisayarlara        | Kullanıcı etkileşimi gerekmeden sessiz modu belirtir                                                                                                                                        | 
| /QN           | Yükleme işlemi sırasında kullanıcı arabirimi olmadığını belirtir                                                                                                                                           | 
| /passive      | Yüklemenin yalnızca bir ilerleme çubuğu gösterdiği katılımsız modu belirtir                                                                                                                    | 
| /l * V          | Günlüğe kaydetmeyi etkinleştirir ve ayrıntılı bilgiler de dahil olmak üzere tüm bilgileri `devinit.log` makinenin yerel Temp klasöründeki bir dosyaya kaydeder. Araç başarısız olursa, günlük dosyası yolu görüntülenir.      | 
| /norestart    | Yükleme tamamlandıktan sonra makinenin yeniden başlatılmasını engeller, ancak yeniden başlatma gerekirse 3010 çıkış kodu döndürür                                                                  | 

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
