---
title: Test denetleyicilerini ve test aracılarını yönetme
description: Test denetleyicilerini ve test aracılarını ilk kez yükledikten ve yapılandırdikten sonra yönetmeyi öğrenin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628088"
---
# <a name="manage-test-controllers-and-test-agents"></a>Test denetleyicilerini ve test aracılarını yönetme

Testleri uzaktan çalıştırmak, Visual Studio makineye dağıtmak veya yük testleri çalıştırmak için bir test denetleyicisi, test aracıları ve test ayarları dosyası yapılandırmanız gerekir. Bu konuda, test denetleyicilerini ve test aracılarını ilk kez yükledikten ve yapılandırdikten sonra nasıl yönetebilirsiniz?

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

::: moniker range="vs-2017"
Laboratuvar ortamlarında Microsoft Test Yöneticisi için Microsoft Test Yöneticisi kullanırsanız, test denetleyicilerini ve onların aracılarını yönetmek için Laboratuvar Merkezi'nde **Test** Denetleyicisi Yöneticisi'ni  Microsoft Test Yöneticisi. Bu konu yalnızca testleri çalıştırmak için Visual Studio geçerlidir.
::: moniker-end

Test aracılarını ve test denetleyicilerini yükleme ve yapılandırma hakkında bilgi için bkz. Test aracılarını Visual Studio [denetleyicilerini yapılandırma.](../test/configure-test-agents-and-controllers-for-load-tests.md)

Test denetleyicisini ve kayıtlı aracıları yapılandırmak ve izlemek için test projesinde çalıştırmak istediğiniz testleri içeren bir test ayarları dosyası olmalıdır. Test ayarları dosyasını açın, **Rol'e tıklayın** ve Denetleyici **alanı açılır menüsünden Test** Denetleyicilerini Yönet'i seçin. 

Yük testi projesi için Yük Testi menüsünden **Test Denetleyicilerini** **Yönet'i de seçebilirsiniz.**

## <a name="add-a-test-agent-to-a-test-controller"></a>Test denetleyicisine test aracısı ekleme

Farklı bir test denetleyicisine test aracısı eklemek veya yeni yüklemiş olabileceğiniz bir test denetleyicisine test aracısı eklemek zorunda da olabilir.

### <a name="to-add-a-test-agent-to-a-test-controller"></a>Test denetleyicisine test aracısı eklemek için

1. Test **Aracısı Yapılandırma** Aracını  >  **Başlat'ı seçin.**

     Test **Aracılarını Yapılandır** iletişim kutusu görüntülenir.

    > [!NOTE]
    > Bir test denetleyicisine eklemek için zaten yüklü bir test aracınız olmalıdır. Bir test aracısı yükleme hakkında daha fazla bilgi için bkz. Test [aracılarını yükleme ve yapılandırma.](../test/lab-management/install-configure-test-agents.md)

