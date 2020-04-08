---
title: Test ayarlarını kullanarak tanılama bilgilerini toplama
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, configuring run settings
ms.assetid: 0c86918b-cd63-4468-8f49-6d547a1276dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2e853e0ec54179178eba0f1566c34d7cfd63cee5
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880292"
---
# <a name="collect-diagnostic-information-using-test-settings"></a>Test ayarlarını kullanarak tanılama bilgilerini toplama

Testlerinizi çalıştırırken ek veri toplamak için Visual Studio'daki *Test ayarlarını* kullanabilirsiniz. Örneğin, testinizi çalıştırırken bir video kaydı yapmak isteyebilirsiniz. Tanısal veri bağdaştırıcıları şunlardır:

- Metin biçimindeki her kullanıcı arabirimi eylem adımLarını toplama

- Oynatma küçülüyor için her bir Ara Birimi eylemini kaydetme

- Sistem bilgilerini toplama

- Olay günlüğü verilerini toplama

- Tekrarlanabilir olmayan hataları yalıtmaya yardımcı olmak için IntelliTrace verilerini topla

Tanılama veri bağdaştırıcıları, test makinesinin davranışını değiştirmek için de kullanılabilir. Örneğin, Visual Studio'daki bir test ayarı ile, ekibinizin uygulamasının performansını değerlendirmek için çeşitli ağ topolojisi darboğazlarını taklit edebilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="use-test-settings-with-visual-studio"></a>Visual Studio ile test ayarlarını kullanma

Visual Studio'yu kullanarak biriminizi, kodlanmış u-posta, web performansı veya yükleme testleri çalıştırmak için, testlerinizi çalıştırdığınızda kullanılacak test ayarlarını ekleyebilir, yapılandırabilir ve seçebilirsiniz. Testlerinizi çalıştırmak, veri toplamak veya bir test makinesini uzaktan etkilemek için test ayarlarınızda kullanılacak bir test denetleyicisi belirtmeniz gerekir. Test denetleyicisinde, test ayarlarınızdaki her rol için kullanılabilecek aracılar vardır.

## <a name="diagnostic-data-adapter-details"></a>Tanılama veri bağdaştırıcısı ayrıntıları

Aşağıdaki tablo, tanılama veri bağdaştırıcılarının yerel veya uzak makine rolleriyle kullanılmak üzere yapılandırılabildiği çeşitli yollara genel bir bakış sağlar.

