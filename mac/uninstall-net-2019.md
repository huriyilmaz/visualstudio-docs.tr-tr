---
title: Mac için Visual Studio Apple Silikon makinelerde 8.10 ve .NET
description: M1 makinelerde 2019'da çalışan desteklenen .NET sürümlerini alma adımları.
author: jmatthiesen
ms.author: jomatthi
manager: dominicn
ms.date: 11/08/2021
ms.topic: how-to
ms.assetid: db2dc420-63d2-44ef-bdda-a351561dc900
ms.openlocfilehash: 3cfda970cbada8ac746603f2439028552bd08478
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135805565"
---
# <a name="visual-studio-for-mac-810-and-net-on-apple-silicon-machines"></a>Mac için Visual Studio Apple Silikon makinelerde 8.10 ve .NET

Apple Silikon makinelerde (M1 veya ARM olarak da bilinir), Mac için Visual Studio 8.10 şu anda Kasım ayında yayımlanan .NET 6, .NET 5 ve .NET Core 3.1 x64 SDK'larını desteklememektedir. .NET 6 Arm64 SDK'sı da desteklemez. Bunlardan herhangi biri yüklüyse, 8.10'Mac için Visual Studio ve kaldırılması gereken eski .NET SDK'leri kaldırılır. 

> [!NOTE]
> Bu bilgiler, Mac için Visual Studio 2019 (8.10.x) sürümlerine özeldir. Mac için Visual Studio 2022 Preview sürümlerine ilişkin bu işlem hakkında bilgi için ayrıntılar için Apple Silikon Mac için Visual Studio [17.0 ve .NET'e](/visualstudio/mac/uninstall-net-2022) bakın.

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

1. .NET 5 ve .NET Core 3.1 x64 SDK'larının Ekim yayınlarını yükleme 
    - [.NET 5.0.402 x64 SDK](https://download.visualstudio.microsoft.com/download/pr/88bc1553-e90f-4a4f-9574-65d9a5065cd2/1d5646e1abb8b4d4a61ba0b0be976047/dotnet-sdk-5.0.402-osx-x64.pkg)
    - [.NET Core 3.1.414 x64 SDK](https://download.visualstudio.microsoft.com/download/pr/0517421d-3300-42c7-a420-e42d55068126/76b722e65c0745962156e622ed76501c/dotnet-sdk-3.1.414-osx-x64.pkg)
2. Yeni Mac için Visual Studio algılaması için yeniden başlatın. 
