---
title: Visual Studio kaldır
titleSuffix: ''
description: Visual Studio bilgisayarınızdan tamamen kaldırmayı öğrenin, adım adım.
ms.date: 08/17/2021
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
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 82545d775d03b13ce87ea11682124f43e70856cf
ms.sourcegitcommit: f930bc28bdb0ba01d6f7cb48f229afecfa0c90cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2021
ms.locfileid: "122334706"
---
# <a name="remove-visual-studio"></a>Visual Studio kaldır

Visual Studio çok önemli bir hatayla karşılaşırsanız ve `InstallCleanup.exe` Visual Studio 2017, Visual Studio 2019 veya Visual Studio 2022 yüklü tüm örnekleri için yükleme dosyalarını ve ürün bilgilerini kaldırmak üzere aracı çalıştırabilirsiniz.

> [!WARNING]
> Yalnızca onarma veya kaldırma başarısız olursa, ınstallcleanup aracını **yalnızca son çare olarak** kullanın. bu araç diğer Visual Studio yüklemelerinden veya diğer ürünlerden özellikleri kaldırabilir, bu da onarılması veya yeniden yüklenmesi gerekebilir.

## <a name="run-installcleanupexe"></a>InstallCleanup.exe Çalıştır

Araçla aşağıdaki komut satırı anahtarlarından birini kullanabilirsiniz `InstallCleanup.exe` :

| Anahtar | Davranış                                                                                                                                                                                                                                                                                                                 |
|--------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-i`   | Başka bir anahtar geçirilmezse bu anahtar varsayılandır. Yalnızca ana yükleme dizinini ve ürün bilgilerini kaldırır. aracı çalıştırdıktan sonra aynı Visual Studio sürümünü yeniden yüklemek istiyorsanız bu anahtarı kullanın `InstallCleanup.exe` .                                                              |
| `-f`   | bu anahtar, ana yükleme dizinini, ürün bilgilerini ve yükleme dizini dışında yüklenen diğer birçok özelliği kaldırır, diğer Visual Studio yüklemeleri veya diğer ürünlerle de paylaşılabilir. daha sonra yeniden yüklemeden Visual Studio kaldırmak istiyorsanız bu anahtarı kullanın. |

Aracın nasıl çalıştırılacağı aşağıda verilmiştir `InstallCleanup.exe` :

1. Visual Studio Yükleyicisi’ni kapatın.
1. Bir yönetici komut istemi açın. Bir yönetici komut istemi açmak için şu adımları izleyin:
   * "Aramak için buraya yazın" kutusuna **cmd** yazın.
   * **Komut istemi**' ne sağ tıklayın ve ardından **yönetici olarak çalıştır**' ı seçin.
1. Aracın tam yolunu girin `InstallCleanup.exe` ve tercih ettiğiniz komut satırı anahtarını ekleyin. Varsayılan olarak, aracın yolu aşağıdaki gibidir. Çift tırnak işaretleri, boşluk içeren bir komutu kapsar:

   ```shell
   "C:\Program Files (x86)\Microsoft Visual Studio\Installer\InstallCleanup.exe"
   ```

   > [!NOTE]
   > `InstallCleanup.exe`her zaman içinde bulunan Visual Studio Yükleyicisi dizin altında bulamazsanız `%ProgramFiles(x86)%\Microsoft Visual Studio` , daha sonra yapmanız gerekenler aşağıda verilmiştir. [Visual Studio yüklemek](install-visual-studio.md)için yönergeleri izleyin. Sonra, iş yükü seçim ekranı görüntülendiğinde, pencereyi kapatın ve bu sayfadaki adımları yeniden izleyin.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleme](install-visual-studio.md)
* [Visual Studio’yu güncelleştirme](update-visual-studio.md)
* [Visual Studio’yu değiştirme](modify-visual-studio.md)
* [Visual Studio'yu kaldırma](uninstall-visual-studio.md)
