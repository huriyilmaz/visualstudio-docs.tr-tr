---
title: Git Deposu Ayarlama
description: Mac için Visual Studio kullanarak Git deposuna bağlanma.
author: therealjohn
ms.author: johmil
ms.date: 12/03/2020
ms.assetid: E992FA1D-B2AD-4A28-ADC6-47E4FC471060
ms.topic: how-to
ms.openlocfilehash: bacd533bf5c28c6f431fe7088fad36b6bbd3d04b
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123964811"
---
# <a name="set-up-a-git-repository"></a>Git deposu ayarlama

Git, ekiplerin aynı belgeler üzerinde aynı anda çalışmasına olanak sağlayan bir dağıtılmış sürüm denetim sistemidir. Bu, tüm dosyaları içeren tek bir sunucu olduğu anlamına gelir, ancak bu merkezi kaynaktan bir depo kullanıma her iade edilirse, deponun tamamı yerel olarak makinenize kopyalanmış olur.

Sürüm denetimi için Git ile çalışmana olanak sağlayan birçok uzak konak vardır, ancak en yaygın konak GitHub. Aşağıdaki örnek bir GitHub ana bilgisayar kullanır, ancak sürüm denetimi için herhangi bir Git ana bilgisayar Mac için Visual Studio.

Bu makaledeki adımları GitHub önce bir hesap oluşturduğunuzdan ve yapılandırıldığından emin olun.

## <a name="creating-a-remote-repo-on-github"></a>GitHub'da uzak bir depolama GitHub

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

