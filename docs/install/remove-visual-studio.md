---
title: Kaldırma Visual Studio
titleSuffix: ''
description: Adım adım bilgisayarınızdan Visual Studio kaldırmayı öğrenin.
ms.date: 08/24/2021
ms.custom: vs-acquisition
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
ms.openlocfilehash: 360124f0e831233728ba8b4c222e6ad2106ef098
ms.sourcegitcommit: 215680b355cf613bfa125cf6b864c8bb5f2c71a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2021
ms.locfileid: "132453587"
---
# <a name="remove-visual-studio"></a>Kaldırma Visual Studio

Yıkıcı bir hatayla karşılaştınız ve Visual Studio'ı onaramaz veya kaldıramazsanız, `InstallCleanup.exe` Visual Studio 2017, Visual Studio 2019 veya Visual Studio 2022'nin tüm yüklü örnekleri için yükleme dosyalarını ve ürün bilgilerini kaldırmak için aracı çalıştırabilirsiniz.

> [!WARNING]
> Onarım veya kaldırma başarısız olursa **InstallCleanup aracını yalnızca** son çözüm olarak kullanın. Bu araç, özellikleri diğer Visual Studio yüklemelerinden veya diğer ürünlerden kaldırarak onarılması veya yeniden yüklenmesi gerekebilir.

## <a name="run-installcleanupexe"></a>Çalıştırma InstallCleanup.exe

Araçla aşağıdaki komut satırı anahtarlardan birini `InstallCleanup.exe` kullanabilirsiniz:

| Anahtar | Davranış |
|-----------------|--------------------|
|  `-i [version]`   | Bu anahtar, başka bir anahtar geçirilamazsa varsayılan değerdir. Yalnızca ana yükleme dizinini ve ürün bilgilerini kaldırır. Aracı çalıştırdikten sonra aynı sürümü yeniden yüklemek Visual Studio bu anahtarı `InstallCleanup.exe` kullanın. Bir değer `[version]` belirtilirse, yalnızca bu dize değeriyle başlangıç sürümüne sahip ürünler kaldırılır. |
|   `-f`           | Bu anahtar ana yükleme dizinini, ürün bilgilerini ve yükleme dizininin dışında yüklü olan ve diğer yüklemeler veya diğer ürünlerle Visual Studio diğer özellikleri kaldırır. Daha sonra yeniden yüklemeden bu anahtarı Visual Studio bu anahtarı kullanın. |

Aracı şu şekilde `InstallCleanup.exe` çalıştırabilirsiniz:

1. Visual Studio Yükleyicisi’ni kapatın.
1. Yönetici komut istemini açın. Yönetici komut istemini açmak için şu adımları izleyin:
   * "Aramak için buraya yazın" kutusuna **cmd** yazın.
   * Komut **İstemi'ne sağ tıklayın** ve ardından Yönetici olarak **çalıştır'ı seçin.**
1. Aracın tam yolunu `InstallCleanup.exe` girin ve istediğiniz komut satırı anahtarını ekleyin. Varsayılan olarak, aracın yolu aşağıdaki gibidir. Çift tırnak, boşluk içeren bir komutu içerir:

   ```shell
   "C:\Program Files (x86)\Microsoft Visual Studio\Installer\InstallCleanup.exe"
   ```

   > [!NOTE]
   > Her zaman dizininde bulunan Visual Studio Yükleyicisi dizininde `InstallCleanup.exe` bulamazsanız, `%ProgramFiles(x86)%\Microsoft Visual Studio` bundan sonra yapacaklar şu şekildedir. 'i yüklemek için [yönergeleri Visual Studio.](install-visual-studio.md) Ardından iş yükü seçim ekranı görüntülendiğinde pencereyi kapatın ve bu sayfada yer alan adımları tekrar izleyin.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleme](install-visual-studio.md)
* [Visual Studio’yu güncelleştirme](update-visual-studio.md)
* [Visual Studio’yu değiştirme](modify-visual-studio.md)
* [Visual Studio'yu kaldırma](uninstall-visual-studio.md)
