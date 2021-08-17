---
title: Test denetleyicilerini ve test aracılarını yönetme
description: "' İ yükleyip ilk kez yapılandırdıktan sonra test denetleyicilerini ve test aracılarını yönetmeyi öğrenin."
ms.custom: SEO-VS-2020
ms.date: 09/18/2018
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
ms.openlocfilehash: dfbd12f9e4f18da356ed69c10a8e913f492f2c2f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092286"
---
# <a name="manage-test-controllers-and-test-agents"></a>Test denetleyicilerini ve test aracılarını yönetme

testleri uzaktan çalıştırmak, testleri birden çok makineye dağıtmak veya yük testleri çalıştırmak için Visual Studio kullanmak istiyorsanız, bir test denetleyicisi, test aracıları ve test ayarları dosyası yapılandırmanız gerekir. Bu konu, ilk kez yüklenip yapılandırıldıktan sonra test denetleyicilerinin ve test aracılarının nasıl yönetileceğini açıklar.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

::: moniker range="vs-2017"
Laboratuvar ortamlarında testleri çalıştırmak için Microsoft Test Yöneticisi kullanıyorsanız, Microsoft Test Yöneticisi için **Laboratuvar merkezindeki** **Test denetleyicisi Yöneticisi** ' ni kullanarak test denetleyicilerini ve aracılarını yönetirsiniz. bu konu yalnızca, testleri çalıştırmak için Visual Studio kullanıyorsanız geçerlidir.
::: moniker-end

test aracılarını ve test denetleyicilerini Visual Studio testleri çalıştırmak üzere yüklemek ve yapılandırmak hakkında daha fazla bilgi için bkz. [test aracılarını ve denetleyicilerini yapılandırma](../test/configure-test-agents-and-controllers-for-load-tests.md).

Test denetleyicisini ve tüm kayıtlı aracıları yapılandırmak ve izlemek için, test projenizde çalıştırmak istediğiniz testleri içeren bir test ayarları dosyası olması gerekir. Test ayarları dosyasını açın, **rol** ' i seçin ve **Denetleyici** alanı Için açılan listeden **Test Denetleyicilerini Yönet** ' i seçin.

Yük testi projesi için **Yük testi** menüsünden **Test Denetleyicilerini Yönet** ' i de seçebilirsiniz.

## <a name="add-a-test-agent-to-a-test-controller"></a>Test denetleyicisine test aracısı ekleme

Farklı bir test denetleyicisine test aracısı eklemek isteyebilirsiniz veya yeni yüklediğiniz bir test denetleyicisine test aracısı eklemeniz gerekebilir.

### <a name="to-add-a-test-agent-to-a-test-controller"></a>Test denetleyicisine test aracısı eklemek için

1.   >  **Test Aracısı yapılandırma aracını** Başlat ' ı seçin.

     **Test aracısını Yapılandır** iletişim kutusu görüntülenir.

    > [!NOTE]
    > Test denetleyicisine eklemek için zaten yüklü bir test aracınız olması gerekir. Test aracısının nasıl yükleneceğine ilişkin daha fazla bilgi için bkz. [test aracılarını yüklemek ve yapılandırmak](../test/lab-management/install-configure-test-agents.md).

