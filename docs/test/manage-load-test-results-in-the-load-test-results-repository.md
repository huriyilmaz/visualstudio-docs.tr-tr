---
title: Yük Test Sonuçları Yönet
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
manager: jillfra
ms.openlocfilehash: 9945551469541cdcffe520844da600d758dc43b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85286771"
---
# <a name="manage-load-test-results-in-the-load-test-results-repository"></a>Yük Test Sonuçları deposundaki yük testi sonuçlarını yönetme

Yük testlerinizi çalıştırdığınızda, yük testi çalıştırması sırasında toplanan herhangi bir bilgi, SQL veritabanı olan *load test sonuçları deposunda*depolanabilir. Load Test Sonuçları Deposu, performans sayacı verilerini ve kayıtlı hatalar hakkındaki tüm bilgileri içerir. Sonuçlar deposu veritabanı, denetleyiciler için kurulum tarafından oluşturulur veya bir yük testinin ilk yerel çalıştırmasında otomatik olarak oluşturulur. Yerel çalıştırma için, yük testi şeması yoksa veritabanı otomatik olarak oluşturulur.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Denetleyicinin sonuç deposu bağlantı dizesini farklı bir sunucu kullanacak şekilde değiştirirseniz, yeni sunucunun şemayı oluşturmak için *loadtestresultsrepository. SQL* komut dosyası çalıştırması gerekir.

Visual Studio Enterprise, bir teknolojiyi temel alan ortak performans sayaçlarını toplayacak adlandırılmış sayaç kümeleri sağlar. Bu kümeler, bir IIS sunucusunu, bir ASP.NET sunucusunu veya bir SQL sunucusunu çözümlemede yararlıdır. Sayaç kümeleriyle toplanan tüm veriler Load Test Sonuçları deposunda depolanır.

> [!IMPORTANT]
> Sayaç kümesi ve performans sayacı verileri arasında bir farklılık vardır. Bir sayaç kümesi meta verilerdir. IIS veya SQL Server gibi belirli bir rol gerçekleştiren bir bilgisayardan toplanması gereken bir dizi performans sayacını tanımlar. Sayaç kümesi yük testi tanımının bir parçasıdır. Performans sayacı verileri sayaç kümelerine, sayaç kümesinin belirli bir bilgisayara eşlenmesinin ve örnek hızının temel alınarak toplanır.

## <a name="sql-server-versions"></a>SQL Server sürümleri

Yük testlerini kullanmak için, Visual Studio ile birlikte yüklenen SQL Server Express LocalDB kullanabilirsiniz. Yükleme testleri için varsayılan veritabanı sunucusudur (Microsoft Excel tümleştirmesi dahil). SQL Server Express LocalDB, program geliştiricilerine hedeflenen SQL Server Express yürütme modudur. SQL Server Express LocalDB yüklemesi, SQL Server veritabanı altyapısını başlatmak için gereken en az bir dosya kümesini kopyalar.

Takımınız ağır veritabanı ihtiyaçlarına ihtiyaç duyuyor veya projeleriniz SQL Server Express LocalDB 'ye yükseldiğinde, daha fazla ölçeklendirme olasılığı sağlamak için SQL Express 'e veya tam SQL Server yükseltmeniz gerekir. SQL Server yükseltirseniz, SQL Server Express LocalDB için MDF ve LDF dosyaları Kullanıcı profili klasöründe depolanır. Bu dosyalar, SQL Server Express veya SQL Server yük testi veritabanını içeri aktarmak için kullanılabilir.

## <a name="load-test-results-store-considerations"></a>Yük testi sonuçları deposu konuları

Visual Studio Enterprise yüklendiğinde, yük testi sonuçları deposu, bilgisayarda yüklü olan bir SQL Express örneğini kullanmak üzere ayarlanır. SQL Express, en fazla 4 GB disk alanı kullanımıyla sınırlıdır. Uzun bir süre boyunca çok sayıda yük testi çalıştıracağınızı düşünüyorsanız, yük testi sonuçları deposunu, varsa tam SQL Server ürünün bir örneğini kullanacak şekilde yapılandırmayı düşünmelisiniz.

## <a name="load-test-analyzer-tasks"></a>Yük Testi Çözümleyicisi görevleri

|Görevler|İlişkili konular|
|-|-----------------------|
|**Yük testi sonuçları deposu ayarlama:** Bir SQL veritabanında yük testi sonuçları deposu ayarlayabilirsiniz. **Note:**  Bir test denetleyicisi yüklediğinizde, yük testi deposu da oluşturulabilir. Daha fazla bilgi için bkz. [test aracılarını yükleyip yapılandırma](../test/lab-management/install-configure-test-agents.md).||
|**Bir sonuç deposunu seçme ve görüntüleme:** Belirli bir sonuç deposu seçebilirsiniz. Yerel bir sonuç deposuyla sınırlı değilsiniz. Genellikle, yük testleri, uzak bir aracı bilgisayarları kümesi üzerinde çalıştırılır. Aracılarınızdan veya yerel bilgisayarınızda test sonuçları, yük testi sonuçları deposu oluşturduğunuz herhangi bir SQL Server 'a kaydedilebilir. Her iki durumda da, **Test Denetleyicilerini Yönet** penceresini kullanarak yük testi sonuçlarınızı nerede depolayabileceğiniz belirlemeniz gerekir.|-   [Nasıl yapılır: yük testi sonuçları deposu seçme](../test/how-to-select-a-load-test-results-repository.md)<br />-   [Nasıl yapılır: analiz için yük testi sonuçlarına erişme](../test/how-to-access-load-test-results-for-analysis.md)|
|**Depodan bir yük testi sonucunu silme:** **Yük Testi Düzenleyicisi** yük testi sonucunu, **Load Test sonuçları aç ve Yönet** iletişim kutusunu kullanarak kaldırabilirsiniz.|-   [Nasıl yapılır: bir depodan yük testi sonuçlarını silme](../test/how-to-delete-load-test-results-from-a-repository.md)|
|**Sonuçları bir depoya içeri ve dışarı aktarma:** Yük testi sonuçlarını **Yük Testi Düzenleyicisi**içeri ve dışarı aktarabilirsiniz.|-   [Nasıl yapılır: yük testi sonuçlarını depoya aktarma](../test/how-to-import-load-test-results-into-a-repository.md)<br />-   [Nasıl yapılır: bir depodan yük testi sonuçlarını dışarı aktarma](../test/how-to-export-load-test-results-from-a-repository.md)|

## <a name="related-tasks"></a>İlişkili görevler

[Yük testi sonuçlarını çözümle](../test/analyze-load-test-results-using-the-load-test-analyzer.md)

**Yük Testi Çözümleyicisi**'ni kullanarak, çalışan bir yük testinin ve tamamlanan bir yük testinin sonuçlarını görüntüleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi sonuçlarını çözümle](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Nasıl yapılır: analiz için yük testi sonuçlarına erişme](../test/how-to-access-load-test-results-for-analysis.md)
