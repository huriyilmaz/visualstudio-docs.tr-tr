---
title: Visual Studio 'Yu kaldırma 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- uninstalling
- uninstalling visual studio
- uninstall
- uninstall Visual Studio
ms.assetid: 0e445255-b796-426d-ad93-a4d8e36da2c5
caps.latest.revision: 9
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: ed9d33501644c6fa7252dffa758f92c0919653b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62546908"
---
# <a name="uninstall-visual-studio"></a>Visual Studio'yu kaldırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio ile ilgili en son belgeler için bkz. [Visual Studio 'Yu kaldırma](/visualstudio/install/uninstall-visual-studio).

Bu sayfada, geliştiriciler için tümleşik üretkenlik araçları takımımızın önceki bir sürümü olan Visual Studio 2015 ' yi kaldırma işlemi adım adım açıklanmaktadır.

## <a name="uninstall-visual-studio-by-using-the-standard-uninstallation-method"></a>"Standart" kaldırma yöntemini kullanarak Visual Studio 'Yu kaldırın

1. **Denetim Masası**' nda, **Programlar ve Özellikler** sayfasında, kaldırmak istediğiniz ürün sürümünü seçin ve ardından **Değiştir**' i seçin.

2. Kurulum sihirbazında, **Kaldır**' ı seçin, **Evet**' i seçin ve ardından sihirbazda kalan yönergeleri izleyin.

   Bu standart veya varsayılan yöntem, ilk Visual Studio yüklemenizin (örneğin, Microsoft .NET Framework, Microsoft Visual C++ yeniden dağıtılabilir, Microsoft SQL Server, vb.) geri yüklendiği bazı öğeleri bırakır.   Diğer birçok uygulamanın bu uygulamalara bağımlı olması nedeniyle bunları yükledik. Ancak, bunları da kaldırmak istiyorsanız, **Programlar ve Özellikler**' de bunların girişini seçin ve her birini ayrı ayrı kaldırın.

## <a name="uninstall-visual-studio-and-all-other-related-files-that-is-to-uninstall-almost-everything"></a>Visual Studio 'Yu ve diğer tüm ilgili dosyaları (yani, neredeyse her şeyi kaldırmak için) kaldırın

1. Visual Studio. exe dosyasını bulun (örneğin, "vs_enterprise.exe" konumunu bulun).

    > [!NOTE]
    > Dosya "%ProgramData%\Package cache" öğesinin bir alt klasöründe olmalıdır, örneğin: C:\ProgramData\Package cache \\ {37e19555-e88d-4aed-9d42-82d0784d2b79} \vs_enterprise.exe

2. /Uninstall/Force komut satırı parametrelerini kullanarak. exe dosyasını çalıştırın.

     Örneğin, ```vs_enterprise.exe /uninstall /force``` Visual Studio 'yu ve varsayılan bir kaldırma işleminin arkasında kalan çekirdek bileşenlerin çoğunu kaldıracak olan öğesini çalıştırın. Ancak, Visual Studio eklentileri ve uzantılarının yükleyebileceği ek içeriğin tümünü kaldırmaz (örneğin, Visual Studio güncelleştirmeleri ve diğer isteğe bağlı bileşenler).

    > [!TIP]
    > Alternatif olarak, Visual Studio 'Nun veya Visual Studio güncelleştirmelerinin yüklediği her şeyi kaldırmak için "**Toplam UnInstaller**" aracını kullanabilirsiniz. Diğer bir deyişle, Visual Studio 2013 veya üzeri bir sürümü. Daha fazla bilgi edinmek için GitHub 'daki [Visual Studio Uninstaller aracını](https://github.com/Microsoft/VisualStudioUninstaller/releases) inceleyin.

## <a name="uninstall-visual-studio-in-silent-or-passive-modes-that-is-to-uninstall-from-source"></a>Visual Studio 'Yu sessiz veya pasif modlarda kaldırın (diğer bir deyişle, kaynaktan kaldırma)

1. Visual Studio'nun yüklü olduğu bilgisayarda Windows komut istemini açın.

2. Aşağıdaki parametreleri girin:

     *DVDRoot* \\<yükleme dosyası \> \</quiet&#124;/passive> [/norestart]/Uninstall

## <a name="roll-back-to-a-previous-version-or-release-of--visual-studio"></a>Visual Studio 'nun önceki bir sürümüne geri dönme

1. Bu konuda listelenen yöntemlerden birini kullanarak Visual Studio 'Yu kaldırın.

   > [!WARNING]
   > Visual Studio 'nun geçerli bir sürümünü (veya bir Visual Studio güncelleştirmesini) kaldırmak ve daha sonra önceki bir sürümü yüklemek beklendiği gibi çalışmayabilir.
   >
   > Sonuç, yüklediğiniz Visual Studio sürümüne veya sürümüne, bileşenlerinin hangi sürümlerinin yüklü olduğuna, hangi ürünlerin yüklü olduğunu, Visual Studio sürümü ya da bileşenlerinden biri ve son olarak yüklemeyi veya yeniden yüklemeyi planladığınız daha eski Visual Studio sürümü olan bir sürüme bağlıdır.  Tüm bu değişkenler nedeniyle, standart kaldırma işlemi, önceki Visual Studio sürümleri veya sürümleriyle çalışmayan bileşenleri genellikle arkasında bırakır.
   >
   > Bu nedenle, en iyi sonuçlar için, [Visual Studio UnInstaller aracının](https://github.com/Microsoft/VisualStudioUninstaller/releases)kullanılmasını öneririz.

2. Visual Studio 'nun kullanmak istediğiniz önceki sürümünü yükleyin veya yeniden yükleyin.

   Visual Studio 'nun önceki bir sürümünü yükleseniz bile, Kurulum programı, varsa, daha yeni bir sürüm veya sürüm kullanmayı denemeye devam edebilir. Daha ayrıntılı bilgi için bkz. [nasıl yapılır: Visual Studio 'Nun belirli bir sürümünü yüklemek](../install/how-to-install-a-specific-release-of-visual-studio.md) konusunun.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'yu yükleme](https://msdn.microsoft.com/library/e2h7fzkw.aspx)