---
title: Yeni bağlantı ekle | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 8a93c287-2834-4a83-a590-bdc3fe8d293f
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 44146613fb43b6fc4269741ba09b94629f888d5f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673081"
---
# <a name="add-new-connections"></a>Yeni bağlantı ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir veritabanı veya hizmetle bağlantınızı test edebilir ve **Sunucu Gezgini**, **bulut Gezgini**veya **SQL Server Nesne Gezgini**kullanarak veritabanı içeriğini ve şemalarını keşfedebilirsiniz. Bu pencerelerin işlevselliği bir ölçüde çakışıyor. Temel farklılıklar şunlardır:

 Sunucu Gezgini, Visual Studio 'da varsayılan olarak yüklenir. Bağlantıları test etmek ve SQL Server veritabanlarını, ADO.NET sağlayıcısı yüklü diğer veritabanlarını ve bazı Azure hizmetlerini görüntülemek için kullanılabilir. Ayrıca sistem performans sayaçları, olay günlükleri ve ileti kuyrukları gibi alt düzey nesneleri gösterir. Bir veri kaynağının ADO.NET sağlayıcısı yoksa, burada gösterilmez, ancak programlı olarak bağlanarak Visual Studio 'dan kullanmaya devam edebilirsiniz.

 Cloud Explorer, **Araçlar**  >  **Uzantılar ve güncelleştirmeler**  >  **çevrimiçi**  >  **Visual Studio Galerisi**' ni seçerek bu pencereyi Visual Studio uzantısı olarak el ile yükler. , Azure hizmetlerine yönelik keşfetmeye ve bağlamaya yönelik özel işlevler sağlar.

 SQL Server Veri Araçları ve **Görünüm** menüsü altında görünür SQL Server Nesne Gezgini. Burada görmüyorsanız, Denetim Masası 'ndaki **Programlar ve Özellikler** ' e gidin, Visual Studio ' yı bulun ve ardından SQL Server veri araçları onay kutusunu seçtikten sonra yükleyiciyi yeniden çalıştırmak için **Değiştir** ' i seçin. SQL veritabanlarını görüntülemek için **SQL Server Nesne Gezgini** kullanın (bir ADO.NET sağlayıcısı varsa), yeni veritabanları oluşturun, şemaları değiştirin, saklı yordamlar oluşturun, bağlantı dizelerini alın, verileri görüntüleyin ve daha fazlasını yapın. ADO.NET sağlayıcısı yüklü olmayan SQL veritabanları burada gösterilmez, ancak yine de bunlara programlı olarak bağlanabilirsiniz.

## <a name="add-a-connection-in-server-explorer"></a>Sunucu Gezgini bağlantı ekleme
 Veritabanına bir bağlantı oluşturmak için **Sunucu Gezgini** **bağlantı ekle** simgesine tıklayın veya **veri bağlantıları** düğümünde **Sunucu Gezgini** ' a sağ tıklayıp **bağlantı ekle**' yi seçin. Buradan, başka bir sunucuda, SharePoint hizmetinde veya bir Azure hizmetinde bir veritabanına da bağlanabilirsiniz.

 ![Sunucu Gezgini yeni bağlantı simgesi](../data-tools/media/raddata-server-explorer-new-connection-icon.png "radveri Sunucu Gezgini yeni bağlantı simgesi")

 Bu, **bağlantı ekle** iletişim kutusunu açar. Burada SQL Server LocalDB örneğinin adını girdik.

 ![Yeni bağlantı ekle](../data-tools/media/raddata-add-new-connection-dialog.png "radveri ekleme yeni bağlantı Iletişim kutusu")

## <a name="change-the-provider"></a>Sağlayıcıyı değiştirme
 Veri kaynağı istediğiniz gibi değilse, yeni bir veri kaynağı ve/veya yeni bir ADO.NET veri sağlayıcısı seçmek için **Değiştir** düğmesine tıklayın. Yeni sağlayıcı, nasıl yapılandırdığınıza bağlı olarak kimlik bilgilerinizi isteyebilir.

 ![AD0.NET Veri Sağlayıcısı Değiştir](../data-tools/media/raddata-change-ad0-net-data-provider.png "radveri değişikliği AD0.NET Veri Sağlayıcısı")

## <a name="test-the-connection"></a>Bağlantıyı test etme
 Veri kaynağını seçtikten sonra **Bağlantıyı Sına**' ya tıklayın. Başarılı olmazsa, satıcının belgelerine göre sorun gidermeniz gerekecektir.

 ![Bağlantıyı Sına](../data-tools/media/raddata-test-connection.png "radveri sınama bağlantısı")

 Test başarılı olursa, aslında temel veritabanını veya hizmeti temel alan bir *veri modeli* anlamına gelen bir Visual Studio terimi olan bir *veri kaynağı*oluşturmaya hazırsınızdır.

## <a name="see-also"></a>Ayrıca Bkz.
 [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
