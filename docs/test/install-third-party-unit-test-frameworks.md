---
title: 'Nasıl yapılır: Üçüncü taraf birim test çerçevelerini yükleme'
ms.date: 07/09/2020
ms.topic: how-to
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: c274f203b9bf2746716c0625c61141aaa332977a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86387193"
---
# <a name="install-unit-test-frameworks"></a>Birim testi çerçeveleri 'ni yükler

Visual Studio Test Gezgini, bir bağdaştırıcı arabirimi geliştirmiş olan herhangi bir birim test çerçevesinden testleri çalıştırabilir. Framework 'ü yüklemek, ikilileri kopyalar ve desteklediği diller için Visual Studio proje şablonları ekler. Şablonuyla bir proje oluşturduğunuzda, çerçeve test Gezgini ile kaydedilir.

Visual Studio çözümü, farklı çerçeveleri kullanan ve farklı dillerde hedeflenen birim testi projeleri içerebilir.

::: moniker range=">=vs-2019"
.NET, [MSTest, NUnit ve xUnit](getting-started-with-unit-testing.md) için varsayılan olarak yüklenen Visual Studio tarafından sunulan test çerçeveleri vardır.
::: moniker-end
::: moniker range="vs-2017"
[MSTest](getting-started-with-unit-testing.md) , Visual Studio tarafından sunulan ve varsayılan olarak yüklenen test çerçevesidir.
::: moniker-end

## <a name="acquire-frameworks"></a>Çerçeveleri al

**NuGet Paket Yöneticisi 'ni**kullanarak üçüncü taraf birim testi çerçeveleri ' ni yükler.

1. Test kodunuzu içerecek projeye sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.

2. **NuGet Paket Yöneticisi**' nde, yüklemek istediğiniz test çerçevesini arayın ve ardından **yükler**' i tıklatın.

   ![Visual Studio 'da NuGet Paket Yöneticisi](media/vs-2019/nuget-package-manager.png)

## <a name="update-to-the-latest-test-adapters"></a>En son test bağdaştırıcılarına Güncelleştir

Daha iyi test bulma ve yürütme deneyimi sağlamak için en son kararlı test bağdaştırıcısına güncelleştirin. MSTest, NUnit ve xUnit test bağdaştırıcılarındaki güncelleştirmeler hakkında daha fazla bilgi için bkz. [Visual Studio blogu](https://devblogs.microsoft.com/visualstudio/test-experience-improvements/).

### <a name="to-update-to-the-latest-stable-test-adapter-version"></a>En son kararlı test bağdaştırıcısı sürümüne güncelleştirmek için

1. **Araçlar**  >  **NuGet Paket Yöneticisi**  >  **çözüm için NuGet Paketlerini Yönet**' e giderek çözümünüz için NuGet Paket Yöneticisi 'ni açın.

2. **Güncelleştirmeler** sekmesine tıklayın ve yüklü MSTest, NUnit veya xUnit test bağdaştırıcıları için arama yapın.

3. Her test bağdaştırıcısını seçin ve ardından açılan menüden en son kararlı sürümü seçin.

4. **Install** düğmesini seçin.

   ![Test bağdaştırıcısını yükselt](media/install-adapter-upgrade.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzun birim testi](../test/unit-test-your-code.md)
