---
title: Git deposu ayarlama
description: Mac için Visual Studio git ve alt sürüm kullanma.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 02/15/2018
ms.assetid: E992FA1D-B2AD-4A28-ADC6-47E4FC471060
ms.topic: how-to
ms.openlocfilehash: c226e1a8160d0eb1321d244b26177119ec3a5846
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238562"
---
# <a name="set-up-a-git-repository"></a>Git deposu ayarlama

Git, ekiplerin aynı belgelerde aynı anda çalışmasına izin veren bir dağıtılmış sürüm denetim sistemidir. Bu, tüm dosyaları içeren tek bir sunucu olduğu anlamına gelir, ancak bu Merkezi kaynaktan bir depo kullanıma alındığı zaman, tüm depo yerel olarak makinenize kopyalanır.

Sürüm denetimi için git ile çalışmanıza izin veren birçok uzak ana bilgisayar vardır, ancak en yaygın konak GitHub ' dır. Aşağıdaki örnek bir GitHub Konağı kullanır, ancak Mac için Visual Studio ' de sürüm denetimi için herhangi bir git konağını kullanabilirsiniz.

GitHub kullanmak istiyorsanız, bu makaledeki adımları izleyerek önce oluşturulmuş ve yapılandırılmış bir hesabınız olduğundan emin olun.

## <a name="creating-a-remote-repo-on-github"></a>GitHub 'da uzak depo oluşturma

Aşağıdaki örnek bir GitHub Konağı kullanır, ancak Mac için Visual Studio ' de sürüm denetimi için herhangi bir git konağını kullanabilirsiniz.

Bir git deposu ayarlamak için aşağıdaki adımları yürütün:

1. Github.com adresinde yeni bir git deposu oluşturun:

    ![Yeni git deposu oluştur](media/version-control-git1-sml.png)

2. Depo adı, açıklama ve gizliliği ayarlayın. Depoyu **başlatmayın** . . Gitignore ve lisansını None olarak ayarlayın:

    ![Git deposunun ayrıntılarını ayarlama](media/version-control-git2.png)

3. Sonraki sayfada, HTTPS ya da SSH adresini görüntüleme ve oluşturduğunuz depoya kopyalama seçeneği sunulur:

    ![adresi görüntüle ve Kopyala](media/version-control-git3.png)

   Mac için Visual Studio bu depoya işaret etmek için HTTPS adresine ihtiyacınız olacak.

## <a name="publishing-an-existing-project"></a>Mevcut bir projeyi yayımlama

Zaten sürüm denetiminde _olmayan_ mevcut bir projeniz varsa, git 'te ayarlamak için aşağıdaki adımları kullanın:

1. Mac için Visual Studio Çözüm Bölmesi çözüm adını seçin.

2. Menü çubuğunda, **Depo Seç** iletişim kutusunu göstermek için sürüm denetimi **'Nde Yayımla > sürüm** denetimi ' ni seçin:

    ![Mac için Visual Studio kullanıma almayı Başlat](media/version-control-git4-sml.png)

    Menüdeki bu menü öğesi gri görünürse, çözüm adını seçtiğinizden emin olun.

3. **Kayıtlı depolar** sekmesini seçin ve **Ekle** düğmesine basın:

    ![Depo Seç iletişim kutusunun kayıtlı depolar sekmesinde, modül adı ve Ileti için ekleme, kaldırma ve düzenleme düğmeleri ve kutuları bulunur.](media/version-control-git5.png)

4. Yerel olarak görüntülenmesini istediğiniz deponun adını girin ve adım #3 ' den URL 'YI yapıştırın. Depo yapılandırma iletişim kutusu, aşağıdakine benzer olmalıdır. Tamam 'a basın:

    ![Git ayrıntıları iletişim kutusunu girin](media/version-control-git6.png)

    Ayrıca, git 'e bağlanmak için SSH kullanmak mümkündür.

