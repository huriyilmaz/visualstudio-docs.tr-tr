---
title: Ağ tabanlı bir yüklemeyi güncelleştirme
description: Ağ düzeninden yüklenmiş Visual Studio istemcisini güncelleştirmeyi öğrenin
ms.date: 11/23/2021
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 1AF69C0E-0AC9-451B-845D-AE4EDBCEA65C
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 858e593ab6c2e5bc0beed0749c5864d8a75b3e97
ms.sourcegitcommit: 2281b4f1f8737f263c0d7e55e00b5ec81517327d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2021
ms.locfileid: "133108828"
---
# <a name="update-a-visual-studio-client-that-was-installed-from-a-network-layout"></a>Bir Visual Studio düzeninden yüklenmiş bir istemciyi güncelleştirme

En son güvenlik ve işlev düzeltmelerini Visual Studio tüm istemcilerini düzenli aralıklarla güncelleştirin ve güncelleştirin. 

Visual Studio istemci başlangıçta bir ağ düzeni aracılığıyla yüklendiyse, büyük olasılıkla istemci makinesi "yönetilen bir ortamın" parçasıdır, yani merkezi bir yönetim ekibi tarafından yönetilir ve kuruluş ilkelerine uyması gerekir. Yönetilen bir ortamdaki istemci makinelerini güncelleştirmek için, aşağıdaki yanıtlarının güncelleştirme sürecine nasıl yaklaşması gerektiği konusunda bilgi edinecek soruları göz önünde bulundurabilirsiniz. 

-  Güncelleştirmeler nereden geliyor: ağ düzeni veya Microsoft tarafından barındırılan sunucular? Güncelleştirme bir ağ düzeninden geliyorsa ağ düzeni hazır mı?
-  Güncelleştirme kullanıcı tarafından mı başlatacak yoksa yönetici tarafından başlatılan bir olay mı? Güncelleştirmeyi gerçekleştiren kişinin yönetici izinlerine sahip olması gerektiğini unutmayın.

## <a name="prepare-the-update-source"></a>Güncelleştirme kaynağını hazırlama

İstemcinizi Microsoft tarafından barındırılan sunuculardan güncelleştireceksanız, istemci microsoft'tan edinilen en son sürümü bu kanala indirir ve [indirir.](/visualstudio/releases/2022/vs2022-release-rhythm) 

