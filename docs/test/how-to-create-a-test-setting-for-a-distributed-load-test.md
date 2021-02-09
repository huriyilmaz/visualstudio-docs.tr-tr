---
title: Dağıtılmış yük testi için bir test ayarı oluşturma
description: Test aracılarını ve test denetleyicilerini kullanarak bu testleri birden çok makineye dağıtabilmeniz için yük testlerinizin test ayarlarını nasıl yapılandıracağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- test settings, for distributed load tests
ms.assetid: b63d4b71-3b74-4872-b2d1-f0bd1a9a8544
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 4ca0058d1f06e00941766ed1ecf6f81d73939a8c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877999"
---
# <a name="how-to-create-a-test-settings-file-for-a-distributed-load-test"></a>Nasıl yapılır: dağıtılmış yük testi için test ayarları dosyası oluşturma

Test aracılarını ve test denetleyicilerini kullanarak bu testleri birden çok makineye dağıtabilmeniz için yük testlerinizin *test ayarlarını* yapılandırın. Test ayarlarını Ayrıca, toplamak istediğiniz veri türlerini veya Visual Studio 'dan yük testlerinizi çalıştırdığınızda test makinelerini nasıl etkileyeceğini belirten *Tanılama veri bağdaştırıcılarını* kullanacak şekilde yapılandırabilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Örneğin, ASP.NET profil oluşturucu tanılama veri bağdaştırıcısını kodun performans dökümünü toplamak için kullanabilirsiniz. Ayrıca, tanılama veri bağdaştırıcıları, test makinesinde olası performans sorunlarını taklit etmek veya kullanılabilir sistem belleğini azaltmak için kullanılabilir.

Visual Studio için test ayarları bir dosyada depolanır. Test ayarları her bir rolle ilgili olarak aşağıdaki bilgileri tanımlar:

- Test edilen uygulamanız için gereken roller kümesi

- Testlerinizi çalıştırmak için kullanılacak rol

- Her rol için kullanılacak tanılama veri bağdaştırıcıları

Testlerinizi çalıştırdığınızda, bu belirli test çalıştırması için ihtiyaç duyduğunuz seçeneğe bağlı olarak etkin test ayarları olarak kullanılacak test ayarlarını seçersiniz. Test ayarları dosyası çözümünüzün bir parçası olarak depolanır. Dosya adı *. testsettings* uzantısına sahiptir.

Bir çözüme Web performansı ve yük testi projesi eklediğinizde, *varsayılan bir. testsettings* dosyası oluşturulur. Dosya çözüm **öğeleri** klasörü altında çözüme otomatik olarak eklenir. Bu dosya testlerinizi herhangi bir tanılama veri bağdaştırıcısı olmadan yerel olarak çalıştırır. Tanılama veri bağdaştırıcılarını ve test denetleyicilerini belirtmek için başka bir *. testsettings* dosyası ekleyebilir veya bir *. testsettings* dosyasını düzenleyebilirsiniz.

Test denetleyicisi, test ayarlarınızda her bir rol için kullanılabilecek aracılara sahip olacaktır. Test denetleyicileri ve test aracıları hakkında daha fazla bilgi için bkz. [Visual Studio ile test denetleyicilerini ve test aracılarını yönetme](../test/manage-test-controllers-and-test-agents.md).

Visual Studio 'dan çalıştırmayı planladığınız yük testleri için çözümünüzdeki test ayarlarını oluşturmak ve kaldırmak için bu adımları izleyin.

## <a name="create-a-test-settings-file"></a>Test ayarları dosyası oluşturma

1. **Çözüm Gezgini**, **Çözüm öğeleri**' ne sağ tıklayın, **Ekle**' nin üzerine gelin ve sonra **Yeni öğe**' yi seçin.

     **Yeni Öğe Ekle** iletişim kutusu görünür.

2. **Yüklü şablonlar** bölmesinde, **Test ayarları**' nı seçin.

3. Seçim **Ad** kutusunda, test ayarları dosyasının adını değiştirin.

4. **Ekle**' yi seçin.

     Yeni test ayarları dosyası, **Çözüm öğeleri** klasörü altında **Çözüm Gezgini** görüntülenir.

5. **Test ayarları** iletişim kutusu görüntülenir. **Genel** sayfa seçilidir.

     Şimdi, test ayarları değerlerini düzenleyebilir ve kaydedebilirsiniz.

