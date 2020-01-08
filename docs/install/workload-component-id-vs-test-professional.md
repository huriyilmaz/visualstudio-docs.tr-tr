---
title: Visual Studio Test Professional iş yükü ve bileşen kimlikleri
titleSuffix: ''
description: Tümleşik test araçları için genel test edicileri sağlamak için Visual Studio iş yükü ve Bileşen kimlikleri kullanın
author: jillre
ms.author: jillfra
manager: jillfra
ms.date: 09/23/2019
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.assetid: 70c03438-8434-4921-ada0-c172519af431
ms.prod: visual-studio-windows
ms.technology: vs-installation
monikerRange: vs-2017
ms.openlocfilehash: 9ed75c9731d36f48dcb50be7f929c4cba5ed3b6c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590907"
---
# <a name="visual-studio-test-professional-component-directory"></a>Visual Studio Test Professional bileşen dizini

Tabloları bu sayfa listesi kimliklerinin komut satırını kullanarak Visual Studio'yu yüklemek için kullanabilirsiniz veya bağımlılık VSIX bildirimi olarak belirtebilirsiniz. Visual Studio güncelleştirmeleri yayınlayabilir gibi ek bileşenler ekleyeceğiz olduğunu unutmayın.

Ayrıca sayfa hakkında aşağıdakileri unutmayın:

* Her iş yükü, izlediği iş yükü kimliği ve iş yükü için kullanılabilir olan bileşenlerin bir tablo, kendi bölümü vardır.
* Varsayılan olarak, **gerekli** bileşenleri, iş yükünü yüklediğinizde yüklenir.
* Kullanmayı tercih ederseniz de yükleyebilirsiniz **önerilen** ve **isteğe bağlı** bileşenleri.
* Her türlü iş yükü ile bağlı olmayan ek bileşenleri listeleyen bir bölüm de ekledik.

VSIX bildiriminizi bağımlılıkları oluşturduğunuzda, Bileşen kimlikleri yalnızca belirtmeniz gerekir. Tablolar, sunduğumuz en az Bileşen bağımlılıkları belirlemek için bu sayfada kullanın. Bazı senaryolarda, bir iş yükü yalnızca bir bileşenden belirttiğiniz gelebilir. Diğer senaryolarda, tek bir iş yükünü birden fazla bileşenlerini veya birden çok iş yükü birden çok bileşenlerini belirttiğiniz gelebilir. Daha fazla bilgi için bkz [nasıl yapılır: Visual Studio 2017'ye geçirme genişletilebilirlik projeleri](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) sayfası.

Bu kimliklerinin kullanma hakkında daha fazla bilgi için bkz. [Visual Studio 2017'yi yükleme komut satırı parametreleri kullanmak](use-command-line-parameters-to-install-visual-studio.md) sayfası. Ve iş yükü ve Bileşen kimlikleri diğer ürünlere yönelik bir listesi için bkz. [Visual Studio 2017 iş yükü ve Bileşen kimlikleri](workload-and-component-ids.md) sayfası.

## <a name="test-professional"></a>Test Uzmanı

**ID:** Microsoft.VisualStudio.Workload.TestProfessional

**Açıklama:** Test Professional, BT'yi uzmanı edicileri hedefleyen tümleşik test araçları, tüm test yaşam test ihtiyaçlarını sürücü sağlar.

### <a name="components-included-by-this-workload"></a>Bu iş yükü tarafından bulunan bileşenler

Bileşen kimliği | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Microsoft.VisualStudio.Component.TestTools.FeedbackClient | Microsoft Geri Bildirim İstemcisi | 15.6.27406.0 | Gerekli
Microsoft.VisualStudio.Component.TestTools.MicrosoftTestManager | Microsoft Test Manager | 15.6.27406.0 | Gerekli

## <a name="unaffiliated-components"></a>Kullanıcıyla bağlantılı olmayan bileşenleri

Bu, her türlü iş yükü ile dahil edilmez, ancak tek bir bileşeni olarak seçilebilir bileşenlerdir.

Bileşen kimliği | Name | Sürüm
--- | --- | ---
yok | yok | yok

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md)
* [Visual Studio Yönetici Kılavuzu](visual-studio-administrator-guide.md)
* [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
  * [Komut satırı parametresi örnekleri](command-line-parameter-examples.md)
* [Visual Studio’nun çevrimdışı yüklemesini oluşturma](create-an-offline-installation-of-visual-studio.md)
