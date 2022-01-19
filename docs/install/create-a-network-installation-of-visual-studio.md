---
title: Ağ tabanlı yükleme oluşturma
description: kuruluş içinde Visual Studio dağıtmak için bir ağ yüklemesi noktası oluşturmayı öğrenin.
ms.date: 12/7/2021
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 4CABFD20-962E-482C-8A76-E4012052F701
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 06ee527da845d9a0ecd400069d90cf94c1c9d1b1
ms.sourcegitcommit: ec474f32358861e1f62e92d8262051162f291edc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2022
ms.locfileid: "136924118"
---
# <a name="create-maintain-and-deploy-a-network-installation-of-visual-studio"></a>Visual Studio ağ yüklemesi oluşturun, bakımını yapın ve dağıtın

bazen bir kurumsal yönetici, istemci iş istasyonlarına dağıtılabilecek Visual Studio dosyaları içeren bir ağ yüklemesi noktası oluşturmak istemektedir. Bu, istemci makinelerin internet 'e sınırlı izinlere sahip olabileceği veya bir kuruluşun belirli bir geliştirici araç takımı sürümünde standartlaştırmak istediği durumlarda senaryoları kolaylaştırmaktır. bir yöneticinin bir iç ağ paylaşımında depolanabilecek bir ağ düzeni (dosya önbelleği) _oluşturup koruyabilmesi_ için Visual Studio tasarlıyoruz. ağ düzeni, hem ilk yükleme hem de sonraki ürün güncelleştirmeleri için gereken tüm Visual Studio dosyalarını içerir.

Bu Web sayfası hakkında çok fazla bilgi vardır ve aşağıdaki bölümlere göre gruplandırılır:

