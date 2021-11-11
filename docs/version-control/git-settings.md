---
title: Visual Studio git ayarları
titleSuffix: ''
description: Visual Studio, tercihlerinizi yönetmek için. gitconfig 'de ayarla dosyalarını ve Git ayarlarını nasıl kullandığını öğrenin
ms.date: 06/08/2021
ms.topic: conceptual
author: Taysser-Gherfal
ms.author: tglee
ms.manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
monikerRange: '>=vs-2019'
ms.openlocfilehash: efe8498a770a6bcb6394ce435ce997922e0cc955
ms.sourcegitcommit: dc12d3d0ca2ec3601cb9de7c22e61ecf22c7c514
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2021
ms.locfileid: "132264131"
---
# <a name="git-settings-and-preferences-in-visual-studio"></a>Visual Studio git ayarları ve tercihleri

Visual Studio, ad ve e-posta adresiniz, tercih ettiğiniz fark ve birleştirme araçları ve daha fazlası gibi yaygın Git ayarlarını ve tercihlerini yapılandırabilir ve görüntüleyebilirsiniz. bu ayarlar ve tercihler **git genel Ayarlar** sayfasında (tüm depolarınız için geçerlidir) veya **git deposu Ayarlar** sayfasında (geçerli depo için geçerlidir) **seçenekler iletişim kutusunda** görüntülenebilir ve yapılandırılabilir.

İki tür ayar yapılandırabilirsiniz:

- [Git ayarları](#git-settings) -bu bölümdeki Ayarlar git yapılandırma dosyalarına kaydedilen git ayarlarına karşılık gelir. bu ayarlar Visual Studio görüntülenebilir ve değiştirilebilir, ancak Git yapılandırma dosyaları tarafından yönetilebilir.
- [Visual Studio ayarları](#visual-studio-settings) -bu bölümdeki ayarlar, Git ile ilgili ayarları ve Visual Studio tarafından yönetilen tercihleri yapılandırır.

## <a name="how-to-configure-settings"></a>Ayarları yapılandırma

1. Visual Studio git ayarlarını yapılandırmak için üst düzey Git menüsünden **Ayarlar** ' i seçin.

   :::image type="content" source="media/git-menu-settings.png" alt-text="Ayarlar komutuna bir belirtme çizgisi içeren Git menüsü.":::

2. genel düzeyi veya depo düzeyi ayarlarını görüntülemek ve yapılandırmak için **git genel Ayarlar** veya **git deposu Ayarlar** seçin.

   :::image type="content" source="media/source-control-settings.png" alt-text="Seçenekler iletişim kutusundaki gezinti bölmesi git ayarlarına bir belirtme çizgisi ile.":::

3. Bu makalenin aşağıdaki bölümlerinde açıklandığı gibi, birkaç ortak git ayarı yapılandırabilirsiniz. İstediğiniz ayarları yapılandırdıktan sonra, güncelleştirilmiş ayarları kaydetmek için **Tamam** ' ı seçin.

   :::image type="content" source="media/ok-button.png" alt-text="Seçenekler iletişim kutusunun görüntüleme alanı Tamam düğmesine bir belirtme çizgisi ile.":::

## <a name="git-settings"></a>Git ayarları

Ayrıca, en yaygın git yapılandırma ayarlarından bazılarını yapılandırabilir ve kontrol edebilirsiniz. Git yapılandırma dosyaları tarafından yönetilse de, Visual Studio aşağıdaki ayarları görüntüleyebilir ve değiştirebilirsiniz.

- [Ad ve e-posta](#name-and-email)
- [Getirme sırasında uzak dalları Ayıkla](#prune-remote-branches-during-fetch)
- [Çekme sırasında yerel dalı yeniden temellendir](#rebase-local-branch-when-pulling)
- [Şifreleme ağ sağlayıcısı](#cryptographic-network-provider)
- [Kimlik bilgisi Yardımcısı](#credential-helper)
- [Fark & birleştirme araçları](#diff--merge-tools)
- [Git dosyaları](#git-files)
- [Uzak depolar](#remotes)
- [Diğer ayarlar](#other-settings)

>[!NOTE]
>Visual Studio **genel Ayarlar** ' de yapılandırılan git ayarları, git 'in kullanıcıya özgü yapılandırma dosyasındaki ayarlara karşılık gelir ve **depo Ayarlar** ayarları, depoya özgü yapılandırma dosyasındaki ayarlara karşılık gelir. git yapılandırması hakkında daha fazla bilgi için git, [git-config belgelerini](https://git-scm.com/docs/git-config)özelleştirme [Pro ve yapılandırma dosyalarında git başvurusunu](https://git-scm.com/docs/git-config#FILES) [Pro git](https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration)bölümüne bakın. Visual Studio gösterilmeyen Git ayarlarını yapılandırmak için, `git config` yapılandırma dosyalarınıza bir değer yazmak üzere komutunu kullanın: `git config [--local|--global|--system] section.key value` .

### <a name="name-and-email"></a>Ad ve e-posta

Sağladığınız ad ve e-posta, yaptığınız herhangi bir yürütmeye ait komter bilgileri olarak kullanılacaktır. Bu ayar hem genel hem de depo kapsamlarında kullanılabilir ve `git config` [user.name](https://git-scm.com/docs/git-config#Documentation/git-config.txt-username) ve [User.email](https://git-scm.com/docs/git-config#Documentation/git-config.txt-useremail) ayarlarına karşılık gelir.

1. git menüsünden **Ayarlar**' a gidin. kullanıcı adınızı ve e-postanızı genel düzeyde ayarlamak için **git genel Ayarlar**'ye gidin. kullanıcı adınızı ve e-postanızı depo düzeyinde ayarlamak için **git deposu Ayarlar** gidin.

2. Kullanıcı adınızı ve e-postanızı girip kaydetmek için **Tamam** ' ı seçin.

   :::image type="content" source="media/user-email-setting.png" alt-text="Seçenekler iletişim kutusundaki Git genel ayarlar bölmesi, bir e-postaya Kullanıcı adı için bir belirtme çizgisi ile.":::

### <a name="prune-remote-branches-during-fetch"></a>Getirme sırasında uzak dalları Ayıkla

Ayıklama, uzak üzerinde artık mevcut olmayan uzaktan izleme dallarını kaldırır ve Dallarınızın listesini temiz ve güncel tutmanıza yardımcı olur. Bu ayar hem genel hem de depo kapsamlarında kullanılabilir ve `git config` [Fetch. Ayıkla](https://git-scm.com/docs/git-config#Documentation/git-config.txt-fetchprune) ayarına karşılık gelir.

Bu seçeneği, genel düzeyde **true** olarak ayarlamayı öneririz. Geçerli ayarlar şunlardır:

- Doğru (önerilir)
- Yanlış
- Unset (varsayılan)

1. git menüsünden **Ayarlar**' a gidin. bu seçeneği genel düzeyde yapılandırmak için **git genel Ayarlar** gidin; bu seçeneği depo düzeyinde yapılandırmak için **git deposu Ayarlar** gidin.

2. Doğru **getirme sırasında uzak dalları Ayıkla** (  önerilir) olarak ayarlayın. Kaydetmek için **Tamam ' ı** seçin.

:::image type="content" source="media/prune-setting.png" alt-text="' Fetch sırasında uzak dalları Ayıkla ' ve açılan listeden ' true ' seçiliyken görüntülenen ekran görüntüsü.":::

### <a name="rebase-local-branch-when-pulling"></a>Çekme sırasında yerel dalı yeniden temellendir

Yeniden temellendirmeler, yukarı akış dalında olmayan geçerli dalda işlemeler tarafından yapılan değişiklikleri kaydederek, geçerli dalı yukarı akış dalına sıfırlar, ardından, ayrılan değişiklikleri uygular. Bu ayar hem genel hem de depo kapsamlarında kullanılabilir ve `git config` [çekme. yeniden temellendirme](https://git-scm.com/docs/git-config#Documentation/git-config.txt-pullrebase) ayarına karşılık gelir. Geçerli ayarlar şunlardır:

- Doğru: getirme sonrasında yukarı akış dalının üzerine geçerli dalı yeniden temellendir.
- Yanlış: geçerli dalı yukarı akış dalında birleştirin.
- Unset (varsayılan): diğer yapılandırma dosyalarında belirtilmedikçe, geçerli dalı yukarı akış dalında birleştirin.
- Etkileşimli: etkileşimli modda yeniden temellendir.
- Koru: yerel olarak oluşturulan birleştirme yürütmelerini Düzleştirmeden yeniden temellendir.

1. git menüsünden **Ayarlar**' a gidin. bu seçeneği genel düzeyde yapılandırmak için **git genel Ayarlar** gidin; bu seçeneği depo düzeyinde yapılandırmak için **git deposu Ayarlar** gidin.

2. İstenen ayara **çekme sırasında yerel dalı yeniden temellendir** seçeneğini belirleyin ve kaydetmek için **Tamam** ' ı seçin.

    :::image type="content" source="media/rebase-setting.png" alt-text="Açılan ekran görüntüsü, açılan listeden ' vurgulanmış ve ' doğru ' olarak yerel dalı yeniden temellendir ' i gösterir.":::

`pull.rebase`Visual Studio ' de **etkileşimli** olarak yapılandırmak mümkün değildir. Visual Studio etkileşimli yeniden temellendirme desteği yoktur.
`pull.rebase`Etkileşimli modu kullanacak şekilde yapılandırmak için komut satırını kullanın.

### <a name="cryptographic-network-provider"></a>Şifreleme ağ sağlayıcısı

Şifreleme ağ sağlayıcısı, çalışma zamanında hangi TLS/SSL arka ucunu kullanacağınızı yapılandıran ve `git config` [http. sslarka uç](https://git-scm.com/docs/git-config#Documentation/git-config.txt-httpsslBackend) ayarına karşılık gelen genel kapsamdaki bir git yapılandırma ayarıdır. Değerler şunlardır:

- OpenSSL: TLS ve SSL protokolleri için [OpenSSL](https://www.openssl.org/) kullanın.
- Güvenli kanal: TLS ve SSL protokolleri için [güvenli kanal (Schannel)](/windows/win32/secauthn/secure-channel) kullanın. Schannel, Windows kimlik bilgileri deposuna erişen yerel Windows çözümüdür ve bu sayede sertifikaların kurumsal çapta yönetimine olanak tanır.
- Unset (varsayılan): Bu ayar unset ise, OpenSSL varsayılandır.

1. git menüsünden **Ayarlar**' a gidin. bu ayarı yapılandırmak için **git genel Ayarlar** sayfasına gidin.

2. **Şifreleme ağ sağlayıcısını** istenen değere ayarlayın ve kaydetmek için **Tamam** ' ı seçin.

   :::image type="content" source="media/network-provider-setting.png" alt-text="Açılır listeden ' OpenSSL ' ile vurgulanmış ' şifreleme ağ sağlayıcısı ' ' nı gösteren ekran görüntüsü.":::

### <a name="credential-helper"></a>Kimlik bilgisi Yardımcısı

Visual Studio uzak bir Git işlemi gerçekleştirdiğinde, istek ile birlikte sağlanması için kimlik bilgilerinin gerektirdiğinden uzak uç nokta isteği reddedebilir. Bu sırada git, işlemi gerçekleştirmek için gereken kimlik bilgilerini döndürecek bir kimlik bilgisi Yardımcısı çağırır ve sonra isteği yeniden dener. Kullanılan kimlik bilgisi Yardımcısı, `git config` [Credential. Helper](https://git-scm.com/docs/gitcredentials) ayarına karşılık gelir. Genel kapsamda aşağıdaki değerlerle kullanılabilir:

- Windows için GCM: yardımcı olarak [Windows için Git kimlik bilgileri yöneticisini](https://github.com/microsoft/Git-Credential-Manager-for-Windows) kullanın.
- GCM Core: yardımcı olarak [Git Credential Manager Core](https://github.com/microsoft/Git-Credential-Manager-Core) kullanın.
- Unset (varsayılan): Bu ayar ayarlanmamışsa, sistem yapılandırması 'nda ayarlanan kimlik bilgisi Yardımcısı kullanılır. Windows 2,29 için Git 'in varsayılan kimlik bilgisi yardımcısı GCM Core ' dır.

1. git menüsünden **Ayarlar**' a gidin. bu ayarı yapılandırmak için **git genel Ayarlar** sayfasına gidin.

2. **Kimlik bilgisi yardımcısını** istenen değere ayarlayın ve kaydetmek için **Tamam** ' ı seçin.

:::image type="content" source="media/credential-helper-setting.png" alt-text="Seçenekler iletişim kutusunda kimlik bilgisi Yardımcısı ayarını gösteren ekran görüntüsü.":::

### <a name="diff--merge-tools"></a>Fark & birleştirme araçları

Git, tercih ettiğiniz araçlarınızla farkları hesaplanarak ve birleştirme çakışmalarını gösterecektir. Bu bölümdeki ayarlar, `git config` [diff. Tool](https://git-scm.com/docs/git-config#Documentation/git-config.txt-difftool) ve [merge. Tool](https://git-scm.com/docs/git-config#Documentation/git-config.txt-mergetool) ayarlarına karşılık gelir. git 'i, **git genel Ayarlar** ve **git deposu Ayarlar** **Visual Studio kullan** seçeneğini belirleyerek Visual Studio kullanacak şekilde yapılandırabilirsiniz. Diğer fark ve birleştirme araçlarını yapılandırmak için, `git config` [diff. Tool](https://git-scm.com/docs/git-config#Documentation/git-config.txt-difftool) veya [merge. Tool](https://git-scm.com/docs/git-config#Documentation/git-config.txt-mergetool) anahtarıyla kullanın.

:::image type="content" source="media/tools-setting.png" alt-text="Seçenekler iletişim kutusunda varsayılan fark aracını ve birleştirme aracını Ayarlama bölümünü gösteren ekran görüntüsü.":::

### <a name="git-files"></a>Git dosyaları

deponuzla ilgili [gitignore](https://git-scm.com/docs/gitignore) ve [gıtattributes](https://git-scm.com/docs/gitattributes) dosyalarını görüntülemek ve düzenlemek için **git deposu Ayarlar** kapsamındaki **git dosyaları** bölümünü kullanabilirsiniz.

:::image type="content" source="media/git-files-setting.png" alt-text="Depoda Ignore ve attributes dosyalarını görüntüleme ve düzenleme bölümünü gösteren ekran görüntüsü.":::

### <a name="remotes"></a>Kumanda

Deponun uzak **depolarını** yapılandırmak için **Git Deposu Ayarlar** UzakLar bölmesini kullanabilirsiniz. Bu ayar git uzak [komutuna karşılık gelen](https://git-scm.com/docs/git-remote) ve uzak depoları eklemenize, düzenlemenize veya kaldırmanıza olanak sağlar.

:::image type="content" source="media/remotes-settings.png" alt-text="Seçenekler iletişim kutusundaki Git Uzak Depolar bölmesini gösteren ekran görüntüsü.":::

### <a name="other-settings"></a>Diğer ayarlar

Diğer Tüm Git yapılandırma ayarlarınızı görüntülemek için yapılandırma dosyalarını açabilir ve görüntüebilirsiniz veya ayarları görüntülemek için `git config --list` çalıştırabilirsiniz.

## <a name="visual-studio-settings"></a>Visual Studio ayarları

Aşağıdaki ayarlar Git ile ilgili tercihleri Visual Studio ve Git yapılandırma dosyaları Visual Studio tarafından yönetilir. Bu bölümdeki tüm ayarlar **Git** Genel Erişim Ayarlar yapılandırılır.

- [Varsayılan konum](#default-location)
- [Depo açılırken Git'in altında yer alan açık çözümleri kapatma](#close-open-solutions-not-under-git-when-opening-a-repository)
- [Üçüncü taraf kaynaklardan yazar görüntülerini indirmeyi etkinleştirme](#enable-download-of-author-images-from-third-party-sources)
- [Değişiklikleri birleştirmeden sonra varsayılan olarak işleme](#commit-changes-after-merge-by-default)
- [Push --force'yi etkinleştirme](#enable-push---force-with-lease)
- [Git deposu Çözüm Gezgini klasör açma](#open-folder-in-solution-explorer-when-opening-a-git-repository)
- [Git deposu açılırken çözümü otomatik olarak yükleme](#automatically-load-the-solution-when-opening-a-git-repository)
- [Çift tıklama veya Enter tuşuyla dalları otomatik olarak denetleme](#automatically-check-out-branches-with-double-click-or-the-enter-key)

### <a name="default-location"></a>Varsayılan konum

**Varsayılan konum,** depoların kopyalanmış olduğu varsayılan klasörü yapılandırıyor.

:::image type="content" source="media/default-location-setting.png" alt-text="Seçenekler iletişim kutusundaki varsayılan konum alanını gösteren ekran görüntüsü.":::

### <a name="close-open-solutions-not-under-git-when-opening-a-repository"></a>Depo açılırken Git'in altında yer alan açık çözümleri kapatma

Varsayılan olarak, Visual Studio depoya geçişte açık olan tüm çözüm veya klasörleri kapatır. Bunu yaptığı zaman, Bir Git deposu açılırken klasör aç seçeneğine göre yeni deponun çözümünü veya klasörünü de yükleyebilir Çözüm Gezgini [Git](#open-folder-in-solution-explorer-when-opening-a-git-repository) deposu açılırken çözümü otomatik olarak [yükleyebilir.](#automatically-load-the-solution-when-opening-a-git-repository) Bu, açık kod ile açık depo arasındaki tutarlılığı sürdürür. Ancak çözümünüz depoyla aynı klasör kökünde yer alamasa da, depoya geçiş yapmak için çözümü açık tutmak iyi olabilir. Bunu bu ayarla da yapabiliriz. Değerler şu şekildedir:

- Evet: Bir depo açıldığında, o anda açık olan çözüm her zaman kapalı olur
- Hayır: Bir depo açıldığında Visual Studio çözümün Git'in altında olup olmadığını denetlemeyi gerçekleştirir. Açılmazsa çözüm açık kalır.
- Her zaman sor (varsayılan): Bu ayar ayar olduğunda, geçerli çözümü açık tutmak veya kapatmak istemeden depo başına bir iletişim kutusu aracılığıyla bir seçim belirleyebilirsiniz.

:::image type="content" source="media/close-sln-setting.png" alt-text="Seçenekler iletişim kutusundaki çözümü kapat ayarını gösteren ekran görüntüsü.":::


### <a name="enable-download-of-author-images-from-third-party-sources"></a>Üçüncü taraf kaynaklardan yazar görüntülerini indirmeyi etkinleştirme

Üçüncü taraf kaynaklardan yazar görüntülerinin indir indirebilirsiniz, genel kapsamda Visual Studio bir ayardır. İşaretlendiğinde, yazma görüntüleri [Kullanılabilirse, Dosyaatar](https://en.gravatar.com/)görüntü hizmetlerinden indirilir ve işleme ve geçmiş görünümlerde görüntülenir.

:::image type="content" source="media/download-image-setting.png" alt-text="Seçenekler iletişim kutusunda üçüncü taraf kaynaktan yazar görüntülerini indirmeyi etkinleştirmek için onay kutusunu gösteren ekran görüntüsü. ":::

>[!IMPORTANT]
>Araç, Commit ve History görünümlerinde yazar görüntüleri sağlamak için etkin depoda depolanan yazar e-posta adresleri için bir MD5 karması oluşturur. Daha sonra bu karma, hizmete daha önce kayıt olan kullanıcılar için eşleşen bir karma değeri bulmak üzere Biratar'a gönderilir. Eşleşme bulunursa, kullanıcı görüntüsü hizmetten alınır ve kullanıcı görüntüsü Visual Studio. Hizmeti yapılandırmamış kullanıcılar rastgele oluşturulmuş bir görüntü geri döner. E-posta adreslerinin E-posta adresleri Visual Studio veya Herhangi bir üçüncü tarafla paylaşılmaz.

### <a name="commit-changes-after-merge-by-default"></a>Değişiklikleri birleştirmeden sonra varsayılan olarak işleme

Birleştirmeden **sonra değişiklikleri işle varsayılan olarak** etkinleştirildiğinde, bir dal geçerli dalla birleştirildiğinde Git otomatik olarak yeni bir işleme oluşturur.

:::image type="content" source="media/merge-commit-setting.png" alt-text="Seçenekler iletişim kutusunda değişiklikleri birleştirmeden sonra varsayılan olarak işle onay kutusunu gösteren ekran görüntüsü.":::

- İşaretlendiğinde, `git merge` tarafından Visual Studio komutu seçeneğiyle birlikte `--commit` çalıştırıldı.
- Bu seçenek `git merge` işaretlenmezse, Visual Studio tarafından verilen komutlar seçeneklerle `--no-commit --no-ff` birlikte çalıştırabilirsiniz.

Bu seçenekler hakkında daha fazla bilgi için bkz. [--commit ve --no-commit](https://git-scm.com/docs/git-merge#Documentation/git-merge.txt---commit) ve [--no-ff](https://git-scm.com/docs/git-merge#Documentation/git-merge.txt---no-ff).

### <a name="enable-push---force-with-lease"></a>Push --force-with-lease'yi etkinleştirme

Etkinleştirildiğinde, bu ayar uygulamanın içinde `push --force-with-lease` Visual Studio. Varsayılan olarak **Push --force-with-lease'yi etkinleştir devre** dışıdır.

:::image type="content" source="media/push-force-setting.png" alt-text="Seçenekler iletişim kutusunda kiralama ile itme zorlamasını etkinleştirme onay kutusunu gösteren ekran görüntüsü.":::

Daha fazla bilgi için [bkz. push --force-with-lease](https://git-scm.com/docs/git-push#Documentation/git-push.txt---no-force-with-lease).

### <a name="open-folder-in-solution-explorer-when-opening-a-git-repository"></a>Git deposu Çözüm Gezgini klasör açma
<!-- todo: write section -->
Bir Git Visual Studio açmak veya bir Git deposuna geçiş yapmak için Visual Studio' i kullanarak değişiklikleri, işlemeleri, dalları ve depoyu IDE'nin içinde yönetebilirsiniz. Ayrıca Visual Studio depo kodunu da Çözüm Gezgini. Visual Studio, depo klasörünü çözümler, CMakeLists.txt veya tanıyacak diğer tüm görünüm dosyaları için tarar ve bunları depoda liste olarak Çözüm Gezgini. Buradan, yüklemek için bir çözüm veya dizin içeriğini görüntülemek için klasörü seçin. Bu onay kutusunu kapatarak Visual Studio depo klasörünü Çözüm Gezgini. Bu, temel olarak depoyu yalnızca Git Visual Studio olarak açmana olanak sağlar. Bu ayar varsayılan olarak açıktır.

:::image type="content" source="media/open-folder-setting.png" alt-text="Seçenekler iletişim kutusunda Git deposu açılırken klasör aç onay kutusunu gösteren ekran görüntüsü.":::

### <a name="automatically-load-the-solution-when-opening-a-git-repository"></a>Git deposu açılırken çözümü otomatik olarak yükleme

Bu ayar yalnızca Bir [Git](#open-folder-in-solution-explorer-when-opening-a-git-repository) deposu Çözüm Gezgini klasör aç ayarı açık olduğunda geçerlidir. Visual Studio'de bir Git deposu Visual Studio, sonraki klasör taraması depoda yalnızca bir çözüm olduğunu algılar ve Visual Studio otomatik olarak yükler. Ayarı devre dışı bırakırsanız, Çözüm Gezgini, görünümler listesinde depoda mevcut olan tek çözümü görüntüler. Ancak çözümü yüklemez. Varsayılan olarak bu ayar kapalıdır.

:::image type="content" source="media/load-solution-setting.png" alt-text="Seçenekler iletişim kutusunda Git deposu açılırken çözümü otomatik olarak yüklemek için onay kutusunu gösteren ekran görüntüsü.":::

### <a name="automatically-check-out-branches-with-double-click-or-the-enter-key"></a>Çift tıklama veya Enter tuşuyla dalları otomatik olarak denetleme

Git Deposu penceresinde ağaç yapısında görüntülenen dalların listesi vardır. Bir dal seçildiğinde, seçilen dal için işlemeler görüntülemek üzere işleme geçmişi bölmesine geçiş yapar. Bir dalı kontrol etmek için sağ tıklar ve bağlam menüsünü açıp Tamamla'yı **seçebilirsiniz.** Bu ayarı etkinleştirirseniz Enter tuşuna çift tıklar veya tuşuna basılarak dal kontrol olur ve dalın işlemeleri görüntülenir.

:::image type="content" source="media/checkout-branch-setting.png" alt-text="Seçenekler iletişim kutusunda çift tıklama veya Enter tuşuyla dalları iade etmek için onay kutusunu gösteren ekran görüntüsü.":::


## <a name="see-also"></a>Ayrıca bkz.

> [!IMPORTANT]
> Bize bir öneriniz varsa lütfen bize haber ver! Geliştirici portalı üzerinden tasarım kararları alma fırsatınız [**Community.**](https://aka.ms/vsgitsuggestions)

- [Başlarken öğreticisinde Git GitHub Visual Studio](/learn/modules/visual-studio-github-push/) ile Microsoft Learn
- [YouTube'daki Visual Studio Git](https://www.youtube.com/watch?v=GCZ9x3yqkyc) ile çalışmaya başlama
- [Git ile gelişmiş üretkenlik Visual Studio](https://devblogs.microsoft.com/visualstudio/enhanced-productivity-with-git-in-visual-studio/) blog gönderisi
- [Seçenekler iletişim kutusu](../ide/reference/options-dialog-box-visual-studio.md)