2. Test aracısının nasıl çalıştırılabilecekiyle ilgili iki seçenek sunulur:

   - **Hizmet**: kodlanmış UI testleri gibi masaüstü ile etkileşime geçen otomatik testleri çalıştırmak veya testiniz çalıştığında bir video kaydı oluşturmak zorunda değilseniz, **Test aracısını farklı çalıştır**' ın altında **hizmet**' i seçin. Test Aracısı bir hizmet olarak başlatılır. **İleri**’yi seçin.

      Artık, test Aracısı hizmet olarak başladığında kullanıcı hakkındaki ayrıntıları girebilirsiniz.

      1. **Kullanıcı adında** adı girin.

      2. Parolayı **parola** olarak girin.

        |**Önemli Kullanıcı hesabı bilgileri**|
        |-|
        |-Null parolalar Kullanıcı hesapları için desteklenmez.|
        |-IntelliTrace toplayıcısını veya ağ öykünmesini kullanmak istiyorsanız, Kullanıcı hesabının Yöneticiler grubunun bir üyesi olması gerekir.|
        |-Aracı Kullanıcı adı aracı hizmetinde değilse, test denetleyicisinde izinler gerektiren bu uygulamayı eklemeye çalışacaktır.|
        |-Test denetleyicisini kullanmaya çalışan Kullanıcı, test denetleyicisinin Kullanıcı hesabında olmalıdır, aksi durumda denetleyiciye karşı testleri çalıştıramazlar.|

   - **Etkileşimli işlem**: kodlanmış UI testleri gibi masaüstü ile etkileşmesi gereken otomatik testleri çalıştırmak veya testiniz çalıştığında bir video kaydı oluşturmak Istiyorsanız **etkileşimli işlem**' i seçin. Test Aracısı hizmet yerine etkileşimli bir işlem olarak başlatılır.

      Bir sonraki sayfada, test Aracısı işlem olarak başladığında kullanıcı hakkındaki ayrıntıları ve diğer seçenekleri girin.

      1. **Kullanıcı adında** adı girin.

      2. Parolayı **parola** olarak girin.

        > [!NOTE]
        > Test aracısını, şu anda etkin olan kullanıcı olmayan farklı bir kullanıcıyla etkileşimli bir işlem olarak çalışacak şekilde yapılandırırsanız, bilgisayarı yeniden başlatmanız ve aracıyı başlatabilmeniz için bu farklı kullanıcı olarak oturum açmanız gerekir. Ayrıca, null parolalar Kullanıcı hesapları için desteklenmez. IntelliTrace toplayıcısını veya ağ öykünmesini kullanmak istiyorsanız, Kullanıcı hesabının Yöneticiler grubunun bir üyesi olması gerekir.

      3. Test aracısı olan bir bilgisayarın yeniden başlatıldıktan sonra testleri çalıştırabileceği emin olmak için, bilgisayarı test Aracısı tarafından otomatik olarak oturum açacak şekilde ayarlayabilirsiniz. **Otomatik oturum aç '** ı seçin. Bu işlem, Kullanıcı adını ve parolayı kayıt defterindeki şifreli bir biçimde depolar.

      4. BT koruyucunun devre dışı bırakıldığından emin olmak için, bu, masaüstü ile etkileşim kurması gereken otomatikleştirilmiş testleri etkileyebilecek olduğundan, **ekran koruyucunun devre dışı bırakıldığından emin olun**' ı seçin.

        > [!WARNING]
        > Otomatik olarak oturum açtığınızda veya ekran koruyucuyu devre dışı bıraktığınızda güvenlik riskleri vardır. Otomatik oturum açma özelliğini etkinleştirerek, diğer kullanıcıların bu bilgisayarı başlatmasını ve otomatik olarak oturum açtığı hesabı kullanabilmelerini sağlayabilirsiniz. Ekran koruyucusunu devre dışı bırakırsanız, bilgisayar bir kullanıcının bilgisayarın kilidini açmak için oturum açmasını istemez. Bu, bilgisayara fiziksel erişimi olan herkesin makineye erişmesini sağlar. Bu özellikleri bir bilgisayarda etkinleştirirseniz, bu bilgisayarların fiziksel olarak güvenli olduğundan emin olun. Örneğin, bu bilgisayarlar fiziksel olarak güvenli bir laboratuvarda bulunur. ( **Ekran koruyucunun devre dışı bırakıldığından emin olun**, bu ekran koruyucunuzu etkinleştirmez.)

3. Bu aracıyı farklı bir test denetleyicisiyle kaydetmek için, **test denetleyicisiyle kaydet** ' i seçin. Test denetleyicinizin adını izleyen **:** ve **Test aracısını aşağıdaki test denetleyicisiyle kaydet** bölümünde kullandığınız bağlantı noktası numarasını yazın. Örneğin, **agent1:6901** yazın.

    > [!NOTE]
    > Varsayılan bağlantı noktası numarası 6901 ' dir.

