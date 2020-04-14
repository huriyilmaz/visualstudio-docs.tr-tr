---
title: Visual Studio Test Profesyonel iş yükü ve bileşen tisi
titleSuffix: ''
description: Generalist test edenler için tümleşik test araçları sağlamak için Visual Studio iş yükünü ve bileşen dalgınlarını kullanın
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.date: 03/16/2020
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.assetid: 70c03438-8434-4921-ada0-c172519af431
ms.prod: visual-studio-windows
ms.technology: vs-installation
monikerRange: vs-2017
open_to_public_contributors: false
ms.openlocfilehash: 61a52d98f695a6420dd6081117b8c6c4e83ae0a4
ms.sourcegitcommit: 22deb247ad951e4971f27fdab413b158415d0584
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81276220"
---
# <a name="visual-studio-test-professional-component-directory"></a>Visual Studio Test Profesyonel bileşen dizini

Bu sayfadaki tablolar, komut satırını kullanarak Visual Studio'yu yüklemek için kullanabileceğiniz veya VSIX bildiriminde bağımlılık olarak belirtebileceğiniz künyeleri listelediğinizde. Visual Studio'ya güncellemeler yayınlarken ek bileşenler ekleyeceğiz.

Ayrıca sayfa hakkında aşağıdaki leri unutmayın:

* Her iş yükünün kendi bölümü vardır ve ardından iş yükü kimliği ve iş yükü için kullanılabilir bileşenlerin bir tablosu vardır.
* Varsayılan olarak, iş yükünü yüklediğinizde **Gerekli** bileşenler yüklenir.
* İsterseniz, **Önerilen** ve **İsteğe Bağlı** bileşenleri de yükleyebilirsiniz.
* Ayrıca, herhangi bir iş yüküne bağlı olmayan ek bileşenleri listeleyen bir bölüm ekledik.

VSIX bildiriminizde bağımlılıkları ayarladığınızda, yalnızca Bileşen kimliklerini belirtmeniz gerekir. Minimum bileşen bağımlılıklarımızı belirlemek için bu sayfadaki tabloları kullanın. Bazı senaryolarda, bu iş yükünden yalnızca bir bileşen belirttiğiniz anlamına gelebilir. Diğer senaryolarda, tek bir iş yükünden birden çok bileşen veya birden çok iş yükünden birden çok bileşen belirtmeniz anlamına gelebilir. Daha fazla bilgi için Visual [Studio 2017 sayfasına Nasıl Taşınır: Genişletilebilirlik Projelerini Geçirin](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) sayfasına bakın.

Bu tbm'lerin nasıl kullanılacağı hakkında daha fazla bilgi için [Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) sayfasını yüklemek için Komut Satırı Parametrelerini Kullanın sayfasına bakın. Ayrıca, diğer ürünler için iş yükü ve bileşen idelerinin listesi için [Visual Studio 2017 İş Yükü ve Bileşen II'leri](workload-and-component-ids.md) sayfasına bakın.

## <a name="test-professional"></a>Test Uzmanı

**Kimlik Numarası:** Microsoft.VisualStudio.Workload.TestProfessional

**Açıklama:** Test Professional, tüm test yaşam döngüsü boyunca test gereksinimlerini karşılamalarına yardımcı olan geneltest test lerini hedefleyen entegre test araçları sağlar.

### <a name="components-included-by-this-workload"></a>Bu iş yükü tarafından dahil edilen bileşenler

Bileşen Kimliği | Adı | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Microsoft.VisualStudio.Component.TestTools.FeedbackClient | Microsoft Geri Bildirim İstemcisi | 15.6.27406.0 | Gerekli
Microsoft.visualstudio.component.testtools.microsofttestmanager | Microsoft Test Manager | 15.6.27406.0 | Gerekli

## <a name="unaffiliated-components"></a>Bağlı olmayan bileşenler

Bunlar, iş yüküne dahil olmayan, ancak tek bir bileşen olarak seçilebilen bileşenlerdir.

Bileşen Kimliği | Adı | Sürüm
--- | --- | ---
yok | yok | yok

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md)
* [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
* [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
  * [Komut satırı parametresi örnekleri](command-line-parameter-examples.md)
* [Visual Studio’nun çevrimdışı yüklemesini oluşturma](create-an-offline-installation-of-visual-studio.md)
