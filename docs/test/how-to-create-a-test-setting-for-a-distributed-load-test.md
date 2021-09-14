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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634225"
---
# <a name="how-to-create-a-test-settings-file-for-a-distributed-load-test"></a>Nasıl kullanılır: Dağıtılmış yük testi için test ayarları dosyası oluşturma

Yük *testlerinizi* test ayarlarını, test aracılarını ve test denetleyicilerini kullanarak birden çok makineye dağıtacak şekilde yapılandırabilirsiniz. Ayrıca test ayarlarını, toplamak istediğiniz veri türleri veya yük testlerinizi bu bağdaştırıcılardan çalıştırıldığında test makinelerini nasıl etkileyeceğini belirten tanılama veri bağdaştırıcılarını Visual Studio.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Örneğin, kodun performans dökümünü ASP.NET için ASP.NET Profiler tanılama veri bağdaştırıcısını kullanabilirsiniz. Ayrıca, tanılama veri bağdaştırıcıları test makinesi üzerinde olası performans sorunlarının benzetimini yapmak veya kullanılabilir sistem belleğini azaltmak için kullanılabilir.

Test ayarları Visual Studio bir dosyada depolanır. Test ayarları her rol hakkında aşağıdaki bilgileri tanımlar:

- Test kapsamındaki uygulamanıza gereken roller kümesi

- Testlerinizi çalıştırmak için kullanabileceğiniz rol

- Her rol için kullanmak üzere tanılama veri bağdaştırıcıları

Testlerinizi çalıştırarak, belirli bir test çalıştırması için gerekenlere bağlı olarak etkin test ayarları olarak kullanmak üzere test ayarlarını seçersiniz. Test ayarları dosyası, çözüm bir parçası olarak depolanır. Dosya adı *.testsettings uzantısına sahip.*

Bir çözüme web performansı ve yük testi projesi eklerken bir *Default.testsettings* dosyası oluşturulur. Dosya çözüme Çözüm Öğeleri klasörü altında otomatik **olarak** eklenir. Bu dosya, testlerinizi herhangi bir tanılama veri bağdaştırıcısı olmadan yerel olarak çalıştırır. Başka bir *.testsettings dosyası ekleyebilir* veya tanılama veri bağdaştırıcılarını ve test denetleyicilerini belirtmek için *bir .testsettings* dosyasını düzenleyebilirsiniz.

Test denetleyicisi, test ayarlarınıza her rol için kullanılmaktadır aracılar içerir. Test denetleyicileri ve test aracıları hakkında daha fazla bilgi için bkz. Test denetleyicilerini ve [test aracılarını Visual Studio.](../test/manage-test-controllers-and-test-agents.md)

Bu adımları izleyin ve çözümde çalışmayı planlayılan yük testleri için test ayarlarını Visual Studio.

## <a name="create-a-test-settings-file"></a>Test ayarları dosyası oluşturma

1. Bu **Çözüm Gezgini,** Çözüm Öğeleri'ne **sağ tıklayın,** Ekle'nin üzerine **gelin** ve Yeni **Öğe'yi seçin.**

     **Yeni Öğe Ekle** iletişim kutusu görünür.

2. Yüklü **Şablonlar bölmesinde Test** şablonları'Ayarlar. 

3. (İsteğe bağlı) Ad **kutusunda** test ayarları dosyasının adını değiştirin.

4. **Ekle'yi seçin.**

     Yeni test ayarları dosyası, Çözüm Gezgini **Öğeleri** klasörünün **altında görüntülenir.**

5. **Test Ayarlar** iletişim kutusu görüntülenir. Genel **sayfası** seçilidir.

     Artık test ayarları değerlerini düzenleyebilir ve kaydedebilirsiniz.

6. **Ad'ın** altına test ayarlarının adını yazın.

7. (İsteğe bağlı) **Açıklama'nın** altına test ayarı için bir açıklama yazın, böylece diğer ekip üyeleri bunun amacını bilirsiniz.

