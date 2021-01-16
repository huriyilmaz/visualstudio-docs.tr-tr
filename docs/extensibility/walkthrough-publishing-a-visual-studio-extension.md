---
title: 'İzlenecek yol: Visual Studio uzantısı yayımlama | Microsoft Docs'
description: Visual Studio Market için bir Visual Studio uzantısı yayımlamayı öğrenin. Bu, geliştiricilerin yeni ve güncelleştirilmiş uzantılara gözatmasına olanak tanır.
ms.custom: SEO-VS-2020
ms.date: 01/15/2021
ms.topic: how-to
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 01a46f54bfbce6126c16fa418d5c4bef53afd09b
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533955"
---
# <a name="walkthrough-publish-a-visual-studio-extension"></a>İzlenecek yol: Visual Studio uzantısı yayımlama

Bu izlenecek yol, Visual Studio Market için bir Visual Studio uzantısı yayımlamayı gösterir. Uzantınızı Visual Studio Market eklediğinizde, geliştiriciler yeni ve güncelleştirilmiş uzantılara gözatabilmeniz için **uzantıları ve güncelleştirmeleri** kullanabilir.

## <a name="prerequisites"></a>Ön koşullar

 Bu yönergeyi izlemek için, Visual Studio SDK 'sını yüklemelisiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yüklemeyi](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Visual Studio uzantısı oluşturma

Bu makale varsayılan VSPackage uzantısını kullanır, ancak adımlar her tür uzantı için geçerlidir.

- Bir menü komutu olan adlı C# adlı bir VSPackage oluşturun `TestPublish` . Daha fazla bilgi için bkz. [ilk uzantınızı oluşturma: Merhaba Dünya](../extensibility/extensibility-hello-world.md).

## <a name="package-your-extension"></a>Uzantınızı paketleyin

1. *. Valtmanifest* uzantısını ürün adı, yazarı ve sürümü hakkında doğru bilgilerle güncelleştirin.

   ![Uzantı valtbildirimini Güncelleştir](media/update-extension-vsixmanifest.png)

2. Uzantınızı **yayın** modunda derleyin. Artık uzantınız, \bin\Release klasöründe bir VSıX olarak paketlenmiştir.

3. Yüklemeyi doğrulamak için VSıX 'e çift tıklayabilirsiniz.

## <a name="test-the-extension"></a>Uzantıyı test etme

 Uzantıyı dağıtmadan önce, Visual Studio 'nun deneysel örneğine doğru yüklendiğinden emin olmak için oluşturun ve test edin.

1. Visual Studio 'da, Visual Studio 'nun deneysel bir örneğini açmak için hata ayıklamayı başlatın.

2. Deneysel örnekte, **Araçlar** menüsüne gidin ve **Uzantılar ve güncelleştirmeler**' e tıklayın. TestPublish uzantısı Orta bölmede görünmelidir ve etkinleştirilmelidir.

3. **Araçlar** menüsünde, test komutunu görtığınızdan emin olun.

## <a name="publish-the-extension-to-visual-studio-marketplace"></a>Uzantıyı Visual Studio Market yayımlayın

1. Uzantınızın yayın sürümünü derlediğinizden ve güncel olduğundan emin olun.

