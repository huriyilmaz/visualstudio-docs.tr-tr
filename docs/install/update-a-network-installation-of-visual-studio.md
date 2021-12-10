---
title: Ağ tabanlı yüklemeyi güncelleştirme
description: bir ağ düzeninden yüklenmiş bir Visual Studio istemcisini güncelleştirme hakkında bilgi edinin
ms.date: 12/7/2021
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
ms.openlocfilehash: d1961c85d6c918e9b3dcdbef9bf5511b77998186
ms.sourcegitcommit: 99e0146dfe742f6d1955b9415a89c3d1b8afe4e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2021
ms.locfileid: "134553992"
---
# <a name="update-a-visual-studio-client-that-was-installed-from-a-network-layout"></a>bir ağ düzeninden yüklenmiş bir Visual Studio istemcisini güncelleştirme

tüm Visual Studio istemcileri, en son güvenlik ve işlev düzeltmelerini alacak şekilde düzenli olarak güncelleştirmeniz gerekir. 

Visual Studio istemcisi ilk olarak bir ağ düzeni aracılığıyla yüklendiyse, büyük olasılıkla istemci makine bir "yönetilen ortamın" parçasıdır ve bu da merkezi bir yönetim ekibi tarafından yönetilir ve kuruluş ilkelerine uyması gerekir. Yönetilen bir ortamdaki istemci makinelerini güncelleştirmek için, yanıtları güncelleştirme işlemine nasıl yaklaşıma dikkat etmeniz gerektiğini bildiren aşağıdaki soruları göz önünde bulundurun. 

-  Güncelleştirmeler nereden geliyor: bir ağ düzeni veya Microsoft barındırılan sunucular? Güncelleştirme bir ağ düzeninden geliyorsa, ağ düzeni hazırlandı mı?
-  Güncelleştirme Kullanıcı tarafından başlatılacak mı, yoksa yöneticinin başlattığı bir olay mı? Güncelleştirme gerçekleştirdiğine ilişkin yönetici izinlerinin olması gerektiğini unutmayın.

## <a name="prepare-the-update-source"></a>Güncelleştirme kaynağını hazırlama

İstemcinizi Microsoft tarafından barındırılan sunuculardan güncelleyecekseniz, istemci bu [kanalda](/visualstudio/releases/2022/vs2022-release-rhythm)Microsoft 'tan erişilebilen en son sürümü indirip yükler. 

