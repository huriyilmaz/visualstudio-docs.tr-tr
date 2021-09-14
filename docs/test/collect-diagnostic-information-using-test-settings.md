---
title: Test ayarlarını kullanarak tanılama bilgilerini topla
description: testlerinizi çalıştırdığınızda ek veri toplamak için Visual Studio Test ayarlarını nasıl kullanacağınızı öğrenin. Birkaç tanılama veri bağdaştırıcısı hakkında bilgi edinin.
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
ms.openlocfilehash: de3734650efc8831a30f6460b32ede93449280fe
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634265"
---
# <a name="collect-diagnostic-information-using-test-settings"></a>Test ayarlarını kullanarak tanılama bilgilerini topla

testlerinizi çalıştırdığınızda ek verileri toplamak için Visual Studio *Test ayarlarını* kullanabilirsiniz. Örneğin, testinizi çalıştırırken bir video kaydı yapmak isteyebilirsiniz. Şunları yapmak için tanılama veri bağdaştırıcıları vardır:

- Her UI eylemi adımını metin biçiminde topla

- Her bir kullanıcı arabirimi eylemini kayıttan yürütmeye yönelik olarak kaydet

- Sistem bilgilerini topla

- Olay günlüğü verilerini topla

- Tekrarlamayan hataları yalıtmaya yardımcı olmak için IntelliTrace verilerini toplayın

Tanılama veri bağdaştırıcıları, bir test makinesinin davranışını değiştirmek için de kullanılabilir. örneğin, Visual Studio bir test ayarıyla, takımınızın uygulamasının performansını değerlendirmek için çeşitli ağ topolojisi performans sorunlarını taklit edebilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="use-test-settings-with-visual-studio"></a>Visual Studio ile test ayarlarını kullanma

Visual Studio kullanarak birimini, kodlanmış uı 'yi, web performansını veya yük testlerini çalıştırmak için, testlerinizi çalıştırdığınızda kullanılacak test ayarlarını ekleyebilir, yapılandırabilir ve seçebilirsiniz. Testlerinizi çalıştırmak, veri toplamak veya test makinesini uzaktan etkilemek için, test ayarlarınızda kullanmak üzere bir test denetleyicisi belirtmeniz gerekir. Test denetleyicisi, test ayarlarınızda her bir rol için kullanılabilen aracılara sahiptir.

## <a name="diagnostic-data-adapter-details"></a>Tanılama veri bağdaştırıcısı ayrıntıları

Aşağıdaki tabloda, tanılama veri bağdaştırıcılarının yerel veya uzak makine rolleriyle kullanılmak üzere yapılandırılabileceği çeşitli yollarla ilgili bir genel bakış sunulmaktadır.

