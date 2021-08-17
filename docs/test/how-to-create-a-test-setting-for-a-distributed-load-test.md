---
title: Dağıtılmış Yük Testi için Test Ayarı Oluşturma
description: Test aracılarını ve test denetleyicilerini kullanarak bu testleri birden çok makineye dağıtacak şekilde yük testlerinizi test ayarlarını yapılandırmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- test settings, for distributed load tests
ms.assetid: b63d4b71-3b74-4872-b2d1-f0bd1a9a8544
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 7e08163be95d2249b091ce40072d54111e35ef2b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122033284"
---
# <a name="how-to-create-a-test-settings-file-for-a-distributed-load-test"></a>Nasıl kullanılır: Dağıtılmış yük testi için test ayarları dosyası oluşturma

Test *aracılarını ve* test denetleyicilerini kullanarak bu testleri birden çok makineye dağıtacak şekilde yük testlerinizi test ayarlarını yapılandırma. Ayrıca, toplamak istediğiniz veri türleri veya yük testlerinizi yük testlerinizi çalıştırıldığında test makinelerini nasıl etkileyeceğini belirten tanılama veri bağdaştırıcılarını kullanmak için test ayarlarını Visual Studio.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Örneğin, kodun performans dökümünü ASP.NET için ASP.NET Profiler tanılama veri bağdaştırıcısını kullanabilirsiniz. Ayrıca tanılama veri bağdaştırıcıları, test makinesi üzerinde olası performans sorunlarının benzetimini yapmak veya kullanılabilir sistem belleğini azaltmak için kullanılabilir.

Test ayarları Visual Studio bir dosyada depolanır. Test ayarları her rol hakkında aşağıdaki bilgileri tanımlar:

- Test kapsamındaki uygulamanıza gereken roller kümesi

- Testlerinizi çalıştırmak için kullanabileceğiniz rol

- Her rol için kullanmak üzere tanılama veri bağdaştırıcıları

Testlerinizi çalıştırarak, belirli bir test çalıştırması için gerekenlere bağlı olarak etkin test ayarları olarak kullanmak üzere test ayarlarını seçersiniz. Test ayarları dosyası çözümünüz kapsamında depolanır. Dosya adı *.testsettings uzantısına sahip.*

Bir çözüme web performansı ve yük testi projesi eklerken bir *Default.testsettings* dosyası oluşturulur. Dosya çözüme Çözüm Öğeleri klasörü altında otomatik **olarak** eklenir. Bu dosya, testlerinizi herhangi bir tanılama veri bağdaştırıcısı olmadan yerel olarak çalıştırır. Başka bir *.testsettings dosyası ekleyebilir* veya tanılama veri bağdaştırıcılarını ve test denetleyicilerini belirtmek için *bir .testsettings* dosyasını düzenleyebilirsiniz.

Test denetleyicisi, test ayarlarınıza her rol için kullanılmaktadır aracılar içerir. Test denetleyicileri ve test aracıları hakkında daha fazla bilgi için bkz. Test denetleyicilerini ve [test aracılarını Visual Studio.](../test/manage-test-controllers-and-test-agents.md)

Bu adımları izleyin ve çözümde çalışmayı planlayılan yük testleri için çözümde test ayarlarını Visual Studio.

## <a name="create-a-test-settings-file"></a>Test ayarları dosyası oluşturma

1. Bu **Çözüm Gezgini,** Çözüm Öğeleri'ne **sağ tıklayın,** Ekle'nin üzerine **gelin ve** Yeni **Öğe'yi seçin.**

     **Yeni Öğe Ekle** iletişim kutusu görünür.

2. Yüklü **Şablonlar bölmesinde Test** şablonu'Ayarlar. 

3. (İsteğe bağlı) Ad **kutusunda** test ayarları dosyasının adını değiştirin.

4. **Ekle'yi seçin.**

     Yeni test ayarları dosyası, **Çözüm Gezgini** Öğeleri klasörünün **altında görüntülenir.**