8. (İsteğe bağlı) Test çalıştırmalarınız için varsayılan adlandırma düzenini seçmek için Varsayılan adlandırma **şeması'ı seçin.** Kendi adlandırma düzeninizi tanımlamak için Kullanıcı **tanımlı düzen'i seçin** ve ardından Önek metni'ne **istediğiniz metni yazın.** Test çalıştırması adına tarih ve saat damgası eklemek için Tarih-saat **damgasını ekle'yi seçin.**

9. **Roller'i seçin.**

     **Roller** sayfası görüntülenir.

     ![Test ayarı rolü](../test/media/load_testtestrole.png)

10. Testlerinizi uzaktan çalıştırmak veya testlerinizi uzaktan çalıştırmak ve verileri uzaktan toplamak için **Test yürütme yöntemi** açılan listesinden Uzaktan yürütme'yi **seçin.**

11. Denetleyici açılır **listesinden** Test aracıları için testlerinizi  çalıştırmak veya veri toplamak için kullanılacak bir test denetleyicisi seçin.

    > [!NOTE]
    > Denetleyiciyi ilk kez ekliyorsanız, aşağı açılan listede hiçbir denetleyici listelenmiyor. Liste, diğer test ayarlarında belirttiğiniz önceki denetleyiciler tarafından doldurulur. Kutuya denetleyicinin adını yazmanız gerekir (örneğin, **TestControllerMachine1**).

12. Testleri çalıştırmak ve veri toplamak için kullanmak istediğiniz rolleri eklemek için Roller'in **altında** Ekle'yi **seçin.**

13. Ad sütununa rol için bir **ad** yazın. Örneğin, rol "Web Sunucusu" olabilir.

14. İstediğiniz tüm rolleri eklemek için 12. ve 13. adımları tekrarlayın.

     Her rol, test denetleyicisi tarafından yönetilen bir test aracısı kullanır.

15. Testlerinizi çalıştırmak istediğiniz rolü seçin ve ardından Testleri çalıştırmak için **Rol olarak ayarla'ya seçin.**

    > [!IMPORTANT]
    > Sizin oluşturladığınız ve tanımladığınız diğer roller testleri çalıştırmaz, ancak yalnızca Veri ve Tanılama sayfasındaki roller için belirttiğiniz verilere ve tanılama bağdaştırıcılara göre **veri toplamak için** kullanılır.

16. Bir rol için kullanılan aracıları sınırlamak için  rolü seçin ve ardından seçili rolün Aracı öznitelikleri'nin altındaki **araç çubuğunda Ekle'yi seçin.**

     Aracı **Seçim Kuralı** iletişim kutusu görüntülenir.

     Öznitelik **Adı'nın adını ve** Öznitelik Değeri'ne değeri **yazın** ve ardından Tamam'ı **seçin.** Gereken sayıda öznitelik ekleyin.

     Örneğin, 16 GB'den fazla belleğe sahip test aracısı makinelerini filtrelemek için "True" veya "False" değerine sahip olan "RAM > 16 GB" adlı bir öznitelik eklersiniz. Aynı özniteliği bir veya daha fazla test aracısına uygulamak için Test Denetleyicisini **Yönet iletişim kutusunu** kullanın. Daha fazla bilgi için [bkz. Test denetleyicilerini ve test aracılarını Visual Studio.](../test/manage-test-controllers-and-test-agents.md)

17. Veri **ve Tanılama'yı seçin.**

     **Veri ve Tanılama** sayfası görüntülenir.

     ![Test ayarı verileri ve tanılama](../test/media/load_testtest.png)