İstemcinizi bir ağ düzeninden güncelleştirileyecekseniz, ilk adım ağ düzeninin güncelleştirilmiş ürünle hazırlanması olur. [Mevcut düzeninizi en son ürün güncelleştirmeleriyle güncelleştirebilirsiniz](/visualstudio/install/create-a-network-installation-of-visual-studio#update-or-modify-your-layout) , böylece yeni yüklemeler ve güncelleştirmelerin her ikisi de güncelleştirilmiş sürümü alacaktır. Ya da, istemci makinelerini güncelleştirmek için kullanabileceğiniz farklı bir dizinde bir [bütün yeni düzen oluşturabilirsiniz](/visualstudio/install/create-a-network-installation-of-visual-studio) .

## <a name="enable-manual-user-initiated-client-side-updates"></a>El ile Kullanıcı tarafından başlatılan istemci tarafı güncelleştirmelerini etkinleştir 
istemci makinedeki yeterli izinlere sahip bir kullanıcı [Visual Studio güncelleştirmeyi kendiniz başlatabilir](/visualstudio/install/update-visual-studio). Visual Studio istemci güncelleştirmelerin kullanılabilir olduğunu tanıyabilmesi için doğru kaynak konumuna bakmak üzere doğru şekilde yapılandırılmalıdır. güncelleştirme gerçekleştiğinde herhangi bir dosya kullanımda olduğunda, Visual Studio açıksa olduğu gibi, güncelleştirmenin tamamlanabilmesi için Visual Studio kapatılması gerekir. Bazen bir güncelleştirme yeniden başlatma gerektirir.

### <a name="manually-configure-where-the-visual-studio-client-looks-for-updates"></a>Visual Studio istemcisinin güncelleştirmeler için nerede göründüğünü el ile yapılandırın

Visual Studio başlangıçta istemci makinesine yüklendiğinde, güncelleştirmeleri denetlemesi gereken konumu kaydeder. microsoft tarafından barındırılan sunuculardan Visual Studio yüklenmişse, varsayılan olarak microsoft 'un barındırıldığı sunuculardan güncelleştirmeleri arar. bir ağ düzeninde önyükleyici çağırarak Visual Studio yüklendiyse veya güncelleştirilirse, bu durumda, [düzen tarafından belirtilen konumdaki](/visualstudio/install/automated-installation-with-response-file)güncelleştirmeler görünür.  

::: moniker range="vs-2017"

Visual Studio 2017 ' de, istemci ürünü yükledikten sonra istemcinin güncelleştirme konumu yapılandırması kilitlidir ve kilitleme geri yüklenebilir. Güncelleştirmeler için farklı bir kaynak konum yapılandırmak üzere, doğru düzen yapılandırmasını kullanarak ürünü kaldırmanız ve yeniden yüklemeniz gerekir.

::: moniker-end

::: moniker range="vs-2019"

varsayılan Visual Studio 2019 işlevselliğiyle, istemci ürünü yükledikten sonra istemcinin güncelleştirme konumu yapılandırması kilitlenir ve bu özellik, geri yüklenemez. Güncelleştirmelerin kaynak konumunu _güvenilir_ bir şekilde değiştirmek için tek yol, doğru yapılandırmayı kullanarak ürünü kaldırmak ve yeniden yüklemektir.
 
ancak, Visual Studio istemcisi en son Visual Studio 2022 yükleyicisini kullanıyorsa, istemci güncelleştirmeleri için kaynak konumu değiştirilebilir. Bu, bir düzenden yüklemek istiyorsanız ancak güncelleştirmelerin başka bir düzenden gelmesi durumunda yararlıdır. Visual Studio 2022 yükleyicisini bir istemci makinesine almanın iki yolu vardır. en kolay Visual Studio 2022 ürününü yüklemek ve kullanmak yeterlidir. alternatif olarak, [Visual Studio 2022 yükleyicisini Visual Studio 2019 düzenlerinizi kullanarak dağıtabilirsiniz](/visualstudio/install/create-a-network-installation-of-visual-studio#configure-the-layout-to-always-use-the-latest-installer).

::: moniker-end

::: moniker range=">=vs-2019"

istemcinin güncelleştirmeleri arayacağı güncelleştirme konumunu el ile görüntülemek ve yapılandırmak için [güncelleştirme Ayarlar](/visualstudio/install/update-visual-studio?view=vs-2022&preserve-view=true#configure-source-location-of-updates-1)' yi getirin, doğru yapılandırıldığından emin olun. Bundan sonra güncelleştirmeyi istemciden başlatabilirsiniz.  

::: moniker-end

### <a name="update-notifications"></a>Güncelleştirme bildirimleri

İstemcide güncelleştirmeler arayan bir güncelleştirme varsa, istemci [bir ileti veya bir bildirim bayrağı](/visualstudio/install/update-visual-studio?#use-the-message-box-in-the-ide-1)görünecektir.  

güncelleştirme bildirimlerinin kullanıcılara ne zaman sunulduğunu denetleme hakkında daha fazla bilgi için bkz. [ağ tabanlı Visual Studio dağıtımlarında güncelleştirmeleri denetleme](/visualstudio/install/set-defaults-for-enterprise-deployments#controlling-notifications-in-the-visual-studio-ide).

### <a name="manually-initiate-the-update"></a>Güncelleştirmeyi el ile başlatın

kullanıcılar, bir Visual Studio örneğini [el ile güncelleştirebilir](/visualstudio/install/update-visual-studio) : 
  * Visual Studio Yükleyicisi başlatılıyor. Bir güncelleştirme varsa **Güncelleştir**' e tıklayabilir.
  * Visual Studio ıde 'yi başlatma ve bildirim bayrağına veya iletisine yanıt verme veya güncelleştirme için yardım/denetim 'i seçme.  

## <a name="programatically-update-the-client-machines"></a>Program aracılığıyla istemci makinelerini güncelleştirme
yöneticiler, istemci tarafı yükleyicisinden komutları yayımlayarak veya düzende bir önyükleyici çağırarak Visual Studio istemci yüklemelerini programlı bir şekilde güncelleştirebilir.

### <a name="programatically-update-visual-studio-by-using-the-visual-studio-installer"></a>Visual Studio Yükleyicisi kullanarak Visual Studio güncelleştirme program aracılığıyla

::: moniker range="vs-2017"

istemci yükleyicisini programlı olarak çağırarak ve update komutunu yayımlayarak Visual Studio bir güncelleştirme başlatabilirsiniz. Örnek:

```shell
c:\program files (x86)\microsoft\visual studio\installer\>setup.exe update --installPath "C:\Program Files\Microsoft Visual Studio\2017\Enterprise" 
```

::: moniker-end

::: moniker range=">=vs-2019"

istemci yükleyicisini programlı olarak çağırarak ve update komutunu yayımlayarak Visual Studio bir güncelleştirme başlatabilirsiniz. bu komut Visual Studio [güncelleştirmeler için kaynak konumda](/visualstudio/install/update-visual-studio#configure-source-location-of-updates-1)bulunan güncelleştirilmiş ürüne bağlı olarak güncelleştirilecek. İstemcideki güncelleştirme kaynak konumunu değiştirmek istiyorsanız,--channelURI parametresini geçirerek bu program aracılığıyla yapabilirsiniz. Örnek:  

Kanalı bir ağ düzeni olarak değiştirebilir _ve_ istemcide şu şekilde bir güncelleştirme komutu yürütebilirsiniz:

```shell
c:\program files (x86)\microsoft\visual studio\installer\>setup.exe update --installPath "C:\Program Files\Microsoft Visual Studio\2019\Enterprise" --channelURI "\\\\server\\share\\newlayoutdir\\channelmanifest.json"
```
Bunun gibi, güncelleştirme kaynağını Microsoft tarafından barındırılan bir konuma ayarlayan:

```shell
c:\program files (x86)\microsoft\visual studio\installer\>setup.exe update --installPath "C:\Program Files\Microsoft Visual Studio\2019\Enterprise" --channelURI "https://aka.ms/vs/16/release/channel"
```

::: moniker-end

### <a name="programatically-update-visual-studio-by-using-a-bootstrapper"></a>Program aracılığıyla bir önyükleyici kullanarak Visual Studio 'yu güncelleştirin.

::: moniker range=">=vs-2017"

program aracılığıyla tarafından, ilk olarak yüklediğiniz konumdan bir önyükleyici çağırarak Visual Studio güncelleştirebilirsiniz. Microsoft tarafından barındırılan sunuculardan kaynaklanan tüm bootstrap'lar aynı konumdan kabul edilir. Önyükleyici bir ağ düzeni paylaşımındaysa, ağ düzeninin istenen ürün güncelleştirmelerini içermesi için [güncelleştirilmeleri gerekir](/visualstudio/install/create-a-network-installation-of-visual-studio#update-or-modify-your-layout) .

```shell
\\server\share\originalinstallVSdirectory\vs_enterprise.exe update --installPath "C:\clientmachine\installpath" --quiet 
```

::: moniker-end

::: moniker range="vs-2019"

ayrıca, istemciyi güncelleştirmek istediğiniz ürünün sürümünü içeren _farklı_ bir kaynak konumundan önyükleyici çağırarak, Visual Studio 2019 istemcinizi bir güncelleştirme de başlatabilirsiniz. bunu yapmak için istemcide Visual Studio 2022 yükleyicisini almanız gerekir. bunu etkinleştirmenin en kolay yolu, [yeni Visual Studio 2019 düzeniniz en son yükleyiciyi kullandığından emin](/visualstudio/install/create-a-network-installation-of-visual-studio#ensure-your-layout-is-using-the-latest-installer)sağlamaktır. Önyükleyici yeni bir düzenden çalıştırırsanız, istemcideki güncelleştirme kanalı, [düzende belirtilen güncelleştirme konumuna](/visualstudio/install/automated-installation-with-response-file)ayarlanır. Örneğin, bu komutu istemci makinesinde çalıştırabilirsiniz:

::: moniker-end

::: moniker range=">=vs-2022"

ayrıca, istemciyi güncelleştirmek istediğiniz ürünün sürümünü içeren _farklı_ bir kaynak konumundan önyükleyici çağırmak program aracılığıyla tarafından Visual Studio istemciniz için bir güncelleştirme başlatabilirsiniz. Önyükleyici yeni bir düzenden çalıştırırsanız, istemcideki güncelleştirme kanalı, [düzende belirtilen güncelleştirme konumuna](/visualstudio/install/automated-installation-with-response-file)ayarlanır. Örneğin, bu komutu istemci makinesinde çalıştırabilirsiniz:

::: moniker-end

::: moniker range=">=vs-2019"

```shell
   \\server\share\desiredupdatelayoutdir\vs_enterprise.exe update --installPath "C:\clientmachine\installpath" --quiet 
```
Düzenin Response. JSON dosyasındaki channelURI değeri, istemcinin gelecekteki güncelleştirmeleri aradığı konum olacaktır.

::: moniker-end

> [!NOTE]
> bir istemci makinesinde var olan bir Visual Studio örneğinin yüklemesinin yolunu tanımlamak için [vswhere.exe komutunu](tools-for-managing-visual-studio-instances.md) kullanın.

### <a name="programatically-update-a-client-that-doesnt-have-internet-access"></a>Program aracılığıyla internet erişimi olmayan bir istemciyi güncelleştirme

İstemci makinenizin internet erişimi yoksa, güncelleştirmeleri bir ağ _düzeninden almalıdır._ Visual Studio her güncelleştirildiğinde güncellenmesi gereken iki bölüm olduğunu unutmayın. birincisi yükleyicidir ve ikincisi Visual Studio ürünün kendisidir. istemci makinesinde bu komutları çalıştırarak, bu bileşenlerin _her ikisini de_ ağ düzeninden _açıkça_ aramak için Visual Studio söyleyebilirsiniz. İlk komut, yükleyicinin düzenden gelmesini zorlar ve ikinci komut, tüm paketlerin internet 'teki Microsoft tarafından barındırılan sunuculardan indirilmesini engeller.

 ```shell
    \\server\share\VSlayoutdirectory\vs_enterprise.exe --quiet --update
    \\server\share\VSlayoutdirectory\vs_enterprise.exe update --installPath "C:\clientmachine\installpath" --noWeb --wait --quiet --norestart
 ```
    
İstemcinin ağ düzeninden güncelleştirmelerini aldığından emin olmanın bir diğer yolu da, `--noweb` `--noUpdateInstaller` ağ düzeninde önyükleyici için tek bir komutta ve seçenekleri geçmektir. İlki, güncelleştirilen iş yüklerini, internet 'ten bileşenleri indirmeyi engeller ve ikinci, yükleyicinin kendi kendini güncellemeden engel olur. Her zaman en son ve en büyük yükleyiciyi kullanmanız gerektiğinden, kullanılabilir durumdayken bu seçenek genellikle önerilmez.

> [!IMPORTANT]
> bu `--noWeb` seçenek, internet 'e bağlı bir bilgisayardaki güncelleştirmeleri _denetlemek_ için Visual Studio kurulum 'u durdurmaz. Bunun yerine, istemcinin ürün paketlerini indirmesine engel olur. daha fazla bilgi için bkz. [ağ tabanlı Visual Studio dağıtımları için güncelleştirmeleri denetleme](controlling-updates-to-visual-studio-deployments.md) sayfası.

## <a name="get-support-for-your-network-layout"></a>Ağ düzeniniz için destek alın

Ağ düzeninizle ilgili bir sorunla karşılaşırsanız, bunun hakkında bilgi sahibi olmak istiyoruz. bize söylemek için en iyi yol, hem Visual Studio Yükleyicisi hem de Visual Studio ıde 'de görüntülenen [sorun bildir](/visualstudio/ide/how-to-report-a-problem-with-visual-studio) aracını kullanmaktır. bt yöneticisiyseniz ve yüklü Visual Studio yoksa, [**buraya buraya, yönetici geri bildirimi**](https://aka.ms/vs/admin/guide)gönderebilirsiniz. Bu aracı kullandığınızda, bu sorunu tanılamanıza ve gidermenize yardımcı olabilecek [vs Collect aracından günlükleri](https://aka.ms/vscollect) gönderebiliyorsanız çok yararlı olacaktır.

Ayrıca, yükleme ile ilgili sorunlar için bir [**yükleme sohbeti**](https://visualstudio.microsoft.com/vs/support/#talktous) (yalnızca İngilizce) için destek seçeneği sunuyoruz.

Diğer destek seçenekleri de mevcuttur. [Visual Studio geliştirici Community](https://developercommunity.visualstudio.com/home)bakın.


## <a name="see-also"></a>Ayrıca bkz.

* [Ağ düzeni oluşturma ve sürdürme](create-a-network-installation-of-visual-studio.md)
* [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
* [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio örneklerini algılamaya ve yönetmeye yönelik araçlar](tools-for-managing-visual-studio-instances.md)
* [ağ tabanlı Visual Studio dağıtımlarında güncelleştirmeleri denetleme](controlling-updates-to-visual-studio-deployments.md)
* [ürün yaşam döngüsü ve bakım Visual Studio](/visualstudio/releases/2019/servicing/)
