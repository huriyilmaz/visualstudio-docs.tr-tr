---
title: Visual Studio'yı Kaldır
titleSuffix: ''
description: Visual Studio'u bilgisayarınızdan adım adım nasıl kaldırarak tamamen kaldırabilirsiniz öğrenin.
ms.date: 12/19/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- uninstall
- uninstall Visual Studio
- remove
- remove Visual Studio
- cleanup
- cleanup Visual Studio
- clean up
- clean up Visual Studio
ms.assetid: 9c81a777-9c95-4934-b517-c60c6dc78799
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 98886df1c7fb09fa30d5c54abe19452780195b6a
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649204"
---
# <a name="remove-visual-studio"></a>Visual Studio'yı Kaldır

Büyük bir hata yla karşılaşırsanız ve Visual Studio'yu onaramıyor veya kaldıramıyorsanız, Visual Studio 2017 veya Visual Studio 2019'un yüklü tüm örnekleri için yükleme dosyalarını ve ürün bilgilerini kaldırmak için `InstallCleanup.exe` aracı çalıştırabilirsiniz.

> [!WARNING]
> InstallCleanup aracını yalnızca onarım veya kaldırma başarısız olursa **son çare olarak** kullanın. Bu araç, diğer Visual Studio yüklemelerinden veya diğer ürünlerden gelen ve daha sonra onarılması veya yeniden yüklenmesi gerekebilecek özellikleri kaldırabilir.

## <a name="run-installcleanupexe"></a>InstallCleanup.exe çalıştırın

`InstallCleanup.exe` Araçla aşağıdaki komut satırı anahtarlarından birini kullanabilirsiniz:

| Anahtar | Davranış |
| ------ | -------- |
| `-i`   | Başka bir anahtar geçirilirse, bu anahtar varsayılandır. Yalnızca ana yükleme dizini ve ürün bilgilerini kaldırır. `InstallCleanup.exe` Aracı çalıştırdıktan sonra Visual Studio'nun aynı sürümünü yeniden yüklemek istiyorsanız bu anahtarı kullanın. |
| `-f`   | Bu anahtar, yükleme dizininin dışında yüklenen ve diğer Visual Studio yüklemeleri veya diğer ürünlerle de paylaşılabilecek ana yükleme dizinini, ürün bilgilerini ve diğer özellikleri kaldırır. Visual Studio'u daha sonra yeniden yüklemeden kaldırmak istiyorsanız bu anahtarı kullanın. |

`InstallCleanup.exe` Aracı şu şekilde çalıştırabilirsiniz:

1. Visual Studio Yükleyicisi’ni kapatın.
1. Yönetici komut istemini açın. Yönetici komut istemini açmak için aşağıdaki adımları izleyin:
   * "Aramak için buraya yazın" kutusuna **cmd** yazın.
   * **Komut İstemi'ni**sağ tıklatın ve ardından **yönetici olarak Çalıştır'ı**seçin.
1. `InstallCleanup.exe` Aracın tam yolunu girin ve tercih ettiğiniz komut satırı anahtarını ekleyin. Varsayılan olarak, aracın yolu aşağıdaki gibidir. Çift tırnak boşlukiçeren bir komut u içine:

   ```
   "C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe"
   ```

   > [!NOTE]
   > Visual Studio Installer `InstallCleanup.exe` dizininin altında her zaman bulunan bu dizini `%ProgramFiles(x86)%\Microsoft Visual Studio`bulamıyorsanız, bir sonraki yapmanız gerekenler aşağıda bulabilirsiniz. Visual Studio [yüklemek](install-visual-studio.md)için yönergeleri izleyin. Ardından, iş yükü seçim ekranı görüntülendiğinde, pencereyi kapatın ve bu sayfadaki adımları yeniden izleyin.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleme](install-visual-studio.md)
* [Visual Studio’yu güncelleştirme](update-visual-studio.md)
* [Visual Studio’yu değiştirme](modify-visual-studio.md)
* [Visual Studio'yu kaldırma](uninstall-visual-studio.md)
