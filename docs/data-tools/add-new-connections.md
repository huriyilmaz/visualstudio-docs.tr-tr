---
title: Yeni bağlantı ekleme
description: Veritabanına veya Visual Studio bir bağlantı ekleyin ve Sunucu Gezgini, Cloud Explorer veya SQL Server Nesne Gezgini kullanarak veritabanı içeriklerini ve şemalarını keşfedin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0348a3ba4db339e7472fc3ff72b09fe8cc23135e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631622"
---
# <a name="add-new-connections"></a>Yeni bağlantı ekleme

Veritabanı veya hizmetle bağlantınızı test etmek ve veritabanı içeriğini ve şemalarını keşfetmek için **Sunucu Gezgini,** **Cloud Explorer** veya **SQL Server Nesne Gezgini.** Bu pencerelerin işlevselliği bir ölçüde çakışıyor. Temel farklar:

- Sunucu Gezgini

   Varsayılan olarak Visual Studio. Bağlantıları test etmek ve SQL Server, ADO.NET sağlayıcının yüklü olduğu diğer veritabanlarını ve bazı Azure hizmetlerini görüntülemek için kullanılabilir. Ayrıca sistem performans sayaçları, olay günlükleri ve ileti kuyrukları gibi alt düzey nesneleri gösterir. Bir veri kaynağında ADO.NET sağlayıcısı yoksa burada gösterilebilir, ancak program aracılığıyla bağlanarak veri Visual Studio kullanabilirsiniz.

- Cloud Explorer

   Bu pencereyi Market'te Visual Studio uzantısı olarak [Visual Studio yükleyin.](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.CloudExplorerForVS) Azure hizmetlerini keşfetmek ve bu hizmetlere bağlanmak için özel işlevler sağlar.

- SQL Server Nesne Gezgini

   Görünüm menüsünde SQL Server Veri Araçları ve görünür olarak **yüklenir.** Orada görmüyorsanız, Denetim Masası'da Programlar  ve Özellikler'e gidin, Visual Studio'yi bulun ve  ardından Yenile onay kutusunu işaretledikten sonra yükleyiciyi yeniden çalıştırmak için Değiştir'i SQL Server Veri Araçları. SQL Server Nesne Gezgini  veritabanlarını görüntülemek SQL (ADO.NET sağlayıcısı varsa), yeni veritabanları oluşturma, şemaları değiştirme, saklı yordamlar oluşturma, bağlantı dizelerini alma, verileri görüntüleme ve daha fazlası için SQL Server Nesne Gezgini kullanın. SQL sağlayıcısı ADO.NET veritabanları burada gösterilebilir ancak yine de bu veritabanlarına program aracılığıyla bağlanabilirsiniz.

## <a name="add-a-connection-in-server-explorer"></a>Sunucu Gezgini'a bağlantı ekleme

Veritabanına bağlantı oluşturmak için, Sunucu Gezgini'daki Bağlantı Ekle simgesine tıklayın veya  Veri Bağlantıları  düğümünde Sunucu Gezgini'ye sağ tıklayın ve Bağlantı **Ekle'yi seçin.**  Buradan başka bir sunucu, SharePoint veya Azure hizmetine de bağlanabilirsiniz.

![Sunucu Gezgini Yeni Bağlantı simgesi](../data-tools/media/raddata-server-explorer-new-connection-icon.png)

Bu, Bağlantı Ekle **iletişim kutusunu** getirir. Burada LocalDB örneğinin SQL Server girildi.

![Yeni Bağlantı Ekle](../data-tools/media/raddata-add-new-connection-dialog.png)

## <a name="change-the-provider"></a>Sağlayıcıyı değiştirme

Veri kaynağı istediğiniz gibi yoksa Değiştir  düğmesine tıklayarak yeni bir veri kaynağı ve/veya yeni bir veri ADO.NET seçin. Yeni sağlayıcı, nasıl yapılandırdınıza bağlı olarak kimlik bilgilerinizi sorabilir.

![Değişiklik AD0.NET Veri Sağlayıcısı](../data-tools/media/raddata-change-ad0.net-data-provider.png)

## <a name="test-the-connection"></a>Bağlantıyı test etme

Veri kaynağını seçtikten sonra Bağlantıyı **Sına'ya tıklayın.** Başarılı olmazsa, satıcının belgelerine göre sorun gidermeniz gerekir.

![Bağlantıyı Sına](../data-tools/media/raddata-test-connection.png)

Test başarılı olursa, temel alınan veritabanı veya hizmeti temel alan bir veri modeli  anlamına Visual Studio terim olan bir veri kaynağı oluşturmak için hazırsınız demektir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
