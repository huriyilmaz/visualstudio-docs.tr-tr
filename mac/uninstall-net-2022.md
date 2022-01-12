---
title: Mac için Visual Studio Apple Silikon makinelerde 17.0 ve .NET
description: M1 makinelerde 2022'de çalışan desteklenen .NET sürümlerini alma adımları.
author: jmatthiesen
ms.author: jomatthi
manager: dominicn
ms.date: 11/08/2021
ms.topic: how-to
ms.assetid: 18f722bc-3d9d-4c75-9e77-d66b64784c8d
ms.openlocfilehash: 941169c00a16d9228cde128c59967c35fb1fdceb
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135804603"
---
# <a name="visual-studio-for-mac-170-previews-and-net-on-apple-silicon-machines"></a>Mac için Visual Studio Apple Silikon makinelerde 17.0 Önizlemeleri ve .NET

Eski x64 SDK'ların yüklü olduğu Apple Silikon makinelerde (M1 veya ARM olarak da bilinir), .NET 6 GA Arm64 SDK'sı kullanmak için tüm mevcut .NET yüklemelerini kaldırmanız gerekir.  

> [!NOTE]
> Bu bilgiler, Mac için Visual Studio 2022 Preview (17.0) sürümlerine özeldir. Mac için Visual Studio 2019 sürümleri için bu işlem hakkında daha fazla bilgi için bkz. Apple Silikon Mac için Visual Studio [8.10 ve .NET.](/visualstudio/mac/uninstall-net-2019)

## <a name="uninstall-net-from-your-machine"></a>Makineden .NET'i kaldırın: 

1. .NET [depolama deposundan](https://github.com/dotnet/sdk/blob/main/scripts/obtain/uninstall/dotnet-uninstall-pkgs.sh) kaldırma GitHub sağ tıklar ve Farklı Kaydet'i seçerek dosyayı Mac'inize kaydedin. 
2. Terminal'i açın ve çalışma dizinini betiğin indirilmiş olduğu dizin olarak değiştirme:
 
    ```bash
    cd /location/of/file
    ```
3. Betiği yürütülebilir hale çalıştırın ve **sudo ile çalıştırın:**

    ```bash
    chmod +x dotnet-uninstall-pkgs.sh 
    sudo ./dotnet-uninstall-pkgs.sh
    sudo rm -r /etc/dotnet
    ```  

## <a name="install-supported-net-sdks"></a>Desteklenen .NET SDK'larını yükleme

1. [.NET 6 Arm64 SDK'sı yükleme](https://download.visualstudio.microsoft.com/download/pr/ed60d37e-7842-4fc2-8250-2bd66073d79e/725d486e04d27e45d2b41c687dc35f49/dotnet-sdk-6.0.100-osx-arm64.pkg)
2. Yüklü Mac için Visual Studio SDK'yı algılaması için yeniden başlatın. 