18. Veri **ve Tanılama sayfasında,** rolün veri toplamak için  kullanabileceği tanılama veri bağdaştırıcılarını seçerek rolün ne yaptığını tanımlarsiniz. Bu nedenle, rol için bir veya daha fazla veri ve tanılama bağdaştırıcısı etkinleştirilirse, test denetleyicisi, rol için tanımlandığı öznitelikleri temel alarak belirtilen veriler ve tanılama bağdaştırıcıları için veri toplamak üzere kullanılabilir bir test aracısı makinesi seçer. Her rol için toplamak istediğiniz veri ve tanılama veri bağdaştırıcılarını seçmek için rolü seçin. Her rol için, testlerin ihtiyaçlarına göre tanılama veri bağdaştırıcılarını seçin. Her rol için seçtiğiniz her tanılama veri bağdaştırıcısını yapılandırmak için Yapılandır'ı **seçin.**

     **Rol ve tanılama veri bağdaştırıcıları örneği:**

     Örneğin, "SQL" özniteliği "True" olarak ayarlanmış "Masaüstü İstemcisi" adlı bir istemci rolü ve "RAM > 16 GB" olarak ayarlanmış bir öznitelike sahip "SQL Server" adlı bir sunucu rolü oluşturabilirsiniz. "Masaüstü İstemcisi"nin, Roller sayfasında Testleri  çalıştırmak için rol olarak  ayarla seçeneğini belirterek testleri çalıştıracaklarını belirtirse, test denetleyicisi testleri çalıştıracak "Uses SQL" özniteliğini içeren test aracıları olan makineleri seçer. Test denetleyicisi ayrıca SQL yalnızca role dahil olan veri ve tanılama bağdaştırıcıları tarafından tanımlanan verileri toplamak için "RAM > 16 GB" özniteliğini içeren test aracıları olan sunucu makinelerini de seçer. "Masaüstü İstemcisi" test aracısı, bu rol için veri ve tanılama bağdaştırıcıları da seçmenizde çalıştırıldık makineler için veri toplayabilirsiniz.

     Tanılama veri bağdaştırıcılarının her biri ve nasıl yapılandırıldıklarının ayrıntıları için aşağıdaki tabloda ilişkilendirilmiş konuyu görüntüebilirsiniz.

     Tanılama veri bağdaştırıcıları hakkında daha fazla bilgi için [bkz. Test ayarlarını kullanarak tanılama bilgilerini toplama.](../test/collect-diagnostic-information-using-test-settings.md)

     **Yük Testleri için Tanılama Veri Bağdaştırıcıları**

    |Tanılama veri bağdaştırıcısı|Yük testlerinde kullanma|İlişkili konu|
    |-|-------------------------|-|
    |**ASP.NET IntelliTrace ve Test Etkisi için İstemci Ara Sunucusu:** Bu ara sunucu, IntelliTrace ve Test Etkisi tanılama veri bağdaştırıcıları için bir istemciden web sunucusuna yapılan http çağrıları hakkında bilgi toplamaya olanak sağlar.|![Bilgi simgesi](../test/media/vc364f4.gif)<br /><br /> Test aracısı makineleri için sistem bilgilerini toplamaya özel bir ihtiyacınız yoksa, bu bağdaştırıcıyı dahil edin. **Dikkat:**  Toplanan büyük miktarda veri nedeniyle oluşan sorunlar nedeniyle yük testlerinde IntelliTrace bağdaştırıcısının kullanılması önerilmez. <br /><br /> Yük testleri kullanılarak test etkisi verileri toplanmaz.||
    |**IntelliTrace:** Bir günlük dosyasında depolanan belirli tanılama izleme bilgilerini yapılandırabilirsiniz. Günlük dosyasının uzantısı *.tdlog'dır.* Testlerinizi çalıştırarak bir test adımı başarısız olduğunda hata oluşturabilirsiniz. Tanılama izlemesi içeren günlük dosyası bu hataya otomatik olarak eklenir. Günlük dosyasında toplanan veriler, kodda bir hatayı yeniden oluşturmak ve tanılamak için gereken zamanı azaltarak hata ayıklama üretkenliğini artırır. Bu günlük dosyasından yerel oturum başka bir bilgisayarda yeniden oluşturulabilirsiniz. Bu, bir hatanın yeniden üretilenema riskini azaltır.<br /><br /> Daha fazla bilgi için [bkz. IntelliTrace verilerini toplama.](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)|![Önemli simgesi](../test/media/vc364f3.gif)<br /><br /> Toplanan ve günlüğe kaydedilen büyük miktarda veri nedeniyle oluşan sorunlar nedeniyle yük testlerinde IntelliTrace bağdaştırıcısının kullanılması önerilmez. IntelliTrace bağdaştırıcısını yalnızca uzun süre çalışan ve çok sayıda test aracısı kullanmayan yük testlerinde kullanmayı denemeniz gerekir.|[Nasıl kullanılır: Zor sorunlarda hata ayıklamaya yardımcı olmak için IntelliTrace verileri toplama](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)|
    |**ASP.NET Profiler:** Web uygulamalarında performans verilerini toplayan ASP.NET içeren bir test ASP.NET oluşturabilirsiniz.|Bu ASP.NET profil oluşturma tanılama veri bağdaştırıcısı, Internet Information Services (IIS) işleminin profilini profiller, bu nedenle geliştirme web sunucusuna karşı çalışmaz. Yük testinde web sitesinin profilini oluşturmak için IIS'nin üzerinde çalıştır olduğu makineye bir test aracısı yüklemeniz gerekir. Test aracısı yük oluşturmaz, ancak yalnızca bir koleksiyon aracısı olur. Daha fazla bilgi için [bkz. Test aracılarını yükleme ve yapılandırma.](../test/lab-management/install-configure-test-agents.md)|[Nasıl yapabilirsiniz: Test ASP.NET yük testleri için profil profilleyici yapılandırma](../test/how-to-configure-aspnet-profiler-for-load-tests-using-test-settings.md)|
    |**Olay günlüğü:** Test sonuçlarına dahil edilecek olay günlüğü toplamayı içerecek şekilde bir test ayarı yapılandırabilirsiniz.||[Nasıl yapabilirsiniz: Test ayarlarını kullanarak olay günlüğü toplamayı yapılandırma](/previous-versions/dd504816(v=vs.110))|
    |**Ağ Öykünmesi:** Test ayarı kullanarak teste yapay ağ yükü koymak istediğiniz belirtebilirsiniz. Ağ öykünmesi, çevirmeli bağlantı gibi belirli bir ağ bağlantı hızı öykünerek makineye gelen ve makineden gelen iletişimi etkiler. **Not:**  Ağ öykünmesi, ağ bağlantı hızını artırmak için kullanılamaz.|Ağ Öykünme bağdaştırıcısı yük testleri tarafından yoksayılır. Bunun yerine, yük testleri yük testi senaryosunun ağ karışımında belirtilen ayarları kullanır.<br /><br /> Daha fazla bilgi için [bkz. Sanal ağ türlerini belirtme.](../test/specify-virtual-network-types-in-a-load-test-scenario.md)||
    |**Sistem Bilgileri:** Tanılama ve veri toplayıcının üzerinde çalıştırıldıkları makineler hakkında sistem bilgilerini Sistem Bilgileri bir test ayarı ayarlanabilir. Sistem bilgileri, bir test ayarı kullanılarak test sonuçlarında belirtilir.|![Bilgi simgesi](../test/media/vc364f4.gif)<br /><br /> Hem yük aracılarından hem de test altındaki sistemden sistem bilgilerini toplayabilirsiniz.|Bu bilgileri toplamak için yapılandırma gerekmez.|
    |**Test Etkisi:** Bir test çalışması çalıştıryken uygulama kodunuzun hangi yöntemlerinin kullanıldıkları hakkında bilgi toplayabilirsiniz. Bu, hangi testlerin bu geliştirme değişikliklerinden etkilendiğini belirlemek için geliştiriciler tarafından yapılan uygulama kodu değişiklikleriyle birlikte kullanılabilir.|Yük testleriyle test etkisi verileri toplanmaz.||
    |**Video Recorder:** Otomatikleştirilmiş bir test çalıştırarak masaüstü oturumunuz için bir video kaydı oluşturabilirsiniz. Bu, kodlanmış ui testi için kullanıcı eylemlerini görüntülemek için yararlı olabilir. Video, diğer ekip üyelerinin yeniden oluşturması zor uygulama sorunlarını yalıtmalarına yardımcı olabilir. **Not:**  Testleri uzaktan çalıştıracaksanız, aracı etkileşimli işlem modunda çalışmadıkça video kaydedici çalışmaz.|![Önemli simgesi ](../test/media/vc364f3.gif) **Uyarı:**  Yük testleri için Video Recorder bağdaştırıcısının kullanılması önerilmez.|[Nasıl kullanılır: Test ayarlarını kullanarak testler sırasında ekran ve ses kayıtlarını dahil edin](../test/how-to-include-recordings-of-the-screen-and-voice-during-tests.md)|

