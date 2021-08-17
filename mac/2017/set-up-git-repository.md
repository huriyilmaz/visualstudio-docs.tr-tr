---
title: Git Deposu Ayarlama
description: Git ve Subversion'ı Mac için Visual Studio.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 02/15/2018
ms.assetid: E992FA1D-B2AD-4A28-ADC6-47E4FC471060
ms.topic: how-to
ms.openlocfilehash: ef846c09d609d4a7df2663f1077ba45087154ae4f98521cacd87948639e4fc87
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121350882"
---
# <a name="set-up-a-git-repository"></a>Git deposu ayarlama

Git, ekiplerin aynı belgeler üzerinde aynı anda çalışmasına olanak sağlayan bir dağıtılmış sürüm denetim sistemidir. Bu, tüm dosyaları içeren tek bir sunucu olduğu anlamına gelir, ancak bu merkezi kaynaktan bir depo kullanıma her iade edilirse, deponun tamamı yerel olarak makinenize kopyalanmış olur.

Sürüm denetimi için Git ile çalışmana olanak sağlayan birçok uzak konak vardır, ancak en yaygın konak GitHub. Aşağıdaki örnek bir GitHub ana bilgisayar kullanır, ancak sürüm denetimi için herhangi bir Git ana bilgisayar Mac için Visual Studio.

Bu makaledeki adımları GitHub önce bir hesap oluşturduğunuzdan ve yapılandırıldığından emin olun.

## <a name="creating-a-remote-repo-on-github"></a>GitHub'de uzak bir depolama GitHub

Aşağıdaki örnek bir GitHub ana bilgisayar kullanır, ancak sürüm denetimi için herhangi bir Git ana bilgisayar Mac için Visual Studio.

Git deposu ayarlamak için aşağıdaki adımları yürütün:

1. Github.com'da yeni bir Git github.com:

    ![Yeni git depo oluşturma](media/version-control-git1-sml.png)

2. Repo Adı, açıklaması ve gizliliği ayarlayın. **Repo'nun** başlatılmaz. .gitignore ve lisansı Yok olarak ayarlayın:

    ![Git depo ayrıntılarını ayarlama](media/version-control-git2.png)

3. Sonraki sayfada, HTTPS veya SSH adresini görüntüleyebilirsiniz ve oluşturduğunuz repoya kopyaleyebilirsiniz:

    ![adresi görüntüleme ve kopyalama](media/version-control-git3.png)

   Bu repoya işaret etmek için HTTPS Mac için Visual Studio gerekir.

## <a name="publishing-an-existing-project"></a>Mevcut projeyi yayımlama

Sürüm denetiminde yer alan _mevcut bir_ projeniz varsa, Git'te ayarlamak için aşağıdaki adımları kullanın:

1. Dosyanın içinde yer alan Çözüm Bölmesi Çözüm Mac için Visual Studio.

2. Menü çubuğunda Sürüm **Denetimi'>'ı seçerek Depo Seç** iletişim **kutusunu görüntülemek için Sürüm Denetimi'ne** tıklayın:

    ![Mac için Visual Studio'da checkout'Mac için Visual Studio](media/version-control-git4-sml.png)

    Menüde bu menü öğesi gri görünüyorsa Çözüm adını seçtiğinizden emin olun.

3. Kayıtlı **Depolar sekmesini** seçin ve Ekle **düğmesine** basın:

    ![Depo Seç iletişim kutusunun Kayıtlı Depolar sekmesinde Modül adı ve İleti kutularına ek olarak Ekle, Kaldır ve Düzenle düğmeleri bulunur.](media/version-control-git5.png)

4. Deponun yerel olarak görüntülemesini istediğiniz adı girin ve sonraki adımdan URL'yi #3. Depo Yapılandırması iletişim kutusu aşağıdakine benzer şekilde görünür. Tamam'a basın:

    ![Git ayrıntılarını girin iletişim kutusu](media/version-control-git6.png)

    Git'e bağlanmak için SSH de kullanabilirsiniz.