5. **Test Ayarlar** iletişim kutusu görüntülenir. Genel **sayfası** seçilidir.

     Artık test ayarları değerlerini düzenleyebilir ve kaydedebilirsiniz.

6. **Ad'ın** altına test ayarlarının adını yazın.

7. (İsteğe bağlı) **Açıklama'nın** altına test ayarı için bir açıklama yazın, böylece diğer ekip üyeleri bunun amacını bilirsiniz.

8. (İsteğe bağlı) Test çalıştırmalarınız için varsayılan adlandırma düzenini seçmek için Varsayılan adlandırma **şeması'ı seçin.** Kendi adlandırma düzeninizi tanımlamak için Kullanıcı **tanımlı düzen'i seçin** ve ardından Önek metni'ne **istediğiniz metni yazın.** Test çalıştırması adına tarih ve saat damgası eklemek için Tarih-saat **damgasını ekle'yi seçin.**

9. **Roller'i seçin.**

     Roller  sayfası görüntülenir.

     ![Test ayarı rolü](../test/media/load_testtestrole.png)

10. Testlerinizi uzaktan çalıştırmak veya testlerinizi uzaktan çalıştırmak ve verileri uzaktan toplamak için **Test yürütme yöntemi** açılan listesinden Uzaktan yürütme'yi **seçin.**

11. Denetleyici açılır **listesinden** Test aracıları için testlerinizi  çalıştırmak veya veri toplamak için kullanılacak bir test denetleyicisi seçin.

    > [!NOTE]
    > Denetleyiciyi ilk kez ekliyorsanız, aşağı açılan listede hiçbir denetleyici listelenmiyor. Liste, diğer test ayarlarında belirttiğiniz önceki denetleyiciler tarafından doldurulur. Kutuya denetleyicinin adını yazmanız gerekir (örneğin, **TestControllerMachine1**).

12. Testleri çalıştırmak ve veri toplamak için kullanmak istediğiniz rolleri eklemek için Roller'in **altında** Ekle'yi **seçin.**

13. Ad sütununa rol için bir **ad** yazın. Örneğin, rol "Web Sunucusu" olabilir.

14. Size gereken tüm rolleri eklemek için 12. ve 13. adımları tekrarlayın.

     Her rol, test denetleyicisi tarafından yönetilen bir test aracısı kullanır.

15. Testlerinizi çalıştırmak istediğiniz rolü seçin ve ardından Testleri çalıştırmak için **Rol olarak ayarla'ya seçin.**

    > [!IMPORTANT]
    > Sizin oluşturladığınız ve tanımladığınız diğer roller testleri çalıştırmaz, ancak yalnızca Veri ve Tanılama sayfasındaki roller için belirttiğiniz verilere ve tanılama bağdaştırıcılara göre **veri toplamak için** kullanılır.

16. Bir rol için kullanılan aracıları sınırlamak için  rolü seçin ve ardından seçili rolün Aracı öznitelikleri'nin **altındaki araç çubuğunda Ekle'yi seçin.**

     Aracı **Seçim Kuralı** iletişim kutusu görüntülenir.

     Öznitelik **Adı'nın adını ve** Öznitelik Değeri'ne değeri **yazın** ve ardından Tamam'ı **seçin.** Gereken sayıda öznitelik ekleyin.

     Örneğin, 16 GB'den fazla belleğe sahip test aracısı makinelerini filtrelemek için "True" veya "False" değerine sahip olan "RAM > 16 GB" adlı bir öznitelik eklersiniz. Aynı özniteliği bir veya daha fazla test aracısına uygulamak için Test Denetleyicisini **Yönet iletişim kutusunu** kullanın. Daha fazla bilgi için [bkz. Test denetleyicilerini ve test aracılarını Visual Studio.](../test/manage-test-controllers-and-test-agents.md)

17. Veri **ve Tanılama'yı seçin.**

     **Veri ve Tanılama** sayfası görüntülenir.

     ![Test ayarı verileri ve tanılama](../test/media/load_testtest.png)

