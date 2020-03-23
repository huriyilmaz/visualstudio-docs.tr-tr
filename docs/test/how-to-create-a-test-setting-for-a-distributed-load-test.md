---
title: Dağıtılmış Yük Testi için Test Ayarı Oluşturma
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, for distributed load tests
ms.assetid: b63d4b71-3b74-4872-b2d1-f0bd1a9a8544
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3129aa5139533db0783c168c3489e071fe9339b5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589159"
---
# <a name="how-to-create-a-test-settings-file-for-a-distributed-load-test"></a>Nasıl yapılır: Dağıtılmış yük testi için test ayarları dosyası oluşturma

Test *aracıları* ve test denetleyicileri kullanarak bu testleri birden çok makineye dağıtabilmek için yük testleriniz için test ayarlarını yapılandırın. Ayrıca, visual studio'dan yük testlerinizi çalıştırdığınızda toplamak istediğiniz veri türlerini veya test makinelerini nasıl etkileyeceğinizi belirten *tanılama veri bağdaştırıcılarını*kullanacak şekilde test ayarlarını yapılandırabilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Örneğin, kodun performans dökümünü toplamak için ASP.NET Profiler tanıveri bağdaştırıcısını kullanabilirsiniz. Ayrıca, tanılama veri bağdaştırıcıları test makinesindeki olası darboğazları simüle etmek veya kullanılabilir sistem belleği azaltmak için kullanılabilir.

Visual Studio için test ayarları bir dosyada depolanır. Test ayarları her rol hakkında aşağıdaki bilgileri tanımlar:

- Test altında uygulamanız için gerekli olan roller kümesi

- Testlerinizi çalıştırmak için kullanılacak rol

- Her rol için kullanılacak tanısal veri bağdaştırıcıları

Testlerinizi çalıştırdığınızda, söz konusu test çalışması için ne istediğinize bağlı olarak etkin test ayarları olarak kullanılacak test ayarlarını seçersiniz. Test ayarları dosyası çözümünuzun bir parçası olarak depolanır. Dosya adı uzantısı *.test ayarları*vardır.

Bir çözüme bir web performansı ve yük testi projesi eklediğinizde, *Varsayılan.test ayarları* dosyası oluşturulur. Dosya, **Çözüm Öğeleri** klasörü altındaki çözüme otomatik olarak eklenir. Bu dosya, herhangi bir tanılama veri bağdaştırıcısı olmadan testlerinizi yerel olarak çalıştırın. Başka bir *.test ayarları* dosyası ekleyebilir veya tanılama veri bağdaştırıcıları ve test denetleyicileri belirtmek için bir *.test ayarları* dosyasını değiştirebilirsiniz.

