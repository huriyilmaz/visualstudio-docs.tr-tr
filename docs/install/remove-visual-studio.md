---
title: Visual Studio Kaldır
titleSuffix: ''
description: Visual Studio 'Yu bilgisayarınızdan tamamen kaldırmayı öğrenin, adım adım.
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
ms.openlocfilehash: b0e8c8fe10451e9e5906eabf7f4f65086d147904
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76113718"
---
# <a name="remove-visual-studio"></a>Visual Studio Kaldır

Çok önemli bir hatayla karşılaşırsanız ve Visual Studio 'yu onaramıyorsanız veya kaldıramıyorsanız, Visual Studio 2017 veya Visual Studio 2019 ' nin yüklü tüm örneklerine ilişkin yükleme dosyalarını ve ürün bilgilerini kaldırmak için `InstallCleanup.exe` aracını çalıştırabilirsiniz.

> [!WARNING]
> Yalnızca onarma veya kaldırma başarısız olursa, ınstallcleanup aracını **yalnızca son çare olarak** kullanın. Bu araç diğer Visual Studio yüklemelerinin veya diğer ürünlerin özelliklerini kaldırabilir, bu da onarılması veya yeniden yüklenmesi gerekebilir.

## <a name="run-installcleanupexe"></a>Installcleanup. exe dosyasını çalıştır

`InstallCleanup.exe` aracı ile aşağıdaki komut satırı anahtarlarından birini kullanabilirsiniz:

| Anahtar | Davranış |
| ------ | -------- |
| `-i`   | Başka bir anahtar geçirilmezse bu anahtar varsayılandır. Yalnızca ana yükleme dizinini ve ürün bilgilerini kaldırır. `InstallCleanup.exe` aracını çalıştırdıktan sonra Visual Studio 'nun aynı sürümünü yeniden yüklemek istiyorsanız bu anahtarı kullanın. |
| `-f`   | Bu anahtar, ana yükleme dizinini, ürün bilgilerini ve yükleme dizini dışında yüklenen diğer birçok özelliği kaldırır. Bu, diğer Visual Studio yüklemeleri veya diğer ürünlerle de paylaşılabilir. Visual Studio 'Yu daha sonra yeniden yüklemeden kaldırmak istiyorsanız bu anahtarı kullanın. |

`InstallCleanup.exe` aracını çalıştırmak için aşağıdaki adımları uygulayın:

1. Visual Studio Yükleyicisi’ni kapatın.
1. Bir yönetici komut istemi açın. Bir yönetici komut istemi açmak için şu adımları izleyin:
   * "Aramak için buraya yazın" kutusuna **cmd** yazın.
   * **Komut istemi**' ne sağ tıklayın ve ardından **yönetici olarak çalıştır**' ı seçin.
1. `InstallCleanup.exe` aracının tam yolunu girin ve tercih ettiğiniz komut satırı anahtarını ekleyin. Varsayılan olarak, aracın yolu aşağıdaki gibidir:

   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```

   > [!NOTE]
   > Her zaman `%ProgramFiles(x86)%\Microsoft Visual Studio`' de bulunan Visual Studio Yükleyicisi dizin altında `InstallCleanup.exe` bulamazsanız, daha sonra yapmanız gerekenler aşağıda verilmiştir. [Visual Studio 'yu yüklemek](install-visual-studio.md)için yönergeleri izleyin. Sonra, iş yükü seçim ekranı görüntülendiğinde, pencereyi kapatın ve bu sayfadaki adımları yeniden izleyin.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleyin](install-visual-studio.md)
* [Visual Studio’yu güncelleştirme](update-visual-studio.md)
* [Visual Studio’yu değiştirme](modify-visual-studio.md)
* [Visual Studio'yu kaldırma](uninstall-visual-studio.md)
