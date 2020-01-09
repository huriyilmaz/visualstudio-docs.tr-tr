---
title: Uzantıları bul ve yüklensin
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594415"
---
# <a name="manage-extensions-for-visual-studio"></a>Visual Studio için uzantıları yönetme

Uzantılar, Visual Studio içinde çalışan ve yeni veya geliştirilmiş özellikler sağlayan kod paketlerdir. Uzantılar, Visual Studio 'ya işlev ekleyen denetimler, örnekler, şablonlar, araçlar veya başka bileşenler (örneğin, [live share](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsls-vs) veya [Visual Studio ıntellicode](https://marketplace.visualstudio.com/items?itemName=VisualStudioExptTeam.VSIntelliCode)) olabilir.

Visual Studio uzantıları oluşturma hakkında daha fazla bilgi için bkz. [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md). Uzantıları kullanma hakkında daha fazla bilgi için, [Visual Studio Market](https://marketplace.visualstudio.com)tek tek uzantı sayfasına bakın.

::: moniker range="vs-2017"

## <a name="extensions-and-updates-dialog-box"></a>Uzantılar ve güncelleştirmeler iletişim kutusu

Visual Studio uzantılarını yüklemek ve yönetmek için **Uzantılar ve güncelleştirmeler** iletişim kutusunu kullanın. **Uzantılar ve güncelleştirmeler** iletişim kutusunu açmak için **Araçlar** > **Uzantılar ve güncelleştirmeler**' i seçin veya **Hızlı başlatma** arama kutusuna **Uzantılar** yazın.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="manage-extensions-dialog-box"></a>Uzantıları Yönet iletişim kutusu

Visual Studio uzantılarını yüklemek ve yönetmek için **Uzantıları Yönet** iletişim kutusunu kullanın. **Uzantıları Yönet** iletişim kutusunu açmak için, uzantıları **Yönet** > **Uzantılar** ' ı seçin. Ya da, arama kutusuna **Uzantılar** yazın ve **Uzantıları Yönet**' i seçin.

::: moniker-end

![Visual Studio 'da uzantılar penceresi](media/finding-using-visual-studio-extensions/extensions-and-updates.png)

Sol taraftaki bölme, yüklenmiş olanlar, Visual Studio Market (**çevrimiçi**) ve güncelleştirmeleri olan güncelleştirmeler tarafından kategorilere ayırır. **Dolaşım uzantısı Yöneticisi** , Visual Studio 'nun herhangi bir makinesinde veya örneğinde yüklü olan tüm Visual Studio uzantılarının bir listesini tutar. En sevdiğiniz uzantıları daha kolay bir şekilde bulmanıza olanak sağlayacak şekilde tasarlanmıştır.

## <a name="find-and-install-extensions"></a>Uzantıları bul ve yüklensin

::: moniker range="vs-2017"

Uzantıları, Visual Studio 'daki [Visual Studio Market](https://marketplace.visualstudio.com) veya Uzantılar ve güncelleştirmeler iletişim kutusundan yükleyebilirsiniz.

Visual Studio içinden uzantı yüklemek için:

1. **Araçlar** > **Uzantılar ve güncelleştirmeler**'den yüklemek istediğiniz uzantıyı bulun. Uzantının adının veya adının bir kısmını biliyorsanız **arama** penceresinde arama yapabilirsiniz.

2. **Download** (İndir) seçeneğini belirleyin.

   Uzantı yüklenmek üzere zamanlandı. Uzantınız, Visual Studio 'nun tüm örnekleri kapatıldıktan sonra yüklenir.

Bağımlılıkları olan bir uzantıyı yüklemeye çalışırsanız, yükleyici bunların yüklenmiş olup olmadığını denetler. Bunlar yüklü değilse **Uzantılar ve güncelleştirmeler** iletişim kutusunda uzantıyı yükleyebilmeniz için önce yüklenmesi gereken bağımlılıklar listelenmiştir.

### <a name="install-without-using-the-extensions-and-updates-dialog-box"></a>Uzantılar ve güncelleştirmeler iletişim kutusunu kullanmadan yükler

*. Vsix* dosyalarında paketlenmiş uzantılar Visual Studio Market dışındaki konumlarda kullanılabilir olabilir. **Araçlar** > **Uzantılar ve güncelleştirmeler** iletişim kutusu bu dosyaları algılayamaz, ancak dosyayı çift tıklayarak veya dosyayı seçip **ENTER**tuşuna basarak bir *. vsix* dosyası yükleyebilirsiniz. Bundan sonra yalnızca yönergeleri izleyin. Uzantı yüklendiğinde, kullanabileceğiniz **Uzantılar ve güncelleştirmeler** etkinleştirmek, devre dışı bırakmak veya kaldırmak için iletişim kutusu.

> [!NOTE]
> - Visual Studio Market hem VSıX hem de MSI uzantılarını içerir. Uzantılar ve güncelleştirmeler iletişim kutusu, MSI tabanlı uzantıları etkinleştiremez veya devre dışı bırakamıyorum.
> - MSI tabanlı bir uzantı *. valtmanifest dosyası uzantısı* içeriyorsa, uzantı **Uzantılar ve güncelleştirmeler** iletişim kutusunda görünür.

::: moniker-end

::: moniker range=">=vs-2019"

Uzantıları, Visual Studio 'daki [Visual Studio Market](https://marketplace.visualstudio.com) veya Uzantıları Yönet iletişim kutusundan yükleyebilirsiniz.

Visual Studio içinden uzantı yüklemek için:

1. Uzantılardan **Uzantıları yönet** ** > ,** yüklemek istediğiniz uzantıyı bulun. (Adı veya uzantı adının bir kısmını biliyorsanız, içinde arama yapabilirsiniz **arama** penceresi.)

2. **Download** (İndir) seçeneğini belirleyin.

   Uzantı yüklenmek üzere zamanlandı. Uzantınız, Visual Studio 'nun tüm örnekleri kapatıldıktan sonra yüklenir.

Bağımlılıkları olan bir uzantıyı yüklemeye çalışırsanız, yükleyici bunların yüklenmiş olup olmadığını denetler. Yüklenmemişse, **Uzantıları Yönet** iletişim kutusu, uzantıyı yükleyebilmeniz için yüklenmesi gereken bağımlılıkları listeler.

### <a name="install-without-using-the-manage-extensions-dialog-box"></a>Uzantıları Yönet iletişim kutusunu kullanmadan yükler

*. Vsix* dosyalarında paketlenmiş uzantılar Visual Studio Market dışındaki konumlarda kullanılabilir olabilir. **Uzantılar** > **Uzantıları Yönet** iletişim kutusu bu dosyaları algılayamaz, ancak dosyayı çift tıklayarak veya dosyayı seçip **ENTER**tuşuna basarak bir *. vsix* dosyası yükleyebilirsiniz. Bundan sonra yalnızca yönergeleri izleyin. Uzantı yüklendiğinde, **Uzantıları Yönet** iletişim kutusunu etkinleştirmek, devre dışı bırakmak veya kaldırmak için kullanabilirsiniz.

> [!NOTE]
> - Visual Studio Market hem VSıX hem de MSI uzantılarını içerir. Uzantıları Yönet iletişim kutusu, MSI tabanlı uzantıları etkinleştiremez veya devre dışı bırakamıyorum.
> - MSI tabanlı bir uzantı *. valtmanifest dosyası uzantısı* içeriyorsa, uzantı **Uzantıları Yönet** iletişim kutusunda görünür.

::: moniker-end

## <a name="uninstall-or-disable-an-extension"></a>Uzantıyı kaldırma veya devre dışı bırakma

Bir uzantıyı kullanmayı bırakmak isterseniz devre dışı bırakabilir veya kaldırabilirsiniz. Bir uzantı devre dışı bırakıldığında yüklü kalır, ancak etkin değildir. Uzantı bulun ve tıklatın **kaldırma** veya **devre dışı**. Devre dışı bırakılmış bir uzantıyı kaldırmak için Visual Studio 'Yu yeniden başlatın.

> [!NOTE]
> VSıX uzantılarını devre dışı bırakabilirsiniz, ancak MSI kullanılarak yüklenen uzantılar kullanılamaz. MSI yüklenmiş uzantılar yalnızca kaldırılabilir.

## <a name="per-user-and-administrative-extensions"></a>Kullanıcı başına ve yönetim uzantıları

Çoğu uzantı Kullanıcı başına ve *%LocalAppData%\microsoft\visualstudio\\< Visual Studio sürümü\>\Extensions\\* klasörüne yüklenir. Birkaç uzantı yönetim uzantılarıdır ve *\<Visual Studio yükleme klasörü > \Common7\IDE\Extensions\\* klasörüne yüklenir.

Hata veya kötü amaçlı kod içerebilecek uzantıları karşı sisteminizi korumak için yalnızca Visual Studio normal kullanıcı izinleriyle çalıştırıldığında yüklemek için kullanıcı başına uzantılar kısıtlayabilirsiniz. Bu, Visual Studio yükseltilmiş izinlerle çalıştırıldığında kullanıcı başına uzantıların devre dışı bırakıldığı anlamına gelir.

Kullanıcı başına uzantıların ne zaman yükleneceğini kısıtlamak için:

1. Uzantılar Seçenekler sayfasını açın (**araçlar** > **seçenekler** > **ortam** > **uzantıları**).

2. **Yönetici olarak çalışırken Kullanıcı Uzantıları başına yükle** onay kutusunu temizleyin.

3. Visual Studio'yu yeniden başlatın.

## <a name="automatic-extension-updates"></a>Otomatik uzantı güncelleştirmeleri

Visual Studio Market yeni bir sürüm kullanılabilir olduğunda uzantılar otomatik olarak güncelleştirilir. Uzantının yeni sürümü algılanır ve arka planda yüklenir. Visual Studio 'Yu bir sonraki açışınızda, uzantının yeni sürümü çalışıyor olur.

Otomatik güncelleştirmeleri devre dışı bırakmak istiyorsanız, tüm uzantılar için veya yalnızca belirli Uzantılar için özelliği devre dışı bırakabilirsiniz.

::: moniker range="vs-2017"

- Tüm uzantılar için otomatik güncelleştirmeleri devre dışı bırakmak için **araçlar** > **Uzantılar ve güncelleştirmeler** iletişim kutusundaki **uzantılarınızı ve güncelleştirme ayarlarını değiştirin** bağlantısını seçin. **Seçenekler** iletişim kutusunda, **uzantıları otomatik güncelleştir**onay kutusunun işaretini kaldırın.

- Belirli bir uzantı için Otomatik Güncelleştirmeler devre dışı bırakmak için işareti kaldırın **bu uzantıyı otomatik olarak güncelleştir** seçeneği uzantının ayrıntıları bölmesinde sağ alt tarafında **Uzantılar ve güncelleştirmeler** iletişim.

::: moniker-end

::: moniker range=">=vs-2019"

- Tüm uzantılar için otomatik güncelleştirmeleri devre dışı bırakmak üzere **uzantılar > uzantıları** **Yönet** iletişim kutusunda uzantılar **için ayarları değiştir** bağlantısını seçin. **Seçenekler** iletişim kutusunda, **uzantıları otomatik güncelleştir**onay kutusunun işaretini kaldırın.

- Belirli bir uzantının otomatik güncelleştirmelerini devre dışı bırakmak için, **Uzantıları Yönet** iletişim kutusunun sağ tarafındaki uzantının Ayrıntılar bölmesinde **Bu uzantıyı otomatik olarak güncelleştir** seçeneğinin işaretini kaldırın.

::: moniker-end

## <a name="crash-and-unresponsiveness-notifications"></a>Kilitlenme ve yanıt verme bildirimleri

Visual Studio, bir uzantının önceki bir oturum sırasında kilitlenmeyle ilgili olduğunu şüpheleniyorsa sizi bilgilendirir. Visual Studio kilitleniyor, özel durum yığını depolar. Visual Studio başlatılır, sonraki açışınızda yaprak ile başlayan ve temel çalışma yığını inceler. Visual Studio çerçeve uzantı yüklü ve etkin bir parçası olan bir modüle ait olduğunu belirlerse, bir bildirim gösterilir.

Visual Studio, bir uzantının ne kadar şüpheleniyorsa, Kullanıcı arabiriminin yanıt vermemesine neden olduğunu da bildirir.

Bu bildirimleri gösterilirken, bildirim Yoksay veya aşağıdaki eylemlerden birini gerçekleştirin:

::: moniker range="vs-2017"

- Seçin **bu uzantıyı devre dışı**. Visual Studio, uzantıyı devre dışı bırakır ve devre dışı bırakma etkinleşmesi için sisteminizi yeniden başlatması gerek olup olmadığını bildirir. İsterseniz, uzantıyı **araçlar** > **Uzantılar ve güncelleştirmeler** iletişim kutusunda yeniden etkinleştirebilirsiniz.

::: moniker-end

::: moniker range=">=vs-2019"

- Seçin **bu uzantıyı devre dışı**. Visual Studio, uzantıyı devre dışı bırakır ve devre dışı bırakma etkinleşmesi için sisteminizi yeniden başlatması gerek olup olmadığını bildirir. İsterseniz uzantıyı **uzantılar** > uzantıları **Yönet** iletişim kutusunda yeniden etkinleştirebilirsiniz.

::: moniker-end

- Seçin **bu iletiyi bir daha gösterme**.

  - Bildirim önceki bir oturumdaki kilitlenmeyle ilgiliyse, bu uzantıyla ilişkili bir kilitlenme oluştuğunda Visual Studio artık bir bildirim göstermez. Bu uzantı veya kilitlenme veya diğer uzantıları ile ilişkilendirilebilen yanıt vermeyi durdurma sorununa yanıt vermeyi durdurma sorununa ilişkilendirilebilir zaman visual Studio hala bildirimleri göster.
  - Bildirim yanıt verme ile ilgiliyse, bu uzantı yanıt verme ile ilişkilendirildiğinde tümleşik geliştirme ortamı (IDE) artık bildirim göstermez. Visual Studio, bu uzantı için kilitlenmeyle ilgili bildirimleri ve diğer uzantılara yönelik kilitlenme ve yanıt verme ile ilgili bildirimleri göstermeye devam eder.

- Bu sayfaya gitmek için **daha fazla bilgi** ' yi seçin.

- Seçin **X** bildirimi kapatmak için bildirim sonunda düğmesi. Gelecekteki bir kilitlenme veya kullanıcı Arabirimi yanıt vermeyi durdurma sorununa ile ilişkilendiriliyor uzantısı örneklerinin yeni bir bildirim görüntülenir.

> [!NOTE]
> Bir kullanıcı Arabirimi yanıt vermeyi durdurma sorununa veya kilitlenme bildirimi yalnızca bir uzantının modüllerinin yığında UI yanıt vermiyor veya kilitlenme ortaya çıktığında anlamına gelir. Bu mutlaka uzantısı sorunlu olduğunu gelmez. Uzantı, Visual Studio 'nun parçası olan kod olarak adlandırılır, bu da yanıt vermeyen Kullanıcı arabirimi veya kilitlenme ile sonuçlanır. Ancak, bildirim yine de kullanıcı Arabirimi yanıt vermeyi durdurma sorununa veya kilitlenme sonuçlanan uzantı sizin için önemli değilse yararlı olabilir. Bu durumda, uzantıyı devre dışı kullanıcı Arabirimi yanıt vermeyi durdurma sorununa veya kilitlenme gelecekte üretkenliğinizi etkilemeden önler.

## <a name="samples"></a>Örnekler

Çevrimiçi bir örneği yüklediğinizde, çözüm iki konumda depolanır:

- Çalışma kopyası, projeyi oluştururken belirttiğiniz konumda depolanır.

- Ayrı bir ana kopya bilgisayarınızda depolanır.

::: moniker range="vs-2017"

Bu örneklerle ilgili görevleri gerçekleştirmek için **araçlar** > **Uzantılar ve güncelleştirmeler** iletişim kutusunu kullanabilirsiniz:

::: moniker-end

::: moniker range=">=vs-2019"

**Uzantılar >** **Yönet** iletişim kutusunu kullanarak bu örneklerle ilgili görevleri gerçekleştirebilirsiniz:

::: moniker-end

- Yüklediğiniz örneklerin ana kopyalarını listeleyin.

- Bir örneğin ana kopyasını devre dışı bırakın veya kaldırın.

- Örnek Paketleri (bir teknoloji veya özellik ile ilgili örnek koleksiyonları) yükleyin.

- Tek tek çevrimiçi örnekleri yükleyin.

- Yüklü örnekler için kaynak kodu değişiklikleri yayımlandığında güncelleştirme bildirimlerini görüntüleyin.

- Bir güncelleştirme bildirimi olduğunda yüklü bir örneğin ana kopyasını güncelleştirin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Market](https://marketplace.visualstudio.com)
- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)
