---
title: Uzantıları bulma ve yükleme
description: Uzantılar hakkında bilgi Visual Studio ve ihtiyacınız olan denetimlere, örneklere, şablonlara, araçlara ve diğer bileşenlere sahip olmak için bunları nasıl yönetebilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 11/23/2021
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
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 6aaf9a49d7f12014936c6de4dacbbdda7d6c0dd7
ms.sourcegitcommit: a1c18c491e310b00a43e76a911f778e643cd8f8d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "132995575"
---
# <a name="manage-extensions-for-visual-studio"></a>Visual Studio için uzantıları yönetme

Uzantılar, yeni veya geliştirilmiş özellikler Visual Studio kod paketleridir. Uzantılar denetimler, örnekler, şablonlar, araçlar veya [IntelliCode](https://marketplace.visualstudio.com/items?itemName=VisualStudioExptTeam.VSIntelliCode)gibi Visual Studio işlevler Live Share [Visual Studio](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsls-vs) olabilir.

::: moniker range="vs-2022"

Uygulama uzantıları oluşturma hakkında Visual Studio için bkz. [Visual Studio SDK.](../extensibility/visual-studio-sdk.md) Uzantıları kullanma hakkında daha fazla bilgi için Market'te tek [Visual Studio bakın.](https://marketplace.visualstudio.com) Uzantıları bulma hakkında daha fazla bilgi için [2022'de En](https://devblogs.microsoft.com/visualstudio/where-are-my-favorite-extensions-in-visual-studio-2022/) Visual Studio Uzantılarım Nerede? blog gönderisi'ne bakın.

::: moniker-end

::: moniker range="<=vs-2019"

Uygulama uzantıları oluşturma hakkında Visual Studio için bkz. [Visual Studio SDK.](../extensibility/visual-studio-sdk.md) Uzantıları kullanma hakkında daha fazla bilgi için Market'te tek [Visual Studio bakın.](https://marketplace.visualstudio.com)

::: moniker-end

::: moniker range="vs-2017"

## <a name="extensions-and-updates-dialog-box"></a>Uzantılar ve Güncelleştirmeler iletişim kutusu

Uzantıları yüklemek **ve yönetmek için** Uzantılar ve Güncelleştirmeler iletişim Visual Studio kullanın. Uzantılar ve **Güncelleştirmeler iletişim kutusunu açmak** için Araçlar   >  **Uzantılar ve Güncelleştirmeler'i** seçin veya **uzantılar Hızlı Başlat** yazın. 

![Visual Studio'de uzantılar penceresi](media/finding-using-visual-studio-extensions/extensions-and-updates.png)

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="manage-extensions-dialog-box"></a>Uzantıları Yönet iletişim kutusu

Uzantıları **yönetmek ve yüklemek** için Uzantıları Yönet iletişim Visual Studio kullanın. Uzantıları Yönet **iletişim kutusunu açmak için** Uzantıları **Yönet'i**  >  **seçin.** Veya arama **kutusuna Uzantılar** yazın ve Uzantıları **Yönet'i seçin.**

:::image type="content" source="media/finding-using-visual-studio-extensions/vs-2022/extensions-and-updates.png" alt-text="Visual Studio'da Uzantıları Yönet penceresinin ekran görüntüsü":::

::: moniker-end

Sol bölmede uzantılar yüklü olanlara, Visual Studio Market'te (**Çevrimiçi**) bulunanlara ve güncelleştirmeleri bulunanlara göre kategorilere ayrılmıştır. **Gezici** Uzantı Yöneticisi, herhangi bir Visual Studio makineye veya uygulama örneğine yüklemiş olduğunu tüm uygulama uzantılarının listesini Visual Studio. Sık kullanılan uzantılarınızı daha kolay bulmanızı sağlar.

## <a name="find-and-install-extensions"></a>Uzantıları bulma ve yükleme

::: moniker range="vs-2017"

Uzantıları Market'Visual Studio [veya uzantılar](https://marketplace.visualstudio.com) ve Güncelleştirmeler iletişim kutusundan Visual Studio.

Uzantıları uygulamanın içinde yüklemek Visual Studio:

1. Araç   >  **Uzantıları ve Güncelleştirmeler'den** yüklemek istediğiniz uzantıyı bulun. Uzantının adını veya bir kısmını biliyorsanız Arama penceresinde arama **yapabilirsiniz.**

2. **İndir**'i seçin.

   Uzantı yüklenmek üzere zamanlandı. Uzantınız, uygulamanın tüm örnekleri Visual Studio yüklenir.

Bağımlılıkları olan bir uzantıyı yüklemeye çalışırsanız, yükleyici bunların yüklenmiş olup olmadığını denetler. Yüklü değilse, **Uzantılar ve** Güncelleştirmeler iletişim kutusunda uzantıyı yükleymeden önce yüklü olması gereken bağımlılıklar liste olur.

### <a name="install-without-using-the-extensions-and-updates-dialog-box"></a>Uzantılar ve Güncelleştirmeler iletişim kutusunu kullanmadan yükleme

*.vsix* dosyalarında paketlenmiş uzantılar Market'in dışında Visual Studio kullanılabilir. Araçlar **Uzantıları** ve Güncelleştirmeler iletişim kutusu bu dosyaları algılayamasa da, dosyaya çift tıklayarak veya dosyayı seçerek ve Enter tuşuna basarak  >   bir *.vsix* dosyası **yükleyebilirsiniz.** Bundan sonra yönergeleri izlemelisiniz. Uzantı yüklenirken, uzantıyı etkinleştirmek, devre dışı **bırakmak** veya kaldırmak için Uzantılar ve Güncelleştirmeler iletişim kutusunu kullanabilirsiniz.

> [!NOTE]
> - Visual Studio Market hem VSIX hem de MSI uzantılarını içerir. Uzantılar ve Güncelleştirmeler iletişim kutusu MSI tabanlı uzantıları etkinleştirene veya devre dışı bırakamayabilirsiniz.
> - MSI tabanlı bir uzantı *bir extension.vsixmanifest* dosyası içerirse uzantı Uzantılar ve **Güncelleştirmeler iletişim kutusunda** görünür.

::: moniker-end

::: moniker range=">=vs-2019"

Uzantıları Market'Visual Studio [veya](https://marketplace.visualstudio.com) Visual Studio.Market'te yükleyebilirsiniz.

Uzantıları uygulamanın içinde yüklemek Visual Studio:

1. Uzantıları   >  **Yönet'den** yüklemek istediğiniz uzantıyı bulun. (Uzantının adını veya bir kısmını biliyorsanız Arama penceresinde arama **yapabilirsiniz.)**

2. **İndir**'i seçin.

   Uzantı yüklenmek üzere zamanlandı. Uzantınız, uygulamanın tüm örnekleri Visual Studio yüklenir.

Bağımlılıkları olan bir uzantıyı yüklemeye çalışırsanız, yükleyici bunların yüklenmiş olup olmadığını denetler. Bunlar yüklü değilse, Uzantıları Yönet **iletişim** kutusunda uzantıyı yükleymeden önce yüklü olması gereken bağımlılıklar liste olur.

### <a name="install-without-using-the-manage-extensions-dialog-box"></a>Uzantıları Yönet iletişim kutusunu kullanmadan yükleme

*.vsix* dosyalarında paketlenmiş uzantılar Market'in dışında Visual Studio kullanılabilir. Uzantıları **Yönet** iletişim kutusu bu dosyaları algılayamasa da, dosyaya çift tıklayarak veya dosyayı seçerek ve Enter tuşuna basarak  >   bir *.vsix* dosyası **yükleyebilirsiniz.** Bundan sonra yönergeleri izlemelisiniz. Uzantı yüklenirken, uzantıyı etkinleştirmek,  devre dışı bırakmak veya kaldırmak için Uzantıları Yönet iletişim kutusunu kullanabilirsiniz.

> [!NOTE]
> - Visual Studio Market hem VSIX hem de MSI uzantılarını içerir. Uzantıları Yönet iletişim kutusu MSI tabanlı uzantıları etkinleştirene veya devre dışı bırakamayabilirsiniz.
> - MSI tabanlı bir uzantı *extension.vsixmanifest* dosyası içerirse uzantı, Uzantıları Yönet **iletişim kutusunda** görünür.

::: moniker-end

## <a name="uninstall-or-disable-an-extension"></a>Uzantıyı kaldırma veya devre dışı bırakma

Bir uzantıyı kullanmayı bırakmak isterseniz devre dışı bırakabilir veya kaldırabilirsiniz. Bir uzantı devre dışı bırakıldığında yüklü kalır, ancak etkin değildir. Uzantıyı bulun ve Kaldır veya Devre **Dışı Bırak'a** **tıklayın.** Devre Visual Studio uzantıyı kaldırmayı yeniden başlatın.

> [!NOTE]
> VSIX uzantılarını devre dışı güncelleştirmeyi, ancak MSI kullanılarak yüklenmiş uzantıları devre dışı güncelleştirmeyiz. MSI yüklü uzantılar yalnızca kaldırabilirsiniz.

## <a name="per-user-and-administrative-extensions"></a>Kullanıcı başına ve yönetim uzantıları

Uzantıların çoğu kullanıcı başınadır ve *%LocalAppData%\Microsoft\VisualStudio \\<Visual Studio \> \Extensions klasörüne \\* yüklenir. Birkaç uzantı yönetici uzantılarıdır ve *\<Visual Studio installation folder> \Common7\IDE\Extensions klasörüne \\* yüklenir.

Sisteminizi hata veya kötü amaçlı kod içeren uzantılara karşı korumak için, kullanıcı başına uzantıların yalnızca normal kullanıcı izinleriyle Visual Studio yüklerini kısıtabilirsiniz. Bu, kullanıcı başına uzantıların yükseltilmiş izinlerle Visual Studio devre dışı bırakılacakları anlamına gelir.

Kullanıcı başına uzantıların yüklenme zamanlarını kısıtlamak için:

1. Uzantı seçenekleri sayfasını açın( Araçlar  >  **Seçenekler**  >  **Ortam**  >  **Uzantıları**).

2. Yönetici olarak **çalışan kullanıcı başına yükle onay kutusunun işaretini** kaldırın.

3. Visual Studio’yu yeniden başlatın.

## <a name="automatic-extension-updates"></a>Otomatik uzantı güncelleştirmeleri

Market'te yeni bir sürüm kullanılabilir olduğunda uzantılar Visual Studio güncelleştirilir. Uzantının yeni sürümü algılanır ve arka planda yüklenir. Bir sonraki Visual Studio, uzantının yeni sürümü çalışıyor olur.

Otomatik güncelleştirmeleri devre dışı bırakmak isterseniz özelliği tüm uzantılar veya yalnızca belirli uzantılar için devre dışı abilirsiniz.

::: moniker range="vs-2017"

- Tüm uzantılarda otomatik güncelleştirmeleri devre  dışı bırakmak için Araçlar Uzantıları ve Güncelleştirmeler iletişim kutusundaki **Uzantı** ve Güncelleştirme ayarlarınızı  >  **değiştirin** bağlantısını seçin. Seçenekler iletişim **kutusunda Uzantıları** otomatik olarak güncelleştir **seçeneğinin işaretini kaldırın.**

- Belirli bir uzantı için otomatik güncelleştirmeleri  devre dışı bırakmak için Uzantılar ve Güncelleştirmeler iletişim kutusunun sağ tarafındaki Uzantı ayrıntıları bölmesinde Bu uzantıyı otomatik olarak güncelleştir **seçeneğinin işaretini** kaldırın.

::: moniker-end

::: moniker range=">=vs-2019"

- Tüm uzantılarda otomatik güncelleştirmeleri devre  dışı bırakmak için Uzantıları Yönet iletişim kutusundaki **Uzantılar için ayarlarınızı**  >  **değiştirin** bağlantısını seçin. Seçenekler iletişim **kutusunda Uzantıları** otomatik olarak güncelleştir **seçeneğinin işaretini kaldırın.**

- Belirli bir uzantı için otomatik güncelleştirmeleri  devre dışı bırakmak için Uzantıları Yönet iletişim kutusunun sağ tarafındaki Uzantının ayrıntılar bölmesinde Bu uzantıyı otomatik olarak güncelleştir **seçeneğinin işaretini** kaldırın.

::: moniker-end

## <a name="crash-and-unresponsiveness-notifications"></a>Kilitlenme ve yanıt vermemeye başladı bildirimleri

Visual Studio önceki oturumda bir uzantının kilitlenmeye dahil olduğunu doğrularsa size bilgi sağlar. Özel Visual Studio kilitleniyorsa, özel durum yığınını depolar. Sonraki Visual Studio, yaprakla başlayarak ve temele doğru çalışarak yığını inceler. Bu Visual Studio çerçevenin yüklü ve etkinleştirilmiş bir uzantının parçası olan modüle ait olduğunu belirlerse bir bildirim gösterir.

Visual Studio, bir uzantının kullanıcı arabiriminin yanıt vermemeye neden olduğunu varsa da size bilgi sağlar.

Bu bildirimler gösterildiğinde bildirimi yoksayabilirsiniz veya aşağıdaki eylemlerden birini gerçekleştirin:

::: moniker range="vs-2017"

- Bu **uzantıyı devre dışı bırak'ı seçin.** Visual Studio uzantıyı devre dışı bırakarak devre dışı bırakmanın etkili olması için sisteminizi yeniden başlatmanız gerekip gerekip gerek olmadığını size sağlar. Sınıyorsanız Araç Uzantıları ve **Güncelleştirmeler** iletişim  >  **kutusunda** uzantıyı yeniden etkinleştirebilirsiniz.

::: moniker-end

::: moniker range=">=vs-2019"

- Bu **uzantıyı devre dışı bırak'ı seçin.** Visual Studio uzantıyı devre dışı bırakarak devre dışı bırakmanın etkili olması için sisteminizi yeniden başlatmanız gerekip gerekip gerek olmadığını size sağlar. Uzantıyı yeniden etkinleştirmek için uzantıları **Uzantıları Yönet** iletişim kutusunda  >   kullanabilirsiniz.

::: moniker-end

- Bu **iletiyi bir daha asla gösterme'yi seçin.**

  - Bildirim önceki oturumda bir kilitlenmeyle ilgili Visual Studio uzantıyla ilişkilendirilmiş bir kilitlenme oluştuğunda artık bildirim görüntülemeyecektir. Visual Studio yanıt vermiyorluk bu uzantıyla ilişkilendirilene veya diğer uzantılarla ilişkilendirilen kilitlenmeler veya yanıt vermemeye yönelik bildirimler göstermeye devam ediyor.
  - Bildirim yanıt verme ile ilgiliyse, bu uzantı yanıt verme ile ilişkilendirildiğinde tümleşik geliştirme ortamı (IDE) artık bildirim göstermez. Visual Studio, bu uzantı için kilitlenmeyle ilgili bildirimleri ve diğer uzantılara yönelik kilitlenme ve yanıt verme ile ilgili bildirimleri göstermeye devam edecektir.

- Bu sayfaya gitmek için **daha fazla bilgi** ' yi seçin.

- Bildirimi kapatmak için bildirimin sonundaki **X** düğmesini seçin. Uzantının kilitlenme veya Kullanıcı Arabirimi yanıt verme ile ilişkilendirilmesi gelecekteki örnekleri için yeni bir bildirim görüntülenir.

> [!NOTE]
> Kullanıcı Arabirimi yanıt verme veya kilitlenme bildirimi, Kullanıcı Arabirimi yanıt vermediğinde veya kilitlenme oluştuğunda yalnızca uzantının modüllerinde bir yığının bulunduğu anlamına gelir. Uzantının kendisinin kendisi olduğu anlamına gelmez. uzantının Visual Studio parçası olan kod olarak adlandırılmasından dolayı, bu da yanıt vermeyen kullanıcı arabirimine veya çökmeye neden olabilir. Ancak, Kullanıcı Arabirimi yanıt verme veya kilitlenme için yol gösteren uzantının sizin için önemli olmadığı durumlarda bildirim yine de yararlı olabilir. Bu durumda, uzantının devre dışı bırakılması, üretkenliğinizi etkilemeden UI 'nin yanıt verme hızını veya ileride çökmeyi önler.

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