6. **Ad**' ın altında, test ayarlarının adını yazın.

7. Seçim **Açıklama**' nın altında, diğer takım üyelerinin ne için tasarlandığını bilmesi için test ayarı için bir açıklama yazın.

8. Seçim Test çalışmalarınız için varsayılan adlandırma şemasını seçmek için **varsayılan adlandırma şeması**' nı seçin. Kendi adlandırma düzeninizi tanımlamak için **Kullanıcı tanımlı düzen** ' i seçin ve ardından **önek metninde** istediğiniz metni yazın. Tarih ve saat damgasını test çalıştırması adına eklemek için, **Tarih-saat damgasını ekle**' yi seçin.

9. **Rolleri** seçin.

     **Roller** sayfası görüntülenir.

     ![Test ayarı rolü](../test/media/load_testtestrole.png)

10. Testlerinizi uzaktan çalıştırmak veya testlerinizi uzaktan çalıştırmak ve uzaktan veri toplamak için **test yürütme yöntemi** açılır öğesini kullanın ve **Uzaktan yürütme**' yi seçin.

11. Testleri çalıştırmak veya veri toplamak için kullanılacak **denetleyicideki** test aracıları için bir test denetleyicisi seçmek için **Denetleyici** açılır listesini kullanın.

    > [!NOTE]
    > İlk kez bir denetleyici ekliyorsanız, açılan listede hiçbir denetleyici listelenmeyecektir. Liste, diğer test ayarlarında belirttiğiniz önceki denetleyiciler tarafından doldurulur. Denetleyicinin adını kutuya yazmanız gerekir (örneğin, **TestControllerMachine1**).

12. Testleri çalıştırmak ve veri toplamak için kullanmak istediğiniz rolleri eklemek için **Roller** altında **Ekle**' yi seçin.

13. **Ad** sütununa rol için bir ad yazın. Örneğin, rol "Web sunucusu" olabilir.

14. İhtiyacınız olan tüm rolleri eklemek için 12 ve 13. adımları yineleyin.

     Her rol, test denetleyicisi tarafından yönetilen bir test Aracısı kullanır.

15. Testlerinizi çalıştırmak istediğiniz rolü seçin ve ardından **Testleri çalıştırmak için rol olarak ayarla**' yı seçin.

    > [!IMPORTANT]
    > Oluşturduğunuz ve tanımladığınız diğer roller testleri çalıştırmaz, ancak yalnızca **veri ve tanılama** sayfasındaki Roller için belirttiğiniz veri ve tanılama bağdaştırıcılarına göre veri toplamak için kullanılacaktır.

16. Bir rol için kullanılabilecek aracıları sınırlandırmak için, rolü seçin ve ardından **Seçilen rolün aracı öznitelikleri** altındaki araç çubuğunda **Ekle** ' yi seçin.

     **Aracı seçim kuralı** iletişim kutusu görüntülenir.

     **Öznitelik adına** adı ve **öznitelik değerindeki** değeri yazın ve ardından **Tamam**' ı seçin. İhtiyaç duyduğunuz kadar çok öznitelik ekleyin.

     Örneğin, 16GB 'den fazla belleğe sahip test aracısı makinelerinde filtrelemek için "doğru" veya "yanlış" değerine sahip "RAM > 16GB" adlı bir öznitelik ekleyebilirsiniz. Aynı özniteliği bir veya daha fazla test aracısına uygulamak için, **Test denetleyicisini Yönet** iletişim kutusunu kullanın. Daha fazla bilgi için bkz. [Visual Studio ile test denetleyicilerini ve test aracılarını yönetme](../test/manage-test-controllers-and-test-agents.md).

17. **Veri ve tanılama** seçeneklerini belirleyin.

     **Veri ve tanılama** sayfası görüntülenir.

     ![Test ayarı verileri ve tanılama](../test/media/load_testtest.png)