|Test ayarında kullanılan tanılama veri bağdaştırıcısı|Yerel makinede Manuel Testler|Otomatik Testler|El Ile Testler: Bir dizi rol ve ortam kullanarak veri toplama|Notlar|
|-|-|-|-|-|
|**IntelliTrace ve Test Etkisi için ASP.NET İstemci Proxy:** Bu proxy, intelliTrace ve Test Impact tanıveri bağdaştırıcıları için bir web sunucusuna istemciden http aramaları hakkında bilgi toplamanızı sağlar.|Evet|Evet|Evet|- Bunu yalnızca IntelliTrace veya Test Impact tanıveri bağdaştırıcıları bir istemci rolü için seçildiğinde kullanın.|
|**ASP.NET profilleyici:** ASP.NET web uygulamalarında performans verileri toplayan ASP.NET profil oluşturma içeren bir test ayarı oluşturabilirsiniz.|Hayır|Evet (Bkz. Notlar)|Hayır|- Bu tanılama veri bağdaştırıcısı yalnızca Visual Studio'dan yük testleri çalıştırdığınızda desteklenir.|
|**Kod kapsamı:** Kodunuzun ne kadarının testler tarafından kapsandığını araştırmak için kullanılan kod kapsamı bilgilerini içeren bir test ayarı oluşturabilirsiniz.|Hayır|Evet (Bkz. Notlar)|Hayır|- Kod kapsamını yalnızca Visual Studio veya *mstest.exe'den*ve yalnızca testi çalıştıran makineden otomatik bir test çalıştırdığınızda kullanabilirsiniz. Uzak toplama desteklenmez.<br />- Ayrıca IntelliTrace bilgi toplamak için yapılandırılmış test ayarı varsa kod kapsama verileri toplama çalışmıyor. **Not:**  Bu tanılama veri bağdaştırıcısı yalnızca Visual Studio test ayarları için geçerlidir. Microsoft Test Manager'da test ayarları için kullanılmaz (Visual Studio 2017'de amortismana dahil edilir). Ayrıca, bu bağdaştırıcı Visual Studio 2010 test projeleri ile uyumluluk içindir. **Not:**  Uyumluluk için, otomatik testler Microsoft Test Yöneticisi'nden veya eski MSTest runner'ını kullanarak Visual Studio'dan uzak bir Test aracısı üzerinde çalıştırıldığında kod kapsamı geçerlidir.|
|**Olay günlüğü:** Test ayarını, test sonuçlarına dahil edilen olay günlüğü toplamayı içerecek şekilde yapılandırabilirsiniz.|Evet|Evet|Evet||
|**IntelliTrace:** *IntelliTrace* için tanılama veri bağdaştırıcısını, yeniden oluşturulması zor hataları yalıtmak için belirli tanılama izleme bilgileri toplamak üzere yapılandırabilirsiniz. Bu, bu bilgileri içeren bir IntelliTrace dosyası oluşturur. IntelliTrace dosyasında *.iTrace*uzantısı vardır. Bir test başarısız olduğunda, bir hata oluşturabilirsiniz. Test sonuçlarıyla birlikte kaydedilen IntelliTrace dosyası otomatik olarak bu hataya bağlanır. IntelliTrace dosyasında toplanan veriler, koddaki bir hatayı çoğaltmak ve tanılamak için gereken süreyi azaltarak hata ayıklama verimliliğini artırır. Bu IntelliTrace dosyasından yerel oturum başka bir bilgisayarda simüle edilebilir. Bu, bir hatanın tekrarlanamaz olma riskini azaltır.|Evet|Evet|Evet|- IntelliTrace verilerinin toplanmasını etkinleştiriseniz, kod kapsamı verilerinin toplanması çalışmaz.<br />- Bir web istemcisi rolü için IntelliTrace kullanıyorsanız, intelliTrace ve Test Impact tanıveri bağdaştırıcısı için ASP.NET İstemci Proxy'sini de seçmeniz gerekir.<br />- IIS'nin yalnızca aşağıdaki sürümleri desteklenir: IIS 7.0, IIS 7.5 ve IIS 8.0.|
|**Ağ öykünme:** Bir test ayarı kullanarak testinize yapay ağ yükü yerleştirmek istediğinizi belirtebilirsiniz. Ağ öykünme, çevirmeli bağlantı hızı gibi belirli bir ağ bağlantı hızını taklit ederek makineyle olan ve makineden gelen iletişimi etkiler. |Hayır|Evet (Bkz. Notlar)|Hayır|Ağ öykünme tanılama veri bağdaştırıcısını istemci veya sunucu rolü için kullanabilirsiniz. Bağdaştırıcıyı, birbiriyle iletişim kurabilen bu iki rolde de kullanmanız gerekmez. **Not:**  Bu tanılama veri bağdaştırıcısı yalnızca Visual Studio test ayarları için geçerlidir. Microsoft Test Manager'da test ayarları için kullanılmaz (Visual Studio 2017'de amortismana dahil edilir). **Not:**  Ağ bağlantı hızını artırmak için ağ öykünme kullanılamaz. **Uyarı:**  Ağ öykünme tanılama veri bağdaştırıcısını test ayarlarına eklerseniz ve bunu yerel makinenizde kullanmayı planlıyorsanız, ağ öykünme sürücüsünü de makinenizin ağ bağdaştırıcılarından birine bağlamanız gerekir. Ağ öykünme sürücüsü, ağ öykünme tanıveri bağdaştırıcısının işlevi ne kadar gerekli. Ağ öykünme sürücüsü yüklenir ve bağdaştırıcınıza iki şekilde bağlanır: <ul><li>**Microsoft Visual Studio Test Aracısı ile yüklü ağ öykünme sürücüsü:** Visual Studio Test Aracısı hem uzak makinelerde hem de yerel makinenizde kullanılabilir. Visual Studio Test Aracısı yüklediğinizde, yükleme işlemi ağ öykünme sürücüsünü ağ kartınıza bağlayan bir yapılandırma adımı içerir. Daha fazla bilgi için [bkz.](../test/lab-management/install-configure-test-agents.md)</li><li>**Microsoft Visual Studio Test Professional ile yüklü ağ öykünme sürücüsü:** Ağ öykünme sini'ni ilk kez kullandığınızda, ağ öykünme sürücüsünü bir ağ kartına bağlamanız istenir.</li></ul> Aşağıdaki komutu kullanarak Visual Studio test aracısını yüklemeden komut satırındaki ağ öykünme sürücüsünü yerel makinenize de yükleyebilirsiniz: **VSTestConfig NETWORKEMULATION /install** **Warning:** Ağ Öykünme bağdaştırıcısı yük testleri tarafından yoksayılır. Bunun yerine, yük testleri yük testi senaryosunun ağ karışımında belirtilen ayarları kullanır.|
|**Sistem bilgileri:** Test ayarı, testin çalıştırıldığı makine hakkındaki sistem bilgilerini içerecek şekilde ayarlanabilir.|Evet|Evet|Evet||
|**Test etkisi:** Bir test çalışması çalıştırıldığında uygulama kodunuzu hangi yöntemlerin kullanıldığı hakkında bilgi toplayabilirsiniz. Bu, geliştiriciler tarafından bu geliştirme değişikliklerinden hangi testlerin etkilendiğini belirlemek için yapılan uygulama kodudeğişiklikleriyle birlikte kullanılabilir.|Evet|Evet|Evet|- Bir web istemcisi rolü için test etki verileri topluyorsanız, IntelliTrace ve Test Impact tanıveri bağdaştırıcısı için ASP.NET İstemci Proxy'yi de seçmeniz gerekir.<br />- IIS'nin yalnızca aşağıdaki sürümleri desteklenir: IIS 7.0, IIS 7.5 ve IIS 8.0.|
|**Video Kaydedici:** Bir testi çalıştırdığınızda masaüstü oturumunuzun video kaydını oluşturabilirsiniz. Video, diğer ekip üyelerinin yeniden oluşturulması zor olan uygulama sorunlarını yalıtmalarına yardımcı olabilir.|Evet|Evet (Bkz. Notlar)|Evet|- Test aracısı yazılımının hizmet yerine işlem olarak çalışmasını sağlarsanız, otomatik testler çalıştırdığınızda bir video kaydı oluşturabilirsiniz.|
