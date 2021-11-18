---
title: Apple Silicon machines üzerinde 8,10 ve .net Mac için Visual Studio
description: M1 makinelerinde 2019 ' de çalışan .NET sürümünün desteklenen sürümlerini alma adımları.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/08/2021
ms.assetid: db2dc420-63d2-44ef-bdda-a351561dc900
ms.openlocfilehash: 333f6cb27ef7a3f94556f1e7a7b1caae514292ef
ms.sourcegitcommit: 76541583274c4af4218ac2a8ab4308077a7e340e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2021
ms.locfileid: "132733198"
---
# <a name="visual-studio-for-mac-810-and-net-on-apple-silicon-machines"></a>Apple Silicon machines üzerinde 8,10 ve .net Mac için Visual Studio

Apple Silicon machines 'de (M1 veya ARM olarak da bilinir) Mac için Visual Studio 8,10, şu anda kasım ayında yayınlanan .net 6, .net 5 ve .net Core 3,1 x64 sdk 'larını desteklememektedir. Ayrıca .NET 6 Arm64 SDK 'sını desteklemez. bunlardan herhangi biri yüklüyse, Mac için Visual Studio 8,10 ' i keser ve kaldırılması gerekir ve eski .net sdk 'ları yüklü olur. 

> [!NOTE]
> bu bilgiler Mac için Visual Studio 2019 (8.10. x) sürümleri için özeldir. Mac için Visual Studio 2022 önizleme sürümleri için bu işlem hakkında bilgi için bkz. ayrıntılar için [Apple Silicon machines hakkında Mac için Visual Studio 17,0 ve .net](/uninstall-net-2022.md) .

## <a name="uninstall-net-from-your-machine"></a>.NET 'i makinenizden kaldırın: 

1. betiği Mac 'e kaydetmek için komut dosyasına sağ tıklayıp **farklı kaydet** ' i seçerek [kaldırma betiğini](https://github.com/dotnet/sdk/blob/main/scripts/obtain/uninstall/dotnet-uninstall-pkgs.sh) .net GitHub deposundan indirin.
2. Terminali açın ve çalışma dizinini betiğin indirildiği yere değiştirin:
 
    ```bash
    cd /location/of/file
    ```
3. Betiği çalıştırılabilir yapın ve **sudo** ile çalıştırın:

    ```bash
    chmod +x dotnet-uninstall-pkgs.sh 
    sudo ./dotnet-uninstall-pkgs.sh
    sudo rm -r /etc/dotnet
    ```  

## <a name="install-supported-net-sdks"></a>Desteklenen .NET SDK 'larını yükler

1. .NET 5 ve .NET Core 3,1 x64 SDK 'larının Ekim sürümlerini yükler 
    - [.NET 5.0.402 x64 SDK](https://download.visualstudio.microsoft.com/download/pr/88bc1553-e90f-4a4f-9574-65d9a5065cd2/1d5646e1abb8b4d4a61ba0b0be976047/dotnet-sdk-5.0.402-osx-x64.pkg)
    - [.NET Core 3.1.414 x64 SDK](https://download.visualstudio.microsoft.com/download/pr/0517421d-3300-42c7-a420-e42d55068126/76b722e65c0745962156e622ed76501c/dotnet-sdk-3.1.414-osx-x64.pkg)
2. yeni sdk 'ların yüklü olduğunu algılaması için Mac için Visual Studio yeniden başlatın. 