2. Test aracısına nasıl çalıştırılana iki seçenek sunulmaktadır:

   - **Hizmet:** Kodlanmış UI testleri gibi masaüstüyle etkileşimde olan otomatikleştirilmiş testler çalıştırmanız veya test çalıştırmanız sırasında bir video kaydı oluşturma gibi otomatikleştirilmiş testler çalıştırmanız gerek yoksa, Test aracılarını farklı çalıştır'ın **altında** Hizmet'i **seçin.** Test aracısı hizmet olarak başlatacak. **İleri**’yi seçin.

      Artık test aracısı hizmet olarak başladığında kullanıcıyla ilgili ayrıntıları girebilirsiniz.

      1. Kullanıcı adı alanına **adı girin.**

      2. Parola alanına **parolayı girin.**

        |**Önemli kullanıcı hesabı bilgileri**|
        |-|
        |- Kullanıcı hesapları için null parolalar desteklenmiyor.|
        |- IntelliTrace toplayıcısı veya ağ öykünmesi kullanmak için kullanıcı hesabının Yöneticiler grubunun bir üyesi olması gerekir.|
        |- Aracı kullanıcı adı aracı hizmetinde yoksa, test denetleyicisi üzerinde izinler gerektiren aracıyı eklemeye dener.|
        |- Test denetleyicisini kullanmaya çalışan kullanıcının test denetleyicisinin Kullanıcılar hesabında olması gerekir, yoksa denetleyiciye karşı testleri çalıştıramaz.|

   - **Etkileşimli İşlem:** Kodlanmış UI testleri gibi masaüstüyle etkileşim kurması gereken otomatikleştirilmiş testler çalıştırmak veya test çalıştırmanız sırasında bir video kaydı oluşturmak için Etkileşimli **İşlem'i seçin.** Test aracısı, hizmet yerine etkileşimli bir işlem olarak başlatacağız.

      Sonraki sayfada, test aracısı işlem olarak başladığında kullanıcıyla ilgili ayrıntıları ve diğer seçenekleri girin.

      1. Kullanıcı adı alanına **adı girin.**

      2. Parola alanına **parolayı girin.**

        > [!NOTE]
        > Test aracıyı etkin kullanıcı olan farklı bir kullanıcıyla etkileşimli bir işlem olarak çalıştırılacak şekilde yapılandırdısanız, aracıyı başlatabilecek şekilde bilgisayarı yeniden başlatmanız ve bu farklı kullanıcı olarak oturum açmanız gerekir. Ayrıca, kullanıcı hesapları için null parolalar desteklanmaz. IntelliTrace toplayıcısı veya ağ öykünmesi kullanmak için kullanıcı hesabının Yöneticiler grubunun bir üyesi olması gerekir.

      3. Test aracısı olan bir bilgisayarın yeniden başlatıldıktan sonra testleri çalıştırana kadar bilgisayarı test aracısı kullanılırken otomatik olarak oturum açacak şekilde ayarlayabilirsiniz. Otomatik olarak **oturum aç'ı seçin.** Bu, kullanıcı adını ve parolayı kayıt defterinde şifrelenmiş bir biçimde depolar.

      4. Bu durum masaüstüyle etkileşim kurması gereken otomatikleştirilmiş testlerle etkileşeyene kadar ekran koruyucunun devre dışı bırakıldı olduğundan emin olmak için Ekran **koruyucunun devre dışı bırakıldı olduğundan emin olun'ı seçin.**

        > [!WARNING]
        > Otomatik olarak oturum asanız veya ekran koruyucusunu devre dışı bırakırsanız güvenlik riskleri vardır. Otomatik oturum açma özelliğini etkinleştirerek, diğer kullanıcıların bu bilgisayarı başlatmalarını ve otomatik olarak oturum açtığı hesabı kullanamalarını sağlarsınız. Ekran koruyucusunu devre dışı bırakırsanız, bilgisayar bir kullanıcının bilgisayarın kilidini açmak için oturum açmasını isteminde çalışmayabilir. Bu, bilgisayara fiziksel erişimi olan herkesin makineye erişmelerine olanak sağlar. Bu özellikleri bir bilgisayarda etkinleştirirsanız, bu bilgisayarların fiziksel olarak güvenli olduğundan emin olun. Örneğin, bu bilgisayarlar fiziksel olarak güvenli bir laboratuvarda bulunur. (Ekran koruyucunun **devre dışı bırakıldı olduğundan emin olmak** ayarını temizlersanız bu, ekran koruyucusunu etkinleştirmez.)

3. Bu aracıyı farklı bir test denetleyicisine kaydetmek için Test denetleyicisiyle **kaydol'a tıklayın.** Test denetleyicinizin adını ve ardından **gelen** adını ve test aracısını aşağıdaki test denetleyicisine kaydetme içinde **kullanmakta olduğunu bağlantı noktası numarasını yazın.** Örneğin, **agent1:6901yazdır.**

    > [!NOTE]
    > Varsayılan bağlantı noktası numarası 6901'tir.

4. Değişikliklerinizi kaydetmek için Uygulama'Ayarlar. Yapılandırma özeti **iletişim** kutusunu kapatın ve ardından Test Aracısı **Yapılandırma Aracı'nı kapatın.**

