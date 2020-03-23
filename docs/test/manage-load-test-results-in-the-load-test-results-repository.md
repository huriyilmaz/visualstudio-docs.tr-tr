---
title: Yük Testi Sonuçlarını Yönetme
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, results repository
- results, load test
- load test results, repository
- Load Test Results Repository
ms.assetid: 1cd63c4b-4f74-4133-b675-5e8fbeab25f3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bd0562a6cceeb50d43222a7850de11d52b0587cf
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75584432"
---
# <a name="manage-load-test-results-in-the-load-test-results-repository"></a>Yük Testi Sonuçları Deposu'nda yük testi sonuçlarını yönetme

Yük testlerinizi çalıştırdığınızda, bir yük testi çalışması sırasında toplanan tüm bilgiler, SQL veritabanı olan *Yük Testi Sonuçları Deposu'nda*depolanabilir. Yük Testi Sonuçları Deposu, performans sayacı verilerini ve kaydedilen hatalar la ilgili tüm bilgileri içerir. Sonuç Deposu veritabanı denetleyicileri için kurulum tarafından oluşturulur veya bir yük testinin ilk yerel çalışmasında otomatik olarak oluşturulur. Yerel bir çalıştırma için, yük testi şeması yoksa veritabanı otomatik olarak oluşturulur.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Denetleyicinin sonuç deposu bağlantı dizesini farklı bir sunucu kullanmak üzere değiştirirseniz, şemayı oluşturmak için yeni sunucunun *loadtestresultsrepository.sql* komut dosyası çalıştırılmaya sahip olması gerekir.

Visual Studio Enterprise, bir teknolojiye dayalı olarak ortak performans sayaçları toplayan adlandırılmış sayaç kümeleri sağlar. Bu kümeler, bir IIS sunucusu, bir ASP.NET sunucusu veya bir SQL sunucusu çözümlenirken yararlıdır. Sayaç kümeleri ile toplanan tüm veriler Yük Testi Sonuçları Deposu'nda depolanır.

> [!IMPORTANT]
> Sayaç kümesi ile performans sayacı verileri arasında fark vardır. Sayaç kümesi meta veridir. IIS veya SQL Server gibi belirli bir rolü gerçekleştiren bir bilgisayardan toplanması gereken bir performans sayacı grubunu tanımlar. Sayaç kümesi yük testi tanımının bir parçasıdır. Performans sayacı verileri sayaç kümelerine, sayaç kümesinin belirli bir bilgisayara eşleneme sine ve örnek oranına göre toplanır.

## <a name="sql-server-versions"></a>SQL Server sürümleri

Yük testlerini kullanmak için Visual Studio yüklü OLAN SQL Server Express LocalDB'yi kullanabilirsiniz. Yük testleri için varsayılan veritabanı sunucusudur (Microsoft Excel tümleştirmesi dahil). SQL Server Express LocalDB, SQL Server Express'in program geliştiricileri hedefleyen bir yürütme modudur. SQL Server Express LocalDB yüklemesi, SQL Server Database Engine'i başlatmak için gereken en az dosya kümesini kopyalar.

Ekibiniz ağır veritabanı gereksinimleri bekliyorsa veya projeleriniz SQL Server Express LocalDB'den daha fazla büyüyecekse, daha fazla ölçeklendirme potansiyeli sağlamak için SQL Express veya tam SQL Server'a yükseltmeyi düşünmelisiniz. SQL Server'ı yükseltirseniz, SQL Server Express LocalDB'nin MDF ve LDF dosyaları kullanıcı profil klasöründe depolanır. Bu dosyalar, yükleme testi veritabanını SQL Server Express veya SQL Server'a almak için kullanılabilir.

## <a name="load-test-results-store-considerations"></a>Yük testi sonuçları depoda dikkat edilmesi gerekenler

Visual Studio Enterprise yüklendiğinde, yükleme testi sonuçları deposu bilgisayarda yüklü olan SQL Express'in bir örneğini kullanmak üzere ayarlanır. SQL Express, en fazla 4 GB disk alanı kullanmakla sınırlıdır. Uzun bir süre boyunca çok sayıda yükleme testi çalıştıracaksanız, varsa tam SQL Server ürününün bir örneğini kullanacak şekilde yük testi sonuçları deposunu yapılandırmayı düşünmelisiniz.

## <a name="load-test-analyzer-tasks"></a>Yük Testi Çözümleyicisi görevleri

|Görevler|İlişkili konular|
|-|-----------------------|
|**Yük testi sonuçları deposunu ayarlayın:** Bir SQL veritabanında bir yük testi sonuçları deposu ayarlayabilirsiniz. **Not:**  Bir test denetleyicisi yüklediğinizde bir yük testi deposu da oluşturulabilir. Daha fazla bilgi için [bkz.](../test/lab-management/install-configure-test-agents.md)||
|**Sonuç deposunun seçilmesi ve görüntülenmesi:** Belirli bir sonuç deposu seçebilirsiniz. Yerel bir sonuç deposuyla sınırlı değildir. Sık sık, yükleme testleri Aracılı bilgisayarların uzak bir kümesi nde çalıştırılır. Aracılarınızın veya yerel bilgisayarınızın test sonuçları, bir yük testi sonuçları deposu oluşturduğunuz herhangi bir SQL sunucusuna kaydedilebilir. Her iki durumda da, **Test Denetleyicilerini Yönet** penceresini kullanarak yük testi sonuçlarınızı nerede depolayacağınızı belirlemeniz gerekir.|-   [Nasıl seçilir: Yük testi sonuçları deposunu seçin](../test/how-to-select-a-load-test-results-repository.md)<br />-   [Nasıl yapılı: Analiz için yük testi sonuçlarına erişin](../test/how-to-access-load-test-results-for-analysis.md)|
|**Depodan yük testi sonucu silme:** Yük Testi **Sonuçlarını Aç ve Yönet** iletişim kutusunu kullanarak Yük Testi Düzenleyicisi'nden bir yük testi sonucunu kaldırabilirsiniz. **Load Test Editor**|-   [Nasıl yapılı: Yük testi sonuçlarını bir depodan silme](../test/how-to-delete-load-test-results-from-a-repository.md)|
|**İthalat ve dışa aktarma sonuçları bir depoya aktarın:** Yük Testi Düzenleyicisi'nden **Load Test Editor**yük testi sonuçlarını içe aktarıp aktarabilirsiniz.|-   [Nasıl yapilir: Yük testi sonuçlarını depoya alma](../test/how-to-import-load-test-results-into-a-repository.md)<br />-   [Nasıl yapilir: Yük testi sonuçlarını bir depodan dışa aktarma](../test/how-to-export-load-test-results-from-a-repository.md)|

## <a name="related-tasks"></a>İlişkili görevler

[Yük testi sonuçlarını analiz edin](../test/analyze-load-test-results-using-the-load-test-analyzer.md)

**Yük Testi Çözümleyicisini**kullanarak hem çalışan yük testinin hem de tamamlanmış bir yük testinin sonuçlarını görüntüleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi sonuçlarını analiz edin](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Nasıl yapılı: Analiz için yük testi sonuçlarına erişin](../test/how-to-access-load-test-results-for-analysis.md)
