---
title: Yük Test Sonuçları Yönet
description: load Test Sonuçları Repository SQL veritabanında depolanan bir yük testi sırasında toplanan verileri yönetmeyi öğrenin.
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
ms.openlocfilehash: 7d5bf3decd66b285bbc50d5bee21b5f46fe380f77cac72b7a36273ce39378c59
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121352675"
---
# <a name="manage-load-test-results-in-the-load-test-results-repository"></a>Yük Test Sonuçları deposundaki yük testi sonuçlarını yönetme

yük testlerinizi çalıştırdığınızda, yük testi çalıştırması sırasında toplanan herhangi bir bilgi, SQL veritabanı olan *load Test Sonuçları deposunda* depolanabilir. Load Test Sonuçları Deposu, performans sayacı verilerini ve kayıtlı hatalar hakkındaki tüm bilgileri içerir. Sonuçlar deposu veritabanı, denetleyiciler için kurulum tarafından oluşturulur veya bir yük testinin ilk yerel çalıştırmasında otomatik olarak oluşturulur. Yerel çalıştırma için, yük testi şeması yoksa veritabanı otomatik olarak oluşturulur.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Denetleyicinin sonuç deposu bağlantı dizesini farklı bir sunucu kullanacak şekilde değiştirirseniz, yeni sunucunun şemayı oluşturmak için *loadtestresultsrepository. SQL* komut dosyası çalıştırması gerekir.

Visual Studio Enterprise, bir teknolojiyi temel alan ortak performans sayaçlarını toplayacak adlandırılmış sayaç kümeleri sağlar. bu kümeler bir ııs sunucusunu, ASP.NET sunucusunu veya bir SQL sunucusunu analiz ettiğinizde faydalıdır. Sayaç kümeleriyle toplanan tüm veriler Load Test Sonuçları deposunda depolanır.

> [!IMPORTANT]
> Sayaç kümesi ve performans sayacı verileri arasında bir farklılık vardır. Bir sayaç kümesi meta verilerdir. IIS veya SQL Server gibi belirli bir rol gerçekleştiren bir bilgisayardan toplanması gereken bir dizi performans sayacını tanımlar. Sayaç kümesi yük testi tanımının bir parçasıdır. Performans sayacı verileri sayaç kümelerine, sayaç kümesinin belirli bir bilgisayara eşlenmesinin ve örnek hızının temel alınarak toplanır.

## <a name="sql-server-versions"></a>SQL Server sürümleri

yük testlerini kullanmak için, Visual Studio yüklenmiş SQL Server Express localdb kullanabilirsiniz. yükleme testleri için varsayılan veritabanı sunucusudur (Microsoft Excel tümleştirme dahil). SQL Server Express localdb, program geliştiricilerine hedeflenmiş SQL Server Express yürütme modudur. SQL Server Express localdb yüklemesi, SQL Server veritabanı altyapısını başlatmak için gereken en az bir dosya kümesini kopyalar.

takımınız ağır veritabanı ihtiyaçlarına ihtiyaç duyuyor veya projeleriniz SQL Server Express localdb 'ye yükseldiğinde, daha fazla ölçeklendirme olasılığı sağlamak için SQL Express veya tam SQL Server yükseltmeniz gerekir. SQL Server yükseltirseniz, SQL Server Express localdb için MDF ve LDF dosyaları kullanıcı profili klasöründe depolanır. bu dosyalar, SQL Server Express veya SQL Server yük testi veritabanını içeri aktarmak için kullanılabilir.

## <a name="load-test-results-store-considerations"></a>Yük testi sonuçları deposu konuları

Visual Studio Enterprise yüklendiğinde, yük testi sonuçları deposu, bilgisayarda yüklü olan bir SQL Express örneğini kullanmak üzere ayarlanır. SQL Express, en fazla 4 GB disk alanı kullanımıyla sınırlandırılmıştır. uzun bir süre boyunca çok sayıda yük testi çalıştıracağınızı düşünüyorsanız, yük testi sonuçları deposunu, varsa tam SQL Server ürünün bir örneğini kullanacak şekilde yapılandırmayı düşünmelisiniz.

## <a name="load-test-analyzer-tasks"></a>Yük Testi Çözümleyicisi görevleri

|Görevler|İlişkili konular|
|-|-----------------------|
|**Yük testi sonuçları deposu ayarlama:** bir SQL veritabanında yük testi sonuçları deposu ayarlayabilirsiniz. **Note:**  Bir test denetleyicisi yüklediğinizde, yük testi deposu da oluşturulabilir. Daha fazla bilgi için bkz. [test aracılarını yükleyip yapılandırma](../test/lab-management/install-configure-test-agents.md).||
|**Bir sonuç deposunu seçme ve görüntüleme:** Belirli bir sonuç deposu seçebilirsiniz. Yerel bir sonuç deposuyla sınırlı değilsiniz. Genellikle, yük testleri, uzak bir aracı bilgisayarları kümesi üzerinde çalıştırılır. aracılarınızdan veya yerel bilgisayarınızda Test sonuçları, yük testi sonuçları deposu oluşturduğunuz SQL sunucusuna kaydedilebilir. Her iki durumda da, **Test Denetleyicilerini Yönet** penceresini kullanarak yük testi sonuçlarınızı nerede depolayabileceğiniz belirlemeniz gerekir.|-   [Nasıl yapılır: yük testi sonuçları deposu seçme](../test/how-to-select-a-load-test-results-repository.md)<br />-   [Nasıl yapılır: analiz için yük testi sonuçlarına erişme](../test/how-to-access-load-test-results-for-analysis.md)|
|**Depodan bir yük testi sonucunu silme:** **Yük Testi Düzenleyicisi** yük testi sonucunu, **Load Test sonuçları aç ve Yönet** iletişim kutusunu kullanarak kaldırabilirsiniz.|-   [Nasıl yapılır: bir depodan yük testi sonuçlarını silme](../test/how-to-delete-load-test-results-from-a-repository.md)|
|**Sonuçları bir depoya içeri ve dışarı aktarma:** Yük testi sonuçlarını **Yük Testi Düzenleyicisi** içeri ve dışarı aktarabilirsiniz.|-   [Nasıl yapılır: yük testi sonuçlarını depoya aktarma](../test/how-to-import-load-test-results-into-a-repository.md)<br />-   [Nasıl yapılır: bir depodan yük testi sonuçlarını dışarı aktarma](../test/how-to-export-load-test-results-from-a-repository.md)|

## <a name="related-tasks"></a>İlişkili görevler

[Yük testi sonuçlarını çözümle](../test/analyze-load-test-results-using-the-load-test-analyzer.md)

**Yük Testi Çözümleyicisi**'ni kullanarak, çalışan bir yük testinin ve tamamlanan bir yük testinin sonuçlarını görüntüleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi sonuçlarını çözümle](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Nasıl yapılır: analiz için yük testi sonuçlarına erişme](../test/how-to-access-load-test-results-for-analysis.md)
