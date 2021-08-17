---
title: Visual Studio'de Git ayarları
titleSuffix: ''
description: Tercihlerinizi Visual Studio için .gitconfig dosyalarını ve Git ayarlarını nasıl kullandığını öğrenin
ms.date: 06/08/2021
ms.topic: conceptual
ms.author: prnadago
author: prnadago
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.manager: jmartens
monikerRange: '>=vs-2019'
ms.openlocfilehash: 5a92d27aa170afe365b878368bc32599bfe87030aacf5ef15fe3ef056b8d19e2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121226975"
---
# <a name="git-settings-and-preferences-in-visual-studio"></a>Visual Studio'daki Git ayarları ve tercihleri

Bu Visual Studio, adınız ve e-posta adresiniz, tercih ettiğiniz fark ve birleştirme araçları gibi yaygın Git ayarlarını ve tercihlerini yapılandırabilirsiniz ve görüntüebilirsiniz. Bu ayarlar ve tercihler, **Git Genel**  Ayarlar sayfasındaki Seçenekler iletişim kutusunda (tüm depolar için geçerlidir) veya Git Deposu Ayarlar sayfasında (geçerli depo için geçerlidir)  görüntüleyebilirsiniz.

İki tür ayar yapılandırabilirsiniz:

- [Git ayarları](#git-settings) - Bu bölümdeki ayarlar, Git yapılandırma dosyalarına kaydedilen Git ayarlarına karşılık gelen ayarlardır. Bu ayarlar, uygulama içinde değiştirilebilir Visual Studio, ancak Git yapılandırma dosyaları tarafından yönetilir.
- [Visual Studio ayarları](#visual-studio-settings) - Bu bölümdeki ayarlar Git ile ilgili ayarları ve uygulama tarafından yönetilen tercihleri Visual Studio.

## <a name="how-to-configure-settings"></a>Ayarları yapılandırma

1. Git ayarlarını Visual Studio için üst **Ayarlar** Git menüsünden Git'i seçin.

   :::image type="content" source="media/git-menu-settings.png" alt-text="Ayarlar komutuna bir çağrı Ayarlar.":::

2. Genel düzey Ayarlar veya **depo düzeyi Ayarlar** görüntülemek ve yapılandırmak için **Git** Genel Depolama Veya Git Deposu'Ayarlar'yi seçin.

   :::image type="content" source="media/source-control-settings.png" alt-text="Seçenekler iletişim kutusunda Git ayarlarına bir çağrıyla birlikte gezinti bölmesi.":::

3. Bu makalenin aşağıdaki bölümlerinde açıklandığı gibi bazı yaygın Git ayarlarını yapılandırabilirsiniz. İstediğiniz ayarları yapılandırdikten sonra, güncelleştirilmiş **ayarları kaydetmek** için Tamam'ı seçin.

   :::image type="content" source="media/ok-button.png" alt-text="Seçenekler iletişim kutusunun Tamam düğmesine bir çağrı çizgisiyle birlikte görünen alanı.":::

## <a name="git-settings"></a>Git ayarları

Ayrıca en yaygın Git yapılandırma ayarlarından bazılarını yapılandırabilirsiniz ve kontrol edebilirsiniz. Git yapılandırma dosyaları tarafından yönetilseler Visual Studio aşağıdaki ayarları görüntüp değiştirebilirsiniz.

- [Ad ve e-posta](#name-and-email)
- [Getirme sırasında uzak dalları ayıklama](#prune-remote-branches-during-fetch)
- [Çekmede yerel dalı yeniden temeli](#rebase-local-branch-when-pulling)
- [Şifreleme ağ sağlayıcısı](#cryptographic-network-provider)
- [Kimlik bilgisi yardımcı](#credential-helper)
- [Fark & birleştirme Araçları](#diff--merge-tools)
- [Git dosyaları](#git-files)
- [Kumanda](#remotes)
- [Diğer ayarlar](#other-settings)

>[!NOTE]
>Visual Studio'nin Genel Ayarlar'de yapılandırılan Git ayarları Git'in kullanıcıya özgü yapılandırma dosyasındaki ayarlara  karşılık, Depo Ayarlar'daki ayarlar ise depoya özgü yapılandırma dosyasındaki ayarlara karşılık gelen ayarlardır.  Git yapılandırması hakkında daha fazla bilgi için [Git'Pro,](https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration) [git-config](https://git-scm.com/docs/git-config)belgeleri ve yapılandırma dosyalarında git başvurusu ile ilgili git Pro Git başvurusu [bölümlerine bakın.](https://git-scm.com/docs/git-config#FILES) Bu dosyalarda açık Visual Studio Git ayarlarını yapılandırmak için komutunu kullanarak `git config` yapılandırma dosyalarınıza bir değer yazın: `git config [--local|--global|--system] section.key value` .

### <a name="name-and-email"></a>Ad ve e-posta

Sağlayıcının adı ve e-postası, yapılan tüm işlemeler için committer bilgileri olarak kullanılır. Bu ayar hem genel hem de depo kapsamları için kullanılabilir ve user.name `git config` [](https://git-scm.com/docs/git-config#Documentation/git-config.txt-username) ve user.email karşılık gelen ayarlardır. [](https://git-scm.com/docs/git-config#Documentation/git-config.txt-useremail)

1. Git menüsünden git'e **Ayarlar.** Kullanıcı adını ve e-postanızı genel düzeyde ayarlamak için **Git** Genel Ayarlar; Kullanıcı adını ve e-postanızı depo düzeyinde ayarlamak için Git **Deposu'Ayarlar.**

2. Kullanıcı adı ve e-postanızı girin, sonra kaydetmek için **Tamam'ı** seçin. 

   :::image type="content" source="media/user-email-setting.png" alt-text="Seçenekler iletişim kutusundaki Git Genel ayarlar bölmesinde, e-postanın kullanıcı adını ifade etmek için bir çağrı ekleyin.":::

### <a name="prune-remote-branches-during-fetch"></a>Getirme sırasında uzak dalları ayıklama

Ayıklama, uzakta artık mevcut olmayan uzaktan izleme dallarını kaldırır ve dallar listenizi temiz ve güncel tutmanıza yardımcı olur. Bu ayar hem genel hem de depo kapsamlarında kullanılabilir ve `git config` [fetch.prune ayarına karşılık](https://git-scm.com/docs/git-config#Documentation/git-config.txt-fetchprune) geliyor.

Bu seçeneği genel düzeyde **True** olarak ayarlamayı öneririz. Geçerli ayarlar şunlardır:

- Doğru (önerilir)
- Yanlış
- Kümeyi geri ala (varsayılan)

1. Git menüsünden git'e **Ayarlar.** Bu seçeneği **genel Ayarlar** yapılandırmak için Git Genel Erişim'e gidin; Bu seçeneği **depo Ayarlar** için Git Deposu deposuna gidin.

2. Getirme **sırasında uzak dalları ayıklamayı** True olarak **ayarlayın** (önerilir). Kaydetmek **için Tamam'ı** seçin.

:::image type="content" source="media/prune-setting.png" alt-text="'Getirme sırasında uzak dalları ayıklama' vurgulanmış ve açılan listelerden 'True' seçilmiş olarak gösteren ekran görüntüsü.":::    

### <a name="rebase-local-branch-when-pulling"></a>Çekmede yerel dalı yeniden temeli

Yenidenbasing, geçerli dalda yer alan ve yukarı akış dalda yer alan commit'ler tarafından yapılan değişiklikleri bir kenara bırakıp geçerli dalı yukarı akış dalına sıfırlar ve sonra bir kenara ayarlanmış değişiklikleri uygular. Bu ayar hem genel hem de depo kapsamları için kullanılabilir ve `git config` [pull.rebase ayarına karşılık](https://git-scm.com/docs/git-config#Documentation/git-config.txt-pullrebase) gelen bir ayardır. Geçerli ayarlar şunlardır:

- Doğru: Getirme sonrasında geçerli dalı yukarı akış dalın üzerine yeniden tabanına alın.
- False: Geçerli dalı yukarı akış dalı ile birleştirin.
- Kümeyi geri alın (varsayılan): Diğer yapılandırma dosyalarında belirtilmemişse geçerli dalı yukarı akış dalı ile birleştirin.
- Etkileşimli: Etkileşimli modda yeniden temeli yapın.
- Koru: Yerel olarak oluşturulan birleştirme işlemelerini düz yapmadan yeniden temeli oluşturma.

1. Git menüsünden git'e **Ayarlar.** Bu seçeneği **genel Ayarlar** yapılandırmak için Git Genel Erişim'e gidin; Bu seçeneği **depo Ayarlar** için Git Deposu deposuna gidin.

2. İstenen **ayara doğru çekerek Yerel dalı** yeniden temeli olarak ayarlayın ve kaydetmek için **Tamam'ı** seçin.

    :::image type="content" source="media/rebase-setting.png" alt-text="Açılan listelerden 'Çekmede yerel dalı yeniden temeli' vurgulanmış ve 'True' seçilmiş olarak gösteren ekran görüntüsü.":::

Uygulama içinde Etkileşimli olarak `pull.rebase`  yapılandırmak Visual Studio. Visual Studio etkileşimli yeniden tabanı desteğine sahip değil.
etkileşimli modu `pull.rebase` kullanmak üzere yapılandırmak için komut satırı kullanın.

### <a name="cryptographic-network-provider"></a>Şifreleme ağ sağlayıcısı

Şifreleme ağ sağlayıcısı, genel kapsamda çalışma zamanında hangi TLS/SSL arka ucun kullandırılacak yapılandıran ve `git config` [http.sslBackend](https://git-scm.com/docs/git-config#Documentation/git-config.txt-httpsslBackend) ayarına karşılık gelen bir Git yapılandırma ayarıdır. Değerler şu şekildedir:

- OpenSSL: TLS ve SSL protokolleri için [OpenSSL](https://www.openssl.org/) kullanın.
- Güvenli Kanal: TLS ve SSL protokolleri için Güvenli Kanal [(schannel)](/windows/win32/secauthn/secure-channel) kullanın. Schannel, Windows erişim sağlayan yerel Windows Credential Store çözümüdür ve bu sayede sertifikaların kuruluş genelinde yönetimine olanak sağlar.
- Kümeyi geri ala (varsayılan): Bu ayar unset ise OpenSSL varsayılan ayardır.

1. Git menüsünden git'e **Ayarlar.** Bu ayarı **yapılandırmak Ayarlar Git** Genel Erişim'e gidin.

2. Şifreleme **ağ sağlayıcısını istenen** değere ayarlayın ve kaydetmek için **Tamam'ı** seçin.

   :::image type="content" source="media/network-provider-setting.png" alt-text="Açılan listelerden 'OpenSSL' seçili olarak vurgulanmış 'Şifreleme ağ sağlayıcısı'nın ekran görüntüsü.":::

### <a name="credential-helper"></a>Kimlik bilgisi yardımcı

Uzak Visual Studio bir Git işlemi gerçekleştiriyorsa, istekle kimlik bilgilerinin sağlanmalıdır gerektirdiği için uzak uç nokta isteği reddeder. Bu sırada Git, işlemi gerçekleştirmek için gereken kimlik bilgilerini geri çağıran bir kimlik bilgisi yardımcısı çağırır ve ardından isteği yeniden dener. Kullanılan kimlik bilgisi yardımcı, `git config` [credential.helper ayarına karşılık](https://git-scm.com/docs/gitcredentials) geldi. Genel kapsamda aşağıdaki değerlerle kullanılabilir:

- Windows GCM: Yardımcı [Kimlik Bilgileri Yöneticisi için Windows Git'i](https://github.com/microsoft/Git-Credential-Manager-for-Windows) kullanın.
- GCM Core: [Yardımcı Kimlik Bilgileri Yöneticisi Git Kimlik Bilgileri Yöneticisi Core](https://github.com/microsoft/Git-Credential-Manager-Core) kullanın.
- Kümeyi geri ayarla (varsayılan): Bu ayar ayarlanmamışsa, sistem yapılandırmasında ayarlanmış kimlik bilgisi yardımcısı kullanılır. Windows 2.29 için Git'te varsayılan kimlik bilgisi yardımcı GCM Core'dır.

1. Git menüsünden git'e **Ayarlar.** Bu ayarı **yapılandırmak Ayarlar Git** Genel Erişim'e gidin.

2. Kimlik **Bilgisi yardımcısı'nın** istediğiniz değere ayarlayın ve kaydetmek için **Tamam'ı** seçin.

:::image type="content" source="media/credential-helper-setting.png" alt-text="Seçenekler iletişim kutusundaki kimlik bilgisi yardımcı ayarını gösteren ekran görüntüsü.":::

### <a name="diff--merge-tools"></a>Fark & birleştirme araçları

Git tercih ettiğiniz araçlarda farkları ve birleştirme çakışmalarını gösterir. Bu bölümdeki ayarlar `git config` [diff.tool ve merge.tool](https://git-scm.com/docs/git-config#Documentation/git-config.txt-difftool) [ayarlarına karşılık](https://git-scm.com/docs/git-config#Documentation/git-config.txt-mergetool) gelen ayarlardır. Git'i Git Genel Visual Studio'da birleştirme veya fark aracı olarak kullanmak üzere yapılandırabilirsiniz **Ayarlar** **Git Deposu Ayarlar'i** **Visual Studio.** Diğer fark ve birleştirme araçlarını yapılandırmak için `git config` [diff.tool](https://git-scm.com/docs/git-config#Documentation/git-config.txt-difftool) veya [merge.tool anahtarıyla](https://git-scm.com/docs/git-config#Documentation/git-config.txt-mergetool) kullanın.

:::image type="content" source="media/tools-setting.png" alt-text="Seçenekler iletişim kutusunda varsayılan Fark aracını ve Birleştir aracını ayarlama bölümünü gösteren ekran görüntüsü.":::

### <a name="git-files"></a>Git dosyaları

Deponun [gitignore](https://git-scm.com/docs/gitignore) ve  [gitattributes](https://git-scm.com/docs/gitattributes) dosyalarını görüntülemek **Ayarlar** ve düzenlemek için Git Deposu'nda Git dosyaları bölümünü kullanabilirsiniz.

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
- Hayır: Bir depo açıldığında Visual Studio çözümün Git'in altında olup olmadığını kontrol etmek için bir denetim gerçekleştirir. Açılmazsa çözüm açık kalır.
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

- İşaretlendiğinde, `git merge` bir Visual Studio verilen komutlar seçeneğiyle birlikte `--commit` çalıştırıldı.
- Bu seçenek `git merge` işaretlenmezse, Visual Studio tarafından verilen komutlar seçeneklerle `--no-commit --no-ff` birlikte çalıştırıldı.

Bu seçenekler hakkında daha fazla bilgi için bkz. [--commit ve --no-commit](https://git-scm.com/docs/git-merge#Documentation/git-merge.txt---commit) ve [--no-ff](https://git-scm.com/docs/git-merge#Documentation/git-merge.txt---no-ff).

### <a name="enable-push---force-with-lease"></a>Push --force-with-lease'yi etkinleştirme

Etkinleştirildiğinde, bu ayar bir uygulamanın `push --force-with-lease` içinde Visual Studio. Varsayılan olarak **Push --force-with-lease'yi etkinleştir devre** dışıdır.

:::image type="content" source="media/push-force-setting.png" alt-text="Seçenekler iletişim kutusunda kiralama ile itme zorlamasını etkinleştirme onay kutusunu gösteren ekran görüntüsü.":::

Daha fazla bilgi için [bkz. push --force-with-lease](https://git-scm.com/docs/git-push#Documentation/git-push.txt---no-force-with-lease).

### <a name="open-folder-in-solution-explorer-when-opening-a-git-repository"></a>Git deposunu Çözüm Gezgini klasör açma
<!-- todo: write section -->
Bir Git Visual Studio açmak veya bir Git deposuna geçiş yapmak için Visual Studio, değişiklikleri, işlemeleri, dalları görüntüleyebilirsiniz ve depoyu IDE'nin içinde yönetebilirsiniz. Ayrıca Visual Studio depo kodunu da Çözüm Gezgini. Visual Studio, depo klasörünü çözümler, CMakeLists.txt veya tanıyacak diğer tüm görünüm dosyaları için tarar ve bunları depoda liste olarak Çözüm Gezgini. Buradan, yüklemek için bir çözüm veya dizin içeriğini görüntülemek için klasörü seçin. Bu onay kutusunu kapatarak Visual Studio depo klasörünü Çözüm Gezgini. Bu, temel olarak bir git Visual Studio git depo yöneticisi olarak açmana olanak sağlar. Bu ayar varsayılan olarak açıktır.

:::image type="content" source="media/open-folder-setting.png" alt-text="Seçenekler iletişim kutusunda Git deposu açılırken klasör aç onay kutusunu gösteren ekran görüntüsü.":::

### <a name="automatically-load-the-solution-when-opening-a-git-repository"></a>Git deposu açılırken çözümü otomatik olarak yükleme

Bu ayar yalnızca Bir [Git](#open-folder-in-solution-explorer-when-opening-a-git-repository) deposu Çözüm Gezgini klasör aç ayarı açık olduğunda geçerlidir. Visual Studio'de bir Git deposu açıp sonraki klasör taraması, depoda yalnızca bir çözüm olduğunu algılar ve Visual Studio otomatik olarak yükler. Ayarı devre dışı bırakırsanız, Çözüm Gezgini, görünümler listesinde depoda mevcut olan tek çözümü görüntüler. Ancak çözümü yüklemez. Varsayılan olarak bu ayar kapalıdır.

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