4. değişikliklerinizi kaydetmek için **Ayarlar uygula**' yı seçin. **Yapılandırma Özeti** iletişim kutusunu kapatın ve ardından **Test Aracısı yapılandırma aracını** kapatın.

> [!WARNING]
> Aracı şu anda başka bir test denetleyicisinde çalışacak şekilde yapılandırıldıysa, test aracısını o denetleyiciden kaldırmanız gerekir.

## <a name="remove-a-test-agent-from-a-test-controller"></a>Test denetleyicisinden test aracısını kaldırma

Bir test aracısının kaldırılmadan önce çevrimdışı duruma ayarlanması gerekir.

::: moniker range="vs-2017"
> [!NOTE]
> Laboratuvar ortamının bir parçası olarak bir denetleyiciye kayıtlı aracıları kaldırmak için bu yordamı kullanamazsınız. Bu aracıları bir denetleyiciden kaldırmak için Microsoft Test Yöneticisi kullanarak ortamı kaldırmanız gerekir.
::: moniker-end
::: moniker range=">=vs-2019"
> [!NOTE]
> Laboratuvar ortamının bir parçası olarak bir denetleyiciye kayıtlı aracıları kaldırmak için bu yordamı kullanamazsınız.
::: moniker-end

### <a name="to-remove-a-test-agent-from-a-test-controller"></a>Test denetleyicisinden bir test aracısı kaldırmak için

::: moniker range=">=vs-2019"
Visual Studio 2019 ' de, test denetleyicisi bir proje ile kayıtlıysa test aracısını kaldıramazsınız.
::: moniker-end
Test denetleyicisi bir projeye kayıtlı değilse, bu adımları izleyin.

1. Visual Studio test projeniz için test ayarları dosyasını açın, **rol** ' i seçin ve **denetleyici** alanı için açılan listeden **test denetleyicilerini yönet** ' i seçin.

   **Test denetleyicisini Yönet** iletişim kutusu görüntülenir.

2. **Denetleyici** açılan listesinde, test denetleyicisi 'ni ayarladığınız bilgisayarın adını yazın. Daha önce belirli bir test denetleyicisi yönetilmiyorsa listeden adı seçebilirsiniz.

3. **Aracılar** bölmesinde, test Aracısı adını seçin. Aracı hala çevrimiçiyse, çevrimdışı ' ı seçin **.** Kaldırmak için **Kaldır**' ı seçin.

   > [!NOTE]
   > Test aracısının kaldırılması, bunu test denetleyicisi ile ilişkilendirir. Test aracısını tamamen kaldırmak için, test aracısı bilgisayarındaki  **Programlar ve Özellikler** denetim masasını kullanın.

::: moniker range="vs-2017"
Test denetleyicisi bir proje ile kayıtlıysa, Microsoft Test Yöneticisi kullanarak aracıyı kaldırın.
::: moniker-end

## <a name="change-the-settings-for-a-test-agent"></a>Test Aracısı için ayarları değiştirme

Test aracısının durumu aşağıdaki değerlerden herhangi biri olabilir:

|Durum|Açıklama|
|-|-----------------|
|Test çalıştırılıyor|Testleri çalıştırma|
|Hazır|Testleri çalıştırmak veya veri ve tanılama toplamak için kullanılabilir|
|Çevrimdışı|Testleri çalıştırmak veya veri ve tanılama toplamak için kullanılamaz|
|Bağlantı kesildi|Test aracısı başlatılmadı|

Aşağıdaki yordamları kullanarak bir test aracısının durumunu ve diğer ayarlarını değiştirebilirsiniz.

### <a name="to-change-the-settings-of-a-test-agent"></a>Bir test aracısının ayarlarını değiştirmek için

::: moniker range="vs-2017"
> [!NOTE]
> Test Aracısı bir proje ile kayıtlı bir test denetleyicisine kayıtlıysa, Microsoft Test Yöneticisi ayarları değiştirin.
::: moniker-end

1. test denetleyicisini ve bir yük testi için kayıtlı aracıları yapılandırmak ve izlemek için, Visual Studio ' de **yük testi** menüsünü seçin ve ardından **test denetleyicilerini yönet**' i seçin. diğer herhangi bir test için, Visual Studio ' de test projeniz için test ayarları dosyasını açın, **rol** ' i seçin ve **denetleyici** alanı için açılan listeden **test denetleyicilerini yönet** ' i seçin.

   **Test denetleyicisini Yönet** iletişim kutusu açılır.

