---
title: 'Walkthrough: Görsel Stüdyo Uzantısı Yayınlama | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a34260124baedeba297dbd64e8a2c1856b55ec5a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697137"
---
# <a name="walkthrough-publish-a-visual-studio-extension"></a>Walkthrough: Visual Studio uzantısı yayımlama

Bu izlik, Visual Studio Marketplace'te Visual Studio uzantısını nasıl yayınlayacağınızı gösterir. Uzantınızı Market'e eklediğinizde, geliştiriciler yeni ve güncelleştirilmiş uzantılara göz atmak için **Uzantıları ve Güncelleştirmeleri** kullanabilir.

## <a name="prerequisites"></a>Ön koşullar

 Bu izlenmeyi takip etmek için Visual Studio SDK'yı yüklemeniz gerekir. Daha fazla bilgi için Visual [Studio SDK'yı yükleyin.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-visual-studio-extension"></a>Visual Studio uzantısı oluşturma

Bu makalede varsayılan VSPackage uzantısı kullanır, ancak adımlar her tür uzantı için geçerlidir.

1. C# adlı `TestPublish` bir VSPackage oluşturarak menü komutu oluşturun. Daha fazla bilgi için ilk [uzantınızı oluşturun: Hello World](../extensibility/extensibility-hello-world.md)' e bakın.

## <a name="package-your-extension"></a>Uzantınızı paketle

1. Ürün adı, yazar ve sürüm hakkında doğru bilgilerle *.vsixmanifest* uzantısını güncelleştirin.

   ![uzantısı vsixmanifest güncelleme](media/update-extension-vsixmanifest.png)

2. Uzantınızı **Sürüm** modunda oluşturun. Şimdi uzantınız \bin\Release klasöründe VSIX olarak paketlenir.

3. Yüklemeyi doğrulamak için VSIX'yi çift tıklatabilirsiniz.

## <a name="test-the-extension"></a>Uzantıyı test edin

 Uzantıyı dağıtmadan önce, Visual Studio'nun deneysel örneğine doğru şekilde yüklendiğinden emin olmak için uzantını oluşturun ve test edin.

1. Visual Studio'da, Visual Studio'nun deneysel bir örneğini açmak için hata ayıklamaya başlayın.

2. Deneysel durumda, **Araçlar** menüsüne gidin ve **Uzantılar ve Güncelleştirmeler'i**tıklatın. TestPublish uzantısı orta bölmede görünmeli ve etkinleştirilmelidir.

3. **Araçlar** menüsünde test komutunu gördüğünüzden emin olun.

## <a name="publish-the-extension-to-the-visual-studio-marketplace"></a>Visual Studio Marketplace uzantısı nı yayınlayın

1. Uzantınızın Sürüm sürümünü oluşturduğundan ve güncel olduğundan emin olun.

2. Bir web tarayıcısında [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) web sitesini açın.

3. Sağ üst köşede Oturum **Aç'ı**tıklatın.

4. Oturum açabilmek için Microsoft hesabınızı kullanın. Microsoft hesabınız yoksa, bu noktada bir hesap oluşturabilirsiniz.

5. **Uzantıları Yayımla'yı**tıklatın.  Bu seçenek, tüm uzantılarınız için sizi yönet sayfasına yönlendirer. Yayımcı hesabınız yoksa, şu anda bir yayımcı hesabınız olması istenir.

   ![PazarA Yükle](media/upload-to-marketplace.png)

6. Uzantınızı yüklemek için kullanmak istediğiniz yayımcıyı seçin. Solda listelenen yayımcı adlarını tıklatarak yayımcıdeğiştirebilirsiniz. Yeni **uzantısı** tıklayın ve **Visual Studio**seçin.

7. 1: **Yükleme uzantısı**, Visual Studio Marketplace doğrudan bir VSIX dosyası yüklemek veya sadece kendi web sitesine bir bağlantı eklemek seçebilirsiniz. Bu örnekte, uzantısı, *TestPublish.vsix* yüklenir. Uzantınızı sürükleyip bırakın veya dosyaya göz atmak için **tıklama** bağlantısını kullanın. Uzantınızı projenin \bin\Release klasöründe bulun.  **Devam**’a tıklayın.

8. **2: Uzantı ayrıntıları sağlayın,** bazı alanlar uzantınızdan *source.extension.vsixmanifest* dosyasından otomatik olarak doldurulur. Her biri hakkında daha fazla ayrıntıyı aşağıda bulabilirsiniz:

    * **İç Ad,** uzantının ayrıntı sayfasının URL'sinde kullanılır. Örneğin, yayımcı adı "myname" altında bir uzantı yayımlamak ve dahili adı "uzanım" olarak\.belirtmek, uzantınızın ayrıntı sayfası için "marketplace.visualstudio com/items?itemName=myname.myextension" URL'si ile sonuçlanır.

    * Uzantınızın **Adını görüntüleyin.** Bu ad *source.extension.vsixmanifest* dosyasından otomatik olarak doldurulur.

    * Yüklediğiniz uzantının **sürüm** numarası. Bu sürüm *source.extension.vsixmanifest* dosyasından otomatik olarak doldurulur.

    * **VSIX ID,** Visual Studio'nun uzantınız için kullandığı benzersiz tanımlayıcıdır. Uzantınızın otomatik olarak güncelleştirilmiş olmasını istiyorsanız, bu tanımlayıcı gereklidir. Bu tanımlayıcı *source.extension.vsixmanifest* dosyasından otomatik olarak doldurulur.

    * Uzantınız için kullanılan **logo.** Bu logo, sağlanırsa *source.extension.vsixmanifest* dosyasından otomatik olarak doldurulur.

    * Uzantınızın ne işe yaradığı hakkında **kısa bir açıklama.** Bu açıklama *source.extension.vsixmanifest* dosyasından otomatik olarak doldurulur.

    * **Genel bakış,** uzantınızın ne yaptığı hakkında ekran görüntüleri ve ayrıntılı bilgiler eklemek için iyi bir yerdir.

    * **Desteklenen Visual Studio sürümleri,** uzantınızın Visual Studio'nun hangi sürümlerinde çalışacağını seçmenize olanak tanır. Uzantınız yalnızca bu sürümlere yüklenir.

    * **Desteklenen Visual Studio sürümü, uzantınızın hangi sürümlerinde çalışacağını seçmenizi sağlar. Uzantınız yalnızca bu sürümlere yüklenir.

    * **Yazın.** Uzantıların en yaygın türü **Araçlardır.**

    * **Kategoriler**. Uzatmanız için en uygun olan üç e kadar topayın.

    * **Etiketler,** kullanıcıların uzantınızı bulmasına yardımcı olan anahtar kelimelerdir. Etiketler, Market'teki uzantılarınızın arama alaka düzeyini artırmaya yardımcı olabilir.

    * **Fiyatlandırma Kategorisi,** uzantınızın maliyetidir.

    * **Kaynak kodu deposu,** kaynak kodunuzdaki bağlantıyı toplulukla paylaşmanıza olanak tanır.

    * **Uzantınız için Q&A'ya izin verin,** kullanıcıların uzantı giriş sayfanızda soru bırakmasına izin verin.