- [**Başlamadan önce**](#before-you-get-started): plan yaparken göz önünde bulundurmanız gereken ipuçları ve diğer önemli konular.
- [**Doğru önyükleyici edinin**](#download-the-visual-studio-bootstrapper-to-create-the-network-layout): nerede bulacağınızı ve kullanabileceğiniz çeşitli bootstrapsayısını nasıl ayırabileceğinizi gösteren rehberlik.
- [**Ağ düzeni oluşturma**](#create-the-network-layout): doğru ürün içeriği, kanal ayarları ve yükleyicinin sürümü ile düzenin nasıl oluşturulacağını ve bir ağ paylaşımının nasıl kopyalanacağını açıklar. 
- [**Ağ yerleşimini güncelleştirme, değiştirme ve koruma**](#update-or-modify-your-layout): düzenin ürün sürümünü, ürün içeriğini, kanal ayarlarını, yükleyici sürümünü ve klasör boyutunu güncelleştirme dahil olmak üzere, düzeninizi en iyi şekilde koruma hakkında bilgiler. 
- [**Düzeni istemci makinelere yükler**](#install-visual-studio-onto-a-client-machine-from-a-network-installation): varsayılan olarak yüklenecek iş yükleri ve bileşenler ve istemcinin güncelleştirmeleri arayacağı konum gibi istemci varsayılan ayarlarının nasıl yapılandırılacağını açıklar. ayrıca, Visual Studio düzeninin _ilk yüklemesinin_ istemci makinelere nasıl yapılacağını de içerir. düzenli olarak bir düzenden yüklenmiş _olan istemci makinelerini güncelleştirme hakkında_ rehberlik ve bilgiler, Visual Studio sayfanın [ağ tabanlı yüklemesi](update-a-network-installation-of-visual-studio.md) için ayrı güncelleştirme kapsamında ele alınmıştır.
- [**Yardım ve destek**](#get-support-for-your-network-layout): nereden yardım isteyeceğiz

## <a name="before-you-get-started"></a>Başlamadan önce

Çalışmaya başlamadan önce planlamanız ve farkında olmanız gereken önemli noktalar vardır.  
::: moniker range="vs-2017"

- **Klasör yönetimi:** kuruluşunuzda kullanımda olan Visual Studio birden çok sürümü varsa (örneğin, Visual Studio 2017 Professional ve Visual Studio 2017 Enterprise), her sürüm için ayrı bir ağ yüklemesi noktası oluşturmanız gerekir. ayrıca, orijinal Visual Studio yükleme düzeni ve sonraki tüm ürün güncelleştirmeleri, istemcinin onarma ve kaldırma işlevlerinin düzgün çalıştığından emin olmak için aynı ağ dizininde bulunmalıdır. Son olarak, Düzen yolu 80 karakterden kısa olmalıdır, ancak bazı kuruluşlar 80 karakterlik sınırlamaya geçici bir çözüm için [simgesel bağlantıları](/windows/win32/fileio/symbolic-links) başarıyla kullandı. 
- **Güncelleştirmeleri planlama:** İlk istemci yüklemesi _yapmadan önce_ istemci makinelerinizin ürün güncelleştirmelerini nasıl alması gerektiğine karar vermelisiniz. Bu, istemcilerinizin güncelleştirme konum yapılandırmasının doğru ayarlandığından emin olmak için gereklidir. Seçenekleriniz, istemcilerin ağ düzeni konumundan veya internet 'teki Microsoft tarafından barındırılan sunuculardan güncelleştirme almasını içerir. İstemci düzenden yüklendikten sonra, istemcinin güncelleştirme konumu yapılandırması kilitlidir ve korumasız olur. 

::: moniker-end

::: moniker range="vs-2019"

- **Klasör yönetimi:** kuruluşunuzda kullanımda olan Visual Studio birden çok sürümü varsa (örneğin, Visual Studio 2019 Professional ve Visual Studio 2019 Enterprise), her sürüm için ayrı bir ağ yüklemesi noktası oluşturmanız gerekir. Ayrıca, Düzen yolu 80 karakterden kısa olmalıdır, ancak bazı kuruluşlar 80 karakterlik sınırlamaya geçici bir çözüm için [simgesel bağlantıları](/windows/win32/fileio/symbolic-links) başarıyla kullandı. 
- **Güncelleştirmeleri planlama:** İlk istemci yüklemesi _yapmadan önce_ istemci makinelerinizin ürün güncelleştirmelerini nasıl alması gerektiğine karar vermeniz gerekir. Bu, istemcilerinizin güncelleştirme konum yapılandırmasının doğru ayarlandığından emin olmak için gereklidir. Seçenekleriniz, istemcilerin ağ düzeni konumundan veya internet 'teki Microsoft tarafından barındırılan sunuculardan güncelleştirme almasını içerir. 

 > [!IMPORTANT]
 > yalnızca Visual Studio 2019 işlevini kullandığınızda, düzen yönetimi ile aşağıdaki kısıtlama mevcuttur: istemci düzenden yüklendikten sonra, istemcinin güncelleştirme konumu kilitli ve korumasız olur. Bu, istemcilerinizin, onarım ve kaldırma işlevlerini koruyarak mizanpajınızdan güncelleştirme almasını amaçlıyorsanız, daha sonra tüm ürün güncelleştirmelerini istemcilerinizin yüklendiği _orijinal_ düzen klasörüne yerleştirmeniz gerekir. diğer bir deyişle, temel Visual Studio 2019 işlevi, bir istemcinin bir düzen konumundan özgün yükleme yapma **yeteneğini desteklemez ve** daha sonra bu istemcinin farklı bir düzen konumundan bir ürün güncelleştirmesi almasını sağlar. 
 > 
 > bu sınırlama, ürün güncelleştirme konumunun düzeltilme ve ürün güncelleştirmelerinin özgün yüklemesi düzeni Visual Studio 2022 ' de mevcut **olmadığından** aynı düzen klasöründe yer almalıdır. Visual Studio 2022 ' de, güncelleştirmelerin istemci kaynak konumunu kolayca değiştirebilirsiniz. Visual Studio 2019 düzenlerinizi yönetmek ve ürünün 2019 sürümündeki sınırlamayı ortadan kaldırmak için Visual Studio ürün ailesinin _tüm_ modern sürümlerini yöneten en son (Visual Studio 2022) yükleyiciyi dahil etmeniz ve kullanmanız mümkün yaptık. Aşağıdaki bölümde [, düzen her zaman dahil edilecek şekilde yapılandırılır ve en son yükleyiciyi sağlamak](#configure-the-layout-to-always-include-and-provide-the-latest-installer) bunun nasıl etkinleştirileceğini açıklar.
 
::: moniker-end

::: moniker range="vs-2022"

- **Klasör yönetimi:** kuruluşunuzda kullanımda olan Visual Studio birden çok sürümü varsa (örneğin, Visual Studio 2022 Professional ve Visual Studio 2022 Enterprise), her sürüm için ayrı bir ağ yüklemesi noktası oluşturmanız gerekir. Ayrıca, Düzen yolu 80 karakterden kısa olmalıdır, ancak bazı kuruluşlar 80 karakterlik sınırlamaya geçici bir çözüm için [simgesel bağlantıları](/windows/win32/fileio/symbolic-links) başarıyla kullandı.
- **Güncelleştirmeleri planlama:** İlk istemci yüklemesi _yapmadan önce_ istemci makinelerinizin ürün güncelleştirmelerini nasıl alması gerektiğine karar vermeniz önerilir. Bunun nedeni, istemcilerinizin güncelleştirme konum yapılandırmasının doğru şekilde başlatılmış olması sağlamaktır. Seçenekleriniz, istemcilerin ağ düzeni konumundan veya internet 'teki Microsoft tarafından barındırılan sunuculardan güncelleştirme almasını içerir. Neyse ki, ilk yüklemesi _gerçekleştirildikten sonra_ istemci kaynak konumunu güncelleştirmeler için yapılandırmak da mümkündür. 

::: moniker-end

## <a name="download-the-visual-studio-bootstrapper-to-create-the-network-layout"></a>ağ düzeni oluşturmak için Visual Studio önyükleyici 'yi indirin

istediğiniz Visual Studio sürümü için önyükleyici indirin ve düzeni kaynak konumu olarak kullanmak istediğiniz dizine kopyalayın. Önyükleyici, diğer düzen işlemlerini oluşturmak, güncelleştirmek ve gerçekleştirmek için kullandığınız yürütülebilir dosyadır.

::: moniker range="vs-2017"

aşağıda listelenen bootstrap, her zaman Visual Studio 2017 ' nin en son güvenli sürümünü her ne zaman çalıştırdığınızda olsun yükler:

| Sürüm                                      | Önyükleyici            |
|----------------------------------------------|---------------------|
| Visual Studio 2017 Enterprise sürüm 15,9   | [vs_enterprise.exe](https://aka.ms/vs/15/release/vs_enterprise.exe) |
| Visual Studio 2017 Professional sürüm 15,9 | [vs_professional.exe](https://aka.ms/vs/15/release/vs_professional.exe) |
| Visual Studio 2017 derleme araçları sürüm 15,9  | [vs_buildtools.exe](https://aka.ms/vs/15/release/vs_buildtools.exe)   |

Desteklenen diğer bootstrapdenetleyicileri vs_feedbackclient.exe, vs_teamexplorer.exe, vs_testagent.exe, vs_testcontroller.exe ve vs_testprofessional.exe içerir.

::: moniker-end

::: moniker range="vs-2019"

aşağıda listelenen bootstrap, her zaman Visual Studio 2019 ' nin en son güvenli sürümünü, ne zaman çalıştırdıklarından bağımsız olarak yükler. alternatif olarak, Visual Studio 2019 ' nin belirli bir sürümüne düzen oluşturmak veya güncelleştirmek istiyorsanız, her bir bakım sürümü için sabit sürüm bootstrapbağlantıları olan [Visual Studio 2019 yayınlar](/visualstudio/releases/2019/history#installing-an-earlier-release) sayfasına gidin ve istediğiniz birini indirin. Düzeni kaynak konumu olarak kullanmak istediğiniz dizine kopyalayın.

| Sürüm                                       | Önyükleyici                                                            |
|-----------------------------------------------|-------------------------------------------------------------------------|
| Visual Studio 2019 Enterprise sürüm 16,11   | [vs_enterprise.exe](https://aka.ms/vs/16/release/vs_enterprise.exe)     |
| Visual Studio 2019 Professional sürüm 16,11 | [vs_professional.exe](https://aka.ms/vs/16/release/vs_professional.exe) |
| Visual Studio 2019 derleme araçları sürüm 16,11  | [vs_buildtools.exe](https://aka.ms/vs/16/release/vs_buildtools.exe)     |

Desteklenen diğer bootstrapdenetleyicileri [vs_teamexplorer.exe](https://aka.ms/vs/16/release/vs_TeamExplorer.exe), [vs_testagent.exe](https://aka.ms/vs/16/release/vs_TestAgent.exe)ve [vs_testcontroller.exe](https://aka.ms/vs/16/release/vs_TestController.exe)içerir.

::: moniker-end

::: moniker range=">=vs-2022"

aşağıda listelenen bootstrap, her zaman geçerli kanala Visual Studio 2022 ' in en son güvenli sürümünü, çalıştırdığınızda bağımsız olarak yükler. alternatif olarak, belirli bir sürüme veya Visual Studio 2022 ' nin belirli bir kanalına bir düzen oluşturmak veya güncelleştirmek istiyorsanız, her bir kanaldaki her bir bakım sürümü için tek yeşil ve sabit sürüm bootstrapbağlantıları olan [Visual Studio 2022 yayın geçmişi](/visualstudio/releases/2022/release-history#release-dates-and-build-numbers) sayfasına gidin ve istediğiniz birini indirin. Düzeni kaynak konumu olarak kullanmak istediğiniz dizine kopyalayın. 

| Sürüm                    | Önyükleyici                                                        |
|----------------------------|----------------------------------------------------------------------|
| Visual Studio Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/17/release/vs_enterprise.exe)     |
| Visual Studio Professional | [vs_professional.exe](https://aka.ms/vs/17/release/vs_professional.exe) |
| Visual Studio 2022 derleme araçları   | [vs_buildtools.exe](https://aka.ms/vs/17/release/vs_buildtools.exe)         |

::: moniker-end

::: moniker range="vs-2017"

>[!TIP]
>Daha önce bir önyükleyici dosyası indirdiyseniz ve hangi sürümün olduğunu doğrulamak istiyorsanız, bunun nasıl yapıldığını burada bulabilirsiniz. Windows, dosya gezgini 'ni açın, önyükleyici dosyasına sağ tıklayın, **özellikler**' i seçin, **ayrıntılar** sekmesini seçin ve ardından **ürün sürümü** numarasını görüntüleyin. bu sayıyı Visual Studio bir sürümüyle eşleştirmek için, bkz. [Visual Studio derleme numaraları ve sürüm tarihleri](visual-studio-build-numbers-and-release-dates.md).

::: moniker-end

::: moniker range="vs-2019"

>[!TIP]
>Daha önce bir önyükleyici dosyası indirdiyseniz ve hangi sürümün olduğunu doğrulamak istiyorsanız, bunun nasıl yapıldığını burada bulabilirsiniz. Windows, dosya gezgini 'ni açın, önyükleyici dosyasına sağ tıklayın, **özellikler**' i seçin, **ayrıntılar** sekmesini seçin ve ardından **ürün sürümü** numarasını görüntüleyin. bu numarayı bir Visual Studio sürümüyle eşleştirmek için, [Visual Studio 2019 yayınları](/visualstudio/releases/2019/history) sayfasının altındaki tabloya bakın.

::: moniker-end

::: moniker range=">=vs-2022"

>[!TIP]
>Daha önce bir önyükleyici dosyası indirdiyseniz ve hangi sürümün yükleneceğini doğrulamak istiyorsanız, şöyle olur. Windows, dosya gezgini 'ni açın, önyükleyici dosyasına sağ tıklayın, **özellikler** ' i seçin ve **ayrıntılar** sekmesini seçin. **Ürün sürümü** alanı, önyükleyicinin yükleneceği [kanalı ve sürümü](/visualstudio/releases/2022/vs2022-release-rhythm) anlatmaktadır. Sürüm numarası her zaman "belirtilen sayının en son bakım sürümü" olarak okunmalı ve açıkça belirtilmediği sürece kanalın geçerli olduğu varsayılır. Bu nedenle, LTSC 17,0 ürün sürümüne sahip bir önyükleyici, 17,0 LTSC kanalında bulunan en son 17.0. x bakım sürümünü yükler. yalnızca Visual Studio 2022 ' i belirten ürün sürümüne sahip bir önyükleyici, geçerli kanala Visual Studio 2022 ' nin en son bakım sürümünü yükler.

::: moniker-end

## <a name="create-the-network-layout"></a>Ağ düzeni oluşturma

Bu adımı tamamlayabilmeniz için bir internet bağlantınızın olması gerekir.

yönetici ayrıcalıklarıyla bir komut istemi açın, önyükleyiciyi indirdiğiniz dizine gidin ve ağ düzeninizi oluşturmak ve sürdürmek için [Visual Studio sayfasını yüklemek üzere bootstrapper komut satırı parametrelerini kullanma](use-command-line-parameters-to-install-visual-studio.md) bölümünde tanımlanan önyükleyici parametrelerini kullanın. ilk düzen oluşturma örnekleri aşağıda gösterilmektedir ve [Visual Studio yükleme sayfası için komut satırı parametre örnekleri verilmiştir](command-line-parameter-examples.md) .  

tek bir dil yerel ayarı için bir başlangıç düzeni, Visual Studio Enterprise Visual Studio Community ve 45 gb için 35 gb disk alanı gerektirir. Ek [dil yerel ayarları](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales) her bırı için GB olmak üzere gereklidir. 
 
önerilen yaklaşım, tüm diller ve ağ sunucusundaki düzen dizinindeki tüm iş yükleri ile Visual Studio Enterprise ilk yerleşimini oluşturmaktır. Bu şekilde, istemcileriniz tüm ürün sunumuna erişim sahibi olur. Visual Studio tam eksiksiz bir düzeni oluşturmak için, ağ yerleşimini barındırmak için planladığınız makineden aşağıdakileri çalıştırın:

  ```vs_enterprise.exe --layout c:\VSLayout```
  
::: moniker range=">=vs-2022"

### <a name="ensure-your-layout-has-the-correct-channel"></a>Mizanpajınızın doğru kanala sahip olduğundan emin olun

Ağ düzeninin doğru [kanalı](/visualstudio/releases/2022/vs2022-release-rhythm)temel aldığından emin olmak önemlidir çünkü bu, kuruluş genelinde dağıtıldıklarında, [yönetici tarafından güncelleştirme](applying-administrator-updates.md)yapılan ölçütlerden biridir. Bu, hangi istemci örneklerinin güncelleştirileceğini belirlemek için kullanın. Örneğin, düzeniniz VisualStudio. 17. Release. LTSC. 17.0 kanalını temel alıyorsa ve istemcileriniz Microsoft tarafından barındırılan sunuculardan güncelleştirmeleri alacak şekilde yapılandırıldıysa, 17,0 LTSC kanalında kullanılabilir hale yaptığımız tüm güvenlik güncelleştirmeleri bu düzenden yüklenmiş veya güncelleştirilmiş olan istemciler tarafından kullanılabilir. 

Yukarıda listelenen Bootstrap, geçerli kanalın tabanlıdır. ltsc kanallarından birini temel alarak bir düzen oluşturmak için, [Visual Studio 2022 yayın geçmişi](/visualstudio/releases/2022/release-history#release-dates-and-build-numbers) sayfasından doğru kanalın önyükleyici edinmeniz, düzen klasörünüze kopyalamanız ve düzeni oluşturmak veya güncelleştirmek için onu kullanmanız yeterlidir. 

::: moniker-end

### <a name="configure-the-contents-of-a-network-layout"></a>Bir ağ düzeninin içeriğini yapılandırma

Ağ düzeniniz içeriğini özelleştirmek için kullanabileceğiniz çeşitli seçenekler vardır. Yalnızca belirli bir [dil yerel](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales)ayarı, [iş yükleri, bileşenler ve önerilen ya da isteğe bağlı bağımlılıklarını](workload-and-component-ids.md)içeren kısmi bir düzen oluşturabilirsiniz. Bu, istemci iş istasyonlarına yalnızca bir iş yükü alt kümesini dağıtacağınızı biliyorsanız yararlı olabilir. Düzeni özelleştirmeye yönelik tipik komut satırı parametreleri şunları içerir:

* `--add`[iş yükünü veya bileşen kimliklerini](workload-and-component-ids.md)belirtmek için. <br>Kullanılıyorsa `--add` , yalnızca ile belirtilen iş yükleri ve bileşenler `--add` indirilir.  `--add`Kullanılmıyorsa, tüm iş yükü ve bileşenler indirilir.
* `--includeRecommended` Belirtilen iş yükü kimlikleri için önerilen tüm bileşenleri eklemek için.
* `--includeOptional` Belirtilen iş yükü kimlikleri için tüm isteğe bağlı bileşenleri dahil etmek.
* `--lang`[dil yerel ayarlarını](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales)belirtmek için.

Özel kısmi düzenin nasıl oluşturulacağı hakkında birkaç örnek aşağıda verilmiştir.

* Yalnızca bir dile ait tüm iş yükleri ve bileşenlerle bir düzen oluşturmak için şunu çalıştırın:

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --lang en-US
    ```

* Birden çok dil için tüm iş yüklerini ve bileşenleri içeren bir düzen oluşturmak için şunu çalıştırın:

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --lang en-US de-DE ja-JP
    ```

* Bir iş yüküne ve bu iş yükü için önerilen tüm bileşenlere sahip bir düzen oluşturmak için, tüm diller için şunu çalıştırın:

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --includeRecommended
    ```

* Üç dil için iki iş yüküne ve isteğe bağlı bir bileşene sahip bir düzen oluşturmak için şunu çalıştırın:

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Component.Git --lang en-US de-DE ja-JP
    ```

* İki iş yükle ve tüm önerilen ve isteğe bağlı bileşenleriyle bir düzen oluşturmak için şunu çalıştırın:

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --includeOptional
    ```
    
::: moniker range=">=vs-2019"

### <a name="ensure-your-layout-is-using-the-latest-installer"></a>Mizanpajlarınızın en son yükleyiciyi kullandığından emin olun

en son Visual Studio yükleyicisini her zaman düzeninizde kullanmanızı ve istemcilerinize dağıtmanızı öneririz. Bu şekilde, ürünün sonraki sürümlerinde kullanıma sunduğumuz yeni özellik ve işlevlere erişebilirsiniz. örneğin, Visual Studio 2022 yükleyicisini Visual Studio 2019 düzenlerinizde dağıtırsanız, söz konusu düzeni temel alan Visual Studio 2019 istemcileriniz, güncelleştirmelerin kaynak konumunu değiştirme olanağına sahip olur. Bu işlevin yararlı olacağı senaryo, tek bir düzenden yüklemek istiyorsanız ancak güncelleştirmelerin başka bir düzenden gelmesini sağlar. En son yükleyiciyi kullanarak _kapatma_ dahil olmak üzere diğer ayrıntılar [aşağıda açıklanmıştır](#configure-the-layout-to-always-include-and-provide-the-latest-installer)

 > [!IMPORTANT]
 > en son yükleyiciyi kullanma özelliği, yalnızca Visual Studio 2022 ilk kez sevkedildikten sonra oluşturulan Visual Studio 2019 bootstraptarafından kullanılabilir. Bu nedenle, aşağıdaki örnekteki vs_enterprise.exe 10 Kasım 2021 ' _den sonra_ gelen bir sürüm olmalıdır. 

* Mevcut en son ve en büyük yükleyiciyi kullanan tüm ürünün bir yerleşimini oluşturmak için, şunu çalıştırın
    ```shell
    vs_enterprise.exe --layout C:\VSLayout --useLatestInstaller
    ```

::: moniker-end

### <a name="copy-the-layout-to-a-network-share"></a>Düzeni bir ağ paylaşımında kopyalama

İstemci makinelerden çalıştırılabilmesi için düzeni bir ağ paylaşımında barındırmanıza gerek duyarsınız. Düzeni yerel bir makinede oluşturduysanız, bunu bir ağ konumuna kopyalamanız gerekir. Aşağıdaki örnek kullanılmıştır [`xcopy`](/windows-server/administration/windows-commands/xcopy/) . Ayrıca, istediğiniz öğesini de kullanabilirsiniz [`robocopy`](/windows-server/administration/windows-commands/robocopy/) . Örnek:

```shell
xcopy /e c:\VSLayout \\server\share\layoutdirectory
```

> [!IMPORTANT]
> Bir hatayı engellemek için, ağ paylaşımındaki tam düzen yolunun 80 karakterden kısa olduğundan emin olun. Ya da, bazı kuruluşlar 80 karakter sınırlaması etrafında çalışmak için [sembolik bağlantıları](/windows/win32/fileio/symbolic-links) başarıyla kullandı.

## <a name="update-or-modify-your-layout"></a>Düzeninizi güncelleştirme veya değiştirme

Visual Studio bir ağ düzeninin en son ürün güncelleştirmeleriyle güncelleştirilmesi olasıdır. böylece, hem bir yükleme noktası hem de istemci iş istasyonlarının en son Visual Studio sürümünü alması için bir güncelleştirme kaynağı kullanılabilir. Özellikle, kullanıcılarınızın düzenden güncelleştirme almasını istiyorsanız, düzeninizi düzenli olarak güncellemek için en iyi uygulamadır. Bu bölümde en yaygın veya yararlı düzen bakım işlemleri açıklanmaktadır.

Bir dosya paylaşımında bir düzen barındırdıysanız, düzenin özel bir kopyasını (örneğin, c:\VSLayout) güncellemek isteyebilirsiniz ve sonra tüm güncelleştirilmiş içerik indirildikten sonra dosyayı dosya paylaşımınıza kopyalayın (örneğin, \\ \Server\products\vs). Bunu yapmazsanız, düzeni güncelleştirirken kurulum 'U çalıştırmak için gereken tüm kullanıcıların, henüz tamamen güncelleştirilmediği için düzenden içerik uyuşmazlığı olabileceği daha büyük bir şansınız vardır.

### <a name="update-the-layout-to-the-most-current-version-of-the-product"></a>Düzeni ürünün en güncel sürümüne güncelleştirin

Microsoft, işlevselliği veya güvenlik sorunlarını gidermek için ürünün güncelleştirilmiş sürümlerini sıklıkla yayınlar. Yeni istemci yüklemesi her zaman en son bir iyal alacak şekilde, düzeninizi ürünün en son sürümüne göre güncel tutmanız önerilir. İstemcileriniz, düzenden güncelleştirmeleri alacak şekilde yapılandırıldıysa, mizanpajınızın güncelleştirilmesini sağlamak da çok önemlidir. 

Başlangıç yerleşimini oluşturduğunuzda, mizanpaja dahil edilecek iş yükleri ve dillerin, düzenin yapılandırma dosyasına kaydedildiği gibi, belirtilen seçenekler. Daha sonra, bu düzeni ürünün daha yeni bir sürümüne güncellemek istediğinizde, ilk düzen oluşturma sırasında kullandığınız seçenekleri yeniden belirtmeniz gerekmez. Düzen güncelleştirme komutları, kaydedilen düzen ayarlarını otomatik olarak kullanır. 

[Yukarıdaki tabloda tek yeşil bootstrap'tan birini](#download-the-visual-studio-bootstrapper-to-create-the-network-layout)kullanarak bu kısmi düzeni zaten oluşturduğunuzu varsayalım.

```shell
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
```

Bu düzenin Microsoft tarafından sunulan ve Microsoft sunucularında barındırılan en son sürümüne güncelleştirilmesi kolaydır. Yalnızca aynı yaprak yeşil önyükleyici kullanmanız gerekir ve `--layout` en son paketleri düzeninize indirmek için komutu yeniden çalıştırın.

```shell
vs_enterprise.exe --layout c:\VSLayout
```

Ayrıca, düzeninizi daha yeni bir sürüme katılımsız bir şekilde güncelleştirebilirsiniz. Düzen işlemi, kurulum işlemini yeni bir konsol penceresinde çalıştırır. Bu pencere açık kalır, böylece kullanıcılar nihai sonucu ve oluşmuş olabilecek hataların özetini görebilirler. Bir düzen işlemini katılımsız bir şekilde gerçekleştiriyorsanız (örneğin, düzeninizi en son sürüme güncelleştirmek için düzenli olarak çalıştırılan bir betiğe sahipseniz), ardından `--passive` parametresini kullanın ve işlem pencereyi otomatik olarak kapatır.

```shell
vs_enterprise.exe --layout c:\VSLayout --passive
```

### <a name="update-the-layout-to-a-specific-version-of-the-product"></a>Düzeni ürünün belirli bir sürümüne güncelleştirin

Bazen, düzeninizi _ürünün belirli bir sürümüne_ güncelleştirmek isteyebilirsiniz.  Örneğin, düzeninizi kuruluşunuzda standartlaştırmış olduğunuz hizmet temelinin en son güvenli sürümüyle düzeninizi eşleştirmek isteyebilirsiniz. Bu işlemi şöyle yapabilirsiniz:

::: moniker range="vs-2019"

[Visual Studio 2019 yayınları](/visualstudio/releases/2019/history#installing-an-earlier-release) sayfasına gidebilir ve belirli bir sabit sürüm önyükleyiciyi indirebilir, mizanpajına kopyalayabilir ve bu düzeni kullanarak taslağı önyükleyici içinde belirtilen tam sürüme güncelleştirebilirsiniz. Yukarıdaki şekilde tam olarak aynı sözdizimini kullanırsınız.

::: moniker-end

::: moniker range="vs-2022"

[Visual Studio 2022 yayın geçmişi](/visualstudio/releases/2022/release-history#release-dates-and-build-numbers) sayfasına gidebilir ve belirli bir sabit sürüm önyükleyiciyi indirebilir, mizanpajına kopyalayabilir ve bu düzeni kullanarak taslağı önyükleyici içinde belirtilen tam sürüme güncelleştirebilirsiniz. Yukarıdaki şekilde tam olarak aynı sözdizimini kullanırsınız.

::: moniker-end

Düzeninizi belirli bir sürüme güncelleştirmek için **[yönetici güncelleştirmesi](applying-administrator-updates.md)** kullanabilirsiniz. **Yönetici güncelleştirmesini** almak Için [Microsoft Update kataloğuna](https://catalog.update.microsoft.com)gidin, düzeninizi güncelleştirmek istediğiniz güncelleştirmeyi arayın.  _update.exe_ düzeni barındıran bilgisayara indirin, bu bilgisayarda bir komut istemi açın ve şu şekilde bir komut çalıştırın:

```shell
visualstudioupdate-17.0.0to17.0.1.exe layout --layoutPath c:\VSLayout
```
Yönetici güncelleştirmelerinin orijinal bir düzen yüklemesi başlatmadığını unutmayın; yalnızca var olan bir düzeni veya istemci örneğini güncelleştirir. 

::: moniker range=">=vs-2022"

### <a name="modify-the-channel-of-the-network-layout"></a>Ağ düzeninin kanalını değiştirme

Bazen, kanallar destek dışında geçiş yaparken, istemcilerinizin güvenlik güncelleştirmeleriyle ilgili bildirimleri almaya devam edebilmesi için, ağ düzeninin desteklenen bir kanala dayanmaya devam ettiğinden emin olmanız gerekir. Düzeniniz VisualStudio. 17. Release. LTSC. 17.0 kanalını temel alıyorsa, 17,0 LTSC kanalının destek dışına çıkmasıyla ilgili daha fazla güvenlik güncelleştirmesi sunmuyoruz ve sizin düzenleriniz ve istemcileriniz güvenli olmaz.

düzenin dayandığı kanalı değiştirmek için, istenen kanalın önyükleyici [Visual Studio 2022 yayın geçmişi](/visualstudio/releases/2022/release-history#release-dates-and-build-numbers) sayfasından edinmeniz, düzen klasörünüze kopyalamanız ve normal bir güncelleştirme gerçekleştirmeniz yeterlidir. Daha sonra istemcileriniz da güvenli bir şekilde kalabilmeleri için bir güncelleştirme ile uygun şekilde bildirilmesi gerekir.

::: moniker-end

### <a name="modify-the-contents-of-the-layout"></a>Düzenin içeriğini değiştirme

Bu düzeni değiştirmek ve ek iş yüklerini veya bileşenleri veya dilleri eklemek veya kaldırmak mümkündür. Aşağıdaki örnekte, Azure iş yükünü ve yerelleştirilmiş dili yukarıda oluşturduğumuz düzene ekleyeceğiz. Değişiklik yapıldıktan sonra, hem yönetilen masaüstü ve Azure iş yükleri hem de Ingilizce ve Almanca kaynaklar bu düzene dahildir. Ayrıca, düzen kullanılabilir en son sürüme güncelleştirilir.

```shell
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
```

Varolan bir kısmi düzeni tam düzen olacak şekilde değiştirmek istiyorsanız, aşağıdaki örnekte gösterildiği gibi--ALL seçeneğini kullanın.

```shell
vs_enterprise.exe --layout c:\VSLayout --all
```

Sürümü güncelleştirmeden ek iş yükü ve _yerelleştirilmiş dil ekleme_ hakkında daha fazla bilgiyi burada bulabilirsiniz. (bu komut ASP.NET ve Web geliştirme iş yükünü ekler.) artık yönetilen masaüstü, Azure ve ASP.NET & Web geliştirme iş yükleri bu düzene dahildir. Ingilizce, Almanca ve Fransızca için dil kaynakları, tüm bu iş yükleri için de eklenmiştir. Ancak, bu komut çalıştırıldığında düzen en son kullanılabilir sürüme güncellenmez. Mevcut sürümde kalır.

```shell
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.NetWeb --lang fr-FR --keepLayoutVersion
```

 > [!IMPORTANT]
 > Bir güncelleştirme işlemi, düzen veya istemciye ek isteğe bağlı bileşenler indirmez veya yüklemez. İsteğe bağlı bileşenler eklemeniz veya değiştirmeniz gerekiyorsa, önce önceki isteğe bağlı bileşenleri `layout.json` yapılandırma dosyasından kaldırın ve ' in "Ekle" bölümünde ihtiyacınız olan yeni bileşenleri ekleyin `layout.json` . Sonra, `--layout` düzeni güncellemek için komutunu çalıştırdığınızda, yeni eklenen bileşenleri mizanpaja indirir.
 >
 > Bu yeni bileşenlerin istemci makinesine yüklenmesini sağlamak için bu üç adımı yaptığınızdan emin olun. İlk olarak, yukarıda açıklandığı gibi düzenin yeni bileşenleri içerdiğini doğrulayın. Sonra, istemcinizi mizanpajda en son bitleri güncelleştirin. Son olarak, istemci üzerinde, yeni bileşenleri (düzene eklenen) istemci makinesine yükleyecek bir değiştirme işlemi çalıştırın.

::: moniker range=">=vs-2019"

### <a name="configure-the-layout-to-always-include-and-provide-the-latest-installer"></a>Yerleşimi her zaman içerecek şekilde yapılandırın ve en son yükleyiciyi sağlayın

Bir yükleyicinin daha yeni bir Visual Studio sürümünün parçası olarak kabul edilse bile, düzeninizi _her zaman_ , istemcilerinize en son yükleyiciyi içerecek şekilde yapılandırabilir ve sağlayabilirsiniz. Bu nedenle, istemciniz bu düzenden güncelleştirdiğinizde, istemci bu düzen tarafından sunulan ve sağlanan en son yükleyiciyi elde eder. Bunun avantajı, en son yükleyicinin istemcide olması durumunda, istemci yüklemelerinizin hata düzeltmelerinden ve yükleyiciden eklenmeye devam ettiğimiz yeni işlevlerden faydalanması mümkün olacaktır. 

::: moniker-end

::: moniker range="vs-2019"

>[!TIP]
>[istemcinizin Visual Studio 2019 yüklemesinin güncelleştirmeleri aradığı konumu değiştirmek](update-visual-studio.md#configure-source-location-of-updates)istiyorsanız, istemci makinenizde en son Visual Studio 2022 *yükleyicisini almalısınız.* bunu yapmanın bir yolu, aşağıda açıklanan parametreleri kullanarak Visual Studio 2019 düzenlerinizde Visual Studio 2022 yükleyicisini dahil etmenin bir yoludur. en son yükleyiciyi kullanma özelliği, yalnızca Visual Studio 2022 ilk kez sevkedildikten sonra oluşturulan Visual Studio 2019 bootstraptarafından kullanılabilir. Bu nedenle vs_enterprise.exe örnekteki örnek, 10 Kasım  2021'den sonra gönderilen bir sürüme sahip olması gerekir. 

::: moniker-end

::: moniker range=">=vs-2019"

Düzeninizi dahil etmek ve en son yükleyiciyi sağlamak için iki yol vardır:

- Düzeni oluştururken veya `--useLatestInstaller` güncelleştirirken parametresini önyükleyiciye geçebilirsiniz. Bu, düzenin kök dizininde bulunabilecek layout.json dosyasında bir ayarın ayarlanmış olmasına neden olur. Burada, düzeni güncelleştirme ve kullanılabilir en son ve en büyük yükleyiciyi kullanmak üzere yapılandırmaya bir örnek ve ardından.  


   ```shell
   vs_enterprise.exe --layout C:\VSLayout --useLatestInstaller
   ```

- Bu ayarı eklemek için layout.json dosyasını doğrudan düzenleyebilirsiniz.

   ```Example layout.json contents
   {
     "installChannelUri": ".\\ChannelManifest.json",
     "channelUri": "\\\\server\\share\\layoutdirectory\\ChannelManifest.json",
     "installCatalogUri": ".\\Catalog.json",
     "channelId": "VisualStudio.16.Release",
     "productId": "Microsoft.VisualStudio.Product.Enterprise",
   
     "useLatestInstaller": true
     
   }
   ```

layout.json dosyasındaki bu ayarı program aracılığıyla kaldırmanın bir yolu yoktur.  Bu nedenle, düzeninizin Microsoft tarafından kullanılabilir olan en son yükleyiciyi kullanmayı durdurması ve bunun yerine yükleyicinin önyükleyiciye karşılık gelen sürümünü (büyük olasılıkla en son yükleyiciden daha eski olan) kullanmak için layout.json dosyasını düzenlemeniz ve ayarı kaldırmanız `"UseLatestInstaller": true` gerekir. 

Bu ayarı düzenin response.json dosyasında da bulabilirsiniz ancak burada `"UseLatestInstaller": true` yoksayılır. [response.json  dosyası, istemci](automated-installation-with-response-file.md)bir düzenden yüklenirken veya güncelleştirmeyi kullandığında istemcide varsayılan yapılandırma seçeneklerini ayarlamak için kullanılır. Bu ayar, düzenin içeriğinin en son yükleyiciyi içerdiğinden emin olmak için kullanılır, böylece istemci makineleri daha sonra düzenden en `"useLatestInstaller": true` son yükleyiciyi  edinebilirsiniz.

::: moniker-end

### <a name="verify-a-layout"></a>Düzeni doğrulama

Paket `--verify` dosyalarının eksik veya geçersiz olup olduğunu kontrol etmek üzere ağ düzeninde doğrulama gerçekleştirmek için kullanın. Doğrulamanın sonunda eksik ve geçersiz dosyaların listesini yazdırır.

Doğrulama yalnızca belirli bir ikincil sürümün en son sürümü için Visual Studio. Yeni bir sürüm yayımlanmasıyla birlikte doğrulama, önceki sürümler içeren düzenler için çalışmaz.

```shell
vs_enterprise.exe --layout <layoutDir> --verify
```

> [!NOTE]
> seçeneği tarafından gereken bazı önemli meta `--verify` veri dosyaları düzen klasöründe yer almalı. Bu meta veri dosyaları eksikse "--verify" çalıştıramaz ve Kurulum size bir hata verir. Bu hatayla karşılaştıysanız, düzeni yeniden güncelleştirmeyi deneyin veya farklı bir klasörde yeni bir ağ düzeni yeniden oluşturun.

Sabit bağlantı önyükleyicileri kullanmadıkça, Microsoft'un güncelleştirmeleri düzenli aralıklarla Visual Studio, dolayısıyla daha yeni bir düzen ilk düzen ile aynı sürümü [içereyemsin.](#download-the-visual-studio-bootstrapper-to create-the-network-layout)

### <a name="fix-a-layout"></a>Düzeni düzeltme

ile `--fix` aynı doğrulamayı gerçekleştirmek için `--verify` kullanın ve ayrıca tanımlanan sorunları düzeltmeyi deneyin. İşlem için bir İnternet bağlantısı olması gerekir, bu nedenle çağırmadan `--fix` önce makinenizin İnternet'e bağlı olduğundan emin `--fix` olun.

```shell
vs_enterprise.exe --layout <layoutDir> --fix
```

### <a name="remove-older-versions-from-a-layout"></a>Düzenden eski sürümleri kaldırma

Bir ağ önbelleğinde düzen güncelleştirmeleri gerçekleştirdikten sonra, düzen klasöründe artık en son uygulama yüklemesi için gerekmeyecek bazı eski Visual Studio olabilir. Eski paketleri ağ `--clean` düzeni klasöründen kaldırmak için seçeneğini kullanabilirsiniz.

Bunu yapmak için, bu eski paketleri içeren katalog bildirimlerini içeren dosya yollara ihtiyacınız vardır. Katalog bildirimlerini ağ düzeni önbelleğinde bir "Arşiv" klasöründe bulabilirsiniz. Bir düzeni güncelleştirenler buraya kaydedilir. "Arşiv" klasöründe, her biri eski bir katalog bildirimi içeren bir veya daha fazla "GUID" adlı klasör vardır. "GUID" klasörlerinin sayısı, düzenlerinize yapılan güncelleştirmelerin sayısıyla aynı olması gerekir.

Her "GUID" klasörüne birkaç dosya kaydedilir. En çok ilgini alan iki dosya bir "catalog.json" dosyası ve bir "version.txt" dosyasıdır. "catalog.json" dosyası, seçeneğine geçmemiz gereken eski katalog `--clean` bildirimidir. Diğer version.txt dosyası bu eski katalog bildiriminin sürümünü içerir. Sürüm numarasına bağlı olarak, bu katalog bildiriminden eski paketleri kaldırmak isteyip istemeyebilirsiniz. Aynı şekilde diğer "GUID" klasörlerini de geçebilirsiniz. Temizlemek istediğiniz kataloglarla ilgili karar verdikten sonra, bu kataloglara dosya yollarını `--clean` serek komutunu çalıştırın.

Burada --clean seçeneğinin nasıl kullanıla bir örneği ve bir örnek vetir:

```shell
c:\VSLayout\vs_enterprise.exe --layout c:\VSLayout --clean c:\VSLayout\Archive\1cd70189-fc55-4583-8ad8-a2711e928325\Catalog.json --clean c:\VSLayout\Archive\d420889f-6aad-4ba4-99e4-ed7833795a10\Catalog.json
```

Bu komutu yürütürken Kurulum, kaldıracak dosyaların listesini bulmak için ağ düzeni klasörlerinizi analiz eder. Ardından, silinecek dosyaları gözden geçirme ve silme işlemlerini onaylama fırsatınız olur.

## <a name="install-visual-studio-onto-a-client-machine-from-a-network-installation"></a>Ağ Visual Studio istemci makinesine yükleme

Yöneticiler bir yükleme Visual Studio parçası olarak istemci iş istasyonlarına sanal ağ dağıtarak iş istasyonlarına dağıtın. Ya da yönetici haklarına sahip kullanıcılar doğrudan paylaşımdan kurulumu çalıştırarak makinelerine Visual Studio yükleyebilir.

* Kullanıcılar aşağıdaki komutu çalıştırarak ürünü bir ağ düzeninden el ile yükleyebilir:

    ```shell
    \\server\products\VS\vs_enterprise.exe
    ```

* Yöneticiler aşağıdaki komutu çalıştırarak katılımsız modda yükleyebilir:

    ```shell
    \\server\products\VS\vs_enterprise.exe --quiet --wait --norestart
    ```

> [!NOTE] 
> Sabırlı olun. Hem yükleyicinin `--wait` hem de ürünün tamam olduğundan emin olun. Bir düzenin istemcisini yüklerken veya güncelleştirdiğinde, her zaman ilk olarak yükleyici yüklenir veya güncelleştirilir ve ardından Visual Studio ürünün kendisi yüklenir veya güncelleştirilir. **Başarılı** bir güncelleştirme olarak kabul etmek için bu işlemlerin her ikisinin de bitmelidir.   
>
> Katılımsız otomatik toplu iş dosyasının bir parçası olarak yükleme veya güncelleştirme yürütürken, seçenek, bir çıkış kodu döndürene kadar yükleme tamamlandıktan sonra sürecin beklemesini sağlamak `--wait` `vs_enterprise.exe` için yararlıdır. Bu, kuruluş yöneticisinin tamamlanmış bir yüklemede başarılı bir yüklemeye ürün anahtarı uygulama gibi başka [eylemler gerçekleştirmek istediği durumlarda kullanışlıdır.](automatically-apply-product-keys-when-deploying-visual-studio.md) --wait seçeneğinin kullanımı, sonraki işlemlerin erkenden sonuç almasını önler. kullanmayacaksanız, yüklemenin her iki parçası da tamamlandıktan önce işlemden çıkabilir ve bu nedenle yükleme işleminin durumunu temsil etmeyen yanlış bir çıkış `--wait` `vs_enterprise.exe` kodu geri döner.

### <a name="install-on-a-client-that-doesnt-have-internet-access"></a>İnternet erişimi olmayan bir istemciye yükleme

Bir düzenden yüklemesi, yüklü olan içeriğin varsayılan olarak düzenden elde edilmiş olmasıdır. Ancak, düzende olmayan bir bileşeni seçer ve istemci güncelleştirmeler için [Microsoft](automated-installation-with-response-file.md)tarafından barındırılan sunuculara bakacak şekilde yapılandırılmışsa, yükleyici de internetten Visual Studio paketleri elde etmek için girişimde lar. Bu ayarın, Visual Studio web'den düzende eksik olan içeriği indirmeye çalışmasını önlemek için seçeneğini `--noWeb` kullanın. `--noWeb`kullanılırsa ve düzende yüklenmek üzere seçilen herhangi bir içerik eksikse, kurulum başarısız olur.

> [!IMPORTANT]
> seçeneği, istemcinin Microsoft tarafından Visual Studio sunucuları güncelleştirmelere göz atacak şekilde yapılandırılmış olup olmadığını denetlemesini İnternet'e bağlı bir istemci makinesine yükleme yükleyicisini `--noWeb` durdurmaz.  Bunun `--noWeb` yerine, yalnızca istemcinin ürün paketlerini indirmesini engellemektir. Daha fazla bilgi için ağ [düzeni sayfasından Visual Studio istemcisini güncelleştirme sayfasına](update-a-network-installation-of-visual-studio.md) bakın.

::: moniker range=">=vs-2019"

"Aşağıdaki parametrelerle eşleşen bir ürün bulunamadı" hata iletisini alırsanız anahtarını kullanırkenn emin `--noweb` olun.

::: moniker-end

### <a name="configure-initial-client-installation-defaults-for-this-layout"></a>Bu düzen için ilk istemci yükleme varsayılanlarını yapılandırma

Ürün istemci makinesine ilk kez yüklenirken kullanılan varsayılan değerleri ayarlamak için düzen klasöründeki bazı dosyaları değiştirebilirsiniz. Yaygın yapılandırma seçenekleri şunlardır:

- İlk yükleme **sırasında varsayılan olarak hangi iş yüklerinin, bileşenlerin veya dillerin seçileceklerini** yapılandırma olanağı. 
- İstemcinin **güncelleştirmeleri nereden alası gerektiğini belirtme olanağı.**  Seçenekler, yönetici denetimli ağ düzeni konumu veya İnternet üzerinde Microsoft tarafından barındırılan sunuculardan (varsayılan seçenektir) gelen seçeneklerdir.

Düzen için varsayılan istemci ayarlarını özelleştirme ve yapılandırma hakkında daha fazla bilgi için bkz. [Yanıt dosyası Visual Studio yüklemesini otomatikleştirme.](automated-installation-with-response-file.md)  

### <a name="configure-enterprise-deployment-behavior"></a>Kurumsal dağıtım davranışını yapılandırma

::: moniker range=">=vs-2019"

Ayrıca, şu gibi diğer kurumsal dağıtım davranışını da kontrol altına aabilirsiniz:

- Yönetici güncelleştirmelerinin etkinleştirilmesi ve nasıl uygulanması gerektiği.
- Hangi güncelleştirme kanallarının kullanılabilir olduğu ve Ağ düzenlerini güncelleştir iletişim kutusundaki istemci makinelerine Ayarlar görünür.
- Paylaşılan paketlerin yüklü olduğu yer.
- Paketlerin nerede ve önbelleğe alınıp alın olmadığı.
- Bildirimlerin görünme veya görünmema durumu.

Ek ayrıntılar [için Bkz. Kurumsal dağıtımların kurumsal dağıtımları Visual Studio](set-defaults-for-enterprise-deployments.md) ayarları.

::: moniker-end

::: moniker range="vs-2017"

Ayrıca, paylaşılan paketlerin yük olduğu yer gibi diğer kurumsal dağıtım davranışlarını da kontrol etmek için kullanabilirsiniz. Ek ayrıntılar [için Bkz. Kurumsal dağıtımların kurumsal dağıtımları Visual Studio](set-defaults-for-enterprise-deployments.md) ayarları.

::: moniker-end

### <a name="error-codes"></a>Hata kodları

parametresini `--wait` kullandıysanız, işlem sonucuna bağlı olarak ortam `%ERRORLEVEL%` değişkeni aşağıdaki değerlerden biri olarak ayarlanır:

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

### <a name="get-support-for-your-network-layout"></a>Ağ düzeniniz için destek al

Ağ düzeniniz ile ilgili bir sorun yaşamanız, bunun hakkında bilgi almak istiyor. Bize söylemenin en iyi yolu, hem Visual Studio Yükleyicisi hem de Visual Studio IDE'de görünen Sorun Bildir aracını kullanmaktır. [](../ide/how-to-report-a-problem-with-visual-studio.md) BIR IT Yöneticisiyseniz ve yüklü bir Visual Studio yoksa, burada IT Yöneticisi geri [**bildirimi gönderebilirsiniz.**](https://aka.ms/vs/admin/guide) Bu aracı kullanırsanız, vs [Collect](https://aka.ms/vscollect) aracından günlükleri gönderebilirsiniz ve bu da sorunu tanılamamıza ve düzeltmemıza yardımcı olabilir.

Ayrıca yüklemeyle ilgili [**sorunlar için bir**](https://visualstudio.microsoft.com/vs/support/#talktous) yükleme sohbeti (yalnızca İngilizce) destek seçeneği sunuyoruz.

Başka destek seçenekleri de mevcuttur. Geliştirici [Visual Studio'mıza Community.](https://developercommunity.visualstudio.com/home)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
- [Visual Studio’nun ağ tabanlı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md)
- [Ağ ile ilgili sorunları gidermek için ağ Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
- [Ağ tabanlı dağıtımlarda güncelleştirmeleri Visual Studio denetleme](controlling-updates-to-visual-studio-deployments.md)
- [Visual Studio yaşam döngüsü ve bakım](/visualstudio/releases/2019/servicing/)
- [Bakım temeli sırasında Visual Studio’yu güncelleştirme](update-servicing-baseline.md)
- [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
- [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md)
- [Çevrimdışı yükleme için Visual Studio sertifikaları yükleme](install-certificates-for-visual-studio-offline.md)