> [!WARNING]
> Aracı şu anda başka bir test denetleyicisinde çalıştıracak şekilde yapılandırılmışsa, test aracısını o denetleyiciden kaldırmanız gerekir.

## <a name="remove-a-test-agent-from-a-test-controller"></a>Test denetleyicisinden test aracısını kaldırma

Bir test aracısı kaldırılamadan önce çevrimdışı duruma ayarılmalıdır.

::: moniker range="vs-2017"
> [!NOTE]
> Laboratuvar ortamının bir parçası olarak bir denetleyiciye kayıtlı aracıları kaldırmak için bu yordamı kullanasınız. Bu aracıları bir denetleyiciden kaldırmak için, bu aracıları kullanarak ortamı Microsoft Test Yöneticisi.
::: moniker-end
::: moniker range=">=vs-2019"
> [!NOTE]
> Laboratuvar ortamının bir parçası olarak bir denetleyiciye kayıtlı aracıları kaldırmak için bu yordamı kullanasınız.
::: moniker-end

### <a name="to-remove-a-test-agent-from-a-test-controller"></a>Test denetleyicisinden test aracısını kaldırmak için

::: moniker range=">=vs-2019"
Bu Visual Studio 2019'da, test denetleyicisi bir projeye kayıtlı ise test aracısını kaldırabilirsiniz.
::: moniker-end
Test denetleyicisi bir projeye kayıtlı değilse aşağıdaki adımları izleyin.

1. Bu Visual Studio test projenizin test ayarları dosyasını açın, Rol'e tıklayın ve Denetleyici alanı açılır **menüsünden Test** Denetleyicilerini Yönet'i seçin.  

   Test **Denetleyicisini Yönet** iletişim kutusu görüntülenir.

2. Denetleyici **açılan** listesinde, test denetleyicisini ayar listeniz olan bilgisayarın adını yazın. Daha önce belirli bir test denetleyicisini yönettiyebilirsiniz, listeden adı seçebilirsiniz.

3. Aracılar **bölmesinde** test aracısı adını seçin. Aracı hala çevrimiçi ise Çevrimdışı'ı **seçin.** Kaldırmak için Kaldır'ı **seçin.**

   > [!NOTE]
   > Bir test aracısını kaldırmak yalnızca test denetleyicisiyle olan ilişkilendirilmemiş olur. Test aracısini tamamen kaldırmak için, test  **aracısı** bilgisayarın Denetim Masası Programlar ve Özellikler'i kullanın.

::: moniker range="vs-2017"
Test denetleyicisi bir projeye kayıtlı ise, aracıyı Microsoft Test Yöneticisi.
::: moniker-end

## <a name="change-the-settings-for-a-test-agent"></a>Test aracısı ayarlarını değiştirme

Test aracılarının durumu aşağıdaki değerlerden herhangi biri olabilir:

|Durum|Açıklama|
|-|-----------------|
|Test Çalıştırma|Testleri çalıştırma|
|Hazır|Testleri çalıştırmak veya veri ve tanılama toplamak için kullanılabilir|
|Çevrimdışı|Testler çalıştırılamıyor veya veri ve tanılama toplanamıyor|
|Bağlantı kesildi|Test aracısı başlamadı|

Aşağıdaki yordamları kullanarak bir test aracısına ilişkin durumu ve diğer ayarları değiştirebilirsiniz.

### <a name="to-change-the-settings-of-a-test-agent"></a>Test aracılarının ayarlarını değiştirmek için

::: moniker range="vs-2017"
> [!NOTE]
> Test aracısı bir projeyle kaydedilmiş bir test denetleyicisine kayıtlı ise, test denetleyicisinin Microsoft Test Yöneticisi.
::: moniker-end

1. Bir yük testi için test denetleyicisini ve kayıtlı aracıları yapılandırmak ve izlemek için, Visual Studio'de Yük Testi menüsünü seçin ve ardından **Test Denetleyicilerini Yönet'i seçin.**  Diğer tüm testler için test projenizin test ayarları dosyasını Visual Studio, Rol'Visual Studio seçin ve Denetleyici alanı açılır **menüsünden Test** Denetleyicilerini Yönet'i seçin.  

   **Test Denetleyicisini Yönet** iletişim kutusu açılır.