1. Test denetleyicisi listesinde, test aracılarını değiştirmek istediğiniz test denetleyicisinin adını seçin. Test denetleyicisi listede görünmezse, test denetleyicisinin doğru şekilde kaydedilip kaydedilmadığını denetleyin. Daha fazla bilgi için, test denetleyicisi yapılandırma hakkında aşağıdaki yordama bakın.

1. Seçim **Test aracıları** bölmesinde, özelliklerini değiştirmek istediğiniz test aracısı bilgisayarını seçin.

1. **Özellikler**'i seçin.

1. Aşağıdaki test Aracısı özelliklerini gerekli şekilde değiştirin:

|Test Aracısı özelliği|Açıklama|
|-|-----------------|
|**Ağırlık**|Farklı performans düzeylerine sahip test aracılarını kullanırken yükü dağıtmak için kullanılır. Örneğin, ağırlık 100 olan bir test aracısı, 50 ağırlığı olan bir test aracısı olarak yükün iki katı kadar alır.|
|**IP Değiştirme**|IP geçişlerini yapılandırmak için kullanılır. IP değiştirme, bir test aracısına bir IP adresi aralığı kullanarak sunucuya istek göndermesini sağlar. Bu, farklı istemci bilgisayarlardan gelen çağrıların benzetimini sağlar.<br /><br /> Yük testi bir web grubu erişıyorsa IP Değiştirme önemlidir. Çoğu yük dengeci, istemcinin IP adresini kullanarak bir istemci ile belirli bir web sunucusu arasında benzeştir. Tüm istekler tek bir istemciden geliyor gibi görünüyorsa yük dengeleyici yükü dengelemez. Web grubu içinde iyi bir yük dengelemesi elde etmek için isteklerin bir dizi IP adresi aralığından olduğundan emin olun. **Not:**  Bir ağ bağdaştırıcısı belirtebilirsiniz veya şu anda kullanılmamış bir bağdaştırıcıyı otomatik olarak seçmek için **kullanabilirsiniz (Atanmamış** Tüm). <br /><br /> IP değiştirme özelliğini kullanmak için, Visual Studio Test Aracısı hizmetinin o aracı bilgisayarın Yöneticiler grubunda bir kullanıcı olarak çalışıyor olması gerekir. Bu kullanıcı aracı kurulumu sırasında seçilir, ancak hizmetin özellikleri değiştirerek ve yeniden başlatarak değiştirilebilir.<br /><br /> IP değiştirmenin düzgün çalıştığını doğrulamak için web sunucusunda IIS günlüğünü etkinleştirin, isteklerin yapılandırılan IP adreslerinden geldiğini doğrulamak için IIS günlük işlevini kullanın.|
|**Öznitelikler**|Test aracısı seçiminde kullanılan ad/değer çiftleri kümesi. Örneğin, bir test belirli bir işletim sistemi gerektirir. Öznitelikler, test ayarları **dosyanın** Roller sekmesinde kullanılmaktadır ve bunlar eşleşen özniteliklere sahip bir test aracısı seçmek için kullanılabilir. Birden çok makinede test çalıştırmak için, testlerinizi çalıştırmak üzere yapılandırılmış test ayarları rolünde bir öznitelik oluşturun ve ardından bu rolde kullanmak istediğiniz her test aracısında eşleşen bir öznitelik yapılandırabilirsiniz. **Not:**  Bu ayar yalnızca bir projeye kayıtlı bir test denetleyicisiyle kayıtlı test aracıları için kullanılabilir, çünkü bu öznitelikler yalnızca proje için test ayarlarında Visual Studio.|

Test aracısı ağırlığı ve test aracısı özniteliği değişiklikleri hemen etkili olur, ancak çalışan testleri etkilemez. Test denetleyicisi yeniden başlatıldıktan sonra IP Adresi Aralığı etkin olur.

