---
title: Git Deposu Kurma
description: Mac için Visual Studio'da Git ve Subversion'u kullanma.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 02/15/2018
ms.assetid: E992FA1D-B2AD-4A28-ADC6-47E4FC471060
ms.openlocfilehash: e6dbe3b04a39a1ffd9a6e1b8f241b497ba8a6563
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984853"
---
# <a name="set-up-a-git-repository"></a>Git deposu ayarlama

Git, ekiplerin aynı belgeler üzerinde aynı anda çalışmasını sağlayan dağıtılmış bir sürüm kontrol sistemidir. Bu, tüm dosyaları içeren tek bir sunucu olduğu anlamına gelir, ancak bu merkezi kaynaktan bir depo kullanıma alındığında, tüm depo makinenize yerel olarak klonlanır.

Sürüm denetimi için Git ile çalışmanızı sağlayan birçok uzak ana bilgisayar vardır, ancak en yaygın ana bilgisayar GitHub'dır. Aşağıdaki örnekte GitHub ana bilgisayarı kullanılır, ancak Mac için Visual Studio'da sürüm denetimi için herhangi bir Git ana bilgisayar ını kullanabilirsiniz.

GitHub'ı kullanmak istiyorsanız, bu makaledeki adımları izleyerek önce bir hesap oluşturulduğunuve yapılandırıldığından emin olun.

## <a name="creating-a-remote-repo-on-github"></a>GitHub'da uzaktan repo oluşturma

Aşağıdaki örnekte GitHub ana bilgisayarı kullanılır, ancak Mac için Visual Studio'da sürüm denetimi için herhangi bir Git ana bilgisayar ını kullanabilirsiniz.

Git deposu ayarlamak için aşağıdaki adımları uygulayın:

1. github.com'da yeni bir Git repo'su oluşturun:

    ![Yeni git repo oluşturma](media/version-control-git1-sml.png)

2. Repo Adını, açıklamasını ve gizliliği ayarlayın. Repo'nun başlatılmasını **etmeyin.** Set .gitignore ve lisans hiçbiri için:

    ![Git repo ayrıntılarını ayarlama](media/version-control-git2.png)

3. Bir sonraki sayfa, oluşturduğunuz repo'nun HTTPS veya SSH adresini görüntüleme ve kopyalama seçeneği sunar:

    ![adresi görüntüleme ve kopyalama](media/version-control-git3.png)

   Bu repo için Mac için Visual Studio'yu işaret etmek için HTTPS adresine ihtiyacınız olacak.

## <a name="publishing-an-existing-project"></a>Varolan bir projeyi yayımlama

Sürüm denetiminde zaten _olmayan_ varolan bir projeniz varsa, bunu Git'de ayarlamak için aşağıdaki adımları kullanın:

1. Mac için Visual Studio'daki Solution Pad'den Çözüm adını seçin.