5. Uygulamayı Git'te yayımlamayı denemeniz için depoyu seçin  ve hem Modül Adı hem de İleti metin **alanlarının tamamlandığından** emin olmak için:

    ![Projeyi git'e yayımlamayı deneme](media/version-control-git7.png)

6. **Tamam'a** tıklayın ve **ardından uyarı** iletişim kutusunda Yayımla'ya tıklayın.

7. Git **Kimlik Bilgileri penceresinde** kullanıcı adınızı ve GitHub girin. 

> [!NOTE]
> Hesabınız iki faktörlü kimlik doğrulamasını (2FA) etkinleştirdiyse, parola yerine kullanılan bir Erişim Belirteci oluşturmanız gerekir. Erişim belirteci oluşturmadısanız Git Erişim Belirteci [belgelerinde yer alan adımları](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) izleyin.

8. Kullanıcı adını ve Kişisel Erişim Belirteci girin ve Tamam'a **basın:**

    ![Git için kullanıcı adı ve parola girin](media/version-control-git9-sml.png)

9. Birkaç saniye sonra, Çözüm ilk işlemesi ile yayımlanır. Artık birçok seçenekle doldurulması gereken Sürüm Denetimi menü öğesine göz atarak yayım olduğunu onaylayın:

    ![Sürüm Denetimi Menüsü](media/version-control-git10.png)

10. Ek değişiklikler yapmaya başladıktan sonra değişiklikleri uzak **depoya** itmek için Değişiklikleri **Itme'yi** seçin. Bu, tüm uygun kullanıcıların bu görünümü şu github.com:

    ![Değişiklikleri uzak depoya itme](media/version-control-git11.png)

## <a name="publishing-a-new-project"></a>Yeni proje yayımlama

Yeni proje iletişim kutusu, yerel git deposuyla yeni bir proje oluşturmak için kullanılabilir. Etkinleştirmek için, aşağıdaki ekran **görüntüsünde gösterildiği gibi** Sürüm denetimi için git kullan onay kutusunu seçin. Bu, deponızı başlatacak ve isteğe bağlı bir .gitignore dosyası ekler:

![Git desteğiyle yeni proje oluşturma](media/version-control-git-publish-new1.png)

Yeni yerel depoyu yeni bir depolama deposuna GitHub izleyin:

> [!NOTE]
> Henüz bir depo oluşturmadı GitHub uzak depo oluşturma [bölümüne GitHub](#creating-a-remote-repo-on-github) bakın.

1. Menü Çubuğunda Sürüm Denetimi'ne gidip **çözümü > ve Commit'i seçerek** ilk işlemenizi oluşturun.

2. Durum sekmesinde, sol üst **tarafta Commit** (Commit) (Commit) (Tamamla) seçeneğine tıklayın.

3. "İlk Commit" gibi bir işleme iletisi yazın, sonra Dala'ya **tıklayın:**

    ![Git deposuna ilk değişiklikleri işleme](media/version-control-git-publish-new2.png)

4. Ardından, Menü Çubuğunda Sürüm Denetimi'ne **gidin > Ve UzakLarı Yönet'e gidin.**

5. Uzak Kaynaklar **sekmesine gidin** ve Ekle'ye **tıklayın.**

6. Uzak **Kaynak penceresinde,** önceden oluşturduğunuz deponun ayrıntılarını ekleyin GitHub'a **tıklayın:**

    ![Git deposu için uzak kaynakları yapılandırma](media/version-control-git-publish-new3.png)

7. Git Deposu **Yapılandırması penceresini kapatın,** ardından Menü Çubuğunda Sürüm Denetimi'ne gidin ve **değişiklikleri >'a gidin.**

8. Depoya **Itme penceresinde** Değişiklikleri Itme **düğmesine** tıklayın:

    ![Değişiklikleri uzak depoya itme](media/version-control-git-publish-new4.png)

9. İstendiğinde kullanıcı adı GitHub parolanızı girin.

> [!NOTE]
> Hesabınız iki faktörlü kimlik doğrulamasını (2FA) etkinleştirdiyse, parola yerine kullanılan bir Erişim Belirteci oluşturmanız gerekir. Erişim belirteci oluşturmadısanız Git Erişim Belirteci [belgelerinde yer alan adımları](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) izleyin.

Mac için Visual Studio şimdi değişiklikleri uzak depo GitHub itecek:

![Anında iletişim işlemi başarıyla tamamlandı onayı](media/version-control-git11.png)

## <a name="check-out-an-existing-repository"></a>Mevcut depoyu denetleme

Büyük olasılıkla yerel makineniz üzerinde değil, yalnızca uzak GitHub bir depolama depolaması ile çalışmanız gerekir. Mac için Visual Studio hızlı bir şekilde bu repoya göz atabilirsiniz. Makinenize klonlamak için aşağıdaki adımları izleyin:

1. Menü çubuğunda Sürüm **Denetimi'ne tıklayın ve > edin:**

2. Depoya **Bağlan sekmesi görüntülenir:**

    ![Bağlan ayrıntıların gir olduğu Depo sekmesine gidin](media/version-control-git13.png)

3. Uzak GitHub üst sayfasında Kopyala veya İndir düğmesine **basın ve** sağlanan URL'yi kopyalayın:

    ![görüntülenen github URL'si](media/version-control-git14.png)

4. Url girişi alanında yer **alan** tüm metni Depo Bağlan **değiştirin.** Bu, adım adım görüntüde gösterildiği gibi bu sekmede yer alan diğer alanların çoğunu sizin #2.

5. Repo'nun içine klonlamak istediğiniz dizini girin ve **Checkout tuşuna basın.**

> [!NOTE]
> Depolama alanı boyutu 4 GB'ın üzerinde ise sorun yaşanabilirsiniz.

## <a name="troubleshooting"></a>Sorun giderme

Projenizi boş bir uzak depoyla başlatmayla ilgili sorunlarınız varsa aşağıdaki adımları denemeniz gerekir:

1. Çözüm klasörünüze gidin.
1. Komut **+ Shift + tuşlarına basın.** gizli dosyaları ve klasörleri göstermek için.
1. **Bir .git klasörü varsa** silin.
1. **Gitignore dosyası varsa** silin.
1. Komut **+ Shift + tuşlarına basın.** dosya ve klasörleri gizlemek için.
1. Çözümlerinizi Mac için VS'de açın.
1. Çözüm Paneli'nin çözüm düğümünü seçin.
1. Sürüm Denetimi menüsüne gidin ve Sürüm Denetiminde **Yayımla'yı seçin.**
1. 6. adımdan başlayarak yukarıdaki öğreticinin adımlarını izleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio sürüm denetimi (Windows)](/visualstudio/version-control/)
