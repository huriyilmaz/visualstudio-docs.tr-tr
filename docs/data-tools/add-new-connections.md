---
title: Yeni bağlantı ekleme
description: Veritabanına veya Visual Studio bağlantı ekleyin ve Sunucu Gezgini, Cloud Explorer veya SQL Server Nesne Gezgini kullanarak veritabanı içeriklerini ve şemalarını keşfedin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6a5e6ea72056fcb7e4a7b4ca15750aa57dea7bf1
ms.sourcegitcommit: 3cfe24a74b611440b831d9591e067874c51a3bfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2021
ms.locfileid: "130087494"
---
# <a name="add-new-connections"></a>Yeni bağlantı ekleme

Veritabanı veya hizmetle bağlantınızı test etmek ve veritabanı içeriğini ve şemalarını keşfetmek için **Sunucu Gezgini,** **Cloud Explorer** veya **SQL Server Nesne Gezgini.** Bu pencerelerin işlevselliği bir ölçüde çakışıyor. Temel farklar:

- Sunucu Gezgini

   Varsayılan olarak Visual Studio. Bağlantıları test etmek ve SQL Server, bir ADO.NET sağlayıcısının yüklü olduğu diğer veritabanlarını ve bazı Azure hizmetlerini görüntülemek için kullanılabilir. Ayrıca sistem performans sayaçları, olay günlükleri ve ileti kuyrukları gibi alt düzey nesneleri gösterir. Bir veri kaynağında ADO.NET sağlayıcı yoksa burada gösterilebilir, ancak yine de program aracılığıyla bağlanarak Visual Studio kaynağından kullanabilirsiniz.

- Cloud Explorer

   Bu pencereyi Market'te Visual Studio uzantısı olarak [el Visual Studio yükleyin.](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.CloudExplorerForVS) Azure hizmetlerini keşfetmek ve bu hizmetlere bağlanmak için özel işlevler sağlar.

- SQL Server Nesne Gezgini

   Görünüm menüsünde SQL Server Veri Araçları ve görünür **olarak** yüklenir. Orada görmüyorsanız, Denetim Masası'de Programlar  ve Özellikler'e gidin, Visual Studio'ı bulun ve  ardından Yenile onay kutusunu işaretledikten sonra yükleyiciyi yeniden çalıştırmak için Değiştir'i SQL Server Veri Araçları. SQL Server Nesne Gezgini  veritabanlarını görüntülemek SQL (bir ADO.NET sağlayıcısı varsa), yeni veritabanları oluşturma, şemaları değiştirme, saklı yordamlar oluşturma, bağlantı dizelerini alma, verileri görüntüleme ve daha fazlası için SQL Server Nesne Gezgini kullanın. SQL sağlayıcının ADO.NET veritabanı burada gösterilebilir ancak yine de bu veritabanlarına program aracılığıyla bağlanabilirsiniz.

## <a name="add-a-connection-in-server-explorer"></a>Sunucu Gezgini'a bağlantı ekleme

Veritabanına bağlantı oluşturmak için, Sunucu Gezgini'daki Bağlantı Ekle simgesine tıklayın veya  Veri Bağlantıları düğümünde Sunucu Gezgini'ye sağ tıklayın ve Bağlantı   **Ekle'yi seçin.** Buradan başka bir sunucu, hizmet veya Azure SharePoint veritabanına da bağlanabilirsiniz.

![Sunucu Gezgini Bağlantı simgesi](../data-tools/media/raddata-server-explorer-new-connection-icon.png)

Bu, Bağlantı Ekle **iletişim kutusunu** getirir. Burada LocalDB örneğinin SQL Server girildi.

![Yeni Bağlantı Ekle](../data-tools/media/raddata-add-new-connection-dialog.png)

## <a name="change-the-provider"></a>Sağlayıcıyı değiştirme

Veri kaynağı istediğiniz gibi yoksa Değiştir  düğmesine tıklayarak yeni bir veri kaynağı ve/veya yeni bir veri ADO.NET sağlayıcısı seçin. Yeni sağlayıcı, nasıl yapılandırdınıza bağlı olarak kimlik bilgilerinizi sorabilir.

::: moniker range=">=vs-2022"
> [!NOTE]
> OLEDB veya ODBC veri sağlayıcılarına bağlanmak için Visual Studio 2022 kullanıyorsanız, Visual Studio 2022'nin artık 64 bitlik bir işlem olduğunu fark etmek gerekir.
>
> Başka bir ifadeyle, Visual Studio veri araçlarından bazıları 32 bit veri sağlayıcılarını kullanarak OLEDB veya ODBC veritabanlarına bağlanamayacak. Buna Microsoft Access 32 bit OLEDB veri sağlayıcısının yanı sıra diğer üçüncü taraf 32 bit sağlayıcılar dahildir.
>
>OLEDB veya ODBC'ye bağlı 32 bit uygulamaları sürdürmeye devam ediyorsanız, uygulamayı 2022'de Visual Studio çalıştırabilirsiniz. Ancak, Sunucu Gezgini, Veri Kaynağı Sihirbazı veya Veri Kümesi Tasarımcısı gibi Visual Studio Veri Araçları'nın herhangi birini kullanıyorsanız, Visual Studio'nin hala 32 bitlik bir işlem olan önceki bir sürümünü kullansanız gerekir. 32 bitlik Visual Studio olan son sürüm, 2019'Visual Studio sürümüdür.
>
>Projeyi 64 bitlik bir işlem olacak şekilde dönüştürmeyi planlıyorsanız OLEDB ve ODBC veri bağlantılarını 64 bit veri sağlayıcılarını kullanmak üzere güncelleştirmeniz gerekir.
>
>Uygulamanız Microsoft Access veritabanları kullanıyorsa ve projeyi 64 bit'e dönüştürebiliyorsa, Access Bağlantı Altyapısı (ACE) olarak da adlandırılan 64 bit Microsoft Access Veritabanı Altyapısı'nın kullanılması önerilir. Daha fazla [OLE DB için lütfen Jet ve ODBC için sağlayıcının 32 bit sürümlerine sahip](/office/troubleshoot/access/jet-odbc-driver-available-32-bit-version) olduğunu lütfen unutmayın.
>
>Üçüncü taraf bir veri sağlayıcısı kullanıyorsanız, projeyi 64 bit'e dönüştürmeden önce satıcınıza bağlanarak 64 bit sağlayıcı sun olup olduklarını görmenizi öneririz.

::: moniker-end

![Değişiklik AD0.NET Veri Sağlayıcısı](../data-tools/media/raddata-change-ad0.net-data-provider.png)

## <a name="test-the-connection"></a>Bağlantıyı test etme

Veri kaynağını seçtikten sonra Bağlantıyı **Sına'ya tıklayın.** Başarılı olmazsa, satıcının belgelerine göre sorun gidermeniz gerekir.

![Bağlantıyı Sına](../data-tools/media/raddata-test-connection.png)

Test başarılı olursa, temel alınan veritabanı veya hizmeti temel alan bir veri modeli  anlamına Visual Studio bir veri kaynağı ( ) oluşturmak için hazırsınız demektir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
