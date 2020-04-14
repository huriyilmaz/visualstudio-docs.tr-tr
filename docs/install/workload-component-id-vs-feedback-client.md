---
title: Visual Studio Geri Bildirim İstemci iş yükü ve bileşen itlemi
titleSuffix: ''
description: Azure DevOps Hizmetleri veya Team Foundation Server için zengin geri bildirim sağlamak için Visual Studio iş yükünü ve bileşen tünalarını kullanın
keywords: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.date: 11/13/2018
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.assetid: 7392a100-100c-458c-9394-828695109015
ms.prod: visual-studio-windows
ms.technology: vs-installation
monikerRange: vs-2017
open_to_public_contributors: false
ms.openlocfilehash: fe4eec389389622f0d87d30edbbd46d7c5b53d80
ms.sourcegitcommit: 22deb247ad951e4971f27fdab413b158415d0584
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81276311"
---
# <a name="visual-studio-feedback-client-component-directory"></a>Visual Studio Geri bildirim İstemci bileşen dizini

Bu sayfadaki tablolar, komut satırını kullanarak Visual Studio'yu yüklemek için kullanabileceğiniz veya VSIX bildiriminde bağımlılık olarak belirtebileceğiniz künyeleri listelediğinizde. Visual Studio'ya güncellemeler yayınlarken ek bileşenler ekleyeceğiz.

Ayrıca sayfa hakkında aşağıdaki leri unutmayın:

* Her iş yükünün kendi bölümü vardır ve ardından iş yükü kimliği ve iş yükü için kullanılabilir bileşenlerin bir tablosu vardır.
* Varsayılan olarak, iş yükünü yüklediğinizde **Gerekli** bileşenler yüklenir.
* İsterseniz, **Önerilen** ve **İsteğe Bağlı** bileşenleri de yükleyebilirsiniz.
* Ayrıca, herhangi bir iş yüküne bağlı olmayan ek bileşenleri listeleyen bir bölüm ekledik.

VSIX bildiriminizde bağımlılıkları ayarladığınızda, yalnızca Bileşen kimliklerini belirtmeniz gerekir. Minimum bileşen bağımlılıklarımızı belirlemek için bu sayfadaki tabloları kullanın. Bazı senaryolarda, bu iş yükünden yalnızca bir bileşen belirttiğiniz anlamına gelebilir. Diğer senaryolarda, tek bir iş yükünden birden çok bileşen veya birden çok iş yükünden birden çok bileşen belirtmeniz anlamına gelebilir. Daha fazla bilgi için Visual [Studio 2017 sayfasına Nasıl Taşınır: Genişletilebilirlik Projelerini Geçirin](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) sayfasına bakın.

Bu tbm'lerin nasıl kullanılacağı hakkında daha fazla bilgi için [Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) sayfasını yüklemek için Komut Satırı Parametrelerini Kullanın sayfasına bakın. Ayrıca, diğer ürünler için iş yükü ve bileşen idelerinin listesi için [Visual Studio 2017 İş Yükü ve Bileşen II'leri](workload-and-component-ids.md) sayfasına bakın.

## <a name="feedback-client"></a>Geribildirim İstemcisi

**Kimlik Numarası:** Microsoft.VisualStudio.Workload.FeedbackClient

**Açıklama:** Geri bildirim istemcisi, Hissedarların Azure DevOps Hizmetleri veya Team Foundation Server için zengin geri bildirimler sağlamasına olanak tanır.

### <a name="components-included-by-this-workload"></a>Bu iş yükü tarafından dahil edilen bileşenler

Bileşen Kimliği | Adı | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Microsoft.VisualStudio.Component.TestTools.FeedbackClient | Microsoft Geri Bildirim İstemcisi | 15.6.27406.0 | Gerekli

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
