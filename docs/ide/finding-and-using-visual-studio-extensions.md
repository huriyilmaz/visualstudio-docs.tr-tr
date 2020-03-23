---
title: Uzantıları bulma ve yükleme
ms.date: 09/18/2019
ms.topic: conceptual
f1_keywords:
- vs.ExtensionManager
helpviewer_keywords:
- install extensions
- install packages
- managing extensions visual studio
ms.assetid: 4ca92d93-31b9-47ef-8109-4a429d9e2ca3
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f016af58b5799ca37b1a8f0cc54366d639c57c03
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594415"
---
# <a name="manage-extensions-for-visual-studio"></a>Visual Studio için uzantıları yönetme

Uzantılar, Visual Studio içinde çalışan ve yeni veya geliştirilmiş özellikler sağlayan kod paketleridir. Uzantılar, Visual Studio'ya işlevsellik katan denetimler, örnekler, şablonlar, araçlar veya diğer bileşenler olabilir, [örneğin, Live Share](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsls-vs) veya [Visual Studio IntelliCode.](https://marketplace.visualstudio.com/items?itemName=VisualStudioExptTeam.VSIntelliCode)

Visual Studio uzantıları oluşturma hakkında daha fazla bilgi için [Visual Studio SDK'ya](../extensibility/visual-studio-sdk.md)bakın. Uzantıları kullanma hakkında daha fazla bilgi için [Visual Studio Marketplace'teki](https://marketplace.visualstudio.com)tek tek uzantı sayfasına bakın.

::: moniker range="vs-2017"

## <a name="extensions-and-updates-dialog-box"></a>Uzantılar ve Güncelleştirmeler iletişim kutusu

Visual Studio uzantılarını yüklemek ve yönetmek için **Uzantılar ve Güncelleştirmeler** iletişim kutusunu kullanın. **Uzantılar ve Güncelleştirmeler** iletişim kutusunu açmak için **Araçlar** > **Uzantıları ve Güncelleştirmeleri'ni**seçin veya **Hızlı Başlatma** arama kutusuna **Uzantılar** yazın.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="manage-extensions-dialog-box"></a>Uzantıları yönet iletişim kutusunu yönet

Visual Studio uzantılarını yüklemek ve yönetmek için **Uzantıları Yönet** iletişim kutusunu kullanın. **Uzantıları Yönet** iletişim kutusunu açmak için **Uzantıları** > **Yönet Uzantıları'nı**seçin. Veya arama kutusuna **Uzantılar** yazın ve **Uzantıları Yönet'i**seçin.

::: moniker-end

![Visual Studio'da uzantılar penceresi](media/finding-using-visual-studio-extensions/extensions-and-updates.png)

Soldaki bölme, uzantıları yüklenenlere, Visual Studio Marketplace'te **(Çevrimiçi)** bulunanlara ve güncelleştirmeleri bulunanlara göre kategorilere ayırıyor. **Roaming Extension Manager,** Visual Studio'nun herhangi bir makinesine veya örneğine yüklediğiniz tüm Visual Studio uzantılarının listesini tutar. En sevdiğiniz uzantıları daha kolay bulmanızı sağlamak için tasarlanmıştır.

## <a name="find-and-install-extensions"></a>Uzantıları bulma ve yükleme

::: moniker range="vs-2017"

[Visual Studio Marketplace](https://marketplace.visualstudio.com) uzantılarını veya Visual Studio'daki Uzantılar ve Güncellemeler iletişim kutusundan yükleyebilirsiniz.

Visual Studio içinden uzantıları yüklemek için:

1. **Araçlar** > **Uzantıları ve Güncelleştirmeleri'nden**yüklemek istediğiniz uzantıyı bulun. Uzantının adını veya bölümünü biliyorsanız, **Arama** penceresinde arama yapabilirsiniz.

2. **Download** (İndir) seçeneğini belirleyin.

   Uzantı yüklemek için zamanlanır. Visual Studio'nun tüm örnekleri kapatıldıktan sonra uzantınız yüklenir.

Bağımlılıkları olan bir uzantıyı yüklemeye çalışırsanız, yükleyici bunların yüklenmiş olup olmadığını denetler. Bunlar yüklenmezse, **Uzantılar ve Güncelleştirmeler** iletişim kutusu, uzantıyı yükleyemeden önce yüklenmesi gereken bağımlılıkları listeler.

### <a name="install-without-using-the-extensions-and-updates-dialog-box"></a>Uzantılar ve Güncelleştirmeler iletişim kutusunu kullanmadan yükleme

*.vsix* dosyalarında paketlenmiş uzantılar Visual Studio Marketplace dışındaki konumlarda kullanılabilir. **Araçlar** > **Uzantıları ve Güncelleştirmeleri** iletişim kutusu bu dosyaları algılayamaz, ancak dosyayı çift tıklatarak veya dosyayı seçerek ve **Enter**tuşuna basarak *.vsix* dosyasını yükleyebilirsiniz. Ondan sonra, sadece talimatları izleyin. Uzantı yüklendiğinde, uzantıları etkinleştirmek, devre dışı kaldırmak veya kaldırmak için **Uzantılar ve Güncelleştirmeler** iletişim kutusunu kullanabilirsiniz.

> [!NOTE]
> - Visual Studio Marketplace hem VSIX hem de MSI uzantıları içerir. Uzantılar ve Güncelleştirmeler iletişim kutusu MSI tabanlı uzantıları etkinleştiremez veya devre dışı kılamaz.
> - MSI tabanlı bir uzantı *bir uzantı.vsixmanifest* dosyası içeriyorsa, uzantı **Uzantılar ve Güncelleştirmeler** iletişim kutusunda görünür.

::: moniker-end

::: moniker range=">=vs-2019"

[Visual Studio Marketplace'ten](https://marketplace.visualstudio.com) uzantılar veya Visual Studio'da Uzantıları Yönet iletişim kutusundan yükleyebilirsiniz.

Visual Studio içinden uzantıları yüklemek için:

1. **Uzantıları** > **Yönet Uzantıları'ndan,** yüklemek istediğiniz uzantıyı bulun. (Uzantının adını veya bölümünü biliyorsanız, **Arama** penceresinde arama yapabilirsiniz.)

2. **Download** (İndir) seçeneğini belirleyin.

   Uzantı yüklemek için zamanlanır. Visual Studio'nun tüm örnekleri kapatıldıktan sonra uzantınız yüklenir.

Bağımlılıkları olan bir uzantıyı yüklemeye çalışırsanız, yükleyici bunların yüklenmiş olup olmadığını denetler. Bunlar yüklenmezse, Uzantıları Yönet iletişim kutusu, uzantıyı yükleyemeden önce yüklenmesi gereken **bağımlılıkları** listeler.

### <a name="install-without-using-the-manage-extensions-dialog-box"></a>Uzantıları Yönet iletişim kutusunu kullanmadan yükleme

*.vsix* dosyalarında paketlenmiş uzantılar Visual Studio Marketplace dışındaki konumlarda kullanılabilir. **Uzantıları** > **Yönet uzantıları** iletişim kutusu bu dosyaları algılayamaz, ancak dosyayı çift tıklatarak veya dosyayı seçerek ve **Enter**tuşuna basarak .vsix dosyasını yükleyebilirsiniz. *.vsix* Ondan sonra, sadece talimatları izleyin. Uzantı yüklendiğinde, etkinleştirmek, devre dışı kaldırmak veya kaldırmak için **Uzantıları Yönet** iletişim kutusunu kullanabilirsiniz.

> [!NOTE]
> - Visual Studio Marketplace hem VSIX hem de MSI uzantıları içerir. Uzantıları Yönet iletişim kutusu MSI tabanlı uzantıları etkinleştiremez veya devre dışı kılamaz.
> - MSI tabanlı bir uzantı *bir uzantı.vsixmanifest* dosyası içeriyorsa, uzantı **Uzantıları Yönet** iletişim kutusunda görünür.

::: moniker-end

## <a name="uninstall-or-disable-an-extension"></a>Uzantıyı kaldırma veya devre dışı kaldırma

Bir uzantıyı kullanmayı bırakmak isterseniz devre dışı bırakabilir veya kaldırabilirsiniz. Bir uzantı devre dışı bırakıldığında yüklü kalır, ancak etkin değildir. Uzantıyı bulun ve **Kaldır** veya **Devre Dışı Kaldır'ı**tıklatın. Devre dışı bırakılmış bir uzantıyı boşaltmak için Visual Studio'yı yeniden başlatın.

> [!NOTE]
> MsI kullanılarak yüklenen VSIX uzantılarını devre dışı kaldırabilirsiniz. MSI yüklü uzantılar yalnızca kaldırılabilir.

## <a name="per-user-and-administrative-extensions"></a>Kullanıcı başına ve yönetim uzantıları

Uzantıların çoğu kullanıcı başınadır ve *%LocalAppData%\Microsoft\VisualStudio\\<Visual\>Studio sürümü\\ \Extensions* klasörüne yüklenir. Birkaç uzantı yönetim uzantılarıdır ve Visual * \<Studio yükleme klasörüne\\>\Common7\IDE\Extensions* klasörüne yüklenir.

Sisteminizi hatalar veya kötü amaçlı kod içerebilecek uzantılara karşı korumak için, kullanıcı başına uzantıları yalnızca Visual Studio normal kullanıcı izinleriyle çalıştırıldığında yüklenmesini kısıtlayabilirsiniz. Bu, Visual Studio yüksek izinlerle çalıştırıldığında kullanıcı başına uzantıların devre dışı bırakıldığı anlamına gelir.

Kullanıcı başına uzantıların yüklenmesini kısıtlamak için:

1. Uzantıseçenekleri sayfasını açın (**Araç** > **Seçenekleri** > **Ortamı** > **Uzantıları**).

2. Yönetici onay kutusu **olarak çalışırken kullanıcı uzantıları başına Yükle'yi** temizleyin.

3. Visual Studio'yu yeniden başlatın.

## <a name="automatic-extension-updates"></a>Otomatik uzantı güncelleştirmeleri

Uzantılar Visual Studio Marketplace'te yeni bir sürüm bulunduğunda otomatik olarak güncellenir. Uzantının yeni sürümü algılanır ve arka planda yüklenir. Visual Studio'yu bir sonraki açtığınızda, uzantının yeni sürümü çalışır.

Otomatik güncelleştirmeleri devre dışı kullanabilirsiniz, özelliği tüm uzantılar için veya yalnızca belirli uzantılar için devre dışı kullanabilirsiniz.

::: moniker range="vs-2017"

- Tüm uzantılar için otomatik güncelleştirmeleri devre dışı kalmak **için, Araçlar** > **Uzantıları ve Güncelleştirmeleri** iletişim kutusundaki **Uzantılar ve Güncelleştirmeler ayarlarınızı değiştir** bağlantısını seçin. **Seçenekler** iletişim kutusunda, **uzantıları otomatik olarak güncelleştir'in**denetimini kaldırın.

- Belirli bir uzantı için otomatik güncelleştirmeleri devre dışı bırakıp, **Uzantılar ve Güncelleştirmeler** iletişim kutusunun sağ tarafındaki uzantının ayrıntılar bölmesinde **bu uzantıyı otomatik olarak güncelleştirme** seçeneğini kaldırın.

::: moniker-end

::: moniker range=">=vs-2019"

- Tüm uzantılar için otomatik güncelleştirmeleri devre dışı kalmak için **Extensions** > Uzantıları**Yönet** iletişim kutusunda **uzantılar için ayarlarınızı değiştir** bağlantısını seçin. **Seçenekler** iletişim kutusunda, **uzantıları otomatik olarak güncelleştir'in**denetimini kaldırın.

- Belirli bir uzantı için otomatik güncelleştirmeleri devre dışı kalmak için, **Uzantıları Yönet** iletişim kutusunun sağ tarafındaki uzantının ayrıntılar bölmesinde **bu uzantıyı otomatik olarak güncelleştirme** seçeneğini kaldırın.

::: moniker-end

## <a name="crash-and-unresponsiveness-notifications"></a>Kilitlenme ve yanıt vermeme bildirimleri

Visual Studio, bir önceki oturumda bir uzatmanın bir kazaya karıştığından şüphelenirse sizi fark edin. Visual Studio çöktüğe göre, özel durum yığınını depolar. Visual Studio bir dahaki sefere, yaprakile başlayan ve tabanına doğru çalışan, yığını inceler. Visual Studio, bir çerçevenin yüklü ve etkin bir uzantının parçası olan bir modüle ait olduğunu belirlerse, bir bildirim gösterir.

Visual Studio ayrıca, ui'nin yanıt vermemesine neden olan bir uzantıdan şüpheleniyorsa sizi de size haber verir.

Bu bildirimler gösterildiğinde, bildirimi yoksayabilir veya aşağıdaki eylemlerden birini alabilirsiniz:

::: moniker range="vs-2017"

- **Bu uzantıyı devre dışı bırakmayı**seçin. Visual Studio uzantıyı devre dışı düşürür ve devre dışı bırakmanın etkili olması için sisteminizi yeniden başlatmanız gerekip gerekmediğini bilmenizi sağlar. İsterseniz **Araçlar** > **Uzantıları ve Güncelleştirmeleri** iletişim kutusunda uzantıyı yeniden etkinleştirebilirsiniz.

::: moniker-end

::: moniker range=">=vs-2019"

- **Bu uzantıyı devre dışı bırakmayı**seçin. Visual Studio uzantıyı devre dışı düşürür ve devre dışı bırakmanın etkili olması için sisteminizi yeniden başlatmanız gerekip gerekmediğini bilmenizi sağlar. İsterseniz **Uzantıları** > **Yönet Uzantıları** Iletişim kutusunda uzantıyı yeniden etkinleştirebilirsiniz.

::: moniker-end

- **Bu iletiyi bir daha asla gösterme'yi**seçin.

  - Bildirim önceki oturumda bir kilitlenmeyle ilgiliyse, Visual Studio bu uzantıyla ilişkili bir kilitlenme oluştuğunda artık bir bildirim göstermez. Visual Studio, yanıt vermeme bu uzantıyla ilişkilendirildiğinde veya diğer uzantılarla ilişkilendirilebilen kilitlenmeler veya yanıt vermeme için bildirimler göstermeye devam eder.
  - Bildirim yanıt vermeme yle ilgiliyse, tümleşik geliştirme ortamı (IDE), bu uzantı yanıt vermeme ile ilişkilendirildiğinde artık bir bildirim göstermez. Visual Studio, bu uzantı ve diğer uzantılar için kilitlenme ve yanıt vermeyle ilgili bildirimler için çökmeyle ilgili bildirimleri göstermeye devam edecektir.

- Bu sayfaya gitmek için **daha fazla bilgi** edinin'i seçin.

- Bildirimi kapatmak için bildirimin sonundaki **X** düğmesini seçin. Uzantının bir kilitlenme veya UI yanıt vermeme ile ilişkili olan gelecekteki örnekleri için yeni bir bildirim görüntülenir.

> [!NOTE]
> UI yanıt vermeme veya kilitlenme bildirimi, ui yanıt vermediğinde veya kilitlenme oluştuğunda yalnızca uzantının modüllerinden birinin yığında olduğu anlamına gelir. Bu mutlaka uzantısı kendisi suçlu olduğu anlamına gelmez. Visual Studio'nun bir parçası olan kod adı verilen uzantı, yanıt vermeyen ui veya bir çökmeile sonuçlanmış olabilir. Ancak, UI yanıt vermemeveya kilitlenme yol açan uzantısı sizin için önemli değilse bildirim yine de yararlı olabilir. Bu durumda, uzantını devre dışı bırakmak, üretkenliğinizi etkilemeden ui yanıt vermemeyi veya gelecekte çökmeyi önler.

## <a name="samples"></a>Örnekler

Çevrimiçi bir örneği yüklediğinizde, çözüm iki konumda depolanır:

- Çalışan bir kopya, projeyi oluşturduğunuzda belirttiğiniz konumda depolanır.

- Ayrı bir ana kopya bilgisayarınızda depolanır.

::: moniker range="vs-2017"

**Örneklerle** > ilgili bu görevleri gerçekleştirmek için Araçlar **Uzantıları ve Güncelleştirmeleri** iletişim kutusunu kullanabilirsiniz:

::: moniker-end

::: moniker range=">=vs-2019"

Bu örneklerle ilgili görevleri gerçekleştirmek için **Uzantıları** > **Yönet uzantıları** iletişim kutusunu kullanabilirsiniz:

::: moniker-end

- Yüklediğiniz örneklerin ana kopyalarını listeleyin.

- Bir örneğin ana kopyasını devre dışı bırakın veya kaldırın.

- Örnek Paketleri (bir teknoloji veya özellik ile ilgili örnek koleksiyonları) yükleyin.

- Tek tek çevrimiçi örnekleri yükleyin.

- Yüklü örnekler için kaynak kodu değişiklikleri yayımlandığında güncelleştirme bildirimlerini görüntüleyin.

- Güncelleştirme bildirimi olduğunda yüklü bir örneğin ana kopyasını güncelleştirin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Market](https://marketplace.visualstudio.com)
- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)