(İsteğe bağlı) Test aracılarının durumunu değiştirmek için listeden aracıyı seçin ve ardından kullanılabilir seçeneklerden aracının geçerli durumuna göre eylemi seçin.

> [!NOTE]
> Test aracınız bir işlem olarak çalışıyorsa, test aracınız yüklü olan bilgisayarda çalışan bildirim alanı simgesinden test aracının durumunu yönetirsiniz. Bu, test aracılarının durumunu gösterir. Bu aracıyı kullanarak bir işlem olarak çalıştırılacaksa aracıyı başlatabilirsiniz, durdurabilir veya yeniden başlatabilirsiniz.

## <a name="configure-a-test-controller"></a>Test denetleyicisi yapılandırma

Bir test denetleyicisini yapılandırmak için Takım Test Denetleyicisi **Yapılandırma Aracı'nı kullan gerekir.** Test denetleyicinizi yapılandırarak test denetleyicinizi farklı bir proje koleksiyonuna kayded veya test denetleyicinizin proje koleksiyonundan kaydını sildiniz.

Test denetleyicinizi Team Foundation Server proje koleksiyonunuzla kaydetmek için, test denetleyicisi hizmeti için kullanabileceğiniz hesap, Project Koleksiyonu için Project Koleksiyonu Test Hizmeti Hesapları grubunun bir üyesi olmalıdır veya test denetleyicisi yapılandırma aracını çalıştırmak için kullanabileceğiniz hesap bir Project Koleksiyon Yöneticisi olmalıdır.

> [!NOTE]
> Bir proje koleksiyonunda mevcut ortamları olan bir proje koleksiyonundan bir test denetleyicisinin kaydını geri alıyorsanız, bu proje koleksiyonunu taşıdınız ve test denetleyicisini bu taşınan proje koleksiyonuna yeniden kaydettiyebilirsiniz.

### <a name="to-configure-a-test-controller"></a>Test denetleyicisini yapılandırmak için

1. Test denetleyicinizi istediğiniz zaman yeniden yapılandırmak üzere aracı çalıştırmak için Test Denetleyicisi Yapılandırma Aracını  >  **Başlat'ı seçin.**

     **Test Denetleyicisini Yapılandır** iletişim kutusu görüntülenir.

2. Test denetleyicisi hizmetiniz için oturum açma hesabı olarak kullanmak üzere kullanıcı seçin.

    > [!NOTE]
    > Kullanıcı hesapları için null parolalar desteklenmiyor.

4. (İsteğe bağlı) Test denetleyicinizi bir laboratuvar ortamıyla kullanmak istemiyorsanız, ancak yalnızca testlerinizi Visual Studio çalıştırmak için Test denetleyicisini **Team Project Collection'a kaydetme'Project.**

5. (İsteğe bağlı) Test denetleyicinizi yük testi için yapılandırmak üzere Test denetleyicisini **yük testi için yapılandır'ı seçin.** Aşağıdaki SQL Server örnek içinde **Yük testi sonuçları veritabanı oluştur altına SQL Server girin.**

> [!NOTE]
> Test denetleyicileri hakkında daha fazla sorun atış bilgisi için bkz. [Test aracılarını yükleme ve yapılandırma.](../test/lab-management/install-configure-test-agents.md)

## <a name="manage-your-agents-when-you-run-your-tests-with-a-test-controller"></a>Testlerinizi bir test denetleyicisiyle çalıştırarak aracılarınızı yönetme

Uygulamanıza rol eklemek için test ayarlarınıza rol Visual Studio, rollerinizin her biri için aracı özellikleri ekebilirsiniz. Bu, bu rol için hangi test aracılarının kullanılabilir olduğunu belirler. Testlerinizi bu test ayarlarını kullanarak çalıştırsanız, test ayarları için seçilen test denetleyicisi gerekli aracıların kullanılabilirliğini belirler. Aracı kullanılabilirliği belirlen olduğunda aşağıdaki durumlar ortaya çıkabilir:

