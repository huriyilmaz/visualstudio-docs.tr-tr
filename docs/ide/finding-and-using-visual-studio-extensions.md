---
title: Uzantıları bul ve yüklensin
description: Visual Studio 'daki Uzantılar ve bunları yönetme hakkında bilgi edinin ve bu sayede denetimleri, örnekleri, şablonları, araçları ve ihtiyacınız olan diğer bileşenlere sahip olursunuz.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bb088954833f42e35de6c8316e5553d0f9e3fc68
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945597"
---
# <a name="manage-extensions-for-visual-studio"></a>Visual Studio için uzantıları yönetme

Uzantılar, Visual Studio içinde çalışan ve yeni veya geliştirilmiş özellikler sağlayan kod paketlerdir. Uzantılar, Visual Studio 'ya işlev ekleyen denetimler, örnekler, şablonlar, araçlar veya başka bileşenler (örneğin, [live share](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsls-vs) veya [Visual Studio ıntellicode](https://marketplace.visualstudio.com/items?itemName=VisualStudioExptTeam.VSIntelliCode)) olabilir.

Visual Studio uzantıları oluşturma hakkında daha fazla bilgi için bkz. [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md). Uzantıları kullanma hakkında daha fazla bilgi için, [Visual Studio Market](https://marketplace.visualstudio.com)tek tek uzantı sayfasına bakın.

::: moniker range="vs-2017"

## <a name="extensions-and-updates-dialog-box"></a>Uzantılar ve güncelleştirmeler iletişim kutusu

Visual Studio uzantılarını yüklemek ve yönetmek için **Uzantılar ve güncelleştirmeler** iletişim kutusunu kullanın. **Uzantılar ve güncelleştirmeler** iletişim kutusunu açmak için **Araçlar**  >  **Uzantılar ve güncelleştirmeler**' i seçin veya **Hızlı Başlat** arama kutusuna **Uzantılar** yazın.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="manage-extensions-dialog-box"></a>Uzantıları Yönet iletişim kutusu

Visual Studio uzantılarını yüklemek ve yönetmek için **Uzantıları Yönet** iletişim kutusunu kullanın. **Uzantıları Yönet** iletişim kutusunu açmak için **Uzantılar**  >  **Yönet uzantılar**' ı seçin. Ya da, arama kutusuna **Uzantılar** yazın ve **Uzantıları Yönet**' i seçin.

::: moniker-end

![Visual Studio 'da uzantılar penceresi](media/finding-using-visual-studio-extensions/extensions-and-updates.png)

Sol taraftaki bölme, yüklenmiş olanlar, Visual Studio Market (**çevrimiçi**) ve güncelleştirmeleri olan güncelleştirmeler tarafından kategorilere ayırır. **Dolaşım uzantısı Yöneticisi** , Visual Studio 'nun herhangi bir makinesinde veya örneğinde yüklü olan tüm Visual Studio uzantılarının bir listesini tutar. En sevdiğiniz uzantıları daha kolay bir şekilde bulmanıza olanak sağlayacak şekilde tasarlanmıştır.

## <a name="find-and-install-extensions"></a>Uzantıları bul ve yüklensin

::: moniker range="vs-2017"

Uzantıları, Visual Studio 'daki [Visual Studio Market](https://marketplace.visualstudio.com) veya Uzantılar ve güncelleştirmeler iletişim kutusundan yükleyebilirsiniz.

Visual Studio içinden uzantı yüklemek için:

1. **Araçlar**  >  **uzantılarından ve güncelleştirmelerden**, yüklemek istediğiniz uzantıyı bulun. Uzantının adının veya adının bir kısmını biliyorsanız **arama** penceresinde arama yapabilirsiniz.

2. **İndir**'i seçin.

   Uzantı yüklenmek üzere zamanlandı. Uzantınız, Visual Studio 'nun tüm örnekleri kapatıldıktan sonra yüklenir.

Bağımlılıkları olan bir uzantıyı yüklemeye çalışırsanız, yükleyici bunların yüklenmiş olup olmadığını denetler. Yüklü değilse, **Uzantılar ve güncelleştirmeler** iletişim kutusu, uzantıyı yükleyebilmeniz için yüklenmesi gereken bağımlılıkları listeler.

### <a name="install-without-using-the-extensions-and-updates-dialog-box"></a>Uzantılar ve güncelleştirmeler iletişim kutusunu kullanmadan yükler

*. Vsix* dosyalarında paketlenmiş uzantılar Visual Studio Market dışındaki konumlarda kullanılabilir olabilir. **Araçlar**  >  **uzantıları ve güncelleştirmeler** iletişim kutusu bu dosyaları algılayamaz, ancak dosyayı çift tıklayarak veya dosyayı seçip **ENTER** tuşuna basarak bir *. vsix* dosyası yükleyebilirsiniz. Bundan sonra yönergeleri izlemeniz yeterlidir. Uzantı yüklendiğinde, uzantıyı etkinleştirmek, devre dışı bırakmak veya kaldırmak için **Uzantılar ve güncelleştirmeler** iletişim kutusunu kullanabilirsiniz.

> [!NOTE]
> - Visual Studio Market hem VSıX hem de MSI uzantılarını içerir. Uzantılar ve güncelleştirmeler iletişim kutusu, MSI tabanlı uzantıları etkinleştiremez veya devre dışı bırakamıyorum.
> - MSI tabanlı bir uzantı *. valtmanifest dosyası uzantısı* içeriyorsa, uzantı **Uzantılar ve güncelleştirmeler** iletişim kutusunda görünür.

::: moniker-end

::: moniker range=">=vs-2019"

Uzantıları, Visual Studio 'daki [Visual Studio Market](https://marketplace.visualstudio.com) veya Uzantıları Yönet iletişim kutusundan yükleyebilirsiniz.

Visual Studio içinden uzantı yüklemek için:

1. Uzantılardan   >  **Uzantıları Yönet**' den yüklemek istediğiniz uzantıyı bulun. (Uzantının adının adını veya parçasını biliyorsanız, **arama** penceresinde arama yapabilirsiniz.)

2. **İndir**'i seçin.

   Uzantı yüklenmek üzere zamanlandı. Uzantınız, Visual Studio 'nun tüm örnekleri kapatıldıktan sonra yüklenir.

Bağımlılıkları olan bir uzantıyı yüklemeye çalışırsanız, yükleyici bunların yüklenmiş olup olmadığını denetler. Yüklenmemişse, **Uzantıları Yönet** iletişim kutusu, uzantıyı yükleyebilmeniz için yüklenmesi gereken bağımlılıkları listeler.

### <a name="install-without-using-the-manage-extensions-dialog-box"></a>Uzantıları Yönet iletişim kutusunu kullanmadan yükler

*. Vsix* dosyalarında paketlenmiş uzantılar Visual Studio Market dışındaki konumlarda kullanılabilir olabilir. Uzantıları   >  **Yönet** iletişim kutusu bu dosyaları algılayamaz, ancak dosyayı çift tıklayarak veya dosyayı seçip **ENTER** tuşuna basarak bir *. vsix* dosyası yükleyebilirsiniz. Bundan sonra yönergeleri izlemeniz yeterlidir. Uzantı yüklendiğinde, **Uzantıları Yönet** iletişim kutusunu etkinleştirmek, devre dışı bırakmak veya kaldırmak için kullanabilirsiniz.

> [!NOTE]
> - Visual Studio Market hem VSıX hem de MSI uzantılarını içerir. Uzantıları Yönet iletişim kutusu, MSI tabanlı uzantıları etkinleştiremez veya devre dışı bırakamıyorum.
> - MSI tabanlı bir uzantı *. valtmanifest dosyası uzantısı* içeriyorsa, uzantı **Uzantıları Yönet** iletişim kutusunda görünür.

::: moniker-end

## <a name="uninstall-or-disable-an-extension"></a>Uzantıyı kaldırma veya devre dışı bırakma

Bir uzantıyı kullanmayı bırakmak isterseniz devre dışı bırakabilir veya kaldırabilirsiniz. Bir uzantı devre dışı bırakıldığında yüklü kalır, ancak etkin değildir. Uzantıyı bulun ve **Kaldır** veya **devre dışı bırak**' a tıklayın. Devre dışı bırakılmış bir uzantıyı kaldırmak için Visual Studio 'Yu yeniden başlatın.

> [!NOTE]
> VSıX uzantılarını devre dışı bırakabilirsiniz, ancak MSI kullanılarak yüklenen uzantılar kullanılamaz. MSI yüklenmiş uzantılar yalnızca kaldırılabilir.

## <a name="per-user-and-administrative-extensions"></a>Kullanıcı başına ve yönetim uzantıları

Çoğu uzantı Kullanıcı başına ve *%LocalAppData%\microsoft\visualstudio \\<Visual Studio Sürüm \> \ Extensions \\* klasörüne yüklenir. Birkaç uzantı yönetim uzantılarıdır ve *\<Visual Studio installation folder> \Common7\IDE\Extensions \\* klasörüne yüklenir.

Sisteminizi hatalar veya kötü amaçlı kod içerebilen uzantılara karşı korumak için, Kullanıcı başına uzantıları yalnızca Visual Studio normal Kullanıcı izinleriyle çalıştırıldığında yüklenecek şekilde kısıtlayabilirsiniz. Bu, Visual Studio yükseltilmiş izinlerle çalıştırıldığında kullanıcı başına uzantıların devre dışı bırakıldığı anlamına gelir.

Kullanıcı başına uzantıların ne zaman yükleneceğini kısıtlamak için:

1. Uzantılar Seçenekler sayfasını açın (**Araçlar**  >  **Seçenekler**  >  **ortam**  >  **uzantıları**).

2. **Yönetici olarak çalışırken Kullanıcı Uzantıları başına yükle** onay kutusunu temizleyin.

3. Visual Studio’yu yeniden başlatın.

## <a name="automatic-extension-updates"></a>Otomatik uzantı güncelleştirmeleri

Visual Studio Market yeni bir sürüm kullanılabilir olduğunda uzantılar otomatik olarak güncelleştirilir. Uzantının yeni sürümü algılanır ve arka planda yüklenir. Visual Studio 'Yu bir sonraki açışınızda, uzantının yeni sürümü çalışıyor olur.

Otomatik güncelleştirmeleri devre dışı bırakmak istiyorsanız, tüm uzantılar için veya yalnızca belirli Uzantılar için özelliği devre dışı bırakabilirsiniz.

::: moniker range="vs-2017"

- Tüm uzantılar için otomatik güncelleştirmeleri devre dışı bırakmak için, **Araçlar** Uzantılar ve güncelleştirmeler iletişim kutusunda **uzantılarınızı ve güncelleştirme ayarlarını değiştirin** bağlantısını seçin  >   . **Seçenekler** iletişim kutusunda, **uzantıları otomatik güncelleştir** onay kutusunun işaretini kaldırın.

- Belirli bir uzantının otomatik güncelleştirmelerini devre dışı bırakmak için **Uzantılar ve güncelleştirmeler** iletişim kutusunun sağ tarafındaki uzantının Ayrıntılar bölmesinde **Bu uzantıyı otomatik olarak güncelleştir** seçeneğinin işaretini kaldırın.

::: moniker-end

::: moniker range=">=vs-2019"

- Tüm uzantılar için otomatik güncelleştirmeleri devre dışı bırakmak **üzere uzantılar** Uzantıları Yönet iletişim kutusunda **Uzantılar için ayarlarınızı değiştirin** bağlantısı ' nı seçin  >   . **Seçenekler** iletişim kutusunda, **uzantıları otomatik güncelleştir** onay kutusunun işaretini kaldırın.

- Belirli bir uzantının otomatik güncelleştirmelerini devre dışı bırakmak için, **Uzantıları Yönet** iletişim kutusunun sağ tarafındaki uzantının Ayrıntılar bölmesinde **Bu uzantıyı otomatik olarak güncelleştir** seçeneğinin işaretini kaldırın.

::: moniker-end

## <a name="crash-and-unresponsiveness-notifications"></a>Kilitlenme ve yanıt verme bildirimleri

Visual Studio, bir uzantının önceki bir oturum sırasında kilitlenmeyle ilgili olduğunu şüpheleniyorsa sizi bilgilendirir. Visual Studio kilitlenirse, özel durum yığınını depolar. Visual Studio 'Nun bir sonraki başlatılmasında, yaprağı inceleyerek ve temel doğru çalışarak yığını inceler. Visual Studio, bir çerçevenin yüklü ve etkin bir uzantının parçası olan bir modüle ait olduğunu belirlerse, bir bildirim gösterir.

Visual Studio, bir uzantının ne kadar şüpheleniyorsa, Kullanıcı arabiriminin yanıt vermemesine neden olduğunu da bildirir.

Bu bildirimler gösterildiğinde, bildirimi yoksayabilirsiniz veya aşağıdaki eylemlerden birini gerçekleştirebilirsiniz:

::: moniker range="vs-2017"

- **Bu uzantıyı devre dışı bırak**' ı seçin. Visual Studio, uzantıyı devre dışı bırakır ve devre dışı bırakmanın etkili olması için sisteminizi yeniden başlatmanız gerekip gerekmediğini bilmenizi sağlar. İsterseniz, uzantıyı **Araçlar**  >  **Uzantılar ve güncelleştirmeler** iletişim kutusunda yeniden etkinleştirebilirsiniz.

::: moniker-end

::: moniker range=">=vs-2019"

- **Bu uzantıyı devre dışı bırak**' ı seçin. Visual Studio, uzantıyı devre dışı bırakır ve devre dışı bırakmanın etkili olması için sisteminizi yeniden başlatmanız gerekip gerekmediğini bilmenizi sağlar. İsterseniz **uzantıları**  >  **Yönet** iletişim kutusunda uzantıyı yeniden etkinleştirebilirsiniz.

::: moniker-end

- **Bu Iletiyi hiçbir daha gösterme** seçeneğini belirleyin.

  - Bildirim önceki bir oturumdaki kilitlenmeyle ilgiliyse, bu uzantıyla ilişkili bir kilitlenme oluştuğunda Visual Studio artık bir bildirim göstermez. Yanıt verme süresi bu uzantıyla ilişkilendirilemediği veya diğer uzantılarla ilişkilendirilebilen kilitlenmeler veya yanıt verme için, Visual Studio hala bildirim göstermeye devam eder.
  - Bildirim yanıt verme ile ilgiliyse, bu uzantı yanıt verme ile ilişkilendirildiğinde tümleşik geliştirme ortamı (IDE) artık bildirim göstermez. Visual Studio, bu uzantı için kilitlenmeyle ilgili bildirimleri ve diğer uzantılara yönelik kilitlenme ve yanıt verme ile ilgili bildirimleri göstermeye devam eder.

- Bu sayfaya gitmek için **daha fazla bilgi** ' yi seçin.

- Bildirimi kapatmak için bildirimin sonundaki **X** düğmesini seçin. Uzantının kilitlenme veya Kullanıcı Arabirimi yanıt verme ile ilişkilendirilmesi gelecekteki örnekleri için yeni bir bildirim görüntülenir.

> [!NOTE]
> Kullanıcı Arabirimi yanıt verme veya kilitlenme bildirimi, Kullanıcı Arabirimi yanıt vermediğinde veya kilitlenme oluştuğunda yalnızca uzantının modüllerinde bir yığının bulunduğu anlamına gelir. Uzantının kendisinin kendisi olduğu anlamına gelmez. Uzantı, Visual Studio 'nun parçası olan kod olarak adlandırılır, bu da yanıt vermeyen Kullanıcı arabirimi veya kilitlenme ile sonuçlanır. Ancak, Kullanıcı Arabirimi yanıt verme veya kilitlenme için yol gösteren uzantının sizin için önemli olmadığı durumlarda bildirim yine de yararlı olabilir. Bu durumda, uzantının devre dışı bırakılması, üretkenliğinizi etkilemeden UI 'nin yanıt verme hızını veya ileride çökmeyi önler.

## <a name="samples"></a>Örnekler

Çevrimiçi bir örneği yüklediğinizde, çözüm iki konumda depolanır:

- Çalışma kopyası, projeyi oluştururken belirttiğiniz konumda depolanır.

- Ayrı bir ana kopya bilgisayarınızda depolanır.

::: moniker range="vs-2017"

 > Bu örneklerle ilgili görevleri gerçekleştirmek için Araçlar **Uzantılar ve güncelleştirmeler** iletişim kutusunu kullanabilirsiniz:

::: moniker-end

::: moniker range=">=vs-2019"

 > Bu örneklerle ilgili görevleri gerçekleştirmek için uzantıları **Yönet** iletişim kutusunu kullanabilirsiniz:

::: moniker-end

- Yüklediğiniz örneklerin ana kopyalarını listeleyin.

- Bir örneğin ana kopyasını devre dışı bırakın veya kaldırın.

- Örnek Paketleri (bir teknoloji veya özellik ile ilgili örnek koleksiyonları) yükleyin.

- Tek tek çevrimiçi örnekleri yükleyin.

- Yüklü örnekler için kaynak kodu değişiklikleri yayımlandığında güncelleştirme bildirimlerini görüntüleyin.

- Bir güncelleştirme bildirimi olduğunda, yüklü bir örneğin ana kopyasını güncelleştirin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Market](https://marketplace.visualstudio.com)
- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)
