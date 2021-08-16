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
ms.openlocfilehash: 4da4dd43094b5e16f5ebdbee54771296ceb15ad69d5fca5e356f86e682a4042d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121366504"
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
|**Ağırlıklı**|Farklı performans düzeyleriyle test aracıları kullandığınızda yükü dağıtmak için kullanılır. Örneğin, 100 ağırlığı olan bir test aracısı, yük, 50 ağırlığa sahip bir test aracısı olarak iki kat alır.|
|**IP değiştirme**|IP geçişini yapılandırmak için kullanılır. IP anahtarlama, bir test aracısının bir IP adresi aralığı kullanarak istekleri sunucuya göndermesini sağlar. Bu, farklı istemci bilgisayarlardan gelen çağrıların benzetimini yapar.<br /><br /> Yük testiniz bir Web grubuna erişiyorsa, IP geçişi önemlidir. Çoğu yük dengeleyiciler, istemcinin IP adresini kullanarak bir istemciyle belirli bir Web sunucusu arasında benzeşim kurar. Tüm istekler tek bir istemciden geliyor gibi görünüyorsa, yük dengeleyici yükü dengeetmez. Web grubunda iyi yük dengelemesi elde etmek için isteklerin bir IP adresi aralığından geldiğinden emin olun. **Note:**  Bir ağ bağdaştırıcısı belirtebilir veya şu anda kullanılmayan birini otomatik olarak seçmek için **(Tümü Atanmamış)** seçeneğini kullanabilirsiniz. <br /><br /> ıp anahtarlama özelliğini kullanmak için, Visual Studio Test aracısı hizmeti, aracı bilgisayar için yöneticiler grubunda bir kullanıcı olarak çalışıyor olmalıdır. Bu Kullanıcı, aracı kurulumu sırasında seçilir, ancak hizmetin özellikleri değiştirilerek yeniden başlatılarak değiştirilebilir.<br /><br /> IP geçişinin düzgün çalıştığını doğrulamak için Web sunucusunda IIS günlüğü 'nü etkinleştirin, isteklerin yapılandırdığınız IP adreslerinden geldiğini doğrulamak için IIS günlük oluşturma işlevini kullanın.|
|**Öznitelikler**|Test Aracısı seçiminde kullanılabilecek ad/değer çiftleri kümesi. Örneğin, bir test belirli bir işletim sistemi gerektirebilir. Öznitelikleri, test ayarları dosyanızın **Roller** sekmesine ekleyebilirsiniz ve eşleşen özniteliklere sahip bir test aracısı seçmek için kullanılabilirler. Birden çok makine üzerinde bir test çalıştırmak istiyorsanız, testlerinizi çalıştırmak için yapılandırılan test ayarları rolünde bir öznitelik oluşturun ve ardından bu rolde kullanmak istediğiniz her test aracısında eşleşen bir öznitelik yapılandırın. **Note:**  Bu ayar yalnızca, bir projeye kayıtlı olmayan bir test denetleyicisiyle kayıtlı test aracılarında kullanılabilir, çünkü bu öznitelikler yalnızca Visual Studio için test ayarlarında kullanılır.|

Test Aracısı ağırlığı ve test aracısı öznitelik değişiklikleri hemen yürürlüğe girer, ancak çalıştıran testleri etkilemez. IP adresi aralığı, test denetleyicisi yeniden başlatıldıktan sonra devreye girer.

Seçim Bir test aracısının durumunu değiştirmek için, listeden aracıyı seçin ve ardından aracının geçerli durumuna bağlı olarak kullanılabilir seçimlerden eylemi seçin.

> [!NOTE]
> Test aracınız bir işlem olarak çalışıyorsa, test aracısının durumunu test aracınızın yüklendiği bilgisayarda çalışan bildirim alanı simgesinden yönetirsiniz. Bu, test aracısının durumunu gösterir. Bu aracı kullanarak bir işlem olarak çalışıyorsa aracıyı başlatabilir, durdurabilir veya yeniden başlatabilirsiniz.

