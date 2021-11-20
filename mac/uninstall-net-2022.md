---
title: Apple Silicon machines üzerinde 17,0 ve .net Mac için Visual Studio
description: M1 makinelerinde 2022 ' de çalışan .NET sürümünün desteklenen sürümlerini alma adımları.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/08/2021
ms.assetid: 18f722bc-3d9d-4c75-9e77-d66b64784c8d
ms.openlocfilehash: 048fc31412159cea02333086253ef0d8c22cd8be
ms.sourcegitcommit: 8b44ba7864f67afa476708d5092729345e689f93
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2021
ms.locfileid: "132861685"
---
# <a name="visual-studio-for-mac-170-previews-and-net-on-apple-silicon-machines"></a>Apple Silicon machines üzerinde 17,0 önizleme ve .net Mac için Visual Studio

Eski x64 SDK 'Ları yüklü olan Apple Silicon Machines (M1 veya ARM olarak da bilinir), .NET 6 GA Arm64 SDK 'sını kullanabilmeniz için mevcut tüm .NET yüklemelerini kaldırmanız gerekir.  

> [!NOTE]
> bu bilgiler Mac için Visual Studio 2022 Preview (17,0) sürümleri için özeldir. Mac için Visual Studio 2019 sürümleri için bu işlem hakkında daha fazla bilgi için bkz. [Apple Silicon machines hakkında ayrıntılar için Mac için Visual Studio 8,10 ve .net](/visualstudio/mac/uninstall-net-2019) .

## <a name="uninstall-net-from-your-machine"></a>.NET 'i makinenizden kaldırın: 

1. betiği Mac 'e kaydetmek için komut dosyasına sağ tıklayıp **farklı kaydet** ' i seçerek [kaldırma betiğini](https://github.com/dotnet/sdk/blob/main/scripts/obtain/uninstall/dotnet-uninstall-pkgs.sh) .net GitHub deposundan indirin.
2. Terminali açın ve çalışma dizinini betiğin indirildiği yere değiştirin:
 
    ```bash
    cd /location/of/file
    ```
3. Betiği çalıştırılabilir yapın ve **sudo** ile çalıştırın:

    ```bash
    chmod +x dotnet-uninstall-pkgs.sh 
    sudo ./ dotnet-uninstall-pkgs.sh
    sudo rm -r /etc/dotnet
    ```  

## <a name="install-supported-net-sdks"></a>Desteklenen .NET SDK 'larını yükler

1. [.NET 6 Arm64 SDK 'sını yükler](https://download.visualstudio.microsoft.com/download/pr/ed60d37e-7842-4fc2-8250-2bd66073d79e/725d486e04d27e45d2b41c687dc35f49/dotnet-sdk-6.0.100-osx-arm64.pkg)
2. yeni SDK 'nın yüklü olduğunu algılamak için Mac için Visual Studio yeniden başlatın. 