18. **Veri ve tanılama** sayfasında, rolün veri toplamak için kullanacağı *Tanılama veri bağdaştırıcılarını* seçerek rolün ne yaptığını tanımlarsınız. Bu nedenle, rol için bir veya daha fazla veri ve tanılama bağdaştırıcısı etkinleştirildiyse, test denetleyicisi, rol için tanımladığınız özniteliklere göre belirtilen veri ve tanılama bağdaştırıcıları için veri toplamak üzere kullanılabilir bir test aracısı makinesini seçer. Her rol için toplamak istediğiniz veri ve tanılama veri bağdaştırıcılarını seçmek için, rolünü seçin. Her rol için, testlerin ihtiyaçlarına göre tanılama veri bağdaştırıcılarını seçin. Her bir rol için seçtiğiniz her bir tanılama veri bağdaştırıcısını yapılandırmak için **Yapılandır**' ı seçin.

     **Rol ve tanılama veri bağdaştırıcısı örneği:**

     Örneğin, "SQL kullanır" özniteliği "true" olarak ayarlanmış ve "RAM > 16GB" olarak ayarlanmış bir özniteliği olan "SQL Server" adlı bir sunucu rolü olan "Masaüstü Istemcisi" adlı bir istemci rolü oluşturabilirsiniz. **Roller** sayfasında **Testleri çalıştırmak Için rol olarak ayarla** ' yı seçerek "Masaüstü istemcisi" nin testleri çalıştıracağınızı belirtirseniz, test denetleyicisi Testlerı çalıştırmak için "SQL kullanır" özniteliği "true" olarak ayarlanmış test aracıları olan makineleri seçer. Test denetleyicisi Ayrıca "RAM > 16GB" özniteliğini içeren test aracılarına sahip SQL Server makinelerini, yalnızca role dahil edilen veri ve tanılama bağdaştırıcıları tarafından tanımlanan verileri toplamak için de seçer. "Masaüstü Istemcisi" test aracısı Ayrıca, söz konusu rol için veri ve tanılama bağdaştırıcılarını de seçerseniz, üzerinde çalıştığı makineler için veri toplayabilir.

     Her bir tanılama veri bağdaştırıcısı hakkındaki ayrıntılar ve bunu yapılandırma hakkında daha fazla bilgi için, ilgili konuyu aşağıdaki tabloda görebilirsiniz.

     Tanılama veri bağdaştırıcıları hakkında daha fazla bilgi için bkz. [test ayarlarını kullanarak tanılama bilgilerini toplama](../test/collect-diagnostic-information-using-test-settings.md).

     **Yük testleri için tanılama veri bağdaştırıcıları**

    |Tanılama veri bağdaştırıcısı|Yük testlerinde kullanma|İlişkili konu|
    |-|-------------------------|-|
    |**IntelliTrace ve test etkisi için ASP.net Istemci proxy 'si:** Bu proxy, IntelliTrace ve test etkisi tanılama veri bağdaştırıcıları için bir istemciden bir Web sunucusuna http çağrıları hakkında bilgi toplamanıza olanak tanır.|![Bilgi simgesi](../test/media/vc364f4.gif)<br /><br /> Test Aracısı makinelerinde sistem bilgilerini toplamak için özel bir ihtiyacınız yoksa, bu bağdaştırıcıyı eklemeyin. **Dikkat:**  Toplanan büyük miktarda veri nedeniyle oluşan sorunlardan dolayı yük testlerinde IntelliTrace bağdaştırıcısının kullanımını önermiyoruz. <br /><br /> Test etkisi verileri, yük testleri kullanılarak toplanmaz.||
    |**IntelliTrace:** Bir günlük dosyasında depolanan belirli tanılama izleme bilgilerini yapılandırabilirsiniz. Bir günlük dosyası *. tdlog* uzantısına sahiptir. Testinizi çalıştırdığınızda bir test adımı başarısız olursa, bir hata oluşturabilirsiniz. Tanılama izlemesini içeren günlük dosyası bu hataya otomatik olarak eklenir. Günlük dosyasında toplanan veriler, kodda bir hatayı yeniden oluşturmak ve tanılamak için gereken süreyi azaltarak hata ayıklama verimliliğini artırır. Bu günlük dosyasından yerel oturum başka bir bilgisayarda yeniden oluşturulabilir. Bu, bir hatanın yeniden oluşturulamayacağından riskini azaltır.<br /><br /> Daha fazla bilgi için bkz. [IntelliTrace verilerini toplama](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md).|![Önemli simgesi](../test/media/vc364f3.gif)<br /><br /> Toplanan ve günlüğe kaydedilen büyük miktarda veri nedeniyle oluşan sorunlardan dolayı yük testlerinde IntelliTrace bağdaştırıcısının kullanımını önermiyoruz. IntelliTrace bağdaştırıcısını yalnızca uzun çalıştırmayan ve çok sayıda test aracısı kullanmayan yük testlerinde kullanmayı denemeniz gerekir.|[Nasıl yapılır: hata ayıklama zor sorunlarını gidermek için IntelliTrace verilerini toplama](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)|
    |**ASP.NET Profil Oluşturucu:** ASP.NET Web uygulamalarında performans verilerini toplayan ASP.NET profil oluşturmayı içeren bir test ayarı oluşturabilirsiniz.|ASP.NET Profiler tanılama veri bağdaştırıcısı Internet Information Services (IIS) işlemini profiller, bu nedenle bir geliştirme Web sunucusunda çalışmayacaktır. Yük testinizde web sitesinin profilini almak için, IIS 'nin üzerinde çalıştığı makineye bir test aracısı yüklemeniz gerekir. Test Aracısı Yük oluşturmamayacak, ancak yalnızca koleksiyon Aracısı olacak. Daha fazla bilgi için bkz. [test aracılarını yükleyip yapılandırma](../test/lab-management/install-configure-test-agents.md).|[Nasıl yapılır: test ayarlarını kullanarak yük testleri için ASP.NET profil oluşturucuyu yapılandırma](../test/how-to-configure-aspnet-profiler-for-load-tests-using-test-settings.md)|
    |**Olay günlüğü:** Test sonuçlarına dahil edilecek olay günlüğü toplamayı dahil etmek için bir test ayarı yapılandırabilirsiniz.||[Nasıl yapılır: test ayarlarını kullanarak olay günlüğü koleksiyonunu yapılandırma](/previous-versions/dd504816(v=vs.110))|
    |**Ağ öykünmesi:** Test ayarı kullanarak testinize yapay bir ağ yükü koymak istediğinizi belirtebilirsiniz. Ağ öykünmesi, çevirmeli gibi belirli bir ağ bağlantı hızına öykünüyerek makineye ve makineden iletişimi etkiler. **Note:**  Ağ öykünmesi, ağ bağlantısı hızını artırmak için kullanılamaz.|Ağ öykünmesi bağdaştırıcısı, yük testleri tarafından yok sayılır. Bunun yerine, yük testleri yük testi senaryosunun ağ karışımında belirtilen ayarları kullanır.<br /><br /> Daha fazla bilgi için bkz. [sanal ağ türlerini belirtme](../test/specify-virtual-network-types-in-a-load-test-scenario.md).||
    |**Sistem bilgileri:** Sistem bilgileri tanısı ve veri toplayıcısının çalıştırıldığı makineler hakkındaki sistem bilgilerini içerecek şekilde bir test ayarı ayarlanabilir. Sistem bilgileri, test ayarları kullanılarak test sonuçlarında belirtilir.|![Bilgi simgesi](../test/media/vc364f4.gif)<br /><br /> Sistem bilgilerini hem yük aracılarından hem de test altındaki sistemden toplayabilirsiniz.|Bu bilgileri toplamak için yapılandırma gerekmez.|
    |**Test etkisi:** Bir test çalışması çalıştırıldığında, uygulama kodunuzun hangi yöntemlerinin kullanıldığı hakkında bilgi toplayabilirsiniz. Bu, hangi testlerin bu geliştirme değişikliklerinden etkilendiğini belirlemede, geliştiriciler tarafından yapılan uygulama kodundaki değişikliklerle birlikte kullanılabilir.|Test etkisi verileri, Yük Testleriyle toplanmaz.||
    |**Video kaydedicisi:** Otomatikleştirilmiş bir test çalıştırdığınızda masaüstü oturumunuzun bir video kaydını oluşturabilirsiniz. Bu, kodlanmış UI testi için kullanıcı eylemlerini görüntülemek için yararlı olabilir. Video, diğer takım üyelerinin yeniden oluşturulması zor olan uygulama sorunlarını yalıtmalarına yardımcı olabilir. **Note:**  Testleri uzaktan çalıştırırken, aracı etkileşimli işlem modunda çalışmadığı sürece video kaydedicisi çalışmaz.|![Önemli simge ](../test/media/vc364f3.gif) **uyarısı:**  yük testleri için video kaydedici bağdaştırıcısının kullanımını önermiyoruz.|[Nasıl yapılır: test ayarlarını kullanarak testler sırasında ekran ve ses kayıtlarını ekleme](../test/how-to-include-recordings-of-the-screen-and-voice-during-tests.md)|

