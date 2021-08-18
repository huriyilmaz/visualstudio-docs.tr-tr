---
title: wsl-install
description: devinit tool wsl-install.
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
ms.openlocfilehash: 448df85f9a67189d22a8d371c1d5ec30b960928a9242c05f44e07ba5eb198bc2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121418031"
---
# <a name="wsl-install"></a>wsl-install

> [!IMPORTANT]
> 12 Nisan 2021'den itibaren Visual Studio 2019'dan GitHub Codespaces'a bağlanma desteklemeyecek ve bu özel önizleme sonuçlandırıldı. Bulut destekli iç döngü için gelişen deneyimlere ve çok çeşitli iş yükleri için iyileştirilmiş VDI çözümlerine Visual Studio odaklanacağız. Bu ve ilişkili `devinit` araçların bir parçası olarak artık kullanılamaz. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi için Visual Studio geliştirici topluluğu forummize katılın.

Araç, `wsl-install` Linux için Windows Alt Sistemi (WSL) için Linux [dağıtımlarını](/windows/wsl/) yüklemek için kullanılır.

> [!IMPORTANT]
> Araç, `wsl-install` wsl 2'nin Windows. Herhangi bir nedenle WSL 2 etkinleştirilmediyse, [WSL](https://docs.microsoft.com/windows/wsl/install-win10)yükleme belgelerini takip edin. [Windowsfeature-enable aracını,](tool-windowsfeature-enable.md) gerekli tüm özellikleri etkinleştirmek için windowsfeature-enable Windows kullanabilirsiniz.

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak [açıklanmış varsayılan](#default-behavior) davranışı takip eder.

| Ad                                             | Tür   | Gerekli | Değer                                                             |
|--------------------------------------------------|--------|----------|-------------------------------------------------------------------|
| **yorumlar**                                     | dize | No       | İsteğe bağlı açıklamalar özelliği. Kullanılmadı.                             |
| [**Giriş**](#input)                              | string | Yes      | Yüklenecek dağıtım. Ayrıntılar [için](#input) aşağıdaki Giriş'e bakın.     |
| [**additionalOptions**](#additional-options)     | dize | No       | Ayrıntılar [için aşağıdaki](#additional-options) Ek seçenekler'e bakın.  |

### <a name="input"></a>Giriş

Dağıtacak dağıtımı içeren AppX uygulama dağıtım paketi ( `.appx` ) için URI. URI, arşiv kökünde veya bir iç arşiv içinde tek bir içeren `.appx` `install.tar.gz` arşive işaret `.appx` etmek gerekir. Desteklenen dağıtım örnekleri şunlardır:

| Dağıtım                          | Urı                                                           |
|---------------------------------|---------------------------------------------------------------|
| Ubuntu 20.04                    | https://aka.ms/wslubuntu2004                                  |
| Ubuntu 18.04                    | https://aka.ms/wsl-ubuntu-1804                                |
| Ubuntu 16.04                    | https://aka.ms/wsl-ubuntu-1604                                |
| Debian GNU/Linux                | https://aka.ms/wsl-debian-gnulinux                            |
| Kali Linux                      | https://aka.ms/wsl-kali-linux-new                             |
| OpenSUSE Leap 42                | https://aka.ms/wsl-opensuse-42                                |
| SUSE Linux Enterprise Server 12 | https://aka.ms/wsl-sles-12                                    |

> [!NOTE]
> ARM Linux dağıtımları şu anda Codespaces'GitHub desteklemektedir.

### <a name="additional-options"></a>Ek seçenekler

Birden çok ek seçenek de kullanılabilir:

| Ad                      | Tür      | Gerekli | Değer                                                                                                                                                                                    |
|---------------------------|-----------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| --wsl-version             | dize    | No       | Kullanmak için WSL sürümü. Varsayılan değer 2'dir.                                                                                                                                  |
| --post-create-command     | dize    | No       | Yükleme tamamlandıktan sonra Linux dağıtımı içinde yürütülecek komut. Komutun tek bir sözcük olarak biçimlendirilerek veya tırnak içine alınarak sarmalanmış olması gerekir. Varsayılan değer komut değildir.  |

### <a name="default-behavior"></a>Varsayılan davranış

Aracının varsayılan davranışı, yüklemenin dağıtım özelliği `wsl-install` `input` gerektiğinden hataya neden olmasıdır.

## <a name="example-usage"></a>Örnek kullanım
Aşağıda, kullanarak çalıştırma örnekleri `wsl-install` `.devinit.json` verilmiştir.

#### <a name="devinitjson-that-will-install-ubuntu-2004"></a>.devinit.jsUbuntu 20.04'ü yükleyecek:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-ubuntu-2004-and-perform-a-post-create-command"></a>.devinit.jsUbuntu 20.04'ü yükecek ve oluşturma sonrası komutu gerçekleştirecek:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'echo Hello from Ubuntu!'"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-ubuntu-2004-and-perform-a-post-create-command-that-configures-the-packages-listed"></a>.devinit.jsUbuntu 20.04'ü yükecek ve listelenen paketleri yapılandıran bir post create komutu gerçekleştirecek:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'apt-get update && apt-get install g++ gcc g++-9 gcc-9 cmake gdb ninja-build zip rsync -y'"
        }
    ]
}
```