1. Test denetleyicisi listesinde test aracılarını değiştirmek istediğiniz test denetleyicisinin adını seçin. Test denetleyicisi listede görünmüyorsa, test denetleyicisinin doğru kaydedilmiş olup olmadığını denetleyin. Daha fazla bilgi için, bir test denetleyicisini yapılandırma hakkında aşağıdaki yordama bakın.

1. (İsteğe bağlı) Test **Aracıları** bölmesinde, özelliklerini değiştirmek istediğiniz test aracısı bilgisayarlarını seçin.

1. **Özellikler**'i seçin.

1. Aşağıdaki test aracısı özelliklerini gereken şekilde değiştirin:

|Test Aracısı Özelliği|Description|
|-|-----------------|
|**Ağırlık**|Farklı performans düzeylerine sahip test aracılarını kullanırken yükü dağıtmak için kullanılır. Örneğin, ağırlık 100 olan bir test aracısı, 50 ağırlığı olan bir test aracısı olarak yükün iki katı kadar alır.|
|**IP Değiştirme**|IP değiştirmeyi yapılandırmak için kullanılır. IP değiştirme, bir test aracısına bir IP adresi aralığı kullanarak sunucuya istek göndermesini sağlar. Bu, farklı istemci bilgisayarlardan gelen çağrıların benzetimini sağlar.<br /><br /> Yük testi bir web grubu erişıyorsa IP Değiştirme önemlidir. Çoğu yük dengeci, istemcinin IP adresini kullanarak bir istemci ile belirli bir web sunucusu arasında benzeştir. Tüm istekler tek bir istemciden geliyor gibi görünüyorsa yük dengeleyici yükü dengelemez. Web grubu üzerinde iyi yük dengelemesi elde etmek için isteklerin bir dizi IP adresi aralığından geliyor olduğundan emin olun. **Not:**  Bir ağ bağdaştırıcısı belirtebilirsiniz veya şu anda kullanılmamış bir bağdaştırıcıyı otomatik olarak seçmek için **kullanabilirsiniz (Atanmamış** Tüm). <br /><br /> IP değiştirme özelliğini kullanmak için, Visual Studio Test Aracısı hizmetinin o aracı bilgisayarın Yöneticiler grubunda bir kullanıcı olarak çalışıyor olması gerekir. Bu kullanıcı aracı kurulumu sırasında seçilir, ancak hizmetin özellikleri değiştirerek ve yeniden başlatarak değiştirilebilir.<br /><br /> IP değiştirmenin düzgün çalıştığını doğrulamak için web sunucusunda IIS günlüğünü etkinleştirin, isteklerin yapılandırılan IP adreslerinden geldiğini doğrulamak için IIS günlük işlevini kullanın.|
|**Öznitelikler**|Test aracısı seçiminde kullanılan ad/değer çiftleri kümesi. Örneğin, bir test belirli bir işletim sistemi gerektirir. Öznitelikler, test ayarları **dosyanın** Roller sekmesinde kullanılmaktadır ve bunlar eşleşen özniteliklere sahip bir test aracısı seçmek için kullanılabilir. Birden çok makinede test çalıştırmak için, testlerinizi çalıştırmak üzere yapılandırılmış test ayarları rolünde bir öznitelik oluşturun ve ardından bu rolde kullanmak istediğiniz her test aracısında eşleşen bir öznitelik yapılandırabilirsiniz. **Not:**  Bu ayar yalnızca bir projeye kayıtlı bir test denetleyicisiyle kayıtlı test aracıları için kullanılabilir, çünkü bu öznitelikler yalnızca bir proje için test ayarlarında Visual Studio.|

Test aracısı ağırlığı ve test aracısı özniteliği değişiklikleri hemen etkili olur, ancak çalışan testleri etkilemez. Test denetleyicisi yeniden başlatıldıktan sonra IP Adresi Aralığı etkin olur.

(İsteğe bağlı) Test aracılarının durumunu değiştirmek için listeden aracıyı seçin ve ardından aracının geçerli durumuna göre kullanılabilir seçeneklerden eylemi seçin.

