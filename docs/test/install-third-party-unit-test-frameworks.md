---
title: 'Nasıl yapılır: Üçüncü taraf birim test çerçevelerini yükleme'
description: Visual Studio Test Gezgini, bunun için bir bağdaştırıcı arabirimi geliştiren herhangi bir birim testi çerçevesinden testleri çalıştırabilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 07/09/2020
ms.topic: how-to
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: f6cee707882c9cf4b8c16749922e844eee1c596a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148460"
---
# <a name="install-unit-test-frameworks"></a>Birim testi çerçevelerini yükleme

Visual Studio Test Gezgini, bunun için bir bağdaştırıcı arabirimi geliştiren herhangi bir birim testi çerçevesinden testleri çalıştırabilirsiniz. Çerçeveyi yüklemek ikilileri kopyalar ve Visual Studio dillere proje şablonları ekler. Şablonla bir proje ekleyebilirsiniz, çerçeve Test Gezgini'ne kaydedilir.

Bir Visual Studio, farklı çerçeveler kullanan ve farklı dilleri hedef alan birim testi projeleri içerebilir.

::: moniker range=">=vs-2019"
.NET için [MSTest, NUnit ve xUnit,](getting-started-with-unit-testing.md) varsayılan olarak Visual Studio tarafından sağlanan test çerçeveleridir. C++ için CTest gibi farklı bir test çerçevesi kümesi sağlanır.
::: moniker-end
::: moniker range="vs-2017"
[MSTest,](getting-started-with-unit-testing.md) Visual Studio tarafından sağlanan test çerçevesidir ve varsayılan olarak yüklenir.
::: moniker-end

## <a name="acquire-frameworks"></a>Çerçeveleri edinme

NuGet Paket Yöneticisi kullanarak üçüncü taraf birim **testi çerçevelerini yükleyin.**

1. Test kodunuzu içeren projeye sağ tıklayın ve Paketleri **Yönet'i NuGet seçin.**

2. Bu **NuGet Paket Yöneticisi** yüklemek istediğiniz test çerçevesini arayın ve yükle'ye **tıklayın.**

   ![NuGet Paket Yöneticisi Visual Studio](media/vs-2019/nuget-package-manager.png)

## <a name="update-to-the-latest-test-adapters"></a>En son test bağdaştırıcılarını güncelleştirme

Daha iyi test bulma ve yürütme deneyimi için en son kararlı test bağdaştırıcısına güncelleştirin. MSTest, NUnit ve xUnit test bağdaştırıcıları güncelleştirmeleri hakkında daha fazla bilgi için Visual Studio [bakın.](https://devblogs.microsoft.com/visualstudio/test-experience-improvements/)

### <a name="to-update-to-the-latest-stable-test-adapter-version"></a>En son kararlı test bağdaştırıcısı sürümüne güncelleştirmek için

1. Araçlar NuGet Paket Yöneticisi Yönet'e giderek çözümünüz için NuGet Paket Yöneticisi  >    >  **NuGet paketlerini açın.**

2. Güncelleştirmeler **sekmesine** tıklayın ve yüklü MSTest, NUnit veya xUnit test bağdaştırıcıları için arama yapın.

3. Her test bağdaştırıcısını seçin ve ardından açılan menüden en son kararlı sürümü seçin.

4. Yükle **düğmesini** seçin.

   ![Test Bağdaştırıcısını Yükseltme](media/install-adapter-upgrade.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzu birim testi](../test/unit-test-your-code.md)