İstemcinizi bir ağ düzeninden güncelleştiriyorsanız, ilk adım güncelleştirilmiş ürünle ağ düzenini hazırlamaktır. Hem yeni [yüklemelerin hem de güncelleştirmelerin güncelleştirilmiş sürümü](/visualstudio/install/create-a-network-installation-of-visual-studio#update-or-modify-your-layout) aldıracak şekilde mevcut düzeninizi en son ürün güncelleştirmeleriyle güncelleştirebilirsiniz. Veya istemci [makinelerini güncelleştirmek için kullanabileceğiniz](/visualstudio/install/create-a-network-installation-of-visual-studio) farklı bir dizinde yepyeni bir düzen oluşturabilirsiniz.

## <a name="enable-manual-user-initiated-client-side-updates"></a>El ile kullanıcı tarafından başlatılan istemci tarafı güncelleştirmelerini etkinleştirme 
İstemci makinesi üzerinde yeterli izinlere sahip bir kullanıcı, kendi [kendini güncelleştiren Visual Studio başlatabilirsiniz.](/visualstudio/install/update-visual-studio) Yeni Visual Studio, güncelleştirmelerin doğru kaynak konumunu bakarak bir güncelleştirmenin kullanılabilir olduğunu tanıyacak şekilde düzgün yapılandırılması gerekir. Güncelleştirme gerçekleşirken herhangi bir dosya (Visual Studio açıksa) kullanılırsa, Visual Studio tamamlamak için dosyanın kapanması gerekir. Bazen bir güncelleştirmenin yeniden başlatılması gerekir.

### <a name="manually-configure-where-the-visual-studio-client-looks-for-updates"></a>İstemcinin güncelleştirmeleri Visual Studio el ile yapılandırma

İstemci Visual Studio başlangıçta yüklü olduğunda, güncelleştirmeleri denetlemesi gereken konumu kaydeder. Microsoft Visual Studio sunuculardan yüklenmişse, varsayılan olarak Microsoft tarafından barındırılan sunuculardan güncelleştirmeleri aramaz. Ağ Visual Studio önyükleyicisi tarafından yüklenmiş veya güncelleştirilmişse, düzeni tarafından belirtilen konumdaki [güncelleştirmeleri bakar.](/visualstudio/install/automated-installation-with-response-file)  

::: moniker range="vs-2017"

Bu Visual Studio 2017'de, istemci ürünü yüklediği zaman istemcinin güncelleştirme konumu yapılandırması kilitlenir ve değiştirilemez. Güncelleştirmeler için farklı bir kaynak konumu yapılandırmak üzere, doğru düzen yapılandırmasını kullanarak ürünü kaldırmanız ve yeniden yüklemeniz gerekir.

::: moniker-end

::: moniker range="vs-2019"

Varsayılan Visual Studio 2019 işlevselliğiyle, istemci ürünü yükledikten sonra istemcinin güncelleştirme konumu yapılandırması kilitlenir ve değiştirilemez. Güncelleştirmelerin kaynak _konumunu güvenilir bir_ şekilde değiştirmenin tek yolu, doğru yapılandırmayı kullanarak ürünü kaldırmak ve yeniden yüklemektir.
 
Ancak, Visual Studio en son Visual Studio 2022 Yükleyicisi kullanıyorsa, güncelleştirmeler için istemcinin kaynak konumu değiştirilebilir. Bu, bir düzenden yüklemek ancak güncelleştirmelerin başka bir düzenden geliyor olması için kullanışlıdır. Visual Studio 2022 Yükleyicisini bir istemci makinesine almak için iki yol vardır. En kolayı, Visual Studio 2022 ürününü yüklemek ve kullanmaktır. Alternatif olarak, Visual Studio [2022 yükleyicisini Visual Studio 2019 düzenleri aracılığıyla dağıtabilirsiniz.](/visualstudio/install/create-a-network-installation-of-visual-studio#configure-the-layout-to-always-use-the-latest-installer)

::: moniker-end

::: moniker range=">=vs-2019"

İstemcinin güncelleştirmeleri araması için güncelleştirme konumunu el ile görüntülemek ve yapılandırmak için Update [Ayarlar'yi](/visualstudio/install/update-visual-studio?view=vs-2022&preserve-view=true#configure-source-location-of-updates-1)getirin ve doğru yapılandırıldığından emin olun. Ardından güncelleştirmeyi istemciden başlatarak başlatarak.  

::: moniker-end

### <a name="update-notifications"></a>Güncelleştirme bildirimleri

İstemcinin güncelleştirmeleri aray bulunduğu konumda kullanılabilir bir güncelleştirme varsa, istemci bir [ileti veya bildirim bayrağı görüntüler.](/visualstudio/install/update-visual-studio?#use-the-message-box-in-the-ide-1)  

Güncelleştirme bildirimlerinin kullanıcılara ne zaman sun alınarak kontrol edilecekleri hakkında ayrıntılı bilgi için bkz. Ağ tabanlı [güncelleştirmeler ve dağıtımlar için Visual Studio denetleme.](/visualstudio/install/set-defaults-for-enterprise-deployments#controlling-notifications-in-the-visual-studio-ide)

### <a name="manually-initiate-the-update"></a>Güncelleştirmeyi el ile başlatma

Kullanıcılar bir [örneği el](/visualstudio/install/update-visual-studio) Visual Studio şu şekilde güncelleştirebilir: 
  * başlatarak Visual Studio Yükleyicisi. Bir güncelleştirme varsa Güncelleştir'e **tıklarlar.**
  * IDE'Visual Studio başlatma ve bildirim bayrağına veya iletisine yanıt verme ya da Yardım/Güncelleştirmeleri denetleme'ye tıklayın.  

## <a name="programatically-update-the-client-machines"></a>İstemci makinelerini programlı olarak güncelleştirme
Yöneticiler, komutları istemci tarafı yükleyiciye Visual Studio veya bir önyükleyiciyi başlatarak istemci yüklemelerini program aracılığıyla güncelleştirebilirsiniz.

### <a name="programatically-update-visual-studio-by-using-the-visual-studio-installer"></a>Visual Studio Yükleyicisi kullanarak Visual Studio programlı güncelleştirme Visual Studio Yükleyicisi

::: moniker range="vs-2017"

İstemcinin yükleyicisini program Visual Studio ve güncelleştirme komutunu başlatarak bir güncelleştirme başlatabilirsiniz. Örnek:

```shell
c:\program files (x86)\microsoft\visual studio\installer\>setup.exe update --installPath "C:\Program Files\Microsoft Visual Studio\2017\Enterprise" 
```

::: moniker-end

::: moniker range=">=vs-2019"

İstemcinin yükleyicisini program Visual Studio ve güncelleştirme komutunu başlatarak bir güncelleştirme başlatabilirsiniz. Bu komut, Visual Studio için kaynak konumda bulunan güncelleştirilmiş ürüne [göre güncelleştirilecek.](/visualstudio/install/update-visual-studio#configure-source-location-of-updates-1) İstemcide güncelleştirme kaynağı konumunu değiştirmek için --channelURI parametresini geçerek programlı olarak bunu yapabiliriz. Örnek:  

Kanalı bir ağ düzeni olarak değiştirebilir ve _istemcide_ aşağıdaki gibi bir güncelleştirme komutu yürütebilirsiniz:

```shell
c:\program files (x86)\microsoft\visual studio\installer\>setup.exe update --installPath "C:\Program Files\Microsoft Visual Studio\2019\Enterprise" --channelURI "\\\\server\\share\\newlayoutdir\\channelmanifest.json"
```
veya bunun gibi, güncelleştirmelerin kaynağını Microsoft tarafından barındırılan bir konuma ayarlar:

```shell
c:\program files (x86)\microsoft\visual studio\installer\>setup.exe update --installPath "C:\Program Files\Microsoft Visual Studio\2019\Enterprise" --channelURI "https://aka.ms/vs/16/release/channel"
```

::: moniker-end

### <a name="programatically-update-visual-studio-by-using-a-bootstrapper"></a>Önyükleyici kullanarak Visual Studio'ya programlı güncelleştirme.

::: moniker range=">=vs-2017"

İlk olarak Visual Studio konumdan bir önyükleyiciyi programlı olarak çağırarak bu önyükleyiciyi güncelleştirebilirsiniz. Microsoft tarafından barındırılan sunuculardan gelen tüm önyükleyiciler aynı konumdan kabul edilir. Önyükleyiciniz bir ağ düzeni paylaşımında ise, ağ düzeninin istenen ürün [güncelleştirmelerini](/visualstudio/install/create-a-network-installation-of-visual-studio#update-or-modify-your-layout) içermesi için güncelleştirilmiş olması gerekir.

```shell
\\server\share\originalinstallVSdirectory\vs_enterprise.exe update --installPath "C:\clientmachine\installpath" --quiet 
```

::: moniker-end

::: moniker range="vs-2019"

Ayrıca, istemciyi güncelleştirmek istediğiniz ürünün sürümünü içeren farklı bir kaynak konumdan programlı  bir önyükleyici çağırarak Visual Studio 2019 istemcinizi güncelleştirebilirsiniz. Bunu yapmak için istemcide Visual Studio 2022 yükleyicisini alasiniz. Bunu etkinleştirmenin en kolay yolu, [yeni 2019 Visual Studio en son yükleyiciyi kullanmaktır.](/visualstudio/install/create-a-network-installation-of-visual-studio#ensure-your-layout-is-using-the-latest-installer) Önyükleyiciyi yeni bir düzenden çalıştırırsanız, istemcinin güncelleştirme kanalı, düzeninde [belirtilen güncelleştirme konumu olarak ayarlanır.](/visualstudio/install/automated-installation-with-response-file) Örneğin, bu komutu istemci makinede çalıştırabilirsiniz:

::: moniker-end

::: moniker range=">=vs-2022"

Ayrıca, istemciyi güncelleştirmek istediğiniz ürünün sürümünü içeren farklı bir kaynak konumdan  programlı bir önyükleyici çağırarak Visual Studio istemcinize bir güncelleştirme başlatabilirsiniz. Önyükleyiciyi yeni bir düzenden çalıştırırsanız, istemcinin güncelleştirme kanalı, düzeninde [belirtilen güncelleştirme konumu olarak ayarlanır.](/visualstudio/install/automated-installation-with-response-file) Örneğin, bu komutu istemci makinede çalıştırabilirsiniz:

::: moniker-end

::: moniker range=">=vs-2019"

```shell
   \\server\share\desiredupdatelayoutdir\vs_enterprise.exe update --installPath "C:\clientmachine\installpath" --quiet 
```
Düzenin response.json dosyasındaki channelURI değeri ne olursa olsun, istemcinin gelecekteki güncelleştirmeleri için bakacakları konum olacaktır.

::: moniker-end

> [!NOTE]
> İstemci [vswhere.exe var](tools-for-managing-visual-studio-instances.md) olan bir istemci örneğinin yükleme yolunu belirlemek için Visual Studio komutunu kullanın.

### <a name="programatically-update-a-client-that-doesnt-have-internet-access"></a>İnternet erişimi olmayan bir istemciyi programlı olarak güncelleştirme

İstemci makinenizin İnternet erişimi yoksa, güncelleştirmeleri _bir ağ_ düzeninden edinmesi gerekir. Her güncelleştirildiğinde güncelleştirilen iki parça olduğunu Visual Studio unutmayın. Birincisi yükleyici, ikincisi ise Visual Studio ürünüdür. İstemci makinede bu Visual Studio _komutlarını_ _çalıştırarak_ ağ düzeninden bu bileşenlerin her ikisini de açık bir şekilde ağına bakmalarını belirtebilirsiniz. İlk komut yükleyiciyi düzenden gelecek şekilde, ikinci komut ise paketlerin Microsoft tarafından barındırılan sunuculardan internete indirildikten sonra indirilmalarını önler.

 ```shell
    \\server\share\VSlayoutdirectory\vs_enterprise.exe --quiet --update
    \\server\share\VSlayoutdirectory\vs_enterprise.exe update --installPath "C:\clientmachine\installpath" --noWeb --wait --quiet --norestart
 ```
    
İstemcinin güncelleştirmelerini ağ düzeninden alıyor olmasını sağlamak için ve seçeneklerini tek bir komutta ağ düzeninde önyükleyiciye `--noweb` `--noUpdateInstaller` iletirsiniz. önceki, güncelleştirilmiş iş yüklerinin ve bileşenlerin internetten indir indirebilirsiniz ve ikincisi yükleyicinin kendi kendini güncelleştirmesini önler. Kullanılabilir durumdayken bu seçenek genellikle önerilmez çünkü her zaman en son ve en büyük yükleyiciyi kullansanız iyi olur.

> [!IMPORTANT]
> seçeneği, `--noWeb` İnternet'e Visual Studio bir bilgisayarda kurulumun güncelleştirmeleri _denetlemesi için bu ayarı_ durdurmaz. Bunun yerine, istemcinin ürün paketlerini indirmesini önler. Daha fazla bilgi için Ağ [tabanlı dağıtımlarda güncelleştirmeleri denetleme Visual Studio bakın.](controlling-updates-to-visual-studio-deployments.md)

## <a name="get-support-for-your-network-layout"></a>Ağ düzeniniz için destek al

Ağ düzeniniz ile ilgili bir sorun yaşamanız, bunun hakkında bilgi almak istiyor. Bize söylemenin en iyi yolu, hem Visual Studio Yükleyicisi hem de Visual Studio IDE'de görünen Sorun Bildir aracını kullanmaktır. [](/visualstudio/ide/how-to-report-a-problem-with-visual-studio) BIR IT Yöneticisiyseniz ve yüklü bir Visual Studio yoksa, BURADA IT Yöneticisi geri [**bildirimi gönderebilirsiniz.**](https://aka.ms/vs/admin/guide) Bu aracı kullanırsanız, vs [Collect](https://aka.ms/vscollect) aracından günlükleri gönderebilirsiniz ve bu da sorunu tanılamamıza ve düzeltmemıza yardımcı olabilir.

Ayrıca yüklemeyle ilgili [**sorunlar için bir**](https://visualstudio.microsoft.com/vs/support/#talktous) yükleme sohbeti (yalnızca İngilizce) destek seçeneği sunuyoruz.

Başka destek seçenekleri de mevcuttur. Geliştirici [Visual Studio'mıza Community.](https://developercommunity.visualstudio.com/home)


## <a name="see-also"></a>Ayrıca bkz.

* [Ağ düzeni oluşturma ve sürdürme](create-a-network-installation-of-visual-studio.md)
* [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
* [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio örneklerini algılamaya ve yönetmeye yönelik araçlar](tools-for-managing-visual-studio-instances.md)
* [Ağ tabanlı dağıtımlarda güncelleştirmeleri Visual Studio denetleme](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio yaşam döngüsü ve bakım](/visualstudio/releases/2019/servicing/)