Test denetleyicisinde, test ayarlarınızdaki her rol için kullanılabilecek aracılar bulunur. Test denetleyicileri ve test aracıları hakkında daha fazla bilgi için [Visual Studio ile test denetleyicilerini ve test aracılarını yönet'e](../test/manage-test-controllers-and-test-agents.md)bakın.

Visual Studio'dan çalıştırmayı planladığınız yük testleri için çözümünüzde test ayarlarını oluşturmak ve kaldırmak için aşağıdaki adımları izleyin.

## <a name="create-a-test-settings-file"></a>Test ayarları dosyası oluşturma

1. **Çözüm Gezgini'nde**, **Çözüm Öğeleri'ni**sağ tıklatın , **Ekle'ye**işaret edin ve ardından **Yeni Öğe'yi**seçin.

     **Yeni Öğe Ekle** iletişim kutusu görünür.

2. Yüklü **Şablonlar** **bölmesinde, Test Ayarları'nı**seçin.

3. (İsteğe bağlı) **Ad** kutusunda, test ayarları dosyasının adını değiştirin.

4. **Ekle'yi**seçin.

     Yeni test ayarları dosyası **Çözüm Gezgini'nde**, **Çözüm Öğeleri** klasöründe görünür.

5. **Test Ayarları** iletişim kutusu görüntülenir. **Genel** sayfa seçilir.

     Artık test ayarları değerlerini disep kaydedebilirsiniz.

6. **Ad**altında, test ayarları için adı yazın.

7. (İsteğe bağlı) **Açıklama**altında, diğer ekip üyelerinin ne amaçlandığını bilmesi için test ayarı için bir açıklama yazın.

8. (İsteğe bağlı) Test çalışır için varsayılan adlandırma düzenini seçmek için **Varsayılan adlandırma düzenini**seçin. Kendi adlandırma düzeninizi tanımlamak **için, Kullanıcı tanımlı düzeni** seçin ve ardından **Önek metninde**istediğiniz metni yazın. Test çalıştırma adına tarih ve saat damgasını eklemek **için, Ek tarih-saat damgasını**seçin.

9. **Rolleri**Seçin.

     **Roller** sayfası görüntülenir.

     ![Test ayarı rolü](../test/media/load_testtestrole.png)

10. Testlerinizi uzaktan çalıştırmak veya testlerinizi uzaktan çalıştırmak ve verileri uzaktan toplamak için, **Test yürütme yöntemiaçılır** ve **Uzaktan yürütmeyi**seçin.

11. **Testlerinizi** çalıştırmak veya veri toplamak için kullanılacak Denetleyici'den test aracıları için bir test denetleyicisi seçmek için **Denetleyici** açılır masını kullanın.

    > [!NOTE]
    > İlk kez bir denetleyici ekliyorsanız, açılan listede hiçbir denetleyici listelenmez. Liste, diğer test ayarlarında belirttiğiniz önceki denetleyiciler tarafından doldurulur. Kutuya denetleyicinin adını yazmanız gerekir (örneğin, **TestControllerMachine1).**

12. Testleri çalıştırmak ve veri toplamak için kullanmak istediğiniz rolleri eklemek için **Roller**altında **Ekle'yi**seçin.

13. **Ad** sütunundaki rol için bir ad yazın. Örneğin, rol "Web Sunucusu" olabilir.

14. İhtiyacınız olan tüm rolleri eklemek için 12 ve 13 adımlarını yineleyin.

     Her rol, test denetleyicisi tarafından yönetilen bir test aracısı kullanır.

15. Testlerinizi çalıştırmak istediğiniz rolü seçin ve ardından **testleri çalıştırmak için rol olarak Ayarla'yı**seçin.

    > [!IMPORTANT]
    > Oluşturduğunuz ve tanımladığınız diğer roller testleri çalıştırmaz, ancak **yalnızca Veri ve Tanılama** sayfasındaki roller için belirttiğiniz veri ve tanıbağcılara göre veri toplamak için kullanılır.

16. Bir rol için kullanılabilecek aracıları sınırlamak için rolü seçin ve **ardından seçili rol için Aracı öznitelikleri**altında araç çubuğunda **Ekle'yi** seçin.

     **Aracı Seçimi Kuralı** iletişim kutusu görüntülenir.

     **Öznitelik Adı'na** adı ve **Öznitelik Değeri'ndeki**değeri yazın ve sonra **Tamam'ı**seçin. Istediğiniz kadar öznitelik ekleyin.

     Örneğin, 16 GB'tan fazla belleğe sahip test aracısı makinelerine filtre uygulayacak şekilde "Doğru" veya "False" değerine sahip "RAM > 16GB" adlı bir öznitelik ekleyebilirsiniz. Aynı özniteliği bir veya daha fazla test aracısına uygulamak için **Test Denetleyicisini Yönet** iletişim kutusunu kullanırsınız. Daha fazla bilgi için Visual [Studio ile test denetleyicilerini ve test aracılarını yönet'e](../test/manage-test-controllers-and-test-agents.md)bakın.

17. **Veri ve Tanılama'yı**seçin.

     **Veri ve Tanılama** sayfası görüntülenir.

     ![Test ayarı verileri ve tanılama](../test/media/load_testtest.png)