> [!NOTE]
> Test aracınız bir işlem olarak çalışıyorsa, test aracınız yüklü olan bilgisayarda çalışan bildirim alanı simgesinden test aracının durumunu yönetirsiniz. Bu, test aracılarının durumunu gösterir. Bu aracıyı kullanarak bir işlem olarak çalıştırılacaksa aracıyı başlatabilirsiniz, durdurabilir veya yeniden başlatabilirsiniz.

## <a name="configure-a-test-controller"></a>Test denetleyicisi yapılandırma

Bir test denetleyicisini yapılandırmak için Takım Test Denetleyicisi **Yapılandırma Aracı'nı kullan gerekir.** Test denetleyicinizi yapılandırarak test denetleyicinizi farklı bir proje koleksiyonuna kayded veya test denetleyicinizin proje koleksiyonundan kaydını sildiniz.

Test denetleyicinizi Team Foundation Server proje koleksiyonunuzla kaydetmek için, test denetleyicisi hizmeti için kullanabileceğiniz hesabın Project Koleksiyonu için Project Koleksiyonu Test Hizmeti Hesapları grubunun bir üyesi olması veya test denetleyicisi yapılandırma aracını çalıştırmak için kullanmakta olduğu hesabın Project Koleksiyon Yöneticisi olması gerekir.

> [!NOTE]
> Bir proje koleksiyonunda mevcut ortamları olan bir proje koleksiyonundan bir test denetleyicisinin kaydını geri alıyorsanız, bu proje koleksiyonunu taşıdınız ve test denetleyicisini bu taşınan proje koleksiyonuna yeniden kaydettiyebilirsiniz.

### <a name="to-configure-a-test-controller"></a>Test denetleyicisini yapılandırmak için

1. Test denetleyicinizi istediğiniz zaman yeniden yapılandırmak üzere aracı çalıştırmak için Test Denetleyicisi Yapılandırma Aracını  >  **Başlat'ı seçin.**

     **Test Denetleyicisini Yapılandır** iletişim kutusu görüntülenir.

2. Test denetleyicisi hizmetiniz için oturum açma hesabı olarak kullanmak üzere kullanıcı seçin.

    > [!NOTE]
    > Kullanıcı hesapları için null parolalar desteklenmiyor.

4. (İsteğe bağlı) Test denetleyicinizi bir laboratuvar ortamıyla kullanmak istemiyorsanız, ancak yalnızca testlerinizi Visual Studio çalıştırmak için Test denetleyicisini **Team Project Collection'a kaydetme'Project.**

5. (İsteğe bağlı) Test denetleyicinizi yük testi için yapılandırmak üzere Test denetleyicisini **yük testi için yapılandır'ı seçin.** Aşağıdaki SQL Server örnek **içinde Yük testi sonuçları veritabanı oluştur altına SQL Server girin.**

> [!NOTE]
> Test denetleyicileri hakkında daha fazla sorun atış bilgisi için bkz. [Test aracılarını yükleme ve yapılandırma.](../test/lab-management/install-configure-test-agents.md)

## <a name="manage-your-agents-when-you-run-your-tests-with-a-test-controller"></a>Testlerinizi bir test denetleyicisiyle çalıştırarak aracılarınızı yönetme

Uygulamanıza rol eklemek için test ayarlarınıza Visual Studio rollerinizi her biri için aracı özellikleri ebilirsiniz. Bu, bu rol için hangi test aracılarının kullanılabilir olduğunu belirler. Testlerinizi bu test ayarlarını kullanarak çalıştırsanız, test ayarları için seçilen test denetleyicisi gerekli aracıların kullanılabilirliğini belirler. Aracı kullanılabilirliği belirlen olduğunda aşağıdaki durumlar ortaya çıkabilir:

