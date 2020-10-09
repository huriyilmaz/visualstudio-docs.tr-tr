---
title: wsl-install
description: devinit aracı WSL-Install.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 950ca7f1e9c43123b206893dbc6a07da7c3743ec
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862861"
---
# <a name="wsl-install"></a>wsl-install

`wsl-install`Araç, [Linux için Windows alt sistemi](/windows/wsl/) (WSL) için Linux Distro 'lara yüklemek üzere kullanılır.

`wsl-install`Araç, Windows üzerinde WSL 2 ' nin zaten etkinleştirilmesini gerektirir. Bazı nedenlerle WSL2 etkinleştirilmemişse, [WindowsFeature-Enable](tool-windowsfeature-enable.md) aracını ve özellik adını kullanarak WSL2 'yi etkinleştirebilirsiniz `Microsoft-Windows-Subsystem-Linux` .

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak açıklanan [varsayılan](#default-behavior) davranışı izler.

| Ad                                             | Tür   | Gerekli | Değer                                                             |
|--------------------------------------------------|--------|----------|-------------------------------------------------------------------|
| **açıklamaları**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                             |
| [**girişinin**](#input)                              | string | Evet      | Yüklemeyi geri çevirme. Ayrıntılar için aşağıdaki [girişi](#input) inceleyin.     |
| [**additionalOptions**](#additional-options)     | dize | No       | Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.  |

### <a name="input"></a>Giriş

Dağıtımı yapılan kapsayıcıyı içeren AppX uygulama dağıtım paketi ( `.appx` ) IÇIN URI. URI, arşiv kökünde ya da `.appx` `install.tar.gz` bir iç arşiv içinde tek bir içeren bir arşivi işaret etmelidir `.appx` . Desteklenen destekler arasında şunlar yer alır:

| Distro                          | Kullanılmamışsa                                                           |
|---------------------------------|---------------------------------------------------------------|
| Ubuntu 20.04                    | https://aka.ms/wslubuntu2004                                  |
| Ubuntu 18.04                    | https://aka.ms/wsl-ubuntu-1804                                |
| Ubuntu 16.04                    | https://aka.ms/wsl-ubuntu-1604                                |
| Borçlu GNU/Linux                | https://aka.ms/wsl-debian-gnulinux                            |
| Kali Linux                      | https://aka.ms/wsl-kali-linux-new                             |
| OpenSUSE artık 42                | https://aka.ms/wsl-opensuse-42                                |
| SUSE Linux Enterprise Server 12 | https://aka.ms/wsl-sles-12                                    |

> [!NOTE]
> ARM Linux Distro 'lara, GitHub codespaces 'de Şu anda desteklenmiyor.

### <a name="additional-options"></a>Ek seçenekler

Birden çok ek seçenek desteklenir:

| Ad                      | Tür      | Gerekli | Değer                                                                                                                                                                                    |
|---------------------------|-----------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| --WSL-sürümü             | dize    | No       | Kullanılacak WSL sürümü. Varsayılan değer 2 ' dir.                                                                                                                                  |
| --oluşturma sonrası-komutu     | dize    | No       | Yükleme tamamlandıktan sonra Linux 'un içinde yürütülecek komut. Komut tek bir sözcük olarak biçimlendirilmelidir veya tırnak işaretleri içine alınmalıdır. Varsayılan, komut değildir.  |

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan davranışı `wsl-install` `input` , ' nin yükleneceğine ilişkin özelliği olarak hata olur.

## <a name="example-usage"></a>Örnek kullanım

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will install Ubuntu 20.04.",
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004"
        },
        {
            "comments": "Example that will install Ubuntu 20.04 using WSL2, and echo 'Hello from Ubuntu!' after installing.",
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'echo Hello from Ubuntu!'"
        },
        {
            "comments": "Example that will install Ubuntu 20.04 using WSL2, and configure it with various packages.",
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'apt-get update && apt-get install g++ gcc g++-9 gcc-9 cmake gdb ninja-build zip rsync -y'"
        }
    ]
}
```