18. Veri **ve Tanılama** sayfasında, rolün veri toplamak için kullanacağı *tanılama veri bağdaştırıcılarını* seçerek rolün ne yaptığını tanımlarsınız. Bu nedenle, rol için bir veya daha fazla veri ve tanıbağdayAn etkinleştirilirse, test denetleyicisi, rol için tanımladığınız özniteliklere bağlı olarak belirtilen veriler ve tanıbağcılar için veri toplamak için kullanılabilir bir test aracısı makinesi seçer. Her rol için toplamak istediğiniz verileri ve tanılama veri bağdaştırıcılarını seçmek için rolü seçin. Her rol için, testlerin ihtiyaçlarına göre tanılama veri bağdaştırıcılarını seçin. Her rol için seçtiğiniz her tanılama veri bağdaştırıcısını yapılandırmak için **Yapıl'ı**seçin.

     **Roller ve tanısal veri bağdaştırıcıları örneği:**

     Örneğin, "SQL Kullanır" özniteliği "True" olarak ayarlanmış "Masaüstü İstemci" adlı bir istemci rolü ve "> 16GB RAM" olarak ayarlanmış bir öznitelik olan "SQL Server" adlı bir sunucu rolü oluşturabilirsiniz. "Masaüstü İstemci"nin, **Roller** sayfasında testleri **çalıştırmak için rol olarak Set'i** seçerek testleri çalıştıracağını belirtirseniz, test denetleyicisi testleri çalıştırmak için "True" olarak ayarlanan "SQL Kullanır" özniteliğini içeren test aracıları olan makineleri seçer. Test denetleyicisi ayrıca, yalnızca rolde yer alan veri ve tanıbağcılar tarafından tanımlanan verileri toplamak için "RAM > 16GB" özniteliğini içeren test aracıları olan SQL sunucu makinelerini de seçer. "Masaüstü İstemci" test aracısı, bu rol için de veri ve tanıbağlayıcıları seçerseniz çalıştırıldığı makineler için veri toplayabilir.

     Her tanılama veri bağdaştırıcısı ve nasıl yapılandırılabildiği hakkında ayrıntılı bilgi için, ilişkili konuyu aşağıdaki tabloda görüntüleyebilirsiniz.

     Tanılama veri bağdaştırıcıları hakkında daha fazla bilgi için [bkz.](../test/collect-diagnostic-information-using-test-settings.md)

     **Yük Testleri için Tanısal Veri Bağdaştırıcıları**

    |Tanısal veri bağdaştırıcısı|Yük testlerinde kullanma|İlişkili konu|
    |-|-------------------------|-|
    |**IntelliTrace ve Test Etkisi için ASP.NET İstemci Proxy:** Bu proxy, intelliTrace ve Test Impact tanıveri bağdaştırıcıları için bir web sunucusuna istemciden http aramaları hakkında bilgi toplamanızı sağlar.|![Bilgi simgesi](../test/media/vc364f4.gif)<br /><br /> Test aracısı makineleri için sistem bilgilerini toplamanız gereken belirli bir gereksinim yoksa, bu bağdaştırıcıyı içermez. **Dikkat:**  Toplanan çok miktarda veri nedeniyle oluşan sorunlar nedeniyle yük testlerinde IntelliTrace bağdaştırıcısının kullanılmasını önermiyoruz. <br /><br /> Test etki verileri yük testleri kullanılarak toplanmaz.||
    |**IntelliTrace:** Günlük dosyasında depolanan belirli tanılama izleme bilgilerini yapılandırabilirsiniz. Günlük dosyasında *.tdlog*uzantısı vardır. Testinizi çalıştırdığınızda ve bir test adımı başarısız olduğunda, bir hata oluşturabilirsiniz. Tanılama izlemesini içeren günlük dosyası bu hataya otomatik olarak eklenir. Günlük dosyasında toplanan veriler, koddaki bir hatayı çoğaltmak ve tanılamak için gereken süreyi azaltarak hata ayıklama verimliliğini artırır. Bu günlük dosyasından yerel oturum başka bir bilgisayarda yeniden oluşturulabilir. Bu, bir hatanın çoğaltılamaz riskini azaltır.<br /><br /> Daha fazla bilgi için Bkz. [IntelliTrace verilerini topla.](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)|![Önemli simgesi](../test/media/vc364f3.gif)<br /><br /> Toplanan ve günlüğe kaydedilen büyük miktardaki veri nedeniyle oluşan sorunlar nedeniyle yük testlerinde IntelliTrace bağdaştırıcısının kullanılmasını önermiyoruz. IntelliTrace bağdaştırıcısını yalnızca uzun süre çalışmayan ve çok sayıda test aracısı kullanmayan yük testlerinde kullanmaya çalışmalısınız.|[Nasıl kullanılır: Zor sorunları hata ayıklamaya yardımcı olmak için IntelliTrace verilerini toplama](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)|
    |**ASP.NET Profilci:** ASP.NET web uygulamalarında performans verileri toplayan ASP.NET profil oluşturma içeren bir test ayarı oluşturabilirsiniz.|ASP.NET profil oluşturucu tanıveri bağdaştırıcısı Internet Information Services (IIS) işlemini profiller, bu nedenle bir geliştirme web sunucusuna karşı çalışmaz. Yükleme testinizdeki web sitesinin profilini çıkarmak için, IIS'nin çalıştırdığı makineye bir test aracısı yüklemeniz gerekir. Test aracısı yük oluşturmaz, ancak yalnızca bir toplama aracısı olur. Daha fazla bilgi için [bkz.](../test/lab-management/install-configure-test-agents.md)|[Nasıl yapılır: Test ayarlarını kullanarak yük testleri için ASP.NET profil oluşturucuya yapılandırın](../test/how-to-configure-aspnet-profiler-for-load-tests-using-test-settings.md)|
    |**Olay günlüğü:** Test ayarını, test sonuçlarına dahil edilecek olay günlüğü toplamayı içerecek şekilde yapılandırabilirsiniz.||[Nasıl yapılır: Test ayarlarını kullanarak olay günlüğü koleksiyonunu yapılandırma](https://msdn.microsoft.com/48d67891-6018-4549-83e3-213d5d824a02)|
    |**Ağ Öykünme:** Bir test ayarı kullanarak testinize yapay ağ yükü koymak istediğinizi belirtebilirsiniz. Ağ öykünme, çevirmeli bağlantı hızı gibi belirli bir ağ bağlantı hızını taklit ederek makineyle olan ve makineden gelen iletişimi etkiler. **Not:**  Ağ bağlantı hızını artırmak için ağ öykünme kullanılamaz.|Ağ Öykünme bağdaştırıcısı yük testleri tarafından yoksayılır. Bunun yerine, yük testleri yük testi senaryosunun ağ karışımında belirtilen ayarları kullanır.<br /><br /> Daha fazla bilgi için [bkz.](../test/specify-virtual-network-types-in-a-load-test-scenario.md)||
    |**Sistem Bilgileri:** Sistem Bilgileri tanılama ve veri toplayıcısının çalıştırıldığı makinelerle ilgili sistem bilgilerini içerecek şekilde bir test ayarı ayarlanabilir. Sistem bilgileri test sonuçlarında bir test ayarı kullanılarak belirtilir.|![Bilgi simgesi](../test/media/vc364f4.gif)<br /><br /> Test altında hem yük aracılarından hem de sistemden sistem bilgileri toplayabilirsiniz.|Bu bilgileri toplamak için yapılandırma gerekmez.|
    |**Test Etkisi:** Bir test çalışması çalıştırıldığında uygulama kodunuzu hangi yöntemlerin kullanıldığı hakkında bilgi toplayabilirsiniz. Bu, geliştiriciler tarafından bu geliştirme değişikliklerinden hangi testlerin etkilendiğini belirlemek için yapılan uygulama kodudeğişiklikleriyle birlikte kullanılabilir.|Test etki verileri yük testleri ile toplanmaz.||
    |**Video Kaydedici:** Otomatik bir test çalıştırdığınızda masaüstü oturumunuzun video kaydını oluşturabilirsiniz. Bu, kodlanmış bir Kullanıcı Arabirimi testi için kullanıcı eylemlerini görüntülemek için yararlı olabilir. Video, diğer ekip üyelerinin yeniden oluşturulması zor olan uygulama sorunlarını yalıtmalarına yardımcı olabilir. **Not:**  Testleri uzaktan çalıştırırken, aracı etkileşimli işlem modunda çalışmadığı sürece video kaydedici çalışmaz.|![Önemli](../test/media/vc364f3.gif) simge **Uyarı:** Yük testleri için Video Kaydedici bağdaştırıcısının kullanılmasını önermiyoruz.|[Nasıl yapılır: Test ayarlarını kullanarak test sırasında ekran ve ses kayıtlarını ekleme](../test/how-to-include-recordings-of-the-screen-and-voice-during-tests.md)|

19. **Dağıtım'ı**seçin.

     **Dağıtım** sayfası görüntülenir.

20. Testlerinizi her çalıştırdığınızda dağıtım için ayrı bir dizin oluşturmak için **dağıtımı Etkinleştir'i**seçin.

    > [!NOTE]
    > Bunu yaparsanız, testlerinizi çalıştırdığınızda uygulamanızı oluşturmaya devam edebilirsiniz.

21. Testlerinizi çalıştırmak için kullandığınız dizine dosya eklemek için **dosya ekle'yi**seçin ve ardından eklemek istediğiniz dosyayı seçin.

    > [!NOTE]
    > Bir yük testlerini çalıştırdığınızda, eklenti derlemeleri, veri dosyaları ve yüklenen dosyalar otomatik olarak dağıtılır.

22. Testlerinizi çalıştırmak için kullandığınız dizine bir dizin eklemek için **Dizin Ekle'yi** seçin ve ardından eklemek istediğiniz dizini seçin.

23. Testlerinden önce ve sonra komut dosyalarını çalıştırmak için **Kurulum ve Temizleme Komut Dosyalarını**seçin.

     **Kurulum ve Temizleme Komut Dosyaları** sayfası görüntülenir.

    1. Komut dosyasının konumunu **Kurulum komut dosyasına** yazın veya kurulum komut dosyasını bulmak için elipsis **(...**) seçeneğini belirleyin.

    2. **Temizleme komut dosyasına** komut dosyasının konumunu yazın veya temizleme komut dosyasını bulmak için elipsis **(...**) seçeneğini belirleyin.

24. Farklı bir ana bilgisayar kullanarak testlerinizi çalıştırmak için **Ana Bilgisayar'ı**seçin.

    1. **Ana Bilgisayar Türü'nde,** **Varsayılan'ın** seçildiğini doğrulayın.

        > [!NOTE]
        > **Ana Bilgisayar türündeki** **ASP.NET** yük testlerinde desteklenmez.

    2. Yük testinizdeki web performansı nın ve birim testlerinin 32 bit veya 64 bit işlem olarak çalışmasını isteyip istemediğiniz iseçmek için **32 bit veya 64 bit** işlem açılırken Çalıştır testini kullanın.

        > [!NOTE]
        > Maksimum esneklik için, Herhangi bir **CPU** yapılandırmasını kullanarak web performansınızı ve yük testi projelerinizi derlemeniz gerekir. Daha sonra hem 32 bit hem de 64 bit aracılar üzerinde çalıştırabilirsiniz. **64 bit** yapılandırmayı kullanarak web performansı ve yük testi projelerini derlemek hiçbir avantaj sunamaz.

25. (İsteğe bağlı) Her test çalışması ve tek tek testler için süreyi sınırlamak için **Test Zaman Eklerini'ni seçin.**

    1. Bir zaman sınırı aşıldığında bir test çalışmasını iptal etmek için, **toplam süre aşılırsa bir test çalışmasını iptal** et ve ardından bu sınır için bir değer yazın.

    2. Bir zaman sınırı aşıldığında tek bir testi başarısız yapmak için, **yürütme süresi aşılırsa tek bir testi başarısız olarak işaretle'yi**seçin ve bu sınır için bir değer yazın.

26. **Ünite Testini**Atla . Yük testleri bu ayarları kullanmaz.

27. **Web Test'i**atla. Yük testleri bu ayarları kullanmaz.

28. Test ayarlarını kaydetmek için **Farklı Kaydet'i**seçin. **Nesne adına**istediğiniz dosyanın adını yazın.

## <a name="remove-a-test-settings-file-from-your-solution"></a>Çözümden bir test ayarları dosyanı kaldırma

**Çözüm Gezgini'ndeki** **Çözüm Öğeleri** klasörü altında, kaldırmak istediğiniz test ayarlarını sağ tıklatın ve ardından **Kaldır'ı**seçin.

Test ayarları dosyası çözümünüzden kaldırılır.

## <a name="see-also"></a>Ayrıca bkz.

- [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)
- [Test ayarlarını kullanarak tanılama bilgilerini toplama](../test/collect-diagnostic-information-using-test-settings.md)