19. **Dağıtım** seçin.

     **Dağıtım** sayfası görüntülenir.

20. Testlerinizi her çalıştırışınızda dağıtım için ayrı bir dizin oluşturmak için **dağıtımı etkinleştir**' i seçin.

    > [!NOTE]
    > Bunu yaparsanız, testlerinizi çalıştırdığınızda uygulamanızı oluşturmaya devam edebilirsiniz.

21. Testlerinizi çalıştırmak için kullandığınız dizine bir dosya eklemek için **Dosya Ekle**' yi seçin ve sonra eklemek istediğiniz dosyayı seçin.

    > [!NOTE]
    > Bir yük testi çalıştırdığınızda, eklenti derlemeleri, veri dosyaları ve karşıya yüklenen dosyalar otomatik olarak dağıtılır.

22. Testlerinizi çalıştırmak için kullandığınız dizine bir dizin eklemek için, **Dizin Ekle** ' yi seçin ve ardından eklemek istediğiniz dizini seçin.

23. Testlerinizin öncesinde ve sonrasında betikleri çalıştırmak için **Kurulum ve Temizleme betikleri**' ni seçin.

     **Kurulum ve Temizleme betikleri** sayfası görüntülenir.

    1. **Kurulum** betiği içindeki betik dosyasının konumunu yazın veya kurulum betiğini bulmak için üç nokta (**...**) simgesini seçin.

    2. **Temizleme** betiği içindeki betik dosyasının konumunu yazın veya temizleme betiğini bulmak için üç nokta (**...**) simgesini seçin.

