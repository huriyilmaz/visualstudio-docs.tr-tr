---
title: Test denetleyicilerini ve test aracılarını yönetme
ms.date: 09/18/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: efcc284291281b6e370cf51ddbe175faf8f1204c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75584419"
---
# <a name="manage-test-controllers-and-test-agents"></a>Test denetleyicilerini ve test aracılarını yönetme

Testleri uzaktan çalıştırmak, testleri birden çok makineye dağıtmak veya yük testleri çalıştırmak için Visual Studio'u kullanmak istiyorsanız, bir test denetleyicisi, test aracıları ve test ayarları dosyasını yapılandırmanız gerekir. Bu konu, ilk kez yükledikten ve yapılandırdıktan sonra test denetleyicilerini ve test aracılarını nasıl yönetişize edilebildiğini açıklar.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Laboratuvar ortamlarında testler çalıştırmak için Microsoft Test Yöneticisi'ni kullanıyorsanız, Microsoft Test Yöneticisi için **Laboratuvar Merkezi'ndeki** **Test Denetleyiciyöneticisini** kullanarak test denetleyicilerini ve aracılarını yönetirsiniz. Bu konu yalnızca testleri çalıştırmak için Visual Studio'yı kullanıyorsanız geçerlidir.

Visual Studio'da testleri çalıştırmak için test aracılarını ve test denetleyicilerini nasıl yükleyip yapılandırılabilme hakkında bilgi [için](../test/configure-test-agents-and-controllers-for-load-tests.md)bkz.

Test denetleyicisini ve kayıtlı aracıları yapılandırmak ve izlemek için, test projenizde çalıştırmak istediğiniz testleri içeren bir test ayarları dosyanız olması gerekir. Test ayarları dosyasını açın, **Rol'u** seçin ve **Denetleyici** alanı için açılan dosyadan **Test Denetleyicilerini Yönet'i** seçin.

Bir yük testi projesi **için, Yük Testi** menüsünden **Test Denetleyicilerini Yönet'i** de seçebilirsiniz.

## <a name="add-a-test-agent-to-a-test-controller"></a>Test denetleyicisine test aracısı ekleme

Farklı bir test denetleyicisine bir test aracısı eklemek isteyebilirsiniz veya yeni yüklediğiniz bir test denetleyicisine bir test aracısı eklemeniz gerekebilir.

### <a name="to-add-a-test-agent-to-a-test-controller"></a>Test denetleyicisine test aracısı eklemek için

1. **Test Aracısı Yapılandırma Aracısı** **Başlat'ı** > seçin.

     **Yapılaşı Test Aracısı** iletişim kutusu görüntülenir.

    > [!NOTE]
    > Bir test denetleyicisine eklemek için zaten yüklü bir test aracısı olması gerekir. Test aracısını nasıl yükleyin hakkında daha fazla bilgi için, [test aracılarını yükle ve yapılandırma](../test/lab-management/install-configure-test-agents.md)ya da yapılandırma ya da

