---
title: 'Nasıl yapılır: Üçüncü taraf birim test çerçevelerini yükleme'
ms.date: 04/01/2019
ms.topic: conceptual
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: fef59c757476b46936389ca48ca2bdaf32aec729
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653247"
---
# <a name="install-unit-test-frameworks"></a>Birim testi çerçeveleri 'ni yükler

Visual Studio Test Gezgini, bir bağdaştırıcı arabirimi geliştirmiş olan herhangi bir birim test çerçevesinden testleri çalıştırabilir. Framework 'ü yüklemek, ikilileri kopyalar ve desteklediği diller için Visual Studio proje şablonları ekler. Şablonuyla bir proje oluşturduğunuzda, çerçeve test Gezgini ile kaydedilir.

Visual Studio çözümü, farklı çerçeveleri kullanan ve farklı dillerde hedeflenen birim testi projeleri içerebilir.

[MSTest](getting-started-with-unit-testing.md) , Visual Studio tarafından sunulan ve varsayılan olarak yüklenen test çerçevesidir.

## <a name="acquire-frameworks"></a>Çerçeveleri al

**NuGet Paket Yöneticisi 'ni**kullanarak üçüncü taraf birim testi çerçeveleri ' ni yükler.

1. Test kodunuzu içerecek projeye sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.

2. **NuGet Paket Yöneticisi**' nde, yüklemek istediğiniz test çerçevesini arayın ve ardından **yükler**' i tıklatın.

   ![Visual Studio 'da NuGet Paket Yöneticisi](media/vs-2019/nuget-package-manager.png)

## <a name="update-to-the-latest-test-adapters"></a>En son test bağdaştırıcılarına Güncelleştir

Daha iyi test bulma ve yürütme deneyimi sağlamak için en son kararlı test bağdaştırıcısına güncelleştirin. MSTest, NUnit ve xUnit test bağdaştırıcılarındaki güncelleştirmeler hakkında daha fazla bilgi için bkz. [Visual Studio blogu](https://devblogs.microsoft.com/visualstudio/test-experience-improvements/).

### <a name="to-update-to-the-latest-stable-test-adapter-version"></a>En son kararlı test bağdaştırıcısı sürümüne güncelleştirmek için

1. Çözüm**için NuGet paketlerini yönet** >   > **NuGet Paket Yöneticisi** ' **ne giderek çözümünüz** için NuGet Paket Yöneticisi 'ni açın.

2. **Güncelleştirmeler** sekmesine tıklayın ve yüklü MSTest, NUnit veya xUnit test bağdaştırıcıları için arama yapın.

3. Her test bağdaştırıcısını seçin ve ardından açılan menüden en son kararlı sürümü seçin.

4. **Install** düğmesini seçin.

   ![Test bağdaştırıcısını yükselt](media/install-adapter-upgrade.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzun birim testi](../test/unit-test-your-code.md)
