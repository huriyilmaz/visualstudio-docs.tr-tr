---
title: Test ayarlarını kullanarak tanılama bilgilerini toplama
description: Testlerinizi çalıştırarak ek veri Visual Studio için Visual Studio'da Test ayarlarını kullanmayı öğrenin. Çeşitli tanılama veri bağdaştırıcıları hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, configuring run settings
ms.assetid: 0c86918b-cd63-4468-8f49-6d547a1276dc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 09d81d40eddd7bcb9470e83f301132c50320189181373febc1e4c0b50b78c636
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121395427"
---
# <a name="collect-diagnostic-information-using-test-settings"></a>Test ayarlarını kullanarak tanılama bilgilerini toplama

Testlerinizi *çalıştırarak Visual Studio* veri toplamak için Visual Studio'da Test ayarlarını kullanabilirsiniz. Örneğin, testini çalıştırarak bir video kaydı yapmak istiyor olabilirsiniz. Şunları yapmak için tanılama veri bağdaştırıcıları vardır:

- Metin biçiminde her kullanıcı arabirimi eylem adımını toplama

- Kayıttan kayıttan dönmek için her ui eylemlerini kaydetme

- Sistem bilgilerini toplama

- Olay günlüğü verilerini toplama

- Yeniden tekrarlandırılemeyen hataları yalıtmak için IntelliTrace verileri toplama

Tanılama veri bağdaştırıcıları, test makinesinin davranışını değiştirmek için de kullanılabilir. Örneğin, bir test ayarı Visual Studio, takımınız uygulamasının performansını değerlendirmek için çeşitli ağ topolojisi performans sorunlarını öykünebilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="use-test-settings-with-visual-studio"></a>Test ayarlarını Visual Studio

Visual Studio kullanarak birim, kodlanmış kullanıcı arabirimi, web performansı veya yük testlerinizi çalıştırmak için testlerinizi çalıştıracak test ayarlarını ekleyebilir, yapılandırabilir ve seçebilirsiniz. Testlerinizi çalıştırmak, veri toplamak veya bir test makinesini uzaktan etkileyebiliyor olmak için test ayarlarınıza bir test denetleyicisi belirtmeniz gerekir. Test denetleyicisi, test ayarlarınıza her rol için kullanılmaktadır aracıları içerir.

## <a name="diagnostic-data-adapter-details"></a>Tanılama veri bağdaştırıcısı ayrıntıları

Aşağıdaki tabloda, tanılama veri bağdaştırıcılarının yerel veya uzak makine rolleriyle birlikte kullanmak üzere yapılandırılanın çeşitli yolları hakkında genel bir bakış ve bulunmaktadır.