5. Uygulamayı git 'e yayımlamayı denemek için depoyu seçin ve hem **Modül adı** hem de **ileti** metin alanlarının tamamlandığından emin olun:

    ![Projeyi git 'e yayımlamayı dene](media/version-control-git7.png)

6. **Tamam**' a ve ardından uyarı Iletişim kutusundan **Yayımla** ' ya tıklayın.

7. **Git kimlik bilgileri** penceresinde GitHub Kullanıcı adınızı ve parolanızı girin. 

> [!NOTE]
> Hesabınızda iki öğeli kimlik doğrulaması (2FA) etkinse, parola yerine kullanılan bir erişim belirteci oluşturmanız gerekir. Erişim belirteci oluşturmadıysanız git [erişim belirteci](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) belgelerindeki adımları izleyin.

8. Kullanıcı adı ve kişisel erişim belirtecini girip **Tamam**' a basın:

    ![Git için Kullanıcı adı ve parola girin](media/version-control-git9-sml.png)

9. Birkaç saniye sonra çözümün ilk yürütmesi ile yayımlanması gerekir. Sürüm denetimi menü öğesine göz atarak yayımlanmış olduğunu onaylayın ve şu anda birçok seçenekten doldurulması gerekir:

    ![Sürüm Denetim menüsü](media/version-control-git10.png)

10. Daha fazla değişiklik yapmaya başladıktan sonra değişiklikleri **Gönder** ' i seçerek değişiklikleri **uzak** depoya gönderin. Bu, tüm uygun kullanıcıların github.com üzerinde görüntülemesini sağlar:

    ![Değişiklikleri uzak depoya gönder](media/version-control-git11.png)

## <a name="publishing-a-new-project"></a>Yeni bir proje yayımlama

Yeni proje iletişim kutusu yerel bir git deposu ile yeni bir proje oluşturmak için kullanılabilir. Etkinleştirmek için, aşağıdaki ekran görüntüsünde gösterildiği gibi **sürüm denetimi için git kullan** onay kutusunu seçin. Bu işlem, depoyu başlatacak ve isteğe bağlı bir. gitignore dosyası ekleyecek:

![Git desteğiyle yeni proje oluşturma](media/version-control-git-publish-new1.png)

Yeni yerel deponuzu yeni bir GitHub deposuna göndermek için aşağıdaki adımları izleyin:

> [!NOTE]
> Zaten bir GitHub deposu oluşturmadıysanız [GitHub 'da uzak depo oluşturma](#creating-a-remote-repo-on-github) bölümüne bakın.

1. **Sürüm denetimi > gözden geçirme çözümü ve** menü çubuğunda Kaydet ' e giderek ilk yürütmeyi oluşturun.

2. Durum sekmesinde, sol üst kısımdaki **Kaydet** ' i seçin.

3. "Ilk tamamlama" gibi bir teslim iletisi yazın ve ardından **Yürüt**' e tıklayın:

    ![Git deposuna ilk değişiklikleri Kaydet](media/version-control-git-publish-new2.png)

4. Ardından, menü çubuğunda sürüm denetimi ' ne gidin **> dalları ve uzaktan**Kumandalar ' ı yönetin.

5. **Uzak kaynaklar** sekmesine gidin ve ardından **Ekle**' ye tıklayın.

6. **Uzak kaynak** penceresinde, önceden oluşturulmuş GitHub deponuzun ayrıntılarını ekleyin ve **Tamam**' a tıklayın:

    ![Git deposu için uzak kaynakları yapılandırma](media/version-control-git-publish-new3.png)

7. **Git deposu yapılandırma** penceresini kapatın, ardından menü çubuğunda **sürüm denetimi > gönderme değişiklikleri**' ne gidin.

8. **Depoya gönder** penceresinde **Değişiklikleri Gönder** düğmesine tıklayın:

    ![Değişiklikleri uzak depoya gönder](media/version-control-git-publish-new4.png)

9. İstendiğinde GitHub Kullanıcı adınızı ve parolanızı girin.

> [!NOTE]
> Hesabınızda iki öğeli kimlik doğrulaması (2FA) etkinse, parola yerine kullanılan bir erişim belirteci oluşturmanız gerekir. Erişim belirteci oluşturmadıysanız git [erişim belirteci](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) belgelerindeki adımları izleyin.

Mac için Visual Studio artık değişiklikleri uzak GitHub deponuza gönderir:

![Gönderme işlemi başarıyla tamamlandı onayı](media/version-control-git11.png)

## <a name="check-out-an-existing-repository"></a>Mevcut bir depoya göz atın

Yerel makinenizde değil yalnızca uzak üzerinde bulunan bir GitHub deposu ile çalışmanız gerekecektir. Mac için Visual Studio, bu depoyu hızla denetlemenizi sağlar. Makinenize kopyalamak için aşağıdaki adımları izleyin:

1. Menü çubuğunda, **sürüm denetimi > kullanıma al**' ı seçin:

2. Bu, **depoya Bağlan** sekmesini görüntüler:

    ![Girilen ayrıntıları içeren depo sekmesine Bağlan](media/version-control-git13.png)

3. Uzak deponun GitHub sayfasında, Kopyala **veya indir** düğmesine basın ve belirtilen URL 'yi kopyalayın:

    ![GitHub URL 'si görüntülendi](media/version-control-git14.png)

4. **Depoya Bağlan** sekmesindeki **URL** girdisi alanındaki tüm metni değiştirin. Bu, adım #2 görüntüde gösterildiği gibi bu sekmedeki diğer birçok alanın çoğunu dolduracaktır.

5. Depoyu kopyalamak istediğiniz dizini girin ve **kullanıma al**' a basın.

> [!NOTE]
> Depo boyutu 4 GB 'ın üzerinde olduğunda sorunlarla karşılaşabilirsiniz.

## <a name="troubleshooting"></a>Sorun giderme

Projenizi boş bir uzak depoyla başlatma ile ilgili sorunlarınız varsa, aşağıdaki adımları deneyebilirsiniz:

1. Çözüm klasörünüze gidin.
1. **Komut + SHIFT +** tuşlarına basın. gizli dosyaları ve klasörleri göstermek için.
1. Bir **. git** klasörü varsa, silin.
1. Bir **gitignore** dosyası varsa, silin.
1. **Komut + SHIFT +** tuşlarına basın. dosya ve klasörleri gizleme.
1. Çözümünüzü Mac için VS 'de açın.
1. Çözüm panelinde, çözüm düğümünüz ' ı seçin.
1. Sürüm denetimi menüsüne gidin ve **sürüm denetiminde Yayımla '** yı seçin.
1. Adım 6 ' dan başlayarak yukarıdaki öğreticinin adımlarını izleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da sürüm denetimi (Windows üzerinde)](/visualstudio/version-control/)
