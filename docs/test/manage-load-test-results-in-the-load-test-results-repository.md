---
title: Yük Dengelemeyi Test Sonuçları
description: Load Test Sonuçları Repository SQL veritabanında depolanan yük testi sırasında toplanan verileri yönetmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, results repository
- results, load test
- load test results, repository
- Load Test Results Repository
ms.assetid: 1cd63c4b-4f74-4133-b675-5e8fbeab25f3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 407e265424863d7018fc6b3e12fc23bddd0a9812
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122139913"
---
# <a name="manage-load-test-results-in-the-load-test-results-repository"></a>Load Test Sonuçları Repository'de yük testi sonuçlarını yönetme

Yük testlerinizi çalıştırarak bir yük testi çalıştırması sırasında toplanan tüm bilgiler, bir yük testi Test Sonuçları deposu olan Load SQL depolanmış olabilir. Load Test Sonuçları Deposu performans sayacı verilerini ve kaydedilen hatalar hakkında tüm bilgileri içerir. Sonuçlar Deposu veritabanı, denetleyiciler için kurulum tarafından veya bir yük testinin ilk yerel çalıştırması üzerinde otomatik olarak oluşturulur. Yerel çalıştırma için, yük testi şeması yoksa veritabanı otomatik olarak oluşturulur.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Denetleyicinin sonuç deposu bağlantı dizesini farklı bir sunucu kullanmak üzere değiştirirsanız, şemayı oluşturmak için yeni sunucuda *loadtestresultsrepository.sql* betiği çalıştır olmalıdır.

Visual Studio Enterprise, bir teknolojiye dayalı olarak ortak performans sayaçlarını toplayan adlandırılmış sayaç kümeleri sağlar. Bu kümeler bir IIS sunucusu, bir ASP.NET sunucusu veya SQL yararlıdır. Sayaç kümeleriyle toplanan tüm veriler Load Test Sonuçları Depoda depolanır.

> [!IMPORTANT]
> Sayaç kümesi ile performans sayacı verileri arasında bir fark vardır. Sayaç kümesi meta verilerdir. IIS veya sanal ağ gibi belirli bir rolü gerçekleştiren bir bilgisayardan toplanacak performans sayaçları grubunu SQL Server. Sayaç kümesi, yük testi tanımının bir parçası. Performans sayacı verileri sayaç kümelerine, sayaç kümesi eşlemesi belirli bir bilgisayara ve örnek hızına göre toplanır.

## <a name="sql-server-versions"></a>SQL Server sürümleri

Yük testlerini kullanmak için, SQL Server Express ile birlikte yüklenmiş olan LocalDB'yi Visual Studio. Bu, yük testleri için varsayılan veritabanı sunucusudur (Microsoft Excel dahil). SQL Server Express LocalDB, program geliştiricilerine SQL Server Express bir yürütme modudur. SQL Server Express LocalDB yüklemesi, veritabanı altyapısını başlatmak için gereken en SQL Server bir dosya kümesi kopyalar.

Takımınız yoğun veritabanı ihtiyacı bekliyorsa veya projeleriniz LocalDB'de SQL Server Express büyükse, daha fazla ölçeklendirme potansiyeli sağlamak için SQL Express'e veya tam veritabanına SQL Server yükseltmeyi göz önünde bulundurabilirsiniz. Yükseltme işlemini SQL Server LocalDB için MDF ve LDF SQL Server Express kullanıcı profili klasöründe depolanır. Bu dosyalar, yük testi veritabanını SQL Server Express veya SQL Server.

## <a name="load-test-results-store-considerations"></a>Yük testi sonuçları deposuyla ilgili dikkat edilmesi gerekenler

Yükleme Visual Studio Enterprise, yük testi sonuçları deposu bilgisayarda yüklü olan SQL Express örneğini kullanmak üzere ayarlanır. SQL Express, en fazla 4 GB disk alanı kullanmakla sınırlıdır. Uzun bir süre boyunca çok sayıda yük testi çalıştıracaksanız, varsa yük testi sonuçları depolarını tam yük SQL Server örneğini kullanmak üzere yapılandırmayı göz önünde bulundurabilirsiniz.

## <a name="load-test-analyzer-tasks"></a>Yük Testi Çözümleyicisi görevleri

|Görevler|İlişkili konular|
|-|-----------------------|
|**Yük testi sonuçları deposu ayarlayın:** Bir veritabanı üzerinde yük testi sonuçları deposu SQL. **Not:**  Bir yük testi deposu, bir test denetleyicisini yükleyemedikten sonra da oluşturulabilir. Daha fazla bilgi için [bkz. Test aracılarını yükleme ve yapılandırma.](../test/lab-management/install-configure-test-agents.md)||
|**Sonuç deposunu seçme ve görüntüleme:** Belirli bir sonuç deposunu seçebilirsiniz. Yerel sonuçlar deposuyla sınırlı değildir. Yük testleri genellikle uzak bir Aracı bilgisayar kümesi üzerinde çalışır. Aracılar veya yerel bilgisayarınızdan alınan test sonuçları, yük testi SQL oluşturduğunuz herhangi bir sunucuya kaydedilebilir. Her iki durumda da, Test Denetleyicilerini Yönet penceresini kullanarak yük testi sonuçlarınızı **nerede depolayabilirsiniz?**|-   [Nasıl: Yük testi sonuçları deposu seçme](../test/how-to-select-a-load-test-results-repository.md)<br />-   [Nasıllı: Analiz için yük testi sonuçlarına erişme](../test/how-to-access-load-test-results-for-analysis.md)|
|**Depodan bir yük testi sonucu silindi:** Yük testini aç ve yönet iletişim kutusunu **Yük Testi Düzenleyicisi** yük testi **sonuçlarını Test Sonuçları** kaldırabilirsiniz.|-   [Nasıl olur: Bir depodan yük testi sonuçlarını silme](../test/how-to-delete-load-test-results-from-a-repository.md)|
|**Sonuçları depoya içeri ve dışarı aktarma:** Yük testi sonuçlarını dosyadan içeri ve dışarı **Yük Testi Düzenleyicisi.**|-   [Nasıl olur: Yük testi sonuçlarını depoya aktarma](../test/how-to-import-load-test-results-into-a-repository.md)<br />-   [Nasıl olur: Bir depodan yük testi sonuçlarını dışarı aktarma](../test/how-to-export-load-test-results-from-a-repository.md)|

## <a name="related-tasks"></a>İlişkili görevler

[Yük testi sonuçlarını analiz etme](../test/analyze-load-test-results-using-the-load-test-analyzer.md)

Yük Testi Çözümleyicisi'nin kullanarak hem çalışan bir yük testinin hem de tamamlanmış bir yük **testinin sonuçlarını görüntüabilirsiniz.**

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi sonuçlarını analiz etme](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Nasıllı: Analiz için yük testi sonuçlarına erişme](../test/how-to-access-load-test-results-for-analysis.md)