24. Testlerinizi farklı bir ana bilgisayar kullanarak çalıştırmak için **konaklar**' ı seçin.

    1. **Ana bilgisayar türü**' nde, **varsayılan** seçeneğinin seçildiğini doğrulayın.

        > [!NOTE]
        > **Konak türündeki** **ASP.net** , yük testlerinde desteklenmez.

    2. Yük testinizde web performansının ve birim testlerinin, 32-bit veya 64-bit işlemler olarak çalışmasını isteyip istemediğinizi seçmek için, **32 bit veya 64 bit işlem içinde Testi Çalıştır** açılan öğesini kullanın.

        > [!NOTE]
        > En yüksek esneklik için, Web performans ve yük testi projelerinizi **herhangi BIR CPU** yapılandırmasını kullanarak derlemeniz gerekir. Ardından, 32-bit ve 64 bit aracılarında çalıştırabilirsiniz. **64 bit** yapılandırma kullanılarak Web performansı ve yük testi projelerini derlemek avantajsız bir avantaj sunar.

25. Seçim Her test çalıştırmasının ve bireysel testlerin zamanını sınırlandırmak için **test zaman aşımları** ' nı seçin.

    1. Bir zaman sınırı aşıldığında test çalıştırmasını iptal etmek için, **Toplam süre aşarsa test çalıştırmasını iptal** et ' i seçin ve ardından bu sınır için bir değer yazın.

    2. Bir zaman sınırı aşıldığında bireysel bir testi başarısız kılmak için, bir **testin yürütme süresi aşılırsa tek bir testi başarısız olarak işaretle** öğesini seçin ve bu sınır için bir değer yazın.

26. **Birim testini** atlayın. Yük testleri bu ayarları kullanmaz.

27. **Web testini** atlayın. Yük testleri bu ayarları kullanmaz.

28. Test ayarlarını kaydetmek için **farklı kaydet**' i seçin. **Nesne adı** alanına istediğiniz dosyanın adını yazın.

## <a name="remove-a-test-settings-file-from-your-solution"></a>Çözümünüzde bir test ayarları dosyasını kaldırma

**Çözüm Gezgini**' deki **Çözüm öğeleri** klasörü altında, kaldırmak istediğiniz test ayarlarını sağ tıklatın ve ardından **Kaldır**' ı seçin.

Test ayarları dosyası çözümünüzde kaldırılır.

## <a name="see-also"></a>Ayrıca bkz.

- [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)
- [Test ayarlarını kullanarak tanılama bilgilerini topla](../test/collect-diagnostic-information-using-test-settings.md)