- Testleri çalıştırması gereken rol için aracı yoktur. Testlerinizi çalıştıramaz. Aşağıdaki eylemlerden birini gerçekleştirin ve ardından testlerinizi yeniden çalıştırabilirsiniz:

  - Bu rolün testleri çalıştırması için bir aracının kullanılabilir olması için bekleyebilirsiniz.

  - Bu rol için kullanılabilen çevrimdışı aracılar varsa, kullanılabilir olması için aracıyı yeniden başlatabilirsiniz.

  - Bu rol için doğru aracı özelliklerine sahip başka bir aracıyı test denetleyicisine ebilirsiniz.

  - Kullanmak istediğiniz diğer aracıları etkinleştirmek için test ayarlarında bu rolün aracı özelliklerini değiştirebilirsiniz.

- Tanılama veri bağdaştırıcıları çalıştıran bir veya daha fazla rol için aracı yoktur. Testlerinizi çalıştırabilirsiniz, ancak tanılama veri bağdaştırıcısı çalıştıramaz. Testlerinizi tanılama veri bağdaştırıcısı olmadan çalıştırabilirsiniz veya aşağıdaki eylemlerden birini gerçekleştirebilirsiniz ve testlerinizi yeniden çalıştırabilirsiniz:

  - Bir aracının bu roller için kullanılabilir olması için bekleyebilirsiniz.

  - Bu rol için kullanılan çevrimdışı aracılar varsa, Test **menüsündeKimlik** Testi Denetleyicisini Yönet'den aracının durumunu çevrimiçi olarak **değiştirebilirsiniz.** Ayrıca, denetleyiciyle bağlantısı kesilmişse aracıyı yeniden başlatmanız da gerekir.

  - Bu test çalıştırması için ihtiyacınız olan aracıların testleri çalıştırmakla meşgul olmadığını doğrulayın. Test menüsündeKimlik Denetleyicisini Yönet **menüsünden aracıların** durumunu **kontrol** edin.

  - Rol için doğru aracı özelliklerine sahip başka bir aracıyı test denetleyicisine ebilirsiniz.

  - Kullanmak istediğiniz diğer aracıları etkinleştirmek için test ayarlarında rolün aracı özelliklerini değiştirebilirsiniz.

## <a name="load-tests-from-delay-signed-assemblies"></a>Gecikmeli imzalı derlemelerden test yükleme

Test denetleyicisi ve test aracıları yalnızca kesin olarak imzalanmış derlemeler veya imzasız derlemeler olan test derlemelerini yükleyemedi. Bazı test derlemeleri, uygulama için üretim derlemelerine erişimi olduğundan gecikmeli imzalıdır. Ancak, bu derlemeler yalnızca test derlemeleri olduğundan ve dağıtılmayıldığından kesin olarak imzalanmaz. Bu derlemeler gecikmeli imzalı olduğundan yüklenemiyor, bu nedenle test denetleyicisi makinesi de dahil olmak üzere derlemenin yükleniyor olduğu tüm makinelerde bu derlemeler için güçlü ad doğrulamasını devre dışı bırakmanız gerekir. Gecikmeli imzalı doğrulamayı devre dışı bırakmak için *sn.exe.* Güçlü ad doğrulamasının atlanması istenen gecikmeli imzalı derlemenin ortak anahtar belirteci de dahil edilebilir.

Gecikmeli *Sn.exe* doğrulamayı devre dışı bırakmak içinSn.exe(Güçlü Ad aracı) aracını kullanın.

Bu, yalnızca belirtilen derleme için, komutu üzerinde çalıştırarak bilgisayarda güçlü ad doğrulamasını devre dışı verir. Bunu yalnızca yeterli izinlere sahip olursanız bunu yapabiliriz.

Test çalıştırması tamamlandıktan sonra,SN.exekomutunu kullanarak *gecikmeli imzalama doğrulamasını yeniden* etkinleştirin.

İmzalama doğrulamasını devre dışı bırakmanın ve yeniden etkinleştirmenin önerilen bir yolu, *betiklerdeSN.exe* komutlarını kullanmaktır. Kurulum betiğinde doğrulamayı devre dışı bırakarak temizleme betiğinde doğrulamayı yeniden etkinleştirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Test aracılarını yükleme ve yapılandırma](../test/lab-management/install-configure-test-agents.md)