2. Bir Web tarayıcısında [Visual Studio Market](https://marketplace.visualstudio.com/vs)' a gidin.

3. Sağ üst köşede **oturum aç**' a tıklayın.

4. Oturum açmak için Microsoft hesabı kullanın. Bir Microsoft hesabı yoksa, bu noktada bir tane oluşturabilirsiniz.

5. **Uzantıları Yayımla**' ya tıklayın. Bu seçenek sizi tüm uzantılarınızın Yönet sayfasına yönlendirir. Yayımcı hesabınız yoksa şu anda bir tane oluşturmanız istenir.

   ![Market 'e yükle](media/upload-to-marketplace.png)

6. Uzantınızı karşıya yüklemek için kullanmak istediğiniz yayımcıyı seçin. Sol tarafta listelenen yayımcı adlarına tıklayarak yayımcıları değiştirebilirsiniz. **Yeni uzantı** ' a tıklayın ve **Visual Studio**' yı seçin.

7. **1: uzantıyı karşıya yükleyin**, bir VSIX dosyasını doğrudan Visual Studio Market veya yalnızca kendi web sitenize bir bağlantı eklemek üzere yüklemeyi seçebilirsiniz. Bu örnekte, *TestPublish. vsix* uzantısı karşıya yüklenir. Uzantınızı sürükleyip bırakın veya dosyaya gitmek için **tıklama** bağlantısını kullanın. Uzantınızı projenin \bin\Release klasöründe bulun.  **Devam**’a tıklayın.

8. **2: uzantı ayrıntılarını sağlayın**, bazı alanlar uzantıınızdan *kaynak. Extension. valtmanifest* dosyasından otomatik olarak doldurulur. Aşağıdakiler hakkında daha fazla ayrıntı bulun:

    * **Iç ad** , uzantının ayrıntı sayfasının URL 'sinde kullanılır. Örneğin, "MyName" yayımcı adı altında bir uzantı yayımlamak ve dahili adı "uzantım" olacak şekilde belirtmek, \. uzantınızın ayrıntı sayfası için "Market. VisualStudio com/Items? ItemName = myname. MyExtension" URL 'si ile sonuçlanır.

    * Uzantınızın **görünen adı** . Bu ad, *Source. Extension. valtmanifest* dosyasından otomatik olarak doldurulur.

    * Karşıya yüklediğiniz uzantının **Sürüm** numarası. Bu sürüm, *kaynak. Extension. valtmanifest* dosyasından otomatik olarak doldurulur.

    * **VSıX kimliği** , Visual Studio 'nun uzantınız için kullandığı benzersiz tanıtıcıdır. Uzantınızın otomatik güncelleştirilmesini istiyorsanız bu tanımlayıcı gereklidir. Bu tanımlayıcı, *kaynak. Extension. valtmanifest* dosyasından otomatik olarak doldurulur.

    * Uzantınız için kullanılan **logo** . Bu logo, sağlanmışsa *kaynak. Extension. valtmanifest* dosyasından otomatik olarak doldurulur.

    * Uzantınızın ne yaptığını **kısa bir açıklama** . Bu açıklama, *Source. Extension. valtmanifest* dosyasından otomatik olarak doldurulur.

    * **Genel bakış** , dahili ekran görüntülerini ve uzantınızın ne yaptığını hakkında ayrıntılı bilgileri içerecek şekilde iyi bir yerdir.

    * **Desteklenen Visual Studio sürümleri** , uzantınızın hangi Visual Studio sürümlerini üzerinde çalışabileceği seçmenize olanak sağlar. Uzantınızın yalnızca bu sürümlere yüklenmiş olması.

    * **Desteklenen Visual Studio sürümü** , uzantınızın hangi Visual Studio sürümlerini üzerinde çalışabileceği seçmenize olanak sağlar. Uzantınız yalnızca bu sürümlere yüklenir.

    * **Yazın**. En yaygın uzantı türü **araçlardır**.

    * **Kategoriler**. Uzantınıza en uygun olan en fazla üç seçin.

    * **Etiketler** , kullanıcıların uzantınızı bulmasına yardımcı olan anahtar sözcüklerdir. Etiketler, Visual Studio Market uzantılarınızın arama uygunluğunu artırmaya yardımcı olabilir.

    * **Fiyatlandırma kategorisi** , uzantınızın maliyetidir.

    * **Kaynak kodu deposu** , topluluk ile kaynak kodunuzun bağlantısını paylaşmanıza olanak sağlar.

    * **Uzantınız Için Q&A 'Nın Izin verme** özelliği, kullanıcıların uzantı giriş sayfanızda soru bırakabilir.

9. **Karşıya yükle & kaydet**' e tıklayın. Bu seçenek sizi yayımcı yönetimi sayfanıza geri götürür. Uzantınız henüz yayımlanmadı.

10. Uzantınızı yayımlamak için uzantınızın üzerine sağ tıklayıp **ortak yap**' ı seçin. Uzantınızın Visual Studio Market nasıl görüneceğine bakmak için **uzantıyı görüntüle**' yi seçin. Alım numaraları için **raporlar**' a tıklayın. Uzantınızın üzerinde değişiklik yapmak için **Düzenle**'ye tıklayın.

    ![Uzantı giriş menüsü](media/extension-entry-menu.png)

11. **Genel yap**' a tıklayın ve uzantınızın artık genel olması gerekir. Uzantınız için Visual Studio Market arayın.

## <a name="update-a-published-extension-in-visual-studio-marketplace"></a>Visual Studio Market yayımlanmış bir uzantıyı güncelleştirme

Başlamadan önce, uzantınızın yeni yayın sürümünü oluşturduğunuzdan ve güncel olduğundan emin olun.

1.  Bir Web tarayıcısında [Visual Studio Market](https://marketplace.visualstudio.com/vs)' a gidin.

1.  Sağ üst köşede **oturum aç**' a tıklayın ve ardından Microsoft hesabı oturum açın.

    :::image type="content" source="media/marketplace-upload-extension.png" alt-text="Dosya Gezgini 'nde karşıya yüklenen bir uzantı dosyasını seçmeyi gösteren ekran görüntüsü.":::

1.  **Uzantıları Yayımla**' ya tıklayın ve ardından, güncelleştirilmiş uzantınızı karşıya yüklemek için kullanmak istediğiniz yayımcıyı seçin.

    :::image type="content" source="media/marketplace-select-extension-version.png" alt-text="Yayımlama uzantıları bağlantısı vurgulanmış Visual Studio Market ekran görüntüsü.":::

1.  Güncelleştirmek istediğiniz uzantının yanında, farenizi üç yatay nokta üzerine getirin ve ardından **Düzenle**' yi seçin.

    :::image type="content" source="media/marketplace-select-extension.png" alt-text="Düzenlenecek uzantıyı seçmeyi gösteren ekran görüntüsü.":::

1.  **1: uzantıyı karşıya yükle**, VSIX dosyanızın adından sonra, yayımlanan uzantınızı düzenlemek için kalem simgesine tıklayın.

     :::image type="content" source="media/marketplace-edit-extension-details.png" alt-text="Uzantınızı düzenlemek için kalem simgesine tıklayan ekran görüntüsü.":::

1.  Güncelleştirilmiş uzantı VSıX dosyanıza gidin. Dosyaya ve sonra **Aç**' a tıklayın.

    Güncelleştirilmiş uzantınız karşıya yüklenir.

    :::image type="content" source="media/marketplace-upload-extension-notification.png" alt-text="Düzenlenmiş bir uzantıyı karşıya yükledikten sonra karşıya dosya yükleme bildiriminin ekran görüntüsü.":::

1. **2: uzantı ayrıntılarını belirtin**, bazı ayrıntılar uzantı güncelleştirmesi için salt okunurdur veya uzantıınızdan *kaynak. Extension. valtmanifest* dosyasından otomatik olarak doldurulur. Uzantı ayrıntıları hakkında daha fazla bilgi aşağıdadır:

    - **Iç ad** \* , uzantının ayrıntı sayfasının URL 'sinde kullanılır. Örnek olarak, "MyName" yayımcı adı altında bir uzantı yayımlamak ve dahili adı "My extenm" olarak belirtmek, uzantınızın ayrıntı sayfası için "marketplace.visualstudio.com/items?itemName=myname.myextension" URL 'SI ile sonuçlanır.

    - **Görünen ad** \* . Bu ad, *Source. Extension. valtmanifest* dosyasından otomatik olarak doldurulur.

    - **Sürümü** \* karşıya yüklediğiniz uzantının numarası. Bu sürüm, *kaynak. Extension. valtmanifest* dosyasından otomatik olarak doldurulur.

    - **VSıX kimliği** \* , Visual Studio 'Nun uzantınız için kullandığı benzersiz tanımlayıcıdır. Uzantınızın otomatik güncelleştirilmesini istiyorsanız bu tanımlayıcı gereklidir. Bu tanımlayıcı, *kaynak. Extension. valtmanifest* dosyasından otomatik olarak doldurulur.

    - **Logo** \* Bu, uzantınız için kullanılır. Bu logo, sağlanmışsa *kaynak. Extension. valtmanifest* dosyasından otomatik olarak doldurulur.

    - **Kısa açıklama** \* uzantınızın ne yaptığını. Bu açıklama, *Source. Extension. valtmanifest* dosyasından otomatik olarak doldurulur.

    - **Genel bakış** , dahili ekran görüntülerini ve uzantınızın ne yaptığını hakkında ayrıntılı bilgileri içerecek şekilde iyi bir yerdir.

    - **Desteklenen Visual Studio sürümleri** \* uzantınızın hangi Visual Studio sürümlerini çalışacaksınız seçmenizi sağlar. Uzantınızın yalnızca bu sürümlere yüklenmiş olması.

    - **Desteklenen Visual Studio sürümü** \* uzantınızın hangi Visual Studio sürümlerini üzerinde çalışabileceği seçmenize olanak sağlar. Uzantınızın yalnızca bu sürümlerde yüklü olması.

    - **Yazın**. En yaygın uzantı türü **araçlardır**.

    - **Kategoriler**. Uzantınıza en uygun olan en fazla üç seçin.

    - **Etiketler** , kullanıcıların uzantınızı bulmasına yardımcı olan anahtar sözcüklerdir. Etiketler, Visual Studio Market uzantılarınızın arama uygunluğunu artırmaya yardımcı olabilir.

    - **Fiyatlandırma kategorisi** , uzantınızın maliyetidir.

    - **Kaynak kodu deposu** , topluluk ile kaynak kodunuzun bağlantısını paylaşmanıza olanak sağlar.

    - **Uzantınız Için Q&A 'Nın Izin verme** özelliği, kullanıcıların uzantı giriş sayfanızda soru bırakabilir.

       \* Bu ayrıntı, bir uzantı güncelleştirmesi için değiştirilemez.

1. **Karşıya yükle & kaydet**' e tıklayın. Bu seçenek sizi yayımcı yönetimi sayfanıza geri götürür. Uzantınız henüz yayımlanmadı.

1. Uzantınızı yayımlamak için, uzantınızı sağ tıklatın ve **genel yap**' ı seçin. Uzantınızın Visual Studio Market nasıl görüneceğine bakmak için **uzantıyı görüntüle**' yi seçin. Alım numaraları için **raporlar**' a tıklayın. Uzantınızın üzerinde değişiklik yapmak için **Düzenle**' ye tıklayın.

## <a name="add-additional-users-to-manage-your-publisher-account"></a>Yayımcı hesabınızı yönetmek için ek kullanıcılar ekleyin

Visual Studio Market, yayımcı hesabına erişmek ve bunları yönetmek için ek kullanıcı izinleri vermeyi destekler.

1. Ek kullanıcı eklemek istediğiniz yayımcı hesabına gidin.

2. **Üyeler** ' i seçin ve **Ekle**' ye tıklayın.

   ![Ek Kullanıcı ekleme](media/add-users.png)

3. Ardından, eklemek istediğiniz kullanıcının e-posta adresini belirtebilir ve **Rol Seç** altında doğru erişim düzeyine sahip olabilirsiniz.  Aşağıdaki seçeneklerden birini belirtebilirsiniz:

   * **Oluşturucu**: Kullanıcı Uzantıları yayımlayabilir, ancak diğer kullanıcılar tarafından yayımlanan uzantıları görüntüleyemez veya yönetemez.

   * **Okuyucu**: Kullanıcı Uzantıları görüntüleyebilir, ancak uzantıları yayımlayamaz veya yönetemez.

   * **Katkıda bulunan**: Kullanıcı Uzantıları yayımlayabilir ve yönetebilir, ancak yayımcı ayarlarını düzenleyemez veya erişimi yönetebilir.

   * **Sahip**: Kullanıcı Uzantıları yayımlayabilir ve yönetebilir, yayımcı ayarlarını düzenleyebilir ve erişimi yönetebilir.

## <a name="install-the-extension-from-visual-studio-marketplace"></a>Uzantıyı Visual Studio Market 'den yüklemesi

Artık uzantı yayımlandığına göre, Visual Studio 'Ya yükleyip test edin.

1. Visual Studio 'da, **Araçlar** menüsünde **Uzantılar ve güncelleştirmeler**' e tıklayın.

2. **Çevrimiçi** ' e tıklayın ve ardından **TestPublish** için arama yapın.

3. **İndir**’e tıklayın. Uzantı daha sonra yüklenmek üzere zamanlanır.

4. Yüklemeyi gerçekleştirmek için Visual Studio 'nun tüm örneklerini kapatın.

## <a name="remove-the-extension"></a>Uzantıyı kaldırma

Uzantıyı Visual Studio Market ve bilgisayarınızdan kaldırabilirsiniz.

### <a name="to-remove-the-extension-from-visual-studio-marketplace"></a>Uzantıyı Visual Studio Market kaldırmak için

1. [Visual Studio Market](https://marketplace.visualstudio.com/vs)gidin.

2. Sağ üst köşede bulunan uzantıları **Yayımla** ' ya tıklayın. **TestPublish** yayımlamak için kullandığınız yayımcıyı seçin. **TestPublish** listesi görüntülenir.

3. Uzantı girişine sağ tıklayın ve **Kaldır**' a tıklayın. Uzantıyı kaldırmak isteyip istemediğinizi onaylamanız istenir. **Tamam**'a tıklayın.

### <a name="to-remove-the-extension-from-your-computer"></a>Uzantıyı bilgisayarınızdan kaldırmak için

1. Visual Studio 'da, **Araçlar** menüsünde **Uzantılar ve güncelleştirmeler**' e tıklayın.

2. **TestPublish** ' ı seçin ve ardından **Kaldır**' a tıklayın. Uzantı daha sonra kaldırma için zamanlanır.

3. Kaldırma işlemini gerçekleştirmek için Visual Studio 'nun tüm örneklerini kapatın.