## <a name="configure-a-test-controller"></a>Test denetleyicisi yapılandırma

Bir test denetleyicisi yapılandırmak için, **takım test denetleyicisi yapılandırma aracını** kullanmanız gerekir. Test denetleyicinizi yapılandırırken, test denetleyicinizi farklı bir proje koleksiyonu ile kaydedebilir veya test denetleyicinizin kaydını bir proje koleksiyonundan silebilirsiniz.

test denetleyicinizi Team Foundation Server projesi koleksiyonunuza kaydetmek istiyorsanız, test denetleyicisi hizmeti için kullandığınız hesabın, Project koleksiyonu için Project koleksiyon test hizmeti hesapları grubunun bir üyesi olması veya test denetleyicisi yapılandırma aracını çalıştırmak için kullandığınız hesabın bir Project koleksiyon yöneticisi olması gerekir.

> [!NOTE]
> Bir test denetleyicisinin bir proje koleksiyonunda mevcut ortamları bulunan bir proje koleksiyonundan kaydını kaldırırsanız, bu proje koleksiyonunu taşıdıysanız ve test denetleyicisini taşınan proje koleksiyonuna yeniden kaydettiğinizde, ortamlar hala sürdürülür.

### <a name="to-configure-a-test-controller"></a>Bir test denetleyicisini yapılandırmak için

1. Test denetleyicinizi istediğiniz zaman yeniden yapılandırmak üzere aracı çalıştırmak için,   >  **Test denetleyicisi yapılandırma aracını** Başlat ' ı seçin.

     **Test denetleyicisini Yapılandır** iletişim kutusu görüntülenir.

2. Test denetleyicisi hizmetiniz için oturum açma hesabı olarak kullanılacak kullanıcıyı seçin.

    > [!NOTE]
    > Kullanıcı hesaplarında null parolalar desteklenmez.

4. Seçim test denetleyicinizi laboratuvar ortamıyla kullanmak istemiyorsanız, ancak yalnızca Visual Studio testleri çalıştırmak için, **test denetleyicisini takım Project koleksiyonuyla kaydet**' i temizleyin.

5. Seçim Test denetleyicinizi yük testi için yapılandırmak için **Test denetleyicisini yük testi Için Yapılandır**' ı seçin. **aşağıdaki SQL Server örneğinde yük testi sonuçları veritabanı oluştur** altında SQL Server örneğini girin.

> [!NOTE]
> Test denetleyicileri hakkında daha fazla sorun giderme için bkz. [test aracılarını yükleyip yapılandırma](../test/lab-management/install-configure-test-agents.md).

## <a name="manage-your-agents-when-you-run-your-tests-with-a-test-controller"></a>Testlerinizi bir test denetleyicisi ile çalıştırdığınızda aracılarınızı yönetin

Visual Studio için test ayarlarınıza uygulamanız için roller eklediğinizde, rollerinizin her biri için aracı özellikleri ekleyebilirsiniz. Bu, hangi test aracılarının bu rol için kullanılabilir olduğunu belirler. Bu test ayarlarını kullanarak testlerinizi çalıştırdığınızda, test ayarları için seçilen test denetleyicisi gerekli aracıların kullanılabilirliğini belirler. Bunlar, aracı kullanılabilirliği belirleniyorsa oluşabilecek aşağıdaki durumlardır:

- Testleri çalıştırması gereken rol için kullanılabilir aracı yok. Testleriniz çalıştırılamaz. Aşağıdaki eylemlerden birini gerçekleştirip testlerinizi yeniden çalıştırabilirsiniz:

  - Bu rolün testleri çalıştırması için bir aracının kullanılabilir olmasını bekleyebilirsiniz.

  - Bu rol için kullanılabilen çevrimdışı aracılar varsa, kullanılabilir olması için aracıyı yeniden başlatabilirsiniz.

  - Test denetleyicisine bu rolün doğru aracı özelliklerine sahip başka bir aracı ekleyebilirsiniz.

  - Kullanmak istediğiniz diğer aracıları etkinleştirmek için test ayarlarında bu rolün aracı özelliklerini değiştirebilirsiniz.

