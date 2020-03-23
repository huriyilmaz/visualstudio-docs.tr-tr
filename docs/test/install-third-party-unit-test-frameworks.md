---
title: 'Nasıl yapılır: Üçüncü taraf birim test çerçevelerini yükleme'
ms.date: 04/01/2019
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: b70e26adc7c0c9a8dc409d9b4b971b233418b8e1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594285"
---
# <a name="install-unit-test-frameworks"></a>Birim test çerçevelerini yükleme

Visual Studio Test Explorer bunun için bir bağdaştırıcı arabirimi geliştirmiş herhangi bir birim test çerçevesinden testler çalıştırabilirsiniz. Çerçevenin yüklenmesi ikilileri kopyalar ve desteklediği diller için Visual Studio proje şablonları ekler. Şablonlu bir proje oluşturduğunuzda, çerçeve Test Gezgini'ne kaydedilir.

Visual Studio çözümü, farklı çerçeveler kullanan ve farklı dilleri hedefleyen birim test projeleri içerebilir.

[MSTest](getting-started-with-unit-testing.md) Visual Studio tarafından sağlanan test çerçevesidir ve varsayılan olarak yüklenir.

## <a name="acquire-frameworks"></a>Çerçeveler edinme

**NuGet Package Manager'ı**kullanarak üçüncü taraf birim test çerçevelerini yükleyin.

1. Test kodunuzu içerecek projeye sağ tıklayın ve **NuGet Paketlerini Yönet'i**seçin.

2. **NuGet Paket**Yöneticisi'nde, yüklemek istediğiniz test çerçevesini arayın ve sonra **Yükle'yi**tıklatın.

   ![NuGet Paket Yöneticisi Görsel Stüdyo'da](media/vs-2019/nuget-package-manager.png)

## <a name="update-to-the-latest-test-adapters"></a>En son test bağdaştırıcılarına güncelleştir

Daha iyi test bulma ve yürütme deneyimi deneyimi için en son kararlı test bağdaştırıcısına güncelleştirin. MSTest, NUnit ve xUnit test bağdaştırıcılarına yapılan güncellemeler hakkında daha fazla bilgi için [Visual Studio bloguna](https://devblogs.microsoft.com/visualstudio/test-experience-improvements/)bakın.

### <a name="to-update-to-the-latest-stable-test-adapter-version"></a>En son kararlı test bağdaştırıcısı sürümüne güncelleştirmek için

1. **Araçlar** > **NuGet Paket Yöneticisi'ne** > yönlendirerek çözümünüz için Nuget Paket**Yöneticisi'ni**açın Çözüm için Paketleri Yönetin.

2. **Güncellemeler** sekmesine tıklayın ve yüklü MSTest, NUnit veya xUnit test bağdaştırıcılarını arayın.

3. Her test bağdaştırıcısını seçin ve ardından açılır menüdeki en son kararlı sürümü seçin.

4. **Yükle** düğmesini seçin.

   ![Yükseltme Testi Adaptörü](media/install-adapter-upgrade.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Birim kodunuzu test edin](../test/unit-test-your-code.md)
