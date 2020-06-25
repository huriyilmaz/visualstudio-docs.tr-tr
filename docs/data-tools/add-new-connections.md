---
title: Yeni bağlantı ekleme
ms.date: 11/04/2016
ms.topic: how-to
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5f6f34c28a6bbba236a4d90e2f936fad0b2a3f60
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283066"
---
# <a name="add-new-connections"></a>Yeni bağlantı ekleme

Bir veritabanı veya hizmetle bağlantınızı test edebilir ve **Sunucu Gezgini**, **bulut Gezgini**veya **SQL Server Nesne Gezgini**kullanarak veritabanı içeriğini ve şemalarını keşfedebilirsiniz. Bu pencerelerin işlevselliği bir ölçüde çakışıyor. Temel farklılıklar şunlardır:

- Sunucu Gezgini

   Visual Studio 'da varsayılan olarak yüklenir. Bağlantıları test etmek ve SQL Server veritabanlarını, ADO.NET sağlayıcısı yüklü diğer veritabanlarını ve bazı Azure hizmetlerini görüntülemek için kullanılabilir. Ayrıca sistem performans sayaçları, olay günlükleri ve ileti kuyrukları gibi alt düzey nesneleri gösterir. Bir veri kaynağının ADO.NET sağlayıcısı yoksa, burada gösterilmez, ancak programlı olarak bağlanarak Visual Studio 'dan kullanmaya devam edebilirsiniz.

- Cloud Explorer

   Bu pencereyi [Visual Studio Market](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.CloudExplorerForVS)Visual Studio uzantısı olarak el ile yükleyebilirsiniz. , Azure hizmetlerine yönelik keşfetmeye ve bağlamaya yönelik özel işlevler sağlar.

- SQL Server Nesne Gezgini

   SQL Server Veri Araçları ile yüklendi ve **Görünüm** menüsü altında görünür. Burada görmüyorsanız, Denetim Masası 'ndaki **Programlar ve Özellikler** ' e gidin, Visual Studio ' yı bulun ve ardından SQL Server veri araçları onay kutusunu seçtikten sonra yükleyiciyi yeniden çalıştırmak için **Değiştir** ' i seçin. SQL veritabanlarını görüntülemek için **SQL Server Nesne Gezgini** kullanın (bir ADO.NET sağlayıcısı varsa), yeni veritabanları oluşturun, şemaları değiştirin, saklı yordamlar oluşturun, bağlantı dizelerini alın, verileri görüntüleyin ve daha fazlasını yapın. ADO.NET sağlayıcısı yüklü olmayan SQL veritabanları burada gösterilmez, ancak yine de bunlara programlı olarak bağlanabilirsiniz.

## <a name="add-a-connection-in-server-explorer"></a>Sunucu Gezgini bağlantı ekleme

Veritabanına bir bağlantı oluşturmak için **Sunucu Gezgini** **bağlantı ekle** simgesine tıklayın veya **veri bağlantıları** düğümünde **Sunucu Gezgini** ' a sağ tıklayıp **bağlantı ekle**' yi seçin. Buradan, başka bir sunucuda, SharePoint hizmetinde veya bir Azure hizmetinde bir veritabanına da bağlanabilirsiniz.

![Sunucu Gezgini yeni bağlantı simgesi](../data-tools/media/raddata-server-explorer-new-connection-icon.png)

Bu, **bağlantı ekle** iletişim kutusunu açar. Burada SQL Server LocalDB örneğinin adını girdik.

![Yeni bağlantı ekle](../data-tools/media/raddata-add-new-connection-dialog.png)

## <a name="change-the-provider"></a>Sağlayıcıyı değiştirme

Veri kaynağı istediğiniz gibi değilse, yeni bir veri kaynağı ve/veya yeni bir ADO.NET veri sağlayıcısı seçmek için **Değiştir** düğmesine tıklayın. Yeni sağlayıcı, nasıl yapılandırdığınıza bağlı olarak kimlik bilgilerinizi isteyebilir.

![AD0.NET Veri Sağlayıcısı Değiştir](../data-tools/media/raddata-change-ad0.net-data-provider.png)

## <a name="test-the-connection"></a>Bağlantıyı sınama

Veri kaynağını seçtikten sonra **Bağlantıyı Sına**' ya tıklayın. Başarılı olmazsa, satıcının belgelerine göre sorun gidermeniz gerekecektir.

![Bağlantıyı Sına](../data-tools/media/raddata-test-connection.png)

Test başarılı olursa, aslında temel veritabanını veya hizmeti temel alan bir *veri modeli* anlamına gelen bir Visual Studio terimi olan bir *veri kaynağı*oluşturmaya hazırsınızdır.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