- Tanılama veri bağdaştırıcılarını çalıştıran bir veya daha fazla rol için kullanılabilir aracı yok. Testleriniz çalıştırılabilir, ancak tanılama veri bağdaştırıcısı çalıştırılamaz. Testlerinizi tanılama veri bağdaştırıcısı olmadan çalıştırabilir veya aşağıdaki eylemlerden birini gerçekleştirip testlerinizi yeniden çalıştırabilirsiniz:

  - Bu roller için bir aracının kullanılabilir olmasını bekleyebilirsiniz.

  - Bu rol için kullanılabilen çevrimdışı aracılar varsa, **Test** menüsündeki **Test denetleyicisini Yönet** ' e, aracının durumunu çevrimiçi olarak değiştirmeniz gerekir. Ayrıca, denetleyicinin bağlantısı kesildiyse aracıyı yeniden başlatmanız gerekebilir.

  - Bu test çalıştırması için ihtiyaç duyduğunuz tüm aracıların testleri çalıştırmakla meşgul olmadığından emin olun. **Test menüsündeki** **Test denetleyicisini Yönet** ' den herhangi bir aracının durumunu kontrol edebilirsiniz.

  - Rolün test denetleyicisine doğru aracı özelliklerine sahip başka bir aracı ekleyebilirsiniz.

  - Kullanmak istediğiniz diğer aracıları etkinleştirmek için test ayarlarındaki rolün aracı özelliklerini değiştirebilirsiniz.

## <a name="load-tests-from-delay-signed-assemblies"></a>Gecikmeli imzalanmış derlemelerden test yükleme

Test denetleyicisi ve test aracıları, yalnızca kesin olarak imzalanmış derlemelerin veya imzasız derlemelerin test derlemelerini yükleyebilir. Bazı test derlemeleri, uygulama için üretim derlemelerine erişimi olması gerektiğinden gecikmeli imzalanmıştır. Ancak, bu derlemeler yalnızca test derlemeleri olduklarından ve dağıtılmadığından sağlam bir şekilde imzalanmamıştır. Bu derlemeler gecikmeli imzalanmış olduklarından yüklenemez, bu nedenle, derlemenin test denetleyicisi makinesi dahil yükleneceği tüm makinelerde, bu derlemeler için tanımlayıcı ad doğrulamasını devre dışı bırakmanız gerekir. Gecikmeli imzalanmış doğrulamayı devre dışı bırakmak için *sn.exe* kullanın. Tanımlayıcı ad doğrulamasının atlandığı, gecikmeli imzalanmış derlemenin ortak anahtar belirtecinin da dahil olması gerekebilir.

Gecikmeli imzalanmış doğrulamayı devre dışı bırakmak için *Sn.exe* (tanımlayıcı ad aracı) kullanın.

Bu, yalnızca belirtilen derleme için komutu çalıştırdığınız bilgisayardaki tanımlayıcı ad doğrulamasını devre dışı bırakır. Bunu yalnızca yeterli izinleriniz varsa yapabilirsiniz.

Test çalıştırması tamamlandıktan sonra, *SN.exe* komutunu kullanarak Gecikmeli imzalama doğrulamasını yeniden etkinleştirin.

İmzalama doğrulamasının devre dışı bırakılması ve yeniden etkinleştirilmesi için önerilen bir yol, betiklerdeki *SN.exe* komutlarını kullanmaktır. Bir kurulum komut dosyasında doğrulamayı devre dışı bırakabilir ve bir temizleme komut dosyasında doğrulamayı yeniden etkinleştirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Test aracılarını yükleme ve yapılandırma](../test/lab-management/install-configure-test-agents.md)