19. **Dağıtım'ı seçin.**

     **Dağıtım** sayfası görüntülenir.

20. Testlerinizi her çalıştırarak dağıtım için ayrı bir dizin oluşturmak için Dağıtımı **etkinleştir'i seçin.**

    > [!NOTE]
    > Bunu yaparsanız, testlerinizi çalıştırarak uygulamalarınızı derlemeye devam edersiniz.

21. Testlerinizi çalıştırmak için kullanmakta olduğu dizine dosya eklemek için Dosya ekle'yi **ve** ardından eklemek istediğiniz dosyayı seçin.

    > [!NOTE]
    > Bir yük testleri çalıştırıldığında, eklenti derlemeleri, veri dosyaları ve karşıya yüklenen dosyalar otomatik olarak dağıtılır.

22. Testlerinizi çalıştırmak için kullanmakta olduğu dizine bir dizin eklemek için Dizin ekle'yi **ve** ardından eklemek istediğiniz dizini seçin.

23. Testlerden önce ve sonra betikleri çalıştırmak için Kurulum ve Temizleme **Betikleri'ne tıklayın.**

     Kurulum **ve Temizleme Betikleri** sayfası görüntülenir.

    1. Kurulum betiğine betik dosyasının **konumunu yazın** veya kurulum betiği bulmak için üç noktayı (**...**) seçin.

    2. Temizleme betiğine betik dosyasının **konumunu yazın** veya temizleme betiği bulmak için üç noktayı (**...**) seçin.