2. Menü çubuğunda, **Depo Seç** iletişim kutusunu görüntülemek için Sürüm Denetimi > **Sürüm Denetimi'nde** Yayımla'yı seçin:

    ![Mac için Visual Studio'da ödeme başlatma](media/version-control-git4-sml.png)

    Bu menü öğesi menüde soluk renkte görünüyorsa, Çözüm adını seçtiğinizden emin olun.

3. Kayıtlı **Depolar sekmesini** seçin ve **Ekle** düğmesine basın:

    ![](media/version-control-git5.png)

4. Deponun adını yerel olarak görüntülemek istediğiniz şekilde girin ve adım #3 URL'ye yapıştırın. Depo Yapılandırma iletişim kutusunuz aşağıdakilere benzer olmalıdır. Tamam'a basın:

    ![Git ayrıntıları iletişim kutusunu girin](media/version-control-git6.png)

    Git'e bağlanmak için SSH kullanmak da mümkündür.

5. Uygulamayı Git'de yayımlamaya çalışmak için depoyu seçin ve hem **Modül Adı** hem de **İleti** metin alanlarının tamamlandığından emin olun:

    ![Git için proje yayımlama girişimi](media/version-control-git7.png)

6. **Tamam'ı**tıklatın ve ardından uyarı iletişim kutusundan **Yayımla'yı** tıklatın.

7. Git **Kimlik Bilgileri** penceresine GitHub kullanıcı adınızı ve parolanızı girin. 

> [!NOTE]
> Hesabınızda iki faktörlü kimlik doğrulama (2FA) etkinleştirilmişse, parola yerine kullanılan bir Erişim Belirteci oluşturmanız gerekir. Bir erişim belirteci oluşturmadıysanız, Git [Access Token](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) belgelerindeki adımları izleyin.

8. Kullanıcı adını ve Kişisel Erişim Jetonunu girin ve **Tamam**tuşuna basın:

    ![Git için kullanıcı adı ve şifre girin](media/version-control-git9-sml.png)

9. Birkaç saniye sonra, Çözüm ilk taahhüdü ile yayınlanmalıdır. Sürüm Denetimi menü öğesine göz atarak yayımlandığını doğrulayın ve şimdi birçok seçenekle doldurulması gerekir:

    ![Sürüm Kontrol Menüsü](media/version-control-git10.png)

10. Ek değişiklikler yapmaya başladıktan sonra, değişiklikleri **uzak** depoya itmek için **Değişiklikleri Zorla'yı** seçin. Bu, tüm uygun kullanıcıların github.com görüntülemek için izin verecektir:

    ![Değişiklikleri uzak depoya itme](media/version-control-git11.png)

## <a name="publishing-a-new-project"></a>Yeni bir proje yayımlama

Yeni proje iletişim kutusu, yerel bir git deposu olan yeni bir proje oluşturmak için kullanılabilir. Etkinleştirmek **için,** aşağıdaki ekran görüntüsünde gösterildiği gibi sürüm denetimi onay kutusunu kullan seçeneğini belirleyin. Bu, repo'nuzu açar ve isteğe bağlı bir .gitignore dosyası ekler:

![git desteği ile yeni proje oluşturun](media/version-control-git-publish-new1.png)

Yeni yerel deponuzu yeni bir GitHub deposuna itmek için aşağıdaki adımları izleyin:

> [!NOTE]
> Daha önce bir GitHub deposu oluşturmadıysanız, GitHub bölümünde [uzaktan repo oluşturma](#creating-a-remote-repo-on-github) bölümüne bakın.

1. Sürüm Denetimi > İnceleme Çözümü'ne giderek ilk taahhüdünüzün oluşturulmasını ve Menü Çubuğu'nda **commit'e bağlanın.**

2. Durum sekmesinde sol üstteki **Commit'i** seçin.

3. "İlk Commit" gibi bir commit iletisi yazın, sonra **Commit'e**tıklayın:

    ![Git deposunda ilk değişiklikleri gerçekleştirme](media/version-control-git-publish-new2.png)

4. Ardından, Menü Çubuğu'nda **Sürüm Denetimi'ne gidin > Dalları ve Uzaktan Kumandaları Yönetin.**

5. **Uzak Kaynaklar** sekmesine gidin ve sonra **Ekle'yi**tıklatın.

6. Uzak **Kaynak** penceresinde, daha önce oluşturduğunuz GitHub deposunun ayrıntılarını ekleyin ve **Tamam'ı**tıklatın:

    ![Git deposu için uzak kaynakları yapılandırma](media/version-control-git-publish-new3.png)

7. Git **Deposu Yapılandırma** penceresini kapatın, ardından Menü Çubuğu'nda Sürüm Denetimi'ne gidin **> Değişiklikleri İttir.**

8. **Depoya Tuşuna Basın** penceresinde **Değişikliklere Basın** düğmesini tıklatın:

    ![Değişiklikleri uzak depoya itin](media/version-control-git-publish-new4.png)

9. İstendiğinde GitHub kullanıcı adınızı ve parolanızı girin.

> [!NOTE]
> Hesabınızda iki faktörlü kimlik doğrulama (2FA) etkinleştirilmişse, parola yerine kullanılan bir Erişim Belirteci oluşturmanız gerekir. Bir erişim belirteci oluşturmadıysanız, Git [Access Token](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) belgelerindeki adımları izleyin.

Mac için Visual Studio artık değişiklikleri uzaktan GitHub deponuza itecektir:

![Push işlemi başarıyla tamamlanan onay](media/version-control-git11.png)

## <a name="check-out-an-existing-repository"></a>Varolan bir depoya göz atın

Yerel makinenizde değil, yalnızca uzaktan kumandada bulunan bir GitHub reposuyla çalışmak zorunda kaldığınız olasıdır. Mac için Visual Studio hızlı bir şekilde bu repo kontrol etmenizi sağlar. Makinenize klonlamak için aşağıdaki adımları izleyin:

1. Menü çubuğunda Sürüm **Denetimi > Ödeme'yi**seçin:

2. Bu, **Depoya Bağlan sekmesini** görüntüler:

    ![Girilen ayrıntılarla Depo sekmesine bağlan](media/version-control-git13.png)

3. Uzaktan deponun GitHub **sayfasında, Klon veya İndir** düğmesine basın ve sağlanan URL'yi kopyalayın:

    ![github url görüntülenir](media/version-control-git14.png)

4. Depoya Bağlan sekmesindeki **URL** giriş alanındaki tüm metni **değiştirin.** Bu, adım #2 görüntüde gösterildiği gibi, bu sekmedeki diğer alanların çoğunu sizin için dolduracaktır.

5. Repo'yu klonlamak istediğiniz dizini girin ve **Kullanıma Çekin'e**basın.

> [!NOTE]
> Repo 4 GB boyutunda ise sorunlar yaşayabilirsiniz.

## <a name="troubleshooting"></a>Sorun giderme

Projenizi boş bir uzaktan depoyla başlatmada sorun varsa, aşağıdaki adımları deneyebilirsiniz:

1. Çözüm klasörünüze gidin.
1. Basın **Komutu + Shift + .** gizli dosya ve klasörleri göstermek için.
1. **Bir .git** klasörü varsa, silin.
1. Bir **gitignore** dosyası varsa, silin.
1. Basın **Komutu + Shift + .** dosya ve klasörleri gizlemek için.
1. Mac için ÇÖZÜMÜNÜZÜ VS'de açın.
1. Çözüm Pad'inde çözüm düğümünüzün seçin.
1. Sürüm Denetimi menüsüne göz atın ve **Sürüm Denetimi'nde Yayımla'yı**seçin.
1. Yukarıdaki öğretici adım 6 başlayarak adımları izleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da sürüm denetimi (Windows'da)](/visualstudio/version-control/)
