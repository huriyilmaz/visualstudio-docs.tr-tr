---
title: Visual Studio 'Yu kaldır
titleSuffix: ''
description: Visual Studio 'Yu bilgisayarınızdan tamamen kaldırmayı öğrenin, adım adım.
ms.date: 12/19/2019
ms.custom: seodec18
ms.topic: how-to
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
ms.openlocfilehash: b26e837ec2c4155c1be0b3639368c4315d2aecd3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85418931"
---
# <a name="remove-visual-studio"></a>Visual Studio 'Yu kaldır

Çok önemli bir hatayla karşılaşırsanız ve Visual Studio 'Yu onaramıyorsanız veya kaldıramıyorsanız, `InstallCleanup.exe` Visual studio 2017 veya Visual studio 2019 ' nin yüklü tüm örnekleri için yükleme dosyalarını ve ürün bilgilerini kaldırmak üzere aracı çalıştırabilirsiniz.

> [!WARNING]
> Yalnızca onarma veya kaldırma başarısız olursa, ınstallcleanup aracını **yalnızca son çare olarak** kullanın. Bu araç diğer Visual Studio yüklemelerinin veya diğer ürünlerin özelliklerini kaldırabilir, bu da onarılması veya yeniden yüklenmesi gerekebilir.

## <a name="run-installcleanupexe"></a>InstallCleanup.exe Çalıştır

Araçla aşağıdaki komut satırı anahtarlarından birini kullanabilirsiniz `InstallCleanup.exe` :

| Anahtar | Davranış |
| ------ | -------- |
| `-i`   | Başka bir anahtar geçirilmezse bu anahtar varsayılandır. Yalnızca ana yükleme dizinini ve ürün bilgilerini kaldırır. Aracı çalıştırdıktan sonra aynı Visual Studio sürümünü yeniden yüklemek istiyorsanız bu anahtarı kullanın `InstallCleanup.exe` . |
| `-f`   | Bu anahtar, ana yükleme dizinini, ürün bilgilerini ve yükleme dizini dışında yüklenen diğer birçok özelliği kaldırır. Bu, diğer Visual Studio yüklemeleri veya diğer ürünlerle de paylaşılabilir. Visual Studio 'Yu daha sonra yeniden yüklemeden kaldırmak istiyorsanız bu anahtarı kullanın. |

Aracın nasıl çalıştırılacağı aşağıda verilmiştir `InstallCleanup.exe` :

1. Visual Studio Yükleyicisi’ni kapatın.
1. Bir yönetici komut istemi açın. Bir yönetici komut istemi açmak için şu adımları izleyin:
   * "Aramak için buraya yazın" kutusuna **cmd** yazın.
   * **Komut istemi**' ne sağ tıklayın ve ardından **yönetici olarak çalıştır**' ı seçin.
1. Aracın tam yolunu girin `InstallCleanup.exe` ve tercih ettiğiniz komut satırı anahtarını ekleyin. Varsayılan olarak, aracın yolu aşağıdaki gibidir. Çift tırnak işaretleri, boşluk içeren bir komutu kapsar:

   ```
   "C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe"
   ```

   > [!NOTE]
   > `InstallCleanup.exe`Her zaman içinde bulunan Visual Studio yükleyicisi dizin altında bulamazsanız `%ProgramFiles(x86)%\Microsoft Visual Studio` , daha sonra yapmanız gerekenler aşağıda verilmiştir. [Visual Studio 'yu yüklemek](install-visual-studio.md)için yönergeleri izleyin. Sonra, iş yükü seçim ekranı görüntülendiğinde, pencereyi kapatın ve bu sayfadaki adımları yeniden izleyin.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleme](install-visual-studio.md)
* [Visual Studio’yu güncelleştirme](update-visual-studio.md)
* [Visual Studio’yu değiştirme](modify-visual-studio.md)
* [Visual Studio'yu kaldırma](uninstall-visual-studio.md)