- Testleri çalıştırması gereken rol için aracı yoktur. Testlerinizi çalıştıramaz. Aşağıdaki eylemlerden birini gerçekleştirin ve ardından testlerinizi yeniden çalıştırabilirsiniz:

  - Bu rolün testleri çalıştırması için bir aracının kullanılabilir olması için bekleyebilirsiniz.

  - Bu rol için kullanılabilen çevrimdışı aracılar varsa, kullanılabilir olması için aracıyı yeniden başlatabilirsiniz.

  - Bu rol için doğru aracı özelliklerine sahip başka bir aracıyı test denetleyicisine ebilirsiniz.

  - Kullanmak istediğiniz diğer aracıları etkinleştirmek için test ayarlarında bu rolün aracı özelliklerini değiştirebilirsiniz.

- Tanılama veri bağdaştırıcıları çalıştıran bir veya daha fazla rol için aracı yoktur. Testlerinizi çalıştırabilirsiniz, ancak tanılama veri bağdaştırıcısı çalıştıramaz. Testlerinizi tanılama veri bağdaştırıcısı olmadan çalıştırabilirsiniz veya aşağıdaki eylemlerden birini gerçekleştirebilirsiniz ve testlerinizi yeniden çalıştırabilirsiniz:

  - Bir aracının bu roller için kullanılabilir olması için bekleyebilirsiniz.

  - Bu rol için kullanılan çevrimdışı aracılar varsa, Test menüsündeKimlik Testi Denetleyicisini Yönet'den aracının durumunu çevrimiçi **olarak** **değiştirebilirsiniz.** Ayrıca, denetleyiciyle bağlantısı kesilmişse aracıyı yeniden başlatmanız da gerekir.

  - Bu test çalıştırması için ihtiyacınız olan aracıların testleri çalıştırmakla meşgul olmadığını doğrulayın. Test menüsündeKimlik Denetleyicisini Yönet **menüsünden herhangi bir aracının** **durumunu kontrol** edin.

  - Rol için doğru aracı özelliklerine sahip başka bir aracıyı test denetleyicisine ebilirsiniz.

  - Kullanmak istediğiniz diğer aracıları etkinleştirmek için test ayarlarında rolün aracı özelliklerini değiştirebilirsiniz.

## <a name="load-tests-from-delay-signed-assemblies"></a>Gecikmeli imzalı derlemelerden test yükleme

Test denetleyicisi ve test aracıları yalnızca kesin olarak imzalanmış derlemeler veya imzasız derlemeler olan test derlemelerini yükleyemedi. Bazı test derlemeleri, uygulama için üretim derlemelerine erişimi olduğundan gecikmeli imzalıdır. Ancak, bu derlemeler yalnızca test derlemeleri olduğundan ve dağıtılmayıldığından kesin olarak imzalanmaz. Bu derlemeler gecikmeli imzalı olduğundan yüklenemediklerinden, test denetleyicisi makinesi de dahil olmak üzere derlemenin yüklenemiyor olduğu tüm makinelerde bu derlemeler için güçlü ad doğrulamasını devre dışı bırakmanız gerekir. Gecikmeli imzalı doğrulamayı devre dışı bırakmak için *sn.exe.* Güçlü ad doğrulamasının atlanması istenen gecikmeli imzalı derlemenin ortak anahtar belirteci de dahil edilebilir.

Gecikmeli *Sn.exe* doğrulamayı devre dışı bırakmak içinSn.exe(Güçlü Ad aracı) aracını kullanın.

Bu, yalnızca belirtilen derleme için, komutu üzerinde çalıştırdınız bilgisayarda, güçlü ad doğrulamasını devre dışı verir. Bunu yalnızca yeterli izinlere sahip olursanız bunu yapabiliriz.

Test çalıştırması tamamlandıktan sonra,SN.exekomutunu kullanarak gecikmeli *imzalama doğrulamasını yeniden* etkinleştirin.

İmzalama doğrulamasını devre dışı bırakmanın ve yeniden etkinleştirmenin önerilen bir yolu, *betiklerdeSN.exe* komutlarını kullanmaktır. Kurulum betiğinde doğrulamayı devre dışı bırakarak temizleme betiğinde doğrulamayı yeniden etkinleştirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Test aracılarını yükleme ve yapılandırma](../test/lab-management/install-configure-test-agents.md)