24. Testlerinizi farklı bir konak kullanarak çalıştırmak için Konaklar'ı **seçin.**

    1. Konak **Türü'ne** Varsayılan'ın **seçili** olduğunu doğrulayın.

        > [!NOTE]
        > Konak **ASP.NET,yük** testlerinde desteklanmaz. 

    2. Yük testinde web performansının ve birim testlerinin **32 bit veya 64 bit** işlemler olarak çalıştırıp çalıştırmamalarını seçmek için Testi 32 bit veya 64 bit işlemle çalıştır açılan listesinden seçim yapmak için kullanın.

        > [!NOTE]
        > En yüksek esneklik için, Herhangi bir CPU yapılandırmasını kullanarak web performansınızı ve yük testi **projelerinizi derlemeniz** gerekir. Ardından hem 32 bit hem de 64 bit aracılar üzerinde çalıştırarak. **64 bit** yapılandırmayı kullanarak web performansı ve yük testi projelerini derlemenin hiçbir avantajı yoktur.

25. (İsteğe bağlı) Her test çalıştırması ve tek tek testlerin zamanlarını sınırlamak için Test Zaman **Aşımı'ı seçin.**

    1. Bir zaman sınırı aşılırken test çalıştırmalarını durdurmak için, Toplam sürenin aşılırsa **test** çalıştırmalarını durdur'ı seçin ve ardından bu sınır için bir değer yazın.

    2. Bir zaman sınırı aşılırken tek bir testi başarısız yapmak için, Yürütme süresi değerini aşarsa tek bir **testi** başarısız olarak işaretle'yi seçin ve bu sınır için bir değer yazın.

26. Birim **Testini Atla**. Yük testleri bu ayarları kullanmaz.

27. **Web Testini Atla**. Yük testleri bu ayarları kullanmaz.

28. Test ayarlarını kaydetmek için Farklı **Kaydet'i seçin.** Nesne adı'nın içinde istediğiniz **dosyanın adını yazın.**

## <a name="remove-a-test-settings-file-from-your-solution"></a>Çözümünüzden test ayarları dosyasını kaldırma

içinde **Çözüm Öğeleri** **klasörünün Çözüm Gezgini,** kaldırmak istediğiniz test ayarlarına sağ tıklayın ve kaldır'ı **seçin.**

Test ayarları dosyası çözümünüzden kaldırılır.

## <a name="see-also"></a>Ayrıca bkz.

- [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)
- [Test ayarlarını kullanarak tanılama bilgilerini toplama](../test/collect-diagnostic-information-using-test-settings.md)