2. Test aracısının çalıştırılma şekline yönelik iki seçenek sunulur:

   - **Hizmet**: Kodlanmış UI testleri veya test çalıştığında video kaydı oluşturma gibi masaüstüyle etkileşimde bulunan otomatik testler çalıştırmak zorunda değilseniz, **Test aracısını Çalıştır'ın**altında **Hizmet'i**seçin. Test aracısı bir hizmet olarak başlatılacaktır. **İleri**’yi seçin.

      Artık test aracısı bir hizmet olarak başladığında kullanıcı hakkındaki ayrıntıları girebilirsiniz.

      1. **Kullanıcı adına**adı girin.

      2. **Parola'ya**şifregirin.

        |**Önemli kullanıcı hesabı bilgileri**|
        |-|
        |- Null şifreleri kullanıcı hesapları için desteklenmez.|
        |- IntelliTrace toplayıcısını veya ağ öykünmesi kullanmak istiyorsanız, kullanıcı hesabı Yöneticiler grubunun bir üyesi olmalıdır.|
        |- Aracı kullanıcı adı aracı hizmetinde değilse, test denetleyicisinde izin gerektiren aracı yı eklemeye çalışır.|
        |- Test denetleyicisini kullanmaya çalışan kullanıcı test denetleyicisinin Kullanıcılar hesabında olmalıdır veya testleri denetleyiciye karşı çalıştıramaz.|

   - **Etkileşimli İşlem**: Kodlanmış UI testleri veya test leriniz çalıştığında video kaydı oluşturma gibi masaüstüyle etkileşimde olması gereken otomatik testler çalıştırmak **istiyorsanız, Etkileşimli İşlem'i**seçin. Test aracısı bir hizmet yerine etkileşimli bir işlem olarak başlatılacaktır.

      Bir sonraki sayfada, test aracısı bir işlem olarak başladığında kullanıcı hakkındaki ayrıntıları ve diğer seçenekleri girin.

      1. **Kullanıcı adına**adı girin.

      2. **Parola'ya**şifregirin.

        > [!NOTE]
        > Test aracısını, şu anda etkin olmayan farklı bir kullanıcıyla etkileşimli bir işlem olarak çalışacak şekilde yapılandırırsanız, aracıyı başlatabilmek için bilgisayarı yeniden başlatmanız ve bu farklı kullanıcı olarak oturum açmanız gerekir. Ayrıca, null parolalar kullanıcı hesapları için desteklenmez. IntelliTrace toplayıcısını veya ağ öykünmesi kullanmak istiyorsanız, kullanıcı hesabı Yöneticiler grubunun bir üyesi olmalıdır.

      3. Test aracısı olan bir bilgisayarın testleri yeniden başlatıldıktan sonra çalıştırabilmesini sağlamak için, bilgisayarı test aracısı kullanırken otomatik olarak oturum açacak şekilde ayarlayabilirsiniz. **Oturum Aç'ı otomatik olarak**seçin. Bu, kullanıcı adı ve parolayı kayıt defterinde şifreli bir biçimde saklar.

      4. Bu, masaüstüyle etkileşimde olması gereken otomatik testleri etkileyebileceğinden ekran koruyucunun devre dışı bırakıldığından emin olmak için **ekran koruyucunun devre dışı bırakıldığından emin olun'u**seçin.

        > [!WARNING]
        > Otomatik olarak oturum açarsanız veya ekran koruyucuyu devre dışı btanırsanız güvenlik riskleri vardır. Otomatik oturum açmayı etkinleştirerek, diğer kullanıcıların bu bilgisayarı başlatmasını ve otomatik olarak oturum açan hesabı kullanabilmesini sağlarsınız. Ekran koruyucuyu devre dışı bederseniz, bilgisayar bir kullanıcının bilgisayarın kilidini açmak için oturum açmasını istemeyebilir. Bu, bilgisayara fiziksel erişimi olan herkesin makineye erişmesini sağlar. Bu özellikleri bilgisayarda etkinleştiriseniz, bu bilgisayarların fiziksel olarak güvenli olduğundan emin olmalısınız. Örneğin, bu bilgisayarlar fiziksel olarak güvenli bir laboratuarda bulunur. (Ekran **koruyucunun devre dışı bırakıldığından emin olun,bu**ekran koruyucunuzu etkinleştirmez'i temizlerseniz.)

3. Bu aracıyı farklı bir test denetleyicisine kaydettirmek için **test denetleyicisine kaydol'u seçin.** Test denetleyicinizin adını **ve** ardından kullandığınız bağlantı noktası numarasını aşağıdaki test **denetleyicisine sahip test aracısını kaydedin.** Örneğin, **agent1:6901**yazın.

    > [!NOTE]
    > Varsayılan bağlantı noktası numarası 6901'dir.

4. Değişikliklerinizi kaydetmek için **Ayarlar'ı Uygula'yı**seçin. Yapılandırma **özeti** iletişim kutusunu kapatın ve ardından **Test Aracısı Yapılandırma Aracısını**kapatın.

> [!WARNING]
> Aracı şu anda başka bir test denetleyicisi üzerinde çalışacak şekilde yapılandırıldıysa, test aracısını bu denetleyiciden kaldırmanız gerekir.

## <a name="remove-a-test-agent-from-a-test-controller"></a>Test aracını test denetleyicisinden kaldırma

Bir test aracısı kaldırılabilmesi için çevrimdışı duruma ayarlanmalıdır.

> [!NOTE]
> Bu yordamı, bir denetleyiciye kayıtlı aracıları laboratuar ortamının bir parçası olarak kaldırmak için kullanamazsınız. Bu aracıları denetleyiciden kaldırmak için Microsoft Test Yöneticisi'ni kullanarak ortamı kaldırmanız gerekir.

### <a name="to-remove-a-test-agent-from-a-test-controller"></a>Test aracısını test denetleyicisinden kaldırmak için

1. Test denetleyicisi bir projeye kayıtlı değilse, aşağıdaki adımları izleyin.

    1. Visual Studio'dan test projeniz için test ayarları dosyasını açın, **Rol'u** seçin ve **Denetleyici** alanı için açılan dosyadan **Test Denetleyicilerini Yönet'i** seçin.

         **Test Denetleyicisini Yönet** iletişim kutusu görüntülenir.

    2. **Denetleyici** açılır listesinde, test denetleyicisini kurduğunuz bilgisayarın adını yazın. Daha önce belirli bir test denetleyicisi uyguladıysanız, listeden adı seçebilirsiniz.

    3. **Aracılar** bölmesinde, test aracısı adını seçin. Aracı hala çevrimiçiyse, **Çevrimdışı'nı seçin.** Kaldırmak için **Kaldır'ı**seçin.

        > [!NOTE]
        > Bir test aracısını kaldırmak, test denetleyicisinden uzaklaştırılı. Test aracısını tamamen kaldırmak için test aracısı bilgisayarındaki **Programlar ve Özellikler** Denetim Masası'nı kullanın.

2. Test denetleyicisi bir projeye kayıtlıysa, Microsoft Test Yöneticisi'ni kullanarak aracıyı kaldırın.

## <a name="change-the-settings-for-a-test-agent"></a>Test aracısının ayarlarını değiştirme

Test aracısının durumu aşağıdaki değerlerden herhangi biri olabilir:

|Durum|Açıklama|
|-|-----------------|
|Koşu Testi|Testleri çalıştırma|
|Hazır|Testleri çalıştırmak veya veri ve tanılama toplamak için kullanılabilir|
|Çevrimdışı|Testleri çalıştırmak veya veri ve tanılama toplamak için kullanılamıyor|
|Bağlantı kesildi|Test aracısı başlatılmadı|

Aşağıdaki yordamları kullanarak bir test aracısının durumunu ve diğer ayarlarını değiştirebilirsiniz.

### <a name="to-change-the-settings-of-a-test-agent"></a>Test aracısının ayarlarını değiştirmek için

> [!NOTE]
> Test aracısı bir projeye kayıtlı bir test denetleyicisine kayıtlıysa, Microsoft Test Yöneticisi'ndeki ayarları değiştirin.

1. Test denetleyicisini ve yük testi için kayıtlı aracıları yapılandırmak ve izlemek için Visual Studio'daki **Yük Testi** menüsünü seçin ve ardından **Test Denetleyicilerini Yönet'i**seçin. Diğer testler için Visual Studio'da test projeniz için test ayarları dosyasını açın, **Role'yi** seçin ve **Denetleyici** alanı için açılan dan **Test Denetleyicilerini Yönet'i** seçin.

   **Test Denetleyicisini Yönet** iletişim kutusu açılır.

1. Test denetleyici listesinde değiştirmek istediğiniz test aracılarını test denetleyicisinin adını seçin. Test denetleyicisi listede görünmüyorsa, test denetleyicisinin doğru kaydedilip kaydedilmediğini denetleyin. Daha fazla bilgi için, bir test denetleyicisini yapılandırma hakkında aşağıdaki yordamı görün.

1. (İsteğe bağlı) Test **Aracıları** bölmesinde, özellikleri değiştirmek istediğiniz test aracısı bilgisayarını seçin.

1. **Özellikler**'i seçin.

1. Aşağıdaki test aracısı özelliklerini gerektiği gibi değiştirin:

|Test Aracısı Özelliği|Açıklama|
|-|-----------------|
|**Ağırlık**|Farklı performans düzeylerine sahip test aracılarını kullandığınızda yükü dağıtmak için kullanılır. Örneğin, 100 ağırlığı olan bir test aracısı, 50 ağırlığı olan bir test aracısı olarak yükün iki katını alır.|
|**IP Anahtarlama**|IP anahtarlama yapılandırmak için kullanılır. IP anahtarlama, bir test aracısının bir dizi IP adresi kullanarak sunucuya istek göndermesine olanak tanır. Bu, farklı istemci bilgisayarlardan gelen aramaları simüle eder.<br /><br /> Yük testiniz bir web çiftliğine erişiyorsa IP Anahtarlama önemlidir. Çoğu yük dengeleyicisi, istemcinin IP adresini kullanarak istemci ile belirli bir web sunucusu arasında yakınlık kurar. Tüm istekler tek bir istemciden geliyormuş gibi görünüyorsa, yük dengeleyici yükü dengelemez. Web çiftliğinde iyi bir yük dengesi elde etmek için, isteklerin çeşitli IP adreslerinden geldiğinden emin olun. **Not:**  Bir ağ bağdaştırıcısı belirtebilir veya şu anda kullanılmayan bir tanesini otomatik olarak seçmek için **(Tümü atanmamış)** kullanabilirsiniz. <br /><br /> IP anahtarlama özelliğini kullanmak için Visual Studio Test Aracısı hizmetinin, bu aracı bilgisayar için Yöneticiler grubunda bir kullanıcı olarak çalışıyor olması gerekir. Bu kullanıcı aracı kurulumu sırasında seçilir, ancak hizmetin özelliklerini değiştirip yeniden başlatArak değiştirilebilir.<br /><br /> IP anahtarlamanın doğru çalıştığını doğrulamak için, Web sunucusunda IIS günlüğe kaydetmeyi etkinleştirin, isteklerin yapılandırdığınız IP adreslerinden geldiğini doğrulamak için IIS günlük işlevini kullanın.|
|**Öznitelikler**|Test aracısı seçiminde kullanılabilecek ad/değer çiftleri kümesi. Örneğin, bir sınama belirli bir işletim sistemi gerektirebilir. Test ayarları dosyanızın **Görevler** sekmesine öznitelikler ekleyebilirsiniz ve bunlar eşleşen özniteliklere sahip bir test aracısı seçmek için kullanılabilir. Birden çok makinede bir test çalıştırmak istiyorsanız, test ayarları rolünde test ayarları rolünde bir öznitelik oluşturun ve ardından bu rolde kullanmak istediğiniz her test aracısında eşleşen bir öznitelik yapılandırın... **Not:**  Bu ayarı yalnızca projeye kayıtlı olmayan bir test denetleyicisine kayıtlı test aracıları için kullanılabilir, çünkü bu öznitelikler yalnızca Visual Studio için test ayarlarında kullanılır.|

Test aracısı ağırlığı ve test aracısı özniteliği değişiklikleri hemen yürürlüğe girer, ancak çalışan testleri etkilemez. TEST denetleyicisi yeniden başlatıldıktan sonra IP Adres Aralığı etkinolur.

(İsteğe bağlı) Bir test aracısının durumunu değiştirmek için, listedeki aracıyı seçin ve ardından aracının geçerli durumuna göre kullanılabilir seçeneklerden eylemi seçin.

> [!NOTE]
> Test aracınız bir işlem olarak çalışıyorsa, test aracınızın yüklü olduğu bilgisayarda çalışan bildirim alanı simgesinden test aracısının durumunu yönetirsiniz. Bu, test aracısının durumunu gösterir. Bu aracı kullanarak bir işlem olarak çalışıyorsa aracıyı başlatabilir, durdurabilir veya yeniden başlatabilirsiniz.

## <a name="configure-a-test-controller"></a>Test denetleyicisi yapılandırma

Bir test denetleyicisini yapılandırmak için **Takım Test Denetleyicisi Yapılandırma Aracı'nı**kullanmanız gerekir. Test denetleyicinizi yapılandırdığınızda, test denetleyicinizi farklı bir proje koleksiyonuyla kaydedebilir veya test denetleyicinizi bir proje koleksiyonundan kaydını çıkarabilirsiniz.

Test denetleyicinizi Team Foundation Server proje koleksiyonunuza kaydetmek istiyorsanız, test denetleyicihizmeti için kullandığınız hesabın Proje Koleksiyonu için Proje Toplama Test Hizmeti Hesapları grubuna veya hesabın adedine üye olması gerekir test denetleyicisi yapılandırma aracını çalıştırmak için kullandığınız bir Proje Koleksiyonu Yöneticisi olmalıdır.

> [!NOTE]
> Proje koleksiyonunda varolan ortamları olan bir proje koleksiyonundan bir test denetleyicisini nkaydığınızda, bu proje koleksiyonunu taşıdıysanız ve test denetleyicisini taşınan proje koleksiyonuna yeniden kaydettirseniz ortamlar yine de korunur.

### <a name="to-configure-a-test-controller"></a>Test denetleyicisini yapılandırmak için

1. Test denetleyicinizi istediğiniz zaman yeniden yapılandırmak için aracı çalıştırmak için **Test** > **Denetleyicisini Başlat Yapılandırma Aracı'nı**seçin.

     **YapılAşı Test Denetleyicisi** iletişim kutusu görüntülenir.

2. Test denetleyici hizmetiniz için oturum açma hesabı olarak kullanılacak kullanıcıyı seçin.

    > [!NOTE]
    > Null parolalar kullanıcı hesapları için desteklenmez.

4. (İsteğe bağlı) Test denetleyicinizi bir laboratuar ortamıyla kullanmak istemiyorsanız, ancak yalnızca Visual Studio'dan testler çalıştırmak istiyorsanız, **Team Project Collection ile kayıt test denetleyicisini**temizleyin.

5. (İsteğe bağlı) Yük testi için test denetleyicinizi yapılandırmak **için, yük testi için yapıyı test denetleyicisini**seçin. Aşağıdaki SQL Server **örneğinde load test sonuçları veritabanını oluştur'un**altına SQL Server örneğini girin.

> [!NOTE]
> Test denetleyicileri hakkında daha fazla sorun giderme bilgileri [için, test aracılarını yükle ve yapılandırma](../test/lab-management/install-configure-test-agents.md)ya da yapılandırma'ya bakın.

## <a name="manage-your-agents-when-you-run-your-tests-with-a-test-controller"></a>Test denetleyicisi ile testlerinizi çalıştırdığınızda aracılarınızı yönetin

Visual Studio için test ayarlarınıza uygulamanız için roller eklediğinizde, her rolünüzün aracı özellikleri ekleyebilirsiniz. Bu, bu rol için hangi test aracılarının kullanılabilir olduğunu belirler. Bu test ayarlarını kullanarak testlerinizi çalıştırdığınızda, test ayarları için seçilen test denetleyicisi gerekli aracıların kullanılabilirliğini belirler. Aracı kullanılabilirliği belirlendiğinde oluşabilecek aşağıdaki durumlar şunlardır:

- Testleri çalıştırması gereken rol için kullanılabilir bir aracı yok. Testleriniz çalıştırılamaz. Aşağıdaki eylemlerden birini gerçekleştirebilir ve ardından testlerinizi yeniden çalıştırabilirsiniz:

  - Bu rolün testleri çalıştırması için bir aracının kullanılabilir olmasını bekleyebilirsiniz.

  - Bu rol için kullanılabilecek çevrimdışı aracılar varsa, aracıyı kullanılabilir olması için yeniden başlatabilirsiniz.

  - Test denetleyicisine bu rol için doğru aracı özelliklerine sahip başka bir aracı ekleyebilirsiniz.

  - Kullanmak istediğiniz diğer aracıları etkinleştirmek için test ayarlarında bu rolün aracı özelliklerini değiştirebilirsiniz.

- Tanılama veri bağdaştırıcılarını çalıştıran bir veya daha fazla rol için kullanılabilir aracı yok. Testleriniz çalıştırılabilir, ancak tanılama veri bağdaştırıcısı çalıştırılamaz. Tanılama veri bağdaştırıcısı olmadan testlerinizi çalıştırabilir veya aşağıdaki eylemlerden birini gerçekleştirip testlerinizi yeniden çalıştırabilirsiniz:

  - Bu roller için kullanılabilir hale gelmesi için bir aracı bekleyebilirsiniz.

  - Bu rol için çevrimdışı olan aracılar varsa, **Test** menüsündeki **Test Denetleyicisini Yönet'ten** aracının durumunu çevrimiçi olarak değiştirmeniz gerekir. Ayrıca, denetleyiciden bağlantısı kesildiyse aracıyı yeniden başlatmanız gerekebilir.

  - Bu test çalışması için ihtiyaç duyabileceğiniz aracıların testleri çalıştırmakla meşgul olmadığını doğrulayın. **Test** menüsündeki **Test Denetleyicisini Yönet'ten** herhangi bir aracının durumunu kontrol edebilirsiniz.

  - Test denetleyicisine rol için doğru aracı özelliklerine sahip başka bir aracı ekleyebilirsiniz.

  - Kullanmak istediğiniz diğer aracıları etkinleştirmek için test ayarlarındaki rolün aracı özelliklerini değiştirebilirsiniz.

## <a name="load-tests-from-delay-signed-assemblies"></a>Gecikme imzalı montajlardan yük testleri

Test denetleyicisi ve test aracıları yalnızca güçlü imzalı derlemeler veya imzalanmamış derlemeler olan test derlemelerini yükleyebilir. Uygulama için üretim derlemelerine erişmesi gerektiğinden, bazı test derlemeleri gecikme imzalıdır. Ancak, bu derlemeler yalnızca test derlemeleri olduğundan ve dağıtılmadığından güçlü bir şekilde imzalanmaz. Bu derlemeler gecikme imzalı olduğundan yüklenemez, bu nedenle test kontrol makinesi de dahil olmak üzere montajın yüklendiği tüm makinelerdeki bu derlemeler için güçlü ad doğrulamasını devre dışı bmelisiniz. Gecikme imzalı doğrulamayı devre dışı kullanabilirsiniz, *sn.exe'yi*kullanın. Güçlü ad doğrulamasının atlanması istenen gecikme imzalı derlemenin ortak anahtar belirteci de dahil edilmesi gerekebilir.

Gecikme *Sn.exe* imzalı doğrulamayı devre dışı kullanabilirsiniz.

Bu, yalnızca belirtilen derleme için komutu çalıştırdığınız bilgisayarda güçlü ad doğrulamasını devre dışı kılabilir. Bunu yalnızca yeterli izinlere sahipseniz yapabilirsiniz.

Test çalışması tamamlandıktan sonra, *SN.exe* komutunu kullanarak gecikmeli imzalama doğrulamasını yeniden etkinleştirin.

İmza doğrulamasını devre dışı bırakıp yeniden etkinleştirmek için önerilen bir yol, komut dosyalarındaki *SN.exe* komutlarını kullanmaktır. Bir kurulum komut dosyasında doğrulamayı devre dışı bırakıp temizleme komut dosyasında doğrulamayı yeniden etkinleştirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Test aracılarını yükleme ve yapılandırma](../test/lab-management/install-configure-test-agents.md)