|Test ayarında kullanılan tanılama veri bağdaştırıcısı|Yerel makinede El İle Testler|OtomatikLeştirilmiş Testler|El ile Yapılan Testler: Bir rol kümesi ve ortam kullanarak veri toplama|Notlar|
|-|-|-|-|-|
|**ASP.NET IntelliTrace ve Test Etkisi için İstemci Ara Sunucusu:** Bu ara sunucu, IntelliTrace ve Test Etkisi tanılama veri bağdaştırıcıları için istemciden web sunucusuna yapılan http çağrıları hakkında bilgi toplamaya olanak sağlar.|Yes|Yes|Yes|- Bunu yalnızca bir istemci rolü için IntelliTrace veya Test Etkisi tanılama veri bağdaştırıcıları seçildiğinde kullanın.|
|**ASP.NET profil oluşturma:** Web uygulamalarında performans verilerini toplayan ASP.NET profil oluşturmayı içeren bir test ASP.NET oluşturabilirsiniz.|Hayır|Evet (Bkz. Notlar)|Hayır|- Bu tanılama veri bağdaştırıcısı yalnızca yük testlerini Visual Studio.|
|**Kod kapsamı:** Kodunuzun ne kadarını testlerin kapsamında olduğunu araştırmak için kullanılan kod kapsamı bilgilerini içeren bir test ayarı oluşturabilirsiniz.|Hayır|Evet (Bkz. Notlar)|Hayır|- Kod kapsamı yalnızca bir otomatikleştirilmiş testi Visual Studio veyamstest.exe ** ve yalnızca testi çalıştıran makineden çalıştırırken kullanabilirsiniz. Uzak koleksiyon desteklenmiyor.<br />- IntelliTrace bilgilerini toplamak için yapılandırılmış test ayarınız da varsa kod kapsamı verilerini toplama çalışmıyor. **Not:**  Bu tanılama veri bağdaştırıcısı yalnızca test ayarları Visual Studio geçerlidir. Microsoft Test Yöneticisi'da test ayarları için Microsoft Test Yöneticisi (Visual Studio 2017'de kullanım dışıdır). Ayrıca, bu bağdaştırıcı 2010 test Visual Studio uyumluluk için kullanılır. **Not:**  Uyumluluk için kod kapsamı, eski MSTest çalıştırıcısı kullanılarak Microsoft Test Yöneticisi veya uzak test aracılarından Visual Studio çalıştırıldıklarından uygulanır.|
|**Olay günlüğü:** Test sonuçlarına dahil edilen olay günlüğü toplamayı içerecek şekilde bir test ayarı yapılandırabilirsiniz.|Yes|Yes|Yes||
|**IntelliTrace:** *IntelliTrace* için tanılama veri bağdaştırıcısını, yeniden oluşturması zor hataları yalıtmak üzere belirli tanılama izleme bilgilerini toplamak üzere yapılandırabilirsiniz. Bu, bu bilgileri içeren bir IntelliTrace dosyası oluşturur. IntelliTrace dosyasının uzantısı *.iTrace'dır.* Test başarısız olduğunda hata oluşturabilirsiniz. Test sonuçlarıyla birlikte kaydedilen IntelliTrace dosyası bu hataya otomatik olarak bağlıdır. IntelliTrace dosyasında toplanan veriler, kodda bir hatayı yeniden oluşturmak ve tanılamak için gereken zamanı azaltarak hata ayıklama üretkenliğini artırır. Bu IntelliTrace dosyasından yerel oturumun benzetimi başka bir bilgisayarda gerçek olabilir. Bu, bir hatanın yeniden tekrarlanabilir olma riskini azaltır.|Yes|Yes|Yes|- IntelliTrace verisi toplamayı etkinleştirirsiniz, kod kapsamı verisi koleksiyonu çalışmıyor.<br />- Bir web istemcisi rolü için IntelliTrace kullanıyorsanız, IntelliTrace ve Test Etkisi tanılama veri ASP.NET İstemci Ara Sunucusu'ASP.NET da seçmeniz gerekir.<br />- Yalnızca aşağıdaki IIS sürümleri de kullanılabilir: IIS 7.0, IIS 7.5 ve IIS 8.0.|
|**Ağ öykünmesi:** Bir test ayarı kullanarak teste yapay ağ yükü yüklemek istediğiniz belirtebilirsiniz. Ağ öykünmesi, çevirmeli bağlantı gibi belirli bir ağ bağlantı hızı öykünerek makineye gelen ve makineden gelen iletişimi etkiler. |Hayır|Evet (Bkz. Notlar)|Hayır|Bir istemci veya sunucu rolü için ağ öykünmesi tanılama veri bağdaştırıcısını kullanabilirsiniz. Bağdaştırıcıyı, birbirleriyle iletişim kuran bu rollerin her ikisinde de kullanmak zorunda değildir. **Not:**  Bu tanılama veri bağdaştırıcısı yalnızca test ayarları Visual Studio geçerlidir. Microsoft Test Yöneticisi'da test ayarları için Microsoft Test Yöneticisi (Visual Studio 2017'de kullanım dışıdır). **Not:**  Ağ öykünmesi, ağ bağlantı hızını artırmak için kullanılamaz. **Uyarı:**  Ağ öykünme tanılama veri bağdaştırıcısını test ayarlarına dahil ediyorsanız ve bunu yerel makineniz üzerinde kullanmak için kullanıyorsanız, ağ öykünme sürücüsünü de makinenizin ağ bağdaştırıcılarından biri ile bağlamanız gerekir. Ağ öykünme sürücüsünün çalışması için ağ öykünmesi tanılama veri bağdaştırıcısı gereklidir. Ağ öykünme sürücüsü iki şekilde yüklenir ve bağdaştırıcınıza bağlı olur: <ul><li>**Microsoft Visual Studio Test Aracısı ile Microsoft Visual Studio öykünme sürücüsü:** Visual Studio Test Aracısı hem uzak makinelerde hem de yerel makinede kullanılabilir. Test Aracısına Visual Studio, yükleme işlemi ağ öykünme sürücüsünü ağ kartınıza bağlayan bir yapılandırma adımı içerir. Daha fazla bilgi için [bkz. Test aracılarını yükleme ve yapılandırma.](../test/lab-management/install-configure-test-agents.md)</li><li>**Ağ öykünme sürücüsü şu Microsoft Visual Studio Test Professional:** Ağ öykünmesini ilk kez kullanıyorsanız, ağ öykünme sürücüsünü bir ağ kartına bağlamanız istenir.</li></ul> Ayrıca, aşağıdaki komutu kullanarak Visual Studio test aracısına yüklemeden komut satırına ağ öykünme sürücüsünü yükleyebilirsiniz: **VSTestConfig NETWORKEMULATION /install** **Warning:** Ağ Öykünmesi bağdaştırıcısı yük testleri tarafından yoksayılır. Bunun yerine, yük testleri yük testi senaryosunun ağ karışımında belirtilen ayarları kullanır.|
|**Sistem bilgileri:** Testin çalıştırıldı olduğu makineyle ilgili sistem bilgilerini içerecek şekilde bir test ayarı ayarlandırabilirsiniz.|Yes|Yes|Yes||
|**Test etkisi:** Bir test çalışması çalıştıryken uygulama kodunuzun hangi yöntemlerinin kullanıldıkları hakkında bilgi toplayabilirsiniz. Bu, hangi testlerin bu geliştirme değişikliklerinden etkilendiğini belirlemek için geliştiriciler tarafından yapılan uygulama kodu değişiklikleriyle birlikte kullanılabilir.|Yes|Yes|Yes|- Bir web istemcisi rolü için test etkisi verileri topluyorsanız IntelliTrace ve Test Etkisi tanılama veri ASP.NET İstemci Ara Sunucusu'ASP.NET da seçmeniz gerekir.<br />- Yalnızca aşağıdaki IIS sürümleri de kullanılabilir: IIS 7.0, IIS 7.5 ve IIS 8.0.|
|**Video Recorder:** Bir test çalıştırarak masaüstü oturumunuz için bir video kaydı oluşturabilirsiniz. Video, diğer ekip üyelerinin yeniden oluşturması zor uygulama sorunlarını yalıtmalarına yardımcı olabilir.|Yes|Evet (Bkz. Notlar)|Yes|- Test aracısı yazılımının bir hizmet yerine işlem olarak çalışmasına olanak sağlarsanız, otomatikleştirilmiş testler çalıştırarak bir video kaydı oluşturabilirsiniz.|