18. Veri **ve Tanılama sayfasında,** rolün veri toplamak için  kullanabileceği tanılama veri bağdaştırıcılarını seçerek rolün ne yaptığını tanımlarsiniz. Bu nedenle, rol için bir veya daha fazla veri ve tanılama bağdaştırıcısı etkinleştirilirse, test denetleyicisi, rol için tanımlandığı öznitelikleri temel alarak belirtilen veriler ve tanılama bağdaştırıcıları için veri toplamak üzere kullanılabilir bir test aracısı makinesi seçer. Her rol için toplamak istediğiniz veri ve tanılama veri bağdaştırıcılarını seçmek için rolü seçin. Her rol için, testlerin ihtiyaçlarına göre tanılama veri bağdaştırıcılarını seçin. Her rol için seçtiğiniz her tanılama veri bağdaştırıcısını yapılandırmak için Yapılandır'ı **seçin.**

     **Rol ve tanılama veri bağdaştırıcıları örneği:**

     Örneğin, "SQL kullanır" özniteliği "True" olarak ayarlanmış "Masaüstü İstemcisi" adlı bir istemci rolü ve "RAM > 16 GB" olarak ayarlanmış bir öznitelike sahip "SQL Server" adlı bir sunucu rolü oluşturabilirsiniz. "Masaüstü İstemcisi"nin, Roller sayfasında Testleri  çalıştırmak için rol olarak  ayarla'yi seçerek testleri çalıştıracaklarını belirtirse, test denetleyicisi testleri çalıştıracak "Uses SQL" özniteliğini içeren test aracıları olan makineleri seçer. Test denetleyicisi ayrıca yalnızca role dahil olan veri ve tanılama bağdaştırıcıları tarafından tanımlanan verileri toplamak için "RAM > 16 GB" özniteliğini içeren test aracıları olan SQL sunucu makinelerini de seçer. "Masaüstü İstemcisi" test aracısı, bu rol için veri ve tanılama bağdaştırıcıları da seçmenizde çalıştırıldık makineler için veri toplayabilirsiniz.

     Tanılama veri bağdaştırıcılarının her biri ve nasıl yapılandırıldıklarının ayrıntıları için aşağıdaki tabloda ilişkilendirilmiş konuyu görüntüebilirsiniz.

     Tanılama veri bağdaştırıcıları hakkında daha fazla bilgi için [bkz. Test ayarlarını kullanarak tanılama bilgilerini toplama.](../test/collect-diagnostic-information-using-test-settings.md)

     **Yük Testleri için Tanılama Veri Bağdaştırıcıları**

    |Tanılama veri bağdaştırıcısı|Yük testlerinde kullanma|İlişkili konu|
    |-|-------------------------|-|
    |**ASP.NET IntelliTrace ve Test Etkisi için İstemci Ara Sunucusu:** Bu ara sunucu, IntelliTrace ve Test Etkisi tanılama veri bağdaştırıcıları için istemciden web sunucusuna yapılan http çağrıları hakkında bilgi toplamaya olanak sağlar.|![Bilgi simgesi](../test/media/vc364f4.gif)<br /><br /> Test aracısı makineleri için sistem bilgilerini toplamaya özel bir ihtiyacınız yoksa, bu bağdaştırıcıyı dahil edin. **Dikkat:**  Toplanan büyük miktarda veri nedeniyle oluşan sorunlar nedeniyle yük testlerinde IntelliTrace bağdaştırıcısının kullanılması önerilmez. <br /><br /> Yük testleri kullanılarak test etkisi verileri toplanmaz.||
    |**IntelliTrace:** Bir günlük dosyasında depolanan belirli tanılama izleme bilgilerini yapılandırabilirsiniz. Günlük dosyasının uzantısı *.tdlog'dır.* Testlerinizi çalıştırarak bir test adımı başarısız olduğunda hata oluşturabilirsiniz. Tanılama izlemesi içeren günlük dosyası bu hataya otomatik olarak eklenir. Günlük dosyasında toplanan veriler, kodda bir hatayı yeniden oluşturmak ve tanılamak için gereken zamanı azaltarak hata ayıklama üretkenliğini artırır. Bu günlük dosyasından yerel oturum başka bir bilgisayarda yeniden oluşturulabilirsiniz. Bu, bir hatanın yeniden üretilenema riskini azaltır.<br /><br /> Daha fazla bilgi için [bkz. IntelliTrace verilerini toplama.](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)|![Önemli simgesi](../test/media/vc364f3.gif)<br /><br /> Toplanan ve günlüğe kaydedilen büyük miktarda veri nedeniyle oluşan sorunlar nedeniyle yük testlerinde IntelliTrace bağdaştırıcısının kullanılması önerilmez. IntelliTrace bağdaştırıcısını yalnızca uzun süre çalışan ve çok sayıda test aracısı kullanmayan yük testlerinde kullanmayı denemeniz gerekir.|[Nasıl kullanılır: Zor sorunlarda hata ayıklamaya yardımcı olmak için IntelliTrace verileri toplama](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)|
    |**ASP.NET Profiler:** Web uygulamalarında performans verilerini toplayan ASP.NET profil oluşturmayı içeren bir test ASP.NET oluşturabilirsiniz.|Bu ASP.NET profil oluşturma tanılama veri bağdaştırıcısı, Internet Information Services (IIS) işlemini profiller, bu nedenle geliştirme web sunucusuna karşı çalışmaz. Yük testinde web sitesinin profilini oluşturmak için IIS'nin üzerinde çalıştırıldı olduğu makineye bir test aracısı yüklemeniz gerekir. Test aracısı yük oluşturmaz, ancak yalnızca bir koleksiyon aracısı olur. Daha fazla bilgi için [bkz. Test aracılarını yükleme ve yapılandırma.](../test/lab-management/install-configure-test-agents.md)|[nasıl yapılır: test ayarlarını kullanarak yük testleri için ASP.NET profil oluşturucuyu yapılandırma](../test/how-to-configure-aspnet-profiler-for-load-tests-using-test-settings.md)|
    |**Olay günlüğü:** Test sonuçlarına dahil edilecek olay günlüğü toplamayı dahil etmek için bir test ayarı yapılandırabilirsiniz.||[Nasıl yapılır: test ayarlarını kullanarak olay günlüğü koleksiyonunu yapılandırma](/previous-versions/dd504816(v=vs.110))|
    |**Ağ öykünmesi:** Test ayarı kullanarak testinize yapay bir ağ yükü koymak istediğinizi belirtebilirsiniz. Ağ öykünmesi, çevirmeli gibi belirli bir ağ bağlantı hızına öykünüyerek makineye ve makineden iletişimi etkiler. **Note:**  Ağ öykünmesi, ağ bağlantısı hızını artırmak için kullanılamaz.|Ağ öykünmesi bağdaştırıcısı, yük testleri tarafından yok sayılır. Bunun yerine, yük testleri yük testi senaryosunun ağ karışımında belirtilen ayarları kullanır.<br /><br /> Daha fazla bilgi için bkz. [sanal ağ türlerini belirtme](../test/specify-virtual-network-types-in-a-load-test-scenario.md).||
    |**Sistem Bilgileri:** Sistem Bilgileri tanılama ve veri toplayıcısının çalıştırıldığı makineler hakkında sistem bilgilerini içerecek şekilde bir test ayarı ayarlanabilir. Sistem bilgileri, test ayarları kullanılarak test sonuçlarında belirtilir.|![Bilgi simgesi](../test/media/vc364f4.gif)<br /><br /> Sistem bilgilerini hem yük aracılarından hem de test altındaki sistemden toplayabilirsiniz.|Bu bilgileri toplamak için yapılandırma gerekmez.|
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
        > **konak türündeki** **ASP.NET** yük testlerinde desteklenmez.

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