> [!TIP]
> Git ile hangi klasörlerin ve dosyaların iz ve yayımlan olduğunu kontrol etmek için bir .gitignore dosyası kullanın. Derleme dizinlerini, ikili dosyaları veya oluşturulan dosyaları dışlamak istemeyebilirsiniz. Daha fazla bilgi için [GitHub yoksayma belgelerine göz atabilirsiniz.](https://docs.github.com/en/free-pro-team@latest/github/using-git/ignoring-files)

1. Mac için Visual Studio'de Çözüm Penceresi'Mac için Visual Studio.

2. Menü çubuğunda Sürüm **Denetimi'>'ı seçerek Depoyu** Kopyala iletişim kutusunu görüntülemek **için Sürüm Denetimi'ne** tıklayın:

    ![Mac için Visual Studio'da checkout'Mac için Visual Studio](media/version-control-git4.png)

    Menüde bu menü öğesi gri görünüyorsa Çözüm adını seçtiğinizden emin olun.

3. **Kayıtlı'dan seç sekmesini** seçin ve Ekle **düğmesine** basın:

    ![Kayıtlı depo ekle iletişim kutusu.](media/version-control-git5.png)

4. Deponun yerel olarak görüntülemesini istediğiniz adı girin ve sonraki adımdan URL'yi #3. Depo Yapılandırması iletişim kutusu aşağıdakine benzer şekilde görünür. Tamam'a basın:

    ![Git ayrıntılarını girin iletişim kutusu](media/version-control-git6.png)

    Git'e bağlanmak için SSH de kullanabilirsiniz.

5. Uygulamayı Git'te yayımlamayı denemeniz için depoyu seçin ve hem Modül Adı hem de İleti **metin** **alanlarının tamamlandığından** emin olmak için:

    ![Projeyi git'e yayımlamayı deneme](media/version-control-git7.png)

6. **Tamam'a** tıklayın ve **ardından uyarı** iletişim kutusunda Yayımla'ya tıklayın.

7. Git **Kimlik Bilgileri penceresinde** kullanıcı adı ve GitHub bilgilerinizi girin. 

> [!NOTE]
> Hesabınız iki faktörlü kimlik doğrulamasını (2FA) etkinleştirdiyse, parola yerine kullanılan bir Erişim Belirteci oluşturmanız gerekir. Erişim belirteci oluşturmadısanız Git Erişim Belirteci [belgelerinde yer alan adımları](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) izleyin.

8. Kullanıcı adını ve Kişisel Erişim Belirteci girin ve Tamam'a **basın:**

    ![Git için kullanıcı adı ve parola girin](media/version-control-git9-sml.png)

9. Birkaç saniye sonra, Çözüm ilk işlemesi ile yayımlanır. Artık birçok seçenekle doldurulması gereken Sürüm Denetimi menü öğesine göz atarak yayım olduğunu onaylayın:

    ![Sürüm Denetimi Menüsü](media/version-control-git10.png)

10. Ek değişiklikler yapmaya başladıktan sonra, durum görünümünü açmak için **> gözden geçir ve** Işle menüsünü kullanarak Sürüm Denetimi'ne gidin. Değişiklikleri seçtikten ve işledikten sonra, değişiklikleri **uzak** depoya itmek için Anındat'ı seçin. Bu, tüm uygun kullanıcıların bu görünümü github.com:

    ![Değişiklikleri uzak depoya itme](media/version-control-git11.png)

## <a name="publishing-a-new-project"></a>Yeni proje yayımlama

Yeni proje iletişim kutusu, yerel git deposuyla yeni bir proje oluşturmak için kullanılabilir. Etkinleştirmek için, aşağıdaki ekran **görüntüsünde gösterildiği gibi** Sürüm denetimi için git kullan onay kutusunu seçin. Bu, deponızı başlatacak ve isteğe bağlı bir .gitignore dosyası ekler:

![Git desteğiyle yeni proje oluşturma](media/version-control-git-publish-new1.png)

Yeni yerel depoyu yeni bir depoya itmek için aşağıdaki GitHub izleyin:

> [!NOTE]
> Henüz bir depo oluşturmadı GitHub uzak depo oluşturma [bölümüne GitHub](#creating-a-remote-repo-on-github) bakın.

1. Menü Çubuğunda Sürüm Denetimi'ne gidip **> ve Commit'i seçerek** ilk işlemenizi oluşturun.

2. Durum sekmesinde, sol üst **kısmından** Commit (Commit) (Tamamla) seçeneğine tıklayın.

3. "İlk Commit" gibi bir işleme iletisi yazın, sonra Dala'ya **tıklayın:**

    ![Git deposuna ilk değişiklikleri işleme](media/version-control-git-publish-new2.png)

4. Ardından, Menü Çubuğunda Sürüm Denetimi'ne **gidin ve > Ve UzakLarı Yönet'e gidin.**

5. Uzak Kaynaklar **sekmesine gidin** ve Ekle'ye **tıklayın.**

6. Uzak **Kaynak penceresinde,** daha önce oluşturduğunuz deponun ayrıntılarını GitHub Tamam'a **tıklayın:**

    ![Git deposu için uzak kaynakları yapılandırma](media/version-control-git-publish-new3.png)

7. Git Deposu **Yapılandırması penceresini kapatın,** ardından Menü Çubuğunda Sürüm Denetimi'ne gidin ve **değişiklikleri >'a gidin.**

8. Depoya **Itme penceresinde** Değişiklikleri Itme **düğmesine** tıklayın:

    ![Değişiklikleri uzak depoya itme](media/version-control-git-publish-new4.png)

9. İstendiğinde kullanıcı adı GitHub parolanızı girin.

> [!NOTE]
> Hesabınız iki faktörlü kimlik doğrulamasını (2FA) etkinleştirdiyse, parola yerine kullanılan bir Erişim Belirteci oluşturmanız gerekir. Erişim belirteci oluşturmadısanız Git Erişim Belirteci [belgelerinde yer alan adımları](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) izleyin.

Mac için Visual Studio şimdi değişiklikleri uzak depo GitHub itecek:

![Anında iletişim işlemi başarıyla tamamlandı onayı](media/version-control-git11.png)

## <a name="clone-an-existing-repository"></a>Mevcut depoyu kopyalama

Büyük olasılıkla yerel makineniz üzerinde değil, yalnızca uzak GitHub bir depolama GitHub çalışmanız gerekir. Mac için Visual Studio hızlı bir şekilde kopyalamaya olanak sağlar. Makinenize klonlamak için aşağıdaki adımları izleyin:

1. Menü çubuğunda Sürüm **Denetimi'> Depoyu Kopyala'ya tıklayın:**

2. Url **sekmesiyle Bağlan görüntülenir:**

    ![Bağlan ayrıntıların gir olduğu Url sekmesinin yer alan url'leri](media/version-control-git13.png)

3. Uzak GitHub üst sayfasında Kopyala veya İndir düğmesine basın ve **sağlanan** URL'yi kopyalayın:

    ![görüntülenen github URL'si](media/version-control-git14.png)

4. Url giriş alanında yer alan **tüm** metni url **Bağlan sekmeyle** değiştirin. Bu, adım adım görüntüde gösterildiği gibi bu sekmede yer alan diğer alanların çoğunu #2.

5. Repo'nun içine klonlamak istediğiniz dizini girin ve Kopyala'ya **basın.**

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
1. Çözüm Penceresinde çözüm düğümünü seçin.
1. Sürüm Denetimi menüsüne gidin ve Sürüm Denetiminde **Yayımla'yı seçin.**
1. 6. adımdan başlayarak yukarıdaki öğreticinin adımlarını izleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio sürüm denetimi (Windows)](/visualstudio/version-control/)