|Test ayarında kullanılan tanılama veri bağdaştırıcısı|Yerel makinede el ile testler|Otomatikleştirilmiş testler|El ile testler: roller ve ortam kümesi kullanarak veri toplama|Notlar|
|-|-|-|-|-|
|**ıntellitrace ve Test etkisi için istemci Proxy ASP.NET:** Bu proxy, IntelliTrace ve test etkisi tanılama veri bağdaştırıcıları için bir istemciden bir Web sunucusuna http çağrıları hakkında bilgi toplamanıza olanak tanır.|Yes|Yes|Yes|-Bunu yalnızca bir istemci rolü için IntelliTrace veya test etkisi tanılama veri bağdaştırıcıları seçildiğinde kullanın.|
|**ASP.NET profil oluşturucu:** ASP.NET web uygulamalarında performans verilerini toplayan ASP.NET profil oluşturma içeren bir test ayarı oluşturabilirsiniz.|No|Evet (bkz. notlar)|No|-Bu tanılama veri bağdaştırıcısı yalnızca Visual Studio yük testlerini çalıştırdığınızda desteklenir.|
|**Kod kapsamı:** Kodunuzun ne kadarının testler kapsamında olduğunu araştırmak için kullanılan kod kapsamı bilgilerini içeren bir test ayarı oluşturabilirsiniz.|No|Evet (bkz. notlar)|No|-yalnızca Visual Studio veya *mstest.exe* ve yalnızca testi çalıştıran makineden otomatikleştirilmiş bir test çalıştırdığınızda kod kapsamını kullanabilirsiniz. Uzak koleksiyon desteklenmiyor.<br />-IntelliTrace bilgilerini toplamak için yapılandırılmış test ayarı da varsa, kod kapsamı verilerinin toplanması çalışmaz. **Note:**  bu tanılama veri bağdaştırıcısı yalnızca Visual Studio test ayarları için geçerlidir. Microsoft Test Yöneticisi (Visual Studio 2017 ' de kullanım dışı) test ayarları için kullanılmaz. ayrıca, bu bağdaştırıcı Visual Studio 2010 test projeleriyle uyumluluk içindir. **Note:**  uyumluluk için, otomatik testler Microsoft Test Yöneticisi veya bir uzak Test aracısından, eski MSTest çalıştırıcısı kullanılarak Visual Studio çalıştırıldığında kod kapsamı geçerlidir.|
|**Olay günlüğü:** Test sonuçlarına dahil olan olay günlüğü toplamayı dahil etmek için bir test ayarı yapılandırabilirsiniz.|Yes|Yes|Yes||
|**IntelliTrace:** Yeniden oluşturulması zor olan hataları yalıtmaya yardımcı olmak üzere *IntelliTrace* için tanılama veri bağdaştırıcısını belirli tanılama izleme bilgilerini toplayacak şekilde yapılandırabilirsiniz. Bu, bu bilgileri içeren bir IntelliTrace dosyası oluşturur. Bir IntelliTrace dosyası *. iTrace* uzantısına sahiptir. Bir test başarısız olduğunda, bir hata oluşturabilirsiniz. Test sonuçlarıyla birlikte kaydedilen IntelliTrace dosyası otomatik olarak bu hataya bağlanır. IntelliTrace dosyasında toplanan veriler, kodda bir hatayı yeniden oluşturmak ve tanılamak için gereken süreyi azaltarak hata ayıklama verimliliğini artırır. Bu IntelliTrace dosyasından yerel oturumun başka bir bilgisayarda benzetimi yapılabilir. Bu, bir hatanın tekrarsız olma riskini azaltır.|Yes|Yes|Yes|-IntelliTrace verileri koleksiyonunu etkinleştirirseniz, kod kapsamı verilerinin toplanması çalışmaz.<br />-bir web istemci rolü için ıntellitrace kullanıyorsanız, ıntellitrace ve Test etkisi tanılama veri bağdaştırıcısı için ASP.NET istemci Proxy 'sini de seçmeniz gerekir.<br />-Yalnızca şu IIS sürümleri desteklenir: IIS 7,0, IIS 7,5 ve IIS 8,0.|
|**Ağ öykünmesi:** Test ayarı kullanarak testinize yapay bir ağ yükü yerleştirmek istediğinizi belirtebilirsiniz. Ağ öykünmesi, çevirmeli gibi belirli bir ağ bağlantı hızına öykünüyerek makineye ve makineden iletişimi etkiler. |No|Evet (bkz. notlar)|No|İstemci veya sunucu rolü için ağ öykünmesi tanılama veri bağdaştırıcısını kullanabilirsiniz. Bağdaştırıcıyı birbirleriyle iletişim kuran bu roller üzerinde kullanmanız gerekmez. **Note:**  bu tanılama veri bağdaştırıcısı yalnızca Visual Studio test ayarları için geçerlidir. Microsoft Test Yöneticisi (Visual Studio 2017 ' de kullanım dışı) test ayarları için kullanılmaz. **Note:**  Ağ öykünmesi, ağ bağlantısı hızını artırmak için kullanılamaz. **Uyarı:**  Ağ öykünmesi tanılama veri bağdaştırıcısını test ayarlarına dahil etmeniz ve yerel makinenizde kullanmayı düşünüyorsanız, ağ öykünmesi sürücüsünü Makinenizin ağ bağdaştırıcılarından birine bağlamanız gerekir. Ağ öykünmesi sürücüsü, ağ öykünmesi tanılama veri bağdaştırıcısının çalışması için gereklidir. Ağ öykünmesi sürücüsü, bağdaştırıcınıza yüklenmiş ve iki şekilde bağlanır: <ul><li>**Microsoft Visual Studio Test aracısı ile yüklenen ağ öykünmesi sürücüsü:** Visual Studio Test aracısı hem uzak makinelerde hem de yerel makinenizde kullanılabilir. bir Visual Studio Test aracısı yüklediğinizde, yükleme işlemi ağ öykünmesi sürücüsünü ağ kartınıza bağlayan bir yapılandırma adımı içerir. Daha fazla bilgi için bkz. [test aracılarını yükleyip yapılandırma](../test/lab-management/install-configure-test-agents.md).</li><li>**Ağ öykünmesi sürücüsü Microsoft Visual Studio Test Professional yüklendi:** Ağ öykünmesini ilk kez kullandığınızda, ağ öykünmesi sürücüsünü bir ağ kartına bağlamanız istenir.</li></ul> ayrıca, aşağıdaki komutu kullanarak Visual Studio test aracısını yüklemeden yerel makinenize komut satırından ağ öykünme sürücüsünü yükleyebilirsiniz: **vstestconfig NETWORKEMULATION/install** **uyarısı:** ağ öykünmesi bağdaştırıcısı yük testleri tarafından yok sayılır. Bunun yerine, yük testleri yük testi senaryosunun ağ karışımında belirtilen ayarları kullanır.|
|**Sistem bilgileri:** Test ayarı, testin çalıştırıldığı makine hakkında sistem bilgilerini içerecek şekilde ayarlanabilir.|Yes|Yes|Yes||
|**Test etkisi:** Bir test çalışması çalıştırıldığında, uygulama kodunuzun hangi yöntemlerinin kullanıldığı hakkında bilgi toplayabilirsiniz. Bu, hangi testlerin bu geliştirme değişikliklerinden etkilendiğini belirlemede, geliştiriciler tarafından yapılan uygulama kodundaki değişikliklerle birlikte kullanılabilir.|Yes|Yes|Yes|-bir web istemci rolü için test etkisi verileri topluyorsanız ıntellitrace ve test etkisi tanılama veri bağdaştırıcısı için ASP.NET istemci Proxy 'sini de seçmeniz gerekir.<br />-Yalnızca şu IIS sürümleri desteklenir: IIS 7,0, IIS 7,5 ve IIS 8,0.|
|**Video kaydedicisi:** Bir testi çalıştırdığınızda masaüstü oturumunuzun bir video kaydını oluşturabilirsiniz. Video, diğer takım üyelerinin yeniden oluşturulması zor olan uygulama sorunlarını yalıtmalarına yardımcı olabilir.|Yes|Evet (bkz. notlar)|Yes|-Test Aracısı yazılımını bir hizmet yerine işlem olarak çalışacak şekilde etkinleştirirseniz otomatik testler çalıştırdığınızda bir video kaydı oluşturabilirsiniz.|