9. **Yükle& Kaydet'i**tıklatın. Bu seçenek sizi yayıncı yönetimi sayfanıza geri götürür. Uzantınız henüz yayınlanmadı. Uzantınızı yayımlamak için uzantınızın üzerine sağ tıklayın ve **Herkese Açık Ol'u**seçin. **Genişletmeyi**Görüntüle'yi seçerek uzantınızın Marketplace'te nasıl görüneceğini görüntüleyebilirsiniz. Edinme numaraları için **Raporlar'a**tıklayın. Uzantınızda değişiklik yapmak **için, Edit'e**tıklayın.

   ![Uzantı Giriş Menüsü](media/extension-entry-menu.png)

10. **Ortak Yap'ı**tıklattıktan sonra uzantınız artık herkese açık. Uzantınız için Visual Studio Marketplace'te arama yapın.

## <a name="add-additional-users-to-manage-your-publisher-account"></a>Yayıncı hesabınızı yönetmek için ek kullanıcılar ekleyin

Market, bir yayımcı hesabına erişmek ve yönetmek için ek kullanıcılara izin verilmesini destekler.

1. Ek kullanıcılar eklemek istediğiniz yayımcı hesabına gidin.

2. **Üyeler'i** seçin ve **Ekle'ye**tıklayın.

   ![Ek Kullanıcı Ekle](media/add-users.png)

3. Daha sonra eklemek istediğiniz kullanıcının e-posta adresini belirtebilir ve **bir rolü seç**altında doğru erişim düzeyini verebilirsiniz.  Aşağıdaki seçeneklerden birini belirtebilirsiniz:

   * **Oluşturan**: Kullanıcı uzantıları yayımlayabilir, ancak diğer kullanıcılar tarafından yayınlanan uzantıları görüntüleyemez veya yönetemez.

   * **Okuyucu**: Kullanıcı uzantıları görüntüleyebilir, ancak uzantıları yayımlayamaz veya yönetemez.

   * **Katkıda Bulunan**: Kullanıcı uzantıları yayımlayabilir ve yönetebilir, ancak yayımcı ayarlarını ayarlayamaz veya erişimi yönetemez.

   * **Sahibi**: Kullanıcı uzantıları yayımlayabilir ve yönetebilir, yayımcı ayarlarını dedebilir ve erişimi yönetebilir.

## <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Visual Studio Marketplace'ten uzantıyı yükleyin

Şimdi uzantısı yayımlanır, Visual Studio yükleyin ve orada test edin.

1. Visual Studio'da, **Araçlar** menüsünde **Uzantılar ve Güncellemeler'i**tıklatın.

2. **Online'ı** tıklatın ve ardından **TestPublish'i**arayın.

3. **İndir'i**tıklatın. Uzantı daha sonra yüklemek için zamanlanır.

4. Yüklemeyi tamamlamak için Visual Studio'nun tüm örneklerini kapatın.

## <a name="remove-the-extension"></a>Uzantıyı kaldırma

Uzantıyı Visual Studio Marketplace'ten ve bilgisayarınızdan kaldırabilirsiniz.

### <a name="to-remove-the-extension-from-the-visual-studio-marketplace"></a>Uzantıyı Visual Studio Marketplace'ten kaldırmak için

1. Visual [Studio Marketplace](https://marketplace.visualstudio.com/vs) web sitesini açın.

2. Sağ üst köşede, uzantıları **yayımla'yı** tıklatın. **TestPublish'i**yayımlamak için kullandığınız yayımcıyı seçin. **TestPublish** listesi görüntülenir.

3. Uzantı girişine sağ tıklayın ve **Kaldır'ı**tıklatın. Uzantıyı kaldırmak isteyip istemediğiniz istenir. **Tamam**'a tıklayın.

### <a name="to-remove-the-extension-from-your-computer"></a>Uzantıyı bilgisayarınızdan kaldırmak için

1. Visual Studio'da, **Araçlar** menüsünde **Uzantılar ve Güncellemeler'i**tıklatın.

2. **TestYayım'ı** seçin ve ardından **Kaldır'ı**tıklatın. Uzantı daha sonra kaldırmak için zamanlanır.

3. Yüklemeyi tamamlamak için Visual Studio'nun tüm örneklerini kapatın.
